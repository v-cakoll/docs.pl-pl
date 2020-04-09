---
title: Zabezpieczanie mikrousług i aplikacji sieci Web .NET
description: Zabezpieczenia w mikrousługach platformy .NET i aplikacjach sieci Web — zapoznaj się z opcjami uwierzytelniania w aplikacjach sieci web ASP.NET Core.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 56ebd95c8a24c7c8d30d3c6acef6650cb63383c6
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988118"
---
# <a name="make-secure-net-microservices-and-web-applications"></a>Zabezpiecz mikrousługi i aplikacje sieci Web .NET

Istnieje tak wiele aspektów dotyczących zabezpieczeń w mikrousług i aplikacji sieci web, że temat może łatwo podjąć kilka książek, takich jak ten, więc w tej sekcji skupimy się na uwierzytelnianiu, autoryzacji i wpisów tajnych aplikacji.

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>Implementowanie uwierzytelniania w mikrousługach i aplikacjach sieci Web .NET

Często jest to konieczne dla zasobów i interfejsów API opublikowanych przez usługę, aby być ograniczone do niektórych zaufanych użytkowników lub klientów. Pierwszym krokiem do podejmowania tego rodzaju decyzji zaufania na poziomie interfejsu API jest uwierzytelnianie. Uwierzytelnianie to proces niezawodnej weryfikacji tożsamości użytkownika.

W scenariuszach mikrousług uwierzytelnianie jest zazwyczaj obsługiwane centralnie. Jeśli używasz bramy interfejsu API, brama jest dobrym miejscem do uwierzytelniania, jak pokazano na rysunku 9-1. Jeśli używasz tej metody, upewnij się, że poszczególne mikrousług nie można osiągnąć bezpośrednio (bez bramy interfejsu API), chyba że dodatkowe zabezpieczenia jest w miejscu do uwierzytelniania wiadomości, czy pochodzą one z bramy, czy nie.

![Diagram przedstawiający sposób interakcji aplikacji mobilnej klienta z zapleczem.](./media/index/api-gateway-centralized-authentication.png)

**Rysunek 9-1**. Scentralizowane uwierzytelnianie za pomocą bramy interfejsu API

Gdy brama interfejsu API centralizuje uwierzytelnianie, dodaje informacje o użytkowniku podczas przekazywania żądań do mikrousług. Jeśli usługi są dostępne bezpośrednio, usługa uwierzytelniania, takich jak azure active directory lub dedykowane mikrousługi uwierzytelniania działające jako usługa tokenu zabezpieczającego (STS) może służyć do uwierzytelniania użytkowników. Decyzje dotyczące zaufania są współużytkowane przez usługi za pomocą tokenów zabezpieczających lub plików cookie. (Tokeny te mogą być współużytkowane przez aplikacje ASP.NET Core, jeśli to konieczne, implementując [udostępnianie plików cookie.)](/aspnet/core/security/cookie-sharing) Wzór ten jest zilustrowany na rysunku 9-2.

![Diagram przedstawiający uwierzytelnianie za pośrednictwem mikrousług wewnętrznej bazy danych.](./media/index/identity-microservice-authentication.png)

**Rysunek 9-2**. Uwierzytelnianie przez mikrousługę tożsamości; zaufanie jest współużytkowane przy użyciu tokenu autoryzacji

Gdy mikrousługi są dostępne bezpośrednio, zaufanie, który obejmuje uwierzytelnianie i autoryzację, jest obsługiwany przez token zabezpieczający wystawiony przez dedykowane mikrousługi, współużytkowane przez mikrousługi.

### <a name="authenticate-with-aspnet-core-identity"></a>Uwierzytelnij się przy użyciu ASP.NET podstawowej tożsamości

Podstawowym mechanizmem w ASP.NET Core do identyfikowania użytkowników aplikacji jest system członkostwa [ASP.NET Core Identity.](/aspnet/core/security/authentication/identity) ASP.NET Podstawowa tożsamość przechowuje informacje o użytkowniku (w tym informacje logowania, role i oświadczenia) w magazynie danych skonfigurowanym przez dewelopera. Zazwyczaj magazyn danych ASP.NET Core Identity jest magazynem entity `Microsoft.AspNetCore.Identity.EntityFrameworkCore` framework dostępnym w pakiecie. Jednak magazyny niestandardowe lub inne pakiety innych firm mogą być używane do przechowywania informacji o tożsamości w usłudze Azure Table Storage, CosmosDB lub innych lokalizacjach.

