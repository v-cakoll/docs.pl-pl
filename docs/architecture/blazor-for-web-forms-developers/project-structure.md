---
title: Struktura projektu dla aplikacji Blazor
description: Dowiedz się, jak porównywane są struktury projektów ASP.NET Web Forms i Blazor.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 2c383e86ff22f5a3460476998992b66e9417cc11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401579"
---
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="844b0-103">Struktura projektu dla aplikacji Blazor</span><span class="sxs-lookup"><span data-stu-id="844b0-103">Project structure for Blazor apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="844b0-104">Pomimo znacznych różnic w strukturze projektu, ASP.NET Web Forms i Blazor mają wiele podobnych koncepcji.</span><span class="sxs-lookup"><span data-stu-id="844b0-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="844b0-105">Tutaj przyjrzymy się strukturze projektu Blazora i porównamy go z projektem ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="844b0-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="844b0-106">Aby utworzyć pierwszą aplikację Blazor, postępuj zgodnie z instrukcjami w [krokach rozpoczęcia pracy blazora.](/aspnet/core/blazor/get-started)</span><span class="sxs-lookup"><span data-stu-id="844b0-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="844b0-107">Możesz postępować zgodnie z instrukcjami, aby utworzyć aplikację Blazor Server lub aplikację Blazor WebAssembly hostowane w ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="844b0-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="844b0-108">Z wyjątkiem logiki specyficzne dla modelu hostingu, większość kodu w obu projektach jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="844b0-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="844b0-109">Plik projektu</span><span class="sxs-lookup"><span data-stu-id="844b0-109">Project file</span></span>

<span data-ttu-id="844b0-110">Aplikacje Blazor Server to projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="844b0-110">Blazor Server apps are .NET Core projects.</span></span> <span data-ttu-id="844b0-111">Plik projektu dla aplikacji Blazor Server jest tak prosty, jak to tylko możliwe:</span><span class="sxs-lookup"><span data-stu-id="844b0-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="844b0-112">Plik projektu dla aplikacji Blazor WebAssembly wygląda nieco bardziej zaangażowany (dokładne numery wersji mogą się różnić):</span><span class="sxs-lookup"><span data-stu-id="844b0-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <RazorLangVersion>3.0</RazorLangVersion>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Blazor" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.Build" Version="3.1.0" PrivateAssets="all" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.HttpClient" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.DevServer" Version="3.1.0" PrivateAssets="all" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\Shared\BlazorWebAssemblyApp1.Shared.csproj" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="844b0-113">Projekty Blazor WebAssembly są przeznaczone dla standardu .NET zamiast .NET Core, ponieważ są uruchamiane w przeglądarce w czasie wykonywania platformy WebAssembly opartej na ustom .NET.</span><span class="sxs-lookup"><span data-stu-id="844b0-113">Blazor WebAssembly projects target .NET Standard instead of .NET Core because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="844b0-114">Nie można zainstalować programu .NET w przeglądarce sieci Web, tak jak na serwerze lub komputerze dewelopera.</span><span class="sxs-lookup"><span data-stu-id="844b0-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="844b0-115">W związku z tym projekt odwołuje się do struktury Blazor przy użyciu poszczególnych odwołań do pakietów.</span><span class="sxs-lookup"><span data-stu-id="844b0-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="844b0-116">Dla porównania, domyślny projekt ASP.NET Web Forms zawiera prawie 300 wierszy XML w pliku *csproj,* z których większość jawnie wyświetla listę różnych plików kodu i zawartości w projekcie.</span><span class="sxs-lookup"><span data-stu-id="844b0-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="844b0-117">Wiele uproszczeń w projektach opartych na standardzie .NET Core i .NET pochodzi z domyślnych `Microsoft.NET.Sdk.Web` obiektów docelowych i właściwości importowanych przez odwoływanie się do sdk, często określanego jako po prostu internetowy zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="844b0-117">Many of the simplifications in the .NET Core- and .NET Standard-based projects come from the default targets and properties imported by referencing the `Microsoft.NET.Sdk.Web` SDK, often referred to as simply the Web SDK.</span></span> <span data-ttu-id="844b0-118">Internetowy zestaw SDK zawiera symbole wieloznaczne i inne udogodnienia, które upraszczają dołączanie do projektu plików kodu i zawartości.</span><span class="sxs-lookup"><span data-stu-id="844b0-118">The Web SDK includes wildcards and other conveniences that simplify inclusion of code and content files in the project.</span></span> <span data-ttu-id="844b0-119">Nie trzeba jawnie wyświetlać listę plików.</span><span class="sxs-lookup"><span data-stu-id="844b0-119">You don't need to list the files explicitly.</span></span> <span data-ttu-id="844b0-120">Podczas określania wartości docelowej .NET Core, web SDK dodaje również odwołania do struktury platformy .NET Core i ASP.NET Core udostępnionych.</span><span class="sxs-lookup"><span data-stu-id="844b0-120">When targeting .NET Core, the Web SDK also adds framework references to both the .NET Core and ASP.NET Core shared frameworks.</span></span> <span data-ttu-id="844b0-121">Struktury są widoczne z węzła**Struktury** **zależności** > w oknie **Eksploratora rozwiązań.**</span><span class="sxs-lookup"><span data-stu-id="844b0-121">The frameworks are visible from the **Dependencies** > **Frameworks** node in the **Solution Explorer** window.</span></span> <span data-ttu-id="844b0-122">Struktury udostępnione są kolekcje zestawów, które zostały zainstalowane na komputerze podczas instalowania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="844b0-122">The shared frameworks are collections of assemblies that were installed on the machine when installing .NET Core.</span></span>

