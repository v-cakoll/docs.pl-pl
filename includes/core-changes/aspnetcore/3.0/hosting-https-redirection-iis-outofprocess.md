---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937299"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a><span data-ttu-id="283a1-101">Hosting: włączono przekierowywanie protokołu HTTPS dla aplikacji pozaprocesowych usług IIS</span><span class="sxs-lookup"><span data-stu-id="283a1-101">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>

<span data-ttu-id="283a1-102">Wersja 13.0.19218.0 [modułu ASP.NET Core (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) do hostingu za pośrednictwem usług IIS umożliwia korzystanie z istniejącej funkcji przekierowywania HTTPS dla aplikacji ASP.NET Core 3,0 i 2,2.</span><span class="sxs-lookup"><span data-stu-id="283a1-102">Version 13.0.19218.0 of the [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) for hosting via IIS out-of-process enables an existing HTTPS redirection feature for ASP.NET Core 3.0 and 2.2 apps.</span></span>

<span data-ttu-id="283a1-103">Aby zapoznać się z omówieniem, zobacz [dotnet/AspNetCore # 15243](https://github.com/dotnet/AspNetCore/issues/15243).</span><span class="sxs-lookup"><span data-stu-id="283a1-103">For discussion, see [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="283a1-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="283a1-104">Version introduced</span></span>

<span data-ttu-id="283a1-105">3.0</span><span class="sxs-lookup"><span data-stu-id="283a1-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="283a1-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="283a1-106">Old behavior</span></span>

<span data-ttu-id="283a1-107">Szablon projektu ASP.NET Core 2,1 został po raz pierwszy wprowadzony do obsługi metod oprogramowania pośredniczącego HTTPS, takich jak <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> i <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span><span class="sxs-lookup"><span data-stu-id="283a1-107">The ASP.NET Core 2.1 project template first introduced support for HTTPS middleware methods like <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> and <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span></span> <span data-ttu-id="283a1-108">Włączenie przekierowania HTTPS wymaga dodania konfiguracji, ponieważ aplikacje w trakcie tworzenia nie używają domyślnego portu 443.</span><span class="sxs-lookup"><span data-stu-id="283a1-108">Enabling HTTPS redirection required the addition of configuration, since apps in development don't use the default port of 443.</span></span> <span data-ttu-id="283a1-109">[Protokół HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) jest aktywny tylko wtedy, gdy żądanie już korzysta z protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="283a1-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) is active only if the request is already using HTTPS.</span></span> <span data-ttu-id="283a1-110">Domyślnie pominięto hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="283a1-110">Localhost is skipped by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="283a1-111">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="283a1-111">New behavior</span></span>

<span data-ttu-id="283a1-112">W ASP.NET Core 3,0 scenariusz HTTPS usług IIS został [ulepszony](https://github.com/dotnet/AspNetCore/pull/4685).</span><span class="sxs-lookup"><span data-stu-id="283a1-112">In ASP.NET Core 3.0, the IIS HTTPS scenario was [enhanced](https://github.com/dotnet/AspNetCore/pull/4685).</span></span> <span data-ttu-id="283a1-113">Dzięki ulepszeniu aplikacja może odnaleźć porty HTTPS serwera i wprowadzić `UseHttpsRedirection` pracy domyślnie.</span><span class="sxs-lookup"><span data-stu-id="283a1-113">With the enhancement, an app could discover the server's HTTPS ports and make `UseHttpsRedirection` work by default.</span></span> <span data-ttu-id="283a1-114">Składnik w procesie przetworzył odnajdywanie portów przy użyciu funkcji `IServerAddresses`, która ma wpływ tylko na aplikacje ASP.NET Core 3,0, ponieważ biblioteka w procesie ma wersję z platformą.</span><span class="sxs-lookup"><span data-stu-id="283a1-114">The in-process component accomplished port discovery with the `IServerAddresses` feature, which only affects ASP.NET Core 3.0 apps because the in-process library is versioned with the framework.</span></span> <span data-ttu-id="283a1-115">Składnik pozaprocesowe został zmieniony, aby automatycznie dodać zmienną środowiskową `ASPNETCORE_HTTPS_PORT`.</span><span class="sxs-lookup"><span data-stu-id="283a1-115">The out-of-process component changed to automatically add the `ASPNETCORE_HTTPS_PORT` environment variable.</span></span> <span data-ttu-id="283a1-116">Ta zmiana dotyczyła zarówno aplikacji ASP.NET Core 2,2, jak i 3,0, ponieważ składnik pozaprocesowe jest współużytkowany globalnie.</span><span class="sxs-lookup"><span data-stu-id="283a1-116">This change affected both ASP.NET Core 2.2 and 3.0 apps because the out-of-process component is shared globally.</span></span> <span data-ttu-id="283a1-117">Nie ma to wpływu na aplikacje ASP.NET Core 2,1, ponieważ domyślnie korzystają z wcześniejszej wersji ANCM.</span><span class="sxs-lookup"><span data-stu-id="283a1-117">ASP.NET Core 2.1 apps aren't affected because they use a prior version of ANCM by default.</span></span>

<span data-ttu-id="283a1-118">Powyższe zachowanie zostało zmodyfikowane w ASP.NET Core 3.0.1 i 3.1.0 w wersji zapoznawczej 3 w celu odwrócenia zmiany zachowania w ASP.NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="283a1-118">The preceding behavior was modified in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 to reverse the behavior changes in ASP.NET Core 2.x.</span></span> <span data-ttu-id="283a1-119">Zmiany te mają wpływ tylko na aplikacje pozaprocesowe w programie IIS.</span><span class="sxs-lookup"><span data-stu-id="283a1-119">These changes only affect IIS out-of-process apps.</span></span>

<span data-ttu-id="283a1-120">Jak opisano powyżej, instalacja ASP.NET Core 3.0.0 miała efekt uboczny aktywowania `UseHttpsRedirection` oprogramowania pośredniczącego w aplikacjach ASP.NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="283a1-120">As detailed above, installing ASP.NET Core 3.0.0 had the side effect of also activating the `UseHttpsRedirection` middleware in ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="283a1-121">Wprowadzono zmianę w ANCM w ASP.NET Core 3.0.1 i 3.1.0 Preview 3, która nie ma już wpływu na aplikacje ASP.NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="283a1-121">A change was made to ANCM in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 such that installing them no longer has this effect on ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="283a1-122">Zmienna środowiskowa `ASPNETCORE_HTTPS_PORT` ANCM wprowadzona w ASP.NET Core 3.0.0 została zmieniona na `ASPNETCORE_ANCM_HTTPS_PORT` w ASP.NET Core 3.0.1 i 3.1.0 Preview 3.</span><span class="sxs-lookup"><span data-stu-id="283a1-122">The `ASPNETCORE_HTTPS_PORT` environment variable that ANCM populated in ASP.NET Core 3.0.0 was changed to `ASPNETCORE_ANCM_HTTPS_PORT` in ASP.NET Core 3.0.1 and 3.1.0 Preview 3.</span></span> <span data-ttu-id="283a1-123">`UseHttpsRedirection` został także zaktualizowany w tych wersjach, aby zrozumieć zarówno nowe, jak i stare zmienne.</span><span class="sxs-lookup"><span data-stu-id="283a1-123">`UseHttpsRedirection` was also updated in these releases to understand both the new and old variables.</span></span> <span data-ttu-id="283a1-124">ASP.NET Core 2. x nie zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="283a1-124">ASP.NET Core 2.x won't be updated.</span></span> <span data-ttu-id="283a1-125">W związku z tym przywraca poprzednie zachowanie, które jest domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="283a1-125">As a result, it reverts to the previous behavior of being disabled by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="283a1-126">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="283a1-126">Reason for change</span></span>

<span data-ttu-id="283a1-127">Ulepszona funkcja ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="283a1-127">Improved ASP.NET Core 3.0 functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="283a1-128">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="283a1-128">Recommended action</span></span>

<span data-ttu-id="283a1-129">Jeśli chcesz, aby wszyscy klienci korzystali z protokołu HTTPS, nie jest wymagana żadna akcja.</span><span class="sxs-lookup"><span data-stu-id="283a1-129">No action is required if you want all clients to use HTTPS.</span></span> <span data-ttu-id="283a1-130">Aby umożliwić niektórym klientom korzystanie z protokołu HTTP, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="283a1-130">To allow some clients to use HTTP, take one of the following steps:</span></span>

* <span data-ttu-id="283a1-131">Usuń wywołania `UseHttpsRedirection` i `UseHsts` z metody `Startup.Configure` projektu i ponownie Wdróż aplikację.</span><span class="sxs-lookup"><span data-stu-id="283a1-131">Remove the calls to `UseHttpsRedirection` and `UseHsts` from your project's `Startup.Configure` method, and redeploy the app.</span></span>
* <span data-ttu-id="283a1-132">W pliku *Web. config* Ustaw zmienną środowiskową `ASPNETCORE_HTTPS_PORT` na pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="283a1-132">In your *web.config* file, set the `ASPNETCORE_HTTPS_PORT` environment variable to an empty string.</span></span> <span data-ttu-id="283a1-133">Ta zmiana może wystąpić bezpośrednio na serwerze bez ponownego wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="283a1-133">This change can occur directly on the server without redeploying the app.</span></span> <span data-ttu-id="283a1-134">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="283a1-134">For example:</span></span>

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

<span data-ttu-id="283a1-135">`UseHttpsRedirection` nadal można:</span><span class="sxs-lookup"><span data-stu-id="283a1-135">`UseHttpsRedirection` can still be:</span></span>

* <span data-ttu-id="283a1-136">Aktywowane ręcznie w ASP.NET Core 2. x przez ustawienie zmiennej środowiskowej `ASPNETCORE_HTTPS_PORT` na odpowiedni numer portu (443 w większości scenariuszy produkcyjnych).</span><span class="sxs-lookup"><span data-stu-id="283a1-136">Activated manually in ASP.NET Core 2.x by setting the `ASPNETCORE_HTTPS_PORT` environment variable to the appropriate port number (443 in most production scenarios).</span></span>
* <span data-ttu-id="283a1-137">Zdezaktywowane w ASP.NET Core 3. x przez zdefiniowanie `ASPNETCORE_ANCM_HTTPS_PORT` z pustą wartością ciągu.</span><span class="sxs-lookup"><span data-stu-id="283a1-137">Deactivated in ASP.NET Core 3.x by defining `ASPNETCORE_ANCM_HTTPS_PORT` with an empty string value.</span></span> <span data-ttu-id="283a1-138">Ta wartość jest ustawiana w taki sam sposób jak w przypadku powyższego przykładu `ASPNETCORE_HTTPS_PORT`.</span><span class="sxs-lookup"><span data-stu-id="283a1-138">This value is set in the same fashion as the preceding `ASPNETCORE_HTTPS_PORT` example.</span></span>

<span data-ttu-id="283a1-139">Maszyny, na których uruchomiono ASP.NET Core aplikacje 3.0.0, powinny zainstalować środowisko uruchomieniowe ASP.NET Core 3.0.1 przed zainstalowaniem ASP.NET Core 3.1.0 Preview 3 ANCM.</span><span class="sxs-lookup"><span data-stu-id="283a1-139">Machines running ASP.NET Core 3.0.0 apps should install the ASP.NET Core 3.0.1 runtime before installing the ASP.NET Core 3.1.0 Preview 3 ANCM.</span></span> <span data-ttu-id="283a1-140">Dzięki temu `UseHttpsRedirection` nadal działać zgodnie z oczekiwaniami dla aplikacji ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="283a1-140">Doing so ensures that `UseHttpsRedirection` continues to operate as expected for the ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="283a1-141">W Azure App Service ANCM wdraża w osobnym harmonogramie z poziomu środowiska uruchomieniowego z powodu jego globalnego charakteru.</span><span class="sxs-lookup"><span data-stu-id="283a1-141">In Azure App Service, ANCM deploys on a separate schedule from the runtime because of its global nature.</span></span> <span data-ttu-id="283a1-142">ANCM został wdrożony na platformie Azure z tymi zmianami po wdrożeniu ASP.NET Core 3.0.1 i 3.1.0.</span><span class="sxs-lookup"><span data-stu-id="283a1-142">ANCM was deployed to Azure with these changes after ASP.NET Core 3.0.1 and 3.1.0 were deployed.</span></span>

#### <a name="category"></a><span data-ttu-id="283a1-143">Kategoria</span><span class="sxs-lookup"><span data-stu-id="283a1-143">Category</span></span>

<span data-ttu-id="283a1-144">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="283a1-144">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="283a1-145">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="283a1-145">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
