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
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a>Migracja z ASP.NET formularzy sieci Web do blazora

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Migrowanie bazy kodu z ASP.NET formularzy sieci Web do blazora jest czasochłonnym zadaniem, które wymaga planowania. W tym rozdziale przedstawiono ten proces. Coś, co może ułatwić przejście jest zapewnienie, że aplikacja jest zgodna z architekturą *n-warstwy,* w którym model aplikacji (w tym przypadku formularze sieci Web) jest oddzielony od logiki biznesowej. Ta logiczna separacja warstw wyjaśnia, co należy przenieść do .NET Core i Blazor.

W tym przykładzie używana jest aplikacja eShop dostępna w [usłudze GitHub.](https://github.com/dotnet-architecture/eShopOnBlazor) eShop to usługa katalogowa, która zapewnia możliwości CRUD poprzez wprowadzanie i walidację formularza.

Dlaczego działająca aplikacja powinna zostać przeniesiona do Blazora? Wiele razy, nie ma potrzeby. ASP.NET formularzy sieci Web będą nadal wspierane przez wiele lat. Jednak wiele funkcji, które zapewnia Blazor, jest obsługiwanych tylko w zmigrowanym aplikacji. Takie funkcje obejmują:

- Poprawa wydajności w takich ramach, jak`Span<T>`
- Możliwość uruchamiania jako WebAssembly
- Obsługa wielu platform dla systemów Linux i macOS
- Wdrożenie lokalne aplikacji lub wdrożenie współużytkowane framework bez wpływu na inne aplikacje

Jeśli te lub inne nowe funkcje są wystarczająco atrakcyjne, może być wartość w migracji aplikacji. Migracja może mieć różne kształty; może to być cała aplikacja lub tylko niektóre punkty końcowe, które wymagają zmian. Decyzja o migracji jest ostatecznie oparta na problemach biznesowych, które mają zostać rozwiązane przez dewelopera.

## <a name="server-side-versus-client-side-hosting"></a>Hosting po stronie serwera i po stronie klienta

Jak opisano w rozdziale [modeli hostingu,](hosting-models.md) aplikacja Blazor może być hostowana na dwa różne sposoby: po stronie serwera i po stronie klienta. Model po stronie serwera używa połączeń ASP.NET Core SignalR do zarządzania aktualizacjami DOM podczas uruchamiania dowolnego rzeczywistego kodu na serwerze. Model po stronie klienta działa jako WebAssembly w przeglądarce i nie wymaga żadnych połączeń z serwerem. Istnieje wiele różnic, które mogą mieć wpływ, co jest najlepsze dla konkretnej aplikacji:

- Uruchamianie jako WebAssembly jest nadal w fazie rozwoju i może nie obsługiwać wszystkich funkcji (takich jak wątki) w bieżącym czasie
- Chatty komunikacji między klientem a serwerem może powodować problemy z opóźnieniem w trybie po stronie serwera
- Dostęp do baz danych i usług wewnętrznych lub chronionych wymaga oddzielnej usługi z hostingiem po stronie klienta

W momencie pisania model po stronie serwera bardziej przypomina formularze sieci Web. Większość tego rozdziału koncentruje się na modelu hostingu po stronie serwera, ponieważ jest gotowy do produkcji.

## <a name="create-a-new-project"></a>Tworzenie nowego projektu

Ten początkowy krok migracji polega na utworzeniu nowego projektu. Ten typ projektu jest oparty na projektach stylu SDK .NET Core i upraszcza wiele standardowego, który był używany w poprzednich formatach projektu. Aby uzyskać więcej informacji, zapoznaj się z rozdziałem [struktury projektu](project-structure.md).

Po utworzeniu projektu zainstaluj biblioteki, które były używane w poprzednim projekcie. W starszych projektach formularzy sieci Web być może użyto pliku *packages.config* do listy wymaganych pakietów NuGet. W nowym projekcie w stylu SDK *packages.config* został zastąpiony elementami `<PackageReference>` w pliku projektu. Zaletą tego podejścia jest, że wszystkie zależności są instalowane przechodnie. Możesz wyświetlić tylko zależności najwyższego poziomu, na których Ci zależy.

Wiele zależności, których używasz, jest dostępnych dla platformy .NET Core, w tym entity framework 6 i log4net. Jeśli nie ma dostępnej wersji .NET Core lub .NET Standard, często można użyć wersji .NET Framework. Przebieg może się różnić. Każdy interfejs API używany, który nie jest dostępny w .NET Core powoduje błąd środowiska uruchomieniowego. Visual Studio powiadamia o takich pakietach. W węźle **Odwołania** projektu pojawi się żółta ikona **.**

W projekcie eShop opartym na Blazorie możesz zobaczyć pakiety, które są zainstalowane. Wcześniej plik *packages.config* wymieniał każdy pakiet używany w projekcie, w wyniku czego plik o długości prawie 50 wierszy. Fragment kodu *packages.config* to:

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

Element `<packages>` zawiera wszystkie niezbędne zależności. Trudno jest zidentyfikować, które z tych pakietów są uwzględniane, ponieważ są one potrzebne. Niektóre `<package>` elementy są wymienione po prostu w celu zaspokojenia potrzeb zależności, których potrzebujesz.

Projekt Blazor wyświetla listę zależności wymaganych w elemencie `<ItemGroup>` w pliku projektu:

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

Jednym z pakietów NuGet, który upraszcza życie programistów formularzy sieci Web, jest [pakiet zgodności systemu Windows](../../core/porting/windows-compat-pack.md). Chociaż program .NET Core jest wieloplatformowy, niektóre funkcje są dostępne tylko w systemie Windows. Funkcje specyficzne dla systemu Windows są udostępniane przez zainstalowanie pakietu zgodności. Przykładami takich funkcji są usługi rejestru, usługi WMI i usługi katalogowe. Pakiet dodaje około 20 000 interfejsów API i aktywuje wiele usług, z którymi możesz być już zaznajomiony. Projekt eShop nie wymaga pakietu zgodności; ale jeśli projekty korzystają z funkcji specyficznych dla systemu Windows, pakiet ułatwia wysiłki na rzecz migracji.

## <a name="enable-startup-process"></a>Włącz proces uruchamiania

Proces uruchamiania blazora zmienił się z formularzy sieci Web i następuje podobna konfiguracja dla innych usług ASP.NET Core. Po hostowane po stronie serwera, składniki Blazor są uruchamiane jako część normalnej aplikacji ASP.NET Core. Gdy hostowane w przeglądarce z WebAssembly, składniki Blazor użyć podobnego modelu hostingu. Różnica polega na tym, że składniki są uruchamiane jako oddzielna usługa od dowolnego z procesów wewnętrznej bazy danych. Tak czy inaczej, uruchamianie jest podobne.

Plik *Global.asax.cs* jest domyślną stroną startową dla projektów formularzy sieci Web. W projekcie eShop ten plik konfiguruje kontener Inwersji kontroli (IoC) i obsługuje różne zdarzenia cyklu życia aplikacji lub żądania. Niektóre z tych zdarzeń są obsługiwane za `Application_BeginRequest`pomocą oprogramowania pośredniczącego (np. ). Inne zdarzenia wymagają zastąpienia określonych usług za pomocą iniekcji zależności (DI).

Na przykład plik *Global.asax.cs* dla sklepu eShop zawiera następujący kod:

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

Poprzedni plik staje `Startup` się klasą w blazorze po stronie serwera:

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

Jedną z istotnych zmian, które można zauważyć w formularzach sieci Web jest znaczenie DI. DI jest wiodącą zasadą w projekcie ASP.NET Core. Obsługuje dostosowywanie prawie wszystkich aspektów ASP.NET core framework. Istnieje nawet wbudowany dostawca usług, który może być używany w wielu scenariuszach. Jeśli wymagane jest więcej dostosowywania, może być obsługiwany przez wiele projektów społeczności. Na przykład można przenieść inwestycję biblioteki DI innej firmy.

W oryginalnej aplikacji eShop istnieje pewna konfiguracja do zarządzania sesjami. Ponieważ blazor po stronie serwera używa ASP.NET Core SignalR do komunikacji, stan sesji nie jest obsługiwany, ponieważ połączenia mogą wystąpić niezależnie od kontekstu HTTP. Aplikacja, która używa stanu sesji wymaga rearchitecting przed uruchomieniem jako aplikacji Blazor.

Aby uzyskać więcej informacji na temat uruchamiania aplikacji, zobacz [Uruchamianie aplikacji](app-startup.md).

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>Migrowanie modułów i programów obsługi HTTP do oprogramowania pośredniczącego

Moduły i programy obsługi HTTP są typowe wzorce w formularzach sieci Web do kontrolowania potoku żądania HTTP. Klasy, `IHttpModule` które `IHttpHandler` implementują lub mogą być zarejestrowane i przetwarzają przychodzące żądania. Formularze sieci Web konfiguruje moduły i programy obsługi w pliku *web.config.* Formularze sieci Web jest również w dużym stopniu oparte na obsłudze zdarzeń cyklu życia aplikacji. ASP.NET Core używa oprogramowania pośredniczącego. Oprogramowanie pośredniczące `Configure` jest zarejestrowane w metodzie `Startup` klasy. Zlecenie wykonania oprogramowania pośredniczącego jest określane przez kolejność rejestracji.

W sekcji [Włącz proces uruchamiania](#enable-startup-process) zdarzenie cyklu życia zostało `Application_BeginRequest` podniesione przez formularze sieci Web jako metodę. To zdarzenie nie jest dostępne w ASP.NET Core. Jednym ze sposobów osiągnięcia tego zachowania jest zaimplementowanie oprogramowania pośredniczącego, jak pokazano w przykładzie pliku *Startup.cs.* To oprogramowanie pośredniczące wykonuje tę samą logikę, a następnie przenosi kontrolę do następnego programu obsługi w potoku oprogramowania pośredniczącego.

Aby uzyskać więcej informacji na temat migrowania modułów i programów obsługi, zobacz [Migrowanie programów obsługi i modułów HTTP w celu ASP.NET oprogramowania pośredniczącego Core](/aspnet/core/migration/http-modules).

## <a name="migrate-static-files"></a>Migrowanie plików statycznych

Aby pliki statyczne były eksponowane (na przykład HTML, CSS, obrazy i javascript), pliki muszą być udostępniane przez oprogramowanie pośredniczące. Wywołanie `UseStaticFiles` metody umożliwia wyświetlanie plików statycznych ze ścieżki głównej sieci web. Domyślny katalog główny sieci web jest *wwwroot*, ale można go dostosować. Zgodnie z `Configure` metodą `Startup` klasy eShop:

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

Projekt eShop umożliwia podstawowy statyczny dostęp do plików. Istnieje wiele dostosowań dostępnych dla statycznego dostępu do plików. Aby uzyskać informacje na temat włączania plików domyślnych lub przeglądarki plików, zobacz [Pliki statyczne w ASP.NET Core](/aspnet/core/fundamentals/static-files).

## <a name="migrate-runtime-bundling-and-minification-setup"></a>Konfiguracja tworzenia pakietów i minyfikacji środowiska uruchomieniowego migrowania

Łączenie i wydobywanie to techniki optymalizacji wydajności w celu zmniejszenia liczby i rozmiaru żądań serwera w celu pobrania niektórych typów plików. JavaScript i CSS często przechodzą jakąś formę łączenia lub minigyfikacji przed wysłaniem do klienta. W ASP.NET formularzy sieci Web te optymalizacje są obsługiwane w czasie wykonywania. Konwencje optymalizacji są definiowane *App_Start/BundleConfig.cs* pliku. W ASP.NET Core przyjęto bardziej deklaratywne podejście. Plik zawiera listę plików, które mają zostać zmętnione, wraz z określonymi ustawieniami łączenia.

Aby uzyskać więcej informacji na temat sprzedaży pakietowej i miniefikacji, zobacz [Pakiet i minify statycznych aktywów w ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).

## <a name="migrate-aspx-pages"></a>Migrowanie stron ASPX

Strona w aplikacji Formularze sieci Web to plik z rozszerzeniem *.aspx.* Strona Formularzy sieci Web często może być mapowana na składnik w blazorze. Składnik Blazor jest autorstwa w pliku z rozszerzeniem *.brzytwa.* W przypadku projektu eShop pięć stron jest konwertowanych na stronę Razor.

Na przykład widok szczegółów składa się z trzech plików w projekcie formularzy sieci Web: *Details.aspx*, *Details.aspx.cs*i *Details.aspx.designer.cs*. Podczas konwersji na Blazor, kod i znaczników są łączone w *Details.brzytwa*. Kompilacja brzytwy (odpowiednik tego, co znajduje się w plikach *.designer.cs)* jest przechowywana w katalogu *obj* i domyślnie nie jest chlubna w **Eksploratorze rozwiązań.** Strona Formularze sieci Web składa się z następujących znaczników:

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

Poprzedni znaczników związanych z kodem zawiera następujący kod:

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

Po przekonwertowaniu na blazor strona Formularze sieci Web tłumaczy się na następujący kod:

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

Należy zauważyć, że kod i znaczniki znajdują się w tym samym pliku. Wszystkie wymagane usługi są dostępne `@inject` za pomocą atrybutu. Zgodnie `@page` z dyrektywą ta strona jest `Catalog/Details/{id}` dostępna na trasie. Wartość symbolu zastępczego `{id}` trasy została powiązana z całkowitej liczby. Zgodnie z opisem w sekcji [routingu,](pages-routing-layouts.md) w przeciwieństwie do formularzy sieci Web składnik Razor jawnie określa jego trasy i wszystkie parametry, które są uwzględnione. Wiele formantów formularzy sieci Web może nie mieć dokładnych odpowiedników w blazorze. Często istnieje równoważny fragment kodu HTML, który będzie służył temu sameu celowi. Na przykład `<asp:Label />` formant można zastąpić `<label>` elementem HTML.

### <a name="model-validation-in-blazor"></a>Walidacja modelu w blazorze

Jeśli kod formularzy sieci Web zawiera sprawdzanie poprawności, można przenieść wiele z tego, co masz z niewiele do żadnych zmian. Zaletą uruchamiania w Blazor jest to, że ta sama logika sprawdzania poprawności może być uruchamiana bez konieczności niestandardowego javascriptu. Adnotacje danych umożliwiają łatwe sprawdzanie poprawności modelu.

Na przykład *create.aspx* strona ma formularz wprowadzania danych z sprawdzania poprawności. Przykładowy fragment kodu będzie wyglądał następująco:

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

W blazorze równoważne znaczniki znajdują się w pliku *Create.brzytwa:*

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

Kontekst `EditForm` obejmuje obsługę sprawdzania poprawności i mogą być zawijane wokół danych wejściowych. Adnotacje danych są typowym sposobem dodawania sprawdzania poprawności. Takie wsparcie sprawdzania poprawności `DataAnnotationsValidator` można dodać za pośrednictwem składnika. Aby uzyskać więcej informacji na temat tego mechanizmu, zobacz [ASP.NET podstawowe formularze Blazora i walidację](/aspnet/core/blazor/forms-validation).

## <a name="migrate-built-in-web-forms-controls"></a>Migrowanie wbudowanych formantów formularzy sieci Web

*Ta zawartość jest już wkrótce.*

## <a name="migrate-configuration"></a>Migrowanie konfiguracji

W projekcie formularzy sieci Web dane konfiguracji są najczęściej przechowywane w pliku *web.config.* Dostęp do danych konfiguracyjnych można uzyskać za pomocą pliku `ConfigurationManager`. Usługi były często wymagane do analizowania obiektów. Z .NET Framework 4.7.2, możliwość komponowania został dodany do konfiguracji za pośrednictwem `ConfigurationBuilders`. Konstruktorzy ci zezwolili deweloperom na dodawanie różnych źródeł konfiguracji, które następnie zostały skomponowane w czasie wykonywania w celu pobrania niezbędnych wartości.

ASP.NET Core wprowadził elastyczny system konfiguracji, który umożliwia zdefiniowanie źródła konfiguracji lub źródeł używanych przez aplikację i wdrożenie. Infrastruktura, `ConfigurationBuilder` której możesz używać w aplikacji Formularze sieci Web, została modelowana na podstawie pojęć używanych w systemie konfiguracji ASP.NET Core.

Poniższy fragment kodu pokazuje, jak projekt web forms eShop używa *web.config* do przechowywania wartości konfiguracji:

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

Często wpisy tajne, takie jak parametry połączenia bazy danych, są przechowywane w *pliku web.config*. Wpisy tajne są nieuchronnie utrwalone w niezabezpieczonych lokalizacjach, takich jak kontrola źródła. W ASP.NET Core w udlać się blazor, poprzednia konfiguracja oparta na języku XML jest zastępowana następującym JSON:

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

JSON jest domyślnym formatem konfiguracji; jednak ASP.NET Core obsługuje wiele innych formatów, w tym XML. Istnieje również kilka formatów obsługiwanych przez społeczność.

Konstruktor w `Startup` klasie projektu Blazor akceptuje `IConfiguration` wystąpienie za pomocą techniki DI znanej jako iniekcja konstruktora:

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

Domyślnie zmienne środowiskowe, pliki JSON (*appsettings.json* i *appsettings.{ Środowisko}.json*), a opcje wiersza polecenia są rejestrowane jako prawidłowe źródła konfiguracji w obiekcie konfiguracji. Dostęp do źródeł konfiguracji można `Configuration[key]`uzyskać za pośrednictwem programu . Bardziej zaawansowaną techniką jest powiązanie danych konfiguracji z obiektami przy użyciu wzorca opcji. Aby uzyskać więcej informacji na temat konfiguracji i wzorca opcji, zobacz [Konfiguracja w ASP.NET](/aspnet/core/fundamentals/configuration/) [wzorzec rdzenia](/aspnet/core/fundamentals/configuration/options)i opcje odpowiednio w ASP.NET Core.

## <a name="migrate-data-access"></a>Migrowanie dostępu do danych

Dostęp do danych jest ważnym aspektem każdej aplikacji. Projekt eShop przechowuje informacje o katalogu w bazie danych i pobiera dane z Entity Framework (EF) 6. Ponieważ EF 6 jest obsługiwany w programie .NET Core 3.0, projekt może nadal go używać.

W sklepie internetowym konieczne były następujące zmiany związane z EF:

- W .NET Framework `DbContext` obiekt akceptuje ciąg *formularza name=ConnectionString* i używa ciągu `ConfigurationManager.AppSettings[ConnectionString]` połączenia do połączenia. W .NET Core nie jest to obsługiwane. Należy podać parametry połączenia.
- Dostęp do bazy danych był dostępny w sposób synchroniczne. Chociaż to działa, skalowalność może ucierpieć. Ta logika powinna zostać przeniesiona do wzorca asynchroniowego.

Chociaż nie ma tej samej natywnej obsługi powiązania zestawu danych, Blazor zapewnia elastyczność i moc dzięki obsłudze języka C# na stronie Razor. Na przykład można wykonywać obliczenia i wyświetlać wynik. Aby uzyskać więcej informacji na temat wzorców danych w blazor, zobacz rozdział [Dostęp do danych.](data.md)

## <a name="architectural-changes"></a>Zmiany w architekturze

Wreszcie, istnieją pewne ważne różnice architektoniczne do rozważenia podczas migracji do Blazor. Wiele z tych zmian ma zastosowanie do czegokolwiek opartego na programie .NET Core lub ASP.NET Core.

Ponieważ Blazor jest zbudowany na .NET Core, istnieją kwestie dotyczące zapewnienia obsługi w programie .NET Core. Niektóre z głównych zmian obejmują usunięcie następujących funkcji:

- Wiele appdomains
- Usług zdalnych
- Zabezpieczenia dostępu kodu (CAS)
- Przejrzystość zabezpieczeń

Aby uzyskać więcej informacji na temat technik umożliwiających identyfikację niezbędnych zmian do obsługi uruchomionych w programie .NET Core, zobacz [Port kodu z programu .NET Framework do platformy .NET Core](/dotnet/core/porting).

ASP.NET Core jest przeprojektowaną wersją ASP.NET i ma pewne zmiany, które początkowo mogą nie wydawać się oczywiste. Główne zmiany to:

- Brak kontekstu synchronizacji, co `HttpContext.Current`oznacza, że nie ma `Thread.CurrentPrincipal`, lub innych statycznych akcesorów
- Brak kopiowania w tle
- Brak kolejki żądań

Wiele operacji w ASP.NET Core są asynchroniczne, co umożliwia łatwiejsze odciążanie zadań związanych we/wy. Ważne jest, aby nigdy `Task.Wait()` nie `Task.GetResult()`blokować przy użyciu lub , które mogą szybko wyczerpywać zasoby puli wątków.

## <a name="migration-conclusion"></a>Wniosek dotyczący migracji

W tym momencie widzieliście wiele przykładów tego, czego potrzeba, aby przenieść projekt formularzy sieci Web do Blazora. Pełny przykład można znaleźć w projekcie [eShopOnBlazor.](https://github.com/dotnet-architecture/eShopOnBlazor)

>[!div class="step-by-step"]
>[Wstecz](security-authentication-authorization.md)
