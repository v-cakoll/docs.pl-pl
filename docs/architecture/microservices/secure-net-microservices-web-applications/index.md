---
title: Zabezpieczanie mikrousług i aplikacji sieci Web platformy .NET
description: Zabezpieczenia w mikrousługach .NET i aplikacjach sieci Web — Uzyskaj informacje na temat opcji uwierzytelniania w ASP.NET Core aplikacji sieci Web.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: b25f02140915ce87c5c478d8a8a5fe28ba7693b3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736964"
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

Poniższy kod jest pobierany z szablonu projektu aplikacji sieci Web ASP.NET Core z wybranym indywidualnym uwierzytelnianiem konta użytkownika. Przedstawiono w nim sposób konfigurowania tożsamości ASP.NET Core przy użyciu EntityFramework. Core w metodzie Startup. ConfigureServices.

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

Po skonfigurowaniu tożsamości ASP.NET Core można ją włączyć, wywołując aplikację. UseIdentity w metodzie `Startup.Configure` usługi.

Korzystanie z ASP.NET Core Identity umożliwia wykonywanie kilku scenariuszy:

- Utwórz nowe informacje o użytkowniku przy użyciu typu Usermanager (usermanager. setasync).

- Uwierzytelnianie użytkowników przy użyciu typu SignInManager. Możesz użyć `signInManager.SignInAsync`, aby zalogować się bezpośrednio, lub `signInManager.PasswordSignInAsync` potwierdzić, że hasło użytkownika jest poprawne, a następnie podpisz.

- Zidentyfikuj użytkownika na podstawie informacji przechowywanych w pliku cookie (który jest odczytywany przez oprogramowanie ASP.NET Core Identity), aby kolejne żądania z przeglądarki obejmowały tożsamość i oświadczenia zalogowanego użytkownika.

Tożsamość ASP.NET Core obsługuje również [uwierzytelnianie dwuskładnikowe](/aspnet/core/security/authentication/2fa).

W przypadku scenariuszy uwierzytelniania, które wykorzystują magazyn danych użytkownika lokalnego i utrzymują tożsamość między żądaniami przy użyciu plików cookie (jak zwykle w przypadku aplikacji sieci Web MVC), ASP.NET Core tożsamość jest zalecanym rozwiązaniem.

### <a name="authenticate-with-external-providers"></a>Uwierzytelnianie z dostawcami zewnętrznymi

ASP.NET Core obsługuje również korzystanie z [zewnętrznych dostawców uwierzytelniania](/aspnet/core/security/authentication/social/) , aby umożliwić użytkownikom logowanie za pomocą przepływów [OAuth 2,0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) . Oznacza to, że użytkownicy mogą logować się przy użyciu istniejących procesów uwierzytelniania od dostawców, takich jak Microsoft, Google, Facebook lub Twitter, i kojarzyć te tożsamości z tożsamością ASP.NET Core w aplikacji.

Aby można było korzystać z uwierzytelniania zewnętrznego, należy uwzględnić odpowiednie oprogramowanie pośredniczące uwierzytelniania w potoku przetwarzania żądań HTTP aplikacji. To oprogramowanie pośredniczące jest odpowiedzialne za obsługę żądań zwrócenia tras URI z dostawcy uwierzytelniania, Przechwytywanie informacji o tożsamości i udostępnianie ich za pośrednictwem metody SignInManager. GetExternalLoginInfo.

W poniższej tabeli przedstawiono popularne zewnętrzne dostawcy uwierzytelniania i powiązane z nimi pakiety NuGet.

| **Dostawca**  | **Pakiet**                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Microsoft.AspNetCore.Authentication.MicrosoftAccount** |
| **Google**    | **Microsoft.AspNetCore.Authentication.Google**           |
| **Facebook**  | **Microsoft.AspNetCore.Authentication.Facebook**         |
| **Twitter**   | **Microsoft.AspNetCore.Authentication.Twitter**          |

