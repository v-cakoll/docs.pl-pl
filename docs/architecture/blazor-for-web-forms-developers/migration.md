---
title: Migrowanie z formularzy sieci Web ASP.NET do Blazor
description: Dowiedz się, jak podejście do migracji istniejącej aplikacji ASP.NET Web Forms do Blazor.
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: b6604e000eaf79bcd8da15d72a3d85713c620851
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191936"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a>Migrowanie z formularzy sieci Web ASP.NET do Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Migrowanie bazy kodu z formularzy sieci Web ASP.NET do Blazor to czasochłonne zadanie, które wymaga planowania. W tym rozdziale opisano proces. Oto, co może ułatwić przejście aplikacji do architektury *N-warstwowej* , co w przypadku, gdy model aplikacji (w tym przypadku formularzy sieci Web) jest oddzielony od logiki biznesowej. To logiczne rozdzielenie warstw sprawia, że musi on zostać przeniesiony do platformy .NET Core i Blazor.

W tym przykładzie jest używana aplikacja eShop dostępna w witrynie [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) . eShop to usługa wykazu, która zapewnia możliwości CRUD za pośrednictwem wpisów i walidacji formularza.

Dlaczego należy zmigrować działającą aplikację do Blazor? Wiele razy nie jest potrzebne. Formularze sieci Web ASP.NET będą nadal obsługiwane przez wiele lat. Jednak wiele funkcji oferowanych przez program Blazor jest obsługiwanych tylko w zmigrowanej aplikacji. Takie funkcje obejmują:

- Ulepszenia wydajności w strukturze, takie jak `Span<T>`
- Możliwość uruchamiania jako zestaw webassembly
- Obsługa wielu platform dla systemów Linux i macOS
- Wdrożenie lokalne aplikacji lub wdrożenie platformy udostępnionej bez wpływu na inne aplikacje

Jeśli te lub inne nowe funkcje są wystarczająco atrakcyjne, może wystąpić wartość migrowania aplikacji. Migracja może mieć różne kształty; może to być cała aplikacja lub tylko niektóre punkty końcowe, które wymagają wprowadzenia zmian. Decyzja o migracji jest ostatecznie oparta na problemach z firmą, które mają zostać rozwiązane przez dewelopera.

## <a name="server-side-versus-client-side-hosting"></a>Klient po stronie serwera a hosting po stronie klienta

Zgodnie z opisem w rozdziale [hosting modeli hostingu](hosting-models.md) aplikacja Blazor może być hostowana na dwa różne sposoby: po stronie serwera i po stronie klienta. Model po stronie serwera korzysta z połączeń ASP.NET Core sygnalizujących, aby zarządzać aktualizacjami modelu DOM podczas uruchamiania dowolnego rzeczywistego kodu na serwerze. Model po stronie klienta jest uruchamiany jako zestaw webassembly w przeglądarce i nie wymaga połączenia z serwerem. Istnieje wiele różnic, które mogą mieć wpływ na to, co jest najlepsze dla określonej aplikacji:

- Uruchamianie jako zestaw webassembly nadal trwa opracowywanie i może nie obsługiwać wszystkich funkcji (takich jak wątkowość) w bieżącym czasie
- Komunikacja między klientem a serwerem może powodować problemy z opóźnieniami w trybie po stronie serwera
- Dostęp do baz danych i wewnętrznych lub chronionych usług wymaga oddzielnej usługi z hostingiem po stronie klienta

W momencie pisania model po stronie serwera bardziej przypomina formularze sieci Web. Większość tego rozdziału koncentruje się na modelu hostingu po stronie serwera, ponieważ jest on gotowy do produkcji.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Ten krok początkowej migracji polega na utworzeniu nowego projektu. Ten typ projektu jest oparty na projektach w stylu zestawu SDK platformy .NET Core i upraszcza wiele standardowych, które były używane w poprzednich formatach projektu. Aby uzyskać więcej informacji, zobacz rozdział dotyczący [struktury projektu](project-structure.md).

Po utworzeniu projektu Zainstaluj biblioteki, które były używane w poprzednim projekcie. W starszych projektach formularzy sieci Web może zostać użyty plik *Packages. config* w celu wyświetlenia listy wymaganych pakietów NuGet. W nowym projekcie w stylu zestawu SDK *pakiet Packages. config* został zastąpiony `<PackageReference>` elementami w pliku projektu. Zaletą tego podejścia jest to, że wszystkie zależności są instalowane w sposób przechodni. Można wyświetlić tylko te zależności najwyższego poziomu.

