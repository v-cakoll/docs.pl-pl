---
title: Zabezpieczanie mikrousług i aplikacji sieci Web platformy .NET
description: Zabezpieczenia w mikrousługach .NET i aplikacjach sieci Web — Uzyskaj informacje na temat opcji uwierzytelniania w ASP.NET Core aplikacji sieci Web.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 0ac2591f8650e9f8cf29560735a9ec803d29ee4f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628335"
---
# <a name="make-secure-net-microservices-and-web-applications"></a>Tworzenie bezpiecznych mikrousług i aplikacji sieci Web platformy .NET

Istnieje wiele aspektów dotyczących zabezpieczeń w mikrousługach i aplikacjach sieci Web, które w tym temacie mogą ułatwić przejęcie kilku książek w taki sposób, aby w tej sekcji skoncentrować się na uwierzytelnianiu, autoryzacji i wpisach tajnych aplikacji.

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>Implementowanie uwierzytelniania w mikrousługach i aplikacjach sieci Web platformy .NET

Często konieczne jest, aby zasoby i interfejsy API opublikowane przez usługę były ograniczone do określonych zaufanych użytkowników lub klientów. Pierwszym krokiem do sortowania decyzji zaufania na poziomie interfejsu API jest uwierzytelnianie. Uwierzytelnianie to proces niezawodnego weryfikowania tożsamości użytkownika.

W scenariuszach mikrousług uwierzytelnianie jest zazwyczaj obsługiwane centralnie. Jeśli używasz bramy interfejsu API, Brama jest dobrym miejscem do uwierzytelniania, jak pokazano na rysunku 9-1. W przypadku korzystania z tej metody upewnij się, że poszczególne mikrousługi nie są dostępne bezpośrednio (bez bramy interfejsu API), o ile nie są stosowane dodatkowe zabezpieczenia umożliwiające uwierzytelnianie komunikatów niezależnie od tego, czy pochodzą one z bramy, czy nie.

![Diagram przedstawiający sposób interakcji aplikacji mobilnej klienta z zapleczem.](./media/index/api-gateway-centralized-authentication.png)

**Rysunek 9-1**. Scentralizowane uwierzytelnianie przy użyciu bramy interfejsu API

Gdy brama interfejsu API scentralizowana uwierzytelnianie, dodaje informacje o użytkowniku podczas przekazywania żądań do mikrousług. W przypadku uzyskiwania dostępu do usług można korzystać z usługi uwierzytelniania, takiej jak Azure Active Directory lub dedykowanej mikrousługi uwierzytelniania działającej jako usługa tokenu zabezpieczającego (STS) do uwierzytelniania użytkowników. Decyzje dotyczące zaufania są współużytkowane przez usługi z tokenami zabezpieczeń lub plikami cookie. (Te tokeny mogą być współużytkowane przez aplikacje ASP.NET Core, w razie konieczności, przez zaimplementowanie [udostępniania plików cookie](/aspnet/core/security/cookie-sharing).) Ten wzorzec przedstawiono na rysunku 9-2.

![Diagram przedstawiający uwierzytelnianie za poorednictwem mikrousług zaplecza.](./media/index/identity-microservice-authentication.png)

**Rysunek 9-2**. Uwierzytelnianie według mikrousług tożsamości; zaufanie jest udostępniane przy użyciu tokenu autoryzacji

W przypadku bezpośredniego dostępu do mikrousług relacja zaufania, która obejmuje uwierzytelnianie i autoryzację, jest obsługiwana przez token zabezpieczający wystawiony przez dedykowaną mikrousługę, współdzieloną przez mikrousługi.

### <a name="authenticate-with-aspnet-core-identity"></a>Uwierzytelnianie za pomocą tożsamości ASP.NET Core