> [!TIP]
> ASP.NET Core 2.1 i nowszych zapewnia [ASP.NET podstawowej tożsamości](/aspnet/core/security/authentication/identity) jako [biblioteki klas Razor,](/aspnet/core/razor-pages/ui-class)więc nie zobaczysz wiele niezbędnego kodu w projekcie, jak w przypadku poprzednich wersji. Aby uzyskać szczegółowe informacje na temat dostosowywania kodu tożsamości do własnych potrzeb, zobacz [Tożsamość szkieletu w projektach ASP.NET Core.](/aspnet/core/security/authentication/scaffold-identity)

Poniższy kod pochodzi z szablonu projektu ASP.NET Core Web Application MVC 3.1 z wybranym uwierzytelnianiem konta użytkownika. Pokazuje, jak skonfigurować ASP.NET tożsamości core przy użyciu `Startup.ConfigureServices` entity framework core w metodzie.

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
    //...
}
```

Po skonfigurowaniu ASP.NET Podstawowej tożsamości można ją włączyć, dodając `app.UseAuthentication()` i `endpoints.MapRazorPages()` jak pokazano w `Startup.Configure` następującym kodzie w metodzie usługi:

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    //...
    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
    //...
}
```

> [!IMPORTANT]
> Wiersze w kodzie preceeding **musi być w kolejności pokazano** dla tożsamości do poprawnego działania.

Korzystanie z ASP.NET Podstawowej tożsamości umożliwia kilka scenariuszy:

- Tworzenie nowych informacji o użytkowniku przy użyciu typu UserManager (userManager.CreateAsync).

- Uwierzytelnianie użytkowników przy użyciu typu SignInManager. Można użyć, `signInManager.SignInAsync` aby zalogować `signInManager.PasswordSignInAsync` się bezpośrednio lub potwierdzić, że hasło użytkownika jest poprawne, a następnie zalogować się.

- Identyfikowanie użytkownika na podstawie informacji przechowywanych w pliku cookie (odczytywanych przez oprogramowanie pośredniczące ASP.NET Core Identity), tak aby kolejne żądania z przeglądarki zawierały tożsamość i oświadczenia zalogowanego użytkownika.

ASP.NET Core Identity obsługuje również [uwierzytelnianie dwuskładnikowe.](/aspnet/core/security/authentication/2fa)

W scenariuszach uwierzytelniania, które korzystają z lokalnego magazynu danych użytkownika i które utrzymują tożsamość między żądaniami przy użyciu plików cookie (co jest typowe dla aplikacji sieci web MVC), ASP.NET Core Identity jest zalecanym rozwiązaniem.

### <a name="authenticate-with-external-providers"></a>Uwierzytelnij się u zewnętrznych dostawców

ASP.NET Core obsługuje również przy użyciu [zewnętrznych dostawców uwierzytelniania,](/aspnet/core/security/authentication/social/) aby umożliwić użytkownikom logowanie się za pośrednictwem [przepływów OAuth 2.0.](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) Oznacza to, że użytkownicy mogą logować się przy użyciu istniejących procesów uwierzytelniania od dostawców takich jak Microsoft, Google, Facebook lub Twitter i powiązać te tożsamości z tożsamością ASP.NET Core w aplikacji.

