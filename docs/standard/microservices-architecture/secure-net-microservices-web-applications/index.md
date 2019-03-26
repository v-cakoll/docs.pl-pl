---
title: Zabezpieczanie Mikrousług .NET i aplikacji sieci Web
description: Zabezpieczenia w Mikrousługach .NET i aplikacji sieci Web - Get w celu wiedzieć opcji uwierzytelniania w aplikacji sieci web platformy ASP.NET Core.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
---
# <a name="make-secure-net-microservices-and-web-applications"></a>Bezpieczne Mikrousług .NET i aplikacji sieci Web

Istnieje wiele aspektów dotyczących zabezpieczeń w mikrousług i aplikacji sieci web czy temat proste może potrwać kilka książki podobny do poniższego, więc w tej sekcji skupimy się na uwierzytelniania, autoryzacji i wpisów tajnych aplikacji.

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>Implementowanie uwierzytelniania w aplikacjach sieci web i mikrousługi platformy .NET

Często jest to niezbędne do zasobów i interfejsów API opublikowana przez usługę ograniczone do niektórych Zaufani użytkownicy lub klienci. Pierwszym krokiem do wprowadzania tego rodzaju decyzji dotyczących zaufania poziom interfejsu API to uwierzytelnianie. Uwierzytelnianie to proces niezawodnie zweryfikowanie tożsamości użytkownika.

W scenariuszach mikrousług uwierzytelniania jest zazwyczaj obsługiwana centralnie. Jeśli używasz bramy interfejsu API, bramy jest dobrym miejscem do uwierzytelniania, jak pokazano w rysunek 9-1. Jeśli używasz tego podejścia, upewnij się, że poszczególne mikrousługi nie można połączyć bezpośrednio (bez bramy interfejsu API), chyba że zapewnienia dodatkowych zabezpieczeń w celu uwierzytelniania wiadomości tego, czy pochodzą one od bramą lub nie.

![Gdy brama interfejsu API umożliwia scentralizowanie uwierzytelniania, dodaje informacje o użytkowniku podczas przesyłania żądania do mikrousług.](./media/image1.png)

**Rysunek 9-1**. Scentralizowane uwierzytelnianie przy użyciu bramy interfejsu API

Jeśli usługi są dostępne bezpośrednio, usługi uwierzytelniania, takich jak Azure Active Directory lub mikrousług dedykowanych uwierzytelniania, pełniący funkcję zabezpieczeń, usługa tokenów (STS) może być używane do uwierzytelniania użytkowników. Usługi za pomocą tokenów zabezpieczających lub pliki cookie są współużytkowane decyzji dotyczących zaufania. (Tokeny te mogą być współużytkowane między aplikacje platformy ASP.NET Core, jeśli to konieczne, implementując [udostępnianie plików cookie](/aspnet/core/security/cookie-sharing).) Ten wzorzec zilustrowano w rysunek 9-2.

![Gdy mikrousług są dostępne bezpośrednio, zaufanie, która obejmuje uwierzytelnianie i autoryzacja, jest obsługiwane przez tokenu zabezpieczającego wydane przez dedykowany mikrousług, współużytkowana mikrousług.](./media/image2.png)

**Rysunek 9-2**. Uwierzytelnienia za pomocą tożsamości mikrousług; zaufanie jest udostępniany przy użyciu tokenu autoryzacji

### <a name="authenticate-with-aspnet-core-identity"></a>Uwierzytelnianie za pomocą tożsamości platformy ASP.NET Core

Podstawowy mechanizm w programie ASP.NET Core do identyfikowania użytkowników w aplikacji jest [tożsamości platformy ASP.NET Core](/aspnet/core/security/authentication/identity) systemu członkostwa. Tożsamości platformy ASP.NET Core przechowuje informacje o użytkowniku (w tym informacje logowania, ról i oświadczenia) w magazynie danych skonfigurowane przez dewelopera. Zazwyczaj magazyn danych tożsamości platformy ASP.NET Core to Entity Framework sklepu udostępniane w `Microsoft.AspNetCore.Identity.EntityFrameworkCore` pakietu. Jednak inne pakiety innych firm lub niestandardowych magazynów może służyć do przechowywania informacji o tożsamości w usłudze Azure Table Storage, bazy danych cosmos DB lub w innych lokalizacjach.