<span data-ttu-id="844b0-123">Mimo że są one obsługiwane, poszczególne odwołania do zestawu są mniej typowe w projektach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="844b0-123">Although they're supported, individual assembly references are less common in .NET Core projects.</span></span> <span data-ttu-id="844b0-124">Większość zależności projektu są obsługiwane jako odwołania nuget pakietu.</span><span class="sxs-lookup"><span data-stu-id="844b0-124">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="844b0-125">W projektach programu .NET Core należy odwoływać się tylko do zależności od zależności pakietów najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="844b0-125">You only need to reference top-level package dependencies in .NET Core projects.</span></span> <span data-ttu-id="844b0-126">Zależności przechodnie są uwzględniane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="844b0-126">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="844b0-127">Zamiast używać pliku *packages.config* powszechnie spotykanego w projektach ASP.NET Web Forms do odwoływania `<PackageReference>` się do pakietów, odwołania do pakietów są dodawane do pliku projektu przy użyciu elementu.</span><span class="sxs-lookup"><span data-stu-id="844b0-127">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="844b0-128">Punkt wejścia</span><span class="sxs-lookup"><span data-stu-id="844b0-128">Entry point</span></span>

<span data-ttu-id="844b0-129">Punkt wejścia aplikacji Blazor Server jest zdefiniowany w *pliku Program.cs,* jak widać w aplikacji Konsola.</span><span class="sxs-lookup"><span data-stu-id="844b0-129">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="844b0-130">Gdy aplikacja jest wykonywana, tworzy i uruchamia wystąpienie hosta sieci web przy użyciu ustawień domyślnych specyficznych dla aplikacji sieci web.</span><span class="sxs-lookup"><span data-stu-id="844b0-130">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="844b0-131">Host internetowy zarządza cyklem życia aplikacji Blazor Server i konfiguruje usługi na poziomie hosta.</span><span class="sxs-lookup"><span data-stu-id="844b0-131">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="844b0-132">Przykładami takich usług są konfiguracja, rejestrowanie, wstrzykiwanie zależności i serwer HTTP.</span><span class="sxs-lookup"><span data-stu-id="844b0-132">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="844b0-133">Kod ten jest w większości standardowy i często pozostaje bez zmian.</span><span class="sxs-lookup"><span data-stu-id="844b0-133">This code is mostly boilerplate and is often left unchanged.</span></span>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

