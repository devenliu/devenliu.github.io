---
title: .NET 面试问答 | ASP.NET 面试问答
date: 2022-06-14 12:25:16
categories: 
- .NET
tags: 
- .NET
- C#
- ASP.NET
---
整理的关于 .NET Framework 和 ASP.NET 的一些面试问答。
<!-- more -->

# 一、初级问题

## 01) 什么是 .NET Framework？

.NET Framework 支持用于在 Windows 上构建应用程序的面向对象的方法。 
它支持各种语言，如 C#、VB、Cobol、Perl、.NET 等。
它具有多种工具和功能，如用于构建、部署和运行 Web 服务和不同应用程序的类、库和 API。

## 02) .NET Framework 有哪些不同的组件？

- Common Language Runtime
- Application Domain （.NET Framework only）
- Common Type System
- .NET Class Library
- .NET Framework / .NET Core
- Profiling

## 03) 你对 CTS 了解多少？

CTS代表通用类型系统（Common Type System）。
它遵循一定的规则，数据类型应该根据这些规则在程序代码中声明和使用。
CTS还描述了将在应用程序中使用的数据类型。
我们甚至可以按照CTS中的规则创建自己的类和函数，它有助于调用其他编程语言在一种编程语言中声明的数据类型。

## 04) 什么是 CLR？

CLR 代表 Common Language Runtime它是 .NET Framework 的重要组成部分。 
我们可以将 CLR 用作各种应用程序的构建块，并为应用程序提供安全的执行环境。
每当编译用 C# 编写的应用程序时，代码都会转换为中间语言。 在此之后，代码以 CLR 为目标，然后执行多项操作，如内存管理、安全检查、加载程序集和线程管理。

## 05) 解释一下 CLS

CLS 代表通用语言规范（Common Language Specification）。
它帮助开发人员使用与 CLS 附带的某些规则的跨语言兼容的组件。
然后，它有助于在其他 .NET 兼容语言中重用代码。

## 06) 你对 JIT 了解多少？

JIT 是一个编译器，代表 Just In Time。
它用于将中间代码转换为本地语言。
在执行期间，中间代码被转换为本地语言。

## 07) 为什么要使用 Response.Output.Write()?

Response.Output.Write() 用于获取格式化输出。

## 08) Response.Redirect 和 Server.Transfer 有什么区别？

Response.Redirect：
Response.Redirect 基本上是将用户的浏览器重定向到另一个页面或站点。
用户浏览器的历史记录也会更新以反映新地址。
它还执行返回客户端的行程，客户端的浏览器被重定向到新页面。

Server.Transfer：
然而，Server.Transfer 从一个页面传输到另一个页面，而不需要返回客户端的浏览器。
在 Server.Transfer 的情况下，历史记录不会更新。

## 09) 托管代码和非托管代码的区别？

托管代码（Managed code）：
- 托管代码由 CLR 管理
- .NET Framework 是执行托管代码所必需的
- CLR 通过垃圾回收（Garbage Collection）管理内存管理

非托管代码（Unmanaged code）：
- 任何不受 CLR 管理的代码
- 独立于 .NET Framework
- 拥有用于执行和编译的运行时环境

## 10) 类和对象的区别？

类（Class）：
- 类是对象的定义
- 是对象的模板
- 描述了所有的方法，属性等

对象（Object）：
- 对象是类的实例
- 除非实例化，否则类不会成为对象
- 对象访问类的所有属性

## 11) 你对装箱和拆箱了解多少？

装箱（Boxing）：
- 隐式的
- 将值类型转换为类型对象的过程
- 例如 - object myObj = a ;

拆箱（Unboxing）：
- 明确的
- 从对象中提取值类型的过程
- 例如 - int a = (int) myObj ;

## 12) 常量和只读变量的区别？

常量（const）：
- 在编译时评估
- 仅支持值类型变量
- 在编译时值不变时使用
- 不能在构造函数或声明中初始化

只读变量（readonly）：
- 在运行时评估
- 可以保存引用类型变量
- 在运行时之前实际值未知时使用
- 能在构造函数或声明中初始化

 ## 13) 什么是 BCL？

- BCL（Base Class Library），是类、接口和值类型的基类库。
- 它是 .NET Framework 应用程序、组件和控件的基础
- 封装了大量常用功能，方便开发人员使用
- 它提供线程、输入/输出、安全、诊断、资源、全球化等功能
- 还用于用户和运行时之间的交互目的
- 它还提供了经常使用的命名空间。 例如：System，System.Activities 等。

