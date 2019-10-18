---
title: Migrowanie z formularzy sieci Web ASP.NET do Blazor
description: Dowiedz się, jak podejście do migracji istniejącej aplikacji ASP.NET Web Forms do Blazor.
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: 78742fc0d998a70c6e3992041d1fa62f2fe53f39
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520281"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a><span data-ttu-id="99fc3-103">Migrowanie z formularzy sieci Web ASP.NET do Blazor</span><span class="sxs-lookup"><span data-stu-id="99fc3-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="99fc3-104">Migrowanie bazy kodu z formularzy sieci Web ASP.NET do Blazor to czasochłonne zadanie, które wymaga planowania.</span><span class="sxs-lookup"><span data-stu-id="99fc3-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="99fc3-105">W tym rozdziale opisano proces.</span><span class="sxs-lookup"><span data-stu-id="99fc3-105">This chapter outlines the process.</span></span> <span data-ttu-id="99fc3-106">Oto, co może ułatwić przejście aplikacji do architektury *N-warstwowej* , co w przypadku, gdy model aplikacji (w tym przypadku formularzy sieci Web) jest oddzielony od logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="99fc3-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="99fc3-107">To logiczne rozdzielenie warstw sprawia, że musi on zostać przeniesiony do platformy .NET Core i Blazor.</span><span class="sxs-lookup"><span data-stu-id="99fc3-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="99fc3-108">W tym przykładzie jest używana aplikacja eShop dostępna w witrynie [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) .</span><span class="sxs-lookup"><span data-stu-id="99fc3-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="99fc3-109">eShop to usługa wykazu, która zapewnia możliwości CRUD za pośrednictwem wpisów i walidacji formularza.</span><span class="sxs-lookup"><span data-stu-id="99fc3-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="99fc3-110">Dlaczego należy zmigrować działającą aplikację do Blazor?</span><span class="sxs-lookup"><span data-stu-id="99fc3-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="99fc3-111">Wiele razy nie jest potrzebne.</span><span class="sxs-lookup"><span data-stu-id="99fc3-111">Many times, there's no need.</span></span> <span data-ttu-id="99fc3-112">Formularze sieci Web ASP.NET będą nadal obsługiwane przez wiele lat.</span><span class="sxs-lookup"><span data-stu-id="99fc3-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="99fc3-113">Jednak wiele funkcji oferowanych przez program Blazor jest obsługiwanych tylko w zmigrowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="99fc3-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="99fc3-114">Takie funkcje obejmują:</span><span class="sxs-lookup"><span data-stu-id="99fc3-114">Such features include:</span></span>

- <span data-ttu-id="99fc3-115">Ulepszenia wydajności w strukturze, takie jak `Span<T>`</span><span class="sxs-lookup"><span data-stu-id="99fc3-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="99fc3-116">Możliwość uruchamiania jako zestaw webassembly</span><span class="sxs-lookup"><span data-stu-id="99fc3-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="99fc3-117">Obsługa wielu platform dla systemów Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="99fc3-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="99fc3-118">Wdrożenie lokalne aplikacji lub wdrożenie platformy udostępnionej bez wpływu na inne aplikacje</span><span class="sxs-lookup"><span data-stu-id="99fc3-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="99fc3-119">Jeśli te lub inne nowe funkcje są wystarczająco atrakcyjne, może wystąpić wartość migrowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="99fc3-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="99fc3-120">Migracja może mieć różne kształty; może to być cała aplikacja lub tylko niektóre punkty końcowe, które wymagają wprowadzenia zmian.</span><span class="sxs-lookup"><span data-stu-id="99fc3-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="99fc3-121">Decyzja o migracji jest ostatecznie oparta na problemach z firmą, które mają zostać rozwiązane przez dewelopera.</span><span class="sxs-lookup"><span data-stu-id="99fc3-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="99fc3-122">Klient po stronie serwera a hosting po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="99fc3-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="99fc3-123">Zgodnie z opisem w rozdziale [hosting modeli hostingu](hosting-models.md) aplikacja Blazor może być hostowana na dwa różne sposoby: po stronie serwera i po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="99fc3-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="99fc3-124">Model po stronie serwera korzysta z połączeń ASP.NET Core sygnalizujących, aby zarządzać aktualizacjami modelu DOM podczas uruchamiania dowolnego rzeczywistego kodu na serwerze.</span><span class="sxs-lookup"><span data-stu-id="99fc3-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="99fc3-125">Model po stronie klienta jest uruchamiany jako zestaw webassembly w przeglądarce i nie wymaga połączenia z serwerem.</span><span class="sxs-lookup"><span data-stu-id="99fc3-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="99fc3-126">Istnieje wiele różnic, które mogą mieć wpływ na to, co jest najlepsze dla określonej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="99fc3-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="99fc3-127">Uruchamianie jako zestaw webassembly nadal trwa opracowywanie i może nie obsługiwać wszystkich funkcji (takich jak wątkowość) w bieżącym czasie</span><span class="sxs-lookup"><span data-stu-id="99fc3-127">Running as WebAssembly is still in development and may not support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="99fc3-128">Komunikacja między klientem a serwerem może powodować problemy z opóźnieniami w trybie po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="99fc3-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="99fc3-129">Dostęp do baz danych i wewnętrznych lub chronionych usług wymaga oddzielnej usługi z hostingiem po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="99fc3-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="99fc3-130">W momencie pisania model po stronie serwera bardziej przypomina formularze sieci Web.</span><span class="sxs-lookup"><span data-stu-id="99fc3-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="99fc3-131">Większość tego rozdziału koncentruje się na modelu hostingu po stronie serwera, ponieważ jest on gotowy do produkcji.</span><span class="sxs-lookup"><span data-stu-id="99fc3-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="99fc3-132">Tworzenie nowego projektu</span><span class="sxs-lookup"><span data-stu-id="99fc3-132">Create a new project</span></span>