Podstawowym mechanizmem w ASP.NET Core do identyfikowania użytkowników aplikacji jest system członkostwa [tożsamości ASP.NET Core](/aspnet/core/security/authentication/identity) . ASP.NET Core Identity przechowuje informacje o użytkowniku (w tym informacje dotyczące logowania, role i oświadczenia) w magazynie danych skonfigurowanym przez dewelopera. Zwykle magazyn danych tożsamości ASP.NET Core jest magazynem Entity Framework udostępnionym w pakiecie `Microsoft.AspNetCore.Identity.EntityFrameworkCore`. Jednak magazyny niestandardowe lub inne pakiety innych firm mogą służyć do przechowywania informacji o tożsamościach w usłudze Azure Table Storage, CosmosDB lub innych lokalizacjach.

> [!TIP]
> ASP.NET Core 2,1 i nowsze zapewniają [ASP.NET Core tożsamość](/aspnet/core/security/authentication/identity) jako [bibliotekę klas Razor](/aspnet/core/razor-pages/ui-class), więc nie zobaczysz wielu niezbędnych kodów w projekcie, tak jak w przypadku poprzednich wersji. Aby uzyskać szczegółowe informacje na temat sposobu dostosowywania kodu tożsamości do własnych potrzeb, zobacz temat [tożsamość szkieletowa w projektach ASP.NET Core](/aspnet/core/security/authentication/scaffold-identity).

Poniższy kod jest pobierany z szablonu projektu ASP.NET Core Web Application MVC 3,1 z wybranym indywidualnym uwierzytelnianiem konta użytkownika. Przedstawiono w nim sposób konfigurowania tożsamości ASP.NET Core przy użyciu Entity Framework Core w metodzie `Startup.ConfigureServices`.

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

Po skonfigurowaniu tożsamości ASP.NET Core można ją włączyć poprzez dodanie `app.UseAuthentication()` i `endpoints.MapRazorPages()` jak pokazano w poniższym kodzie w metodzie `Startup.Configure` usługi:

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
> Wiersze poprzedzające kod **muszą być w kolejności POkazanej** do poprawnego działania tożsamości.

Korzystanie z ASP.NET Core Identity umożliwia wykonywanie kilku scenariuszy:

- Utwórz nowe informacje o użytkowniku przy użyciu typu Usermanager (usermanager. setasync).

- Uwierzytelnianie użytkowników przy użyciu typu SignInManager. Możesz użyć `signInManager.SignInAsync`, aby zalogować się bezpośrednio, lub `signInManager.PasswordSignInAsync` potwierdzić, że hasło użytkownika jest poprawne, a następnie podpisz.

- Zidentyfikuj użytkownika na podstawie informacji przechowywanych w pliku cookie (który jest odczytywany przez oprogramowanie ASP.NET Core Identity), aby kolejne żądania z przeglądarki obejmowały tożsamość i oświadczenia zalogowanego użytkownika.

Tożsamość ASP.NET Core obsługuje również [uwierzytelnianie dwuskładnikowe](/aspnet/core/security/authentication/2fa).

W przypadku scenariuszy uwierzytelniania, które wykorzystują magazyn danych użytkownika lokalnego i utrzymują tożsamość między żądaniami przy użyciu plików cookie (jak zwykle w przypadku aplikacji sieci Web MVC), ASP.NET Core tożsamość jest zalecanym rozwiązaniem.

### <a name="authenticate-with-external-providers"></a>Uwierzytelnianie z dostawcami zewnętrznymi

ASP.NET Core obsługuje również korzystanie z [zewnętrznych dostawców uwierzytelniania](/aspnet/core/security/authentication/social/) , aby umożliwić użytkownikom logowanie za pomocą przepływów [OAuth 2,0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) . Oznacza to, że użytkownicy mogą logować się przy użyciu istniejących procesów uwierzytelniania od dostawców, takich jak Microsoft, Google, Facebook lub Twitter, i kojarzyć te tożsamości z tożsamością ASP.NET Core w aplikacji.

Aby można było korzystać z uwierzytelniania zewnętrznego, między innymi oprogramowania pośredniczącego uwierzytelniania wspomnianego przed, przy użyciu metody `app.UseAuthentication()`, należy również zarejestrować zewnętrznego dostawcę w `Startup`, jak pokazano w następującym przykładzie:

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

