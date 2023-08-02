---
title: OrchardCore CustomSettings
date: 2023-08-02 22:34:05
categories: 
- .NET
tags: 
- .NET
- C#
- ASP.NET Core
- Orchard Core
---
CustomSettings （自定义设置）允许网站管理员创建一组针对网站全局的自定义属性。
这些设置在标准设置部分中进行编辑，可以使用特定权限进行保护。

<!-- more -->

## CustomSettings 是什么？

CustomSettings 是一个数据对象，存储于 ISite 全局对象中。

## 如何创建？

有两种方式可以创建 CustomSettings。
- [以编程方式创建](#以编程方式创建)
- [在 Admin 中创建](#在-Admin-中创建)

## 以编程方式创建

首先需要创建一个 class，包含一些公共属性，如下：

```c#
public class MySettings
{
    public string Prop1 { get; set; } = string.Empty;

    public string? Prop2 { get; set; }

    public int Prop3 { get; set; }

    public bool Prop4 { get; set; }
}

```

其次由于我们的自定义设置是需要支持在 Admin 中进行修改的，因此我们还需要创建 ViewModel 和 编辑视图。

ViewModel 示例：
```c#
public class MySettingsViewModel
{
    public string Prop1 { get; set; } = string.Empty;

    public string? Prop2 { get; set; }

    public int Prop3 { get; set; }

    public bool Prop4 { get; set; }
}
```

编辑视图是一个 Shape，因此需要根据 Template 规则来命名；

因为这里我们的模板命名为“MySettings_Edit”，所以视图文件应该命名为“MySettings.Edit.cshtml”；

编辑视图的内容只是一个 Bootstrap 表单，示例：

```razor
@model MySettingsViewModel

<p class="alert alert-warning">
    @T["The current tenant will be reloaded when the settings are saved."]
</p>

<h3>@T["My Settings"]</h3>

<div class="mb-3 row" asp-validation-class-for="Prop1">
    <div class="col-large">
        <label asp-for="Prop1">@T["Prop1"]</label>
        <input asp-for="Prop1" class="form-control" autocomplete="off" />
        <span asp-validation-for="Prop1"></span>
        <span class="hint">@T["Prop1 hint"]</span>
    </div>
</div>

<div class="mb-3 row" asp-validation-class-for="Prop2">
    <div class="col-large">
        <label asp-for="Prop2">@T["Prop2"]</label>
        <input asp-for="Prop2" class="form-control" autocomplete="off" />
        <span asp-validation-for="Prop2"></span>
        <span class="hint">@T["Prop2 hint"]</span>
    </div>
</div>

<div class="mb-3 row" asp-validation-class-for="Prop3">
    <div class="col-large">
        <label asp-for="Prop3">@T["Prop3"]</label>
        <input asp-for="Prop3" type="number" class="form-control" autocomplete="off" />
        <span asp-validation-for="Prop3"></span>
        <span class="hint">@T["Prop3 hint"]</span>
    </div>
</div>

<div class="mb-3" asp-validation-class-for="Prop4">
    <div class="form-check">
        <input type="checkbox" class="form-check-input" asp-for="Prop4">
        <label class="form-check-label" asp-for="Prop4">@T["Prop4"]</label>
        <span class="hint dashed">@T["Prop4 hint"]</span>
    </div>
</div>
```

然后我们需要实现一个 `IDisplayDriver<ISite>`，这里我们选择继承自 `SectionDisplayDriver<ISite, MySettings>`：

```c#
public class MySettingsDisplayDriver: SectionDisplayDriver<ISite, MySettings>
{
    private readonly IShellHost _shellHost;
    private readonly ShellSettings _shellSettings;

    public MySettingsDisplayDriver(IShellHost shellHost, ShellSettings shellSettings)
    {
        _shellHost = shellHost;
        _shellSettings = shellSettings;
    }

    public override async Task<IDisplayResult> EditAsync(MySettings settings, BuildEditorContext context)
    {
        await Task.Yield();

        // 第一个参数指定了编辑视图的 Shape 模板，
        // 对应 Views/MySettings.Edit.cshtml 
        // 或者 Views/MySettings.Edit.liquid
        return Initialize<MySettingsViewModel>("MySettings_Edit", model =>
        {
            // 初始化视图模型
            model.Prop1 = settings.Prop1;
            model.Prop2 = settings.Prop2;
            model.Prop3 = settings.Prop3;
            model.Prop4 = settings.Prop4;
        })
            // 定义这个自定义设置在表单中的位置（顺序），因为其他模块可能会对这个自定义设置进行扩展
            .Location("Content:1")
            // 定义这个自定义设置的分组
            .OnGroup("MySettingsGroup");
    }

    public override async Task<IDisplayResult> UpdateAsync(MySettings settings, BuildEditorContext context)
    {
        if (context.GroupId == "MySettingsGroup")
        {
            var model = new MySettingsViewModel();

            // 从提交的编辑表单中读取视图模型的值
            await context.Updater.TryUpdateModelAsync(model, Prefix);

            if (context.Updater.ModelState.IsValid)
            {
                // 如果模型验证通过
                // 则将视图模型的值，保存到自定义设置中。
                settings.Host = model.Host;
                settings.ContentType = model.ContentType;
                settings.Account = model.Account;
                settings.Key = model.Key;
                settings.KeyEncrypted = model.KeyEncrypted;
                settings.CheckIp = model.CheckIp;
                settings.AgencyId = model.AgencyId;

                // 重新加载租户配置
                await _shellHost.ReleaseShellContextAsync(_shellSettings);
            }
        }

        return await EditAsync(settings, context);
    }
}

```

注入服务集合

```c#
public class Startup : StartupBase
{
    public override void ConfigureServices(IServiceCollection services)
    {
        // 注入服务
        services.AddScoped<IDisplayDriver<ISite>, MySettingsDisplayDriver>();

        // 最后还需要为自定义设置配置一个 Admin 菜单，这样才能在 Admin 中进行编辑。
        services.AddScoped<INavigationProvider, AdminMenu>();
    }

    public override void Configure(IApplicationBuilder builder, IEndpointRouteBuilder routes, IServiceProvider serviceProvider)
    {
        
    }
}
```

添加管理菜单

```c#
public class AdminMenu : INavigationProvider
{
    private IStringLocalizer S { get; }

    public AdminMenu(IStringLocalizer<AdminMenu> localizer)
    {
        S = localizer;
    }

    public Task BuildNavigationAsync(string name, NavigationBuilder builder)
    {
        if (string.Equals(name, "admin", StringComparison.OrdinalIgnoreCase))
        {
            builder.Add(S["Configuration"], configuration => configuration
                    .Add(S["MySettings"], S["MySettings"].PrefixPosition(), settings => settings
                        .Action("Index", "Admin", new { area = "OrchardCore.Settings", groupId = "MySettingsGroup" })
                        .LocalNav())
                ));
        }

        return Task.CompletedTask;
    }
}
```

## 在 Admin 中创建

相比编程方式创建 CustomSettings，此方法会简单很多。

具体如下：
1. 创建一个内容类型 MySettings
2. 将 Stereotype（构造型）设置为 CustomSettings
3. 添加需要的字段
4. 保存即可

此方法是将 CustomSettings 当作 ContentItem（内容项）进行存储，
因此在 GraphiQL 的 ContentItems 查询中能看到 MySettings。