---
title: Zabezpieczanie Mikrousług .NET i aplikacji sieci Web
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Zabezpieczanie Mikrousług .NET i aplikacji sieci Web
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: c2c7d692517c6a46225542936e05656db915bf0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="securing-net-microservices-and-web-applications"></a>Zabezpieczanie Mikrousług .NET i aplikacji sieci Web

Często jest to niezbędne do zasobów i interfejsach API udostępnianych przez usługę ograniczone do niektórych Zaufani użytkownicy lub klienci. Pierwszym krokiem do wprowadzania tego rodzaju decyzje zaufania poziom interfejsu API jest uwierzytelnianie. Uwierzytelnianie to proces niezawodnie ustalenia tożsamości użytkownika.

W scenariuszach mikrousługi uwierzytelniania zwykle odbywa się centralnie. Jeśli korzystasz z bramy usługi interfejsu API, brama jest dobrym miejscem do uwierzytelniania, jak pokazano w rysunek 11-1. Jeśli użyjesz tej metody upewnij się, czy poszczególnych mikrousług nie można połączyć bezpośrednio (bez bram interfejsu API), chyba że dodatkowe zabezpieczenia w celu uwierzytelniania wiadomości czy pochodzą z bramy lub nie.

![](./media/image1.png)

**Rysunek 11-1**. Scentralizowane uwierzytelnianie z bramą interfejsu API

