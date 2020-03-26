---
title: Migracja z ASP.NET formularzy sieci Web do blazora
description: Dowiedz się, jak podejść do migracji istniejącej aplikacji ASP.NET Formularzy sieci Web do blazora.
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: 0a10a9a3d5ab32e16cb59a68da57116e20c53e49
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134089"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a><span data-ttu-id="cb9e5-103">Migracja z ASP.NET formularzy sieci Web do blazora</span><span class="sxs-lookup"><span data-stu-id="cb9e5-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="cb9e5-104">Migrowanie bazy kodu z ASP.NET formularzy sieci Web do blazora jest czasochłonnym zadaniem, które wymaga planowania.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="cb9e5-105">W tym rozdziale przedstawiono ten proces.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-105">This chapter outlines the process.</span></span> <span data-ttu-id="cb9e5-106">Coś, co może ułatwić przejście jest zapewnienie, że aplikacja jest zgodna z architekturą *n-warstwy,* w którym model aplikacji (w tym przypadku formularze sieci Web) jest oddzielony od logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="cb9e5-107">Ta logiczna separacja warstw wyjaśnia, co należy przenieść do .NET Core i Blazor.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="cb9e5-108">W tym przykładzie używana jest aplikacja eShop dostępna w [usłudze GitHub.](https://github.com/dotnet-architecture/eShopOnBlazor)</span><span class="sxs-lookup"><span data-stu-id="cb9e5-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="cb9e5-109">eShop to usługa katalogowa, która zapewnia możliwości CRUD poprzez wprowadzanie i walidację formularza.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="cb9e5-110">Dlaczego działająca aplikacja powinna zostać przeniesiona do Blazora?</span><span class="sxs-lookup"><span data-stu-id="cb9e5-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="cb9e5-111">Wiele razy, nie ma potrzeby.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-111">Many times, there's no need.</span></span> <span data-ttu-id="cb9e5-112">ASP.NET formularzy sieci Web będą nadal wspierane przez wiele lat.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="cb9e5-113">Jednak wiele funkcji, które zapewnia Blazor, jest obsługiwanych tylko w zmigrowanym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="cb9e5-114">Takie funkcje obejmują:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-114">Such features include:</span></span>

- <span data-ttu-id="cb9e5-115">Poprawa wydajności w takich ramach, jak`Span<T>`</span><span class="sxs-lookup"><span data-stu-id="cb9e5-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="cb9e5-116">Możliwość uruchamiania jako WebAssembly</span><span class="sxs-lookup"><span data-stu-id="cb9e5-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="cb9e5-117">Obsługa wielu platform dla systemów Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="cb9e5-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="cb9e5-118">Wdrożenie lokalne aplikacji lub wdrożenie współużytkowane framework bez wpływu na inne aplikacje</span><span class="sxs-lookup"><span data-stu-id="cb9e5-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="cb9e5-119">Jeśli te lub inne nowe funkcje są wystarczająco atrakcyjne, może być wartość w migracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="cb9e5-120">Migracja może mieć różne kształty; może to być cała aplikacja lub tylko niektóre punkty końcowe, które wymagają zmian.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="cb9e5-121">Decyzja o migracji jest ostatecznie oparta na problemach biznesowych, które mają zostać rozwiązane przez dewelopera.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="cb9e5-122">Hosting po stronie serwera i po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="cb9e5-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="cb9e5-123">Jak opisano w rozdziale [modeli hostingu,](hosting-models.md) aplikacja Blazor może być hostowana na dwa różne sposoby: po stronie serwera i po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="cb9e5-124">Model po stronie serwera używa połączeń ASP.NET Core SignalR do zarządzania aktualizacjami DOM podczas uruchamiania dowolnego rzeczywistego kodu na serwerze.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="cb9e5-125">Model po stronie klienta działa jako WebAssembly w przeglądarce i nie wymaga żadnych połączeń z serwerem.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="cb9e5-126">Istnieje wiele różnic, które mogą mieć wpływ, co jest najlepsze dla konkretnej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="cb9e5-127">Uruchamianie jako WebAssembly jest nadal w fazie rozwoju i może nie obsługiwać wszystkich funkcji (takich jak wątki) w bieżącym czasie</span><span class="sxs-lookup"><span data-stu-id="cb9e5-127">Running as WebAssembly is still in development and may not support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="cb9e5-128">Chatty komunikacji między klientem a serwerem może powodować problemy z opóźnieniem w trybie po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="cb9e5-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="cb9e5-129">Dostęp do baz danych i usług wewnętrznych lub chronionych wymaga oddzielnej usługi z hostingiem po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="cb9e5-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="cb9e5-130">W momencie pisania model po stronie serwera bardziej przypomina formularze sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="cb9e5-131">Większość tego rozdziału koncentruje się na modelu hostingu po stronie serwera, ponieważ jest gotowy do produkcji.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="cb9e5-132">Tworzenie nowego projektu</span><span class="sxs-lookup"><span data-stu-id="cb9e5-132">Create a new project</span></span>

