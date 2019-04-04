---
title: Zabezpieczanie Mikrousług .NET i aplikacji sieci Web
description: Zabezpieczenia w Mikrousługach .NET i aplikacji sieci Web - Get w celu wiedzieć opcji uwierzytelniania w aplikacji sieci web platformy ASP.NET Core.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 3e2598f58bf2fb34a7ad7c107066d34e0e7c3408
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464817"
---
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="813a2-103">Bezpieczne Mikrousług .NET i aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="813a2-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="813a2-104">Istnieje wiele aspektów dotyczących zabezpieczeń w mikrousług i aplikacji sieci web czy temat proste może potrwać kilka książki podobny do poniższego, więc w tej sekcji skupimy się na uwierzytelniania, autoryzacji i wpisów tajnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="813a2-104">There are so many aspects about security in microservices and web applications that the topic could easy take several books like this one so, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="813a2-105">Implementowanie uwierzytelniania w aplikacjach sieci web i mikrousługi platformy .NET</span><span class="sxs-lookup"><span data-stu-id="813a2-105">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="813a2-106">Często jest to niezbędne do zasobów i interfejsów API opublikowana przez usługę ograniczone do niektórych Zaufani użytkownicy lub klienci.</span><span class="sxs-lookup"><span data-stu-id="813a2-106">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="813a2-107">Pierwszym krokiem do wprowadzania tego rodzaju decyzji dotyczących zaufania poziom interfejsu API to uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="813a2-107">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="813a2-108">Uwierzytelnianie to proces niezawodnie zweryfikowanie tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="813a2-108">Authentication is the process of reliably verify a user’s identity.</span></span>

<span data-ttu-id="813a2-109">W scenariuszach mikrousług uwierzytelniania jest zazwyczaj obsługiwana centralnie.</span><span class="sxs-lookup"><span data-stu-id="813a2-109">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="813a2-110">Jeśli używasz bramy interfejsu API, bramy jest dobrym miejscem do uwierzytelniania, jak pokazano w rysunek 9-1.</span><span class="sxs-lookup"><span data-stu-id="813a2-110">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="813a2-111">Jeśli używasz tego podejścia, upewnij się, że poszczególne mikrousługi nie można połączyć bezpośrednio (bez bramy interfejsu API), chyba że zapewnienia dodatkowych zabezpieczeń w celu uwierzytelniania wiadomości tego, czy pochodzą one od bramą lub nie.</span><span class="sxs-lookup"><span data-stu-id="813a2-111">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![Gdy brama interfejsu API umożliwia scentralizowanie uwierzytelniania, dodaje informacje o użytkowniku podczas przesyłania żądania do mikrousług.](./media/image1.png)

<span data-ttu-id="813a2-113">**Rysunek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="813a2-113">**Figure 9-1**.</span></span> <span data-ttu-id="813a2-114">Scentralizowane uwierzytelnianie przy użyciu bramy interfejsu API</span><span class="sxs-lookup"><span data-stu-id="813a2-114">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="813a2-115">Jeśli usługi są dostępne bezpośrednio, usługi uwierzytelniania, takich jak Azure Active Directory lub mikrousług dedykowanych uwierzytelniania, pełniący funkcję zabezpieczeń, usługa tokenów (STS) może być używane do uwierzytelniania użytkowników.</span><span class="sxs-lookup"><span data-stu-id="813a2-115">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="813a2-116">Usługi za pomocą tokenów zabezpieczających lub pliki cookie są współużytkowane decyzji dotyczących zaufania.</span><span class="sxs-lookup"><span data-stu-id="813a2-116">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="813a2-117">(Tokeny te mogą być współużytkowane między aplikacje platformy ASP.NET Core, jeśli to konieczne, implementując [udostępnianie plików cookie](/aspnet/core/security/cookie-sharing).) Ten wzorzec zilustrowano w rysunek 9-2.</span><span class="sxs-lookup"><span data-stu-id="813a2-117">(These tokens can be shared between ASP.NET Core applications, if needed, by implementing [cookie sharing](/aspnet/core/security/cookie-sharing).) This pattern is illustrated in Figure 9-2.</span></span>