Następujący kod pochodzi z szablonu projektu aplikacji sieci Web programu ASP.NET Core przy użyciu uwierzytelniania konta użytkownika, wybrany. Widoczny jest sposób konfigurowania tożsamości platformy ASP.NET Core przy użyciu EntityFramework.Core w metodzie Startup.ConfigureServices.

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

Po skonfigurowaniu tożsamości platformy ASP.NET Core można włączyć aplikacji wywołującej. UseIdentity w usłudze `Startup.Configure` metody.

Za pomocą tożsamości platformy ASP.NET Core umożliwia kilka scenariuszy:

- Utwórz nowe informacje o użytkowniku przy użyciu Menedżera UserManager typu (userManager.CreateAsync).

- Uwierzytelnianie użytkowników przy użyciu typu SignInManager. Możesz użyć `signInManager.SignInAsync` się bezpośrednio lub `signInManager.PasswordSignInAsync` do Potwierdź hasło użytkownika są prawidłowe, a następnie zarejestruj się.

- Tak, że kolejne żądania z poziomu przeglądarki będzie zawierać tożsamości zalogowanego użytkownika oraz oświadczeń, należy zidentyfikować użytkownika, na podstawie informacji przechowywanych w pliku cookie (który jest odczytywany przez oprogramowanie pośredniczące tożsamości platformy ASP.NET Core).

Tożsamości platformy ASP.NET Core obsługuje również [uwierzytelniania dwuskładnikowego](/aspnet/core/security/authentication/2fa).

Scenariusze uwierzytelniania, które korzystanie z magazynu danych użytkowników lokalnych i utrzymują się tożsamości między żądaniami, przy użyciu plików cookie (co jest typowe dla aplikacji sieci web MVC), platformy ASP.NET Core Identity jest zalecanym rozwiązaniem.

### <a name="authenticate-with-external-providers"></a>Uwierzytelnianie za pomocą dostawców zewnętrznych

ASP.NET Core obsługuje również przy użyciu [dostawcy uwierzytelniania zewnętrznego](/aspnet/core/security/authentication/social/) Aby zezwolić użytkownikom na logowanie za pomocą [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) przepływów. Oznacza to, że użytkownicy mogą logować się za pomocą istniejących procesów uwierzytelniania od dostawców, takich jak Microsoft, Google, Facebook lub Twitter i skojarzenia tych tożsamości przy użyciu tożsamości platformy ASP.NET Core w aplikacji.

Aby użyć uwierzytelniania zewnętrznego, możesz uwzględnić odpowiednie oprogramowanie pośredniczące uwierzytelniania w żądaniu HTTP aplikacji, przetwarzania potoku. To oprogramowanie pośredniczące jest odpowiedzialny za obsługę żądań do zwracania identyfikatora URI trasy z dostawcy uwierzytelniania: Przechwytywanie informacji o tożsamości i udostępniając je za pomocą metody SignInManager.GetExternalLoginInfo.

W poniższej tabeli przedstawiono popularne zewnętrznych dostawców tożsamości i ich skojarzone pakiety NuGet:

| **Dostawca**  | **Pakiet**                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Microsoft.AspNetCore.Authentication.MicrosoftAccount** |
| **Google**    | **Microsoft.AspNetCore.Authentication.Google**           |
| **Facebook**  | **Microsoft.AspNetCore.Authentication.Facebook**         |
| **Twitter**   | **Microsoft.AspNetCore.Authentication.Twitter**          |