<span data-ttu-id="cb9e5-133">Ten początkowy krok migracji polega na utworzeniu nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="cb9e5-134">Ten typ projektu jest oparty na projektach stylu SDK .NET Core i upraszcza wiele standardowego, który był używany w poprzednich formatach projektu.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-134">This project type is based on the SDK style projects of .NET Core and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="cb9e5-135">Aby uzyskać więcej informacji, zapoznaj się z rozdziałem [struktury projektu](project-structure.md).</span><span class="sxs-lookup"><span data-stu-id="cb9e5-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="cb9e5-136">Po utworzeniu projektu zainstaluj biblioteki, które były używane w poprzednim projekcie.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="cb9e5-137">W starszych projektach formularzy sieci Web być może użyto pliku *packages.config* do listy wymaganych pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="cb9e5-138">W nowym projekcie w stylu SDK *packages.config* został zastąpiony elementami `<PackageReference>` w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="cb9e5-139">Zaletą tego podejścia jest, że wszystkie zależności są instalowane przechodnie.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="cb9e5-140">Możesz wyświetlić tylko zależności najwyższego poziomu, na których Ci zależy.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="cb9e5-141">Wiele zależności, których używasz, jest dostępnych dla platformy .NET Core, w tym entity framework 6 i log4net.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-141">Many of the dependencies you're using are available for .NET Core, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="cb9e5-142">Jeśli nie ma dostępnej wersji .NET Core lub .NET Standard, często można użyć wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-142">If there's no .NET Core or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="cb9e5-143">Przebieg może się różnić.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-143">Your mileage may vary.</span></span> <span data-ttu-id="cb9e5-144">Każdy interfejs API używany, który nie jest dostępny w .NET Core powoduje błąd środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-144">Any API used that isn't available in .NET Core causes a runtime error.</span></span> <span data-ttu-id="cb9e5-145">Visual Studio powiadamia o takich pakietach.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="cb9e5-146">W węźle **Odwołania** projektu pojawi się żółta ikona **.**</span><span class="sxs-lookup"><span data-stu-id="cb9e5-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="cb9e5-147">W projekcie eShop opartym na Blazorie możesz zobaczyć pakiety, które są zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="cb9e5-148">Wcześniej plik *packages.config* wymieniał każdy pakiet używany w projekcie, w wyniku czego plik o długości prawie 50 wierszy.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="cb9e5-149">Fragment kodu *packages.config* to:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-149">A snippet of *packages.config* is:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  ...
  <package id="Microsoft.ApplicationInsights.Agent.Intercept" version="2.4.0" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.DependencyCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.PerfCounterCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.Web" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer.TelemetryChannel" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls.Core" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.MSAjax" version="5.0.0" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.WebForms" version="5.0.0" targetFramework="net472" />
  ...
  <package id="System.Memory" version="4.5.1" targetFramework="net472" />
  <package id="System.Numerics.Vectors" version="4.4.0" targetFramework="net472" />
  <package id="System.Runtime.CompilerServices.Unsafe" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Channels" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Tasks.Extensions" version="4.5.1" targetFramework="net472" />
  <package id="WebGrease" version="1.6.0" targetFramework="net472" />
</packages>
```

<span data-ttu-id="cb9e5-150">Element `<packages>` zawiera wszystkie niezbędne zależności.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="cb9e5-151">Trudno jest zidentyfikować, które z tych pakietów są uwzględniane, ponieważ są one potrzebne.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="cb9e5-152">Niektóre `<package>` elementy są wymienione po prostu w celu zaspokojenia potrzeb zależności, których potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="cb9e5-153">Projekt Blazor wyświetla listę zależności wymaganych w elemencie `<ItemGroup>` w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

<span data-ttu-id="cb9e5-154">Jednym z pakietów NuGet, który upraszcza życie programistów formularzy sieci Web, jest [pakiet zgodności systemu Windows](../../core/porting/windows-compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="cb9e5-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](../../core/porting/windows-compat-pack.md).</span></span> <span data-ttu-id="cb9e5-155">Chociaż program .NET Core jest wieloplatformowy, niektóre funkcje są dostępne tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-155">Although .NET Core is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="cb9e5-156">Funkcje specyficzne dla systemu Windows są udostępniane przez zainstalowanie pakietu zgodności.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="cb9e5-157">Przykładami takich funkcji są usługi rejestru, usługi WMI i usługi katalogowe.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="cb9e5-158">Pakiet dodaje około 20 000 interfejsów API i aktywuje wiele usług, z którymi możesz być już zaznajomiony.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="cb9e5-159">Projekt eShop nie wymaga pakietu zgodności; ale jeśli projekty korzystają z funkcji specyficznych dla systemu Windows, pakiet ułatwia wysiłki na rzecz migracji.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="cb9e5-160">Włącz proces uruchamiania</span><span class="sxs-lookup"><span data-stu-id="cb9e5-160">Enable startup process</span></span>

<span data-ttu-id="cb9e5-161">Proces uruchamiania blazora zmienił się z formularzy sieci Web i następuje podobna konfiguracja dla innych usług ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="cb9e5-162">Po hostowane po stronie serwera, składniki Blazor są uruchamiane jako część normalnej aplikacji ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="cb9e5-163">Gdy hostowane w przeglądarce z WebAssembly, składniki Blazor użyć podobnego modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="cb9e5-164">Różnica polega na tym, że składniki są uruchamiane jako oddzielna usługa od dowolnego z procesów wewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="cb9e5-165">Tak czy inaczej, uruchamianie jest podobne.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="cb9e5-166">Plik *Global.asax.cs* jest domyślną stroną startową dla projektów formularzy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="cb9e5-167">W projekcie eShop ten plik konfiguruje kontener Inwersji kontroli (IoC) i obsługuje różne zdarzenia cyklu życia aplikacji lub żądania.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="cb9e5-168">Niektóre z tych zdarzeń są obsługiwane za `Application_BeginRequest`pomocą oprogramowania pośredniczącego (np. ).</span><span class="sxs-lookup"><span data-stu-id="cb9e5-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="cb9e5-169">Inne zdarzenia wymagają zastąpienia określonych usług za pomocą iniekcji zależności (DI).</span><span class="sxs-lookup"><span data-stu-id="cb9e5-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="cb9e5-170">Na przykład plik *Global.asax.cs* dla sklepu eShop zawiera następujący kod:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

```csharp
public class Global : HttpApplication, IContainerProviderAccessor
{
    private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

