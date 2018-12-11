---
title: Zabezpieczanie Mikrousług .NET i aplikacji sieci Web
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Zabezpieczanie Mikrousług .NET i aplikacji sieci Web
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 7ee559f3881101a2382e6767607d5de1482d74ba
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126474"
---
# <a name="securing-net-microservices-and-web-applications"></a><span data-ttu-id="34d8d-103">Zabezpieczanie Mikrousług .NET i aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="34d8d-103">Securing .NET Microservices and Web Applications</span></span>

<span data-ttu-id="34d8d-104">Często jest to niezbędne do zasobów i interfejsach API udostępnianych przez usługę ograniczone do niektórych Zaufani użytkownicy lub klienci.</span><span class="sxs-lookup"><span data-stu-id="34d8d-104">It is often necessary for resources and APIs exposed by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="34d8d-105">Pierwszym krokiem do wprowadzania tego rodzaju decyzji dotyczących zaufania poziom interfejsu API to uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="34d8d-105">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="34d8d-106">Uwierzytelnianie to proces niezawodnie ustalenia tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="34d8d-106">Authentication is the process of reliably ascertaining a user’s identity.</span></span>

<span data-ttu-id="34d8d-107">W scenariuszach mikrousług uwierzytelniania jest zazwyczaj obsługiwana centralnie.</span><span class="sxs-lookup"><span data-stu-id="34d8d-107">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="34d8d-108">Jeśli używasz bramy interfejsu API bramy jest dobrym miejscem do uwierzytelniania, jak pokazano w rysunek 11-1.</span><span class="sxs-lookup"><span data-stu-id="34d8d-108">If you are using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 11-1.</span></span> <span data-ttu-id="34d8d-109">Jeśli używasz tego podejścia, upewnij się, że poszczególne mikrousługi nie można połączyć bezpośrednio (bez bramy interfejsu API), chyba że zapewnienia dodatkowych zabezpieczeń w celu uwierzytelniania wiadomości tego, czy pochodzą one od bramą lub nie.</span><span class="sxs-lookup"><span data-stu-id="34d8d-109">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![](./media/image1.png)

