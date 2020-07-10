---
title: Struktura projektu dla Blazor aplikacji
description: Dowiedz się, w jaki sposób struktura projektu dla formularzy i projektów ASP.NET sieci Web jest Blazor porównywana.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 09/11/2019
ms.openlocfilehash: 473b708a9b58fa88844bc6f79a898943d5a7db71
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173045"
---
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="a442e-103">Struktura projektu dla Blazor aplikacji</span><span class="sxs-lookup"><span data-stu-id="a442e-103">Project structure for Blazor apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a442e-104">Pomimo znaczących różnic struktury projektu, ASP.NET formularzy sieci Web i Blazor udostępniają wiele podobnych koncepcji.</span><span class="sxs-lookup"><span data-stu-id="a442e-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="a442e-105">Tutaj Przyjrzyjmy się strukturze Blazor projektu i porównać go z projektem formularzy sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="a442e-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="a442e-106">Aby utworzyć swoją pierwszą Blazor aplikację, postępuj zgodnie z instrukcjami wyświetlanymi w [ Blazor krokach wprowadzenie](/aspnet/core/blazor/get-started).</span><span class="sxs-lookup"><span data-stu-id="a442e-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="a442e-107">Można postępować zgodnie z instrukcjami w celu utworzenia Blazor aplikacji serwera lub Blazor WebAssembly aplikacji hostowanej w ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a442e-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="a442e-108">Poza obsługą logiki specyficznej dla modelu, większość kodu w obu projektach jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="a442e-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="a442e-109">Plik projektu</span><span class="sxs-lookup"><span data-stu-id="a442e-109">Project file</span></span>

Blazor<span data-ttu-id="a442e-110">Aplikacje serwera to projekty platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a442e-110"> Server apps are .NET Core projects.</span></span> <span data-ttu-id="a442e-111">Plik projektu dla Blazor aplikacji serwerowej jest bardzo prosty, ponieważ może uzyskać następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="a442e-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="a442e-112">Plik projektu Blazor WebAssembly aplikacji wygląda nieco więcej (dokładne numery wersji mogą się różnić):</span><span class="sxs-lookup"><span data-stu-id="a442e-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

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

Blazor<span data-ttu-id="a442e-113">WebAssemblyprojekty docelowe .NET standard zamiast .NET Core, ponieważ działają w przeglądarce w WebAssembly środowisku uruchomieniowym .NET opartym na architekturze.</span><span class="sxs-lookup"><span data-stu-id="a442e-113"> WebAssembly projects target .NET Standard instead of .NET Core because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="a442e-114">Nie można zainstalować programu .NET w przeglądarce internetowej, na przykład na serwerze lub na komputerze dewelopera.</span><span class="sxs-lookup"><span data-stu-id="a442e-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="a442e-115">W związku z tym projekt odwołuje się do Blazor struktury przy użyciu poszczególnych odwołań do pakietu.</span><span class="sxs-lookup"><span data-stu-id="a442e-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="a442e-116">Porównując, domyślny projekt formularzy sieci Web ASP.NET zawiera niemal 300 wierszy XML w pliku *. csproj* , z których większość jest jawnie wyświetlona w projekcie różnego kodu i plików zawartości.</span><span class="sxs-lookup"><span data-stu-id="a442e-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="a442e-117">Wiele uproszczeń w projektach opartych na architekturze .NET Core i .NET Standard pochodzi z domyślnych obiektów docelowych i właściwości zaimportowanych przez odwołanie do `Microsoft.NET.Sdk.Web` zestawu SDK, często nazywanego po prostu zestawem SDK sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a442e-117">Many of the simplifications in the .NET Core- and .NET Standard-based projects come from the default targets and properties imported by referencing the `Microsoft.NET.Sdk.Web` SDK, often referred to as simply the Web SDK.</span></span> <span data-ttu-id="a442e-118">Zestaw SDK sieci Web zawiera symbole wieloznaczne i inne wygody upraszczające dołączanie kodu i plików zawartości w projekcie.</span><span class="sxs-lookup"><span data-stu-id="a442e-118">The Web SDK includes wildcards and other conveniences that simplify inclusion of code and content files in the project.</span></span> <span data-ttu-id="a442e-119">Pliki nie muszą być jawnie wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="a442e-119">You don't need to list the files explicitly.</span></span> <span data-ttu-id="a442e-120">W przypadku określania platformy .NET Core zestaw SDK sieci Web dodaje również odwołania do struktur platformy .NET Core i ASP.NET Core wspólnych.</span><span class="sxs-lookup"><span data-stu-id="a442e-120">When targeting .NET Core, the Web SDK also adds framework references to both the .NET Core and ASP.NET Core shared frameworks.</span></span> <span data-ttu-id="a442e-121">Struktury są widoczne w **Dependencies**  >  węźle**struktury** zależności w oknie **Eksplorator rozwiązań** .</span><span class="sxs-lookup"><span data-stu-id="a442e-121">The frameworks are visible from the **Dependencies** > **Frameworks** node in the **Solution Explorer** window.</span></span> <span data-ttu-id="a442e-122">Struktury udostępnione to kolekcje zestawów, które zostały zainstalowane na komputerze podczas instalacji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a442e-122">The shared frameworks are collections of assemblies that were installed on the machine when installing .NET Core.</span></span>