    static IContainerProvider _containerProvider;
    IContainer container;

    public IContainerProvider ContainerProvider
    {
        get { return _containerProvider; }
    }

    protected void Application_Start(object sender, EventArgs e)
    {
        // Code that runs on app startup
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        BundleConfig.RegisterBundles(BundleTable.Bundles);
        ConfigureContainer();
        ConfigDataBase();
    }

    /// <summary>
    /// Track the machine name and the start time for the session inside the current session
    /// </summary>
    protected void Session_Start(Object sender, EventArgs e)
    {
        HttpContext.Current.Session["MachineName"] = Environment.MachineName;
        HttpContext.Current.Session["SessionStartTime"] = DateTime.Now;
    }

    /// <summary>
    /// http://docs.autofac.org/en/latest/integration/webforms.html
    /// </summary>
    private void ConfigureContainer()
    {
        var builder = new ContainerBuilder();
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
        builder.RegisterModule(new ApplicationModule(mockData));
        container = builder.Build();
        _containerProvider = new ContainerProvider(container);
    }

    private void ConfigDataBase()
    {
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);

        if (!mockData)
        {
            Database.SetInitializer<CatalogDBContext>(container.Resolve<CatalogDBInitializer>());
        }
    }

    protected void Application_BeginRequest(object sender, EventArgs e)
    {
        //set the property to our new object
        LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper();

        LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo();

        _log.Debug("Application_BeginRequest");
    }
}
```

<span data-ttu-id="cb9e5-171">Poprzedni plik staje `Startup` się klasą w blazorze po stronie serwera:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    public IConfiguration Configuration { get; }

    public IWebHostEnvironment Env { get; }

    // This method gets called by the runtime. Use this method to add services to the container.
    // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddRazorPages();
        services.AddServerSideBlazor();

        if (Configuration.GetValue<bool>("UseMockData"))
        {
            services.AddSingleton<ICatalogService, CatalogServiceMock>();
        }
        else
        {
            services.AddScoped<ICatalogService, CatalogService>();
            services.AddScoped<IDatabaseInitializer<CatalogDBContext>, CatalogDBInitializer>();
            services.AddSingleton<CatalogItemHiLoGenerator>();
            services.AddScoped(_ => new CatalogDBContext(Configuration.GetConnectionString("CatalogDBContext")));
        }
    }

    // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
    public void Configure(IApplicationBuilder app, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddLog4Net("log4Net.xml");

        if (Env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
        }

        // Middleware for Application_BeginRequest
        app.Use((ctx, next) =>
        {
            LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper(ctx);
            LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo(ctx);
            return next();
        });

        app.UseStaticFiles();

        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapBlazorHub();
            endpoints.MapFallbackToPage("/_Host");
        });

        ConfigDataBase(app);
    }

    private void ConfigDataBase(IApplicationBuilder app)
    {
        using (var scope = app.ApplicationServices.CreateScope())
        {
            var initializer = scope.ServiceProvider.GetService<IDatabaseInitializer<CatalogDBContext>>();

            if (initializer != null)
            {
                Database.SetInitializer(initializer);
            }
        }
    }
}
```

