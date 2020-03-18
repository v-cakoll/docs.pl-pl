---
title: Zabezpieczanie mikrousług i aplikacji sieci Web .NET
description: Zabezpieczenia w mikrousługach .NET i aplikacjach sieci Web — poznaj opcje uwierzytelniania w ASP.NET podstawowych aplikacji sieci web.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 0ac2591f8650e9f8cf29560735a9ec803d29ee4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628335"
---
# <a name="make-secure-net-microservices-and-web-applications"></a>Zabezpieczanie mikrousług i aplikacji sieci Web .NET

Istnieje tak wiele aspektów dotyczących zabezpieczeń w mikrousługach i aplikacjach sieci web, że temat może łatwo podjąć kilka książek, takich jak ten, więc w tej sekcji skupimy się na uwierzytelnianiu, autoryzacji i wtajemnic aplikacji.

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>Implementowanie uwierzytelniania w mikrousługach i aplikacjach sieci Web .NET

Często jest to konieczne dla zasobów i interfejsów API opublikowanych przez usługę, aby być ograniczone do niektórych zaufanych użytkowników lub klientów. Pierwszym krokiem do podejmowania tego rodzaju decyzji zaufania na poziomie interfejsu API jest uwierzytelnianie. Uwierzytelnianie to proces niezawodnego weryfikowania tożsamości użytkownika.

W scenariuszach mikrousług uwierzytelnianie jest zazwyczaj obsługiwane centralnie. Jeśli używasz bramy interfejsu API, brama jest dobrym miejscem do uwierzytelniania, jak pokazano na rysunku 9-1. Jeśli używasz tej metody, upewnij się, że poszczególne mikrousługi nie można uzyskać bezpośrednio (bez bramy interfejsu API), chyba że dodatkowe zabezpieczenia jest w miejscu uwierzytelniania wiadomości, niezależnie od tego, czy pochodzą one z bramy, czy nie.

![Diagram przedstawiający sposób interakcji aplikacji mobilnej klienta z zapleczem.](./media/index/api-gateway-centralized-authentication.png)

**Rysunek 9-1**. Scentralizowane uwierzytelnianie za pomocą bramy interfejsu API

Gdy brama interfejsu API centralizuje uwierzytelnianie, dodaje informacje o użytkowniku podczas przekazywania żądań do mikrousług. Jeśli usługi są dostępne bezpośrednio, usługi uwierzytelniania, takie jak Usługa Azure Active Directory lub mikrousługi dedykowanego uwierzytelniania działającejako usługa tokenu zabezpieczającego (STS) mogą służyć do uwierzytelniania użytkowników. Decyzje dotyczące zaufania są współużytkowane przez usługi za pomocą tokenów zabezpieczającym lub plików cookie. (Te tokeny mogą być współużytkowane między ASP.NET aplikacje podstawowe, jeśli to konieczne, implementując [udostępnianie plików cookie](/aspnet/core/security/cookie-sharing).) Ten wzór przedstawiono na rysunku 9-2.

![Diagram przedstawiający uwierzytelnianie za pośrednictwem mikrousług zaplecza.](./media/index/identity-microservice-authentication.png)

**Rysunek 9-2**. Uwierzytelnianie przez mikrousługę tożsamości; zaufanie jest współużytkowane przy użyciu tokenu autoryzacji

Gdy mikrousługi są uzyskiwane bezpośrednio, zaufanie, który obejmuje uwierzytelniania i autoryzacji, jest obsługiwany przez token zabezpieczający wystawiony przez dedykowaną mikrousługę, współużytkowane przez mikrousługi.

### <a name="authenticate-with-aspnet-core-identity"></a>Uwierzytelnianie przy użyciu ASP.NET podstawowej tożsamości

Podstawowym mechanizmem w ASP.NET Core do identyfikowania użytkowników aplikacji jest system członkostwa [ASP.NET Core Identity.](/aspnet/core/security/authentication/identity) ASP.NET Tożsamość podstawowa przechowuje informacje o użytkowniku (w tym informacje logowania, role i oświadczenia) w magazynie danych skonfigurowanym przez dewelopera. Zazwyczaj magazyn danych ASP.NET Core Identity jest magazynem `Microsoft.AspNetCore.Identity.EntityFrameworkCore` entity framework dostarczonym w pakiecie. Jednak magazyny niestandardowe lub inne pakiety innych firm mogą służyć do przechowywania informacji o tożsamości w usłudze Azure Table Storage, CosmosDB lub innych lokalizacjach.