W poniższej tabeli przedstawiono popularne zewnętrzne dostawcy uwierzytelniania i powiązane z nimi pakiety NuGet.

| **Dostawca**  | **Pakiet**                                          |
| ------------- | ---------------------------------------------------- |
| **Programu** | **Microsoft. AspNetCore. Authentication. MicrosoftAccount** |
| **Google**    | **Microsoft. AspNetCore. Authentication. Google**           |
| **Facebook**  | **Microsoft. AspNetCore. Authentication. Facebook**         |
| **Twitter**   | **Microsoft. AspNetCore. Authentication. Twitter**          |

We wszystkich przypadkach należy wykonać procedurę rejestracji aplikacji, która jest zależna od dostawcy i która zazwyczaj obejmuje:

1. Pobieranie identyfikatora aplikacji klienckiej.
2. Pobieranie klucza tajnego aplikacji klienckiej.
3. Konfigurowanie adresu URL przekierowania, który jest obsługiwany przez oprogramowanie pośredniczące autoryzacji i zarejestrowany dostawca
4. Opcjonalnie można skonfigurować adres URL wylogowania, aby prawidłowo obsługiwać wylogowywanie w scenariuszu logowania jednokrotnego (SSO).

Aby uzyskać szczegółowe informacje na temat konfigurowania aplikacji dla dostawcy zewnętrznego, zobacz [uwierzytelnianie dostawcy zewnętrznego w dokumentacji ASP.NET Core](/aspnet/core/security/authentication/social/).

>[!TIP]
>Wszystkie szczegóły są obsługiwane przez oprogramowanie pośredniczące i wspomniane wcześniej usługi autoryzacji. W związku z tym po utworzeniu projektu aplikacji sieci Web ASP.NET Code w programie Visual Studio wystarczy wybrać opcję uwierzytelniania **poszczególnych kont użytkowników** , jak pokazano na rysunku 9-3, oprócz rejestrowania wyżej wymienionych dostawców uwierzytelniania.

![Zrzut ekranu przedstawiający okno dialogowe Nowa aplikacja sieci Web ASP.NET Core.](./media/index/select-individual-user-account-authentication-option.png)

**Rysunek 9-3**. Podczas tworzenia projektu aplikacji sieci Web w programie Visual Studio 2019 wybierz opcję konta poszczególnych użytkowników, aby korzystać z uwierzytelniania zewnętrznego.

Oprócz zewnętrznych dostawców uwierzytelniania wymienionych wcześniej pakiety innych firm są dostępne, które zapewniają oprogramowanie pośredniczące do korzystania z wielu innych zewnętrznych dostawców uwierzytelniania. Aby uzyskać listę, zobacz repozytorium [ASPNET. Security. OAuth. Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) w witrynie GitHub.

Możesz również utworzyć własne oprogramowanie pośredniczące uwierzytelniania zewnętrznego, aby rozwiązać pewne szczególne potrzeby.

### <a name="authenticate-with-bearer-tokens"></a>Uwierzytelnianie przy użyciu tokenów okaziciela

Uwierzytelnianie za pomocą tożsamości ASP.NET Core (lub tożsamości i zewnętrznych dostawców uwierzytelniania) działa dobrze w przypadku wielu scenariuszy aplikacji sieci Web, w których przechowywane są informacje o użytkowniku w pliku cookie. W innych scenariuszach pliki cookie nie są naturalnymi sposobami utrwalania i przesyłania danych.