<span data-ttu-id="844b0-134">Aplikacje Blazor WebAssembly definiują również punkt wejścia w *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="844b0-134">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="844b0-135">Kod wygląda nieco inaczej.</span><span class="sxs-lookup"><span data-stu-id="844b0-135">The code looks slightly different.</span></span> <span data-ttu-id="844b0-136">Kod jest podobny, ponieważ konfiguruje hosta aplikacji w celu świadczenia tych samych usług na poziomie hosta dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="844b0-136">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="844b0-137">Host aplikacji WebAssembly nie konfiguruje jednak serwera HTTP, ponieważ jest wykonywany bezpośrednio w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="844b0-137">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="844b0-138">Aplikacje Blazor `Startup` mają klasę zamiast pliku *Global.asax,* aby zdefiniować logikę uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="844b0-138">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="844b0-139">Klasa `Startup` służy do konfigurowania aplikacji i dowolnych usług specyficznych dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="844b0-139">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="844b0-140">W aplikacji Blazor Server `Startup` klasa jest używana do konfigurowania punktu końcowego dla połączenia w czasie rzeczywistym używanego przez Blazora między przeglądarkami klienta a serwerem.</span><span class="sxs-lookup"><span data-stu-id="844b0-140">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="844b0-141">W aplikacji Blazor WebAssembly `Startup` klasa definiuje składniki główne aplikacji i gdzie powinny być renderowane.</span><span class="sxs-lookup"><span data-stu-id="844b0-141">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="844b0-142">Przyjrzymy się głębiej `Startup` klasie w sekcji [uruchamiania aplikacji.](./app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="844b0-142">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="844b0-143">Pliki statyczne</span><span class="sxs-lookup"><span data-stu-id="844b0-143">Static files</span></span>

<span data-ttu-id="844b0-144">W przeciwieństwie do projektów ASP.NET Web Forms, nie wszystkie pliki w projekcie Blazor mogą być wymagane jako pliki statyczne.</span><span class="sxs-lookup"><span data-stu-id="844b0-144">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="844b0-145">Tylko pliki w folderze *wwwroot* można adresować w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="844b0-145">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="844b0-146">Ten folder jest określany jako "katalog główny sieci Web" aplikacji.</span><span class="sxs-lookup"><span data-stu-id="844b0-146">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="844b0-147">Wszystko poza katalogiem głównym aplikacji *nie jest* adresowalne w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="844b0-147">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="844b0-148">Ta konfiguracja zapewnia dodatkowy poziom zabezpieczeń, który zapobiega przypadkowemu ujawnieniu plików projektu w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="844b0-148">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="844b0-149">Konfigurowanie</span><span class="sxs-lookup"><span data-stu-id="844b0-149">Configuration</span></span>

<span data-ttu-id="844b0-150">Konfiguracja w aplikacjach ASP.NET formularzy sieci Web jest zazwyczaj obsługiwana przy użyciu jednego lub większej liczby plików *web.config.*</span><span class="sxs-lookup"><span data-stu-id="844b0-150">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="844b0-151">Aplikacje Blazor zazwyczaj nie mają plików *web.config.*</span><span class="sxs-lookup"><span data-stu-id="844b0-151">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="844b0-152">Jeśli tak, plik jest używany tylko do konfigurowania ustawień specyficznych dla usług IIS, gdy są hostowane w usianych przez usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="844b0-152">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="844b0-153">Zamiast tego aplikacje Blazor Server używają abstrakcji konfiguracji ASP.NET Core (aplikacje Blazor WebAssembly nie obsługują obecnie tych samych abstrakcji konfiguracji, ale może to być funkcja dodana w przyszłości).</span><span class="sxs-lookup"><span data-stu-id="844b0-153">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="844b0-154">Na przykład domyślna aplikacja Blazor Server przechowuje niektóre ustawienia w *appsettings.json*.</span><span class="sxs-lookup"><span data-stu-id="844b0-154">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

<span data-ttu-id="844b0-155">Dowiemy się więcej o konfiguracji w ASP.NET projektów podstawowych w [sekcji Konfiguracja.](./config.md)</span><span class="sxs-lookup"><span data-stu-id="844b0-155">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="844b0-156">Elementy maszynki do golenia</span><span class="sxs-lookup"><span data-stu-id="844b0-156">Razor components</span></span>

<span data-ttu-id="844b0-157">Większość plików w projektach Blazor a *plikami .brzytwa.*</span><span class="sxs-lookup"><span data-stu-id="844b0-157">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="844b0-158">Razor jest językiem szablonów opartym na html i C#, który jest używany do dynamicznego generowania interfejsu użytkownika w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="844b0-158">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="844b0-159">*Pliki .brzytwa* definiują składniki, które tworzą interfejsu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="844b0-159">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="844b0-160">W przeważającej części składniki są identyczne zarówno dla blazor server i Blazor WebAssembly aplikacji.</span><span class="sxs-lookup"><span data-stu-id="844b0-160">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="844b0-161">Składniki w blazorze są analogiczne do formantów użytkownika w ASP.NET formularzach sieci Web.</span><span class="sxs-lookup"><span data-stu-id="844b0-161">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="844b0-162">Każdy plik składnika Razor jest kompilowany do klasy .NET, gdy projekt jest zbudowany.</span><span class="sxs-lookup"><span data-stu-id="844b0-162">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="844b0-163">Wygenerowana klasa przechwytuje stan składnika, logikę renderowania, metody cyklu życia, programy obsługi zdarzeń i inną logikę.</span><span class="sxs-lookup"><span data-stu-id="844b0-163">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="844b0-164">Przyjrzymy się tworzeniu komponentów w [sekcji Building wielokrotnego użytku z blazorem.](./components.md)</span><span class="sxs-lookup"><span data-stu-id="844b0-164">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="844b0-165">Pliki *_Imports.razor* nie są plikami komponentu Razor.</span><span class="sxs-lookup"><span data-stu-id="844b0-165">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="844b0-166">Zamiast tego definiują zestaw dyrektyw Razor do zaimportowania do innych plików *.razor* w tym samym folderze i w jego podfolderach.</span><span class="sxs-lookup"><span data-stu-id="844b0-166">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="844b0-167">Na przykład plik *_Imports.razor* jest konwencjonalnym `using` sposobem dodawania instrukcji dla często używanych obszarów nazw:</span><span class="sxs-lookup"><span data-stu-id="844b0-167">For example, a *_Imports.razor* file is a conventional way to add `using` statements for commonly used namespaces:</span></span>

```razor
@using System.Net.Http
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.JSInterop
@using BlazorApp1
@using BlazorApp1.Shared
```

## <a name="pages"></a><span data-ttu-id="844b0-168">Strony</span><span class="sxs-lookup"><span data-stu-id="844b0-168">Pages</span></span>

<span data-ttu-id="844b0-169">Gdzie są strony w aplikacjach Blazor?</span><span class="sxs-lookup"><span data-stu-id="844b0-169">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="844b0-170">Blazor nie definiuje oddzielnego rozszerzenia pliku dla adresowalnych stron, takich jak pliki *.aspx* w aplikacjach ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="844b0-170">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="844b0-171">Zamiast tego strony są definiowane przez przypisywanie tras do komponentów.</span><span class="sxs-lookup"><span data-stu-id="844b0-171">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="844b0-172">Trasa jest zazwyczaj przypisana przy użyciu dyrektywy `@page` Razor.</span><span class="sxs-lookup"><span data-stu-id="844b0-172">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="844b0-173">Na przykład `Counter` komponent, który jest autorem pliku *Pages/Counter.razor,* definiuje następującą trasę:</span><span class="sxs-lookup"><span data-stu-id="844b0-173">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="844b0-174">Routing w Blazor jest obsługiwany po stronie klienta, a nie na serwerze.</span><span class="sxs-lookup"><span data-stu-id="844b0-174">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="844b0-175">Gdy użytkownik nawiguje w przeglądarce, Blazor przechwytuje nawigację, a następnie renderuje komponent z pasującą trasą.</span><span class="sxs-lookup"><span data-stu-id="844b0-175">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="844b0-176">Trasy składników nie są obecnie wywnioskowane przez lokalizację pliku składnika, tak jak w nich znajdują się w odniesieniu do stron *.aspx.*</span><span class="sxs-lookup"><span data-stu-id="844b0-176">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="844b0-177">Ta funkcja może zostać dodana w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="844b0-177">This feature may be added in the future.</span></span> <span data-ttu-id="844b0-178">Każda trasa musi być określona jawnie na składniku.</span><span class="sxs-lookup"><span data-stu-id="844b0-178">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="844b0-179">Przechowywanie składników routingu w folderze *Strony* nie ma specjalnego znaczenia i jest wyłącznie konwencją.</span><span class="sxs-lookup"><span data-stu-id="844b0-179">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="844b0-180">Przyjrzymy się bardziej szczegółowo routingu w Blazor w [sekcji Strony, routing i układy.](./pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="844b0-180">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="844b0-181">Układ</span><span class="sxs-lookup"><span data-stu-id="844b0-181">Layout</span></span>

<span data-ttu-id="844b0-182">W ASP.NET aplikacjach formularzy sieci Web wspólny układ strony jest obsługiwany przy użyciu stron wzorcowych *(Site.Master).*</span><span class="sxs-lookup"><span data-stu-id="844b0-182">In ASP.NET Web Forms apps, common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="844b0-183">W aplikacjach Blazor układ strony jest obsługiwany przy użyciu składników układu *(Shared/MainLayout.brzytwa).*</span><span class="sxs-lookup"><span data-stu-id="844b0-183">In Blazor apps, page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="844b0-184">Składniki układu zostaną omówione bardziej szczegółowo w sekcji [Strona, routing i układy.](./pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="844b0-184">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="844b0-185">Bootstrap Blazor</span><span class="sxs-lookup"><span data-stu-id="844b0-185">Bootstrap Blazor</span></span>

<span data-ttu-id="844b0-186">Aby bootstrap Blazor, aplikacja musi:</span><span class="sxs-lookup"><span data-stu-id="844b0-186">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="844b0-187">Określ, gdzie na stronie powinien być renderowany składnik główny *(App.Razor).*</span><span class="sxs-lookup"><span data-stu-id="844b0-187">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="844b0-188">Dodaj odpowiedni skrypt struktury Blazora.</span><span class="sxs-lookup"><span data-stu-id="844b0-188">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="844b0-189">W aplikacji Blazor Server strona hosta składnika głównego jest zdefiniowana w pliku *_Host.cshtml.*</span><span class="sxs-lookup"><span data-stu-id="844b0-189">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="844b0-190">Ten plik definiuje stronę razor, a nie składnik.</span><span class="sxs-lookup"><span data-stu-id="844b0-190">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="844b0-191">Strony razor używają składni Razor do definiowania strony adresowalnej serwera, bardzo podobnej do strony *.aspx.*</span><span class="sxs-lookup"><span data-stu-id="844b0-191">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="844b0-192">Metoda `Html.RenderComponentAsync<TComponent>(RenderMode)` służy do definiowania, gdzie powinien być renderowany składnik na poziomie głównym.</span><span class="sxs-lookup"><span data-stu-id="844b0-192">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="844b0-193">Opcja `RenderMode` wskazuje sposób, w jaki składnik powinien być renderowany.</span><span class="sxs-lookup"><span data-stu-id="844b0-193">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="844b0-194">W poniższej tabeli przedstawiono `RenderMode` obsługiwane opcje.</span><span class="sxs-lookup"><span data-stu-id="844b0-194">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="844b0-195">Opcja</span><span class="sxs-lookup"><span data-stu-id="844b0-195">Option</span></span>                        |<span data-ttu-id="844b0-196">Opis</span><span class="sxs-lookup"><span data-stu-id="844b0-196">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="844b0-197">Renderowane interaktywnie po nawiązaniu połączenia z przeglądarką</span><span class="sxs-lookup"><span data-stu-id="844b0-197">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="844b0-198">Najpierw wstępnie renderowane, a następnie renderowane interaktywnie</span><span class="sxs-lookup"><span data-stu-id="844b0-198">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="844b0-199">Renderowane jako zawartość statyczna</span><span class="sxs-lookup"><span data-stu-id="844b0-199">Rendered as static content</span></span>|

<span data-ttu-id="844b0-200">Odwołanie do skryptu *do _framework/blazor.server.js* ustanawia połączenie w czasie rzeczywistym z serwerem, a następnie zajmuje się wszystkimi interakcjami użytkownika i aktualizacjami interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="844b0-200">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

```razor
@page "/"
@namespace BlazorApp1.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BlazorApp1</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>
        @(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))
    </app>

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

<span data-ttu-id="844b0-201">W aplikacji Blazor WebAssembly strona hosta jest prostym statycznym plikiem HTML w obszarze *wwwroot/index.html*.</span><span class="sxs-lookup"><span data-stu-id="844b0-201">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="844b0-202">Element `<app>` służy do wskazania, gdzie powinien być renderowany składnik główny.</span><span class="sxs-lookup"><span data-stu-id="844b0-202">The `<app>` element is used to indicate where the root component should be rendered.</span></span>

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>Loading...</app>

    <script src="_framework/blazor.webassembly.js"></script>
</body>
</html>
```

<span data-ttu-id="844b0-203">Określony składnik do renderowania jest skonfigurowany `Startup.Configure` w metodzie aplikacji za pomocą odpowiedniego selektora CSS wskazującego, gdzie składnik powinien być renderowany.</span><span class="sxs-lookup"><span data-stu-id="844b0-203">The specific component to render is configured in the app's `Startup.Configure` method with a corresponding CSS selector indicating where the component should be rendered.</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IComponentsApplicationBuilder app)
    {
        app.AddComponent<App>("app");
    }
}
```

## <a name="build-output"></a><span data-ttu-id="844b0-204">Tworzenie danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="844b0-204">Build output</span></span>

<span data-ttu-id="844b0-205">Po zbudowaniu projektu Blazor wszystkie pliki składowe i kodowe Razor są kompilowane w jeden zespół.</span><span class="sxs-lookup"><span data-stu-id="844b0-205">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="844b0-206">W przeciwieństwie do projektów ASP.NET Web Forms Blazor nie obsługuje kompilacji interfejsu użytkownika w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="844b0-206">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="844b0-207">Uruchomienie aplikacji</span><span class="sxs-lookup"><span data-stu-id="844b0-207">Run the app</span></span>

<span data-ttu-id="844b0-208">Aby uruchomić aplikację Blazor `F5` Server, naciśnij klawisz Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="844b0-208">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="844b0-209">Aplikacje Blazor nie obsługują kompilacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="844b0-209">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="844b0-210">Aby wyświetlić wyniki zmian znaczników kodu i składnika, odbuduj i uruchom ponownie aplikację za pomocą dołączonego debugera.</span><span class="sxs-lookup"><span data-stu-id="844b0-210">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="844b0-211">Jeśli uruchomisz bez dołączonego`Ctrl+F5`debugera ( ), Visual Studio obserwuje zmiany plików i ponownie uruchamia aplikację w miarę wprowadzania zmian.</span><span class="sxs-lookup"><span data-stu-id="844b0-211">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="844b0-212">Ręcznie odświeżaj przeglądarkę w miarę wprowadzanych zmian.</span><span class="sxs-lookup"><span data-stu-id="844b0-212">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="844b0-213">Aby uruchomić aplikację Blazor WebAssembly, wybierz jedną z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="844b0-213">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="844b0-214">Uruchom projekt klienta bezpośrednio przy użyciu serwera deweloperów.</span><span class="sxs-lookup"><span data-stu-id="844b0-214">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="844b0-215">Uruchom projekt serwera podczas hostowania aplikacji z ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="844b0-215">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="844b0-216">Aplikacje Blazor WebAssembly nie obsługują debugowania przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="844b0-216">Blazor WebAssembly apps don't support debugging using Visual Studio.</span></span> <span data-ttu-id="844b0-217">Aby uruchomić aplikację, `Ctrl+F5` użyj `F5`zamiast .</span><span class="sxs-lookup"><span data-stu-id="844b0-217">To run the app, use `Ctrl+F5` instead of `F5`.</span></span> <span data-ttu-id="844b0-218">Zamiast tego można debugować aplikacje Blazor WebAssembly bezpośrednio w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="844b0-218">You can instead debug Blazor WebAssembly apps directly in the browser.</span></span> <span data-ttu-id="844b0-219">Szczegółowe informacje można znaleźć w [ASP.NET Core Blazor.](/aspnet/core/blazor/debug)</span><span class="sxs-lookup"><span data-stu-id="844b0-219">See [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="844b0-220">[Poprzedni](hosting-models.md)
>[następny](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="844b0-220">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