Wiele zależności, z których korzystasz, jest dostępnych dla platformy .NET Core, w tym Entity Framework 6 i log4net. W przypadku braku dostępnej wersji programu .NET Core lub .NET Standard wersja .NET Framework może być często używana. Przebieg może się różnić. Każdy używany interfejs API, który nie jest dostępny w środowisku .NET Core powoduje błąd czasu wykonywania. Program Visual Studio powiadamia o takich pakietach. Żółta ikona pojawia się w węźle **odwołania** projektu w **Eksplorator rozwiązań**.

W projekcie eShop opartym na Blazor można zobaczyć zainstalowane pakiety. Wcześniej plik *Packages. config* został wymieniony w każdym pakiecie używanym w projekcie, co spowodowało niemal 50 wierszy. Fragment kodu *Package. config* jest następujący:

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

Element `<packages>` zawiera wszystkie wymagane zależności. Trudno jest zidentyfikować, które z tych pakietów są uwzględniane, ponieważ są one wymagane. Niektóre elementy `<package>` są wyświetlane po prostu do zaspokajania potrzeb wymaganych zależności.

Projekt Blazor zawiera listę zależności, które są wymagane w ramach elementu `<ItemGroup>` w pliku projektu:

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

Jednym pakietem NuGet, który upraszcza życie deweloperów formularzy sieci Web, jest [pakiet zgodności systemu Windows](../../core/porting/windows-compat-pack.md). Mimo że platforma .NET Core jest międzyplatformowa, niektóre funkcje są dostępne tylko w systemie Windows. Funkcje specyficzne dla systemu Windows są udostępniane przez zainstalowanie pakietu zgodności. Przykłady takich funkcji obejmują rejestr, WMI i usługi katalogowe. Pakiet dodaje około 20 000 interfejsów API i aktywuje wiele usług, za pomocą których użytkownik może już znać. Projekt eShop nie wymaga pakietu zgodności. ale jeśli projekty korzystają z funkcji specyficznych dla systemu Windows, pakiet ułatwia pracę z migracją.

## <a name="enable-startup-process"></a>Włącz proces uruchamiania

Proces uruchamiania programu Blazor został zmieniony z formularzy sieci Web i wygląda podobnie jak w przypadku innych usług ASP.NET Core. Po stronie serwera składniki Blazor są uruchamiane w ramach normalnej aplikacji ASP.NET Core. W przypadku hostowania w przeglądarce z zestawem webassembly składniki Blazor używają podobnego modelu hostingu. Różnica polega na tym, że składniki są uruchamiane jako osobna usługa z dowolnego procesu zaplecza. W obu przypadkach uruchamianie jest podobne.

Plik *Global.asax.cs* jest domyślną stroną startową dla projektów formularzy sieci Web. W projekcie eShop ten plik konfiguruje kontener Inversion of Control (IoC) i obsługuje różne zdarzenia cyklu życia aplikacji lub żądania. Niektóre z tych zdarzeń są obsługiwane za pomocą oprogramowania pośredniczącego (takiego jak `Application_BeginRequest`). Inne zdarzenia wymagają zastąpienia określonych usług za pośrednictwem iniekcji zależności (DI).

Na przykład plik *Global.asax.cs* dla eshop zawiera następujący kod:

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

Poprzedni plik stał się klasą `Startup` w Blazor po stronie serwera:

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

Jedną z znaczących zmian, które można zauważyć w formularzach sieci Web, jest wyeksponowanie DI. DI ma regułę identyfikatora GUID w projekcie ASP.NET Core. Obsługuje on dostosowanie niemal wszystkich aspektów ASP.NET Core Framework. Istnieje nawet wbudowany dostawca usług, który może być używany w wielu scenariuszach. Jeśli wymagane jest dalsze dostosowanie, może ono być obsługiwane przez wiele projektów społeczności. Na przykład możesz przenieść swoją inwestycję w inną firmę.

W oryginalnej aplikacji eShop istnieje pewna Konfiguracja zarządzania sesją. Ponieważ Blazor po stronie serwera używa sygnałów ASP.NET Core do komunikacji, stan sesji nie jest obsługiwany, ponieważ połączenia mogą wystąpić niezależnie od kontekstu HTTP. Aplikacja, która używa stanu sesji, wymaga ponownej architektury przed uruchomieniem aplikacji Blazor.

