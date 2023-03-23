# Blazor
## Blazor Server File
### 1. Project File `.csproj`
- Framework version `<TargetFramework>net6.0</TargetFramework>`
- Nullable `<Nullable>enable</Nullable>`
- Library Using Statement; help us to enable using statement for all libraries `<ImplicitUsings>enable</ImplicitUsings>`

### 2. Properties/ Lunch Settings `.json`
Contains all the properties of project.

### 3. Static File
Only the files in the `wwwroot` folder are web-addressable. This folder is referred to as the app’s “web root”. Anything outside of the app’s web root isn’t web-addressable. This setup provides an additional level of security that prevents accidental exposure of project files over the web  
### 4. Pages
Pages are defined by assigning routes to components. A route is typically assigned using the `@page Razor` directive. Routing in Blazor is handled client-side, not on the server. As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route. Each route must be specified explicitly on the component.
`.cshtml` : Razor Pages 
`.razor` : Razor Component (make up the UI of the app)
**Razor Components**  
Components in Blazor are analogous to user controls in ASP.NET Web Forms. Each Razor component file is compiled into a .NET class when the project is built. The generated class captures the component’s state, rendering logic, lifecycle methods, event handlers, and other logic. It's like global directive for all the pages.

The `_Imports.razor` files aren’t Razor component files. Instead, they define a set of Razor directives to import into other `.razor` files within the same folder and in its subfolders.

    @using System.Net.Http 
    @using Microsoft.AspNetCore.Authorization
    @using Microsoft.AspNetCore.Components.Authorization
    @using Microsoft.AspNetCore.Components.Forms
    @using Microsoft.AspNetCore.Components.Routing
    @using Microsoft.AspNetCore.Components.Web
    @using Microsoft.AspNetCore.Components.Web.Virtualization
    @using Microsoft.JSInterop
    @using BlazorServer_TangyWeb
    @using BlazorServer_TangyWeb.Shared
### 5. Router component
Routing in Blazor is handled by the Router component. The *Router* component is typically used in the app’s root component (`App.razor`).
The Router component discovers the routable components in the specified `AppAssembly` and in the optionally specified `AdditionalAssemblies`. When the browser navigates, the Router intercepts the navigation and renders the contents of its `Found` parameter with the extracted `RouteData` if a route matches the address, otherwise the Router renders its `NotFound` parameter. 
The `RouteView` component handles rendering the matched component specified by the `RouteData` with its layout if it has one. If the matched component doesn’t have a layout, then the optionally specified `DefaultLayout` is used. 
The `LayoutView` component renders its child content within the specified layout.
### 6.  Configuration
Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don’t currently support the same configuration abstractions, but that may be a feature added in the future). the default Blazor Server app stores some settings in `appsettings.json`.

    { "Logging": { "LogLevel": { "Default": "Information", "Microsoft": "Warning", "Microsoft.Hosting.Lifetime": "Information" } }, "AllowedHosts": "*" }
  
 ### 7. Entry Point
 The Blazor Server app’s entry point is defined in the `Program.cs` file.  
In a **Blazor Server** app, the `Program.cs` file shown is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server. In a **Blazor WebAssembly** app, the `Program.cs` file defines the root components for the app and where they should be rendered. 

In the Blazor Server app, the root component’s host page is defined in the `_Host.cshtml` file. This file defines a Razor Page, not a component. The `render-mode` attribute is used to define where a root-level component should be rendered. The `RenderMode` option indicates the manner in which the component should be rendered. 
|Options| Description |
|--|--|
| RenderMode.ServerPrerendered | First prerendered and then rendered interactively |
|RenderMode.Static|Rendered as static content|
|RenderMode.Server|Rendered interactively once a connection with the browser is established|

The `_Layout.cshtml` file includes the default HTML for the app and its components.

### 8. App startup
Routing in Blazor is handled by the *Router* component. The *Router* component is typically used in the app’s root component (`App.razor`).

## Project Operations

 - File & Folder Overview in Blazor
 - Blazor Server & Client Application
 - Data Binding
 - Components & Routing
 - Parameters/ Cascading Parameters
 - JacaScript in Blazor
 - Render fragment, attribute splatting
 - Toastr & Sweet alert integration
 - Blazor Lifecycles
 - CRUD Operation