<span data-ttu-id="a442e-123">Chociaż są one obsługiwane, poszczególne odwołania do zestawów są rzadziej używane w projektach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a442e-123">Although they're supported, individual assembly references are less common in .NET Core projects.</span></span> <span data-ttu-id="a442e-124">Większość zależności projektu jest obsługiwana jako odwołania do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="a442e-124">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="a442e-125">Musisz tylko odwoływać się do zależności pakietów najwyższego poziomu w projektach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a442e-125">You only need to reference top-level package dependencies in .NET Core projects.</span></span> <span data-ttu-id="a442e-126">Zależności przechodnie są włączane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="a442e-126">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="a442e-127">Zamiast korzystać z pliku *packages.config* często znalezionego w projektach formularzy sieci Web ASP.NET do pakietów referencyjnych, odwołania do pakietów są dodawane do pliku projektu przy użyciu `<PackageReference>` elementu.</span><span class="sxs-lookup"><span data-stu-id="a442e-127">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="a442e-128">Punkt wejścia</span><span class="sxs-lookup"><span data-stu-id="a442e-128">Entry point</span></span>

<span data-ttu-id="a442e-129">BlazorPunkt wejścia aplikacji serwera jest zdefiniowany w pliku *program.cs* , jak widać w aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="a442e-129">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="a442e-130">Gdy aplikacja jest wykonywana, tworzy i uruchamia wystąpienie hosta sieci Web przy użyciu ustawień domyślnych, które są specyficzne dla aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a442e-130">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="a442e-131">Host sieci Web zarządza Blazor cyklem życia aplikacji serwera i konfiguruje usługi na poziomie hosta.</span><span class="sxs-lookup"><span data-stu-id="a442e-131">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="a442e-132">Przykładami takich usług są konfiguracje, rejestrowanie, iniekcja zależności i serwer HTTP.</span><span class="sxs-lookup"><span data-stu-id="a442e-132">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="a442e-133">Ten kod jest głównie zwyczajowy i często pozostaje niezmieniony.</span><span class="sxs-lookup"><span data-stu-id="a442e-133">This code is mostly boilerplate and is often left unchanged.</span></span>

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

Blazor<span data-ttu-id="a442e-134">WebAssemblyaplikacje definiują również punkt wejścia w *program.cs*.</span><span class="sxs-lookup"><span data-stu-id="a442e-134"> WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="a442e-135">Kod wygląda nieco inaczej.</span><span class="sxs-lookup"><span data-stu-id="a442e-135">The code looks slightly different.</span></span> <span data-ttu-id="a442e-136">Kod jest podobny w przypadku konfigurowania hosta aplikacji w celu zapewnienia tej samej aplikacji na poziomie hosta.</span><span class="sxs-lookup"><span data-stu-id="a442e-136">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="a442e-137">WebAssemblyHost aplikacji nie jest jednak skonfigurowany jako serwer http, ponieważ jest wykonywany bezpośrednio w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="a442e-137">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