## 14) .NET 有哪些不同版本？

- .NET Framework 1.0 / 1.1
- .NET Framework 2.0
- .NET Framework 3.0 / 3.5
- .NET Framework 4.0 / 4.5 / 4.6 / 4.7 / 4.8
- .NET Core 1.0 / 1.1
- .NET Core 2.0 / 2.1
- .NET Core 3.0 / 3.1
- .NET 5
- .NET 6

## 15) 命名空间和程序集有什么区别？

程序集（Assembly）是逻辑单元的物理分组，而命名空间（Namespace）对类进行分组。 
此外，一个命名空间也可以跨越多个程序集。

## 16) 什么是 LINQ？

LINQ 代表语言集成查询（Lanuage Integrated Query）。

- 它是 Visual Studio 2008 引入的语言集成查询的首字母缩写词。
- LINQ 是一组功能，可将查询功能扩展到 .NET Framework 语言语法，允许在不考虑数据源的情况下进行数据操作
- LINQ 弥合了对象世界和数据世界之间的鸿沟


## 17) 什么是 MSIL？

MSIL 是微软中间语言（Microsoft Intermediate Language），它提供了调用方法、存储和初始化值、内存处理、异常处理等的指令。
所有 .NET 代码首先编译为中间语言。

## 18) 所有 Web 窗体都继承自哪个基类？
Page 类


# 二、中等问题

## 19) 解释程序集的不同部分？

清单（MANIFEST）：
包含有关程序集版本的信息。

类型元数据（TYPE METADATA）：
包含程序的二进制信息。

中间语言（MSIL）：
中间语言代码。

资源（RESOURCES）：
相关文件列表。

## 20) 如何防止类被继承？

在 C# 中，我们可以使用 sealed 关键字来防止类被继承。


## 21) C# 中有哪些不同类型的构造函数？

默认的：
如果未显示提供构造函数，则由编译器生成默认的无参数构造函数。

参数化的：
只要构造函数具有至少1个参数，就是参数化的构造函数。

副本：
在构造函数中接受另一个对象作为参数，并用其属性来初始化自身的属性。

静态：
没有访问修饰符，没有任何参数，由 CLR 自动执行，可初始化静态成员。

私有：
使用了 private 访问修饰符，用于防止通过 new 关键字进行实例化。
例如：可实现单例类。

## 22) 有哪些不同类型的程序集？

私有的：
只能由应用程序访问。
安装在应用程序的安装目录中。

共享的：
可以由多个应用程序共享。
安装在 GAC 中。


## 23) 什么是 MDI 和 SDI？

MDI（Multiple Document Interface）：
MDI 允许您打开多个窗口。
它将有一个父窗口和尽可能多的子窗口。
组件从父窗口共享，如菜单栏、工具栏等。

SDI（Single Document Interface）：
在单独的窗口中打开每个文档。
每个窗口都有自己的组件，如菜单栏、工具栏等。
因此它不受父窗口的限制。

## 24) 区分自定义控件和用户控件？

自定义控件（Custom Control）：
- 派生自 Control
- 动态布局
- 定义单个控件
- 有完整的工具箱支持

用户控件（User Control）：
- 派生自 UserControl
- 静态布局
- 定义一组控件
- 无法添加到工具箱


## 25) 什么是垃圾收集器？

.NET 中的垃圾收集器（Garbage Collector）功能释放内存中未使用的代码对象。

内存堆分为3代：

- 第 0 代（Generation 0）
存储短生存期的对象

- 第 1 代（Generation 1）
存储中等生存期的对象

- 第 2 代（Generation 2）
存储长生存期的对象


另外，内存堆也分为小型对象堆（SOH）和一个大型对象堆（LOH）。
小型对象堆完全符合上述的 3 代回收机制，
而这个大型对象堆略有不同，它在第 0 代被设置，只与第 2 代同时回收。

## 26) 什么是缓存？

缓存只是意味着将数据临时存储在内存中，以便可以从内存中访问数据，而不是在原始位置搜索它。 它提高了应用程序的效率，也提高了它的速度。

- 页面缓存（Page Caching）
可以帮助改善网页加载时间，从而为搜索引擎优化您的网站。 
页面加载时间会显着影响您的用户体验以及您的网站将访问者转化为买家或潜在客户的能力。