Aby uzyskać więcej informacji o uruchamianiu aplikacji, zobacz [Uruchamianie aplikacji](app-startup.md).

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>Migrowanie modułów i programów obsługi HTTP do oprogramowania pośredniczącego

Moduły i programy obsługi HTTP są typowymi wzorcami w formularzach sieci Web w celu kontrolowania potoku żądań HTTP. Klasy implementujące `IHttpModule` lub `IHttpHandler` można rejestrować i przetwarzać żądania przychodzące. Formularze sieci Web konfigurują moduły i programy obsługi w pliku *Web. config* . Formularze sieci Web są również intensywnie oparte na obsłudze zdarzeń cyklu życia aplikacji. ASP.NET Core zamiast tego używa oprogramowania pośredniczącego. Middlewares są zarejestrowane w metodzie `Configure` klasy `Startup`. Kolejność wykonywania oprogramowania pośredniczącego zależy od kolejności rejestracji.

W sekcji [Włączanie procesu uruchamiania](#enable-startup-process) zdarzenie cyklu życia zostało zgłoszone przez formularze sieci Web jako metodę `Application_BeginRequest`. To zdarzenie nie jest dostępne w ASP.NET Core. Jednym ze sposobów osiągnięcia tego zachowania jest wdrożenie oprogramowania pośredniczącego, jak pokazano w przykładzie pliku *Startup.cs* . To oprogramowanie pośredniczące wykonuje tę samą logikę, a następnie przekazuje kontrolę do kolejnej procedury obsługi w potoku programu pośredniczącego.

Aby uzyskać więcej informacji na temat migrowania modułów i programów obsługi, zobacz [Migrowanie programów obsługi i modułów HTTP w celu ASP.NET Core oprogramowania pośredniczącego](/aspnet/core/migration/http-modules).

## <a name="migrate-static-files"></a>Migrowanie plików statycznych

Aby można było obsługiwać pliki statyczne (na przykład HTML, CSS, obrazy i JavaScript), pliki muszą być udostępniane przez oprogramowanie pośredniczące. Wywołanie metody `UseStaticFiles` umożliwia obsługę plików statycznych z ścieżki katalogu głównego sieci Web. Domyślny katalog główny sieci Web to *wwwroot*, ale można go dostosować. Jak zawarta w metodzie `Configure` klasy `Startup` eShop:

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

Projekt eShop umożliwia dostęp do podstawowego pliku statycznego. Istnieje wiele dostosowań dostępnych w przypadku dostępu do pliku statycznego. Aby uzyskać informacje na temat włączania plików domyślnych lub przeglądarki plików, zobacz [pliki statyczne w ASP.NET Core](/aspnet/core/fundamentals/static-files).

## <a name="migrate-runtime-bundling-and-minification-setup"></a>Migruj konfigurację i minifikacja środowiska uruchomieniowego

Tworzenie i minifikacja to techniki optymalizacji wydajności umożliwiające zmniejszenie liczby i rozmiaru żądań serwera w celu pobrania określonych typów plików. JavaScript i CSS są często poddawane pewnej formie minifikacja przed wysłaniem do klienta. W programie ASP.NET Web Forms te optymalizacje są obsługiwane w czasie wykonywania. Konwencje optymalizacji są definiowane jako plik *App_Start/BundleConfig. cs* . W ASP.NET Core zostanie przyjęte bardziej deklaracyjne podejście. Plik zawiera listę plików, które mają być zminimalizowanego, oraz określonych ustawień minifikacja.

Aby uzyskać więcej informacji na temat grupowania i minifikacja, zobacz [zestawy i zminifikować zasobów statycznych w ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).

## <a name="migrate-aspx-pages"></a>Migrowanie stron ASPX

Strona w aplikacji formularzy sieci Web jest plikiem z rozszerzeniem *. aspx* . Strona formularzy sieci Web może być często mapowana na składnik programu Blazor. Składnik Blazor jest tworzony w pliku z rozszerzeniem *. Razor* . W przypadku projektu eShop pięć stron jest konwertowanych na stronę Razor.

Na przykład widok szczegółów składa się z trzech plików w projekcie formularzy sieci Web: *details. aspx*, *details.aspx.cs*i *details.aspx.Designer.cs*. Podczas konwertowania na Blazor, kod źródłowy i znaczniki są łączone w *szczegóły. Razor*. Kompilacja Razor (równoważna z plikami *Designer.cs* ) jest przechowywana w katalogu *obj* i nie jest domyślnie wyświetlana w **Eksplorator rozwiązań**. Strona formularzy sieci Web składa się z następujących oznaczeń:

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

Poprzedzający kod znacznika zawiera następujący kod:

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

W przypadku przekonwertowania na Blazor Strona formularzy sieci Web tłumaczy do następującego kodu:

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

Zauważ, że kod i znaczniki są w tym samym pliku. Wszystkie wymagane usługi są udostępniane z atrybutem `@inject`. Za dyrektywę `@page` można uzyskać dostęp do tej strony przy użyciu trasy `Catalog/Details/{id}`. Wartość symbolu zastępczego `{id}` trasy została ograniczona do liczby całkowitej. Zgodnie z opisem w sekcji [Routing](pages-routing-layouts.md) , w przeciwieństwie do formularzy sieci Web, składnik Razor jawnie określa swoją trasę i wszystkie parametry, które są zawarte. Wiele kontrolek formularzy sieci Web może nie mieć dokładnych odpowiedników w Blazor. Często istnieje odpowiednik fragmentu kodu HTML, który będzie służyć do tego samego celu. Na przykład formant `<asp:Label />` można zamienić na element HTML `<label>`.

### <a name="model-validation-in-blazor"></a>Walidacja modelu w Blazor

Jeśli kod formularzy sieci Web zawiera walidację, można przekazać wiele z nich, aby nie było zmian. Zaletą działania w programie Blazor jest możliwość uruchamiania tej samej logiki walidacji bez potrzeby korzystania z niestandardowego języka JavaScript. Adnotacje danych umożliwiają łatwe sprawdzanie poprawności modeli.

Na przykład strona *Create. aspx* zawiera formularz wprowadzania danych z walidacją. Przykładowy fragment będzie wyglądać następująco:

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

W Blazor odpowiednik znacznika jest dostarczany w pliku *Create. Razor* :

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

Kontekst `EditForm` obejmuje obsługę walidacji i może być zawijany wokół danych wejściowych. Adnotacje danych są typowym sposobem dodawania walidacji. Takie wsparcie sprawdzania poprawności można dodać za pośrednictwem składnika `DataAnnotationsValidator`. Aby uzyskać więcej informacji na temat tego mechanizmu, zobacz [ASP.NET Core Blazor formularzy i walidacji](/aspnet/core/blazor/forms-validation).

## <a name="migrate-built-in-web-forms-controls"></a>Migrowanie wbudowanych formantów formularzy sieci Web

*Ta zawartość zostanie wkrótce udostępniona.*

## <a name="migrate-configuration"></a>Migruj konfigurację

W projekcie formularzy sieci Web dane konfiguracyjne są najczęściej przechowywane w pliku *Web. config* . Do danych konfiguracyjnych uzyskuje się dostęp przy użyciu `ConfigurationManager`. Usługi były często wymagane do analizowania obiektów. Dzięki .NET Framework 4.7.2 można redagować do konfiguracji za pośrednictwem `ConfigurationBuilders`. Ci deweloperzy mogą dodawać różne źródła do konfiguracji, która następnie została złożona w czasie wykonywania w celu pobrania niezbędnych wartości.

ASP.NET Core wprowadzono elastyczny system konfiguracji, który pozwala zdefiniować źródło lub źródła konfiguracji używane przez aplikację i wdrożenie. Infrastruktura `ConfigurationBuilder`, która może być używana w aplikacji formularzy sieci Web, została modelowana po pojęciach używanych w systemie ASP.NET Core Configuration.

W poniższym fragmencie kodu pokazano, jak projekt Web Forms eShop używa *pliku Web. config* do przechowywania wartości konfiguracyjnych:

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

Jest ona wspólna dla wpisów tajnych, takich jak parametry połączenia bazy danych, które mają być przechowywane w *pliku Web. config*. Wpisy tajne są bezwątpliwie utrwalane w niezabezpieczonych lokalizacjach, takich jak kontrola źródła. W przypadku Blazor na ASP.NET Core wcześniejsza Konfiguracja oparta na języku XML jest zastępowana następującym kodem JSON:

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

Format JSON jest domyślnym formatem konfiguracji; jednak ASP.NET Core obsługuje wiele innych formatów, w tym XML. Istnieje również kilka formatów obsługiwanych przez społeczność.

Konstruktor w klasie `Startup` projektu Blazor akceptuje wystąpienie `IConfiguration` za pomocą techniki DI znanego jako iniekcja konstruktora:

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

Domyślnie zmienne środowiskowe, pliki JSON (*appSettings. JSON* i *appSettings. { Environment}. JSON*), a opcje wiersza polecenia są rejestrowane jako prawidłowe źródła konfiguracji w obiekcie Configuration. Dostęp do źródeł konfiguracji można uzyskać za pośrednictwem `Configuration[key]`. Bardziej zaawansowaną techniką jest powiązanie danych konfiguracji z obiektami przy użyciu wzorca opcji. Aby uzyskać więcej informacji na temat konfiguracji i wzorca opcji, zobacz odpowiednio [Konfiguracja w ASP.NET Core](/aspnet/core/fundamentals/configuration/) i [wzorzec opcji w ASP.NET Core](/aspnet/core/fundamentals/configuration/options).

## <a name="migrate-data-access"></a>Migrowanie dostępu do danych

Dostęp do danych jest ważnym aspektem każdej aplikacji. Projekt eShop przechowuje informacje o katalogu w bazie danych i pobiera dane z Entity Framework (EF) 6. Ponieważ program Dr 6 jest obsługiwany w środowisku .NET Core 3,0, nadal można z niego korzystać.

Następujące zmiany związane z EF były niezbędne do eShop:

- W .NET Framework obiekt `DbContext` akceptuje ciąg *nazwa formularza = ConnectionString* i używa parametrów połączenia z `ConfigurationManager.AppSettings[ConnectionString]` do nawiązania połączenia. W programie .NET Core nie jest to obsługiwane. Należy podać parametry połączenia.
- Dostęp do bazy danych odbywa się synchronicznie. To działanie może mieć wpływ na skalowalność. Ta logika powinna zostać przeniesiona do wzorca asynchronicznego.

Chociaż nie ma tej samej natywnej obsługi powiązań zestawu danych, Blazor zapewnia elastyczność i moc z C# obsługą na stronie Razor. Na przykład można wykonać obliczenia i wyświetlić wynik. Aby uzyskać więcej informacji na temat wzorców danych w programie Blazor, zobacz rozdział [dostępu do danych](data.md) .

## <a name="architectural-changes"></a>Zmiany architektury

Na koniec należy wziąć pod uwagę pewne istotne różnice w architekturze podczas migracji do Blazor. Wiele z tych zmian ma zastosowanie do wszystkich elementów opartych na platformie .NET Core lub ASP.NET Core.

Ponieważ Blazor jest oparty na oprogramowaniu .NET Core, istnieją zagadnienia dotyczące zapewniania pomocy technicznej na platformie .NET Core. Niektóre istotne zmiany obejmują usunięcie następujących funkcji:

- Wiele domen aplikacji
- Komunikacji zdalnej
- Zabezpieczenia dostępu kodu (CAS)
- Przejrzystość zabezpieczeń

Aby uzyskać więcej informacji na temat technik umożliwiających identyfikację niezbędnych zmian w celu obsługi programu .NET Core, zobacz [Porting Code from .NET Framework to .NET Core](/dotnet/core/porting).

ASP.NET Core jest reobrazną wersją ASP.NET i zawiera pewne zmiany, które mogą nie być początkowo oczywiste. Główne zmiany są następujące:

- Brak kontekstu synchronizacji, co oznacza, że nie ma `HttpContext.Current`, `Thread.CurrentPrincipal` ani innych metod dostępu statycznego
- Brak kopiowania w tle
- Brak kolejki żądań

Wiele operacji w ASP.NET Core jest asynchronicznych, co umożliwia łatwiejsze ładowanie zadań związanych z operacjami we/wy. Ważne jest, aby nigdy nie blokować przy użyciu `Task.Wait()` lub `Task.GetResult()`, co może szybko wyczerpać zasoby puli wątków.

## <a name="migration-conclusion"></a>Wniosek o migrację

W tym momencie widzisz wiele przykładów potrzebnych do przeniesienia projektu formularzy sieci Web do Blazor. Pełny przykład można znaleźć w projekcie [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) .

>[!div class="step-by-step"]
>[Ubiegł](security-authentication-authorization.md)