Blazor<span data-ttu-id="a442e-138">aplikacje mają `Startup` klasę zamiast pliku *Global. asax* do definiowania logiki uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a442e-138"> apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="a442e-139">`Startup`Klasa służy do konfigurowania aplikacji i wszystkich usług specyficznych dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a442e-139">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="a442e-140">W Blazor aplikacji serwerowej Klasa służy `Startup` do konfigurowania punktu końcowego dla połączenia w czasie rzeczywistym używanego przez Blazor między przeglądarkami klienta a serwerem.</span><span class="sxs-lookup"><span data-stu-id="a442e-140">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="a442e-141">W Blazor WebAssembly aplikacji `Startup` Klasa definiuje główne składniki aplikacji i miejsce, w którym powinny być renderowane.</span><span class="sxs-lookup"><span data-stu-id="a442e-141">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="a442e-142">Zajmiemy się bardziej szczegółowymi `Startup` klasami w sekcji [uruchamiania aplikacji](./app-startup.md) .</span><span class="sxs-lookup"><span data-stu-id="a442e-142">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="a442e-143">Pliki statyczne</span><span class="sxs-lookup"><span data-stu-id="a442e-143">Static files</span></span>

<span data-ttu-id="a442e-144">W przeciwieństwie do projektów ASP.NET Web Forms, nie wszystkie pliki w Blazor projekcie mogą być żądane jako pliki statyczne.</span><span class="sxs-lookup"><span data-stu-id="a442e-144">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="a442e-145">Tylko pliki w folderze *wwwroot* są adresami sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a442e-145">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="a442e-146">Ten folder jest określany jako "katalog główny sieci Web" aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a442e-146">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="a442e-147">Wszystkie elementy poza elementem głównym sieci Web aplikacji *nie są* adresami sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a442e-147">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="a442e-148">Ta konfiguracja zapewnia dodatkowy poziom zabezpieczeń, który uniemożliwia przypadkowe ujawnienie plików projektu za pośrednictwem sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a442e-148">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="a442e-149">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="a442e-149">Configuration</span></span>

<span data-ttu-id="a442e-150">Konfiguracja w aplikacjach ASP.NET Web Forms jest zwykle obsługiwana przy użyciu co najmniej jednego pliku *web.config* .</span><span class="sxs-lookup"><span data-stu-id="a442e-150">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> Blazor<span data-ttu-id="a442e-151">aplikacje nie mają zwykle plików *web.config* .</span><span class="sxs-lookup"><span data-stu-id="a442e-151"> apps don't typically have *web.config* files.</span></span> <span data-ttu-id="a442e-152">Jeśli tak, plik jest używany tylko do konfigurowania ustawień specyficznych dla usług IIS, które są hostowane w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="a442e-152">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="a442e-153">Zamiast tego Blazor aplikacje serwera używają abstrakcji konfiguracji ASP.NET Core ( Blazor WebAssembly aplikacje nie obsługują obecnie tych samych abstrakcji konfiguracji, ale mogą to być funkcje dodane w przyszłości).</span><span class="sxs-lookup"><span data-stu-id="a442e-153">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="a442e-154">Na przykład domyślna Blazor aplikacja serwerowa przechowuje niektóre ustawienia w *appsettings.js*.</span><span class="sxs-lookup"><span data-stu-id="a442e-154">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

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

<span data-ttu-id="a442e-155">Dowiesz się więcej na temat konfiguracji w projektach ASP.NET Core w sekcji [konfiguracji](./config.md) .</span><span class="sxs-lookup"><span data-stu-id="a442e-155">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="a442e-156">Składniki Razor</span><span class="sxs-lookup"><span data-stu-id="a442e-156">Razor components</span></span>

