---
title: IdentityServer dla natywnych aplikacji w chmurze
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | IdentityServer
ms.date: 06/30/2019
ms.openlocfilehash: 48d0b95a40682f3127127851781b4d0e26e44630
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728577"
---
# <a name="identityserver-for-cloud-native-applications"></a><span data-ttu-id="fd467-103">IdentityServer dla aplikacji natywnych w chmurze</span><span class="sxs-lookup"><span data-stu-id="fd467-103">IdentityServer for cloud-native applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="fd467-104">IdentityServer to serwer uwierzytelniania "open source", który implementuje standardy OpenID Connect Connect (OIDC) i OAuth 2,0 dla ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="fd467-104">IdentityServer is an open-source authentication server that implements OpenID Connect (OIDC) and OAuth 2.0 standards for ASP.NET Core.</span></span> <span data-ttu-id="fd467-105">Zaprojektowano w celu zapewnienia typowego sposobu uwierzytelniania żądań do wszystkich aplikacji, niezależnie od tego, czy są to punkty końcowe sieci Web, natywne, mobilne czy interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="fd467-105">It's designed to provide a common way to authenticate requests to all of your applications, whether they're web, native, mobile, or API endpoints.</span></span> <span data-ttu-id="fd467-106">IdentityServer może służyć do implementowania logowania jednokrotnego (SSO) dla wielu aplikacji i typów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fd467-106">IdentityServer can be used to implement Single Sign-On (SSO) for multiple applications and application types.</span></span> <span data-ttu-id="fd467-107">Może służyć do uwierzytelniania rzeczywistych użytkowników za pośrednictwem formularzy logowania i podobnych interfejsów użytkownika, a także uwierzytelniania opartego na usługach, który zazwyczaj obejmuje wystawianie, weryfikację i odnawianie tokenów bez żadnego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fd467-107">It can be used to authenticate actual users via sign-in forms and similar user interfaces as well as service-based authentication that typically involves token issuance, verification, and renewal without any user interface.</span></span> <span data-ttu-id="fd467-108">IdentityServer została zaprojektowana jako dostosowywalne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="fd467-108">IdentityServer is designed to be a customizable solution.</span></span> <span data-ttu-id="fd467-109">Każde wystąpienie jest zwykle dostosowane do konkretnej organizacji i/lub zestawu potrzeb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fd467-109">Each instance is typically customized to suit an individual organization and/or set of applications' needs.</span></span>

## <a name="common-web-app-scenarios"></a><span data-ttu-id="fd467-110">Typowe scenariusze aplikacji sieci Web</span><span class="sxs-lookup"><span data-stu-id="fd467-110">Common web app scenarios</span></span>

<span data-ttu-id="fd467-111">Zazwyczaj aplikacje muszą obsługiwać niektóre lub wszystkie z następujących scenariuszy:</span><span class="sxs-lookup"><span data-stu-id="fd467-111">Typically, applications need to support some or all of the following scenarios:</span></span>

- <span data-ttu-id="fd467-112">Użytkownicy ludzkich uzyskują dostęp do aplikacji sieci Web za pomocą przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="fd467-112">Human users accessing web applications with a browser.</span></span>
- <span data-ttu-id="fd467-113">Użytkownicy ludzki uzyskują dostęp do interfejsów API sieci Web z aplikacji opartych na przeglądarce.</span><span class="sxs-lookup"><span data-stu-id="fd467-113">Human users accessing back-end Web APIs from browser-based apps.</span></span>
- <span data-ttu-id="fd467-114">Użytkownicy w przypadku klientów mobilnych/natywnych uzyskujących dostęp do interfejsów API sieci Web zaplecza.</span><span class="sxs-lookup"><span data-stu-id="fd467-114">Human users on mobile/native clients accessing back-end Web APIs.</span></span>
- <span data-ttu-id="fd467-115">Inne aplikacje uzyskujące dostęp do interfejsów API sieci Web zaplecza (bez aktywnego użytkownika lub interfejsu użytkownika).</span><span class="sxs-lookup"><span data-stu-id="fd467-115">Other applications accessing back-end Web APIs (without an active user or user interface).</span></span>
- <span data-ttu-id="fd467-116">Każda aplikacja może wymagać współdziałania z innymi interfejsami API sieci Web przy użyciu własnej tożsamości lub delegowania do tożsamości użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fd467-116">Any application may need to interact with other Web APIs, using its own identity or delegating to the user's identity.</span></span>