<span data-ttu-id="cb9e5-172">Jedną z istotnych zmian, które można zauważyć w formularzach sieci Web jest znaczenie DI.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="cb9e5-173">DI jest wiodącą zasadą w projekcie ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="cb9e5-174">Obsługuje dostosowywanie prawie wszystkich aspektów ASP.NET core framework.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="cb9e5-175">Istnieje nawet wbudowany dostawca usług, który może być używany w wielu scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="cb9e5-176">Jeśli wymagane jest więcej dostosowywania, może być obsługiwany przez wiele projektów społeczności.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-176">If more customization is required, it can be supported by the many community projects.</span></span> <span data-ttu-id="cb9e5-177">Na przykład można przenieść inwestycję biblioteki DI innej firmy.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="cb9e5-178">W oryginalnej aplikacji eShop istnieje pewna konfiguracja do zarządzania sesjami.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="cb9e5-179">Ponieważ blazor po stronie serwera używa ASP.NET Core SignalR do komunikacji, stan sesji nie jest obsługiwany, ponieważ połączenia mogą wystąpić niezależnie od kontekstu HTTP.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="cb9e5-180">Aplikacja, która używa stanu sesji wymaga rearchitecting przed uruchomieniem jako aplikacji Blazor.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-180">An app that uses session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="cb9e5-181">Aby uzyskać więcej informacji na temat uruchamiania aplikacji, zobacz [Uruchamianie aplikacji](app-startup.md).</span><span class="sxs-lookup"><span data-stu-id="cb9e5-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="cb9e5-182">Migrowanie modułów i programów obsługi HTTP do oprogramowania pośredniczącego</span><span class="sxs-lookup"><span data-stu-id="cb9e5-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="cb9e5-183">Moduły i programy obsługi HTTP są typowe wzorce w formularzach sieci Web do kontrolowania potoku żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="cb9e5-184">Klasy, `IHttpModule` które `IHttpHandler` implementują lub mogą być zarejestrowane i przetwarzają przychodzące żądania.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="cb9e5-185">Formularze sieci Web konfiguruje moduły i programy obsługi w pliku *web.config.*</span><span class="sxs-lookup"><span data-stu-id="cb9e5-185">Web Forms configures modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="cb9e5-186">Formularze sieci Web jest również w dużym stopniu oparte na obsłudze zdarzeń cyklu życia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="cb9e5-187">ASP.NET Core używa oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="cb9e5-188">Oprogramowanie pośredniczące `Configure` jest zarejestrowane w metodzie `Startup` klasy.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-188">Middleware is registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="cb9e5-189">Zlecenie wykonania oprogramowania pośredniczącego jest określane przez kolejność rejestracji.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="cb9e5-190">W sekcji [Włącz proces uruchamiania](#enable-startup-process) zdarzenie cyklu życia zostało `Application_BeginRequest` podniesione przez formularze sieci Web jako metodę.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="cb9e5-191">To zdarzenie nie jest dostępne w ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="cb9e5-192">Jednym ze sposobów osiągnięcia tego zachowania jest zaimplementowanie oprogramowania pośredniczącego, jak pokazano w przykładzie pliku *Startup.cs.*</span><span class="sxs-lookup"><span data-stu-id="cb9e5-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="cb9e5-193">To oprogramowanie pośredniczące wykonuje tę samą logikę, a następnie przenosi kontrolę do następnego programu obsługi w potoku oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="cb9e5-194">Aby uzyskać więcej informacji na temat migrowania modułów i programów obsługi, zobacz [Migrowanie programów obsługi i modułów HTTP w celu ASP.NET oprogramowania pośredniczącego Core](/aspnet/core/migration/http-modules).</span><span class="sxs-lookup"><span data-stu-id="cb9e5-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="cb9e5-195">Migrowanie plików statycznych</span><span class="sxs-lookup"><span data-stu-id="cb9e5-195">Migrate static files</span></span>