<span data-ttu-id="99fc3-133">Ten krok początkowej migracji polega na utworzeniu nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="99fc3-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="99fc3-134">Ten typ projektu jest oparty na projektach w stylu zestawu SDK platformy .NET Core i upraszcza wiele standardowych, które były używane w poprzednich formatach projektu.</span><span class="sxs-lookup"><span data-stu-id="99fc3-134">This project type is based on the SDK style projects of .NET Core and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="99fc3-135">Aby uzyskać więcej informacji, zobacz rozdział dotyczący [struktury projektu](project-structure.md).</span><span class="sxs-lookup"><span data-stu-id="99fc3-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="99fc3-136">Po utworzeniu projektu Zainstaluj biblioteki, które były używane w poprzednim projekcie.</span><span class="sxs-lookup"><span data-stu-id="99fc3-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="99fc3-137">W starszych projektach formularzy sieci Web może zostać użyty plik *Packages. config* w celu wyświetlenia listy wymaganych pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="99fc3-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="99fc3-138">W nowym projekcie w stylu zestawu SDK *pakiet Packages. config* został zastąpiony `<PackageReference>` elementami w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="99fc3-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="99fc3-139">Zaletą tego podejścia jest to, że wszystkie zależności są instalowane w sposób przechodni.</span><span class="sxs-lookup"><span data-stu-id="99fc3-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="99fc3-140">Można wyświetlić tylko te zależności najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="99fc3-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="99fc3-141">Wiele zależności, z których korzystasz, jest dostępnych dla platformy .NET Core, w tym Entity Framework 6 i log4net.</span><span class="sxs-lookup"><span data-stu-id="99fc3-141">Many of the dependencies you're using are available for .NET Core, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="99fc3-142">W przypadku braku dostępnej wersji programu .NET Core lub .NET Standard wersja .NET Framework może być często używana.</span><span class="sxs-lookup"><span data-stu-id="99fc3-142">If there's no .NET Core or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="99fc3-143">Przebieg może się różnić.</span><span class="sxs-lookup"><span data-stu-id="99fc3-143">Your mileage may vary.</span></span> <span data-ttu-id="99fc3-144">Każdy używany interfejs API, który nie jest dostępny w środowisku .NET Core powoduje błąd czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="99fc3-144">Any API used that isn't available in .NET Core causes a runtime error.</span></span> <span data-ttu-id="99fc3-145">Program Visual Studio powiadamia o takich pakietach.</span><span class="sxs-lookup"><span data-stu-id="99fc3-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="99fc3-146">Żółta ikona pojawia się w węźle **odwołania** projektu w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="99fc3-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="99fc3-147">W projekcie eShop opartym na Blazor można zobaczyć zainstalowane pakiety.</span><span class="sxs-lookup"><span data-stu-id="99fc3-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="99fc3-148">Wcześniej plik *Packages. config* został wymieniony w każdym pakiecie używanym w projekcie, co spowodowało niemal 50 wierszy.</span><span class="sxs-lookup"><span data-stu-id="99fc3-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="99fc3-149">Fragment kodu *Package. config* jest następujący:</span><span class="sxs-lookup"><span data-stu-id="99fc3-149">A snippet of *packages.config* is:</span></span>

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

<span data-ttu-id="99fc3-150">Element `<packages>` zawiera wszystkie wymagane zależności.</span><span class="sxs-lookup"><span data-stu-id="99fc3-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="99fc3-151">Trudno jest zidentyfikować, które z tych pakietów są uwzględniane, ponieważ są one wymagane.</span><span class="sxs-lookup"><span data-stu-id="99fc3-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="99fc3-152">Niektóre elementy `<package>` są wyświetlane po prostu do zaspokajania potrzeb wymaganych zależności.</span><span class="sxs-lookup"><span data-stu-id="99fc3-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="99fc3-153">Projekt Blazor zawiera listę zależności, które są wymagane w ramach elementu `<ItemGroup>` w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="99fc3-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