<span data-ttu-id="a442e-157">Większość plików w Blazor projektach to pliki *Razor* .</span><span class="sxs-lookup"><span data-stu-id="a442e-157">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="a442e-158">Razor to tworzenia szablonów język oparty na języku HTML i C#, który jest używany do dynamicznego generowania interfejsu użytkownika sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a442e-158">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="a442e-159">Pliki *. Razor* definiują składniki tworzące interfejs użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a442e-159">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="a442e-160">W większości przypadków składniki są identyczne zarówno dla Blazor serwera, jak i Blazor WebAssembly aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a442e-160">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="a442e-161">Składniki w programie Blazor są analogiczne do kontrolek użytkownika w ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="a442e-161">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="a442e-162">Każdy plik składnika Razor jest kompilowany do klasy .NET podczas kompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="a442e-162">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="a442e-163">Wygenerowana Klasa przechwytuje stan składnika, logiki renderowania, metody cyklu życia, procedury obsługi zdarzeń i inne logiki.</span><span class="sxs-lookup"><span data-stu-id="a442e-163">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="a442e-164">W sekcji [Tworzenie składników interfejsu użytkownika wielokrotnego użytku Blazor ](./components.md) należy zapoznać się z sekcją.</span><span class="sxs-lookup"><span data-stu-id="a442e-164">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="a442e-165">Pliki *_Imports. Razor* nie są plikami składników Razor.</span><span class="sxs-lookup"><span data-stu-id="a442e-165">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="a442e-166">Zamiast tego definiują zestaw dyrektyw Razor do zaimportowania do innych plików *Razor* w tym samym folderze i w jego podfolderach.</span><span class="sxs-lookup"><span data-stu-id="a442e-166">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="a442e-167">Na przykład plik *_Imports. Razor* jest konwencjonalnym sposobem dodawania `using` dyrektyw dla często używanych przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="a442e-167">For example, a *_Imports.razor* file is a conventional way to add `using` directives for commonly used namespaces:</span></span>

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

## <a name="pages"></a><span data-ttu-id="a442e-168">Strony</span><span class="sxs-lookup"><span data-stu-id="a442e-168">Pages</span></span>

<span data-ttu-id="a442e-169">Gdzie znajdują się strony w Blazor aplikacjach?</span><span class="sxs-lookup"><span data-stu-id="a442e-169">Where are the pages in the Blazor apps?</span></span> Blazor<span data-ttu-id="a442e-170">nie definiuje oddzielnego rozszerzenia pliku dla stron adresowanych, takich jak pliki *aspx* w aplikacjach ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="a442e-170"> doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="a442e-171">Zamiast tego strony są definiowane przez przypisanie tras do składników programu.</span><span class="sxs-lookup"><span data-stu-id="a442e-171">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="a442e-172">Trasa jest zwykle przypisana przy użyciu `@page` dyrektywy Razor.</span><span class="sxs-lookup"><span data-stu-id="a442e-172">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="a442e-173">Na przykład `Counter` składnik utworzony w pliku *Pages/Counter. Razor* definiuje następującą trasę:</span><span class="sxs-lookup"><span data-stu-id="a442e-173">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="a442e-174">Routing w programie Blazor jest obsługiwany po stronie klienta, a nie na serwerze.</span><span class="sxs-lookup"><span data-stu-id="a442e-174">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="a442e-175">Gdy użytkownik nawiguje w przeglądarce, Blazor przechwytuje nawigację, a następnie renderuje składnik przy użyciu pasującej trasy.</span><span class="sxs-lookup"><span data-stu-id="a442e-175">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="a442e-176">Trasy składników nie są obecnie wywnioskowane przez lokalizację pliku składnika, tak jak w przypadku stron *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="a442e-176">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="a442e-177">Ta funkcja może zostać dodana w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="a442e-177">This feature may be added in the future.</span></span> <span data-ttu-id="a442e-178">Poszczególne trasy muszą być jawnie określone w składniku.</span><span class="sxs-lookup"><span data-stu-id="a442e-178">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="a442e-179">Przechowywanie składników rutowanych w folderze *Pages* nie ma specjalnego znaczenia i jest czysto Konwencji.</span><span class="sxs-lookup"><span data-stu-id="a442e-179">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="a442e-180">Więcej szczegółów na temat routingu znajduje się w Blazor sekcji [strony, Routing i układy](./pages-routing-layouts.md) .</span><span class="sxs-lookup"><span data-stu-id="a442e-180">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="a442e-181">Układ</span><span class="sxs-lookup"><span data-stu-id="a442e-181">Layout</span></span>

