---
title: Zabezpieczanie Mikrousług .NET i aplikacji sieci Web
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Zabezpieczanie Mikrousług .NET i aplikacji sieci Web
keywords: Docker, Microservices, ASP.NET, Container
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0ca69ada16fbb5a6757da96a7ea64d2113c15b6f
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="securing-net-microservices-and-web-applications"></a><span data-ttu-id="7d65a-104">Zabezpieczanie Mikrousług .NET i aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="7d65a-104">Securing .NET Microservices and Web Applications</span></span>

<span data-ttu-id="7d65a-105">Często jest to niezbędne do zasobów i interfejsach API udostępnianych przez usługę ograniczone do niektórych Zaufani użytkownicy lub klienci.</span><span class="sxs-lookup"><span data-stu-id="7d65a-105">It is often necessary for resources and APIs exposed by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="7d65a-106">Pierwszym krokiem do wprowadzania tego rodzaju decyzje zaufania poziom interfejsu API jest uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="7d65a-106">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="7d65a-107">Uwierzytelnianie to proces niezawodnie ustalenia tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7d65a-107">Authentication is the process of reliably ascertaining a user’s identity.</span></span>

<span data-ttu-id="7d65a-108">W scenariuszach mikrousługi uwierzytelniania zwykle odbywa się centralnie.</span><span class="sxs-lookup"><span data-stu-id="7d65a-108">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="7d65a-109">Jeśli korzystasz z bramy usługi interfejsu API, brama jest dobrym miejscem do uwierzytelniania, jak pokazano w rysunek 11-1.</span><span class="sxs-lookup"><span data-stu-id="7d65a-109">If you are using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 11-1.</span></span> <span data-ttu-id="7d65a-110">Jeśli użyjesz tej metody upewnij się, czy poszczególnych mikrousług nie można połączyć bezpośrednio (bez bram interfejsu API), chyba że dodatkowe zabezpieczenia w celu uwierzytelniania wiadomości czy pochodzą z bramy lub nie.</span><span class="sxs-lookup"><span data-stu-id="7d65a-110">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![](./media/image1.png)