<span data-ttu-id="fd467-117">![typy aplikacji i scenariusze](./media/application-types.png)
**rysunku 8-1**.</span><span class="sxs-lookup"><span data-stu-id="fd467-117">![Application types and scenarios](./media/application-types.png)
**Figure 8-1**.</span></span> <span data-ttu-id="fd467-118">Typy aplikacji i scenariusze.</span><span class="sxs-lookup"><span data-stu-id="fd467-118">Application types and scenarios.</span></span>

<span data-ttu-id="fd467-119">W każdym z tych scenariuszy uwidocznione funkcje muszą być zabezpieczone przed nieautoryzowanym użyciem.</span><span class="sxs-lookup"><span data-stu-id="fd467-119">In each of these scenarios, the exposed functionality needs to be secured against unauthorized use.</span></span> <span data-ttu-id="fd467-120">Minimalnym wymaganiem jest zazwyczaj uwierzytelnianie użytkownika lub podmiotu zabezpieczeń wysyłającego żądanie dotyczące zasobu.</span><span class="sxs-lookup"><span data-stu-id="fd467-120">At a minimum, this typically requires authenticating the user or principal making a request for a resource.</span></span> <span data-ttu-id="fd467-121">Uwierzytelnianie może korzystać z jednego z kilku popularnych protokołów, takich jak SAML2p, WS-karmione lub OpenID Connect Connect.</span><span class="sxs-lookup"><span data-stu-id="fd467-121">This authentication may use one of several common protocols such as SAML2p, WS-Fed, or OpenID Connect.</span></span> <span data-ttu-id="fd467-122">Komunikowanie się z interfejsami API zwykle używa protokołu OAuth2 oraz obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="fd467-122">Communicating with APIs typically uses the OAuth2 protocol and its support for security tokens.</span></span> <span data-ttu-id="fd467-123">Oddzielenie tych krytycznych zagadnień związanych z bezpieczeństwem i ich implementacji z aplikacji zapewnia spójność i zwiększa bezpieczeństwo i łatwość utrzymania.</span><span class="sxs-lookup"><span data-stu-id="fd467-123">Separating these critical cross-cutting security concerns and their implementation details from the applications themselves ensures consistency and improves security and maintainability.</span></span> <span data-ttu-id="fd467-124">Podniesieniu tych problemów do dedykowanego produktu, takiego jak IdentityServer, ułatwia wymagania dla każdej aplikacji, aby rozwiązać te problemy.</span><span class="sxs-lookup"><span data-stu-id="fd467-124">Outsourcing these concerns to a dedicated product like IdentityServer helps the requirement for every application to solve these problems itself.</span></span>