> [!TIP]
> ASP.NET Core 2.1, a później zapewnia [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) jako biblioteka klas [razor,](/aspnet/core/razor-pages/ui-class)dzięki czemu nie zobaczysz wiele niezbędnego kodu w projekcie, jak to miało miejsce w przypadku poprzednich wersji. Aby uzyskać szczegółowe informacje na temat dostosowywania kodu tożsamości do własnych potrzeb, zobacz [Tożsamość szkieletu w ASP.NET projektów podstawowych](/aspnet/core/security/authentication/scaffold-identity).

Poniższy kod jest pobierany z szablonu projektu ASP.NET Core Web Application MVC 3.1 z wybranym uwierzytelnianiem indywidualnego konta użytkownika. Pokazuje, jak skonfigurować ASP.NET Core Identity przy `Startup.ConfigureServices` użyciu core struktury jednostki w metodzie.

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

Po skonfigurowaniu ASP.NET core identity można `app.UseAuthentication()` włączyć `endpoints.MapRazorPages()` go, dodając i jak pokazano w następującym kodzie w `Startup.Configure` metodzie usługi:

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
> Wiersze w kodzie poprzedzającym **muszą być w kolejności pokazanej,** aby tożsamość działała poprawnie.

Korzystanie z ASP.NET Core Identity umożliwia kilka scenariuszy:

- Utwórz nowe informacje o użytkowniku przy użyciu typu UserManager (userManager.CreateAsync).

- Uwierzytelnij użytkowników przy użyciu typu SignInManager. Możesz użyć `signInManager.SignInAsync` do bezpośredniego `signInManager.PasswordSignInAsync` zalogowania się lub potwierdzenia, że hasło użytkownika jest poprawne, a następnie zalogować się.

- Zidentyfikuj użytkownika na podstawie informacji przechowywanych w pliku cookie (które są odczytywane przez ASP.NET core identity middleware), tak aby kolejne żądania z przeglądarki zawierały tożsamość i oświadczenia zalogowanego użytkownika.

ASP.NET Core Identity obsługuje również [uwierzytelnianie dwuskładnikowe.](/aspnet/core/security/authentication/2fa)

W przypadku scenariuszy uwierzytelniania, które korzystają z lokalnego magazynu danych użytkownika i które utrzymują tożsamość między żądaniami przy użyciu plików cookie (jak to jest typowe dla aplikacji sieci Web MVC), ASP.NET Core Identity jest zalecanym rozwiązaniem.

### <a name="authenticate-with-external-providers"></a>Uwierzytelnianie się u dostawców zewnętrznych

ASP.NET Core obsługuje również korzystanie z [zewnętrznych dostawców uwierzytelniania,](/aspnet/core/security/authentication/social/) aby umożliwić użytkownikom logowanie się za pośrednictwem przepływów [OAuth 2.0.](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) Oznacza to, że użytkownicy mogą logować się przy użyciu istniejących procesów uwierzytelniania od dostawców takich jak Microsoft, Google, Facebook lub Twitter i kojarzyć te tożsamości z ASP.NET tożsamości core w aplikacji.

Aby użyć uwierzytelniania zewnętrznego, oprócz tego, że uwierzytelniające pośredniczenie zostało wymienione wcześniej, należy `app.UseAuthentication()` również zarejestrować dostawcę zewnętrznego w `Startup` sposób pokazany w poniższym przykładzie:

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

Popularni zewnętrzni dostawcy uwierzytelniania i skojarzone z nimi pakiety NuGet są pokazane w poniższej tabeli:

| **Dostawca**  | **Pakiet**                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Konto Microsoft.AspNetCore.Authentication.MicrosoftAccount** |
| **Google**    | **Microsoft.AspNetCore.Authentication.Google**           |
| **Facebook**  | **Microsoft.AspNetCore.Authentication.Facebook**         |
| **Twitter**   | **Microsoft.AspNetCore.Authentication.Twitter**          |

We wszystkich przypadkach należy wykonać procedurę rejestracji aplikacji, która jest zależna od dostawcy i która zwykle obejmuje:

1. Uzyskiwanie identyfikatora aplikacji klienta.
2. Uzyskiwanie klucza tajnego aplikacji klienta.
3. Konfigurowanie adresu URL przekierowania, który jest obsługiwany przez zagęszanie autoryzacji i zarejestrowanego dostawcy
4. Opcjonalnie skonfigurowanie adresu URL wylogowania do prawidłowego wylogowania w scenariuszu logowania jednoosobowego (SSO).

Aby uzyskać szczegółowe informacje na temat konfigurowania aplikacji dla zewnętrznego dostawcy, zobacz [uwierzytelnianie dostawcy zewnętrznego w dokumentacji ASP.NET Core).](/aspnet/core/security/authentication/social/)

