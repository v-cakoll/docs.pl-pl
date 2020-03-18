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
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="014e4-103">Zabezpieczanie mikrousług i aplikacji sieci Web .NET</span><span class="sxs-lookup"><span data-stu-id="014e4-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="014e4-104">Istnieje tak wiele aspektów dotyczących zabezpieczeń w mikrousługach i aplikacjach sieci web, że temat może łatwo podjąć kilka książek, takich jak ten, więc w tej sekcji skupimy się na uwierzytelnianiu, autoryzacji i wtajemnic aplikacji.</span><span class="sxs-lookup"><span data-stu-id="014e4-104">There are so many aspects about security in microservices and web applications that the topic could easy take several books like this one so, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="014e4-105">Implementowanie uwierzytelniania w mikrousługach i aplikacjach sieci Web .NET</span><span class="sxs-lookup"><span data-stu-id="014e4-105">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="014e4-106">Często jest to konieczne dla zasobów i interfejsów API opublikowanych przez usługę, aby być ograniczone do niektórych zaufanych użytkowników lub klientów.</span><span class="sxs-lookup"><span data-stu-id="014e4-106">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="014e4-107">Pierwszym krokiem do podejmowania tego rodzaju decyzji zaufania na poziomie interfejsu API jest uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="014e4-107">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="014e4-108">Uwierzytelnianie to proces niezawodnego weryfikowania tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="014e4-108">Authentication is the process of reliably verify a user’s identity.</span></span>

<span data-ttu-id="014e4-109">W scenariuszach mikrousług uwierzytelnianie jest zazwyczaj obsługiwane centralnie.</span><span class="sxs-lookup"><span data-stu-id="014e4-109">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="014e4-110">Jeśli używasz bramy interfejsu API, brama jest dobrym miejscem do uwierzytelniania, jak pokazano na rysunku 9-1.</span><span class="sxs-lookup"><span data-stu-id="014e4-110">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="014e4-111">Jeśli używasz tej metody, upewnij się, że poszczególne mikrousługi nie można uzyskać bezpośrednio (bez bramy interfejsu API), chyba że dodatkowe zabezpieczenia jest w miejscu uwierzytelniania wiadomości, niezależnie od tego, czy pochodzą one z bramy, czy nie.</span><span class="sxs-lookup"><span data-stu-id="014e4-111">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![Diagram przedstawiający sposób interakcji aplikacji mobilnej klienta z zapleczem.](./media/index/api-gateway-centralized-authentication.png)

<span data-ttu-id="014e4-113">**Rysunek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="014e4-113">**Figure 9-1**.</span></span> <span data-ttu-id="014e4-114">Scentralizowane uwierzytelnianie za pomocą bramy interfejsu API</span><span class="sxs-lookup"><span data-stu-id="014e4-114">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="014e4-115">Gdy brama interfejsu API centralizuje uwierzytelnianie, dodaje informacje o użytkowniku podczas przekazywania żądań do mikrousług.</span><span class="sxs-lookup"><span data-stu-id="014e4-115">When the API Gateway centralizes authentication, it adds user information when forwarding requests to the microservices.</span></span> <span data-ttu-id="014e4-116">Jeśli usługi są dostępne bezpośrednio, usługi uwierzytelniania, takie jak Usługa Azure Active Directory lub mikrousługi dedykowanego uwierzytelniania działającejako usługa tokenu zabezpieczającego (STS) mogą służyć do uwierzytelniania użytkowników.</span><span class="sxs-lookup"><span data-stu-id="014e4-116">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="014e4-117">Decyzje dotyczące zaufania są współużytkowane przez usługi za pomocą tokenów zabezpieczającym lub plików cookie.</span><span class="sxs-lookup"><span data-stu-id="014e4-117">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="014e4-118">(Te tokeny mogą być współużytkowane między ASP.NET aplikacje podstawowe, jeśli to konieczne, implementując [udostępnianie plików cookie](/aspnet/core/security/cookie-sharing).) Ten wzór przedstawiono na rysunku 9-2.</span><span class="sxs-lookup"><span data-stu-id="014e4-118">(These tokens can be shared between ASP.NET Core applications, if needed, by implementing [cookie sharing](/aspnet/core/security/cookie-sharing).) This pattern is illustrated in Figure 9-2.</span></span>

![Diagram przedstawiający uwierzytelnianie za pośrednictwem mikrousług zaplecza.](./media/index/identity-microservice-authentication.png)