<span data-ttu-id="fd467-125">IdentityServer zapewnia oprogramowanie pośredniczące działające w ramach aplikacji ASP.NET Core i dodaje obsługę OpenID Connect Connect i OAuth2 (patrz [obsługiwane specyfikacje](http://docs.identityserver.io/en/latest/intro/specs.html)).</span><span class="sxs-lookup"><span data-stu-id="fd467-125">IdentityServer provides middleware that runs within an ASP.NET Core application and adds support for OpenID Connect and OAuth2 (see [supported specifications](http://docs.identityserver.io/en/latest/intro/specs.html)).</span></span> <span data-ttu-id="fd467-126">Organizacje tworzą własne aplikacje ASP.NET Core przy użyciu oprogramowania pośredniczącego IdentityServer, aby działały jako usługa STS dla wszystkich protokołów zabezpieczeń opartych na tokenach.</span><span class="sxs-lookup"><span data-stu-id="fd467-126">Organizations would create their own ASP.NET Core app using IdentityServer middleware to act as the STS for all of their token-based security protocols.</span></span> <span data-ttu-id="fd467-127">Oprogramowanie pośredniczące IdentityServer uwidacznia punkty końcowe do obsługi standardowych funkcji, w tym:</span><span class="sxs-lookup"><span data-stu-id="fd467-127">The IdentityServer middleware exposes endpoints to support standard functionality, including:</span></span>

- <span data-ttu-id="fd467-128">Autoryzuj (uwierzytelniaj użytkownika końcowego)</span><span class="sxs-lookup"><span data-stu-id="fd467-128">Authorize (authenticate the end user)</span></span>
- <span data-ttu-id="fd467-129">Token (żądanie tokenu programowo)</span><span class="sxs-lookup"><span data-stu-id="fd467-129">Token (request a token programmatically)</span></span>
- <span data-ttu-id="fd467-130">Odnajdywanie (metadane dotyczące serwera)</span><span class="sxs-lookup"><span data-stu-id="fd467-130">Discovery (metadata about the server)</span></span>
- <span data-ttu-id="fd467-131">Informacje o użytkowniku (Uzyskiwanie informacji o użytkowniku z prawidłowym tokenem dostępu)</span><span class="sxs-lookup"><span data-stu-id="fd467-131">User Info (get user information with a valid access token)</span></span>
- <span data-ttu-id="fd467-132">Autoryzacja urządzenia (używana do uruchamiania autoryzacji przepływu urządzeń)</span><span class="sxs-lookup"><span data-stu-id="fd467-132">Device Authorization (used to start device flow authorization)</span></span>
- <span data-ttu-id="fd467-133">Introspekcji (Walidacja tokenu)</span><span class="sxs-lookup"><span data-stu-id="fd467-133">Introspection (token validation)</span></span>
- <span data-ttu-id="fd467-134">Odwołanie (odwołanie tokenu)</span><span class="sxs-lookup"><span data-stu-id="fd467-134">Revocation (token revocation)</span></span>
- <span data-ttu-id="fd467-135">Zakończ sesję (Wyzwalaj Logowanie jednokrotne we wszystkich aplikacjach)</span><span class="sxs-lookup"><span data-stu-id="fd467-135">End Session (trigger single sign-out across all apps)</span></span>

## <a name="getting-started"></a><span data-ttu-id="fd467-136">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="fd467-136">Getting started</span></span>

<span data-ttu-id="fd467-137">Usługi identityserver4 to "open source" i bezpłatna do użycia.</span><span class="sxs-lookup"><span data-stu-id="fd467-137">IdentityServer4 is open-source and free to use.</span></span> <span data-ttu-id="fd467-138">Możesz dodać go do aplikacji przy użyciu swoich pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="fd467-138">You can add it to your applications using its NuGet packages.</span></span> <span data-ttu-id="fd467-139">Pakiet główny to [usługi identityserver4](https://www.nuget.org/packages/IdentityServer4/) , który został pobrany ponad 4 000 000 razy.</span><span class="sxs-lookup"><span data-stu-id="fd467-139">The main package is [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) that has been downloaded over four million times.</span></span> <span data-ttu-id="fd467-140">Pakiet podstawowy nie zawiera żadnego kodu interfejsu użytkownika i obsługuje tylko w konfiguracji pamięci.</span><span class="sxs-lookup"><span data-stu-id="fd467-140">The base package doesn't include any user interface code and only supports in memory configuration.</span></span> <span data-ttu-id="fd467-141">Aby używać jej z bazą danych, należy również użyć dostawcy danych, takiego jak [usługi identityserver4. EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) , który używa Entity Framework Core do przechowywania danych konfiguracyjnych i operacyjnych dla IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="fd467-141">To use it with a database, you'll also want a data provider like [IdentityServer4.EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) that uses Entity Framework Core to store configuration and operational data for IdentityServer.</span></span> <span data-ttu-id="fd467-142">W przypadku interfejsu użytkownika można skopiować pliki z [repozytorium szybkiego interfejsu użytkownika](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) do aplikacji ASP.NET Core MVC, aby dodać obsługę logowania i wylogować się przy użyciu oprogramowania pośredniczącego IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="fd467-142">For user interface, you can copy files from the [Quickstart UI repository](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) into your ASP.NET Core MVC application to add support for sign in and sign out using IdentityServer middleware.</span></span>

## <a name="configuration"></a><span data-ttu-id="fd467-143">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="fd467-143">Configuration</span></span>

<span data-ttu-id="fd467-144">Program IdentityServer obsługuje różne rodzaje protokołów i dostawców uwierzytelniania społecznościowego, które można skonfigurować w ramach każdej instalacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="fd467-144">IdentityServer supports different kinds of protocols and social authentication providers that can be configured as part of each custom installation.</span></span> <span data-ttu-id="fd467-145">Jest to zazwyczaj wykonywane w klasie `Startup` aplikacji ASP.NET Core w metodzie `ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="fd467-145">This is typically done in the ASP.NET Core application's `Startup` class in the `ConfigureServices` method.</span></span> <span data-ttu-id="fd467-146">Konfiguracja obejmuje określenie obsługiwanych protokołów i ścieżek do serwerów i punktów końcowych, które będą używane.</span><span class="sxs-lookup"><span data-stu-id="fd467-146">The configuration involves specifying the supported protocols and the paths to the servers and endpoints that will be used.</span></span> <span data-ttu-id="fd467-147">Na rysunku 8-2 przedstawiono przykładową konfigurację wykonywaną w projekcie interfejsu użytkownika szybkiego startu usługi identityserver4:</span><span class="sxs-lookup"><span data-stu-id="fd467-147">Figure 8-2 shows an example configuration taken from the IdentityServer4 Quickstart UI project:</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();

        // some details omitted
        services.AddIdentityServer();

          services.AddAuthentication()
            .AddGoogle("Google", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;

                options.ClientId = "<insert here>";
                options.ClientSecret = "<insert here>";
            })
            .AddOpenIdConnect("demoidsrv", "IdentityServer", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;
                options.SignOutScheme = IdentityServerConstants.SignoutScheme;

                options.Authority = "https://demo.identityserver.io/";
                options.ClientId = "implicit";
                options.ResponseType = "id_token";
                options.SaveTokens = true;
                options.CallbackPath = new PathString("/signin-idsrv");
                options.SignedOutCallbackPath = new PathString("/signout-callback-idsrv");
                options.RemoteSignOutPath = new PathString("/signout-idsrv");

                options.TokenValidationParameters = new TokenValidationParameters
                {
                    NameClaimType = "name",
                    RoleClaimType = "role"
                };
            });
    }
}
```

<span data-ttu-id="fd467-148">**Rysunek 8-2**.</span><span class="sxs-lookup"><span data-stu-id="fd467-148">**Figure 8-2**.</span></span> <span data-ttu-id="fd467-149">Konfigurowanie IdentityServer.</span><span class="sxs-lookup"><span data-stu-id="fd467-149">Configuring IdentityServer.</span></span>

<span data-ttu-id="fd467-150">IdentityServer również udostępnia publiczną witrynę demonstracyjną, która może służyć do testowania różnych protokołów i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fd467-150">IdentityServer also hosts a public demo site that can be used to test various protocols and configurations.</span></span> <span data-ttu-id="fd467-151">Znajduje się on w [https://demo.identityserver.io/](https://demo.identityserver.io/) i zawiera informacje dotyczące sposobu konfigurowania jego zachowania na podstawie podanego `client_id`.</span><span class="sxs-lookup"><span data-stu-id="fd467-151">It's located at [https://demo.identityserver.io/](https://demo.identityserver.io/) and includes information on how to configure its behavior based on the `client_id` provided to it.</span></span>

## <a name="javascript-clients"></a><span data-ttu-id="fd467-152">Klienci języka JavaScript</span><span class="sxs-lookup"><span data-stu-id="fd467-152">JavaScript clients</span></span>

<span data-ttu-id="fd467-153">Wiele aplikacji natywnych w chmurze korzysta z interfejsów API po stronie serwera i rozbudowanych aplikacji jednostronicowych klienta (aplikacji jednostronicowych) na frontonie.</span><span class="sxs-lookup"><span data-stu-id="fd467-153">Many cloud-native applications leverage server-side APIs and rich client single page applications (SPAs) on the front end.</span></span> <span data-ttu-id="fd467-154">IdentityServer dostarcza [klient JavaScript](http://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) (`oidc-client.js`) za pośrednictwem npm, który można dodać do aplikacji jednostronicowych, aby umożliwić im używanie IdentityServer do logowania, wylogowywania i uwierzytelniania interfejsów API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="fd467-154">IdentityServer ships a [JavaScript client](http://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html) (`oidc-client.js`) via NPM that can be added to SPAs to enable them to use IdentityServer for sign in, sign out, and token-based authentication of web APIs.</span></span>

## <a name="references"></a><span data-ttu-id="fd467-155">Odwołania</span><span class="sxs-lookup"><span data-stu-id="fd467-155">References</span></span>

- [<span data-ttu-id="fd467-156">Dokumentacja IdentityServer</span><span class="sxs-lookup"><span data-stu-id="fd467-156">IdentityServer documentation</span></span>](http://docs.identityserver.io/en/latest/)
- [<span data-ttu-id="fd467-157">Typy aplikacji</span><span class="sxs-lookup"><span data-stu-id="fd467-157">Application types</span></span>](https://docs.microsoft.com/azure/active-directory/develop/app-types)
- [<span data-ttu-id="fd467-158">Klient JavaScript OIDC</span><span class="sxs-lookup"><span data-stu-id="fd467-158">JavaScript OIDC client</span></span>](http://docs.identityserver.io/en/latest/quickstarts/4_javascript_client.html)

>[!div class="step-by-step"]
><span data-ttu-id="fd467-159">[Poprzednie](azure-active-directory.md)
>[dalej](security.md)</span><span class="sxs-lookup"><span data-stu-id="fd467-159">[Previous](azure-active-directory.md)
[Next](security.md)</span></span>