<span data-ttu-id="99fc3-154">Jednym pakietem NuGet, który upraszcza życie deweloperów formularzy sieci Web, jest [pakiet zgodności systemu Windows](/dotnet/core/porting/windows-compat-pack).</span><span class="sxs-lookup"><span data-stu-id="99fc3-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](/dotnet/core/porting/windows-compat-pack).</span></span> <span data-ttu-id="99fc3-155">Mimo że platforma .NET Core jest międzyplatformowa, niektóre funkcje są dostępne tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="99fc3-155">Although .NET Core is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="99fc3-156">Funkcje specyficzne dla systemu Windows są udostępniane przez zainstalowanie pakietu zgodności.</span><span class="sxs-lookup"><span data-stu-id="99fc3-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="99fc3-157">Przykłady takich funkcji obejmują rejestr, WMI i usługi katalogowe.</span><span class="sxs-lookup"><span data-stu-id="99fc3-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="99fc3-158">Pakiet dodaje około 20 000 interfejsów API i aktywuje wiele usług, za pomocą których użytkownik może już znać.</span><span class="sxs-lookup"><span data-stu-id="99fc3-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="99fc3-159">Projekt eShop nie wymaga pakietu zgodności. ale jeśli projekty korzystają z funkcji specyficznych dla systemu Windows, pakiet ułatwia pracę z migracją.</span><span class="sxs-lookup"><span data-stu-id="99fc3-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="99fc3-160">Włącz proces uruchamiania</span><span class="sxs-lookup"><span data-stu-id="99fc3-160">Enable startup process</span></span>

<span data-ttu-id="99fc3-161">Proces uruchamiania programu Blazor został zmieniony z formularzy sieci Web i wygląda podobnie jak w przypadku innych usług ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="99fc3-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="99fc3-162">Po stronie serwera składniki Blazor są uruchamiane w ramach normalnej aplikacji ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="99fc3-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="99fc3-163">W przypadku hostowania w przeglądarce z zestawem webassembly składniki Blazor używają podobnego modelu hostingu.</span><span class="sxs-lookup"><span data-stu-id="99fc3-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="99fc3-164">Różnica polega na tym, że składniki są uruchamiane jako osobna usługa z dowolnego procesu zaplecza.</span><span class="sxs-lookup"><span data-stu-id="99fc3-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="99fc3-165">W obu przypadkach uruchamianie jest podobne.</span><span class="sxs-lookup"><span data-stu-id="99fc3-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="99fc3-166">Plik *Global.asax.cs* jest domyślną stroną startową dla projektów formularzy sieci Web.</span><span class="sxs-lookup"><span data-stu-id="99fc3-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="99fc3-167">W projekcie eShop ten plik konfiguruje kontener Inversion of Control (IoC) i obsługuje różne zdarzenia cyklu życia aplikacji lub żądania.</span><span class="sxs-lookup"><span data-stu-id="99fc3-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="99fc3-168">Niektóre z tych zdarzeń są obsługiwane za pomocą oprogramowania pośredniczącego (takiego jak `Application_BeginRequest`).</span><span class="sxs-lookup"><span data-stu-id="99fc3-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="99fc3-169">Inne zdarzenia wymagają zastąpienia określonych usług za pośrednictwem iniekcji zależności (DI).</span><span class="sxs-lookup"><span data-stu-id="99fc3-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="99fc3-170">Na przykład plik *Global.asax.cs* dla eshop zawiera następujący kod:</span><span class="sxs-lookup"><span data-stu-id="99fc3-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

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

<span data-ttu-id="99fc3-171">Poprzedni plik stał się klasą `Startup` w Blazor po stronie serwera:</span><span class="sxs-lookup"><span data-stu-id="99fc3-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

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