Aby użyć uwierzytelniania zewnętrznego, oprócz łącznie z oprogramowaniem `app.UseAuthentication()` pośredniczącym uwierzytelniania, jak `Startup` wspomniano wcześniej, przy użyciu metody, należy również zarejestrować zewnętrznego dostawcy, jak pokazano w poniższym przykładzie:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddAuthentication()
        .AddMicrosoftAccount(microsoftOptions =>
        {
            microsoftOptions.ClientId = Configuration["Authentication:Microsoft:ClientId"];
            microsoftOptions.ClientSecret = Configuration["Authentication:Microsoft:ClientSecret"];
        })
        .AddGoogle(googleOptions => { ... })
        .AddTwitter(twitterOptions => { ... })
        .AddFacebook(facebookOptions => { ... });
    //...
}
```

Popularne zewnętrzne dostawców uwierzytelniania i skojarzone z nimi pakiety NuGet są wyświetlane w poniższej tabeli:

| **Dostawca**  | **Pakiet**                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Microsoft.AspNetCore.Authentication.MicrosoftAccount** |
| **Google**    | **Microsoft.AspNetCore.Authentication.Google**           |
| **Facebook**  | **Microsoft.AspNetCore.Authentication.Facebook**         |
| **Twitter**   | **Microsoft.AspNetCore.Authentication.Twitter**          |

We wszystkich przypadkach należy wykonać procedurę rejestracji aplikacji, która jest zależna od dostawcy i która zwykle obejmuje:

1. Uzyskiwanie identyfikatora aplikacji klienckiej.
2. Uzyskiwanie klucza tajnego aplikacji klienta.
3. Konfigurowanie adresu URL przekierowania obsługiwanego przez oprogramowanie pośredniczące autoryzacji i zarejestrowanego dostawcę
4. Opcjonalnie konfigurowanie adresu URL wylogowania do prawidłowego obchodzenia się z wyloguj się w scenariuszu logowania jednokrotnego.Optionally, configuring a sign-out URL to properly handle sign out in a Single Sign On (SSO) scenario.

Szczegółowe informacje na temat konfigurowania aplikacji dla zewnętrznego dostawcy można znaleźć [w dokumentacji ASP.NET Core w dokumentacji dostawcy zewnętrznego).](/aspnet/core/security/authentication/social/)

>[!TIP]
>Wszystkie szczegóły są obsługiwane przez oprogramowanie pośredniczące autoryzacji i usługi wcześniej wymienione. Tak więc wystarczy wybrać opcję uwierzytelniania **konta użytkownika indywidualnego** podczas tworzenia projektu aplikacji sieci web ASP.NET Code w programie Visual Studio, jak pokazano na rysunku 9-3, oprócz rejestrowania wcześniej wymienionych dostawców uwierzytelniania.

![Zrzut ekranu przedstawiający okno dialogowe Nowa ASP.NET rdzenia aplikacji sieci Web.](./media/index/select-individual-user-account-authentication-option.png)

**Rysunek 9-3**. Wybieranie opcji Indywidualne konta użytkowników, do korzystania z uwierzytelniania zewnętrznego, podczas tworzenia projektu aplikacji sieci web w programie Visual Studio 2019.

Oprócz zewnętrznych dostawców uwierzytelniania wymienionych wcześniej dostępne są pakiety innych firm, które zapewniają oprogramowanie pośredniczące do korzystania z wielu innych zewnętrznych dostawców uwierzytelniania. Aby uzyskać listę, zobacz [aspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repozytorium w usłudze GitHub.

Można również utworzyć własne oprogramowanie pośredniczące uwierzytelniania zewnętrznego, aby rozwiązać niektóre specjalne potrzeby.

### <a name="authenticate-with-bearer-tokens"></a>Uwierzytelnij się za pomocą tokenów na okaziciela

Uwierzytelnianie za pomocą ASP.NET podstawowej tożsamości (lub tożsamości plus zewnętrznych dostawców uwierzytelniania) działa dobrze w wielu scenariuszach aplikacji sieci web, w których przechowywanie informacji o użytkowniku w pliku cookie jest właściwe. W innych scenariuszach pliki cookie nie są jednak naturalnym sposobem utrwalania i przesyłania danych.

Na przykład w ASP.NET Core Web API, który udostępnia restful punktów końcowych, które mogą być dostępne przez aplikacje jednostronicowe (SPA), przez klientów natywnych, a nawet przez inne interfejsy API sieci Web, zazwyczaj chcesz użyć uwierzytelniania tokenu nośnika zamiast. Tego typu aplikacje nie działają z plikami cookie, ale można łatwo pobrać token nośnika i dołączyć go w nagłówku autoryzacji kolejnych żądań. Aby włączyć uwierzytelnianie tokenów, ASP.NET Core obsługuje kilka opcji korzystania z [OAuth 2.0](https://oauth.net/2/) i [OpenID Connect](https://openid.net/connect/).

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>Uwierzytelnianie za pomocą dostawcy tożsamości OpenID Connect lub OAuth 2.0

Jeśli informacje o użytkowniku są przechowywane w usłudze Azure Active Directory lub innym rozwiązaniu tożsamości obsługującym openid connect lub OAuth 2.0, można użyć pakietu **Microsoft.AspNetCore.Authentication.OpenIdConnect** do uwierzytelniania przy użyciu przepływu pracy OpenID Connect. Na przykład, aby uwierzytelnić się w mikrousługi Identity.Api w eShopOnContainers, aplikacja sieci web ASP.NET Core może `Startup.cs`używać oprogramowania pośredniczącego z tego pakietu, jak pokazano w poniższym uproszczonym przykładzie w:

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");
    var sessionCookieLifetime = configuration.GetValue("SessionCookieLifetimeMinutes", 60);

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
    })
    .AddCookie(setup => setup.ExpireTimeSpan = TimeSpan.FromMinutes(sessionCookieLifetime))
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl.ToString();
        options.SignedOutRedirectUri = callBackUrl.ToString();
        options.ClientId = useLoadTest ? "mvctest" : "mvc";
        options.ClientSecret = "secret";
        options.ResponseType = useLoadTest ? "code id_token token" : "code id_token";
        options.SaveTokens = true;
        options.GetClaimsFromUserInfoEndpoint = true;
        options.RequireHttpsMetadata = false;
        options.Scope.Add("openid");
        options.Scope.Add("profile");
        options.Scope.Add("orders");
        options.Scope.Add("basket");
        options.Scope.Add("marketing");
        options.Scope.Add("locations");
        options.Scope.Add("webshoppingagg");
        options.Scope.Add("orders.signalrhub");
    });
}
```