>[!TIP]
>Wszystkie szczegóły są obsługiwane przez zagęszanie autoryzacji i usług wcześniej wymienionych. Tak, po prostu trzeba wybrać opcję uwierzytelniania **indywidualnego konta użytkownika** podczas tworzenia projektu aplikacji sieci web ASP.NET Kod w programie Visual Studio, jak pokazano na rysunku 9-3, oprócz rejestrowania dostawców uwierzytelniania wcześniej wymienionych.

![Zrzut ekranu przedstawiający okno dialogowe Nowa ASP.NET podstawowa aplikacja sieci Web.](./media/index/select-individual-user-account-authentication-option.png)

**Rysunek 9-3**. Wybieranie opcji Indywidualne konta użytkowników, do korzystania z uwierzytelniania zewnętrznego podczas tworzenia projektu aplikacji sieci web w programie Visual Studio 2019.

Oprócz dostawców uwierzytelniania zewnętrznego wymienionych wcześniej dostępne są pakiety innych firm, które zapewniają pośredniczenie do korzystania z wielu innych dostawców uwierzytelniania zewnętrznego. Aby uzyskać listę, zobacz repozytorium [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) w usteercie GitHub.

Można również utworzyć własne zewnętrzne pośrednice uwierzytelniania, aby rozwiązać niektóre specjalne potrzeby.

### <a name="authenticate-with-bearer-tokens"></a>Uwierzytelnianie za pomocą tokenów na okaziciela

Uwierzytelnianie przy użyciu ASP.NET tożsamości podstawowej (lub tożsamości oraz zewnętrznych dostawców uwierzytelniania) działa dobrze w wielu scenariuszach aplikacji sieci web, w których przechowywanie informacji o użytkowniku w pliku cookie jest odpowiednie. W innych scenariuszach pliki cookie nie są jednak naturalnym sposobem utrzymywania się i przesyłania danych.