We wszystkich przypadkach, oprogramowanie pośredniczące jest zarejestrowana przy użyciu wywołania do metody rejestracji, podobnie jak `app.Use{ExternalProvider}Authentication` w `Startup.Configure`. Te metody rejestracji przyjmują opcje obiekt, który zawiera identyfikator aplikacji i danych dotyczących tajnych informacji (hasła, na przykład), zgodnie z potrzebami przez dostawcę. Zewnętrzni dostawcy uwierzytelniania wymagać od aplikacji zarejestrowania (jak wyjaśniono w [dokumentacji platformy ASP.NET Core](/aspnet/core/security/authentication/social/)) tak, aby ich mogą informować użytkownika żąda dostępu do tożsamości aplikacji.

Po zarejestrowaniu oprogramowanie pośredniczące w `Startup.Configure`, możesz też monitować użytkowników, aby zalogować się z dowolnej akcji kontrolera. Aby to zrobić, należy utworzyć `AuthenticationProperties` obiekt, który zawiera nazwę dostawcy uwierzytelniania i adres URL przekierowania. Następnie zwraca odpowiedź na żądanie przekazuje `AuthenticationProperties` obiektu. Poniższy kod przedstawia przykład.

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

Ten parametr redirectUrl zawiera adres URL zewnętrznego dostawcy powinna kierować do po użytkownik został uwierzytelniony. Adres URL powinien reprezentować akcję, która będzie zalogować użytkownika na podstawie informacji z tożsamości zewnętrznej, jak w poniższym przykładzie uproszczona:

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

Jeśli wybierzesz **pojedyncze konto użytkownika** opcję uwierzytelniania podczas tworzenia projektu aplikacji sieci web platformy ASP.NET kodu w programie Visual Studio, należy zalogować się przy użyciu zewnętrznego dostawcy kodu znajduje się już w projekcie, jak pokazano w rysunek 9-3.

![Okno dialogowe Nowy ASP.NET Core aplikacji sieci Web, wyróżnianie przycisk, aby zmienić uwierzytelniania.](./media/image3.png)

**Rysunek 9-3**. Wybranie opcji korzystania z funkcji uwierzytelniania zewnętrznego, podczas tworzenia projektu aplikacji sieci web