<span data-ttu-id="cb9e5-196">Aby pliki statyczne były eksponowane (na przykład HTML, CSS, obrazy i javascript), pliki muszą być udostępniane przez oprogramowanie pośredniczące.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="cb9e5-197">Wywołanie `UseStaticFiles` metody umożliwia wyświetlanie plików statycznych ze ścieżki głównej sieci web.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="cb9e5-198">Domyślny katalog główny sieci web jest *wwwroot*, ale można go dostosować.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="cb9e5-199">Zgodnie z `Configure` metodą `Startup` klasy eShop:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="cb9e5-200">Projekt eShop umożliwia podstawowy statyczny dostęp do plików.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="cb9e5-201">Istnieje wiele dostosowań dostępnych dla statycznego dostępu do plików.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="cb9e5-202">Aby uzyskać informacje na temat włączania plików domyślnych lub przeglądarki plików, zobacz [Pliki statyczne w ASP.NET Core](/aspnet/core/fundamentals/static-files).</span><span class="sxs-lookup"><span data-stu-id="cb9e5-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="cb9e5-203">Konfiguracja tworzenia pakietów i minyfikacji środowiska uruchomieniowego migrowania</span><span class="sxs-lookup"><span data-stu-id="cb9e5-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="cb9e5-204">Łączenie i wydobywanie to techniki optymalizacji wydajności w celu zmniejszenia liczby i rozmiaru żądań serwera w celu pobrania niektórych typów plików.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="cb9e5-205">JavaScript i CSS często przechodzą jakąś formę łączenia lub minigyfikacji przed wysłaniem do klienta.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="cb9e5-206">W ASP.NET formularzy sieci Web te optymalizacje są obsługiwane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="cb9e5-207">Konwencje optymalizacji są definiowane *App_Start/BundleConfig.cs* pliku.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="cb9e5-208">W ASP.NET Core przyjęto bardziej deklaratywne podejście.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="cb9e5-209">Plik zawiera listę plików, które mają zostać zmętnione, wraz z określonymi ustawieniami łączenia.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="cb9e5-210">Aby uzyskać więcej informacji na temat sprzedaży pakietowej i miniefikacji, zobacz [Pakiet i minify statycznych aktywów w ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span><span class="sxs-lookup"><span data-stu-id="cb9e5-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="cb9e5-211">Migrowanie stron ASPX</span><span class="sxs-lookup"><span data-stu-id="cb9e5-211">Migrate ASPX pages</span></span>

<span data-ttu-id="cb9e5-212">Strona w aplikacji Formularze sieci Web to plik z rozszerzeniem *.aspx.*</span><span class="sxs-lookup"><span data-stu-id="cb9e5-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="cb9e5-213">Strona Formularzy sieci Web często może być mapowana na składnik w blazorze.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="cb9e5-214">Składnik Blazor jest autorstwa w pliku z rozszerzeniem *.brzytwa.*</span><span class="sxs-lookup"><span data-stu-id="cb9e5-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="cb9e5-215">W przypadku projektu eShop pięć stron jest konwertowanych na stronę Razor.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="cb9e5-216">Na przykład widok szczegółów składa się z trzech plików w projekcie formularzy sieci Web: *Details.aspx*, *Details.aspx.cs*i *Details.aspx.designer.cs*.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-216">For example, the details view is comprised of three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="cb9e5-217">Podczas konwersji na Blazor, kod i znaczników są łączone w *Details.brzytwa*.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="cb9e5-218">Kompilacja brzytwy (odpowiednik tego, co znajduje się w plikach *.designer.cs)* jest przechowywana w katalogu *obj* i domyślnie nie jest chlubna w **Eksploratorze rozwiązań.**</span><span class="sxs-lookup"><span data-stu-id="cb9e5-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and aren't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="cb9e5-219">Strona Formularze sieci Web składa się z następujących znaczników:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-219">The Web Forms page consists of the following markup:</span></span>

```aspx-csharp
<%@ Page Title="Details" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Details.aspx.cs" Inherits="eShopLegacyWebForms.Catalog.Details" %>

<asp:Content ID="Details" ContentPlaceHolderID="MainContent" runat="server">
    <h2 class="esh-body-title">Details</h2>

    <div class="container">
        <div class="row">
            <asp:Image runat="server" CssClass="col-md-6 esh-picture" ImageUrl='<%#"/Pics/" + product.PictureFileName%>' />
            <dl class="col-md-6 dl-horizontal">
                <dt>Name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Name%>' />
                </dd>

                <dt>Description
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Description%>' />
                </dd>

                <dt>Brand
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogBrand.Brand%>' />
                </dd>

                <dt>Type
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogType.Type%>' />
                </dd>
                <dt>Price
                </dt>

                <dd>
                    <asp:Label CssClass="esh-price" runat="server" Text='<%#product.Price%>' />
                </dd>

                <dt>Picture name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.PictureFileName%>' />
                </dd>

                <dt>Stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.AvailableStock%>' />
                </dd>

                <dt>Restock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.RestockThreshold%>' />
                </dd>

                <dt>Max stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.MaxStockThreshold%>' />
                </dd>

            </dl>
        </div>

        <div class="form-actions no-color esh-link-list">
            <a runat="server" href='<%# GetRouteUrl("EditProductRoute", new {id =product.Id}) %>' class="esh-link-item">Edit
            </a>
            |
            <a runat="server" href="~" class="esh-link-item">Back to list
            </a>
        </div>

    </div>
</asp:Content>
```

<span data-ttu-id="cb9e5-220">Poprzedni znaczników związanych z kodem zawiera następujący kod:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-220">The preceding markup's code-behind includes the following code:</span></span>

```csharp
using eShopLegacyWebForms.Models;
using eShopLegacyWebForms.Services;
using log4net;
using System;
using System.Web.UI;

namespace eShopLegacyWebForms.Catalog
{
    public partial class Details : System.Web.UI.Page
    {
        private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        protected CatalogItem product;

        public ICatalogService CatalogService { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            var productId = Convert.ToInt32(Page.RouteData.Values["id"]);
            _log.Info($"Now loading... /Catalog/Details.aspx?id={productId}");
            product = CatalogService.FindCatalogItem(productId);

            this.DataBind();
        }
    }
}
```

<span data-ttu-id="cb9e5-221">Po przekonwertowaniu na blazor strona Formularze sieci Web tłumaczy się na następujący kod:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

```razor
@page "/Catalog/Details/{id:int}"
@inject ICatalogService CatalogService
@inject ILogger<Details> Logger

<h2 class="esh-body-title">Details</h2>

<div class="container">
    <div class="row">
        <img class="col-md-6 esh-picture" src="@($"/Pics/{_item.PictureFileName}")">

        <dl class="col-md-6 dl-horizontal">
            <dt>
                Name
            </dt>

            <dd>
                @_item.Name
            </dd>

            <dt>
                Description
            </dt>

            <dd>
                @_item.Description
            </dd>

            <dt>
                Brand
            </dt>

            <dd>
                @_item.CatalogBrand.Brand
            </dd>

            <dt>
                Type
            </dt>

            <dd>
                @_item.CatalogType.Type
            </dd>
            <dt>
                Price
            </dt>

            <dd>
                @_item.Price
            </dd>

            <dt>
                Picture name
            </dt>

            <dd>
                @_item.PictureFileName
            </dd>

            <dt>
                Stock
            </dt>

            <dd>
                @_item.AvailableStock
            </dd>

            <dt>
                Restock
            </dt>

            <dd>
                @_item.RestockThreshold
            </dd>

            <dt>
                Max stock
            </dt>

            <dd>
                @_item.MaxStockThreshold
            </dd>

        </dl>
    </div>

    <div class="form-actions no-color esh-link-list">
        <a href="@($"/Catalog/Edit/{_item.Id}")" class="esh-link-item">
            Edit
        </a>
        |
        <a href="/" class="esh-link-item">
            Back to list
        </a>
    </div>

</div>

@code {
    private CatalogItem _item;

    [Parameter]
    public int Id { get; set; }

    protected override void OnInitialized()
    {
        Logger.LogInformation("Now loading... /Catalog/Details/{Id}", Id);

        _item = CatalogService.FindCatalogItem(Id);
    }
}
```

<span data-ttu-id="cb9e5-222">Należy zauważyć, że kod i znaczniki znajdują się w tym samym pliku.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="cb9e5-223">Wszystkie wymagane usługi są dostępne `@inject` za pomocą atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="cb9e5-224">Zgodnie `@page` z dyrektywą ta strona jest `Catalog/Details/{id}` dostępna na trasie.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="cb9e5-225">Wartość symbolu zastępczego `{id}` trasy została powiązana z całkowitej liczby.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="cb9e5-226">Zgodnie z opisem w sekcji [routingu,](pages-routing-layouts.md) w przeciwieństwie do formularzy sieci Web składnik Razor jawnie określa jego trasy i wszystkie parametry, które są uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="cb9e5-227">Wiele formantów formularzy sieci Web może nie mieć dokładnych odpowiedników w blazorze.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="cb9e5-228">Często istnieje równoważny fragment kodu HTML, który będzie służył temu sameu celowi.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="cb9e5-229">Na przykład `<asp:Label />` formant można zastąpić `<label>` elementem HTML.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-blazor"></a><span data-ttu-id="cb9e5-230">Walidacja modelu w blazorze</span><span class="sxs-lookup"><span data-stu-id="cb9e5-230">Model validation in Blazor</span></span>

<span data-ttu-id="cb9e5-231">Jeśli kod formularzy sieci Web zawiera sprawdzanie poprawności, można przenieść wiele z tego, co masz z niewiele do żadnych zmian.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="cb9e5-232">Zaletą uruchamiania w Blazor jest to, że ta sama logika sprawdzania poprawności może być uruchamiana bez konieczności niestandardowego javascriptu.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="cb9e5-233">Adnotacje danych umożliwiają łatwe sprawdzanie poprawności modelu.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="cb9e5-234">Na przykład *create.aspx* strona ma formularz wprowadzania danych z sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="cb9e5-235">Przykładowy fragment kodu będzie wyglądał następująco:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-235">An example snippet would look like this:</span></span>

```aspx
<div class="form-group">
    <label class="control-label col-md-2">Name</label>
    <div class="col-md-3">
        <asp:TextBox ID="Name" runat="server" CssClass="form-control"></asp:TextBox>
        <asp:RequiredFieldValidator runat="server" ControlToValidate="Name" Display="Dynamic"
            CssClass="field-validation-valid text-danger" ErrorMessage="The Name field is required." />
    </div>
</div>
```

<span data-ttu-id="cb9e5-236">W blazorze równoważne znaczniki znajdują się w pliku *Create.brzytwa:*</span><span class="sxs-lookup"><span data-stu-id="cb9e5-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

```razor
<EditForm Model="_item" OnValidSubmit="@...">
    <DataAnnotationsValidator />

    <div class="form-group">
        <label class="control-label col-md-2">Name</label>
        <div class="col-md-3">
            <InputText class="form-control" @bind-Value="_item.Name" />
            <ValidationMessage For="(() => _item.Name)" />
        </div>
    </div>

    ...
</EditForm>
```

<span data-ttu-id="cb9e5-237">Kontekst `EditForm` obejmuje obsługę sprawdzania poprawności i mogą być zawijane wokół danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-237">The `EditForm` context includes validation support and can be wrapped around input.</span></span> <span data-ttu-id="cb9e5-238">Adnotacje danych są typowym sposobem dodawania sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="cb9e5-239">Takie wsparcie sprawdzania poprawności `DataAnnotationsValidator` można dodać za pośrednictwem składnika.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="cb9e5-240">Aby uzyskać więcej informacji na temat tego mechanizmu, zobacz [ASP.NET podstawowe formularze Blazora i walidację](/aspnet/core/blazor/forms-validation).</span><span class="sxs-lookup"><span data-stu-id="cb9e5-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-built-in-web-forms-controls"></a><span data-ttu-id="cb9e5-241">Migrowanie wbudowanych formantów formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="cb9e5-241">Migrate built-in Web Forms controls</span></span>

<span data-ttu-id="cb9e5-242">*Ta zawartość jest już wkrótce.*</span><span class="sxs-lookup"><span data-stu-id="cb9e5-242">*This content is coming soon.*</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="cb9e5-243">Migrowanie konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cb9e5-243">Migrate configuration</span></span>

<span data-ttu-id="cb9e5-244">W projekcie formularzy sieci Web dane konfiguracji są najczęściej przechowywane w pliku *web.config.*</span><span class="sxs-lookup"><span data-stu-id="cb9e5-244">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="cb9e5-245">Dostęp do danych konfiguracyjnych można uzyskać za pomocą pliku `ConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-245">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="cb9e5-246">Usługi były często wymagane do analizowania obiektów.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-246">Services were often required to parse objects.</span></span> <span data-ttu-id="cb9e5-247">Z .NET Framework 4.7.2, możliwość komponowania został dodany do konfiguracji za pośrednictwem `ConfigurationBuilders`.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-247">With .NET Framework 4.7.2, composability was added to configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="cb9e5-248">Konstruktorzy ci zezwolili deweloperom na dodawanie różnych źródeł konfiguracji, które następnie zostały skomponowane w czasie wykonywania w celu pobrania niezbędnych wartości.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-248">These builders allowed developers to add various sources for configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="cb9e5-249">ASP.NET Core wprowadził elastyczny system konfiguracji, który umożliwia zdefiniowanie źródła konfiguracji lub źródeł używanych przez aplikację i wdrożenie.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-249">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="cb9e5-250">Infrastruktura, `ConfigurationBuilder` której możesz używać w aplikacji Formularze sieci Web, została modelowana na podstawie pojęć używanych w systemie konfiguracji ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-250">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="cb9e5-251">Poniższy fragment kodu pokazuje, jak projekt web forms eShop używa *web.config* do przechowywania wartości konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-251">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

```xml
<configuration>
  <configSections>
    <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
  </configSections>
  <connectionStrings>
    <add name="CatalogDBContext" connectionString="Data Source=(localdb)\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;" providerName="System.Data.SqlClient" />
  </connectionStrings>
  <appSettings>
    <add key="UseMockData" value="true" />
    <add key="UseCustomizationData" value="false" />
  </appSettings>
</configuration>
```

<span data-ttu-id="cb9e5-252">Często wpisy tajne, takie jak parametry połączenia bazy danych, są przechowywane w *pliku web.config*. Wpisy tajne są nieuchronnie utrwalone w niezabezpieczonych lokalizacjach, takich jak kontrola źródła.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-252">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="cb9e5-253">W ASP.NET Core w udlać się blazor, poprzednia konfiguracja oparta na języku XML jest zastępowana następującym JSON:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-253">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="cb9e5-254">JSON jest domyślnym formatem konfiguracji; jednak ASP.NET Core obsługuje wiele innych formatów, w tym XML.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-254">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="cb9e5-255">Istnieje również kilka formatów obsługiwanych przez społeczność.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-255">There are also several community-supported formats.</span></span>

<span data-ttu-id="cb9e5-256">Konstruktor w `Startup` klasie projektu Blazor akceptuje `IConfiguration` wystąpienie za pomocą techniki DI znanej jako iniekcja konstruktora:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-256">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    ...
}
```

<span data-ttu-id="cb9e5-257">Domyślnie zmienne środowiskowe, pliki JSON (*appsettings.json* i *appsettings.{ Środowisko}.json*), a opcje wiersza polecenia są rejestrowane jako prawidłowe źródła konfiguracji w obiekcie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-257">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="cb9e5-258">Dostęp do źródeł konfiguracji można `Configuration[key]`uzyskać za pośrednictwem programu .</span><span class="sxs-lookup"><span data-stu-id="cb9e5-258">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="cb9e5-259">Bardziej zaawansowaną techniką jest powiązanie danych konfiguracji z obiektami przy użyciu wzorca opcji.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-259">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="cb9e5-260">Aby uzyskać więcej informacji na temat konfiguracji i wzorca opcji, zobacz [Konfiguracja w ASP.NET](/aspnet/core/fundamentals/configuration/) [wzorzec rdzenia](/aspnet/core/fundamentals/configuration/options)i opcje odpowiednio w ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-260">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="cb9e5-261">Migrowanie dostępu do danych</span><span class="sxs-lookup"><span data-stu-id="cb9e5-261">Migrate data access</span></span>

<span data-ttu-id="cb9e5-262">Dostęp do danych jest ważnym aspektem każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-262">Data access is an important aspect of any app.</span></span> <span data-ttu-id="cb9e5-263">Projekt eShop przechowuje informacje o katalogu w bazie danych i pobiera dane z Entity Framework (EF) 6.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-263">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="cb9e5-264">Ponieważ EF 6 jest obsługiwany w programie .NET Core 3.0, projekt może nadal go używać.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-264">Since EF 6 is supported in .NET Core 3.0, the project can continue to use it.</span></span>

<span data-ttu-id="cb9e5-265">W sklepie internetowym konieczne były następujące zmiany związane z EF:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-265">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="cb9e5-266">W .NET Framework `DbContext` obiekt akceptuje ciąg *formularza name=ConnectionString* i używa ciągu `ConfigurationManager.AppSettings[ConnectionString]` połączenia do połączenia.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-266">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="cb9e5-267">W .NET Core nie jest to obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-267">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="cb9e5-268">Należy podać parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-268">The connection string must be supplied.</span></span>
- <span data-ttu-id="cb9e5-269">Dostęp do bazy danych był dostępny w sposób synchroniczne.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-269">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="cb9e5-270">Chociaż to działa, skalowalność może ucierpieć.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-270">Though this works, scalability may suffer.</span></span> <span data-ttu-id="cb9e5-271">Ta logika powinna zostać przeniesiona do wzorca asynchroniowego.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-271">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="cb9e5-272">Chociaż nie ma tej samej natywnej obsługi powiązania zestawu danych, Blazor zapewnia elastyczność i moc dzięki obsłudze języka C# na stronie Razor.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-272">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="cb9e5-273">Na przykład można wykonywać obliczenia i wyświetlać wynik.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-273">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="cb9e5-274">Aby uzyskać więcej informacji na temat wzorców danych w blazor, zobacz rozdział [Dostęp do danych.](data.md)</span><span class="sxs-lookup"><span data-stu-id="cb9e5-274">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="cb9e5-275">Zmiany w architekturze</span><span class="sxs-lookup"><span data-stu-id="cb9e5-275">Architectural changes</span></span>

<span data-ttu-id="cb9e5-276">Wreszcie, istnieją pewne ważne różnice architektoniczne do rozważenia podczas migracji do Blazor.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-276">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="cb9e5-277">Wiele z tych zmian ma zastosowanie do czegokolwiek opartego na programie .NET Core lub ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-277">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="cb9e5-278">Ponieważ Blazor jest zbudowany na .NET Core, istnieją kwestie dotyczące zapewnienia obsługi w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-278">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="cb9e5-279">Niektóre z głównych zmian obejmują usunięcie następujących funkcji:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-279">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="cb9e5-280">Wiele appdomains</span><span class="sxs-lookup"><span data-stu-id="cb9e5-280">Multiple AppDomains</span></span>
- <span data-ttu-id="cb9e5-281">Usług zdalnych</span><span class="sxs-lookup"><span data-stu-id="cb9e5-281">Remoting</span></span>
- <span data-ttu-id="cb9e5-282">Zabezpieczenia dostępu kodu (CAS)</span><span class="sxs-lookup"><span data-stu-id="cb9e5-282">Code Access Security (CAS)</span></span>
- <span data-ttu-id="cb9e5-283">Przejrzystość zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="cb9e5-283">Security Transparency</span></span>

<span data-ttu-id="cb9e5-284">Aby uzyskać więcej informacji na temat technik umożliwiających identyfikację niezbędnych zmian do obsługi uruchomionych w programie .NET Core, zobacz [Port kodu z programu .NET Framework do platformy .NET Core](/dotnet/core/porting).</span><span class="sxs-lookup"><span data-stu-id="cb9e5-284">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](/dotnet/core/porting).</span></span>