Na przykład w interfejsie API sieci Web ASP.NET, który udostępnia restful punktów końcowych, które mogą być dostępne dla aplikacji jednostronicowych (SPA), przez klientów macierzystych lub nawet przez inne interfejsy API sieci Web, zazwyczaj chcesz użyć uwierzytelniania tokenu elementu nośnego zamiast tego. Tego typu aplikacje nie działają z plikami cookie, ale można łatwo pobrać token elementu nośnego i dołączyć go w nagłówku autoryzacji kolejnych żądań. Aby włączyć uwierzytelnianie tokenów, ASP.NET Core obsługuje kilka opcji korzystania z [oauth 2.0](https://oauth.net/2/) i [OpenID Connect](https://openid.net/connect/).

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>Uwierzytelnianie za pomocą dostawcy tożsamości OpenID Connect lub OAuth 2.0

Jeśli informacje o użytkowniku są przechowywane w usłudze Azure Active Directory lub innym rozwiązaniu tożsamości obsługującym openid connect lub OAuth 2.0, można uwierzytelnić go za pomocą pakietu **Microsoft.AspNetCore.Authentication.OpenIdConnect** do uwierzytelniania przy użyciu przepływu pracy OpenID Connect. Na przykład, aby uwierzytelnić się w mikrousłudze Identity.Api w eShopOnContainers, ASP.NET Core aplikacji sieci web można `Startup.cs`użyć pośredniczenia z tego pakietu, jak pokazano w poniższym uproszczonym przykładzie w:

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

Należy zauważyć, że podczas korzystania z tego przepływu pracy ASP.NET core identity middleware nie jest potrzebne, ponieważ cały magazyn informacji o użytkowniku i uwierzytelniania jest obsługiwany przez usługę Tożsamości.

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>Wystawianie tokenów zabezpieczający z usługi ASP.NET Core

Jeśli wolisz wystawiać tokeny zabezpieczające dla lokalnych użytkowników ASP.NET podstawowej tożsamości, a nie przy użyciu zewnętrznego dostawcy tożsamości, możesz skorzystać z niektórych dobrych bibliotek innych firm.

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) i [OpenIddict](https://github.com/openiddict/openiddict-core) są dostawcami OpenID Connect, którzy łatwo integrują się z ASP.NET Core Identity, aby umożliwić wystawianie tokenów zabezpieczaczy z usługi ASP.NET Core. [Dokumentacja IdentityServer4](https://identityserver4.readthedocs.io/en/latest/) zawiera szczegółowe instrukcje dotyczące korzystania z biblioteki. Jednak podstawowe kroki przy użyciu IdentityServer4 do wystawiania tokenów są następujące.

1. Dzwonisz do aplikacji. UżyjIdentityServer w Startup.Configure metody, aby dodać IdentityServer4 do potoku przetwarzania żądania HTTP aplikacji. Dzięki temu biblioteka obsługuje żądania openid connect i oauth2 punktów końcowych, takich jak /connect/token.

2. IdentityServer4 można skonfigurować w Startup.ConfigureServices, wykonując wywołanie usług. AddIdentityServer.

3. Serwer tożsamości można skonfigurować, ustawiając następujące dane:

   - [Poświadczenia](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) używane do podpisywania.

   - Zasoby [tożsamości i interfejsu API,](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) do których użytkownicy mogą żądać dostępu:

      - Zasoby interfejsu API reprezentują chronione dane lub funkcje, do których użytkownik może uzyskać dostęp za pomocą tokenu dostępu. Przykładem zasobu interfejsu API może być internetowy interfejs API (lub zestaw interfejsów API), który wymaga autoryzacji.

      - Zasoby tożsamości reprezentują informacje (oświadczenia), które są podane do klienta w celu zidentyfikowania użytkownika. Oświadczenia mogą zawierać nazwę użytkownika, adres e-mail itd.

   - [Klienci,](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) którzy będą łączyć się w celu żądania tokenów.

   - Mechanizm przechowywania informacji o użytkowniku, takich jak [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) lub alternatywą.

Po określeniu klientów i zasobów do użycia serwera <xref:System.Collections.Generic.IEnumerable%601> IdentityServer4 można przekazać kolekcję odpowiedniego typu do metod, które przyjmują w pamięci magazyny klientów lub zasobów. Lub dla bardziej złożonych scenariuszy można podać typy klienta lub dostawcy zasobów za pośrednictwem iniekcji zależności.

Przykładowa konfiguracja serwera IdentityServer4 do używania zasobów w pamięci i klientów dostarczonych przez niestandardowy typ iClientStore może wyglądać następująco:

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

### <a name="consume-security-tokens"></a>Korzystanie z tokenów zabezpieczania

Uwierzytelnianie względem punktu końcowego OpenID Connect lub wydawanie własnych tokenów zabezpieczających obejmuje niektóre scenariusze. Ale co z usługą, która po prostu musi ograniczyć dostęp do tych użytkowników, którzy mają prawidłowe tokeny zabezpieczające, które zostały dostarczone przez inną usługę?

W tym scenariuszu zagęszanieuwierzytelniania, które obsługuje tokeny JWT jest dostępna w pakiecie **Microsoft.AspNetCore.Authentication.JwtBearer.** JWT oznacza "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" i jest typowym formatem tokenów zabezpieczających (zdefiniowanym przez RFC 7519) do komunikowania oświadczeń zabezpieczeń. Uproszczony przykład, jak używać pośredniczenia do korzystania z takich tokenów może wyglądać jak ten fragment kodu, zaczerpnięte z mikrousługi Ordering.Api eShopOnContainers.

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

- `Audience`reprezentuje odbiorcę tokenu przychodzącego lub zasób, do który token udziela dostępu. Jeśli wartość określona w tym parametrze nie jest zgodna z parametrem w tokenie, token zostanie odrzucony.

- `Authority`to adres serwera uwierzytelniania wystawiającego tokeny. Zagęszczenie uwierzytelniania elementu nośnego JWT używa tego identyfikatora URI do uzyskania klucza publicznego, który może służyć do sprawdzania poprawności podpisu tokenu. Program pośrednidlaczpotwierdza `iss` również, że parametr w tokenie pasuje do tego identyfikatora URI.

Inny parametr, `RequireHttpsMetadata`, jest przydatny do celów testowych; można ustawić ten parametr false, dzięki czemu można testować w środowiskach, w których nie masz certyfikatów. W rzeczywistych wdrożeniach tokeny elementu nośnego JWT powinny być zawsze przekazywane tylko przez https.

Po umieszczeniu tego narzędzia pośredniczącego tokeny JWT są automatycznie wyodrębniane z nagłówków autoryzacji. Są one następnie deserializowane, weryfikowane (przy użyciu wartości w `Audience` parametrach i) `Authority` i przechowywane jako informacje o użytkowniku, do których można się później odwoływać przez akcje MVC lub filtry autoryzacji.

Pośrednice uwierzytelniania elementu nośnego JWT może również obsługiwać bardziej zaawansowane scenariusze, takie jak używanie certyfikatu lokalnego do sprawdzania poprawności tokenu, jeśli urząd nie jest dostępny. W tym scenariuszu można `TokenValidationParameters` określić `JwtBearerOptions` obiekt w obiekcie.

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

- **AspNet.Security.OAuth.Providers** (repozytowy GitHub dla ASP.NET dostawców OAuth) \
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- **Serwer tożsamości4. Oficjalna dokumentacja** \
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
>[Poprzedni](../implement-resilient-applications/monitor-app-health.md)
>[następny](authorization-net-microservices-web-applications.md)