We wszystkich przypadkach oprogramowanie pośredniczące jest zarejestrowane z wywołaniem metody rejestracji podobnej do `app.Use{ExternalProvider}Authentication` w `Startup.Configure`. Te metody rejestracji przyjmują obiekt Options, który zawiera identyfikator aplikacji i informacje o kluczu tajnym (na przykład hasło), zgodnie z wymaganiami dostawcy. Zewnętrzni dostawcy uwierzytelniania wymagają rejestracji aplikacji (zgodnie z opisem w [dokumentacji ASP.NET Core](/aspnet/core/security/authentication/social/)), dzięki czemu mogą poinformować użytkownika, jakie aplikacje żąda dostępu do ich tożsamości.

Po zarejestrowaniu oprogramowania pośredniczącego w `Startup.Configure`możesz monitować użytkowników o zalogowanie się z dowolnego działania kontrolera. W tym celu należy utworzyć obiekt `AuthenticationProperties`, który zawiera nazwę dostawcy uwierzytelniania i adres URL przekierowania. Następnie zwracasz odpowiedź wyzwania, która przekazuje obiekt `AuthenticationProperties`. Poniższy kod przedstawia przykład tego elementu.

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

Parametr redirectUrl zawiera adres URL, do którego dostawca zewnętrzny powinien przekierować po uwierzytelnieniu użytkownika. Adres URL powinien reprezentować akcję, która będzie podpisywać użytkownika w oparciu o informacje o tożsamości zewnętrznej, jak w poniższym przykładzie uproszczonym:

```csharp
// Sign in the user with this external login provider if the user
// already has a login.
var result = await _signInManager.ExternalLoginSignInAsync(info.LoginProvider, info.ProviderKey, isPersistent: false);

if (result.Succeeded)
{
    return RedirectToLocal(returnUrl);
}
else
{
    ApplicationUser newUser = new ApplicationUser
    {
        // The user object can be constructed with claims from the
        // external authentication provider, combined with information
        // supplied by the user after they have authenticated with
        // the external provider.
        UserName = info.Principal.FindFirstValue(ClaimTypes.Name),
        Email = info.Principal.FindFirstValue(ClaimTypes.Email)
    };
    var identityResult = await _userManager.CreateAsync(newUser);
    if (identityResult.Succeeded)
    {
        identityResult = await _userManager.AddLoginAsync(newUser, info);
        if (identityResult.Succeeded)
        {
            await _signInManager.SignInAsync(newUser, isPersistent: false);
        }
        return RedirectToLocal(returnUrl);
    }
}
```

W przypadku wybrania opcji uwierzytelniania **indywidualnego konta użytkownika** podczas tworzenia projektu aplikacji sieci Web ASP.NET Code w programie Visual Studio cały kod niezbędny do zalogowania się za pomocą zewnętrznego dostawcy jest już w projekcie, jak pokazano na rysunku 9-3.

![Zrzut ekranu przedstawiający okno dialogowe Nowa aplikacja sieci Web ASP.NET Core.](./media/index/select-external-authentication-option.png)

**Rysunek 9-3**. Wybieranie opcji używania uwierzytelniania zewnętrznego podczas tworzenia projektu aplikacji sieci Web

Oprócz zewnętrznych dostawców uwierzytelniania wymienionych wcześniej pakiety innych firm są dostępne, które zapewniają oprogramowanie pośredniczące do korzystania z wielu innych zewnętrznych dostawców uwierzytelniania. Aby uzyskać listę, zobacz " [ASPNET. Security. OAuth. Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) " w witrynie GitHub.

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
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseMvc();
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = OpenIdConnectDefaults.AuthenticationScheme;
    })
    .AddCookie()
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl;
        options.SignedOutRedirectUri = callBackUrl;
        options.ClientSecret = "secret";
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
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
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
    app.UseMvc();
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

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
>[Poprzedni](../implement-resilient-applications/monitor-app-health.md)
>[Następny](authorization-net-microservices-web-applications.md)