<span data-ttu-id="014e4-120">**Rysunek 9-2**.</span><span class="sxs-lookup"><span data-stu-id="014e4-120">**Figure 9-2**.</span></span> <span data-ttu-id="014e4-121">Uwierzytelnianie przez mikrousługę tożsamości; zaufanie jest współużytkowane przy użyciu tokenu autoryzacji</span><span class="sxs-lookup"><span data-stu-id="014e4-121">Authentication by identity microservice; trust is shared using an authorization token</span></span>

<span data-ttu-id="014e4-122">Gdy mikrousługi są uzyskiwane bezpośrednio, zaufanie, który obejmuje uwierzytelniania i autoryzacji, jest obsługiwany przez token zabezpieczający wystawiony przez dedykowaną mikrousługę, współużytkowane przez mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="014e4-122">When microservices are accessed directly, trust, that includes authentication and authorization, is handled by a security token issued by a dedicated microservice, shared between microservices.</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="014e4-123">Uwierzytelnianie przy użyciu ASP.NET podstawowej tożsamości</span><span class="sxs-lookup"><span data-stu-id="014e4-123">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="014e4-124">Podstawowym mechanizmem w ASP.NET Core do identyfikowania użytkowników aplikacji jest system członkostwa [ASP.NET Core Identity.](/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="014e4-124">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="014e4-125">ASP.NET Tożsamość podstawowa przechowuje informacje o użytkowniku (w tym informacje logowania, role i oświadczenia) w magazynie danych skonfigurowanym przez dewelopera.</span><span class="sxs-lookup"><span data-stu-id="014e4-125">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="014e4-126">Zazwyczaj magazyn danych ASP.NET Core Identity jest magazynem `Microsoft.AspNetCore.Identity.EntityFrameworkCore` entity framework dostarczonym w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="014e4-126">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="014e4-127">Jednak magazyny niestandardowe lub inne pakiety innych firm mogą służyć do przechowywania informacji o tożsamości w usłudze Azure Table Storage, CosmosDB lub innych lokalizacjach.</span><span class="sxs-lookup"><span data-stu-id="014e4-127">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

> [!TIP]
> <span data-ttu-id="014e4-128">ASP.NET Core 2.1, a później zapewnia [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) jako biblioteka klas [razor,](/aspnet/core/razor-pages/ui-class)dzięki czemu nie zobaczysz wiele niezbędnego kodu w projekcie, jak to miało miejsce w przypadku poprzednich wersji.</span><span class="sxs-lookup"><span data-stu-id="014e4-128">ASP.NET Core 2.1 and later provides [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) as a [Razor Class Library](/aspnet/core/razor-pages/ui-class), so you won't see much of the necessary code in your project, as was the case for previous versions.</span></span> <span data-ttu-id="014e4-129">Aby uzyskać szczegółowe informacje na temat dostosowywania kodu tożsamości do własnych potrzeb, zobacz [Tożsamość szkieletu w ASP.NET projektów podstawowych](/aspnet/core/security/authentication/scaffold-identity).</span><span class="sxs-lookup"><span data-stu-id="014e4-129">For details on how to customize the Identity code to suit your needs, see [Scaffold Identity in ASP.NET Core projects](/aspnet/core/security/authentication/scaffold-identity).</span></span>

<span data-ttu-id="014e4-130">Poniższy kod jest pobierany z szablonu projektu ASP.NET Core Web Application MVC 3.1 z wybranym uwierzytelnianiem indywidualnego konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="014e4-130">The following code is taken from the ASP.NET Core Web Application MVC 3.1 project template with individual user account authentication selected.</span></span> <span data-ttu-id="014e4-131">Pokazuje, jak skonfigurować ASP.NET Core Identity przy `Startup.ConfigureServices` użyciu core struktury jednostki w metodzie.</span><span class="sxs-lookup"><span data-stu-id="014e4-131">It shows how to configure ASP.NET Core Identity using Entity Framework Core in the `Startup.ConfigureServices` method.</span></span>

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

<span data-ttu-id="014e4-132">Po skonfigurowaniu ASP.NET core identity można `app.UseAuthentication()` włączyć `endpoints.MapRazorPages()` go, dodając i jak pokazano w następującym kodzie w `Startup.Configure` metodzie usługi:</span><span class="sxs-lookup"><span data-stu-id="014e4-132">Once ASP.NET Core Identity is configured, you enable it by adding the `app.UseAuthentication()` and `endpoints.MapRazorPages()` as shown in the following code in the service's `Startup.Configure` method:</span></span>

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
> <span data-ttu-id="014e4-133">Wiersze w kodzie poprzedzającym **muszą być w kolejności pokazanej,** aby tożsamość działała poprawnie.</span><span class="sxs-lookup"><span data-stu-id="014e4-133">The lines in the preceeding code **MUST BE IN THE ORDER SHOWN** for Identity to work correctly.</span></span>

<span data-ttu-id="014e4-134">Korzystanie z ASP.NET Core Identity umożliwia kilka scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="014e4-134">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="014e4-135">Utwórz nowe informacje o użytkowniku przy użyciu typu UserManager (userManager.CreateAsync).</span><span class="sxs-lookup"><span data-stu-id="014e4-135">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="014e4-136">Uwierzytelnij użytkowników przy użyciu typu SignInManager.</span><span class="sxs-lookup"><span data-stu-id="014e4-136">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="014e4-137">Możesz użyć `signInManager.SignInAsync` do bezpośredniego `signInManager.PasswordSignInAsync` zalogowania się lub potwierdzenia, że hasło użytkownika jest poprawne, a następnie zalogować się.</span><span class="sxs-lookup"><span data-stu-id="014e4-137">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user’s password is correct and then sign them in.</span></span>

- <span data-ttu-id="014e4-138">Zidentyfikuj użytkownika na podstawie informacji przechowywanych w pliku cookie (które są odczytywane przez ASP.NET core identity middleware), tak aby kolejne żądania z przeglądarki zawierały tożsamość i oświadczenia zalogowanego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="014e4-138">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="014e4-139">ASP.NET Core Identity obsługuje również [uwierzytelnianie dwuskładnikowe.](/aspnet/core/security/authentication/2fa)</span><span class="sxs-lookup"><span data-stu-id="014e4-139">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="014e4-140">W przypadku scenariuszy uwierzytelniania, które korzystają z lokalnego magazynu danych użytkownika i które utrzymują tożsamość między żądaniami przy użyciu plików cookie (jak to jest typowe dla aplikacji sieci Web MVC), ASP.NET Core Identity jest zalecanym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="014e4-140">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="014e4-141">Uwierzytelnianie się u dostawców zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="014e4-141">Authenticate with external providers</span></span>

<span data-ttu-id="014e4-142">ASP.NET Core obsługuje również korzystanie z [zewnętrznych dostawców uwierzytelniania,](/aspnet/core/security/authentication/social/) aby umożliwić użytkownikom logowanie się za pośrednictwem przepływów [OAuth 2.0.](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span><span class="sxs-lookup"><span data-stu-id="014e4-142">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="014e4-143">Oznacza to, że użytkownicy mogą logować się przy użyciu istniejących procesów uwierzytelniania od dostawców takich jak Microsoft, Google, Facebook lub Twitter i kojarzyć te tożsamości z ASP.NET tożsamości core w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="014e4-143">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="014e4-144">Aby użyć uwierzytelniania zewnętrznego, oprócz tego, że uwierzytelniające pośredniczenie zostało wymienione wcześniej, należy `app.UseAuthentication()` również zarejestrować dostawcę zewnętrznego w `Startup` sposób pokazany w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="014e4-144">To use external authentication, besides including the authentication middleware as mentioned before, using the `app.UseAuthentication()` method, you also have to register the external provider in `Startup` as shown in the following example:</span></span>

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

<span data-ttu-id="014e4-145">Popularni zewnętrzni dostawcy uwierzytelniania i skojarzone z nimi pakiety NuGet są pokazane w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="014e4-145">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="014e4-146">**Dostawca**</span><span class="sxs-lookup"><span data-stu-id="014e4-146">**Provider**</span></span>  | <span data-ttu-id="014e4-147">**Pakiet**</span><span class="sxs-lookup"><span data-stu-id="014e4-147">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="014e4-148">**Microsoft**</span><span class="sxs-lookup"><span data-stu-id="014e4-148">**Microsoft**</span></span> | <span data-ttu-id="014e4-149">**Konto Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="014e4-149">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="014e4-150">**Google**</span><span class="sxs-lookup"><span data-stu-id="014e4-150">**Google**</span></span>    | <span data-ttu-id="014e4-151">**Microsoft.AspNetCore.Authentication.Google**</span><span class="sxs-lookup"><span data-stu-id="014e4-151">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="014e4-152">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="014e4-152">**Facebook**</span></span>  | <span data-ttu-id="014e4-153">**Microsoft.AspNetCore.Authentication.Facebook**</span><span class="sxs-lookup"><span data-stu-id="014e4-153">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="014e4-154">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="014e4-154">**Twitter**</span></span>   | <span data-ttu-id="014e4-155">**Microsoft.AspNetCore.Authentication.Twitter**</span><span class="sxs-lookup"><span data-stu-id="014e4-155">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="014e4-156">We wszystkich przypadkach należy wykonać procedurę rejestracji aplikacji, która jest zależna od dostawcy i która zwykle obejmuje:</span><span class="sxs-lookup"><span data-stu-id="014e4-156">In all cases, you must complete an application registration procedure that is vendor dependent and that usually involves:</span></span>

1. <span data-ttu-id="014e4-157">Uzyskiwanie identyfikatora aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="014e4-157">Getting a Client Application ID.</span></span>
2. <span data-ttu-id="014e4-158">Uzyskiwanie klucza tajnego aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="014e4-158">Getting a Client Application Secret.</span></span>
3. <span data-ttu-id="014e4-159">Konfigurowanie adresu URL przekierowania, który jest obsługiwany przez zagęszanie autoryzacji i zarejestrowanego dostawcy</span><span class="sxs-lookup"><span data-stu-id="014e4-159">Configuring an redirection URL, that's handled by the authorization middleware and the registered provider</span></span>
4. <span data-ttu-id="014e4-160">Opcjonalnie skonfigurowanie adresu URL wylogowania do prawidłowego wylogowania w scenariuszu logowania jednoosobowego (SSO).</span><span class="sxs-lookup"><span data-stu-id="014e4-160">Optionally, configuring a sign-out URL to properly handle sign out in a Single Sign On (SSO) scenario.</span></span>

<span data-ttu-id="014e4-161">Aby uzyskać szczegółowe informacje na temat konfigurowania aplikacji dla zewnętrznego dostawcy, zobacz [uwierzytelnianie dostawcy zewnętrznego w dokumentacji ASP.NET Core).](/aspnet/core/security/authentication/social/)</span><span class="sxs-lookup"><span data-stu-id="014e4-161">For details on configuring your app for an external provider, see the [External provider authentication in the ASP.NET Core documentation](/aspnet/core/security/authentication/social/)).</span></span>