Jeśli usługi są dostępne bezpośrednio, usługi uwierzytelniania, takich jak Azure Active Directory lub mikrousługi dedykowanych uwierzytelniania, działając jako zabezpieczeń usługi tokenów (STS) może być używane do uwierzytelniania użytkowników. Decyzje zaufania są wspólne dla usług z tokenów zabezpieczających lub plików cookie. (Może być udostępniane między aplikacjami, w razie potrzeby w ASP.NET Core z [usługi ochrony danych](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Ten wzorzec jest przedstawione na rysunku nr 11-2.

![](./media/image2.png)

**Rysunek 11-2**. Uwierzytelnianie przez mikrousługi tożsamości; zaufanie jest udostępniany przy użyciu tokenu autoryzacji

## <a name="authenticating-using-aspnet-core-identity"></a>Uwierzytelnianie za pomocą ASP.NET Core Identity

Podstawowy mechanizm platformy ASP.NET Core do identyfikacji użytkowników aplikacji jest [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) systemu członkostwa. Tożsamość platformy ASP.NET Core przechowuje informacje o użytkowniku (w tym informacje logowania, ról i oświadczeń) w magazynie danych skonfigurowane przez dewelopera. Zazwyczaj ASP.NET Core Identity magazynu danych jest magazyn programu Entity Framework, podany w pakiecie Microsoft.AspNetCore.Identity.EntityFrameworkCore. Jednak niestandardowe magazyny inne pakiety innych firm mogą służyć lub do przechowywania informacji o tożsamości w magazynu tabel Azure, usługa DocumentDB lub w innych lokalizacjach.

Poniższy kod jest pobierana z szablonu projektu aplikacji sieci Web platformy ASP.NET Core z wybrane uwierzytelnienia konta użytkownika. Widoczny jest sposób konfigurowania ASP.NET Identity Core za pomocą EntityFramework.Core w metodzie Startup.ConfigureServices.

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

Po skonfigurowaniu ASP.NET Core Identity Włącz przez wywołanie aplikacji. UseIdentity w metodzie Startup.Configure usługi.

Przy użyciu tożsamości kodu ASP.NET umożliwia kilka scenariuszy:

-   Utwórz nowe informacje o użytkowniku przy użyciu typu interfejs UserManager (userManager.CreateAsync).

-   Uwierzytelnianie użytkowników przy użyciu typu SignInManager. SignInManager.SignInAsync można użyć do logowania się bezpośrednio lub signInManager.PasswordSignInAsync o potwierdzenie hasła jest prawidłowa, a następnie zaloguj je.

-   Identyfikacji użytkownika na podstawie informacji przechowywanych w pliku cookie (który jest odczytywany przez oprogramowanie pośredniczące ASP.NET Core Identity), tak aby kolejnych żądań wysyłanych z przeglądarką uwzględni tożsamość zalogowanego użytkownika i oświadczeń.

ASP.NET Core Identity obsługuje również [uwierzytelniania dwuskładnikowego](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).

Scenariusze uwierzytelniania, należy użyć magazynu danych użytkowników lokalnych i który utrwalenia tożsamości między żądaniami używanie plików cookie (podobnie jak w typowej aplikacji sieci web MVC), ASP.NET Core Identity jest zalecanym rozwiązaniem.

## <a name="authenticating-using-external-providers"></a>Uwierzytelnianie przy użyciu zewnętrznego dostawcy

Platformy ASP.NET Core obsługuje również przy użyciu [zewnętrzni dostawcy uwierzytelniania](https://docs.microsoft.com/aspnet/core/security/authentication/social/) umożliwi użytkownikom zalogować się za pośrednictwem [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) przepływów. Oznacza to, że użytkownicy mogą Zaloguj się za pomocą istniejące procesy uwierzytelniania od dostawców, takich jak Microsoft, Google, Facebook lub Twitter i skojarzyć tych tożsamości przy użyciu tożsamości platformy ASP.NET Core w aplikacji.

Aby użyć uwierzytelniania zewnętrznego, możesz uwzględnić odpowiednie oprogramowanie pośredniczące uwierzytelniania w żądaniu HTTP aplikacji przetwarzania potoku. To oprogramowanie pośredniczące jest odpowiedzialny za żądań obsługi zwrócić trasy identyfikatora URI z dostawcy uwierzytelniania: Przechwytywanie informacji o tożsamości i udostępniania przy użyciu metody SignInManager.GetExternalLoginInfo.

Poniżej przedstawiono popularne zewnętrzni dostawcy uwierzytelniania i ich skojarzonych pakietów NuGet.

**Firmy Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount

**Google:** Microsoft.AspNetCore.Authentication.Google

**Facebook:** Microsoft.AspNetCore.Authentication.Facebook

**Twitter:** Microsoft.AspNetCore.Authentication.Twitter

We wszystkich przypadkach oprogramowanie pośredniczące jest zarejestrowany w wywołaniu metody rejestracji podobne do aplikacji. Uwierzytelnianie {ExternalProvider} Startup.Configure. Te metody rejestracji przyjmują opcje obiekt, który zawiera identyfikator aplikacji i tajnych informacji (hasła, na przykład), w razie potrzeby przez dostawcę. Zewnętrzni dostawcy uwierzytelniania wymagają aplikacji ma zostać zarejestrowany (zgodnie z objaśnieniem w [dokumentacji platformy ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/social/)), dzięki czemu można informują użytkownik żąda dostępu do tożsamości jakie aplikacji.

Po zarejestrowaniu oprogramowanie pośredniczące w Startup.Configure możesz monitować użytkowników o logowania z dowolnej akcji kontrolera. Aby to zrobić, należy utworzyć obiekt AuthenticationProperties, który zawiera nazwę dostawcy uwierzytelniania i adres URL przekierowania. Zostanie zwrócona odpowiedź na żądanie przekazuje obiekt AuthenticationProperties. Poniższy kod przedstawia przykład.

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

Parametr redirectUrl zawiera adres URL, który zewnętrznego dostawcy powinna kierować do po uwierzytelnieniu użytkownika. Adres URL powinien reprezentuje akcję, która będzie zalogować użytkownika na podstawie informacji o tożsamości zewnętrznej, jak w poniższym przykładzie uproszczony:

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

Jeśli wybierzesz **indywidualne konto użytkownika** opcję uwierzytelniania podczas tworzenia projektu aplikacji sieci web ASP.NET kodu w programie Visual Studio, należy zalogować się przy użyciu zewnętrznego dostawcy kodu znajduje się już w projekcie, jak pokazano na rysunku 11-3.

![https://msdnshared.blob.core.windows.net/media/2016/10/new-web-app.png](./media/image3.png)

**Rysunek 11-3**. Wybranie opcji korzystania z funkcji uwierzytelniania zewnętrznego, podczas tworzenia projektu aplikacji sieci web

Oprócz uwierzytelniania zewnętrznego dostawcy wymienionymi wcześniej, pakiety innych firm są dostępne, zapewniających przy użyciu wielu bardziej zewnętrznych dostawców uwierzytelniania oprogramowania pośredniczącego. Aby uzyskać listę, zobacz [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repozytorium w witrynie GitHub.

Istnieje również możliwość, aby utworzyć własne oprogramowanie pośredniczące uwierzytelniania zewnętrznego.

## <a name="authenticating-with-bearer-tokens"></a>Uwierzytelnianie za pomocą tokenów elementu nośnego

Uwierzytelniania w produkcie ASP.NET Identity Core (lub tożsamości i zewnętrzni dostawcy uwierzytelniania) działa dobrze w przypadku wielu scenariuszy aplikacji sieci web, w których jest przechowywania informacji o użytkowniku w pliku cookie. W innych sytuacjach, pliki cookie nie są fizyczną oznacza przechowywanie i przesyłania danych.

Na przykład w interfejsie API sieci Web platformy ASP.NET Core RESTful punktów końcowych, które mogą być używane przez aplikacje jednostronicowe (źródła), która udostępnia w klientach natywnych, lub nawet przez innych interfejsów API sieci Web, zazwyczaj chcesz zamiast tego użyj tokenu uwierzytelniania elementu nośnego. Aplikacje tego typu nie pracować z plików cookie, ale można łatwo pobrania tokenu elementu nośnego i uwzględnić go w kolejnych żądań w nagłówku autoryzacji. Aby włączyć uwierzytelnianie tokenu, platformy ASP.NET Core obsługuje kilka opcji przy użyciu [OAuth 2.0](https://oauth.net/2/) i [OpenID Connect](https://openid.net/connect/).

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a>Uwierzytelnianie przy użyciu dostawcy OpenID Connect lub tożsamość OAuth 2.0

Jeśli informacje użytkownika są przechowywane w usłudze Azure Active Directory lub innego rozwiązania tożsamości, które obsługuje OpenID Connect i OAuth 2.0, pakietu Microsoft.AspNetCore.Authentication.OpenIdConnect możesz używać do uwierzytelniania za pomocą przepływu pracy OpenID Connect. Na przykład, aby [uwierzytelniania usługi Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), aplikacji sieci web platformy ASP.NET Core można użyć oprogramowania pośredniczącego z tego pakietu, jak pokazano w poniższym przykładzie:

```csharp
// Configure the OWIN pipeline to use OpenID Connect auth
app.UseOpenIdConnectAuthentication(new OpenIdConnectOptions
{
    ClientId = Configuration["AzureAD:ClientId"],
    Authority = String.Format(Configuration["AzureAd:AadInstance"],
    Configuration["AzureAd:Tenant"]),
    ResponseType = OpenIdConnectResponseType.IdToken,
    PostLogoutRedirectUri = Configuration["AzureAd:PostLogoutRedirectUri"]
});
```

Wartości konfiguracji są wartości usługi Azure Active Directory, które są tworzone, gdy aplikacja jest [zarejestrowany jako klient usługi Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad). Identyfikator jednego klienta mogą być współużytkowane przez wiele mikrousług w aplikacji, jeśli wszystkie wymagane do uwierzytelniania użytkowników uwierzytelnionych za pośrednictwem usługi Azure Active Directory.

Należy pamiętać, czy użycie tego przepływu pracy, oprogramowanie pośredniczące ASP.NET Core Identity nie jest potrzebna, ponieważ wszystkie magazynu informacje użytkownika i uwierzytelnianie jest obsługiwane przez usługę Azure Active Directory.

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a>Wystawianie tokenów zabezpieczeń z usługą platformy ASP.NET Core

Jeśli wolisz wystawiać tokeny zabezpieczające dla użytkowników lokalnych ASP.NET Core Identity, a nie przy użyciu dostawcy tożsamości zewnętrznych, możesz korzystać niektórych dobrej bibliotek innych firm.

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) i [OpenIddict](https://github.com/openiddict/openiddict-core) OpenID Connect dostawców, które łatwo zintegrować z ASP.NET Identity Core pozwala wydawania tokenów zabezpieczających z usługą platformy ASP.NET Core. [Dokumentacji IdentityServer4](https://identityserver4.readthedocs.io/en/release/) zawiera szczegółowe instrukcje dotyczące korzystania z biblioteki. Jednak podstawowe kroki z użyciem IdentityServer4 do wydawania tokenów są następujące.

1.  Aplikacja jest wywoływana. UseIdentityServer w metodzie Startup.Configure, aby dodać IdentityServer4 do potoku przetwarzania żądań HTTP w aplikacji. Dzięki temu biblioteki obsługiwać żądań do punktów końcowych OAuth2, takich jak /connect/token i OpenID Connect.

2.  Należy skonfigurować IdentityServer4 w Startup.ConfigureServices za wywołania do usług. AddIdentityServer.

3.  Możesz skonfigurować serwer tożsamości podając następujące dane:

-   [Poświadczenia](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) do użycia podczas podpisywania.

-   [Tożsamości i interfejs API zasobów](https://identityserver4.readthedocs.io/en/release/topics/resources.html) czy użytkownicy mogą żądać dostępu do:

<!-- -->

-   Zasoby interfejsu API reprezentuje chronionych danych i działania, które użytkownik może korzystać z tokenem dostępu. Przykładem zasobu interfejsu API może być interfejsu API sieci web (lub zestaw interfejsów API) która wymaga autoryzacji.

-   Tożsamość zasobów reprezentuje informacje (oświadczeń), które podano na kliencie do identyfikacji użytkownika. Oświadczenia mogą obejmować nazwę użytkownika, adres e-mail i tak dalej.

<!-- -->

-   [Klientów](https://identityserver4.readthedocs.io/en/release/topics/clients.html) które będą łączyć do żądania tokenów.

-   Mechanizm przechowywania informacji o użytkownikach, takich jak [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) lub alternatywnej.

Po określeniu klientów oraz zasoby IdentityServer4 do używania, można przekazać elementu IEnumerable&lt;T&gt; kolekcji odpowiedniego typu do metod przyjmujących magazynów klienta lub zasobu w pamięci. Lub dla bardziej złożonymi scenariuszami, możesz podać klienta lub zasobu dostawcy typów za pomocą iniekcji zależności.

Przykładowa konfiguracja IdentityServer4 użycie zasobów w pamięci i udostępniane przez typ niestandardowy IClientStore klientów może wyglądać następująco:

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a>Korzystanie z tokenów zabezpieczających

Uwierzytelniany punkt końcowy protokołu OpenID Connect lub wystawianie tokenów zabezpieczeń obejmuje kilka scenariuszy. Ale co usługa, która wystarczy do ograniczenia dostępu do tych użytkowników, którzy mają prawidłowy zabezpieczeń tokeny, które zostały dostarczone przez inną usługę?

Dla tego scenariusza oprogramowanie pośredniczące uwierzytelniania, która obsługuje tokeny JWT jest niedostępny w pakiecie Microsoft.AspNetCore.Authentication.JwtBearer. Oznacza JWT "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" i jest typowe format tokenu zabezpieczeń (zdefiniowany w dokumencie RFC 7519) do komunikacji oświadczeń zabezpieczeń. Prosty przykład sposobu użycia oprogramowania pośredniczącego użycie tych tokenów może wyglądać jak w następującym przykładzie. Ten kod musi poprzedzać wywołania z oprogramowaniem pośredniczącym platformy ASP.NET Core MVC (aplikacja. UseMvc).

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

Dostępne są następujące parametry w ten sposób użycia:

-   Grupy odbiorców reprezentuje odbiornika przychodzącego tokenu lub tokenów udziela dostępu do zasobu. Jeśli wartość określona w tym parametrze nie jest zgodny z parametrem lub w tokenie, token zostanie odrzucone.

-   Urząd jest adres serwera wystawiania tokenu uwierzytelniania. Oprogramowanie pośredniczące uwierzytelniania elementu nośnego JWT używa tego identyfikatora URI w celu uzyskania klucza publicznego, który może służyć do sprawdzania poprawności podpisu tokenu. Oprogramowanie pośredniczące również potwierdza, czy parametr iss w tokenie zgodna tego identyfikatora URI.

-   AutomaticAuthenticate jest wartością logiczną, wskazującą, czy określone przez token powinny być automatycznie logowania użytkownika.

Inny parametr, RequireHttpsMetadata, nie jest używany w tym przykładzie. Jest przydatne w przypadku testowania; Ten parametr jest ustawiony na wartość false tak, aby można było testować w środowiskach, w którym nie ma certyfikatów. W przypadku rzeczywistych wdrożeń tokenów elementu nośnego JWT zawsze można przekazać tylko za pośrednictwem protokołu HTTPS.

Z tego oprogramowania pośredniczącego w miejscu tokenów JWT automatycznie są wyodrębniane z nagłówki autoryzacji. One są następnie deserializowany, weryfikowane (przy użyciu wartości parametrów odbiorców i Urząd) i przechowywane jako informacje o użytkowniku przywoływanie później przez akcje MVC lub filtry autoryzacji.

Oprogramowanie pośredniczące uwierzytelniania elementu nośnego JWT może również obsługiwać bardziej zaawansowanych scenariuszy, takich jak przy użyciu lokalnego certyfikatu do sprawdzania poprawności tokenu, jeśli jako źródło nie jest dostępna. W tym scenariuszu można określić obiektu TokenValidationParameters w obiekcie JwtBearerOptions.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Udostępnianie plików cookie między aplikacjami**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#udostępnianie — uwierzytelnianie — pliki cookie między — aplikacje*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)

-   **Wprowadzenie do tożsamości**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Rick Anderson. Uwierzytelnianie dwuskładnikowe z programem SMS**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)

-   **Włączanie uwierzytelniania za pomocą usługi Facebook, Google i innych dostawców zewnętrznych**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)

-   **Michell Anicas. Wprowadzenie do protokołu OAuth 2**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

-   **AspNet.Security.OAuth.Providers** (repozytorium GitHub dla dostawców uwierzytelniania OAuth ASP.NET.
    [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   **Danny Strockis. Integrowanie usługi Azure AD aplikacji sieci web platformy ASP.NET Core**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

-   **IdentityServer4. Oficjalnej dokumentacji**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)


>[!div class="step-by-step"]
[Poprzednie] (.. /Implement-resilient-Applications/Monitor-App-Health.MD) [dalej] (autoryzacji net mikrousług web-applications.md)