Należy zauważyć, że podczas korzystania z tego przepływu pracy oprogramowanie pośredniczące ASP.NET Core Identity nie jest potrzebne, ponieważ cały magazyn informacji o użytkowniku i uwierzytelnianie są obsługiwane przez usługę tożsamości.

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>Wystawianie tokenów zabezpieczających z usługi ASP.NET Core

Jeśli wolisz wystawiać tokeny zabezpieczające dla użytkowników tożsamości lokalnej ASP.NET, a nie przy użyciu zewnętrznego dostawcy tożsamości, możesz skorzystać z niektórych dobrych bibliotek innych firm.

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) i [OpenIddict](https://github.com/openiddict/openiddict-core) są dostawcami OpenID Connect, którzy łatwo integrują się z ASP.NET Podstawową tożsamością, aby umożliwić wystawianie tokenów zabezpieczających z usługi ASP.NET Core. Dokumentacja [IdentityServer4](https://identityserver4.readthedocs.io/en/latest/) ma szczegółowe instrukcje dotyczące korzystania z biblioteki. Jednak podstawowe kroki do korzystania identityserver4 do wystawiania tokenów są następujące.

1. Dzwonisz do aplikacji. UseIdentityServer w metodzie Startup.Configure, aby dodać IdentityServer4 do potoku przetwarzania żądań HTTP aplikacji. Dzięki temu biblioteki służyć żądania OpenID Connect i OAuth2 punktów końcowych, takich jak /connect/token.

2. Konfiguracja IdentityServer4 w Startup.ConfigureServices przez wywołanie usług. AddIdentityServer.

3. Serwer tożsamości można skonfigurować, ustawiając następujące dane:

   - Poświadczenia używane do [podpisywania.](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html)

   - [Zasoby tożsamości i interfejsu API,](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) do których użytkownicy mogą żądać dostępu:

      - Zasoby interfejsu API reprezentują chronione dane lub funkcje, do których użytkownik może uzyskać dostęp za pomocą tokenu dostępu. Przykładem zasobu interfejsu API może być internetowy interfejs API (lub zestaw interfejsów API), który wymaga autoryzacji.

      - Zasoby tożsamości reprezentują informacje (oświadczenia), które są podane do klienta w celu zidentyfikowania użytkownika. Oświadczenia mogą zawierać nazwę użytkownika, adres e-mail itd.

   - [Klienci,](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) którzy będą łączyć się w celu żądania tokenów.

   - Mechanizm magazynowania informacji o użytkowniku, takich jak [ASP.NET tożsamość podstawowa](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) lub alternatywa.

Po określeniu klientów i zasobów dla IdentityServer4 <xref:System.Collections.Generic.IEnumerable%601> do użycia, można przekazać kolekcję odpowiedniego typu do metod, które przyjmują w pamięci magazynów klienta lub zasobów. Lub w przypadku bardziej złożonych scenariuszy można podać typy klientów lub dostawców zasobów za pośrednictwem iniekcji zależności.

Przykładowa konfiguracja identityserver4 do używania zasobów w pamięci i klientów dostarczonych przez niestandardowy typ IClientStore może wyglądać następująco:

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //...
    services.AddSingleton<IClientStore, CustomClientStore>();
    services.AddIdentityServer()
        .AddSigningCredential("CN=sts")
        .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
        .AddAspNetIdentity<ApplicationUser>();
    //...
}
```

### <a name="consume-security-tokens"></a>Korzystanie z tokenów zabezpieczających

Uwierzytelnianie względem punktu końcowego OpenID Connect lub wystawianie własnych tokenów zabezpieczających obejmuje niektóre scenariusze. Ale co z usługą, która po prostu musi ograniczyć dostęp do tych użytkowników, którzy mają ważne tokeny zabezpieczające, które zostały dostarczone przez inną usługę?

W tym scenariuszu oprogramowanie pośredniczące uwierzytelniania obsługujące tokeny JWT jest dostępne w pakiecie **Microsoft.AspNetCore.Authentication.JwtBearer.** JWT oznacza "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" i jest typowym formatem tokenu zabezpieczającego (zdefiniowanym przez RFC 7519) do komunikowania oświadczeń zabezpieczeń. Uproszczony przykład sposobu używania oprogramowania pośredniczącego do korzystania z takich tokenów może wyglądać jak ten fragment kodu, zaczerpnięty z mikrousługi Ordering.Api eShopOnContainers.

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;

    }).AddJwtBearer(options =>
    {
        options.Authority = identityUrl;
        options.RequireHttpsMetadata = false;
        options.Audience = "orders";
    });
}
```

