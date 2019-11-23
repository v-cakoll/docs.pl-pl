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
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="9f49f-103">Tworzenie bezpiecznych mikrousług i aplikacji sieci Web platformy .NET</span><span class="sxs-lookup"><span data-stu-id="9f49f-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="9f49f-104">Istnieje wiele aspektów dotyczących zabezpieczeń w mikrousługach i aplikacjach sieci Web, które w tym temacie mogą ułatwić przejęcie kilku książek w taki sposób, aby w tej sekcji skoncentrować się na uwierzytelnianiu, autoryzacji i wpisach tajnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f49f-104">There are so many aspects about security in microservices and web applications that the topic could easy take several books like this one so, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="9f49f-105">Implementowanie uwierzytelniania w mikrousługach i aplikacjach sieci Web platformy .NET</span><span class="sxs-lookup"><span data-stu-id="9f49f-105">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="9f49f-106">Często konieczne jest, aby zasoby i interfejsy API opublikowane przez usługę były ograniczone do określonych zaufanych użytkowników lub klientów.</span><span class="sxs-lookup"><span data-stu-id="9f49f-106">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="9f49f-107">Pierwszym krokiem do sortowania decyzji zaufania na poziomie interfejsu API jest uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="9f49f-107">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="9f49f-108">Uwierzytelnianie to proces niezawodnego weryfikowania tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9f49f-108">Authentication is the process of reliably verify a user’s identity.</span></span>

<span data-ttu-id="9f49f-109">W scenariuszach mikrousług uwierzytelnianie jest zazwyczaj obsługiwane centralnie.</span><span class="sxs-lookup"><span data-stu-id="9f49f-109">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="9f49f-110">Jeśli używasz bramy interfejsu API, Brama jest dobrym miejscem do uwierzytelniania, jak pokazano na rysunku 9-1.</span><span class="sxs-lookup"><span data-stu-id="9f49f-110">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="9f49f-111">W przypadku korzystania z tej metody upewnij się, że poszczególne mikrousługi nie są dostępne bezpośrednio (bez bramy interfejsu API), o ile nie są stosowane dodatkowe zabezpieczenia umożliwiające uwierzytelnianie komunikatów niezależnie od tego, czy pochodzą one z bramy, czy nie.</span><span class="sxs-lookup"><span data-stu-id="9f49f-111">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![Diagram przedstawiający sposób interakcji aplikacji mobilnej klienta z zapleczem.](./media/index/api-gateway-centralized-authentication.png)

<span data-ttu-id="9f49f-113">**Rysunek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="9f49f-113">**Figure 9-1**.</span></span> <span data-ttu-id="9f49f-114">Scentralizowane uwierzytelnianie przy użyciu bramy interfejsu API</span><span class="sxs-lookup"><span data-stu-id="9f49f-114">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="9f49f-115">Gdy brama interfejsu API scentralizowana uwierzytelnianie, dodaje informacje o użytkowniku podczas przekazywania żądań do mikrousług.</span><span class="sxs-lookup"><span data-stu-id="9f49f-115">When the API Gateway centralizes authentication, it adds user information when forwarding requests to the microservices.</span></span> <span data-ttu-id="9f49f-116">W przypadku uzyskiwania dostępu do usług można korzystać z usługi uwierzytelniania, takiej jak Azure Active Directory lub dedykowanej mikrousługi uwierzytelniania działającej jako usługa tokenu zabezpieczającego (STS) do uwierzytelniania użytkowników.</span><span class="sxs-lookup"><span data-stu-id="9f49f-116">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="9f49f-117">Decyzje dotyczące zaufania są współużytkowane przez usługi z tokenami zabezpieczeń lub plikami cookie.</span><span class="sxs-lookup"><span data-stu-id="9f49f-117">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="9f49f-118">(Te tokeny mogą być współużytkowane przez aplikacje ASP.NET Core, w razie konieczności, przez zaimplementowanie [udostępniania plików cookie](/aspnet/core/security/cookie-sharing).) Ten wzorzec przedstawiono na rysunku 9-2.</span><span class="sxs-lookup"><span data-stu-id="9f49f-118">(These tokens can be shared between ASP.NET Core applications, if needed, by implementing [cookie sharing](/aspnet/core/security/cookie-sharing).) This pattern is illustrated in Figure 9-2.</span></span>