![Gdy mikrousług są dostępne bezpośrednio, zaufanie, która obejmuje uwierzytelnianie i autoryzacja, jest obsługiwane przez tokenu zabezpieczającego wydane przez dedykowany mikrousług, współużytkowana mikrousług.](./media/image2.png)

<span data-ttu-id="813a2-119">**Rysunek 9-2**.</span><span class="sxs-lookup"><span data-stu-id="813a2-119">**Figure 9-2**.</span></span> <span data-ttu-id="813a2-120">Uwierzytelnienia za pomocą tożsamości mikrousług; zaufanie jest udostępniany przy użyciu tokenu autoryzacji</span><span class="sxs-lookup"><span data-stu-id="813a2-120">Authentication by identity microservice; trust is shared using an authorization token</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="813a2-121">Uwierzytelnianie za pomocą tożsamości platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="813a2-121">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="813a2-122">Podstawowy mechanizm w programie ASP.NET Core do identyfikowania użytkowników w aplikacji jest [tożsamości platformy ASP.NET Core](/aspnet/core/security/authentication/identity) systemu członkostwa.</span><span class="sxs-lookup"><span data-stu-id="813a2-122">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="813a2-123">Tożsamości platformy ASP.NET Core przechowuje informacje o użytkowniku (w tym informacje logowania, ról i oświadczenia) w magazynie danych skonfigurowane przez dewelopera.</span><span class="sxs-lookup"><span data-stu-id="813a2-123">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="813a2-124">Zazwyczaj magazyn danych tożsamości platformy ASP.NET Core to Entity Framework sklepu udostępniane w `Microsoft.AspNetCore.Identity.EntityFrameworkCore` pakietu.</span><span class="sxs-lookup"><span data-stu-id="813a2-124">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="813a2-125">Jednak inne pakiety innych firm lub niestandardowych magazynów może służyć do przechowywania informacji o tożsamości w usłudze Azure Table Storage, bazy danych cosmos DB lub w innych lokalizacjach.</span><span class="sxs-lookup"><span data-stu-id="813a2-125">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

<span data-ttu-id="813a2-126">Następujący kod pochodzi z szablonu projektu aplikacji sieci Web programu ASP.NET Core przy użyciu uwierzytelniania konta użytkownika, wybrany.</span><span class="sxs-lookup"><span data-stu-id="813a2-126">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="813a2-127">Widoczny jest sposób konfigurowania tożsamości platformy ASP.NET Core przy użyciu EntityFramework.Core w metodzie Startup.ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="813a2-127">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="813a2-128">Po skonfigurowaniu tożsamości platformy ASP.NET Core można włączyć aplikacji wywołującej. UseIdentity w usłudze `Startup.Configure` metody.</span><span class="sxs-lookup"><span data-stu-id="813a2-128">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s `Startup.Configure` method.</span></span>

<span data-ttu-id="813a2-129">Za pomocą tożsamości platformy ASP.NET Core umożliwia kilka scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="813a2-129">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="813a2-130">Utwórz nowe informacje o użytkowniku przy użyciu Menedżera UserManager typu (userManager.CreateAsync).</span><span class="sxs-lookup"><span data-stu-id="813a2-130">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="813a2-131">Uwierzytelnianie użytkowników przy użyciu typu SignInManager.</span><span class="sxs-lookup"><span data-stu-id="813a2-131">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="813a2-132">Możesz użyć `signInManager.SignInAsync` się bezpośrednio lub `signInManager.PasswordSignInAsync` do Potwierdź hasło użytkownika są prawidłowe, a następnie zarejestruj się.</span><span class="sxs-lookup"><span data-stu-id="813a2-132">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user’s password is correct and then sign them in.</span></span>