>[!TIP]
><span data-ttu-id="014e4-162">Wszystkie szczegóły są obsługiwane przez zagęszanie autoryzacji i usług wcześniej wymienionych.</span><span class="sxs-lookup"><span data-stu-id="014e4-162">All details are handled by the authorization middleware and services previously mentioned.</span></span> <span data-ttu-id="014e4-163">Tak, po prostu trzeba wybrać opcję uwierzytelniania **indywidualnego konta użytkownika** podczas tworzenia projektu aplikacji sieci web ASP.NET Kod w programie Visual Studio, jak pokazano na rysunku 9-3, oprócz rejestrowania dostawców uwierzytelniania wcześniej wymienionych.</span><span class="sxs-lookup"><span data-stu-id="014e4-163">So, you just have to choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, as shown in Figure 9-3, besides registering the authentication providers previously mentioned.</span></span>

![Zrzut ekranu przedstawiający okno dialogowe Nowa ASP.NET podstawowa aplikacja sieci Web.](./media/index/select-individual-user-account-authentication-option.png)

<span data-ttu-id="014e4-165">**Rysunek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="014e4-165">**Figure 9-3**.</span></span> <span data-ttu-id="014e4-166">Wybieranie opcji Indywidualne konta użytkowników, do korzystania z uwierzytelniania zewnętrznego podczas tworzenia projektu aplikacji sieci web w programie Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="014e4-166">Selecting the Individual User Accounts option, for using external authentication, when creating a web application project in Visual Studio 2019.</span></span>