Parametry w tym użyciu są następujące:

- `Audience`reprezentuje odbiorcę tokenu przychodzącego lub zasobu, do których zapewnia dostęp token. Jeśli wartość określona w tym parametrze nie jest zgodna z parametrem w tokenie, token zostanie odrzucony.

- `Authority`jest adresem serwera uwierzytelniania wystawiającego token. Oprogramowanie pośredniczące uwierzytelniania na okaziciela JWT używa tego identyfikatora URI, aby uzyskać klucz publiczny, który może służyć do sprawdzania poprawności podpisu tokenu. Oprogramowanie pośredniczące potwierdza `iss` również, że parametr w tokenie jest zgodny z tym identyfikatorem URI.

Inny parametr, `RequireHttpsMetadata`, jest przydatny do celów testowych; ten parametr jest ustawiony na false, dzięki czemu można testować w środowiskach, w których nie masz certyfikatów. W rzeczywistych wdrożeń tokeny nośne JWT powinny być zawsze przekazywane tylko za pośrednictwem protokołu HTTPS.

Z tego oprogramowania pośredniczącego w miejscu tokeny JWT są automatycznie wyodrębniane z nagłówków autoryzacji. Są one następnie deserializowane, weryfikowane `Audience` `Authority` (przy użyciu wartości w i parametrów) i przechowywane jako informacje o użytkowniku, do których mają być później odwoływane przez akcje MVC lub filtry autoryzacji.

Oprogramowanie pośredniczące uwierzytelniania na okaziciela JWT może również obsługiwać bardziej zaawansowane scenariusze, takie jak używanie certyfikatu lokalnego do sprawdzania poprawności tokenu, jeśli urząd nie jest dostępny. W tym scenariuszu można `TokenValidationParameters` określić `JwtBearerOptions` obiekt w obiekcie.

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Udostępnianie plików cookie między aplikacjami** \
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- **Wprowadzenie do tożsamości** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Rick Anderson. Uwierzytelnianie dwuskładnikowe za pomocą wiadomości SMS** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- **Włączanie uwierzytelniania za pomocą Facebooka, Google i innych dostawców zewnętrznych** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- **Michell Anicas. Wprowadzenie do OAuth 2** \
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- **AspNet.Security.OAuth.Providers** (Repozytorium GitHub dla ASP.NET dostawców OAuth) \
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- **IdentityServer4. Oficjalna dokumentacja** \
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
>[Poprzedni](../implement-resilient-applications/monitor-app-health.md)
>[następny](authorization-net-microservices-web-applications.md)