Na przykład w interfejsie API sieci Web ASP.NET Core, który uwidacznia punkty końcowe RESTful, do których mogą uzyskiwać dostęp aplikacje jednostronicowe (aplikacji jednostronicowych), przez natywnych klientów, a nawet przez inne interfejsy API sieci Web, zwykle zamiast tego należy użyć uwierzytelniania tokenu nośnego. Te typy aplikacji nie działają z plikami cookie, ale mogą łatwo pobrać token okaziciela i uwzględnić go w nagłówku autoryzacji kolejnych żądań. Aby włączyć uwierzytelnianie tokenu, ASP.NET Core obsługuje kilka opcji używania [uwierzytelniania OAuth 2,0](https://oauth.net/2/) i [OpenID Connect Connect](https://openid.net/connect/).

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>Uwierzytelnianie za pomocą dostawcy tożsamości OpenID Connect Connect lub OAuth 2,0

Jeśli informacje o użytkowniku są przechowywane w Azure Active Directory lub inne rozwiązanie do obsługi tożsamości, które obsługuje OpenID Connect Connect lub OAuth 2,0, można użyć pakietu **Microsoft. AspNetCore. Authentication. OpenIdConnect** do uwierzytelniania za pomocą przepływu pracy OpenID Connect Connect. Na przykład w celu uwierzytelnienia w mikrousłudze Identity. API w eShopOnContainers, aplikacja sieci Web ASP.NET Core może korzystać z oprogramowania pośredniczącego z tego pakietu, jak pokazano w poniższym uproszczonym przykładzie w `Startup.cs`:

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

Należy pamiętać, że w przypadku korzystania z tego przepływu pracy oprogramowanie pośredniczące ASP.NET Core Identity nie jest konieczne, ponieważ usługa tożsamości zawiera wszystkie magazyny informacji o użytkownikach i ich uwierzytelnianie.

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>Wystawianie tokenów zabezpieczających z usługi ASP.NET Core

Jeśli wolisz wydawać tokeny zabezpieczające dla lokalnych użytkowników tożsamości ASP.NET Core zamiast korzystać z zewnętrznego dostawcy tożsamości, możesz korzystać z niektórych dobrych bibliotek innych firm.

[Usługi identityserver4](https://github.com/IdentityServer/IdentityServer4) i [OpenIddict](https://github.com/openiddict/openiddict-core) są dostawcami OpenID Connect, którzy integrują się z usługą ASP.NET Core Identity, aby wystawiać tokeny zabezpieczające z usługi ASP.NET Core. [Dokumentacja usługi identityserver4](https://identityserver4.readthedocs.io/en/latest/) zawiera szczegółowe instrukcje dotyczące korzystania z biblioteki. Jednak podstawowe kroki do korzystania z usługi identityserver4 w celu wystawiania tokenów są następujące.

1. Nazywasz aplikację. UseIdentityServer w metodzie Startup. configure, aby dodać usługi identityserver4 do potoku przetwarzania żądań HTTP aplikacji. Pozwala to, aby Biblioteka obsługiwała żądania OpenID Connect Connect i OAuth2 Endpoints, takich jak/Connect/token.

2. Usługi identityserver4 można skonfigurować w programie Startup. ConfigureServices, wykonując wywołanie do usług. AddIdentityServer.

3. Skonfiguruj serwer tożsamości, ustawiając następujące dane:

   - [Poświadczenia](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) do użycia podczas podpisywania.

   - [Zasoby tożsamości i interfejsu API](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) , do których użytkownicy mogą żądać dostępu:

      - Zasoby interfejsu API reprezentują chronione dane lub funkcje, do których użytkownik może uzyskać dostęp za pomocą tokenu dostępu. Przykładem zasobu interfejsu API będzie interfejs API sieci Web (lub zestaw interfejsów API) wymagający autoryzacji.

      - Zasoby tożsamości reprezentują informacje (oświadczenia), które są nadawane klientowi do identyfikowania użytkownika. Oświadczenia mogą zawierać nazwę użytkownika, adres e-mail i tak dalej.

   - [Klienci](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) , którzy będą łączyć się w celu żądania tokenów.

   - Mechanizm magazynowania dla informacji o użytkowniku, na przykład [tożsamość ASP.NET Core](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) lub alternatywa.

Po określeniu klientów i zasobów do użycia przez usługi identityserver4 można przekazać kolekcję <xref:System.Collections.Generic.IEnumerable%601> odpowiedniego typu do metod, które pobierają klientów lub magazyny zasobów w pamięci. Lub w przypadku bardziej złożonych scenariuszy można dostarczyć klienta lub typy dostawcy zasobów za pomocą iniekcji zależności.

Przykładowa konfiguracja usługi identityserver4 do używania zasobów w pamięci i klientów dostarczanych przez niestandardowy typ IClientStore może wyglądać podobnie do poniższego przykładu:

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

Uwierzytelnianie przy użyciu punktu końcowego OpenID Connect Connect lub wystawianie własnych tokenów zabezpieczających obejmuje niektóre scenariusze. Ale co to jest usługa, która po prostu musi ograniczyć dostęp do tych użytkowników, którzy mają prawidłowe tokeny zabezpieczające udostępniane przez inną usługę?

W tym scenariuszu oprogramowanie pośredniczące uwierzytelniania obsługujące tokeny JWT jest dostępne w pakiecie **Microsoft. AspNetCore. Authentication. JwtBearer** . JWT oznacza "[token sieci Web JSON](https://tools.ietf.org/html/rfc7519)" i jest typowym formatem tokenu zabezpieczającego (zdefiniowanym w dokumencie RFC 7519) do komunikacji oświadczeń zabezpieczeń. Uproszczony przykład użycia oprogramowania pośredniczącego do korzystania z takich tokenów może wyglądać podobnie do tego fragmentu kodu, który został pobrany z mikrousługi porządkowania. API eShopOnContainers.

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

Parametry w tym wykorzystaniu są następujące:

- `Audience` reprezentuje odbiorcę przychodzącego tokenu lub zasobu, do którego token udziela dostępu. Jeśli wartość określona w tym parametrze nie pasuje do parametru w tokenie, token zostanie odrzucony.

- `Authority` jest adresem serwera uwierzytelniania wystawiającego tokeny. Oprogramowanie pośredniczące uwierzytelniania okaziciela JWT używa tego identyfikatora URI do uzyskania klucza publicznego, którego można użyć do zweryfikowania podpisu tokenu. Oprogramowanie pośredniczące potwierdza również, że parametr `iss` w tokenie jest zgodny z tym identyfikatorem URI.

Inny parametr, `RequireHttpsMetadata`, jest przydatny do celów testowych. Ten parametr należy ustawić na wartość false, aby można było testować w środowiskach, w których nie masz certyfikatów. W rzeczywistych wdrożeniach tokeny okaziciela JWT powinny zawsze być przesyłane tylko za pośrednictwem protokołu HTTPS.

W przypadku tego oprogramowania pośredniczącego tokeny JWT są automatycznie wyodrębniane z nagłówków autoryzacji. Są one następnie deserializowane, zweryfikowane (przy użyciu wartości z parametrów `Audience` i `Authority`) i przechowywane jako informacje o użytkowniku, do których odwołuje się później za pomocą akcji MVC lub filtrów autoryzacji.

Oprogramowanie pośredniczące uwierzytelniania okaziciela JWT może również obsługiwać bardziej zaawansowane scenariusze, takie jak użycie certyfikatu lokalnego do walidacji tokenu, jeśli Urząd nie jest dostępny. W tym scenariuszu można określić obiekt `TokenValidationParameters` w obiekcie `JwtBearerOptions`.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Udostępnianie plików cookie między aplikacjami** \
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- **Wprowadzenie do tożsamości** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Rick Anderson. Uwierzytelnianie dwuskładnikowe za pomocą SMS** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- **Włączanie uwierzytelniania przy użyciu usługi Facebook, Google i innych dostawców zewnętrznych** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- **Michell Anicas. Wprowadzenie do \ uwierzytelniania OAuth 2**
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- **ASPNET. Security. OAuth. Providers** (repozytorium GitHub dla dostawców ASP.NET OAuth) \
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- **Usługi identityserver4. Oficjalna dokumentacja** \
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
>[Poprzednie](../implement-resilient-applications/monitor-app-health.md)
>[dalej](authorization-net-microservices-web-applications.md)