<span data-ttu-id="cb9e5-285">ASP.NET Core jest przeprojektowaną wersją ASP.NET i ma pewne zmiany, które początkowo mogą nie wydawać się oczywiste.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-285">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="cb9e5-286">Główne zmiany to:</span><span class="sxs-lookup"><span data-stu-id="cb9e5-286">The main changes are:</span></span>

- <span data-ttu-id="cb9e5-287">Brak kontekstu synchronizacji, co `HttpContext.Current`oznacza, że nie ma `Thread.CurrentPrincipal`, lub innych statycznych akcesorów</span><span class="sxs-lookup"><span data-stu-id="cb9e5-287">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="cb9e5-288">Brak kopiowania w tle</span><span class="sxs-lookup"><span data-stu-id="cb9e5-288">No shadow copying</span></span>
- <span data-ttu-id="cb9e5-289">Brak kolejki żądań</span><span class="sxs-lookup"><span data-stu-id="cb9e5-289">No request queue</span></span>

<span data-ttu-id="cb9e5-290">Wiele operacji w ASP.NET Core są asynchroniczne, co umożliwia łatwiejsze odciążanie zadań związanych we/wy.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-290">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="cb9e5-291">Ważne jest, aby nigdy `Task.Wait()` nie `Task.GetResult()`blokować przy użyciu lub , które mogą szybko wyczerpywać zasoby puli wątków.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-291">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="cb9e5-292">Wniosek dotyczący migracji</span><span class="sxs-lookup"><span data-stu-id="cb9e5-292">Migration conclusion</span></span>

<span data-ttu-id="cb9e5-293">W tym momencie widzieliście wiele przykładów tego, czego potrzeba, aby przenieść projekt formularzy sieci Web do Blazora.</span><span class="sxs-lookup"><span data-stu-id="cb9e5-293">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="cb9e5-294">Pełny przykład można znaleźć w projekcie [eShopOnBlazor.](https://github.com/dotnet-architecture/eShopOnBlazor)</span><span class="sxs-lookup"><span data-stu-id="cb9e5-294">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="cb9e5-295">Wstecz</span><span class="sxs-lookup"><span data-stu-id="cb9e5-295">Previous</span></span>](security-authentication-authorization.md)