<span data-ttu-id="99fc3-172">Jedną z znaczących zmian, które można zauważyć w formularzach sieci Web, jest wyeksponowanie DI.</span><span class="sxs-lookup"><span data-stu-id="99fc3-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="99fc3-173">DI ma regułę identyfikatora GUID w projekcie ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="99fc3-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="99fc3-174">Obsługuje on dostosowanie niemal wszystkich aspektów ASP.NET Core Framework.</span><span class="sxs-lookup"><span data-stu-id="99fc3-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="99fc3-175">Istnieje nawet wbudowany dostawca usług, który może być używany w wielu scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="99fc3-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="99fc3-176">Jeśli wymagane jest dalsze dostosowanie, może ono być obsługiwane przez wiele projektów społeczności.</span><span class="sxs-lookup"><span data-stu-id="99fc3-176">If more customization is required, it can be supported by the many community projects.</span></span> <span data-ttu-id="99fc3-177">Na przykład możesz przenieść swoją inwestycję w inną firmę.</span><span class="sxs-lookup"><span data-stu-id="99fc3-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="99fc3-178">W oryginalnej aplikacji eShop istnieje pewna Konfiguracja zarządzania sesją.</span><span class="sxs-lookup"><span data-stu-id="99fc3-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="99fc3-179">Ponieważ Blazor po stronie serwera używa sygnałów ASP.NET Core do komunikacji, stan sesji nie jest obsługiwany, ponieważ połączenia mogą wystąpić niezależnie od kontekstu HTTP.</span><span class="sxs-lookup"><span data-stu-id="99fc3-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="99fc3-180">Aplikacja, która używa stanu sesji, wymaga ponownej architektury przed uruchomieniem aplikacji Blazor.</span><span class="sxs-lookup"><span data-stu-id="99fc3-180">An app that uses session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="99fc3-181">Aby uzyskać więcej informacji o uruchamianiu aplikacji, zobacz [Uruchamianie aplikacji](app-startup.md).</span><span class="sxs-lookup"><span data-stu-id="99fc3-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="99fc3-182">Migrowanie modułów i programów obsługi HTTP do oprogramowania pośredniczącego</span><span class="sxs-lookup"><span data-stu-id="99fc3-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="99fc3-183">Moduły i programy obsługi HTTP są typowymi wzorcami w formularzach sieci Web w celu kontrolowania potoku żądań HTTP.</span><span class="sxs-lookup"><span data-stu-id="99fc3-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="99fc3-184">Klasy implementujące `IHttpModule` lub `IHttpHandler` można rejestrować i przetwarzać żądania przychodzące.</span><span class="sxs-lookup"><span data-stu-id="99fc3-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="99fc3-185">Formularze sieci Web konfigurują moduły i programy obsługi w pliku *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="99fc3-185">Web Forms configures modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="99fc3-186">Formularze sieci Web są również intensywnie oparte na obsłudze zdarzeń cyklu życia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="99fc3-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="99fc3-187">ASP.NET Core zamiast tego używa oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="99fc3-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="99fc3-188">Middlewares są zarejestrowane w metodzie `Configure` klasy `Startup`.</span><span class="sxs-lookup"><span data-stu-id="99fc3-188">Middlewares are registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="99fc3-189">Kolejność wykonywania oprogramowania pośredniczącego zależy od kolejności rejestracji.</span><span class="sxs-lookup"><span data-stu-id="99fc3-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="99fc3-190">W sekcji [Włączanie procesu uruchamiania](#enable-startup-process) zdarzenie cyklu życia zostało zgłoszone przez formularze sieci Web jako metodę `Application_BeginRequest`.</span><span class="sxs-lookup"><span data-stu-id="99fc3-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="99fc3-191">To zdarzenie nie jest dostępne w ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="99fc3-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="99fc3-192">Jednym ze sposobów osiągnięcia tego zachowania jest wdrożenie oprogramowania pośredniczącego, jak pokazano w przykładzie pliku *Startup.cs* .</span><span class="sxs-lookup"><span data-stu-id="99fc3-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="99fc3-193">To oprogramowanie pośredniczące wykonuje tę samą logikę, a następnie przekazuje kontrolę do kolejnej procedury obsługi w potoku programu pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="99fc3-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="99fc3-194">Aby uzyskać więcej informacji na temat migrowania modułów i programów obsługi, zobacz [Migrowanie programów obsługi i modułów HTTP w celu ASP.NET Core oprogramowania pośredniczącego](/aspnet/core/migration/http-modules).</span><span class="sxs-lookup"><span data-stu-id="99fc3-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="99fc3-195">Migrowanie plików statycznych</span><span class="sxs-lookup"><span data-stu-id="99fc3-195">Migrate static files</span></span>

<span data-ttu-id="99fc3-196">Aby można było obsługiwać pliki statyczne (na przykład HTML, CSS, obrazy i JavaScript), pliki muszą być udostępniane przez oprogramowanie pośredniczące.</span><span class="sxs-lookup"><span data-stu-id="99fc3-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="99fc3-197">Wywołanie metody `UseStaticFiles` umożliwia obsługę plików statycznych z ścieżki katalogu głównego sieci Web.</span><span class="sxs-lookup"><span data-stu-id="99fc3-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="99fc3-198">Domyślny katalog główny sieci Web to *wwwroot*, ale można go dostosować.</span><span class="sxs-lookup"><span data-stu-id="99fc3-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="99fc3-199">Jak zawarta w metodzie `Configure` klasy `Startup` eShop:</span><span class="sxs-lookup"><span data-stu-id="99fc3-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="99fc3-200">Projekt eShop umożliwia dostęp do podstawowego pliku statycznego.</span><span class="sxs-lookup"><span data-stu-id="99fc3-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="99fc3-201">Istnieje wiele dostosowań dostępnych w przypadku dostępu do pliku statycznego.</span><span class="sxs-lookup"><span data-stu-id="99fc3-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="99fc3-202">Aby uzyskać informacje na temat włączania plików domyślnych lub przeglądarki plików, zobacz [pliki statyczne w ASP.NET Core](/aspnet/core/fundamentals/static-files).</span><span class="sxs-lookup"><span data-stu-id="99fc3-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="99fc3-203">Migruj konfigurację i minifikacja środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="99fc3-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="99fc3-204">Tworzenie i minifikacja to techniki optymalizacji wydajności umożliwiające zmniejszenie liczby i rozmiaru żądań serwera w celu pobrania określonych typów plików.</span><span class="sxs-lookup"><span data-stu-id="99fc3-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="99fc3-205">JavaScript i CSS są często poddawane pewnej formie minifikacja przed wysłaniem do klienta.</span><span class="sxs-lookup"><span data-stu-id="99fc3-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="99fc3-206">W programie ASP.NET Web Forms te optymalizacje są obsługiwane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="99fc3-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="99fc3-207">Konwencje optymalizacji są definiowane jako plik *App_Start/BundleConfig. cs* .</span><span class="sxs-lookup"><span data-stu-id="99fc3-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="99fc3-208">W ASP.NET Core zostanie przyjęte bardziej deklaracyjne podejście.</span><span class="sxs-lookup"><span data-stu-id="99fc3-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="99fc3-209">Plik zawiera listę plików, które mają być zminimalizowanego, oraz określonych ustawień minifikacja.</span><span class="sxs-lookup"><span data-stu-id="99fc3-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="99fc3-210">Aby uzyskać więcej informacji na temat grupowania i minifikacja, zobacz [zestawy i zminifikować zasobów statycznych w ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span><span class="sxs-lookup"><span data-stu-id="99fc3-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="99fc3-211">Migrowanie stron ASPX</span><span class="sxs-lookup"><span data-stu-id="99fc3-211">Migrate ASPX pages</span></span>

<span data-ttu-id="99fc3-212">Strona w aplikacji formularzy sieci Web jest plikiem z rozszerzeniem *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="99fc3-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="99fc3-213">Strona formularzy sieci Web może być często mapowana na składnik programu Blazor.</span><span class="sxs-lookup"><span data-stu-id="99fc3-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="99fc3-214">Składnik Blazor jest tworzony w pliku z rozszerzeniem *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="99fc3-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="99fc3-215">W przypadku projektu eShop pięć stron jest konwertowanych na stronę Razor.</span><span class="sxs-lookup"><span data-stu-id="99fc3-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="99fc3-216">Na przykład widok szczegółów składa się z trzech plików w projekcie formularzy sieci Web: *details. aspx*, *details.aspx.cs*i *details.aspx.Designer.cs*.</span><span class="sxs-lookup"><span data-stu-id="99fc3-216">For example, the details view is comprised of three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="99fc3-217">Podczas konwertowania na Blazor, kod źródłowy i znaczniki są łączone w *szczegóły. Razor*.</span><span class="sxs-lookup"><span data-stu-id="99fc3-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="99fc3-218">Kompilacja Razor (równoważna z plikami *Designer.cs* ) jest przechowywana w katalogu *obj* i nie jest domyślnie wyświetlana w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="99fc3-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and aren't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="99fc3-219">Strona formularzy sieci Web składa się z następujących oznaczeń:</span><span class="sxs-lookup"><span data-stu-id="99fc3-219">The Web Forms page consists of the following markup:</span></span>

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

<span data-ttu-id="99fc3-220">Poprzedzający kod znacznika zawiera następujący kod:</span><span class="sxs-lookup"><span data-stu-id="99fc3-220">The preceding markup's code-behind includes the following code:</span></span>

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

<span data-ttu-id="99fc3-221">W przypadku przekonwertowania na Blazor Strona formularzy sieci Web tłumaczy do następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="99fc3-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

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

<span data-ttu-id="99fc3-222">Zauważ, że kod i znaczniki są w tym samym pliku.</span><span class="sxs-lookup"><span data-stu-id="99fc3-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="99fc3-223">Wszystkie wymagane usługi są udostępniane z atrybutem `@inject`.</span><span class="sxs-lookup"><span data-stu-id="99fc3-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="99fc3-224">Za dyrektywę `@page` można uzyskać dostęp do tej strony przy użyciu trasy `Catalog/Details/{id}`.</span><span class="sxs-lookup"><span data-stu-id="99fc3-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="99fc3-225">Wartość symbolu zastępczego `{id}` trasy została ograniczona do liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="99fc3-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="99fc3-226">Zgodnie z opisem w sekcji [Routing](pages-routing-layouts.md) , w przeciwieństwie do formularzy sieci Web, składnik Razor jawnie określa swoją trasę i wszystkie parametry, które są zawarte.</span><span class="sxs-lookup"><span data-stu-id="99fc3-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="99fc3-227">Wiele kontrolek formularzy sieci Web może nie mieć dokładnych odpowiedników w Blazor.</span><span class="sxs-lookup"><span data-stu-id="99fc3-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="99fc3-228">Często istnieje odpowiednik fragmentu kodu HTML, który będzie służyć do tego samego celu.</span><span class="sxs-lookup"><span data-stu-id="99fc3-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="99fc3-229">Na przykład formant `<asp:Label />` można zamienić na element HTML `<label>`.</span><span class="sxs-lookup"><span data-stu-id="99fc3-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-blazor"></a><span data-ttu-id="99fc3-230">Walidacja modelu w Blazor</span><span class="sxs-lookup"><span data-stu-id="99fc3-230">Model validation in Blazor</span></span>

<span data-ttu-id="99fc3-231">Jeśli kod formularzy sieci Web zawiera walidację, można przekazać wiele z nich, aby nie było zmian.</span><span class="sxs-lookup"><span data-stu-id="99fc3-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="99fc3-232">Zaletą działania w programie Blazor jest możliwość uruchamiania tej samej logiki walidacji bez potrzeby korzystania z niestandardowego języka JavaScript.</span><span class="sxs-lookup"><span data-stu-id="99fc3-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="99fc3-233">Adnotacje danych umożliwiają łatwe sprawdzanie poprawności modeli.</span><span class="sxs-lookup"><span data-stu-id="99fc3-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="99fc3-234">Na przykład strona *Create. aspx* zawiera formularz wprowadzania danych z walidacją.</span><span class="sxs-lookup"><span data-stu-id="99fc3-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="99fc3-235">Przykładowy fragment będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="99fc3-235">An example snippet would look like this:</span></span>

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

<span data-ttu-id="99fc3-236">W Blazor odpowiednik znacznika jest dostarczany w pliku *Create. Razor* :</span><span class="sxs-lookup"><span data-stu-id="99fc3-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

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

<span data-ttu-id="99fc3-237">Kontekst `EditForm` obejmuje obsługę walidacji i może być zawijany wokół danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="99fc3-237">The `EditForm` context includes validation support and can be wrapped around input.</span></span> <span data-ttu-id="99fc3-238">Adnotacje danych są typowym sposobem dodawania walidacji.</span><span class="sxs-lookup"><span data-stu-id="99fc3-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="99fc3-239">Takie wsparcie sprawdzania poprawności można dodać za pośrednictwem składnika `DataAnnotationsValidator`.</span><span class="sxs-lookup"><span data-stu-id="99fc3-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="99fc3-240">Aby uzyskać więcej informacji na temat tego mechanizmu, zobacz [ASP.NET Core Blazor formularzy i walidacji](/aspnet/core/blazor/forms-validation).</span><span class="sxs-lookup"><span data-stu-id="99fc3-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-built-in-web-forms-controls"></a><span data-ttu-id="99fc3-241">Migrowanie wbudowanych formantów formularzy sieci Web</span><span class="sxs-lookup"><span data-stu-id="99fc3-241">Migrate built-in Web Forms controls</span></span>

<span data-ttu-id="99fc3-242">*Ta zawartość zostanie wkrótce udostępniona.*</span><span class="sxs-lookup"><span data-stu-id="99fc3-242">*This content is coming soon.*</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="99fc3-243">Migruj konfigurację</span><span class="sxs-lookup"><span data-stu-id="99fc3-243">Migrate configuration</span></span>

<span data-ttu-id="99fc3-244">W projekcie formularzy sieci Web dane konfiguracyjne są najczęściej przechowywane w pliku *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="99fc3-244">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="99fc3-245">Do danych konfiguracyjnych uzyskuje się dostęp przy użyciu `ConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="99fc3-245">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="99fc3-246">Usługi były często wymagane do analizowania obiektów.</span><span class="sxs-lookup"><span data-stu-id="99fc3-246">Services were often required to parse objects.</span></span> <span data-ttu-id="99fc3-247">Dzięki .NET Framework 4.7.2 można redagować do konfiguracji za pośrednictwem `ConfigurationBuilders`.</span><span class="sxs-lookup"><span data-stu-id="99fc3-247">With .NET Framework 4.7.2, composability was added to configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="99fc3-248">Ci deweloperzy mogą dodawać różne źródła do konfiguracji, która następnie została złożona w czasie wykonywania w celu pobrania niezbędnych wartości.</span><span class="sxs-lookup"><span data-stu-id="99fc3-248">These builders allowed developers to add various sources for configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="99fc3-249">ASP.NET Core wprowadzono elastyczny system konfiguracji, który pozwala zdefiniować źródło lub źródła konfiguracji używane przez aplikację i wdrożenie.</span><span class="sxs-lookup"><span data-stu-id="99fc3-249">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="99fc3-250">Infrastruktura `ConfigurationBuilder`, która może być używana w aplikacji formularzy sieci Web, została modelowana po pojęciach używanych w systemie ASP.NET Core Configuration.</span><span class="sxs-lookup"><span data-stu-id="99fc3-250">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="99fc3-251">W poniższym fragmencie kodu pokazano, jak projekt Web Forms eShop używa *pliku Web. config* do przechowywania wartości konfiguracyjnych:</span><span class="sxs-lookup"><span data-stu-id="99fc3-251">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

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
```

<span data-ttu-id="99fc3-252">Jest ona wspólna dla wpisów tajnych, takich jak parametry połączenia bazy danych, które mają być przechowywane w *pliku Web. config*. Wpisy tajne są bezwątpliwie utrwalane w niezabezpieczonych lokalizacjach, takich jak kontrola źródła.</span><span class="sxs-lookup"><span data-stu-id="99fc3-252">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="99fc3-253">W przypadku Blazor na ASP.NET Core wcześniejsza Konfiguracja oparta na języku XML jest zastępowana następującym kodem JSON:</span><span class="sxs-lookup"><span data-stu-id="99fc3-253">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="99fc3-254">Format JSON jest domyślnym formatem konfiguracji; jednak ASP.NET Core obsługuje wiele innych formatów, w tym XML.</span><span class="sxs-lookup"><span data-stu-id="99fc3-254">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="99fc3-255">Istnieje również kilka formatów obsługiwanych przez społeczność.</span><span class="sxs-lookup"><span data-stu-id="99fc3-255">There are also several community-supported formats.</span></span>

<span data-ttu-id="99fc3-256">Konstruktor w klasie `Startup` projektu Blazor akceptuje wystąpienie `IConfiguration` za pomocą techniki DI znanego jako iniekcja konstruktora:</span><span class="sxs-lookup"><span data-stu-id="99fc3-256">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

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

<span data-ttu-id="99fc3-257">Domyślnie zmienne środowiskowe, pliki JSON (*appSettings. JSON* i *appSettings. { Environment}. JSON*), a opcje wiersza polecenia są rejestrowane jako prawidłowe źródła konfiguracji w obiekcie Configuration.</span><span class="sxs-lookup"><span data-stu-id="99fc3-257">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="99fc3-258">Dostęp do źródeł konfiguracji można uzyskać za pośrednictwem `Configuration[key]`.</span><span class="sxs-lookup"><span data-stu-id="99fc3-258">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="99fc3-259">Bardziej zaawansowaną techniką jest powiązanie danych konfiguracji z obiektami przy użyciu wzorca opcji.</span><span class="sxs-lookup"><span data-stu-id="99fc3-259">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="99fc3-260">Aby uzyskać więcej informacji na temat konfiguracji i wzorca opcji, zobacz odpowiednio [Konfiguracja w ASP.NET Core](/aspnet/core/fundamentals/configuration/) i [wzorzec opcji w ASP.NET Core](/aspnet/core/fundamentals/configuration/options).</span><span class="sxs-lookup"><span data-stu-id="99fc3-260">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="99fc3-261">Migrowanie dostępu do danych</span><span class="sxs-lookup"><span data-stu-id="99fc3-261">Migrate data access</span></span>

<span data-ttu-id="99fc3-262">Dostęp do danych jest ważnym aspektem każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="99fc3-262">Data access is an important aspect of any app.</span></span> <span data-ttu-id="99fc3-263">Projekt eShop przechowuje informacje o katalogu w bazie danych i pobiera dane z Entity Framework (EF) 6.</span><span class="sxs-lookup"><span data-stu-id="99fc3-263">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="99fc3-264">Ponieważ program Dr 6 jest obsługiwany w środowisku .NET Core 3,0, nadal można z niego korzystać.</span><span class="sxs-lookup"><span data-stu-id="99fc3-264">Since EF 6 is supported in .NET Core 3.0, the project can continue to use it.</span></span>

<span data-ttu-id="99fc3-265">Następujące zmiany związane z EF były niezbędne do eShop:</span><span class="sxs-lookup"><span data-stu-id="99fc3-265">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="99fc3-266">W .NET Framework obiekt `DbContext` akceptuje ciąg *nazwa formularza = ConnectionString* i używa parametrów połączenia z `ConfigurationManager.AppSettings[ConnectionString]` do nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="99fc3-266">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="99fc3-267">W programie .NET Core nie jest to obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="99fc3-267">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="99fc3-268">Należy podać parametry połączenia.</span><span class="sxs-lookup"><span data-stu-id="99fc3-268">The connection string must be supplied.</span></span>
- <span data-ttu-id="99fc3-269">Dostęp do bazy danych odbywa się synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="99fc3-269">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="99fc3-270">To działanie może mieć wpływ na skalowalność.</span><span class="sxs-lookup"><span data-stu-id="99fc3-270">Though this works, scalability may suffer.</span></span> <span data-ttu-id="99fc3-271">Ta logika powinna zostać przeniesiona do wzorca asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="99fc3-271">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="99fc3-272">Chociaż nie ma tej samej natywnej obsługi powiązań zestawu danych, Blazor zapewnia elastyczność i moc z C# obsługą na stronie Razor.</span><span class="sxs-lookup"><span data-stu-id="99fc3-272">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="99fc3-273">Na przykład można wykonać obliczenia i wyświetlić wynik.</span><span class="sxs-lookup"><span data-stu-id="99fc3-273">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="99fc3-274">Aby uzyskać więcej informacji na temat wzorców danych w programie Blazor, zobacz rozdział [dostępu do danych](data.md) .</span><span class="sxs-lookup"><span data-stu-id="99fc3-274">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="99fc3-275">Zmiany architektury</span><span class="sxs-lookup"><span data-stu-id="99fc3-275">Architectural changes</span></span>

<span data-ttu-id="99fc3-276">Na koniec należy wziąć pod uwagę pewne istotne różnice w architekturze podczas migracji do Blazor.</span><span class="sxs-lookup"><span data-stu-id="99fc3-276">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="99fc3-277">Wiele z tych zmian ma zastosowanie do wszystkich elementów opartych na platformie .NET Core lub ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="99fc3-277">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="99fc3-278">Ponieważ Blazor jest oparty na oprogramowaniu .NET Core, istnieją zagadnienia dotyczące zapewniania pomocy technicznej na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99fc3-278">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="99fc3-279">Niektóre istotne zmiany obejmują usunięcie następujących funkcji:</span><span class="sxs-lookup"><span data-stu-id="99fc3-279">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="99fc3-280">Wiele domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="99fc3-280">Multiple AppDomains</span></span>
- <span data-ttu-id="99fc3-281">Komunikacji zdalnej</span><span class="sxs-lookup"><span data-stu-id="99fc3-281">Remoting</span></span>
- <span data-ttu-id="99fc3-282">Zabezpieczenia dostępu kodu (CAS)</span><span class="sxs-lookup"><span data-stu-id="99fc3-282">Code Access Security (CAS)</span></span>
- <span data-ttu-id="99fc3-283">Przejrzystość zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="99fc3-283">Security Transparency</span></span>

<span data-ttu-id="99fc3-284">Aby uzyskać więcej informacji na temat technik umożliwiających identyfikację niezbędnych zmian w celu obsługi programu .NET Core, zobacz [Porting Code from .NET Framework to .NET Core](/dotnet/core/porting).</span><span class="sxs-lookup"><span data-stu-id="99fc3-284">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](/dotnet/core/porting).</span></span>

<span data-ttu-id="99fc3-285">ASP.NET Core jest reobrazną wersją ASP.NET i zawiera pewne zmiany, które mogą nie być początkowo oczywiste.</span><span class="sxs-lookup"><span data-stu-id="99fc3-285">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="99fc3-286">Główne zmiany są następujące:</span><span class="sxs-lookup"><span data-stu-id="99fc3-286">The main changes are:</span></span>

- <span data-ttu-id="99fc3-287">Brak kontekstu synchronizacji, co oznacza, że nie ma `HttpContext.Current`, `Thread.CurrentPrincipal` ani innych metod dostępu statycznego</span><span class="sxs-lookup"><span data-stu-id="99fc3-287">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="99fc3-288">Brak kopiowania w tle</span><span class="sxs-lookup"><span data-stu-id="99fc3-288">No shadow copying</span></span>
- <span data-ttu-id="99fc3-289">Brak kolejki żądań</span><span class="sxs-lookup"><span data-stu-id="99fc3-289">No request queue</span></span>

<span data-ttu-id="99fc3-290">Wiele operacji w ASP.NET Core jest asynchronicznych, co umożliwia łatwiejsze ładowanie zadań związanych z operacjami we/wy.</span><span class="sxs-lookup"><span data-stu-id="99fc3-290">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="99fc3-291">Ważne jest, aby nigdy nie blokować przy użyciu `Task.Wait()` lub `Task.GetResult()`, co może szybko wyczerpać zasoby puli wątków.</span><span class="sxs-lookup"><span data-stu-id="99fc3-291">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="99fc3-292">Wniosek o migrację</span><span class="sxs-lookup"><span data-stu-id="99fc3-292">Migration conclusion</span></span>

<span data-ttu-id="99fc3-293">W tym momencie widzisz wiele przykładów potrzebnych do przeniesienia projektu formularzy sieci Web do Blazor.</span><span class="sxs-lookup"><span data-stu-id="99fc3-293">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="99fc3-294">Pełny przykład można znaleźć w projekcie [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) .</span><span class="sxs-lookup"><span data-stu-id="99fc3-294">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="99fc3-295">Ubiegł</span><span class="sxs-lookup"><span data-stu-id="99fc3-295">Previous</span></span>](security-authentication-authorization.md)