<span data-ttu-id="7d65a-111">**Rysunek 11-1**.</span><span class="sxs-lookup"><span data-stu-id="7d65a-111">**Figure 11-1**.</span></span> <span data-ttu-id="7d65a-112">Scentralizowane uwierzytelnianie z bramą interfejsu API</span><span class="sxs-lookup"><span data-stu-id="7d65a-112">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="7d65a-113">Jeśli usługi są dostępne bezpośrednio, usługi uwierzytelniania, takich jak Azure Active Directory lub mikrousługi dedykowanych uwierzytelniania, działając jako zabezpieczeń usługi tokenów (STS) może być używane do uwierzytelniania użytkowników.</span><span class="sxs-lookup"><span data-stu-id="7d65a-113">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="7d65a-114">Decyzje zaufania są wspólne dla usług z tokenów zabezpieczających lub plików cookie.</span><span class="sxs-lookup"><span data-stu-id="7d65a-114">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="7d65a-115">(Może być udostępniane między aplikacjami, w razie potrzeby w ASP.NET Core z [usługi ochrony danych](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Ten wzorzec jest przedstawione na rysunku nr 11-2.</span><span class="sxs-lookup"><span data-stu-id="7d65a-115">(These can be shared between applications, if needed, in ASP.NET Core with [data protection services](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) This pattern is illustrated in Figure 11-2.</span></span>

![](./media/image2.png)

<span data-ttu-id="7d65a-116">**Rysunek 11-2**.</span><span class="sxs-lookup"><span data-stu-id="7d65a-116">**Figure 11-2**.</span></span> <span data-ttu-id="7d65a-117">Uwierzytelnianie przez mikrousługi tożsamości; zaufanie jest udostępniany przy użyciu tokenu autoryzacji</span><span class="sxs-lookup"><span data-stu-id="7d65a-117">Authentication by identity microservice; trust is shared using an authorization token</span></span>

## <a name="authenticating-using-aspnet-core-identity"></a><span data-ttu-id="7d65a-118">Uwierzytelnianie za pomocą ASP.NET Core Identity</span><span class="sxs-lookup"><span data-stu-id="7d65a-118">Authenticating using ASP.NET Core Identity</span></span>

<span data-ttu-id="7d65a-119">Podstawowy mechanizm platformy ASP.NET Core do identyfikacji użytkowników aplikacji jest [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) systemu członkostwa.</span><span class="sxs-lookup"><span data-stu-id="7d65a-119">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="7d65a-120">Tożsamość platformy ASP.NET Core przechowuje informacje o użytkowniku (w tym informacje logowania, ról i oświadczeń) w magazynie danych skonfigurowane przez dewelopera.</span><span class="sxs-lookup"><span data-stu-id="7d65a-120">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="7d65a-121">Zazwyczaj ASP.NET Core Identity magazynu danych jest magazyn programu Entity Framework, podany w pakiecie Microsoft.AspNetCore.Identity.EntityFrameworkCore.</span><span class="sxs-lookup"><span data-stu-id="7d65a-121">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the Microsoft.AspNetCore.Identity.EntityFrameworkCore package.</span></span> <span data-ttu-id="7d65a-122">Jednak niestandardowe magazyny inne pakiety innych firm mogą służyć lub do przechowywania informacji o tożsamości w magazynu tabel Azure, usługa DocumentDB lub w innych lokalizacjach.</span><span class="sxs-lookup"><span data-stu-id="7d65a-122">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, DocumentDB, or other locations.</span></span>

<span data-ttu-id="7d65a-123">Poniższy kod jest pobierana z szablonu projektu aplikacji sieci Web platformy ASP.NET Core z wybrane uwierzytelnienia konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7d65a-123">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="7d65a-124">Widoczny jest sposób konfigurowania ASP.NET Identity Core za pomocą EntityFramework.Core w metodzie Startup.ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="7d65a-124">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="7d65a-125">Po skonfigurowaniu ASP.NET Core Identity Włącz przez wywołanie aplikacji. UseIdentity w metodzie Startup.Configure usługi.</span><span class="sxs-lookup"><span data-stu-id="7d65a-125">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s Startup.Configure method.</span></span>

<span data-ttu-id="7d65a-126">Przy użyciu tożsamości kodu ASP.NET umożliwia kilka scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="7d65a-126">Using ASP.NET Code Identity enables several scenarios:</span></span>

-   <span data-ttu-id="7d65a-127">Utwórz nowe informacje o użytkowniku przy użyciu typu interfejs UserManager (userManager.CreateAsync).</span><span class="sxs-lookup"><span data-stu-id="7d65a-127">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

-   <span data-ttu-id="7d65a-128">Uwierzytelnianie użytkowników przy użyciu typu SignInManager.</span><span class="sxs-lookup"><span data-stu-id="7d65a-128">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="7d65a-129">SignInManager.SignInAsync można użyć do logowania się bezpośrednio lub signInManager.PasswordSignInAsync o potwierdzenie hasła jest prawidłowa, a następnie zaloguj je.</span><span class="sxs-lookup"><span data-stu-id="7d65a-129">You can use signInManager.SignInAsync to sign in directly, or signInManager.PasswordSignInAsync to confirm the user’s password is correct and then sign them in.</span></span>

-   <span data-ttu-id="7d65a-130">Identyfikacji użytkownika na podstawie informacji przechowywanych w pliku cookie (który jest odczytywany przez oprogramowanie pośredniczące ASP.NET Core Identity), tak aby kolejnych żądań wysyłanych z przeglądarką uwzględni tożsamość zalogowanego użytkownika i oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="7d65a-130">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="7d65a-131">ASP.NET Core Identity obsługuje również [uwierzytelniania dwuskładnikowego](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="7d65a-131">ASP.NET Core Identity also supports [two-factor authentication](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="7d65a-132">Scenariusze uwierzytelniania, należy użyć magazynu danych użytkowników lokalnych i który utrwalenia tożsamości między żądaniami używanie plików cookie (podobnie jak w typowej aplikacji sieci web MVC), ASP.NET Core Identity jest zalecanym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="7d65a-132">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

## <a name="authenticating-using-external-providers"></a><span data-ttu-id="7d65a-133">Uwierzytelnianie przy użyciu zewnętrznego dostawcy</span><span class="sxs-lookup"><span data-stu-id="7d65a-133">Authenticating using external providers</span></span>

<span data-ttu-id="7d65a-134">Platformy ASP.NET Core obsługuje również przy użyciu [zewnętrzni dostawcy uwierzytelniania](https://docs.microsoft.com/aspnet/core/security/authentication/social/) umożliwi użytkownikom zalogować się za pośrednictwem [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) przepływów.</span><span class="sxs-lookup"><span data-stu-id="7d65a-134">ASP.NET Core also supports using [external authentication providers](https://docs.microsoft.com/aspnet/core/security/authentication/social/) to let users log in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="7d65a-135">Oznacza to, że użytkownicy mogą Zaloguj się za pomocą istniejące procesy uwierzytelniania od dostawców, takich jak Microsoft, Google, Facebook lub Twitter i skojarzyć tych tożsamości przy użyciu tożsamości platformy ASP.NET Core w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d65a-135">This means that users can log in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="7d65a-136">Aby użyć uwierzytelniania zewnętrznego, możesz uwzględnić odpowiednie oprogramowanie pośredniczące uwierzytelniania w żądaniu HTTP aplikacji przetwarzania potoku.</span><span class="sxs-lookup"><span data-stu-id="7d65a-136">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="7d65a-137">To oprogramowanie pośredniczące jest odpowiedzialny za żądań obsługi zwrócić trasy identyfikatora URI z dostawcy uwierzytelniania: Przechwytywanie informacji o tożsamości i udostępniania przy użyciu metody SignInManager.GetExternalLoginInfo.</span><span class="sxs-lookup"><span data-stu-id="7d65a-137">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="7d65a-138">Poniżej przedstawiono popularne zewnętrzni dostawcy uwierzytelniania i ich skojarzonych pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="7d65a-138">Popular external authentication providers and their associated NuGet packages are shown below.</span></span>

<span data-ttu-id="7d65a-139">**Firmy Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span><span class="sxs-lookup"><span data-stu-id="7d65a-139">**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span></span>

<span data-ttu-id="7d65a-140">**Google:** Microsoft.AspNetCore.Authentication.Google</span><span class="sxs-lookup"><span data-stu-id="7d65a-140">**Google:** Microsoft.AspNetCore.Authentication.Google</span></span>

<span data-ttu-id="7d65a-141">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span><span class="sxs-lookup"><span data-stu-id="7d65a-141">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span></span>

<span data-ttu-id="7d65a-142">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span><span class="sxs-lookup"><span data-stu-id="7d65a-142">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span></span>

<span data-ttu-id="7d65a-143">We wszystkich przypadkach oprogramowanie pośredniczące jest zarejestrowany w wywołaniu metody rejestracji podobne do aplikacji. Uwierzytelnianie {ExternalProvider} Startup.Configure.</span><span class="sxs-lookup"><span data-stu-id="7d65a-143">In all cases, the middleware is registered with a call to a registration method similar to app.Use{ExternalProvider}Authentication in Startup.Configure.</span></span> <span data-ttu-id="7d65a-144">Te metody rejestracji przyjmują opcje obiekt, który zawiera identyfikator aplikacji i tajnych informacji (hasła, na przykład), w razie potrzeby przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="7d65a-144">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="7d65a-145">Zewnętrzni dostawcy uwierzytelniania wymagają aplikacji ma zostać zarejestrowany (zgodnie z objaśnieniem w [dokumentacji platformy ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/social/)), dzięki czemu można informują użytkownik żąda dostępu do tożsamości jakie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d65a-145">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="7d65a-146">Po zarejestrowaniu oprogramowanie pośredniczące w Startup.Configure możesz monitować użytkowników o logowania z dowolnej akcji kontrolera.</span><span class="sxs-lookup"><span data-stu-id="7d65a-146">Once the middleware is registered in Startup.Configure, you can prompt users to log in from any controller action.</span></span> <span data-ttu-id="7d65a-147">Aby to zrobić, należy utworzyć obiekt AuthenticationProperties, który zawiera nazwę dostawcy uwierzytelniania i adres URL przekierowania.</span><span class="sxs-lookup"><span data-stu-id="7d65a-147">To do this, you create an AuthenticationProperties object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="7d65a-148">Zostanie zwrócona odpowiedź na żądanie przekazuje obiekt AuthenticationProperties.</span><span class="sxs-lookup"><span data-stu-id="7d65a-148">You then return a Challenge response that passes the AuthenticationProperties object.</span></span> <span data-ttu-id="7d65a-149">Poniższy kod przedstawia przykład.</span><span class="sxs-lookup"><span data-stu-id="7d65a-149">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="7d65a-150">Parametr redirectUrl zawiera adres URL, który zewnętrznego dostawcy powinna kierować do po uwierzytelnieniu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7d65a-150">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="7d65a-151">Adres URL powinien reprezentuje akcję, która będzie zalogować użytkownika na podstawie informacji o tożsamości zewnętrznej, jak w poniższym przykładzie uproszczony:</span><span class="sxs-lookup"><span data-stu-id="7d65a-151">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

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

<span data-ttu-id="7d65a-152">Jeśli wybierzesz **indywidualne konto użytkownika** opcję uwierzytelniania podczas tworzenia projektu aplikacji sieci web ASP.NET kodu w programie Visual Studio, należy zalogować się przy użyciu zewnętrznego dostawcy kodu znajduje się już w projekcie, jak pokazano na rysunku 11-3.</span><span class="sxs-lookup"><span data-stu-id="7d65a-152">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 11-3.</span></span>

![https://msdnshared.blob.core.windows.net/media/2016/10/new-web-app.png](./media/image3.png)

<span data-ttu-id="7d65a-153">**Rysunek 11-3**.</span><span class="sxs-lookup"><span data-stu-id="7d65a-153">**Figure 11-3**.</span></span> <span data-ttu-id="7d65a-154">Wybranie opcji korzystania z funkcji uwierzytelniania zewnętrznego, podczas tworzenia projektu aplikacji sieci web</span><span class="sxs-lookup"><span data-stu-id="7d65a-154">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="7d65a-155">Oprócz uwierzytelniania zewnętrznego dostawcy wymienionymi wcześniej, pakiety innych firm są dostępne, zapewniających przy użyciu wielu bardziej zewnętrznych dostawców uwierzytelniania oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="7d65a-155">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="7d65a-156">Aby uzyskać listę, zobacz [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repozytorium w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="7d65a-156">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="7d65a-157">Istnieje również możliwość, aby utworzyć własne oprogramowanie pośredniczące uwierzytelniania zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="7d65a-157">It is also possible, of course, to create your own external authentication middleware.</span></span>

## <a name="authenticating-with-bearer-tokens"></a><span data-ttu-id="7d65a-158">Uwierzytelnianie za pomocą tokenów elementu nośnego</span><span class="sxs-lookup"><span data-stu-id="7d65a-158">Authenticating with bearer tokens</span></span>

<span data-ttu-id="7d65a-159">Uwierzytelniania w produkcie ASP.NET Identity Core (lub tożsamości i zewnętrzni dostawcy uwierzytelniania) działa dobrze w przypadku wielu scenariuszy aplikacji sieci web, w których jest przechowywania informacji o użytkowniku w pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="7d65a-159">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="7d65a-160">W innych sytuacjach, pliki cookie nie są fizyczną oznacza przechowywanie i przesyłania danych.</span><span class="sxs-lookup"><span data-stu-id="7d65a-160">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="7d65a-161">Na przykład w interfejsie API sieci Web platformy ASP.NET Core RESTful punktów końcowych, które mogą być używane przez aplikacje jednostronicowe (źródła), która udostępnia w klientach natywnych, lub nawet przez innych interfejsów API sieci Web, zazwyczaj chcesz zamiast tego użyj tokenu uwierzytelniania elementu nośnego.</span><span class="sxs-lookup"><span data-stu-id="7d65a-161">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="7d65a-162">Aplikacje tego typu nie pracować z plików cookie, ale można łatwo pobrania tokenu elementu nośnego i uwzględnić go w kolejnych żądań w nagłówku autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="7d65a-162">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="7d65a-163">Aby włączyć uwierzytelnianie tokenu, platformy ASP.NET Core obsługuje kilka opcji przy użyciu [OAuth 2.0](https://oauth.net/2/) i [OpenID Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="7d65a-163">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="7d65a-164">Uwierzytelnianie przy użyciu dostawcy OpenID Connect lub tożsamość OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="7d65a-164">Authenticating with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="7d65a-165">Jeśli informacje użytkownika są przechowywane w usłudze Azure Active Directory lub innego rozwiązania tożsamości, które obsługuje OpenID Connect i OAuth 2.0, pakietu Microsoft.AspNetCore.Authentication.OpenIdConnect możesz używać do uwierzytelniania za pomocą przepływu pracy OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="7d65a-165">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the Microsoft.AspNetCore.Authentication.OpenIdConnect package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="7d65a-166">Na przykład, aby [uwierzytelniania usługi Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), aplikacji sieci web platformy ASP.NET Core można użyć oprogramowania pośredniczącego z tego pakietu, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7d65a-166">For example, to [authenticate against Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), an ASP.NET Core web application can use middleware from that package as shown in the following example:</span></span>

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

<span data-ttu-id="7d65a-167">Wartości konfiguracji są wartości usługi Azure Active Directory, które są tworzone, gdy aplikacja jest [zarejestrowany jako klient usługi Azure AD](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad).</span><span class="sxs-lookup"><span data-stu-id="7d65a-167">The configuration values are Azure Active Directory values that are created when your application is [registered as an Azure AD client](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad).</span></span> <span data-ttu-id="7d65a-168">Identyfikator jednego klienta mogą być współużytkowane przez wiele mikrousług w aplikacji, jeśli wszystkie wymagane do uwierzytelniania użytkowników uwierzytelnionych za pośrednictwem usługi Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7d65a-168">A single client ID can be shared among multiple microservices in an application if they all need to authenticate users authenticated via Azure Active Directory.</span></span>

<span data-ttu-id="7d65a-169">Należy pamiętać, czy użycie tego przepływu pracy, oprogramowanie pośredniczące ASP.NET Core Identity nie jest potrzebna, ponieważ wszystkie magazynu informacje użytkownika i uwierzytelnianie jest obsługiwane przez usługę Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="7d65a-169">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by Azure Active Directory.</span></span>

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="7d65a-170">Wystawianie tokenów zabezpieczeń z usługą platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7d65a-170">Issuing security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="7d65a-171">Jeśli wolisz wystawiać tokeny zabezpieczające dla użytkowników lokalnych ASP.NET Core Identity, a nie przy użyciu dostawcy tożsamości zewnętrznych, możesz korzystać niektórych dobrej bibliotek innych firm.</span><span class="sxs-lookup"><span data-stu-id="7d65a-171">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="7d65a-172">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) i [OpenIddict](https://github.com/openiddict/openiddict-core) OpenID Connect dostawców, które łatwo zintegrować z ASP.NET Identity Core pozwala wydawania tokenów zabezpieczających z usługą platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7d65a-172">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="7d65a-173">[Dokumentacji IdentityServer4](https://identityserver4.readthedocs.io/en/release/) zawiera szczegółowe instrukcje dotyczące korzystania z biblioteki.</span><span class="sxs-lookup"><span data-stu-id="7d65a-173">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/release/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="7d65a-174">Jednak podstawowe kroki z użyciem IdentityServer4 do wydawania tokenów są następujące.</span><span class="sxs-lookup"><span data-stu-id="7d65a-174">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1.  <span data-ttu-id="7d65a-175">Aplikacja jest wywoływana. UseIdentityServer w metodzie Startup.Configure, aby dodać IdentityServer4 do potoku przetwarzania żądań HTTP w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7d65a-175">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="7d65a-176">Dzięki temu biblioteki obsługiwać żądań do punktów końcowych OAuth2, takich jak /connect/token i OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="7d65a-176">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2.  <span data-ttu-id="7d65a-177">Należy skonfigurować IdentityServer4 w Startup.ConfigureServices za wywołania do usług. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="7d65a-177">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3.  <span data-ttu-id="7d65a-178">Możesz skonfigurować serwer tożsamości podając następujące dane:</span><span class="sxs-lookup"><span data-stu-id="7d65a-178">You configure identity server by providing the following data:</span></span>

-   <span data-ttu-id="7d65a-179">[Poświadczenia](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) do użycia podczas podpisywania.</span><span class="sxs-lookup"><span data-stu-id="7d65a-179">The [credentials](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) to use for signing.</span></span>

-   <span data-ttu-id="7d65a-180">[Tożsamości i interfejs API zasobów](https://identityserver4.readthedocs.io/en/release/topics/resources.html) czy użytkownicy mogą żądać dostępu do:</span><span class="sxs-lookup"><span data-stu-id="7d65a-180">The [Identity and API resources](https://identityserver4.readthedocs.io/en/release/topics/resources.html) that users might request access to:</span></span>

<!-- -->

-   <span data-ttu-id="7d65a-181">Zasoby interfejsu API reprezentuje chronionych danych i działania, które użytkownik może korzystać z tokenem dostępu.</span><span class="sxs-lookup"><span data-stu-id="7d65a-181">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="7d65a-182">Przykładem zasobu interfejsu API może być interfejsu API sieci web (lub zestaw interfejsów API) która wymaga autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="7d65a-182">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

-   <span data-ttu-id="7d65a-183">Tożsamość zasobów reprezentuje informacje (oświadczeń), które podano na kliencie do identyfikacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7d65a-183">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="7d65a-184">Oświadczenia mogą obejmować nazwę użytkownika, adres e-mail i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="7d65a-184">The claims might include the user name, email address, and so on.</span></span>

<!-- -->

-   <span data-ttu-id="7d65a-185">[Klientów](https://identityserver4.readthedocs.io/en/release/topics/clients.html) które będą łączyć do żądania tokenów.</span><span class="sxs-lookup"><span data-stu-id="7d65a-185">The [clients](https://identityserver4.readthedocs.io/en/release/topics/clients.html) that will be connecting in order to request tokens.</span></span>

-   <span data-ttu-id="7d65a-186">Mechanizm przechowywania informacji o użytkownikach, takich jak [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) lub alternatywnej.</span><span class="sxs-lookup"><span data-stu-id="7d65a-186">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) or an alternative.</span></span>

<span data-ttu-id="7d65a-187">Po określeniu klientów oraz zasoby IdentityServer4 do używania, można przekazać elementu IEnumerable&lt;T&gt; kolekcji odpowiedniego typu do metod przyjmujących magazynów klienta lub zasobu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="7d65a-187">When you specify clients and resources for IdentityServer4 to use, you can pass an IEnumerable&lt;T&gt; collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="7d65a-188">Lub dla bardziej złożonymi scenariuszami, możesz podać klienta lub zasobu dostawcy typów za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="7d65a-188">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="7d65a-189">Przykładowa konfiguracja IdentityServer4 użycie zasobów w pamięci i udostępniane przez typ niestandardowy IClientStore klientów może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="7d65a-189">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a><span data-ttu-id="7d65a-190">Korzystanie z tokenów zabezpieczających</span><span class="sxs-lookup"><span data-stu-id="7d65a-190">Consuming security tokens</span></span>

<span data-ttu-id="7d65a-191">Uwierzytelniany punkt końcowy protokołu OpenID Connect lub wystawianie tokenów zabezpieczeń obejmuje kilka scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="7d65a-191">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="7d65a-192">Ale co usługa, która wystarczy do ograniczenia dostępu do tych użytkowników, którzy mają prawidłowy zabezpieczeń tokeny, które zostały dostarczone przez inną usługę?</span><span class="sxs-lookup"><span data-stu-id="7d65a-192">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="7d65a-193">Dla tego scenariusza oprogramowanie pośredniczące uwierzytelniania, która obsługuje tokeny JWT jest niedostępny w pakiecie Microsoft.AspNetCore.Authentication.JwtBearer.</span><span class="sxs-lookup"><span data-stu-id="7d65a-193">For that scenario, authentication middleware that handles JWT tokens is available in the Microsoft.AspNetCore.Authentication.JwtBearer package.</span></span> <span data-ttu-id="7d65a-194">Oznacza JWT "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" i jest typowe format tokenu zabezpieczeń (zdefiniowany w dokumencie RFC 7519) do komunikacji oświadczeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7d65a-194">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="7d65a-195">Prosty przykład sposobu użycia oprogramowania pośredniczącego użycie tych tokenów może wyglądać jak w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7d65a-195">A simple example of how to use middleware to consume such tokens might look like the following example.</span></span> <span data-ttu-id="7d65a-196">Ten kod musi poprzedzać wywołania z oprogramowaniem pośredniczącym platformy ASP.NET Core MVC (aplikacja. UseMvc).</span><span class="sxs-lookup"><span data-stu-id="7d65a-196">This code must precede calls to ASP.NET Core MVC middleware (app.UseMvc).</span></span>

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

<span data-ttu-id="7d65a-197">Dostępne są następujące parametry w ten sposób użycia:</span><span class="sxs-lookup"><span data-stu-id="7d65a-197">The parameters in this usage are:</span></span>

-   <span data-ttu-id="7d65a-198">Grupy odbiorców reprezentuje odbiornika przychodzącego tokenu lub tokenów udziela dostępu do zasobu.</span><span class="sxs-lookup"><span data-stu-id="7d65a-198">Audience represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="7d65a-199">Jeśli wartość określona w tym parametrze nie jest zgodny z parametrem lub w tokenie, token zostanie odrzucone.</span><span class="sxs-lookup"><span data-stu-id="7d65a-199">If the value specified in this parameter does not match the aud parameter in the token, the token will be rejected.</span></span>

-   <span data-ttu-id="7d65a-200">Urząd jest adres serwera wystawiania tokenu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="7d65a-200">Authority is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="7d65a-201">Oprogramowanie pośredniczące uwierzytelniania elementu nośnego JWT używa tego identyfikatora URI w celu uzyskania klucza publicznego, który może służyć do sprawdzania poprawności podpisu tokenu.</span><span class="sxs-lookup"><span data-stu-id="7d65a-201">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="7d65a-202">Oprogramowanie pośredniczące również potwierdza, czy parametr iss w tokenie zgodna tego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="7d65a-202">The middleware also confirms that the iss parameter in the token matches this URI.</span></span>

-   <span data-ttu-id="7d65a-203">AutomaticAuthenticate jest wartością logiczną, wskazującą, czy określone przez token powinny być automatycznie logowania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7d65a-203">AutomaticAuthenticate is a Boolean value that indicates whether the user defined by the token should be automatically signed in.</span></span>

<span data-ttu-id="7d65a-204">Inny parametr, RequireHttpsMetadata, nie jest używany w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7d65a-204">Another parameter, RequireHttpsMetadata, is not used in this example.</span></span> <span data-ttu-id="7d65a-205">Jest przydatne w przypadku testowania; Ten parametr jest ustawiony na wartość false tak, aby można było testować w środowiskach, w którym nie ma certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="7d65a-205">It is useful for testing purposes; you set this parameter to false so that you can test in environments where you do not have certificates.</span></span> <span data-ttu-id="7d65a-206">W przypadku rzeczywistych wdrożeń tokenów elementu nośnego JWT zawsze można przekazać tylko za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7d65a-206">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="7d65a-207">Z tego oprogramowania pośredniczącego w miejscu tokenów JWT automatycznie są wyodrębniane z nagłówki autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="7d65a-207">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="7d65a-208">One są następnie deserializowany, weryfikowane (przy użyciu wartości parametrów odbiorców i Urząd) i przechowywane jako informacje o użytkowniku przywoływanie później przez akcje MVC lub filtry autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="7d65a-208">They are then deserialized, validated (using the values in the Audience and Authority parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="7d65a-209">Oprogramowanie pośredniczące uwierzytelniania elementu nośnego JWT może również obsługiwać bardziej zaawansowanych scenariuszy, takich jak przy użyciu lokalnego certyfikatu do sprawdzania poprawności tokenu, jeśli jako źródło nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="7d65a-209">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="7d65a-210">W tym scenariuszu można określić obiektu TokenValidationParameters w obiekcie JwtBearerOptions.</span><span class="sxs-lookup"><span data-stu-id="7d65a-210">For this scenario, you can specify a TokenValidationParameters object in the JwtBearerOptions object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7d65a-211">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="7d65a-211">Additional resources</span></span>

-   <span data-ttu-id="7d65a-212">**Udostępnianie plików cookie między aplikacjami**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#udostępnianie — uwierzytelnianie — pliki cookie między — aplikacje*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span><span class="sxs-lookup"><span data-stu-id="7d65a-212">**Sharing cookies between applications**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span></span>

-   <span data-ttu-id="7d65a-213">**Wprowadzenie do tożsamości**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="7d65a-213">**Introduction to Identity**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="7d65a-214">**Rick Anderson. Uwierzytelnianie dwuskładnikowe z programem SMS**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span><span class="sxs-lookup"><span data-stu-id="7d65a-214">**Rick Anderson. Two-factor authentication with SMS**
[*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span></span>

-   <span data-ttu-id="7d65a-215">**Włączanie uwierzytelniania za pomocą usługi Facebook, Google i innych dostawców zewnętrznych**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span><span class="sxs-lookup"><span data-stu-id="7d65a-215">**Enabling authentication using Facebook, Google and other external providers**
[*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span></span>

-   <span data-ttu-id="7d65a-216">**Michell Anicas. Wprowadzenie do protokołu OAuth 2**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span><span class="sxs-lookup"><span data-stu-id="7d65a-216">**Michell Anicas. An Introduction to OAuth 2**
[*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span></span>

-   <span data-ttu-id="7d65a-217">**AspNet.Security.OAuth.Providers** (repozytorium GitHub dla dostawców uwierzytelniania OAuth ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7d65a-217">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers.</span></span>
    [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   <span data-ttu-id="7d65a-218">**Danny Strockis. Integrowanie usługi Azure AD aplikacji sieci web platformy ASP.NET Core**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span><span class="sxs-lookup"><span data-stu-id="7d65a-218">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app**
[*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span></span>

-   <span data-ttu-id="7d65a-219">**IdentityServer4. Oficjalnej dokumentacji**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span><span class="sxs-lookup"><span data-stu-id="7d65a-219">**IdentityServer4. Official documentation**
[*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7d65a-220">[Poprzednie] (.. /Implement-resilient-Applications/Monitor-App-Health.MD) [dalej] (autoryzacji net mikrousług web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="7d65a-220">[Previous] (../implement-resilient-applications/monitor-app-health.md) [Next] (authorization-net-microservices-web-applications.md)</span></span>