![Diagram przedstawiający uwierzytelnianie za poorednictwem mikrousług zaplecza.](./media/index/identity-microservice-authentication.png)

<span data-ttu-id="9f49f-120">**Rysunek 9-2**.</span><span class="sxs-lookup"><span data-stu-id="9f49f-120">**Figure 9-2**.</span></span> <span data-ttu-id="9f49f-121">Uwierzytelnianie według mikrousług tożsamości; zaufanie jest udostępniane przy użyciu tokenu autoryzacji</span><span class="sxs-lookup"><span data-stu-id="9f49f-121">Authentication by identity microservice; trust is shared using an authorization token</span></span>

<span data-ttu-id="9f49f-122">W przypadku bezpośredniego dostępu do mikrousług relacja zaufania, która obejmuje uwierzytelnianie i autoryzację, jest obsługiwana przez token zabezpieczający wystawiony przez dedykowaną mikrousługę, współdzieloną przez mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="9f49f-122">When microservices are accessed directly, trust, that includes authentication and authorization, is handled by a security token issued by a dedicated microservice, shared between microservices.</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="9f49f-123">Uwierzytelnianie za pomocą tożsamości ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9f49f-123">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="9f49f-124">Podstawowym mechanizmem w ASP.NET Core do identyfikowania użytkowników aplikacji jest system członkostwa [tożsamości ASP.NET Core](/aspnet/core/security/authentication/identity) .</span><span class="sxs-lookup"><span data-stu-id="9f49f-124">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="9f49f-125">ASP.NET Core Identity przechowuje informacje o użytkowniku (w tym informacje dotyczące logowania, role i oświadczenia) w magazynie danych skonfigurowanym przez dewelopera.</span><span class="sxs-lookup"><span data-stu-id="9f49f-125">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="9f49f-126">Zwykle magazyn danych tożsamości ASP.NET Core jest magazynem Entity Framework udostępnionym w pakiecie `Microsoft.AspNetCore.Identity.EntityFrameworkCore`.</span><span class="sxs-lookup"><span data-stu-id="9f49f-126">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="9f49f-127">Jednak magazyny niestandardowe lub inne pakiety innych firm mogą służyć do przechowywania informacji o tożsamościach w usłudze Azure Table Storage, CosmosDB lub innych lokalizacjach.</span><span class="sxs-lookup"><span data-stu-id="9f49f-127">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

<span data-ttu-id="9f49f-128">Poniższy kod jest pobierany z szablonu projektu aplikacji sieci Web ASP.NET Core z wybranym indywidualnym uwierzytelnianiem konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9f49f-128">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="9f49f-129">Przedstawiono w nim sposób konfigurowania tożsamości ASP.NET Core przy użyciu EntityFramework. Core w metodzie Startup. ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="9f49f-129">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="9f49f-130">Po skonfigurowaniu tożsamości ASP.NET Core można ją włączyć, wywołując aplikację. UseIdentity w metodzie `Startup.Configure` usługi.</span><span class="sxs-lookup"><span data-stu-id="9f49f-130">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s `Startup.Configure` method.</span></span>

<span data-ttu-id="9f49f-131">Korzystanie z ASP.NET Core Identity umożliwia wykonywanie kilku scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="9f49f-131">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="9f49f-132">Utwórz nowe informacje o użytkowniku przy użyciu typu Usermanager (usermanager. setasync).</span><span class="sxs-lookup"><span data-stu-id="9f49f-132">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="9f49f-133">Uwierzytelnianie użytkowników przy użyciu typu SignInManager.</span><span class="sxs-lookup"><span data-stu-id="9f49f-133">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="9f49f-134">Możesz użyć `signInManager.SignInAsync`, aby zalogować się bezpośrednio, lub `signInManager.PasswordSignInAsync` potwierdzić, że hasło użytkownika jest poprawne, a następnie podpisz.</span><span class="sxs-lookup"><span data-stu-id="9f49f-134">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user’s password is correct and then sign them in.</span></span>