- <span data-ttu-id="813a2-133">Tak, że kolejne żądania z poziomu przeglądarki będzie zawierać tożsamości zalogowanego użytkownika oraz oświadczeń, należy zidentyfikować użytkownika, na podstawie informacji przechowywanych w pliku cookie (który jest odczytywany przez oprogramowanie pośredniczące tożsamości platformy ASP.NET Core).</span><span class="sxs-lookup"><span data-stu-id="813a2-133">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="813a2-134">Tożsamości platformy ASP.NET Core obsługuje również [uwierzytelniania dwuskładnikowego](/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="813a2-134">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="813a2-135">Scenariusze uwierzytelniania, które korzystanie z magazynu danych użytkowników lokalnych i utrzymują się tożsamości między żądaniami, przy użyciu plików cookie (co jest typowe dla aplikacji sieci web MVC), platformy ASP.NET Core Identity jest zalecanym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="813a2-135">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="813a2-136">Uwierzytelnianie za pomocą dostawców zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="813a2-136">Authenticate with external providers</span></span>

<span data-ttu-id="813a2-137">ASP.NET Core obsługuje również przy użyciu [dostawcy uwierzytelniania zewnętrznego](/aspnet/core/security/authentication/social/) Aby zezwolić użytkownikom na logowanie za pomocą [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) przepływów.</span><span class="sxs-lookup"><span data-stu-id="813a2-137">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="813a2-138">Oznacza to, że użytkownicy mogą logować się za pomocą istniejących procesów uwierzytelniania od dostawców, takich jak Microsoft, Google, Facebook lub Twitter i skojarzenia tych tożsamości przy użyciu tożsamości platformy ASP.NET Core w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="813a2-138">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="813a2-139">Aby użyć uwierzytelniania zewnętrznego, możesz uwzględnić odpowiednie oprogramowanie pośredniczące uwierzytelniania w żądaniu HTTP aplikacji, przetwarzania potoku.</span><span class="sxs-lookup"><span data-stu-id="813a2-139">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="813a2-140">To oprogramowanie pośredniczące jest odpowiedzialny za obsługę żądań do zwracania identyfikatora URI trasy z dostawcy uwierzytelniania: Przechwytywanie informacji o tożsamości i udostępniając je za pomocą metody SignInManager.GetExternalLoginInfo.</span><span class="sxs-lookup"><span data-stu-id="813a2-140">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="813a2-141">W poniższej tabeli przedstawiono popularne zewnętrznych dostawców tożsamości i ich skojarzone pakiety NuGet:</span><span class="sxs-lookup"><span data-stu-id="813a2-141">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="813a2-142">**Dostawca**</span><span class="sxs-lookup"><span data-stu-id="813a2-142">**Provider**</span></span>  | <span data-ttu-id="813a2-143">**Pakiet**</span><span class="sxs-lookup"><span data-stu-id="813a2-143">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="813a2-144">**Microsoft**</span><span class="sxs-lookup"><span data-stu-id="813a2-144">**Microsoft**</span></span> | <span data-ttu-id="813a2-145">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="813a2-145">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="813a2-146">**Google**</span><span class="sxs-lookup"><span data-stu-id="813a2-146">**Google**</span></span>    | <span data-ttu-id="813a2-147">**Microsoft.AspNetCore.Authentication.Google**</span><span class="sxs-lookup"><span data-stu-id="813a2-147">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="813a2-148">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="813a2-148">**Facebook**</span></span>  | <span data-ttu-id="813a2-149">**Microsoft.AspNetCore.Authentication.Facebook**</span><span class="sxs-lookup"><span data-stu-id="813a2-149">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="813a2-150">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="813a2-150">**Twitter**</span></span>   | <span data-ttu-id="813a2-151">**Microsoft.AspNetCore.Authentication.Twitter**</span><span class="sxs-lookup"><span data-stu-id="813a2-151">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="813a2-152">We wszystkich przypadkach, oprogramowanie pośredniczące jest zarejestrowana przy użyciu wywołania do metody rejestracji, podobnie jak `app.Use{ExternalProvider}Authentication` w `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="813a2-152">In all cases, the middleware is registered with a call to a registration method similar to `app.Use{ExternalProvider}Authentication` in `Startup.Configure`.</span></span> <span data-ttu-id="813a2-153">Te metody rejestracji przyjmują opcje obiekt, który zawiera identyfikator aplikacji i danych dotyczących tajnych informacji (hasła, na przykład), zgodnie z potrzebami przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="813a2-153">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="813a2-154">Zewnętrzni dostawcy uwierzytelniania wymagać od aplikacji zarejestrowania (jak wyjaśniono w [dokumentacji platformy ASP.NET Core](/aspnet/core/security/authentication/social/)) tak, aby ich mogą informować użytkownika żąda dostępu do tożsamości aplikacji.</span><span class="sxs-lookup"><span data-stu-id="813a2-154">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="813a2-155">Po zarejestrowaniu oprogramowanie pośredniczące w `Startup.Configure`, możesz też monitować użytkowników, aby zalogować się z dowolnej akcji kontrolera.</span><span class="sxs-lookup"><span data-stu-id="813a2-155">Once the middleware is registered in `Startup.Configure`, you can prompt users to sign in from any controller action.</span></span> <span data-ttu-id="813a2-156">Aby to zrobić, należy utworzyć `AuthenticationProperties` obiekt, który zawiera nazwę dostawcy uwierzytelniania i adres URL przekierowania.</span><span class="sxs-lookup"><span data-stu-id="813a2-156">To do this, you create an `AuthenticationProperties` object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="813a2-157">Następnie zwraca odpowiedź na żądanie przekazuje `AuthenticationProperties` obiektu.</span><span class="sxs-lookup"><span data-stu-id="813a2-157">You then return a Challenge response that passes the `AuthenticationProperties` object.</span></span> <span data-ttu-id="813a2-158">Poniższy kod przedstawia przykład.</span><span class="sxs-lookup"><span data-stu-id="813a2-158">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="813a2-159">Ten parametr redirectUrl zawiera adres URL zewnętrznego dostawcy powinna kierować do po użytkownik został uwierzytelniony.</span><span class="sxs-lookup"><span data-stu-id="813a2-159">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="813a2-160">Adres URL powinien reprezentować akcję, która będzie zalogować użytkownika na podstawie informacji z tożsamości zewnętrznej, jak w poniższym przykładzie uproszczona:</span><span class="sxs-lookup"><span data-stu-id="813a2-160">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

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

<span data-ttu-id="813a2-161">Jeśli wybierzesz **pojedyncze konto użytkownika** opcję uwierzytelniania podczas tworzenia projektu aplikacji sieci web platformy ASP.NET kodu w programie Visual Studio, należy zalogować się przy użyciu zewnętrznego dostawcy kodu znajduje się już w projekcie, jak pokazano w rysunek 9-3.</span><span class="sxs-lookup"><span data-stu-id="813a2-161">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 9-3.</span></span>

![Okno dialogowe Nowy ASP.NET Core aplikacji sieci Web, wyróżnianie przycisk, aby zmienić uwierzytelniania.](./media/image3.png)

<span data-ttu-id="813a2-163">**Rysunek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="813a2-163">**Figure 9-3**.</span></span> <span data-ttu-id="813a2-164">Wybranie opcji korzystania z funkcji uwierzytelniania zewnętrznego, podczas tworzenia projektu aplikacji sieci web</span><span class="sxs-lookup"><span data-stu-id="813a2-164">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="813a2-165">Oprócz uwierzytelniania zewnętrznego dostawcy wymienionych wcześniej pakietów innych firm są dostępne, zapewniających przy użyciu wielu bardziej zewnętrznych dostawców uwierzytelniania oprogramowania pośredniczącego.</span><span class="sxs-lookup"><span data-stu-id="813a2-165">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="813a2-166">Aby uzyskać listę, zobacz [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repozytorium w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="813a2-166">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="813a2-167">Można również utworzyć własne zewnętrzne oprogramowanie pośredniczące uwierzytelniania rozwiązać pewne specjalne potrzeby.</span><span class="sxs-lookup"><span data-stu-id="813a2-167">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="813a2-168">Uwierzytelnianie za pomocą tokenów elementu nośnego</span><span class="sxs-lookup"><span data-stu-id="813a2-168">Authenticate with bearer tokens</span></span>

<span data-ttu-id="813a2-169">Uwierzytelnianie za pomocą tożsamości platformy ASP.NET Core (lub tożsamości oraz dostawców uwierzytelniania zewnętrznych) działa dobrze w przypadku wielu scenariuszy aplikacji sieci web, w których jest zapisywanie informacji o użytkowniku w pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="813a2-169">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="813a2-170">W innych przypadkach jednak pliki cookie nie są naturalnych środków, przechowywanie i przesyłanie danych.</span><span class="sxs-lookup"><span data-stu-id="813a2-170">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="813a2-171">Na przykład w interfejsie API sieci Web platformy ASP.NET Core punktów końcowych RESTful, które mogą być używane przez aplikacje jednostronicowe (źródła), która udostępnia przez klientów natywnych, lub nawet przez inne interfejsy API sieci Web, zazwyczaj chcesz użyć uwierzytelniania tokenu elementu nośnego.</span><span class="sxs-lookup"><span data-stu-id="813a2-171">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="813a2-172">Aplikacje tego typu nie współpracują z plików cookie, ale można łatwo pobierania tokenu elementu nośnego i uwzględniania go w nagłówku autoryzacji kolejnych żądań.</span><span class="sxs-lookup"><span data-stu-id="813a2-172">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="813a2-173">Aby włączyć uwierzytelnianie przy użyciu tokenów, ASP.NET Core obsługuje kilka opcji za pomocą [OAuth 2.0](https://oauth.net/2/) i [OpenID Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="813a2-173">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="813a2-174">Uwierzytelnianie przy użyciu dostawcy OpenID Connect i OAuth 2.0 tożsamości</span><span class="sxs-lookup"><span data-stu-id="813a2-174">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="813a2-175">Jeśli informacje o użytkowniku są przechowywane w usłudze Azure Active Directory lub innego rozwiązania tożsamości, które obsługuje OpenID Connect i OAuth 2.0, możesz użyć **Microsoft.AspNetCore.Authentication.OpenIdConnect** pakietu do uwierzytelniania za pomocą Przepływ protokołu OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="813a2-175">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="813a2-176">Na przykład, aby uwierzytelniać się na mikrousługach Identity.Api w ramach aplikacji eShopOnContainers, aplikację sieci web platformy ASP.NET Core użyć oprogramowania pośredniczącego z tego pakietu jak pokazano w poniższym przykładzie uproszczona w `Startup.cs`:</span><span class="sxs-lookup"><span data-stu-id="813a2-176">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

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

<span data-ttu-id="813a2-177">Należy pamiętać, korzystając z tego przepływu pracy, oprogramowanie pośredniczące tożsamości platformy ASP.NET Core nie jest potrzebna, ponieważ wszystkie przechowywania informacji użytkownika i uwierzytelnianie jest obsługiwane przez usługę tożsamości.</span><span class="sxs-lookup"><span data-stu-id="813a2-177">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="813a2-178">Wystawiać tokeny zabezpieczające od usługi platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="813a2-178">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="813a2-179">Jeśli chcesz wystawiać tokeny zabezpieczające dla użytkowników lokalnych tożsamości platformy ASP.NET Core, a nie przy użyciu zewnętrznego dostawcy tożsamości, możesz korzystać z zalet pewne dobre bibliotek innych firm.</span><span class="sxs-lookup"><span data-stu-id="813a2-179">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="813a2-180">[Pomocą usługi IdentityServer4](https://github.com/IdentityServer/IdentityServer4) i [OpenIddict](https://github.com/openiddict/openiddict-core) dostawców uwierzytelniania OpenID Connect, które łatwo zintegrować z tożsamości platformy ASP.NET Core, aby umożliwić wydawania tokenów zabezpieczających usługi sieci Web platformy ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="813a2-180">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="813a2-181">[Dokumentacji pomocą usługi IdentityServer4](https://identityserver4.readthedocs.io/en/latest/) zawiera szczegółowe instrukcje dotyczące korzystania z biblioteki.</span><span class="sxs-lookup"><span data-stu-id="813a2-181">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="813a2-182">Jednak podstawowe kroki, które korzystają z pomocą usługi IdentityServer4 do wydawania tokenów są w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="813a2-182">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="813a2-183">Możesz wywołać aplikacji. UseIdentityServer w metodzie Startup.Configure dodać pomocą usługi IdentityServer4 do potoku przetwarzania żądań HTTP w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="813a2-183">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="813a2-184">Dzięki temu biblioteki, obsługiwać żądań uwierzytelniania OpenID Connect i punktów końcowych protokołu OAuth2, takich jak /connect/token.</span><span class="sxs-lookup"><span data-stu-id="813a2-184">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="813a2-185">Możesz skonfigurować pomocą usługi IdentityServer4 w Startup.ConfigureServices przez wywołania do usług. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="813a2-185">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="813a2-186">Możesz skonfigurować serwer tożsamości, ustawiając następujące dane:</span><span class="sxs-lookup"><span data-stu-id="813a2-186">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="813a2-187">[Poświadczenia](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) do użycia podczas podpisywania.</span><span class="sxs-lookup"><span data-stu-id="813a2-187">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="813a2-188">[Tożsamość i interfejs API zasobów](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) czy użytkownicy mogą żądać dostępu do:</span><span class="sxs-lookup"><span data-stu-id="813a2-188">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="813a2-189">Zasoby interfejsu API reprezentuje chronionych danych lub funkcji, których użytkownik może uzyskać dostęp przy użyciu tokenu dostępu.</span><span class="sxs-lookup"><span data-stu-id="813a2-189">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="813a2-190">Przykładem zasobu interfejsu API może być, interfejs API sieci web (lub zestaw interfejsów API), wymaga autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="813a2-190">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="813a2-191">Zasoby tożsamości reprezentują informacje (oświadczeń), które podano na kliencie do identyfikacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="813a2-191">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="813a2-192">Oświadczenia mogą obejmować nazwę użytkownika, adres e-mail i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="813a2-192">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="813a2-193">[Klientów](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) będą łączyć, aby żądać tokenów.</span><span class="sxs-lookup"><span data-stu-id="813a2-193">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="813a2-194">Mechanizm magazynu, aby uzyskać informacje o użytkowniku, takie jak [tożsamości platformy ASP.NET Core](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) lub alternatywnej.</span><span class="sxs-lookup"><span data-stu-id="813a2-194">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="813a2-195">Po określeniu, klientów i zasoby dotyczące pomocą usługi IdentityServer4 do użycia, możesz przekazać <xref:System.Collections.Generic.IEnumerable%601> kolekcji odpowiedniego typu do metod, które przyjmują magazynów klienta lub zasobu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="813a2-195">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="813a2-196">Lub w przypadku bardziej złożonych scenariuszy, można dostarczyć klienta lub zasobów dostawcy typów za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="813a2-196">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="813a2-197">Przykładowa konfiguracja pomocą usługi IdentityServer4 do użycia zasobów w pamięci i klientów, dostarczone przez typ niestandardowy IClientStore może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="813a2-197">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a><span data-ttu-id="813a2-198">Używanie tokenów zabezpieczających</span><span class="sxs-lookup"><span data-stu-id="813a2-198">Consume security tokens</span></span>

<span data-ttu-id="813a2-199">Uwierzytelniania w odniesieniu do punktu końcowego protokołu OpenID Connect lub wystawianie tokenów zabezpieczeń obejmuje kilka scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="813a2-199">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="813a2-200">Ale co to usługa, która po prostu wymaga, aby ograniczyć dostęp do tych użytkowników, którzy mają prawidłowy zabezpieczeń tokenów, które zostały dostarczone przez inną usługę?</span><span class="sxs-lookup"><span data-stu-id="813a2-200">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="813a2-201">W tym scenariuszu, oprogramowanie pośredniczące uwierzytelniania, która obsługuje tokeny JWT jest dostępna w **Microsoft.AspNetCore.Authentication.JwtBearer** pakietu.</span><span class="sxs-lookup"><span data-stu-id="813a2-201">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="813a2-202">Token JWT oznacza "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" i jest wspólny format tokenu zabezpieczeń (zdefiniowanej przez RFC 7519) do komunikacji oświadczeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="813a2-202">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="813a2-203">Uproszczony przykład sposobu użycia oprogramowania pośredniczącego do korzystają z tych tokenów może wyglądać jak ten fragment kodu, pobranego z mikrousług Ordering.Api z w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="813a2-203">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

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

<span data-ttu-id="813a2-204">Parametry to wykorzystania są następujące:</span><span class="sxs-lookup"><span data-stu-id="813a2-204">The parameters in this usage are:</span></span>

- <span data-ttu-id="813a2-205">`Audience` reprezentuje odbiorcy przychodzącego tokenu lub tokenów przyznaje dostęp do zasobu.</span><span class="sxs-lookup"><span data-stu-id="813a2-205">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="813a2-206">Jeśli wartości określonej w tym parametrze nie jest zgodny z parametrem w tokenie, token zostanie odrzucone.</span><span class="sxs-lookup"><span data-stu-id="813a2-206">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="813a2-207">`Authority` jest adresem serwera wystawiania tokenu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="813a2-207">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="813a2-208">Oprogramowanie pośredniczące uwierzytelniania elementu nośnego JWT używa tego identyfikatora URI, aby uzyskać klucz publiczny, który może służyć do weryfikowania podpisu tokenu.</span><span class="sxs-lookup"><span data-stu-id="813a2-208">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="813a2-209">Oprogramowanie pośredniczące również potwierdza, że `iss` parametru w tokenie pasuje do tego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="813a2-209">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="813a2-210">Inny parametr `RequireHttpsMetadata`, jest przydatne podczas testowania; ten parametr zostanie ustawiony na wartość false aby możliwe było przetestowanie w środowiskach, w której nie masz certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="813a2-210">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="813a2-211">W przypadku rzeczywistych wdrożeń tokenów elementu nośnego JWT zawsze zostanie przekazana tylko przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="813a2-211">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="813a2-212">Z tego oprogramowania pośredniczącego w miejscu tokenów JWT, są automatycznie wyodrębniane z nagłówków autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="813a2-212">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="813a2-213">Są one następnie deserializacji, zatwierdzone (przy użyciu wartości w `Audience` i `Authority` parametrów) i przechowywane jako informacje o użytkowniku późniejsze przywoływanie przez akcje MVC lub filtry autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="813a2-213">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="813a2-214">Oprogramowanie pośredniczące uwierzytelniania elementu nośnego JWT może również obsługiwać bardziej zaawansowane scenariusze, takie jak przy użyciu lokalnego certyfikatu do sprawdzania poprawności tokenu, jeśli uprawnienia nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="813a2-214">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="813a2-215">W tym scenariuszu można określić `TokenValidationParameters` obiektu `JwtBearerOptions` obiektu.</span><span class="sxs-lookup"><span data-stu-id="813a2-215">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="813a2-216">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="813a2-216">Additional resources</span></span>

- <span data-ttu-id="813a2-217">**Współużytkowanie plików cookie między aplikacjami** \\</span><span class="sxs-lookup"><span data-stu-id="813a2-217">**Sharing cookies between applications** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- <span data-ttu-id="813a2-218">**Wprowadzenie do tożsamości** \\</span><span class="sxs-lookup"><span data-stu-id="813a2-218">**Introduction to Identity** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="813a2-219">**Rick Anderson. Uwierzytelnianie dwuskładnikowe za pomocą wiadomości SMS** \\</span><span class="sxs-lookup"><span data-stu-id="813a2-219">**Rick Anderson. Two-factor authentication with SMS** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="813a2-220">**Włączanie uwierzytelniania za pomocą usługi Facebook, Google i innych dostawców zewnętrznych** \\</span><span class="sxs-lookup"><span data-stu-id="813a2-220">**Enabling authentication using Facebook, Google and other external providers** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="813a2-221">**Michell Anicas. Wprowadzenie do protokołu OAuth 2** \\</span><span class="sxs-lookup"><span data-stu-id="813a2-221">**Michell Anicas. An Introduction to OAuth 2** \\</span></span>
  [https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

- <span data-ttu-id="813a2-222">**AspNet.Security.OAuth.Providers** (repozytorium GitHub dla dostawców uwierzytelniania OAuth ASP.NET) \\</span><span class="sxs-lookup"><span data-stu-id="813a2-222">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers) \\</span></span>
  [https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

- <span data-ttu-id="813a2-223">**Danny Strockis. Integrowanie usługi Azure AD dla aplikacji sieci web ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="813a2-223">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app** \\</span></span>
  [https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

- <span data-ttu-id="813a2-224">**IdentityServer4. Oficjalna dokumentacja** \\</span><span class="sxs-lookup"><span data-stu-id="813a2-224">**IdentityServer4. Official documentation** \\</span></span>
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
><span data-ttu-id="813a2-225">[Poprzednie](../implement-resilient-applications/monitor-app-health.md)
>[dalej](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="813a2-225">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