- 数据缓存（Data Caching）
缓存是一种在内存中存储常用数据或信息的技术。
当下次需要相同的数据或信息时，可以直接从内存中检索，而不是由应用程序生成。

- 片段缓存（Fragment Caching）
片段缓存实际上是指在 Web 表单中缓存单个用户控件。
每个用户控件可以有独立的缓存持续时间和如何应用缓存行为的实现。
当您只需要缓存页面的子集时，片段缓存很有用。


## 解释一下 MVC

MVC 代表模型视图控制器（Model View Controller）。
它是构建 .NET 应用程序的架构。

模型（Model）：
Model基本上是处理对象存储和从应用程序的数据库检索的任何应用程序的逻辑部分。

视图（View）：
View处理应用程序的 UI 部分，即用户界面。
因此它们从模型中获取信息以进行展示。

控制器（Controller）：
Controller 处理用户交互，从用户输入中找出响应，并呈现用户交互所需的视图。

## 28) 什么是 CAS?

CAS表示代码访问安全性（Code Access Security）。
CAS是安全模型的一部分，用于防止对资源的未授权访问。
它还允许用户设置代码的权限。CLR然后根据权限执行代码。

CAS只能用于托管代码。
如果程序集使用CAS，则将其视为部分受信任的。
尽管每次程序集试图访问资源时，它都会执行检查。

## 29) 解释一下本地化和全球化

本地化（Localization）：
这意味着改变已经全球化的应用程序以适应特定的语言或文化。
Microsoft.Extension.Localization 用于本地化应用程序内容。

全球化（Globalization）：
全球化是开发支持多种语言的应用程序的过程。
还可以将现有的应用程序转换为支持多种语言。

## 30) 什么是应用程序域？

ASP.NET 引入了一个应用程序域概念或 AppDomain，它就像一个轻量级进程，既像容器又像边界。

.NET 运行时使用 AppDomain 作为数据和代码的容器。CLR 允许多个 .NET 应用程序在单个 AppDomain 中运行。

## 31) .NET中的委托是什么?

.NET 中的委托（delegate）类似于其他编程语言（如 C 或 C++）中的函数指针。
委托允许用户将方法的引用封装在委托对象中。
可以在程序中传递委托对象，该程序将调用引用的方法。
我们可以使用委托方法在类中创建自定义事件。

## 32) .NET 中抽象类和接口的区别？

抽象类（abstact class）：
抽象类为必须由继承实体实现的功能提供了部分实现。
抽象类也声明字段。

接口（interface）：
接口仅声明实现类应具有的契约或行为。
接口只能声明没有访问修饰符的属性、方法和事件。

## 33) 区分栈和堆？

栈（Stack）：
- 静态内存分配
- 存储值类型
- 跟踪每个线程及其位置

堆（Heap）：
- 动态内存分配
- 存储引用类型
- 跟踪更精确的对象或数据

## 34) ASP.NET 中有哪些不同的验证器?

客户端验证（Client-side validation）：
当在客户端浏览器上进行验证时，它被称为客户端验证。通常，JavaScript用于客户端验证。

服务端验证（Server-side validation）：
当在服务器上进行验证时，就称为服务器端验证。
服务器端验证被认为是一种安全的验证形式，因为即使用户绕过了客户端验证，我们仍然可以在服务器端验证中捕捉到它。


# 三、高级问题

## 35) 什么是 EXE 和 DLL？

EXE：
它是一个可执行文件，可运行为其设计的应用程序。
当我们构建应用程序时，会生成一个 exe 文件。 
因此，程序集在我们运行 exe 时直接加载。 
但是exe文件不能与其他应用程序共享。

DLL：
它代表由需要隐藏的代码组成的动态链接库。 
代码封装在这个库中，一个应用程序可以有很多DLL，也可以与其他应用程序共享。

## 36) 区分函数和存储过程？

函数（Fucntion）：
- 必须返回单个值
- 它只能有输入参数
- 无法使用try catch块进行异常处理
- 无法从函数调用存储过程

存储过程（Stored Procedure）：
- 总是用于执行特定任务
- 可以同时具有输入或输出参数
- 可以使用try catch块进行异常处理
- 可以从存储过程中调用函数

## 列出 ASP.NET 页面的生命周期事件。

Page_PreInit
Page_Init
Page_InitComplete
Page_PreLoad
Page_Load
Page_LoadComplete
Page_PreRender
Render