- <span data-ttu-id="9f49f-135">Zidentyfikuj użytkownika na podstawie informacji przechowywanych w pliku cookie (który jest odczytywany przez oprogramowanie ASP.NET Core Identity), aby kolejne żądania z przeglądarki obejmowały tożsamość i oświadczenia zalogowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9f49f-135">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="9f49f-136">Tożsamość ASP.NET Core obsługuje również [uwierzytelnianie dwuskładnikowe](/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="9f49f-136">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="9f49f-137">W przypadku scenariuszy uwierzytelniania, które wykorzystują magazyn danych użytkownika lokalnego i utrzymują tożsamość między żądaniami przy użyciu plików cookie (jak zwykle w przypadku aplikacji sieci Web MVC), ASP.NET Core tożsamość jest zalecanym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="9f49f-137">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="9f49f-138">Uwierzytelnianie z dostawcami zewnętrznymi</span><span class="sxs-lookup"><span data-stu-id="9f49f-138">Authenticate with external providers</span></span>

<span data-ttu-id="9f49f-139">ASP.NET Core obsługuje również korzystanie z [zewnętrznych dostawców uwierzytelniania](/aspnet/core/security/authentication/social/) , aby umożliwić użytkownikom logowanie za pomocą przepływów [OAuth 2,0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) .</span><span class="sxs-lookup"><span data-stu-id="9f49f-139">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="9f49f-140">Oznacza to, że użytkownicy mogą logować się przy użyciu istniejących procesów uwierzytelniania od dostawców, takich jak Microsoft, Google, Facebook lub Twitter, i kojarzyć te tożsamości z tożsamością ASP.NET Core w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f49f-140">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="9f49f-141">Aby można było korzystać z uwierzytelniania zewnętrznego, należy uwzględnić odpowiednie oprogramowanie pośredniczące uwierzytelniania w potoku przetwarzania żądań HTTP aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f49f-141">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="9f49f-142">To oprogramowanie pośredniczące jest odpowiedzialne za obsługę żądań zwrócenia tras URI z dostawcy uwierzytelniania, Przechwytywanie informacji o tożsamości i udostępnianie ich za pośrednictwem metody SignInManager. GetExternalLoginInfo.</span><span class="sxs-lookup"><span data-stu-id="9f49f-142">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="9f49f-143">W poniższej tabeli przedstawiono popularne zewnętrzne dostawcy uwierzytelniania i powiązane z nimi pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="9f49f-143">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="9f49f-144">**Dostawca**</span><span class="sxs-lookup"><span data-stu-id="9f49f-144">**Provider**</span></span>  | <span data-ttu-id="9f49f-145">**Pakiet**</span><span class="sxs-lookup"><span data-stu-id="9f49f-145">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="9f49f-146">**Microsoft**</span><span class="sxs-lookup"><span data-stu-id="9f49f-146">**Microsoft**</span></span> | <span data-ttu-id="9f49f-147">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="9f49f-147">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="9f49f-148">**Google**</span><span class="sxs-lookup"><span data-stu-id="9f49f-148">**Google**</span></span>    | <span data-ttu-id="9f49f-149">**Microsoft.AspNetCore.Authentication.Google**</span><span class="sxs-lookup"><span data-stu-id="9f49f-149">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="9f49f-150">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="9f49f-150">**Facebook**</span></span>  | <span data-ttu-id="9f49f-151">**Microsoft.AspNetCore.Authentication.Facebook**</span><span class="sxs-lookup"><span data-stu-id="9f49f-151">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="9f49f-152">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="9f49f-152">**Twitter**</span></span>   | <span data-ttu-id="9f49f-153">**Microsoft.AspNetCore.Authentication.Twitter**</span><span class="sxs-lookup"><span data-stu-id="9f49f-153">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="9f49f-154">We wszystkich przypadkach oprogramowanie pośredniczące jest zarejestrowane z wywołaniem metody rejestracji podobnej do `app.Use{ExternalProvider}Authentication` w `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="9f49f-154">In all cases, the middleware is registered with a call to a registration method similar to `app.Use{ExternalProvider}Authentication` in `Startup.Configure`.</span></span> <span data-ttu-id="9f49f-155">Te metody rejestracji przyjmują obiekt Options, który zawiera identyfikator aplikacji i informacje o kluczu tajnym (na przykład hasło), zgodnie z wymaganiami dostawcy.</span><span class="sxs-lookup"><span data-stu-id="9f49f-155">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="9f49f-156">Zewnętrzni dostawcy uwierzytelniania wymagają rejestracji aplikacji (zgodnie z opisem w [dokumentacji ASP.NET Core](/aspnet/core/security/authentication/social/)), dzięki czemu mogą poinformować użytkownika, jakie aplikacje żąda dostępu do ich tożsamości.</span><span class="sxs-lookup"><span data-stu-id="9f49f-156">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="9f49f-157">Po zarejestrowaniu oprogramowania pośredniczącego w `Startup.Configure`możesz monitować użytkowników o zalogowanie się z dowolnego działania kontrolera.</span><span class="sxs-lookup"><span data-stu-id="9f49f-157">Once the middleware is registered in `Startup.Configure`, you can prompt users to sign in from any controller action.</span></span> <span data-ttu-id="9f49f-158">W tym celu należy utworzyć obiekt `AuthenticationProperties`, który zawiera nazwę dostawcy uwierzytelniania i adres URL przekierowania.</span><span class="sxs-lookup"><span data-stu-id="9f49f-158">To do this, you create an `AuthenticationProperties` object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="9f49f-159">Następnie zwracasz odpowiedź wyzwania, która przekazuje obiekt `AuthenticationProperties`.</span><span class="sxs-lookup"><span data-stu-id="9f49f-159">You then return a Challenge response that passes the `AuthenticationProperties` object.</span></span> <span data-ttu-id="9f49f-160">Poniższy kod przedstawia przykład tego elementu.</span><span class="sxs-lookup"><span data-stu-id="9f49f-160">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="9f49f-161">Parametr redirectUrl zawiera adres URL, do którego dostawca zewnętrzny powinien przekierować po uwierzytelnieniu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9f49f-161">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="9f49f-162">Adres URL powinien reprezentować akcję, która będzie podpisywać użytkownika w oparciu o informacje o tożsamości zewnętrznej, jak w poniższym przykładzie uproszczonym:</span><span class="sxs-lookup"><span data-stu-id="9f49f-162">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

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

<span data-ttu-id="9f49f-163">W przypadku wybrania opcji uwierzytelniania **indywidualnego konta użytkownika** podczas tworzenia projektu aplikacji sieci Web ASP.NET Code w programie Visual Studio cały kod niezbędny do zalogowania się za pomocą zewnętrznego dostawcy jest już w projekcie, jak pokazano na rysunku 9-3.</span><span class="sxs-lookup"><span data-stu-id="9f49f-163">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 9-3.</span></span>

![Zrzut ekranu przedstawiający okno dialogowe Nowa aplikacja sieci Web ASP.NET Core.](./media/index/select-external-authentication-option.png)

<span data-ttu-id="9f49f-165">**Rysunek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="9f49f-165">**Figure 9-3**.</span></span> <span data-ttu-id="9f49f-166">Wybieranie opcji używania uwierzytelniania zewnętrznego podczas tworzenia projektu aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="9f49f-166">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="9f49f-167">Oprócz zewnętrznych dostawców uwierzytelniania wymienionych wcześniej pakiety innych firm są dostępne, które zapewniają oprogramowanie pośredniczące do korzystania z wielu innych zewnętrznych dostawców uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="9f49f-167">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="9f49f-168">Aby uzyskać listę, zobacz " [ASPNET. Security. OAuth. Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) " w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="9f49f-168">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="9f49f-169">Możesz również utworzyć własne oprogramowanie pośredniczące uwierzytelniania zewnętrznego, aby rozwiązać pewne szczególne potrzeby.</span><span class="sxs-lookup"><span data-stu-id="9f49f-169">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="9f49f-170">Uwierzytelnianie przy użyciu tokenów okaziciela</span><span class="sxs-lookup"><span data-stu-id="9f49f-170">Authenticate with bearer tokens</span></span>

<span data-ttu-id="9f49f-171">Uwierzytelnianie za pomocą tożsamości ASP.NET Core (lub tożsamości i zewnętrznych dostawców uwierzytelniania) działa dobrze w przypadku wielu scenariuszy aplikacji sieci Web, w których przechowywane są informacje o użytkowniku w pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="9f49f-171">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="9f49f-172">W innych scenariuszach pliki cookie nie są naturalnymi sposobami utrwalania i przesyłania danych.</span><span class="sxs-lookup"><span data-stu-id="9f49f-172">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="9f49f-173">Na przykład w interfejsie API sieci Web ASP.NET Core, który uwidacznia punkty końcowe RESTful, do których mogą uzyskiwać dostęp aplikacje jednostronicowe (aplikacji jednostronicowych), przez natywnych klientów, a nawet przez inne interfejsy API sieci Web, zwykle zamiast tego należy użyć uwierzytelniania tokenu nośnego.</span><span class="sxs-lookup"><span data-stu-id="9f49f-173">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="9f49f-174">Te typy aplikacji nie działają z plikami cookie, ale mogą łatwo pobrać token okaziciela i uwzględnić go w nagłówku autoryzacji kolejnych żądań.</span><span class="sxs-lookup"><span data-stu-id="9f49f-174">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="9f49f-175">Aby włączyć uwierzytelnianie tokenu, ASP.NET Core obsługuje kilka opcji używania [uwierzytelniania OAuth 2,0](https://oauth.net/2/) i [OpenID Connect Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="9f49f-175">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="9f49f-176">Uwierzytelnianie za pomocą dostawcy tożsamości OpenID Connect Connect lub OAuth 2,0</span><span class="sxs-lookup"><span data-stu-id="9f49f-176">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="9f49f-177">Jeśli informacje o użytkowniku są przechowywane w Azure Active Directory lub inne rozwiązanie do obsługi tożsamości, które obsługuje OpenID Connect Connect lub OAuth 2,0, można użyć pakietu **Microsoft. AspNetCore. Authentication. OpenIdConnect** do uwierzytelniania za pomocą przepływu pracy OpenID Connect Connect.</span><span class="sxs-lookup"><span data-stu-id="9f49f-177">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="9f49f-178">Na przykład w celu uwierzytelnienia w mikrousłudze Identity. API w eShopOnContainers, aplikacja sieci Web ASP.NET Core może korzystać z oprogramowania pośredniczącego z tego pakietu, jak pokazano w poniższym uproszczonym przykładzie w `Startup.cs`:</span><span class="sxs-lookup"><span data-stu-id="9f49f-178">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

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

<span data-ttu-id="9f49f-179">Należy pamiętać, że w przypadku korzystania z tego przepływu pracy oprogramowanie pośredniczące ASP.NET Core Identity nie jest konieczne, ponieważ usługa tożsamości zawiera wszystkie magazyny informacji o użytkownikach i ich uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="9f49f-179">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="9f49f-180">Wystawianie tokenów zabezpieczających z usługi ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9f49f-180">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="9f49f-181">Jeśli wolisz wydawać tokeny zabezpieczające dla lokalnych użytkowników tożsamości ASP.NET Core zamiast korzystać z zewnętrznego dostawcy tożsamości, możesz korzystać z niektórych dobrych bibliotek innych firm.</span><span class="sxs-lookup"><span data-stu-id="9f49f-181">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="9f49f-182">[Usługi identityserver4](https://github.com/IdentityServer/IdentityServer4) i [OpenIddict](https://github.com/openiddict/openiddict-core) są dostawcami OpenID Connect, którzy integrują się z usługą ASP.NET Core Identity, aby wystawiać tokeny zabezpieczające z usługi ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9f49f-182">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="9f49f-183">[Dokumentacja usługi identityserver4](https://identityserver4.readthedocs.io/en/latest/) zawiera szczegółowe instrukcje dotyczące korzystania z biblioteki.</span><span class="sxs-lookup"><span data-stu-id="9f49f-183">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="9f49f-184">Jednak podstawowe kroki do korzystania z usługi identityserver4 w celu wystawiania tokenów są następujące.</span><span class="sxs-lookup"><span data-stu-id="9f49f-184">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="9f49f-185">Nazywasz aplikację. UseIdentityServer w metodzie Startup. configure, aby dodać usługi identityserver4 do potoku przetwarzania żądań HTTP aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9f49f-185">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="9f49f-186">Pozwala to, aby Biblioteka obsługiwała żądania OpenID Connect Connect i OAuth2 Endpoints, takich jak/Connect/token.</span><span class="sxs-lookup"><span data-stu-id="9f49f-186">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="9f49f-187">Usługi identityserver4 można skonfigurować w programie Startup. ConfigureServices, wykonując wywołanie do usług. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="9f49f-187">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="9f49f-188">Skonfiguruj serwer tożsamości, ustawiając następujące dane:</span><span class="sxs-lookup"><span data-stu-id="9f49f-188">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="9f49f-189">[Poświadczenia](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) do użycia podczas podpisywania.</span><span class="sxs-lookup"><span data-stu-id="9f49f-189">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="9f49f-190">[Zasoby tożsamości i interfejsu API](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) , do których użytkownicy mogą żądać dostępu:</span><span class="sxs-lookup"><span data-stu-id="9f49f-190">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="9f49f-191">Zasoby interfejsu API reprezentują chronione dane lub funkcje, do których użytkownik może uzyskać dostęp za pomocą tokenu dostępu.</span><span class="sxs-lookup"><span data-stu-id="9f49f-191">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="9f49f-192">Przykładem zasobu interfejsu API będzie interfejs API sieci Web (lub zestaw interfejsów API) wymagający autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="9f49f-192">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="9f49f-193">Zasoby tożsamości reprezentują informacje (oświadczenia), które są nadawane klientowi do identyfikowania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9f49f-193">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="9f49f-194">Oświadczenia mogą zawierać nazwę użytkownika, adres e-mail i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="9f49f-194">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="9f49f-195">[Klienci](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) , którzy będą łączyć się w celu żądania tokenów.</span><span class="sxs-lookup"><span data-stu-id="9f49f-195">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="9f49f-196">Mechanizm magazynowania dla informacji o użytkowniku, na przykład [tożsamość ASP.NET Core](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) lub alternatywa.</span><span class="sxs-lookup"><span data-stu-id="9f49f-196">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="9f49f-197">Po określeniu klientów i zasobów do użycia przez usługi identityserver4 można przekazać kolekcję <xref:System.Collections.Generic.IEnumerable%601> odpowiedniego typu do metod, które pobierają klientów lub magazyny zasobów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="9f49f-197">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="9f49f-198">Lub w przypadku bardziej złożonych scenariuszy można dostarczyć klienta lub typy dostawcy zasobów za pomocą iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="9f49f-198">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="9f49f-199">Przykładowa konfiguracja usługi identityserver4 do używania zasobów w pamięci i klientów dostarczanych przez niestandardowy typ IClientStore może wyglądać podobnie do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="9f49f-199">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a><span data-ttu-id="9f49f-200">Korzystanie z tokenów zabezpieczających</span><span class="sxs-lookup"><span data-stu-id="9f49f-200">Consume security tokens</span></span>

<span data-ttu-id="9f49f-201">Uwierzytelnianie przy użyciu punktu końcowego OpenID Connect Connect lub wystawianie własnych tokenów zabezpieczających obejmuje niektóre scenariusze.</span><span class="sxs-lookup"><span data-stu-id="9f49f-201">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="9f49f-202">Ale co to jest usługa, która po prostu musi ograniczyć dostęp do tych użytkowników, którzy mają prawidłowe tokeny zabezpieczające udostępniane przez inną usługę?</span><span class="sxs-lookup"><span data-stu-id="9f49f-202">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="9f49f-203">W tym scenariuszu oprogramowanie pośredniczące uwierzytelniania obsługujące tokeny JWT jest dostępne w pakiecie **Microsoft. AspNetCore. Authentication. JwtBearer** .</span><span class="sxs-lookup"><span data-stu-id="9f49f-203">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="9f49f-204">JWT oznacza "[token sieci Web JSON](https://tools.ietf.org/html/rfc7519)" i jest typowym formatem tokenu zabezpieczającego (zdefiniowanym w dokumencie RFC 7519) do komunikacji oświadczeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9f49f-204">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="9f49f-205">Uproszczony przykład użycia oprogramowania pośredniczącego do korzystania z takich tokenów może wyglądać podobnie do tego fragmentu kodu, który został pobrany z mikrousługi porządkowania. API eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="9f49f-205">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

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

<span data-ttu-id="9f49f-206">Parametry w tym wykorzystaniu są następujące:</span><span class="sxs-lookup"><span data-stu-id="9f49f-206">The parameters in this usage are:</span></span>

- <span data-ttu-id="9f49f-207">`Audience` reprezentuje odbiorcę przychodzącego tokenu lub zasobu, do którego token udziela dostępu.</span><span class="sxs-lookup"><span data-stu-id="9f49f-207">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="9f49f-208">Jeśli wartość określona w tym parametrze nie pasuje do parametru w tokenie, token zostanie odrzucony.</span><span class="sxs-lookup"><span data-stu-id="9f49f-208">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="9f49f-209">`Authority` jest adresem serwera uwierzytelniania wystawiającego tokeny.</span><span class="sxs-lookup"><span data-stu-id="9f49f-209">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="9f49f-210">Oprogramowanie pośredniczące uwierzytelniania okaziciela JWT używa tego identyfikatora URI do uzyskania klucza publicznego, którego można użyć do zweryfikowania podpisu tokenu.</span><span class="sxs-lookup"><span data-stu-id="9f49f-210">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="9f49f-211">Oprogramowanie pośredniczące potwierdza również, że parametr `iss` w tokenie jest zgodny z tym identyfikatorem URI.</span><span class="sxs-lookup"><span data-stu-id="9f49f-211">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="9f49f-212">Inny parametr, `RequireHttpsMetadata`, jest przydatny do celów testowych. Ten parametr należy ustawić na wartość false, aby można było testować w środowiskach, w których nie masz certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="9f49f-212">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="9f49f-213">W rzeczywistych wdrożeniach tokeny okaziciela JWT powinny zawsze być przesyłane tylko za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9f49f-213">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="9f49f-214">W przypadku tego oprogramowania pośredniczącego tokeny JWT są automatycznie wyodrębniane z nagłówków autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="9f49f-214">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="9f49f-215">Są one następnie deserializowane, zweryfikowane (przy użyciu wartości z parametrów `Audience` i `Authority`) i przechowywane jako informacje o użytkowniku, do których odwołuje się później za pomocą akcji MVC lub filtrów autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="9f49f-215">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="9f49f-216">Oprogramowanie pośredniczące uwierzytelniania okaziciela JWT może również obsługiwać bardziej zaawansowane scenariusze, takie jak użycie certyfikatu lokalnego do walidacji tokenu, jeśli Urząd nie jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="9f49f-216">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="9f49f-217">W tym scenariuszu można określić obiekt `TokenValidationParameters` w obiekcie `JwtBearerOptions`.</span><span class="sxs-lookup"><span data-stu-id="9f49f-217">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9f49f-218">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="9f49f-218">Additional resources</span></span>

- <span data-ttu-id="9f49f-219">**Udostępnianie plików cookie między aplikacjami** </span><span class="sxs-lookup"><span data-stu-id="9f49f-219">**Sharing cookies between applications** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- <span data-ttu-id="9f49f-220">**Wprowadzenie do tożsamości** </span><span class="sxs-lookup"><span data-stu-id="9f49f-220">**Introduction to Identity** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="9f49f-221">**Rick Anderson. Uwierzytelnianie dwuskładnikowe za pomocą SMS** </span><span class="sxs-lookup"><span data-stu-id="9f49f-221">**Rick Anderson. Two-factor authentication with SMS** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="9f49f-222">**Włączanie uwierzytelniania przy użyciu usługi Facebook, Google i innych dostawców zewnętrznych** </span><span class="sxs-lookup"><span data-stu-id="9f49f-222">**Enabling authentication using Facebook, Google and other external providers** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="9f49f-223">**Michell Anicas. Wprowadzenie do \ uwierzytelniania OAuth 2**</span><span class="sxs-lookup"><span data-stu-id="9f49f-223">**Michell Anicas. An Introduction to OAuth 2** \</span></span>
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- <span data-ttu-id="9f49f-224">**ASPNET. Security. OAuth. Providers** (repozytorium GitHub dla dostawców ASP.NET OAuth) </span><span class="sxs-lookup"><span data-stu-id="9f49f-224">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers) </span></span>\
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- <span data-ttu-id="9f49f-225">**Usługi identityserver4. Oficjalna dokumentacja** </span><span class="sxs-lookup"><span data-stu-id="9f49f-225">**IdentityServer4. Official documentation** </span></span>\
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
><span data-ttu-id="9f49f-226">[Poprzedni](../implement-resilient-applications/monitor-app-health.md)
>[Następny](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="9f49f-226">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