<span data-ttu-id="34d8d-110">**Rysunek 11-1**.</span><span class="sxs-lookup"><span data-stu-id="34d8d-110">**Figure 11-1**.</span></span> <span data-ttu-id="34d8d-111">Scentralizowane uwierzytelnianie przy użyciu bramy interfejsu API</span><span class="sxs-lookup"><span data-stu-id="34d8d-111">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="34d8d-112">Jeśli usługi są dostępne bezpośrednio, usługi uwierzytelniania, takich jak Azure Active Directory lub mikrousług dedykowanych uwierzytelniania, pełniący funkcję zabezpieczeń, usługa tokenów (STS) może być używane do uwierzytelniania użytkowników.</span><span class="sxs-lookup"><span data-stu-id="34d8d-112">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="34d8d-113">Usługi za pomocą tokenów zabezpieczających lub pliki cookie są współużytkowane decyzji dotyczących zaufania.</span><span class="sxs-lookup"><span data-stu-id="34d8d-113">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="34d8d-114">(Te można udostępniać między aplikacjami, jeśli to konieczne, w programie ASP.NET Core za pomocą [usługi ochrony danych](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Ten wzorzec zilustrowano w rysunek 11-2.</span><span class="sxs-lookup"><span data-stu-id="34d8d-114">(These can be shared between applications, if needed, in ASP.NET Core with [data protection services](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) This pattern is illustrated in Figure 11-2.</span></span>

![](./media/image2.png)

<span data-ttu-id="34d8d-115">**Rysunek 11-2**.</span><span class="sxs-lookup"><span data-stu-id="34d8d-115">**Figure 11-2**.</span></span> <span data-ttu-id="34d8d-116">Uwierzytelnienia za pomocą tożsamości mikrousług; zaufanie jest udostępniany przy użyciu tokenu autoryzacji</span><span class="sxs-lookup"><span data-stu-id="34d8d-116">Authentication by identity microservice; trust is shared using an authorization token</span></span>

## <a name="authenticating-using-aspnet-core-identity"></a><span data-ttu-id="34d8d-117">Uwierzytelnianie za pomocą tożsamości platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="34d8d-117">Authenticating using ASP.NET Core Identity</span></span>

<span data-ttu-id="34d8d-118">Podstawowy mechanizm w programie ASP.NET Core do identyfikowania użytkowników w aplikacji jest [tożsamości platformy ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/identity) systemu członkostwa.</span><span class="sxs-lookup"><span data-stu-id="34d8d-118">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="34d8d-119">Tożsamości platformy ASP.NET Core przechowuje informacje o użytkowniku (w tym informacje logowania, ról i oświadczenia) w magazynie danych skonfigurowane przez dewelopera.</span><span class="sxs-lookup"><span data-stu-id="34d8d-119">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="34d8d-120">Zazwyczaj magazynu danych tożsamości platformy ASP.NET Core jest magazynem platformy Entity Framework, podany w pakiecie Microsoft.AspNetCore.Identity.EntityFrameworkCore.</span><span class="sxs-lookup"><span data-stu-id="34d8d-120">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the Microsoft.AspNetCore.Identity.EntityFrameworkCore package.</span></span> <span data-ttu-id="34d8d-121">Jednak inne pakiety innych firm lub niestandardowych magazynów może służyć do przechowywania informacji o tożsamości w usłudze Azure Table Storage, usługi DocumentDB lub w innych lokalizacjach.</span><span class="sxs-lookup"><span data-stu-id="34d8d-121">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, DocumentDB, or other locations.</span></span>

<span data-ttu-id="34d8d-122">Następujący kod pochodzi z szablonu projektu aplikacji sieci Web programu ASP.NET Core przy użyciu uwierzytelniania konta użytkownika, wybrany.</span><span class="sxs-lookup"><span data-stu-id="34d8d-122">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="34d8d-123">Widoczny jest sposób konfigurowania tożsamości platformy ASP.NET Core przy użyciu EntityFramework.Core w metodzie Startup.ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="34d8d-123">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="34d8d-124">Po skonfigurowaniu tożsamości platformy ASP.NET Core można włączyć aplikacji wywołującej. UseIdentity w metodzie Startup.Configure tej usługi.</span><span class="sxs-lookup"><span data-stu-id="34d8d-124">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s Startup.Configure method.</span></span>

<span data-ttu-id="34d8d-125">Za pomocą tożsamości platformy ASP.NET Core umożliwia kilka scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="34d8d-125">Using ASP.NET Core Identity enables several scenarios:</span></span>

-   <span data-ttu-id="34d8d-126">Utwórz nowe informacje o użytkowniku przy użyciu Menedżera UserManager typu (userManager.CreateAsync).</span><span class="sxs-lookup"><span data-stu-id="34d8d-126">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

-   <span data-ttu-id="34d8d-127">Uwierzytelnianie użytkowników przy użyciu typu SignInManager.</span><span class="sxs-lookup"><span data-stu-id="34d8d-127">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="34d8d-128">SignInManager.SignInAsync można użyć, aby zalogować się bezpośrednio lub signInManager.PasswordSignInAsync o potwierdzenie hasła jest prawidłowa, a następnie zaloguj je.</span><span class="sxs-lookup"><span data-stu-id="34d8d-128">You can use signInManager.SignInAsync to sign in directly, or signInManager.PasswordSignInAsync to confirm the user’s password is correct and then sign them in.</span></span>

-   <span data-ttu-id="34d8d-129">Tak, że kolejne żądania z poziomu przeglądarki będzie zawierać tożsamości zalogowanego użytkownika oraz oświadczeń, należy zidentyfikować użytkownika, na podstawie informacji przechowywanych w pliku cookie (który jest odczytywany przez oprogramowanie pośredniczące tożsamości platformy ASP.NET Core).</span><span class="sxs-lookup"><span data-stu-id="34d8d-129">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="34d8d-130">Tożsamości platformy ASP.NET Core obsługuje również [uwierzytelniania dwuskładnikowego](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="34d8d-130">ASP.NET Core Identity also supports [two-factor authentication](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="34d8d-131">Scenariusze uwierzytelniania, które korzystanie z magazynu danych użytkowników lokalnych i utrzymują się tożsamości między żądaniami, przy użyciu plików cookie (co jest typowe dla aplikacji sieci web MVC), platformy ASP.NET Core Identity jest zalecanym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="34d8d-131">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

## <a name="authenticating-using-external-providers"></a><span data-ttu-id="34d8d-132">Uwierzytelnianie przy użyciu dostawców zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="34d8d-132">Authenticating using external providers</span></span>

<span data-ttu-id="34d8d-133">ASP.NET Core obsługuje również przy użyciu [dostawcy uwierzytelniania zewnętrznego](https://docs.microsoft.com/aspnet/core/security/authentication/social/) umożliwiające użytkownikom zalogowanie się za pośrednictwem [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) przepływów.</span><span class="sxs-lookup"><span data-stu-id="34d8d-133">ASP.NET Core also supports using [external authentication providers](https://docs.microsoft.com/aspnet/core/security/authentication/social/) to let users log in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="34d8d-134">Oznacza to, że użytkownicy mogą zalogować się przy użyciu istniejące procesy uwierzytelniania od dostawców, takich jak Microsoft, Google, Facebook lub Twitter i skojarzenia tych tożsamości przy użyciu tożsamości platformy ASP.NET Core w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34d8d-134">This means that users can log in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="34d8d-135">Aby użyć uwierzytelniania zewnętrznego, możesz uwzględnić odpowiednie oprogramowanie pośredniczące uwierzytelniania w żądaniu HTTP aplikacji, przetwarzania potoku.</span><span class="sxs-lookup"><span data-stu-id="34d8d-135">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="34d8d-136">To oprogramowanie pośredniczące jest odpowiedzialny za obsługę żądań do zwracania identyfikatora URI trasy z dostawcy uwierzytelniania: Przechwytywanie informacji o tożsamości i udostępniając je za pomocą metody SignInManager.GetExternalLoginInfo.</span><span class="sxs-lookup"><span data-stu-id="34d8d-136">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="34d8d-137">Poniżej przedstawiono popularne zewnętrznych dostawców tożsamości i ich skojarzone pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="34d8d-137">Popular external authentication providers and their associated NuGet packages are shown below.</span></span>

<span data-ttu-id="34d8d-138">**Firmy Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span><span class="sxs-lookup"><span data-stu-id="34d8d-138">**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span></span>

<span data-ttu-id="34d8d-139">**Google:** Microsoft.AspNetCore.Authentication.Google</span><span class="sxs-lookup"><span data-stu-id="34d8d-139">**Google:** Microsoft.AspNetCore.Authentication.Google</span></span>

<span data-ttu-id="34d8d-140">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span><span class="sxs-lookup"><span data-stu-id="34d8d-140">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span></span>

<span data-ttu-id="34d8d-141">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span><span class="sxs-lookup"><span data-stu-id="34d8d-141">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span></span>

<span data-ttu-id="34d8d-142">We wszystkich przypadkach oprogramowanie pośredniczące jest zarejestrowana przy użyciu wywołania do metody rejestracji, podobne do aplikacji. Korzystać z Startup.Configure uwierzytelniania {ExternalProvider}.</span><span class="sxs-lookup"><span data-stu-id="34d8d-142">In all cases, the middleware is registered with a call to a registration method similar to app.Use{ExternalProvider}Authentication in Startup.Configure.</span></span> <span data-ttu-id="34d8d-143">Te metody rejestracji przyjmują opcje obiekt, który zawiera identyfikator aplikacji i danych dotyczących tajnych informacji (hasła, na przykład), zgodnie z potrzebami przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="34d8d-143">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="34d8d-144">Zewnętrzni dostawcy uwierzytelniania wymagać od aplikacji zarejestrowania (jak wyjaśniono w [dokumentacji platformy ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) tak, aby ich mogą informować użytkownika żąda dostępu do tożsamości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34d8d-144">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="34d8d-145">Po zarejestrowaniu oprogramowanie pośredniczące w Startup.Configure możesz monitować użytkowników o logowanie z dowolnej akcji kontrolera.</span><span class="sxs-lookup"><span data-stu-id="34d8d-145">Once the middleware is registered in Startup.Configure, you can prompt users to log in from any controller action.</span></span> <span data-ttu-id="34d8d-146">Aby to zrobić, należy utworzyć obiekt AuthenticationProperties, który zawiera nazwę dostawcy uwierzytelniania i adres URL przekierowania.</span><span class="sxs-lookup"><span data-stu-id="34d8d-146">To do this, you create an AuthenticationProperties object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="34d8d-147">Zostanie zwrócona odpowiedź na żądanie przekazuje obiekt AuthenticationProperties.</span><span class="sxs-lookup"><span data-stu-id="34d8d-147">You then return a Challenge response that passes the AuthenticationProperties object.</span></span> <span data-ttu-id="34d8d-148">Poniższy kod przedstawia przykład.</span><span class="sxs-lookup"><span data-stu-id="34d8d-148">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="34d8d-149">Ten parametr redirectUrl zawiera adres URL zewnętrznego dostawcy powinna kierować do po użytkownik został uwierzytelniony.</span><span class="sxs-lookup"><span data-stu-id="34d8d-149">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="34d8d-150">Adres URL powinien reprezentować akcję, która będzie zalogować użytkownika na podstawie informacji z tożsamości zewnętrznej, jak w poniższym przykładzie uproszczona:</span><span class="sxs-lookup"><span data-stu-id="34d8d-150">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

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

<span data-ttu-id="34d8d-151">Jeśli wybierzesz **pojedyncze konto użytkownika** opcję uwierzytelniania podczas tworzenia projektu aplikacji sieci web platformy ASP.NET kodu w programie Visual Studio, należy zalogować się przy użyciu zewnętrznego dostawcy kodu znajduje się już w projekcie, jak pokazano w rysunek 11-3.</span><span class="sxs-lookup"><span data-stu-id="34d8d-151">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 11-3.</span></span>

![https://msdnshared.blob.core.windows.net/media/2016/10/new-web-app.png](./media/image3.png)

<span data-ttu-id="34d8d-152">**Rysunek 11-3**.</span><span class="sxs-lookup"><span data-stu-id="34d8d-152">**Figure 11-3**.</span></span> <span data-ttu-id="34d8d-153">Wybranie opcji korzystania z funkcji uwierzytelniania zewnętrznego, podczas tworzenia projektu aplikacji sieci web</span><span class="sxs-lookup"><span data-stu-id="34d8d-153">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="34d8d-154">Oprócz uwierzytelniania zewnętrznego dostawcy wymienionych wcześniej pakietów innych firm są dostępne, zapewniających przy użyciu wielu bardziej zewnętrznych dostawców uwierzytelniania oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="34d8d-154">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="34d8d-155">Aby uzyskać listę, zobacz [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repozytorium w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="34d8d-155">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="34d8d-156">Użytkownik może również, oczywiście, aby utworzyć własne oprogramowanie pośredniczące uwierzytelniania zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="34d8d-156">It is also possible, of course, to create your own external authentication middleware.</span></span>

## <a name="authenticating-with-bearer-tokens"></a><span data-ttu-id="34d8d-157">Uwierzytelnianie za pomocą tokenów elementu nośnego</span><span class="sxs-lookup"><span data-stu-id="34d8d-157">Authenticating with bearer tokens</span></span>

<span data-ttu-id="34d8d-158">Uwierzytelnianie za pomocą tożsamości platformy ASP.NET Core (lub tożsamości oraz dostawców uwierzytelniania zewnętrznych) działa dobrze w przypadku wielu scenariuszy aplikacji sieci web, w których jest zapisywanie informacji o użytkowniku w pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="34d8d-158">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="34d8d-159">W innych przypadkach jednak pliki cookie nie są naturalnych środków, przechowywanie i przesyłanie danych.</span><span class="sxs-lookup"><span data-stu-id="34d8d-159">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="34d8d-160">Na przykład w interfejsie API sieci Web platformy ASP.NET Core punktów końcowych RESTful, które mogą być używane przez aplikacje jednostronicowe (źródła), która udostępnia przez klientów natywnych, lub nawet przez inne interfejsy API sieci Web, zazwyczaj chcesz użyć uwierzytelniania tokenu elementu nośnego.</span><span class="sxs-lookup"><span data-stu-id="34d8d-160">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="34d8d-161">Aplikacje tego typu nie współpracują z plików cookie, ale można łatwo pobierania tokenu elementu nośnego i uwzględniania go w nagłówku autoryzacji kolejnych żądań.</span><span class="sxs-lookup"><span data-stu-id="34d8d-161">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="34d8d-162">Aby włączyć uwierzytelnianie przy użyciu tokenów, ASP.NET Core obsługuje kilka opcji za pomocą [OAuth 2.0](https://oauth.net/2/) i [OpenID Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="34d8d-162">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="34d8d-163">Uwierzytelnianie przy użyciu dostawcy OpenID Connect i OAuth 2.0 tożsamości</span><span class="sxs-lookup"><span data-stu-id="34d8d-163">Authenticating with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="34d8d-164">Jeśli informacje o użytkowniku są przechowywane w usłudze Azure Active Directory lub innego rozwiązania tożsamości, które obsługuje OpenID Connect i OAuth 2.0, można użyć pakietu Microsoft.AspNetCore.Authentication.OpenIdConnect do uwierzytelniania za pomocą przepływu pracy uwierzytelniania OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="34d8d-164">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the Microsoft.AspNetCore.Authentication.OpenIdConnect package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="34d8d-165">Na przykład, aby [uwierzytelniania względem usługi Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), aplikacji sieci web programu ASP.NET Core można użyć oprogramowania pośredniczącego z tego pakietu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="34d8d-165">For example, to [authenticate against Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), an ASP.NET Core web application can use middleware from that package as shown in the following example:</span></span>

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

<span data-ttu-id="34d8d-166">Wartości konfiguracji są wartościami usługi Azure Active Directory, które są tworzone, gdy aplikacja jest [zarejestrowany jako klient usługi Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad).</span><span class="sxs-lookup"><span data-stu-id="34d8d-166">The configuration values are Azure Active Directory values that are created when your application is [registered as an Azure AD client](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad).</span></span> <span data-ttu-id="34d8d-167">Identyfikator pojedynczego klienta mogą być współużytkowane przez wiele mikrousług w aplikacji, jeśli wszystkie wymagają uwierzytelniania użytkowników uwierzytelnione za pośrednictwem usługi Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="34d8d-167">A single client ID can be shared among multiple microservices in an application if they all need to authenticate users authenticated via Azure Active Directory.</span></span>

<span data-ttu-id="34d8d-168">Należy pamiętać, korzystając z tego przepływu pracy, oprogramowanie pośredniczące tożsamości platformy ASP.NET Core nie jest potrzebna, ponieważ wszystkie przechowywania informacji użytkownika i uwierzytelnianie jest obsługiwane przez usługę Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="34d8d-168">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by Azure Active Directory.</span></span>

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="34d8d-169">Wystawianie tokeny zabezpieczające od usługi platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="34d8d-169">Issuing security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="34d8d-170">Jeśli chcesz wystawiać tokeny zabezpieczające dla użytkowników lokalnych tożsamości platformy ASP.NET Core, a nie przy użyciu zewnętrznego dostawcy tożsamości, możesz korzystać z zalet pewne dobre bibliotek innych firm.</span><span class="sxs-lookup"><span data-stu-id="34d8d-170">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="34d8d-171">[Pomocą usługi IdentityServer4](https://github.com/IdentityServer/IdentityServer4) i [OpenIddict](https://github.com/openiddict/openiddict-core) dostawców uwierzytelniania OpenID Connect, które łatwo zintegrować z tożsamości platformy ASP.NET Core, aby umożliwić wydawania tokenów zabezpieczających usługi sieci Web platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="34d8d-171">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="34d8d-172">[Dokumentacji pomocą usługi IdentityServer4](https://identityserver4.readthedocs.io/en/release/) zawiera szczegółowe instrukcje dotyczące korzystania z biblioteki.</span><span class="sxs-lookup"><span data-stu-id="34d8d-172">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/release/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="34d8d-173">Jednak podstawowe kroki, które korzystają z pomocą usługi IdentityServer4 do wydawania tokenów są w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="34d8d-173">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1.  <span data-ttu-id="34d8d-174">Możesz wywołać aplikacji. UseIdentityServer w metodzie Startup.Configure dodać pomocą usługi IdentityServer4 do potoku przetwarzania żądań HTTP w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34d8d-174">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="34d8d-175">Dzięki temu biblioteki, obsługiwać żądań uwierzytelniania OpenID Connect i punktów końcowych protokołu OAuth2, takich jak /connect/token.</span><span class="sxs-lookup"><span data-stu-id="34d8d-175">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2.  <span data-ttu-id="34d8d-176">Możesz skonfigurować pomocą usługi IdentityServer4 w Startup.ConfigureServices przez wywołania do usług. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="34d8d-176">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3.  <span data-ttu-id="34d8d-177">Możesz skonfigurować serwer tożsamości, zapewniając następujące dane:</span><span class="sxs-lookup"><span data-stu-id="34d8d-177">You configure identity server by providing the following data:</span></span>

-   <span data-ttu-id="34d8d-178">[Poświadczenia](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) do użycia podczas podpisywania.</span><span class="sxs-lookup"><span data-stu-id="34d8d-178">The [credentials](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) to use for signing.</span></span>

-   <span data-ttu-id="34d8d-179">[Tożsamość i interfejs API zasobów](https://identityserver4.readthedocs.io/en/release/topics/resources.html) czy użytkownicy mogą żądać dostępu do:</span><span class="sxs-lookup"><span data-stu-id="34d8d-179">The [Identity and API resources](https://identityserver4.readthedocs.io/en/release/topics/resources.html) that users might request access to:</span></span>

<!-- -->

-   <span data-ttu-id="34d8d-180">Zasoby interfejsu API reprezentuje chronionych danych lub funkcji, których użytkownik może uzyskać dostęp przy użyciu tokenu dostępu.</span><span class="sxs-lookup"><span data-stu-id="34d8d-180">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="34d8d-181">Przykładem zasobu interfejsu API może być, interfejs API sieci web (lub zestaw interfejsów API), wymaga autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="34d8d-181">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

-   <span data-ttu-id="34d8d-182">Zasoby tożsamości reprezentują informacje (oświadczeń), które podano na kliencie do identyfikacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="34d8d-182">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="34d8d-183">Oświadczenia mogą obejmować nazwę użytkownika, adres e-mail i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="34d8d-183">The claims might include the user name, email address, and so on.</span></span>

<!-- -->

-   <span data-ttu-id="34d8d-184">[Klientów](https://identityserver4.readthedocs.io/en/release/topics/clients.html) będą łączyć, aby żądać tokenów.</span><span class="sxs-lookup"><span data-stu-id="34d8d-184">The [clients](https://identityserver4.readthedocs.io/en/release/topics/clients.html) that will be connecting in order to request tokens.</span></span>

-   <span data-ttu-id="34d8d-185">Mechanizm magazynu, aby uzyskać informacje o użytkowniku, takie jak [tożsamości platformy ASP.NET Core](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) lub alternatywnej.</span><span class="sxs-lookup"><span data-stu-id="34d8d-185">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) or an alternative.</span></span>

<span data-ttu-id="34d8d-186">Po określeniu, klientów i zasoby dotyczące pomocą usługi IdentityServer4 do użycia, można przekazać elementu IEnumerable&lt;T&gt; kolekcji odpowiedniego typu do metod, które przyjmują magazynów klienta lub zasobu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="34d8d-186">When you specify clients and resources for IdentityServer4 to use, you can pass an IEnumerable&lt;T&gt; collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="34d8d-187">Lub w przypadku bardziej złożonych scenariuszy, można dostarczyć klienta lub zasobów dostawcy typów za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="34d8d-187">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="34d8d-188">Przykładowa konfiguracja pomocą usługi IdentityServer4 do użycia zasobów w pamięci i klientów, dostarczone przez typ niestandardowy IClientStore może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="34d8d-188">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a><span data-ttu-id="34d8d-189">Wykorzystywanie tokeny zabezpieczające</span><span class="sxs-lookup"><span data-stu-id="34d8d-189">Consuming security tokens</span></span>

<span data-ttu-id="34d8d-190">Uwierzytelniania w odniesieniu do punktu końcowego protokołu OpenID Connect lub wystawianie tokenów zabezpieczeń obejmuje kilka scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="34d8d-190">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="34d8d-191">Ale co to usługa, która po prostu wymaga, aby ograniczyć dostęp do tych użytkowników, którzy mają prawidłowy zabezpieczeń tokenów, które zostały dostarczone przez inną usługę?</span><span class="sxs-lookup"><span data-stu-id="34d8d-191">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="34d8d-192">W tym scenariuszu oprogramowanie pośredniczące uwierzytelniania, która obsługuje tokeny JWT jest dostępne w pakiecie Microsoft.AspNetCore.Authentication.JwtBearer.</span><span class="sxs-lookup"><span data-stu-id="34d8d-192">For that scenario, authentication middleware that handles JWT tokens is available in the Microsoft.AspNetCore.Authentication.JwtBearer package.</span></span> <span data-ttu-id="34d8d-193">Token JWT oznacza "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" i jest wspólny format tokenu zabezpieczeń (zdefiniowanej przez RFC 7519) do komunikacji oświadczeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="34d8d-193">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="34d8d-194">Prosty przykład sposobu użycia oprogramowania pośredniczącego do korzystają z tych tokenów może wyglądać jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="34d8d-194">A simple example of how to use middleware to consume such tokens might look like the following example.</span></span> <span data-ttu-id="34d8d-195">Ten kod musi poprzedzać wywołania z oprogramowaniem pośredniczącym ASP.NET Core MVC (aplikacja. UseMvc).</span><span class="sxs-lookup"><span data-stu-id="34d8d-195">This code must precede calls to ASP.NET Core MVC middleware (app.UseMvc).</span></span>

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

<span data-ttu-id="34d8d-196">Parametry to wykorzystania są następujące:</span><span class="sxs-lookup"><span data-stu-id="34d8d-196">The parameters in this usage are:</span></span>

-   <span data-ttu-id="34d8d-197">Odbiorcy reprezentuje odbiorcy przychodzącego tokenu lub tokenów przyznaje dostęp do zasobu.</span><span class="sxs-lookup"><span data-stu-id="34d8d-197">Audience represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="34d8d-198">Wartość określona w tym parametrze niezgodny parametr aud w tokenie token zostanie odrzucone.</span><span class="sxs-lookup"><span data-stu-id="34d8d-198">If the value specified in this parameter does not match the aud parameter in the token, the token will be rejected.</span></span>

-   <span data-ttu-id="34d8d-199">Urząd jest adres serwera uwierzytelniania wystawiania tokenu.</span><span class="sxs-lookup"><span data-stu-id="34d8d-199">Authority is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="34d8d-200">Oprogramowanie pośredniczące uwierzytelniania elementu nośnego JWT używa tego identyfikatora URI, aby uzyskać klucz publiczny, który może służyć do weryfikowania podpisu tokenu.</span><span class="sxs-lookup"><span data-stu-id="34d8d-200">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="34d8d-201">Oprogramowanie pośredniczące również potwierdza, że parametr iss w tokenie pasuje do tego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="34d8d-201">The middleware also confirms that the iss parameter in the token matches this URI.</span></span>

-   <span data-ttu-id="34d8d-202">AutomaticAuthenticate jest wartością logiczną, wskazującą, czy użytkownikowi określone przez token powinna istnieć możliwość automatycznej rejestracji.</span><span class="sxs-lookup"><span data-stu-id="34d8d-202">AutomaticAuthenticate is a Boolean value that indicates whether the user defined by the token should be automatically signed in.</span></span>

<span data-ttu-id="34d8d-203">Inny parametr, RequireHttpsMetadata, nie jest używany w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="34d8d-203">Another parameter, RequireHttpsMetadata, is not used in this example.</span></span> <span data-ttu-id="34d8d-204">Jest to przydatne podczas testowania; Ten parametr zostanie ustawiony na wartość false, aby mógł testować w środowiskach, w których nie masz certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="34d8d-204">It is useful for testing purposes; you set this parameter to false so that you can test in environments where you do not have certificates.</span></span> <span data-ttu-id="34d8d-205">W przypadku rzeczywistych wdrożeń tokenów elementu nośnego JWT zawsze zostanie przekazana tylko przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="34d8d-205">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="34d8d-206">Z tego oprogramowania pośredniczącego w miejscu tokenów JWT, są automatycznie wyodrębniane z nagłówków autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="34d8d-206">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="34d8d-207">Są następnie wykonać deserializacji zweryfikowane (przy użyciu wartości parametrów odbiorców i Urząd) i przechowywane jako informacje o użytkowniku późniejsze przywoływanie przez akcje MVC lub filtry autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="34d8d-207">They are then deserialized, validated (using the values in the Audience and Authority parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="34d8d-208">Oprogramowanie pośredniczące uwierzytelniania elementu nośnego JWT może również obsługiwać bardziej zaawansowane scenariusze, takie jak przy użyciu lokalnego certyfikatu do sprawdzania poprawności tokenu, jeśli uprawnienia nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="34d8d-208">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="34d8d-209">W tym scenariuszu można określić obiekt TokenValidationParameters w obiekcie JwtBearerOptions.</span><span class="sxs-lookup"><span data-stu-id="34d8d-209">For this scenario, you can specify a TokenValidationParameters object in the JwtBearerOptions object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="34d8d-210">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="34d8d-210">Additional resources</span></span>

-   <span data-ttu-id="34d8d-211">**Współużytkowanie plików cookie między aplikacjami**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span><span class="sxs-lookup"><span data-stu-id="34d8d-211">**Sharing cookies between applications**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span></span>

-   <span data-ttu-id="34d8d-212">**Wprowadzenie do tożsamości**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="34d8d-212">**Introduction to Identity**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="34d8d-213">**Rick Anderson. Uwierzytelnianie dwuskładnikowe za pomocą wiadomości SMS**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span><span class="sxs-lookup"><span data-stu-id="34d8d-213">**Rick Anderson. Two-factor authentication with SMS**
[*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span></span>

-   <span data-ttu-id="34d8d-214">**Włączanie uwierzytelniania za pomocą usługi Facebook, Google i innych dostawców zewnętrznych**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span><span class="sxs-lookup"><span data-stu-id="34d8d-214">**Enabling authentication using Facebook, Google and other external providers**
[*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span></span>

-   <span data-ttu-id="34d8d-215">**Michell Anicas. Wprowadzenie do protokołu OAuth 2**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span><span class="sxs-lookup"><span data-stu-id="34d8d-215">**Michell Anicas. An Introduction to OAuth 2**
[*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span></span>

-   <span data-ttu-id="34d8d-216">**AspNet.Security.OAuth.Providers** (repozytorium GitHub dla dostawców uwierzytelniania OAuth ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="34d8d-216">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers.</span></span>
    [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   <span data-ttu-id="34d8d-217">**Danny Strockis. Integrowanie usługi Azure AD dla aplikacji sieci web ASP.NET Core**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span><span class="sxs-lookup"><span data-stu-id="34d8d-217">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app**
[*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span></span>

-   <span data-ttu-id="34d8d-218">**Pomocą usługi IdentityServer4. Oficjalna dokumentacja**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span><span class="sxs-lookup"><span data-stu-id="34d8d-218">**IdentityServer4. Official documentation**
[*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="34d8d-219">[Poprzednie](../implement-resilient-applications/monitor-app-health.md)
>[dalej](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="34d8d-219">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>