---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937299"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a><span data-ttu-id="45e3b-101">Hosting: przekierowanie HTTPS włączone dla aplikacji pozaprocesowych usług IIS</span><span class="sxs-lookup"><span data-stu-id="45e3b-101">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>

<span data-ttu-id="45e3b-102">Wersja 13.0.19218.0 [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) do hostowania za pośrednictwem usług IIS poza procesem umożliwia istniejącą funkcję przekierowania HTTPS dla aplikacji ASP.NET Core 3.0 i 2.2.</span><span class="sxs-lookup"><span data-stu-id="45e3b-102">Version 13.0.19218.0 of the [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) for hosting via IIS out-of-process enables an existing HTTPS redirection feature for ASP.NET Core 3.0 and 2.2 apps.</span></span>

<span data-ttu-id="45e3b-103">Aby uzyskać do dyskusji, zobacz [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span><span class="sxs-lookup"><span data-stu-id="45e3b-103">For discussion, see [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="45e3b-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="45e3b-104">Version introduced</span></span>

<span data-ttu-id="45e3b-105">3.0</span><span class="sxs-lookup"><span data-stu-id="45e3b-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="45e3b-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="45e3b-106">Old behavior</span></span>

<span data-ttu-id="45e3b-107">ASP.NET Core 2.1 szablon projektu po raz pierwszy wprowadzono <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>obsługę metod pośredniczynienia HTTPS, takich jak i .</span><span class="sxs-lookup"><span data-stu-id="45e3b-107">The ASP.NET Core 2.1 project template first introduced support for HTTPS middleware methods like <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> and <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span></span> <span data-ttu-id="45e3b-108">Włączenie przekierowania HTTPS wymagało dodania konfiguracji, ponieważ aplikacje w programach nie używają domyślnego portu 443.</span><span class="sxs-lookup"><span data-stu-id="45e3b-108">Enabling HTTPS redirection required the addition of configuration, since apps in development don't use the default port of 443.</span></span> <span data-ttu-id="45e3b-109">[Protokół HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) jest aktywny tylko wtedy, gdy żądanie jest już przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="45e3b-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) is active only if the request is already using HTTPS.</span></span> <span data-ttu-id="45e3b-110">Localhost jest pomijany domyślnie.</span><span class="sxs-lookup"><span data-stu-id="45e3b-110">Localhost is skipped by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="45e3b-111">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="45e3b-111">New behavior</span></span>

<span data-ttu-id="45e3b-112">W ASP.NET Core 3.0 [ulepszono](https://github.com/dotnet/AspNetCore/pull/4685)scenariusz HTTPS iIS .</span><span class="sxs-lookup"><span data-stu-id="45e3b-112">In ASP.NET Core 3.0, the IIS HTTPS scenario was [enhanced](https://github.com/dotnet/AspNetCore/pull/4685).</span></span> <span data-ttu-id="45e3b-113">Dzięki ulepszeniu aplikacja może odnajdywać porty HTTPS serwera i domyślnie działać. `UseHttpsRedirection`</span><span class="sxs-lookup"><span data-stu-id="45e3b-113">With the enhancement, an app could discover the server's HTTPS ports and make `UseHttpsRedirection` work by default.</span></span> <span data-ttu-id="45e3b-114">Składnik w procesie dokonał odnajdywania portów za pomocą `IServerAddresses` funkcji, która ma wpływ tylko na ASP.NET aplikacji Core 3.0, ponieważ biblioteka w procesie jest wersjonowana przy pomocą struktury.</span><span class="sxs-lookup"><span data-stu-id="45e3b-114">The in-process component accomplished port discovery with the `IServerAddresses` feature, which only affects ASP.NET Core 3.0 apps because the in-process library is versioned with the framework.</span></span> <span data-ttu-id="45e3b-115">Składnik poza procesem zmieniony w celu `ASPNETCORE_HTTPS_PORT` automatycznego dodawania zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="45e3b-115">The out-of-process component changed to automatically add the `ASPNETCORE_HTTPS_PORT` environment variable.</span></span> <span data-ttu-id="45e3b-116">Ta zmiana dotyczyła zarówno ASP.NET aplikacji Core 2.2 i 3.0, ponieważ składnik pozaprocesowy jest współużytkowany globalnie.</span><span class="sxs-lookup"><span data-stu-id="45e3b-116">This change affected both ASP.NET Core 2.2 and 3.0 apps because the out-of-process component is shared globally.</span></span> <span data-ttu-id="45e3b-117">ASP.NET nie ma to wpływu na aplikacje Core 2.1, ponieważ domyślnie używają poprzedniej wersji programu ANCM.</span><span class="sxs-lookup"><span data-stu-id="45e3b-117">ASP.NET Core 2.1 apps aren't affected because they use a prior version of ANCM by default.</span></span>

<span data-ttu-id="45e3b-118">Poprzednie zachowanie zostało zmodyfikowane w ASP.NET Core 3.0.1 i 3.1.0 Preview 3, aby odwrócić zmiany zachowania w ASP.NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="45e3b-118">The preceding behavior was modified in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 to reverse the behavior changes in ASP.NET Core 2.x.</span></span> <span data-ttu-id="45e3b-119">Te zmiany dotyczą tylko aplikacji pozaprocesowych usług IIS.</span><span class="sxs-lookup"><span data-stu-id="45e3b-119">These changes only affect IIS out-of-process apps.</span></span>

<span data-ttu-id="45e3b-120">Jak opisano powyżej, instalacja ASP.NET Core 3.0.0 miała `UseHttpsRedirection` efekt uboczny aktywowania pośrednieniu w ASP.NET aplikacjach Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="45e3b-120">As detailed above, installing ASP.NET Core 3.0.0 had the side effect of also activating the `UseHttpsRedirection` middleware in ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="45e3b-121">Zmiana została wdrożena do ANCM w ASP.NET Core 3.0.1 i 3.1.0 Preview 3 w taki sposób, że ich instalacja nie ma już tego wpływu na ASP.NET aplikacji Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="45e3b-121">A change was made to ANCM in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 such that installing them no longer has this effect on ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="45e3b-122">Zmienna środowiskowa, `ASPNETCORE_HTTPS_PORT` którą ancm wypełnił w ASP.NET `ASPNETCORE_ANCM_HTTPS_PORT` Core 3.0.0, została zmieniona na w ASP.NET Core 3.0.1 i 3.1.0 Preview 3.</span><span class="sxs-lookup"><span data-stu-id="45e3b-122">The `ASPNETCORE_HTTPS_PORT` environment variable that ANCM populated in ASP.NET Core 3.0.0 was changed to `ASPNETCORE_ANCM_HTTPS_PORT` in ASP.NET Core 3.0.1 and 3.1.0 Preview 3.</span></span> <span data-ttu-id="45e3b-123">`UseHttpsRedirection`został również zaktualizowany w tych wersjach, aby zrozumieć zarówno nowe, jak i stare zmienne.</span><span class="sxs-lookup"><span data-stu-id="45e3b-123">`UseHttpsRedirection` was also updated in these releases to understand both the new and old variables.</span></span> <span data-ttu-id="45e3b-124">ASP.NET Core 2.x nie zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="45e3b-124">ASP.NET Core 2.x won't be updated.</span></span> <span data-ttu-id="45e3b-125">W rezultacie powraca do poprzedniego zachowania jest domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="45e3b-125">As a result, it reverts to the previous behavior of being disabled by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="45e3b-126">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="45e3b-126">Reason for change</span></span>

<span data-ttu-id="45e3b-127">Ulepszona funkcjonalność ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="45e3b-127">Improved ASP.NET Core 3.0 functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="45e3b-128">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="45e3b-128">Recommended action</span></span>

<span data-ttu-id="45e3b-129">Nie jest wymagana żadna akcja, jeśli chcesz, aby wszyscy klienci używali protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="45e3b-129">No action is required if you want all clients to use HTTPS.</span></span> <span data-ttu-id="45e3b-130">Aby zezwolić niektórym klientom na korzystanie z protokołu HTTP, należy wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="45e3b-130">To allow some clients to use HTTP, take one of the following steps:</span></span>

* <span data-ttu-id="45e3b-131">Usuń wywołania `UseHttpsRedirection` `UseHsts` do i z `Startup.Configure` metody projektu i ponownie wdrożyć aplikację.</span><span class="sxs-lookup"><span data-stu-id="45e3b-131">Remove the calls to `UseHttpsRedirection` and `UseHsts` from your project's `Startup.Configure` method, and redeploy the app.</span></span>
* <span data-ttu-id="45e3b-132">W pliku *web.config* ustaw `ASPNETCORE_HTTPS_PORT` zmienną środowiskową na pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="45e3b-132">In your *web.config* file, set the `ASPNETCORE_HTTPS_PORT` environment variable to an empty string.</span></span> <span data-ttu-id="45e3b-133">Ta zmiana może wystąpić bezpośrednio na serwerze bez ponownego wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45e3b-133">This change can occur directly on the server without redeploying the app.</span></span> <span data-ttu-id="45e3b-134">Przykład:</span><span class="sxs-lookup"><span data-stu-id="45e3b-134">For example:</span></span>

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

<span data-ttu-id="45e3b-135">`UseHttpsRedirection`nadal mogą być:</span><span class="sxs-lookup"><span data-stu-id="45e3b-135">`UseHttpsRedirection` can still be:</span></span>

* <span data-ttu-id="45e3b-136">Aktywowany ręcznie w ASP.NET Core 2.x, ustawiając zmienną `ASPNETCORE_HTTPS_PORT` środowiskową na odpowiedni numer portu (443 w większości scenariuszy produkcyjnych).</span><span class="sxs-lookup"><span data-stu-id="45e3b-136">Activated manually in ASP.NET Core 2.x by setting the `ASPNETCORE_HTTPS_PORT` environment variable to the appropriate port number (443 in most production scenarios).</span></span>
* <span data-ttu-id="45e3b-137">Dezaktywowany w ASP.NET Core `ASPNETCORE_ANCM_HTTPS_PORT` 3.x przez zdefiniowanie z pustą wartością ciągu.</span><span class="sxs-lookup"><span data-stu-id="45e3b-137">Deactivated in ASP.NET Core 3.x by defining `ASPNETCORE_ANCM_HTTPS_PORT` with an empty string value.</span></span> <span data-ttu-id="45e3b-138">Ta wartość jest ustawiona w taki `ASPNETCORE_HTTPS_PORT` sam sposób, jak w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="45e3b-138">This value is set in the same fashion as the preceding `ASPNETCORE_HTTPS_PORT` example.</span></span>

<span data-ttu-id="45e3b-139">Komputery z ASP.NET aplikacjami Core 3.0.0 powinny zainstalować ASP.NET core 3.0.1 przed zainstalowaniem ASP.NET Core 3.1.0 Preview 3 ANCM.</span><span class="sxs-lookup"><span data-stu-id="45e3b-139">Machines running ASP.NET Core 3.0.0 apps should install the ASP.NET Core 3.0.1 runtime before installing the ASP.NET Core 3.1.0 Preview 3 ANCM.</span></span> <span data-ttu-id="45e3b-140">W ten sposób `UseHttpsRedirection` zapewnia, że nadal działa zgodnie z oczekiwaniami dla ASP.NET aplikacji Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="45e3b-140">Doing so ensures that `UseHttpsRedirection` continues to operate as expected for the ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="45e3b-141">W usłudze Azure App Service ancm wdraża na oddzielnym harmonogramie od czasu wykonywania ze względu na jego globalny charakter.</span><span class="sxs-lookup"><span data-stu-id="45e3b-141">In Azure App Service, ANCM deploys on a separate schedule from the runtime because of its global nature.</span></span> <span data-ttu-id="45e3b-142">Ancm został wdrożony na platformie Azure z tych zmian po ASP.NET Core 3.0.1 i 3.1.0 zostały wdrożone.</span><span class="sxs-lookup"><span data-stu-id="45e3b-142">ANCM was deployed to Azure with these changes after ASP.NET Core 3.0.1 and 3.1.0 were deployed.</span></span>

#### <a name="category"></a><span data-ttu-id="45e3b-143">Kategoria</span><span class="sxs-lookup"><span data-stu-id="45e3b-143">Category</span></span>

<span data-ttu-id="45e3b-144">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="45e3b-144">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="45e3b-145">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="45e3b-145">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