<span data-ttu-id="a442e-182">W aplikacjach formularzy sieci Web ASP.NET wspólny układ strony jest obsługiwany przy użyciu stron wzorcowych (*site. Master*).</span><span class="sxs-lookup"><span data-stu-id="a442e-182">In ASP.NET Web Forms apps, common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="a442e-183">W obszarze Blazor aplikacje układ strony jest obsługiwany przy użyciu składników układu (*Shared/MainLayout. Razor*).</span><span class="sxs-lookup"><span data-stu-id="a442e-183">In Blazor apps, page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="a442e-184">Składniki układu zostaną omówione bardziej szczegółowo w sekcji [strony, routingu i układów](./pages-routing-layouts.md) .</span><span class="sxs-lookup"><span data-stu-id="a442e-184">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="a442e-185">BootstrapBlazor</span><span class="sxs-lookup"><span data-stu-id="a442e-185">Bootstrap Blazor</span></span>

<span data-ttu-id="a442e-186">Aby załadować Blazor aplikację, należy wykonać następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="a442e-186">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="a442e-187">Określ, gdzie na stronie ma być renderowany składnik główny (*App. Razor*).</span><span class="sxs-lookup"><span data-stu-id="a442e-187">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="a442e-188">Dodaj odpowiedni Blazor skrypt struktury.</span><span class="sxs-lookup"><span data-stu-id="a442e-188">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="a442e-189">W Blazor aplikacji serwera strona hosta składnika głównego jest zdefiniowana w pliku *_Host. cshtml* .</span><span class="sxs-lookup"><span data-stu-id="a442e-189">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="a442e-190">Ten plik definiuje stronę Razor, a nie składnik.</span><span class="sxs-lookup"><span data-stu-id="a442e-190">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="a442e-191">Razor Pages używać składnia Razor do definiowania strony z adresami serwera, podobnie jak strona *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="a442e-191">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="a442e-192">`Html.RenderComponentAsync<TComponent>(RenderMode)`Metoda służy do definiowania miejsca, w którym ma być renderowany składnik poziomu głównego.</span><span class="sxs-lookup"><span data-stu-id="a442e-192">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="a442e-193">`RenderMode`Opcja wskazuje sposób, w jaki składnik powinien być renderowany.</span><span class="sxs-lookup"><span data-stu-id="a442e-193">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="a442e-194">W poniższej tabeli przedstawiono obsługiwane `RenderMode` Opcje.</span><span class="sxs-lookup"><span data-stu-id="a442e-194">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="a442e-195">Opcja</span><span class="sxs-lookup"><span data-stu-id="a442e-195">Option</span></span>                        |<span data-ttu-id="a442e-196">Opis</span><span class="sxs-lookup"><span data-stu-id="a442e-196">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="a442e-197">Renderowane interaktywnie po nawiązaniu połączenia z przeglądarką</span><span class="sxs-lookup"><span data-stu-id="a442e-197">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="a442e-198">Pierwsze, wstępnie renderowane i renderowane interaktywnie</span><span class="sxs-lookup"><span data-stu-id="a442e-198">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="a442e-199">Renderowane jako zawartość statyczna</span><span class="sxs-lookup"><span data-stu-id="a442e-199">Rendered as static content</span></span>|

<span data-ttu-id="a442e-200">Odwołanie do skryptu do *_framework/blazor.server.js* nawiązuje połączenie w czasie rzeczywistym z serwerem, a następnie zajmuje się wszystkimi interakcjami użytkowników i AKTUALIZACJAmi interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a442e-200">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

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