Oprócz uwierzytelniania zewnętrznego dostawcy wymienionych wcześniej pakietów innych firm są dostępne, zapewniających przy użyciu wielu bardziej zewnętrznych dostawców uwierzytelniania oprogramowania pośredniczącego. Aby uzyskać listę, zobacz [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repozytorium w witrynie GitHub.

Można również utworzyć własne zewnętrzne oprogramowanie pośredniczące uwierzytelniania rozwiązać pewne specjalne potrzeby.

### <a name="authenticate-with-bearer-tokens"></a>Uwierzytelnianie za pomocą tokenów elementu nośnego

Uwierzytelnianie za pomocą tożsamości platformy ASP.NET Core (lub tożsamości oraz dostawców uwierzytelniania zewnętrznych) działa dobrze w przypadku wielu scenariuszy aplikacji sieci web, w których jest zapisywanie informacji o użytkowniku w pliku cookie. W innych przypadkach jednak pliki cookie nie są naturalnych środków, przechowywanie i przesyłanie danych.

Na przykład w interfejsie API sieci Web platformy ASP.NET Core punktów końcowych RESTful, które mogą być używane przez aplikacje jednostronicowe (źródła), która udostępnia przez klientów natywnych, lub nawet przez inne interfejsy API sieci Web, zazwyczaj chcesz użyć uwierzytelniania tokenu elementu nośnego. Aplikacje tego typu nie współpracują z plików cookie, ale można łatwo pobierania tokenu elementu nośnego i uwzględniania go w nagłówku autoryzacji kolejnych żądań. Aby włączyć uwierzytelnianie przy użyciu tokenów, ASP.NET Core obsługuje kilka opcji za pomocą [OAuth 2.0](https://oauth.net/2/) i [OpenID Connect](https://openid.net/connect/).

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>Uwierzytelnianie przy użyciu dostawcy OpenID Connect i OAuth 2.0 tożsamości

Jeśli informacje o użytkowniku są przechowywane w usłudze Azure Active Directory lub innego rozwiązania tożsamości, które obsługuje OpenID Connect i OAuth 2.0, możesz użyć **Microsoft.AspNetCore.Authentication.OpenIdConnect** pakietu do uwierzytelniania za pomocą Przepływ protokołu OpenID Connect. Na przykład, aby uwierzytelniać się na mikrousługach Identity.Api w ramach aplikacji eShopOnContainers, aplikację sieci web platformy ASP.NET Core użyć oprogramowania pośredniczącego z tego pakietu jak pokazano w poniższym przykładzie uproszczona w `Startup.cs`:

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

Należy pamiętać, korzystając z tego przepływu pracy, oprogramowanie pośredniczące tożsamości platformy ASP.NET Core nie jest potrzebna, ponieważ wszystkie przechowywania informacji użytkownika i uwierzytelnianie jest obsługiwane przez usługę tożsamości.

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>Wystawiać tokeny zabezpieczające od usługi platformy ASP.NET Core

Jeśli chcesz wystawiać tokeny zabezpieczające dla użytkowników lokalnych tożsamości platformy ASP.NET Core, a nie przy użyciu zewnętrznego dostawcy tożsamości, możesz korzystać z zalet pewne dobre bibliotek innych firm.

[Pomocą usługi IdentityServer4](https://github.com/IdentityServer/IdentityServer4) i [OpenIddict](https://github.com/openiddict/openiddict-core) dostawców uwierzytelniania OpenID Connect, które łatwo zintegrować z tożsamości platformy ASP.NET Core, aby umożliwić wydawania tokenów zabezpieczających usługi sieci Web platformy ASP.NET Core. [Dokumentacji pomocą usługi IdentityServer4](https://identityserver4.readthedocs.io/en/latest/) zawiera szczegółowe instrukcje dotyczące korzystania z biblioteki. Jednak podstawowe kroki, które korzystają z pomocą usługi IdentityServer4 do wydawania tokenów są w następujący sposób.

1. Możesz wywołać aplikacji. UseIdentityServer w metodzie Startup.Configure dodać pomocą usługi IdentityServer4 do potoku przetwarzania żądań HTTP w aplikacji. Dzięki temu biblioteki, obsługiwać żądań uwierzytelniania OpenID Connect i punktów końcowych protokołu OAuth2, takich jak /connect/token.

2. Możesz skonfigurować pomocą usługi IdentityServer4 w Startup.ConfigureServices przez wywołania do usług. AddIdentityServer.

3. Możesz skonfigurować serwer tożsamości, ustawiając następujące dane:

   - [Poświadczenia](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) do użycia podczas podpisywania.

   - [Tożsamość i interfejs API zasobów](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) czy użytkownicy mogą żądać dostępu do:

      - Zasoby interfejsu API reprezentuje chronionych danych lub funkcji, których użytkownik może uzyskać dostęp przy użyciu tokenu dostępu. Przykładem zasobu interfejsu API może być, interfejs API sieci web (lub zestaw interfejsów API), wymaga autoryzacji.

      - Zasoby tożsamości reprezentują informacje (oświadczeń), które podano na kliencie do identyfikacji użytkownika. Oświadczenia mogą obejmować nazwę użytkownika, adres e-mail i tak dalej.

   - [Klientów](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) będą łączyć, aby żądać tokenów.

   - Mechanizm magazynu, aby uzyskać informacje o użytkowniku, takie jak [tożsamości platformy ASP.NET Core](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) lub alternatywnej.

Po określeniu, klientów i zasoby dotyczące pomocą usługi IdentityServer4 do użycia, możesz przekazać <xref:System.Collections.Generic.IEnumerable%601> kolekcji odpowiedniego typu do metod, które przyjmują magazynów klienta lub zasobu w pamięci. Lub w przypadku bardziej złożonych scenariuszy, można dostarczyć klienta lub zasobów dostawcy typów za pomocą iniekcji zależności.

Przykładowa konfiguracja pomocą usługi IdentityServer4 do użycia zasobów w pamięci i klientów, dostarczone przez typ niestandardowy IClientStore może wyglądać następująco:

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a>Używanie tokenów zabezpieczających

Uwierzytelniania w odniesieniu do punktu końcowego protokołu OpenID Connect lub wystawianie tokenów zabezpieczeń obejmuje kilka scenariuszy. Ale co to usługa, która po prostu wymaga, aby ograniczyć dostęp do tych użytkowników, którzy mają prawidłowy zabezpieczeń tokenów, które zostały dostarczone przez inną usługę?

W tym scenariuszu, oprogramowanie pośredniczące uwierzytelniania, która obsługuje tokeny JWT jest dostępna w **Microsoft.AspNetCore.Authentication.JwtBearer** pakietu. Token JWT oznacza "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" i jest wspólny format tokenu zabezpieczeń (zdefiniowanej przez RFC 7519) do komunikacji oświadczeń zabezpieczeń. Uproszczony przykład sposobu użycia oprogramowania pośredniczącego do korzystają z tych tokenów może wyglądać jak ten fragment kodu, pobranego z mikrousług Ordering.Api z w ramach aplikacji eShopOnContainers.

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

Parametry to wykorzystania są następujące:

- `Audience` reprezentuje odbiorcy przychodzącego tokenu lub tokenów przyznaje dostęp do zasobu. Jeśli wartości określonej w tym parametrze nie jest zgodny z parametrem w tokenie, token zostanie odrzucone.

- `Authority` jest adresem serwera wystawiania tokenu uwierzytelniania. Oprogramowanie pośredniczące uwierzytelniania elementu nośnego JWT używa tego identyfikatora URI, aby uzyskać klucz publiczny, który może służyć do weryfikowania podpisu tokenu. Oprogramowanie pośredniczące również potwierdza, że `iss` parametru w tokenie pasuje do tego identyfikatora URI.

Inny parametr `RequireHttpsMetadata`, jest przydatne podczas testowania; ten parametr zostanie ustawiony na wartość false aby możliwe było przetestowanie w środowiskach, w której nie masz certyfikatów. W przypadku rzeczywistych wdrożeń tokenów elementu nośnego JWT zawsze zostanie przekazana tylko przy użyciu protokołu HTTPS.

Z tego oprogramowania pośredniczącego w miejscu tokenów JWT, są automatycznie wyodrębniane z nagłówków autoryzacji. Są one następnie deserializacji, zatwierdzone (przy użyciu wartości w `Audience` i `Authority` parametrów) i przechowywane jako informacje o użytkowniku późniejsze przywoływanie przez akcje MVC lub filtry autoryzacji.

Oprogramowanie pośredniczące uwierzytelniania elementu nośnego JWT może również obsługiwać bardziej zaawansowane scenariusze, takie jak przy użyciu lokalnego certyfikatu do sprawdzania poprawności tokenu, jeśli uprawnienia nie jest dostępna. W tym scenariuszu można określić `TokenValidationParameters` obiektu `JwtBearerOptions` obiektu.

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Współużytkowanie plików cookie między aplikacjami** \
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- **Wprowadzenie do tożsamości** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Rick Anderson. Uwierzytelnianie dwuskładnikowe za pomocą wiadomości SMS** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- **Włączanie uwierzytelniania za pomocą usługi Facebook, Google i innych dostawców zewnętrznych** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- **Michell Anicas. Wprowadzenie do protokołu OAuth 2** \
  [https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

- **AspNet.Security.OAuth.Providers** (repozytorium GitHub dla dostawców uwierzytelniania OAuth ASP.NET) \
  [https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

- **Danny Strockis. Integrowanie usługi Azure AD dla aplikacji sieci web ASP.NET Core** \
  [https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

- **IdentityServer4. Oficjalna dokumentacja** \
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
>[Poprzednie](../implement-resilient-applications/monitor-app-health.md)
>[dalej](authorization-net-microservices-web-applications.md)