<span data-ttu-id="014e4-167">Oprócz dostawców uwierzytelniania zewnętrznego wymienionych wcześniej dostępne są pakiety innych firm, które zapewniają pośredniczenie do korzystania z wielu innych dostawców uwierzytelniania zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="014e4-167">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="014e4-168">Aby uzyskać listę, zobacz repozytorium [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) w usteercie GitHub.</span><span class="sxs-lookup"><span data-stu-id="014e4-168">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repository on GitHub.</span></span>

<span data-ttu-id="014e4-169">Można również utworzyć własne zewnętrzne pośrednice uwierzytelniania, aby rozwiązać niektóre specjalne potrzeby.</span><span class="sxs-lookup"><span data-stu-id="014e4-169">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="014e4-170">Uwierzytelnianie za pomocą tokenów na okaziciela</span><span class="sxs-lookup"><span data-stu-id="014e4-170">Authenticate with bearer tokens</span></span>

<span data-ttu-id="014e4-171">Uwierzytelnianie przy użyciu ASP.NET tożsamości podstawowej (lub tożsamości oraz zewnętrznych dostawców uwierzytelniania) działa dobrze w wielu scenariuszach aplikacji sieci web, w których przechowywanie informacji o użytkowniku w pliku cookie jest odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="014e4-171">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="014e4-172">W innych scenariuszach pliki cookie nie są jednak naturalnym sposobem utrzymywania się i przesyłania danych.</span><span class="sxs-lookup"><span data-stu-id="014e4-172">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="014e4-173">Na przykład w interfejsie API sieci Web ASP.NET, który udostępnia restful punktów końcowych, które mogą być dostępne dla aplikacji jednostronicowych (SPA), przez klientów macierzystych lub nawet przez inne interfejsy API sieci Web, zazwyczaj chcesz użyć uwierzytelniania tokenu elementu nośnego zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="014e4-173">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="014e4-174">Tego typu aplikacje nie działają z plikami cookie, ale można łatwo pobrać token elementu nośnego i dołączyć go w nagłówku autoryzacji kolejnych żądań.</span><span class="sxs-lookup"><span data-stu-id="014e4-174">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="014e4-175">Aby włączyć uwierzytelnianie tokenów, ASP.NET Core obsługuje kilka opcji korzystania z [oauth 2.0](https://oauth.net/2/) i [OpenID Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="014e4-175">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="014e4-176">Uwierzytelnianie za pomocą dostawcy tożsamości OpenID Connect lub OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="014e4-176">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="014e4-177">Jeśli informacje o użytkowniku są przechowywane w usłudze Azure Active Directory lub innym rozwiązaniu tożsamości obsługującym openid connect lub OAuth 2.0, można uwierzytelnić go za pomocą pakietu **Microsoft.AspNetCore.Authentication.OpenIdConnect** do uwierzytelniania przy użyciu przepływu pracy OpenID Connect.</span><span class="sxs-lookup"><span data-stu-id="014e4-177">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="014e4-178">Na przykład, aby uwierzytelnić się w mikrousłudze Identity.Api w eShopOnContainers, ASP.NET Core aplikacji sieci web można `Startup.cs`użyć pośredniczenia z tego pakietu, jak pokazano w poniższym uproszczonym przykładzie w:</span><span class="sxs-lookup"><span data-stu-id="014e4-178">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

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

<span data-ttu-id="014e4-179">Należy zauważyć, że podczas korzystania z tego przepływu pracy ASP.NET core identity middleware nie jest potrzebne, ponieważ cały magazyn informacji o użytkowniku i uwierzytelniania jest obsługiwany przez usługę Tożsamości.</span><span class="sxs-lookup"><span data-stu-id="014e4-179">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="014e4-180">Wystawianie tokenów zabezpieczający z usługi ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="014e4-180">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="014e4-181">Jeśli wolisz wystawiać tokeny zabezpieczające dla lokalnych użytkowników ASP.NET podstawowej tożsamości, a nie przy użyciu zewnętrznego dostawcy tożsamości, możesz skorzystać z niektórych dobrych bibliotek innych firm.</span><span class="sxs-lookup"><span data-stu-id="014e4-181">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="014e4-182">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) i [OpenIddict](https://github.com/openiddict/openiddict-core) są dostawcami OpenID Connect, którzy łatwo integrują się z ASP.NET Core Identity, aby umożliwić wystawianie tokenów zabezpieczaczy z usługi ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="014e4-182">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="014e4-183">[Dokumentacja IdentityServer4](https://identityserver4.readthedocs.io/en/latest/) zawiera szczegółowe instrukcje dotyczące korzystania z biblioteki.</span><span class="sxs-lookup"><span data-stu-id="014e4-183">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="014e4-184">Jednak podstawowe kroki przy użyciu IdentityServer4 do wystawiania tokenów są następujące.</span><span class="sxs-lookup"><span data-stu-id="014e4-184">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="014e4-185">Dzwonisz do aplikacji. UżyjIdentityServer w Startup.Configure metody, aby dodać IdentityServer4 do potoku przetwarzania żądania HTTP aplikacji.</span><span class="sxs-lookup"><span data-stu-id="014e4-185">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="014e4-186">Dzięki temu biblioteka obsługuje żądania openid connect i oauth2 punktów końcowych, takich jak /connect/token.</span><span class="sxs-lookup"><span data-stu-id="014e4-186">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="014e4-187">IdentityServer4 można skonfigurować w Startup.ConfigureServices, wykonując wywołanie usług. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="014e4-187">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="014e4-188">Serwer tożsamości można skonfigurować, ustawiając następujące dane:</span><span class="sxs-lookup"><span data-stu-id="014e4-188">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="014e4-189">[Poświadczenia](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) używane do podpisywania.</span><span class="sxs-lookup"><span data-stu-id="014e4-189">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="014e4-190">Zasoby [tożsamości i interfejsu API,](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) do których użytkownicy mogą żądać dostępu:</span><span class="sxs-lookup"><span data-stu-id="014e4-190">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="014e4-191">Zasoby interfejsu API reprezentują chronione dane lub funkcje, do których użytkownik może uzyskać dostęp za pomocą tokenu dostępu.</span><span class="sxs-lookup"><span data-stu-id="014e4-191">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="014e4-192">Przykładem zasobu interfejsu API może być internetowy interfejs API (lub zestaw interfejsów API), który wymaga autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="014e4-192">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="014e4-193">Zasoby tożsamości reprezentują informacje (oświadczenia), które są podane do klienta w celu zidentyfikowania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="014e4-193">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="014e4-194">Oświadczenia mogą zawierać nazwę użytkownika, adres e-mail itd.</span><span class="sxs-lookup"><span data-stu-id="014e4-194">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="014e4-195">[Klienci,](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) którzy będą łączyć się w celu żądania tokenów.</span><span class="sxs-lookup"><span data-stu-id="014e4-195">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="014e4-196">Mechanizm przechowywania informacji o użytkowniku, takich jak [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) lub alternatywą.</span><span class="sxs-lookup"><span data-stu-id="014e4-196">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="014e4-197">Po określeniu klientów i zasobów do użycia serwera <xref:System.Collections.Generic.IEnumerable%601> IdentityServer4 można przekazać kolekcję odpowiedniego typu do metod, które przyjmują w pamięci magazyny klientów lub zasobów.</span><span class="sxs-lookup"><span data-stu-id="014e4-197">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="014e4-198">Lub dla bardziej złożonych scenariuszy można podać typy klienta lub dostawcy zasobów za pośrednictwem iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="014e4-198">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="014e4-199">Przykładowa konfiguracja serwera IdentityServer4 do używania zasobów w pamięci i klientów dostarczonych przez niestandardowy typ iClientStore może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="014e4-199">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

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

### <a name="consume-security-tokens"></a><span data-ttu-id="014e4-200">Korzystanie z tokenów zabezpieczania</span><span class="sxs-lookup"><span data-stu-id="014e4-200">Consume security tokens</span></span>

<span data-ttu-id="014e4-201">Uwierzytelnianie względem punktu końcowego OpenID Connect lub wydawanie własnych tokenów zabezpieczających obejmuje niektóre scenariusze.</span><span class="sxs-lookup"><span data-stu-id="014e4-201">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="014e4-202">Ale co z usługą, która po prostu musi ograniczyć dostęp do tych użytkowników, którzy mają prawidłowe tokeny zabezpieczające, które zostały dostarczone przez inną usługę?</span><span class="sxs-lookup"><span data-stu-id="014e4-202">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="014e4-203">W tym scenariuszu zagęszanieuwierzytelniania, które obsługuje tokeny JWT jest dostępna w pakiecie **Microsoft.AspNetCore.Authentication.JwtBearer.**</span><span class="sxs-lookup"><span data-stu-id="014e4-203">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="014e4-204">JWT oznacza "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" i jest typowym formatem tokenów zabezpieczających (zdefiniowanym przez RFC 7519) do komunikowania oświadczeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="014e4-204">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="014e4-205">Uproszczony przykład, jak używać pośredniczenia do korzystania z takich tokenów może wyglądać jak ten fragment kodu, zaczerpnięte z mikrousługi Ordering.Api eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="014e4-205">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

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

<span data-ttu-id="014e4-206">Parametry w tym użyciu są następujące:</span><span class="sxs-lookup"><span data-stu-id="014e4-206">The parameters in this usage are:</span></span>

- <span data-ttu-id="014e4-207">`Audience`reprezentuje odbiorcę tokenu przychodzącego lub zasób, do który token udziela dostępu.</span><span class="sxs-lookup"><span data-stu-id="014e4-207">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="014e4-208">Jeśli wartość określona w tym parametrze nie jest zgodna z parametrem w tokenie, token zostanie odrzucony.</span><span class="sxs-lookup"><span data-stu-id="014e4-208">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="014e4-209">`Authority`to adres serwera uwierzytelniania wystawiającego tokeny.</span><span class="sxs-lookup"><span data-stu-id="014e4-209">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="014e4-210">Zagęszczenie uwierzytelniania elementu nośnego JWT używa tego identyfikatora URI do uzyskania klucza publicznego, który może służyć do sprawdzania poprawności podpisu tokenu.</span><span class="sxs-lookup"><span data-stu-id="014e4-210">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="014e4-211">Program pośrednidlaczpotwierdza `iss` również, że parametr w tokenie pasuje do tego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="014e4-211">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="014e4-212">Inny parametr, `RequireHttpsMetadata`, jest przydatny do celów testowych; można ustawić ten parametr false, dzięki czemu można testować w środowiskach, w których nie masz certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="014e4-212">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="014e4-213">W rzeczywistych wdrożeniach tokeny elementu nośnego JWT powinny być zawsze przekazywane tylko przez https.</span><span class="sxs-lookup"><span data-stu-id="014e4-213">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="014e4-214">Po umieszczeniu tego narzędzia pośredniczącego tokeny JWT są automatycznie wyodrębniane z nagłówków autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="014e4-214">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="014e4-215">Są one następnie deserializowane, weryfikowane (przy użyciu wartości w `Audience` parametrach i) `Authority` i przechowywane jako informacje o użytkowniku, do których można się później odwoływać przez akcje MVC lub filtry autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="014e4-215">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="014e4-216">Pośrednice uwierzytelniania elementu nośnego JWT może również obsługiwać bardziej zaawansowane scenariusze, takie jak używanie certyfikatu lokalnego do sprawdzania poprawności tokenu, jeśli urząd nie jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="014e4-216">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="014e4-217">W tym scenariuszu można `TokenValidationParameters` określić `JwtBearerOptions` obiekt w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="014e4-217">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="014e4-218">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="014e4-218">Additional resources</span></span>

- <span data-ttu-id="014e4-219">**Udostępnianie plików cookie między aplikacjami** </span><span class="sxs-lookup"><span data-stu-id="014e4-219">**Sharing cookies between applications** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- <span data-ttu-id="014e4-220">**Wprowadzenie do tożsamości** </span><span class="sxs-lookup"><span data-stu-id="014e4-220">**Introduction to Identity** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="014e4-221">**Rick Anderson. Uwierzytelnianie dwuskładnikowe za pomocą wiadomości SMS** </span><span class="sxs-lookup"><span data-stu-id="014e4-221">**Rick Anderson. Two-factor authentication with SMS** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="014e4-222">**Włączanie uwierzytelniania za pomocą Facebooka, Google i innych dostawców zewnętrznych** </span><span class="sxs-lookup"><span data-stu-id="014e4-222">**Enabling authentication using Facebook, Google and other external providers** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="014e4-223">**Michell Anicas. Wprowadzenie do OAuth 2** </span><span class="sxs-lookup"><span data-stu-id="014e4-223">**Michell Anicas. An Introduction to OAuth 2** </span></span>\
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- <span data-ttu-id="014e4-224">**AspNet.Security.OAuth.Providers** (repozytowy GitHub dla ASP.NET dostawców OAuth) </span><span class="sxs-lookup"><span data-stu-id="014e4-224">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers) </span></span>\
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- <span data-ttu-id="014e4-225">**Serwer tożsamości4. Oficjalna dokumentacja** </span><span class="sxs-lookup"><span data-stu-id="014e4-225">**IdentityServer4. Official documentation** </span></span>\
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
><span data-ttu-id="014e4-226">[Poprzedni](../implement-resilient-applications/monitor-app-health.md)
>[następny](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="014e4-226">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