<span data-ttu-id="a442e-201">W Blazor WebAssembly aplikacji strona hosta to prosty statyczny plik HTML w katalogu *wwwroot/index.html*.</span><span class="sxs-lookup"><span data-stu-id="a442e-201">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="a442e-202">`<app>`Element służy do wskazywania, gdzie ma być renderowany składnik główny.</span><span class="sxs-lookup"><span data-stu-id="a442e-202">The `<app>` element is used to indicate where the root component should be rendered.</span></span>

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

<span data-ttu-id="a442e-203">Określony składnik do renderowania jest skonfigurowany w `Startup.Configure` metodzie aplikacji przy użyciu odpowiedniego selektora CSS wskazującego, gdzie składnik powinien być renderowany.</span><span class="sxs-lookup"><span data-stu-id="a442e-203">The specific component to render is configured in the app's `Startup.Configure` method with a corresponding CSS selector indicating where the component should be rendered.</span></span>

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

## <a name="build-output"></a><span data-ttu-id="a442e-204">Dane wyjściowe kompilacji</span><span class="sxs-lookup"><span data-stu-id="a442e-204">Build output</span></span>

<span data-ttu-id="a442e-205">Po Blazor skompilowaniu projektu wszystkie składniki i pliki kodu Razor są kompilowane do jednego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a442e-205">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="a442e-206">W przeciwieństwie do projektów ASP.NET Web Forms, Blazor nie obsługuje kompilowania logiki interfejsu użytkownika w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a442e-206">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="a442e-207">Uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="a442e-207">Run the app</span></span>

<span data-ttu-id="a442e-208">Aby uruchomić Blazor aplikację serwerową, naciśnij klawisz `F5` w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a442e-208">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> Blazor<span data-ttu-id="a442e-209">aplikacje nie obsługują kompilacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a442e-209"> apps don't support runtime compilation.</span></span> <span data-ttu-id="a442e-210">Aby zobaczyć wyniki zmian kodu i znaczników składnika, ponownie skompiluj i ponownie uruchom aplikację z dołączonym debugerem.</span><span class="sxs-lookup"><span data-stu-id="a442e-210">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="a442e-211">Jeśli uruchomisz bez dołączonego debugera ( `Ctrl+F5` ), program Visual Studio przeczujuje się pod kątem zmian plików i ponownie uruchomi aplikację w miarę wprowadzania zmian.</span><span class="sxs-lookup"><span data-stu-id="a442e-211">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="a442e-212">Przeglądarka ręcznie jest odświeżana w miarę wprowadzania zmian.</span><span class="sxs-lookup"><span data-stu-id="a442e-212">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="a442e-213">Aby uruchomić Blazor WebAssembly aplikację, wybierz jedną z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="a442e-213">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="a442e-214">Uruchom projekt klienta bezpośrednio przy użyciu serwera deweloperskiego.</span><span class="sxs-lookup"><span data-stu-id="a442e-214">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="a442e-215">Uruchom projekt serwera podczas hostowania aplikacji przy użyciu ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a442e-215">Run the server project when hosting the app with ASP.NET Core.</span></span>

Blazor<span data-ttu-id="a442e-216">WebAssemblyaplikacje nie obsługują debugowania przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a442e-216"> WebAssembly apps don't support debugging using Visual Studio.</span></span> <span data-ttu-id="a442e-217">Aby uruchomić aplikację, użyj `Ctrl+F5` zamiast `F5` .</span><span class="sxs-lookup"><span data-stu-id="a442e-217">To run the app, use `Ctrl+F5` instead of `F5`.</span></span> <span data-ttu-id="a442e-218">Zamiast tego można debugować Blazor WebAssembly aplikacje bezpośrednio w przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="a442e-218">You can instead debug Blazor WebAssembly apps directly in the browser.</span></span> <span data-ttu-id="a442e-219">Aby uzyskać szczegółowe informacje, zobacz [ASP.NET Core Blazor debugowania](/aspnet/core/blazor/debug) .</span><span class="sxs-lookup"><span data-stu-id="a442e-219">See [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a442e-220">[Poprzedni](hosting-models.md) 
> [Dalej](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="a442e-220">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