## 38) 从 ASP.NET 应用程序发送电子邮件的代码是什么？

Mail msg = new Mail();
msg.From = "abc@gmail.com";
msg.To = "xyz@gmail.com";
msg.Subject = "test";
msg.Body = "hello";

SmtpMail.SmtpServer = "localhost";
SmtpMail.Send(msg);

以上代码无法运行，属于伪代码

## 39) ASP.NET 中 Global.asax 文件有哪些事件处理程序？

Application_Start
Application_End
Application_AuthenticatedRequest
Application_AuthorizeRequest
Application_BeginRequest
Application_Disposed
Application_EndRequest
Application_Error
Application_PostRequestHandlerExecute
Application_PreRequestHandlerExecute
Application_PreSendRequestContent
Application_PreSendRequestHeader
Application_ReleaseRequestState
Application_ResolveRequestCache
Application_UpdateRequestCache


## 40) 解释一下基于角色的安全性

基于角色的安全性是指根据组织中分配给用户的角色来实施安全措施。
然后根据用户在组织中的角色对其进行授权。
例如，Windows 具有基于角色的访问权限，例如用户、管理员和来宾。

## 41) 什么是跨页公布？

cross-page posting：
- 每当我们单击页面上的提交按钮时，数据都存储在同一个页面上。但如果数据存储在不同的页面上，则称为跨页面发布。
- 跨页发布可以通过导致回发的 POSTBACKURL 属性实现。
- FindControl 方法可用于获取该页面已发布到的该页面上发布的值。

## 42) 如何将主题应用于 ASP.NET 应用程序？

下面是更改主题的代码：

<configuration>
    <system.web>
        <pages theme="windows" />
    </system.web>
</configuration>

## 43) 解释护照认证
在护照认证期间，它首先检查护照认证cookie，如果cookie不可用，应用程序将重定向到护照登录页面。 Passport 服务然后在登录页面上验证用户的详细信息，如果它们有效，则将它们存储在客户端计算机上，然后将用户重定向到请求的页面。

## 44) 什么是 ASP.NET 安全控件？

<asp:Login>
<asp:LoginName>
<asp:LoginStatus>
<asp:LoginView>
<asp:PasswordRecovery>

## 45) 列出 ASP.NET 转发器控件的所有模板？

ItemTemplate
AlternatingItemTemplate
SeparatorTemplate
HeaderTemplate
FooterTemplate

## 46) web.config 文件中的 appSettings 部分是什么？

<configuration>
    <appsettings>
        <add key="ConnectionString" value="xxxxxx" />
    </appsettings>
</configuration>

web.config 文件中的 appsettings 部分是 web 应用程序的自定义配置

## 47) 什么是 MIME？

MIME 代表多用途互联网邮件扩展（multipurpose internet mail extensions）。
它是电子邮件协议的扩展，允许用户使用该协议在互联网上交换文件。
服务器在我们传输的开头插入 MIME 标头。 
然后客户端使用此标头为标头指示的数据类型选择适当的“播放器”。
其中一些播放器内置于网络浏览器中。

## 48) 什么是 HTTP handler?

对 ASP.NET 应用程序的每个请求都由一个称为 HTTP 处理程序的专用组件处理。
它是处理 ASP.NET 应用程序请求的最重要的组件。
它使用不同的处理程序来处理不同的文件。 
网页处理程序创建页面和控件对象，运行您的代码，然后呈现最终的 HTML。

- Page Handler (.aspx)：处理 web 页面
- User Control Handler (.ascx)：处理 web 用户控件页面
- Web Service Handler (.asmx)：处理 web 服务页面
- Trace Handler (trace.axd)：处理跟踪功能

## 49) ASP.NET 中有哪些不同类型的 Cookie？

会话 Cookie（Session cookie）：
对于单个会话，它驻留在客户端机器上，直到用户注销。

持久性 Cookie（Persistent cookie）：
在指定的期限内驻留在用户计算机上。可能是一个小时，一个月或永远不会。

## 50) 区分 ExecuteScalar 和 ExecuteNonQuery？

ExecuteScalar：
- 返回输出值
- 用于获取单个值
- 不返回受影响的行数

ExecuteNonQuery：
- 不返回任何值
- 用于执行插入和更新语句
- 返回受影响的行数


# 相关视频
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/5WwzmjgmqUA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>