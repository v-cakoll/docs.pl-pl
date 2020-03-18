---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968244"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="07cac-101">HTTP: Zmiana przeglądarki SameSite wpływa na uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="07cac-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="07cac-102">Niektóre przeglądarki, takie jak Chrome i Firefox, dokonały `SameSite` przełomowych zmian w implementacjach plików cookie.</span><span class="sxs-lookup"><span data-stu-id="07cac-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="07cac-103">Zmiany mają wpływ na scenariusze uwierzytelniania zdalnego, takie jak OpenID Connect `SameSite=None`i WS-Federation, które muszą zrezygnować, wysyłając .</span><span class="sxs-lookup"><span data-stu-id="07cac-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="07cac-104">Jednak `SameSite=None` przerwy na iOS 12 i niektórych starszych wersjach innych przeglądarek.</span><span class="sxs-lookup"><span data-stu-id="07cac-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="07cac-105">Aplikacja musi wąchać te wersje i pominąć `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="07cac-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="07cac-106">Aby uzyskać dyskusję na ten temat, zobacz [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span><span class="sxs-lookup"><span data-stu-id="07cac-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="07cac-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="07cac-107">Version introduced</span></span>

<span data-ttu-id="07cac-108">3.1 Podgląd 1</span><span class="sxs-lookup"><span data-stu-id="07cac-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="07cac-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="07cac-109">Old behavior</span></span>

<span data-ttu-id="07cac-110">`SameSite`jest wersją roboczą standardowego rozszerzenia plików cookie HTTP z 2016 r.</span><span class="sxs-lookup"><span data-stu-id="07cac-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="07cac-111">Jego celem jest złagodzenie fałszerstwa żądań między witrynami (CSRF).</span><span class="sxs-lookup"><span data-stu-id="07cac-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="07cac-112">Pierwotnie został zaprojektowany jako funkcja, na którą serwery będą wybierać, dodając nowe parametry.</span><span class="sxs-lookup"><span data-stu-id="07cac-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="07cac-113">ASP.NET Core 2.0 dodał `SameSite`początkową obsługę .</span><span class="sxs-lookup"><span data-stu-id="07cac-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="07cac-114">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="07cac-114">New behavior</span></span>

<span data-ttu-id="07cac-115">Google zaproponowałnowy projekt standardu, który nie jest wstecznie kompatybilny.</span><span class="sxs-lookup"><span data-stu-id="07cac-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="07cac-116">Standard zmienia tryb domyślny `Lax` i dodaje `None` nowy wpis, aby zrezygnować. `Lax` wystarczy dla większości plików cookie aplikacji; jednak przerwy cross-site scenariuszy, takich jak OpenID Connect i WS-Federation logowania.</span><span class="sxs-lookup"><span data-stu-id="07cac-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="07cac-117">Większość logowania OAuth nie ma wpływu z powodu różnic w sposobie przepływu żądania.</span><span class="sxs-lookup"><span data-stu-id="07cac-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="07cac-118">Nowy `None` parametr powoduje problemy ze zgodnością z klientami, którzy zaimplementowali poprzedni standard wersji roboczej (na przykład iOS 12).</span><span class="sxs-lookup"><span data-stu-id="07cac-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="07cac-119">Chrome 80 będzie zawierać zmiany.</span><span class="sxs-lookup"><span data-stu-id="07cac-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="07cac-120">Zobacz [Aktualizacje tej samej witryny,](https://www.chromium.org/updates/same-site) aby uzyskać oś czasu uruchamiania produktu Chrome.</span><span class="sxs-lookup"><span data-stu-id="07cac-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="07cac-121">ASP.NET Core 3.1 został zaktualizowany w `SameSite` celu zaimplementowania nowego zachowania.</span><span class="sxs-lookup"><span data-stu-id="07cac-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="07cac-122">Aktualizacja ponownie definiuje zachowanie `SameSiteMode.None` do emitują `SameSite=None` i `SameSiteMode.Unspecified` dodaje nową `SameSite` wartość, aby pominąć atrybut.</span><span class="sxs-lookup"><span data-stu-id="07cac-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="07cac-123">Wszystkie interfejsy API `Unspecified`plików cookie są teraz domyślnie domyślnie używane, chociaż niektóre składniki, które używają plików cookie, ustawiły wartości bardziej szczegółowe dla ich scenariuszy, takich jak korelacja OpenID Connect i pliki cookie nonce.</span><span class="sxs-lookup"><span data-stu-id="07cac-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="07cac-124">Aby zapoznać się z innymi ostatnimi zmianami w tym obszarze, zobacz [HTTP: Niektóre ustawienia domyślne tej samej witryny zostały zmienione na Brak](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span><span class="sxs-lookup"><span data-stu-id="07cac-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="07cac-125">W ASP.NET Core 3.0 większość ustawień <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> domyślnych została zmieniona z (ale nadal przy użyciu poprzedniego standardu).</span><span class="sxs-lookup"><span data-stu-id="07cac-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="07cac-126">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="07cac-126">Reason for change</span></span>

<span data-ttu-id="07cac-127">Zmiany przeglądarki i specyfikacji zgodnie z opisem w poprzednim tekście.</span><span class="sxs-lookup"><span data-stu-id="07cac-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="07cac-128">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="07cac-128">Recommended action</span></span>

<span data-ttu-id="07cac-129">Aplikacje, które współdziałają z witrynami zdalnymi, na przykład za pośrednictwem logowania innych firm, muszą:</span><span class="sxs-lookup"><span data-stu-id="07cac-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="07cac-130">Przetestuj te scenariusze w wielu przeglądarkach.</span><span class="sxs-lookup"><span data-stu-id="07cac-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="07cac-131">Zastosuj ograniczenie wąchania przeglądarki cookie omówione w [pomocy technicznej starszych przeglądarek](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="07cac-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="07cac-132">Instrukcje dotyczące testowania i wąchania przeglądarki można znaleźć w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="07cac-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="07cac-133">Określ, czy dotyczy Cię</span><span class="sxs-lookup"><span data-stu-id="07cac-133">Determine if you're affected</span></span>

<span data-ttu-id="07cac-134">Przetestuj aplikację sieci web przy użyciu wersji klienta, która może zdecydować się na nowe zachowanie.</span><span class="sxs-lookup"><span data-stu-id="07cac-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="07cac-135">Chrome, Firefox i Microsoft Edge Chromium mają nowe flagi funkcji opt-in, które mogą być używane do testowania.</span><span class="sxs-lookup"><span data-stu-id="07cac-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="07cac-136">Sprawdź, czy aplikacja jest zgodna ze starszymi wersjami klienta po zastosowaniu poprawek, zwłaszcza przeglądarki Safari.</span><span class="sxs-lookup"><span data-stu-id="07cac-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="07cac-137">Aby uzyskać więcej informacji, zobacz [Obsługa starszych przeglądarek](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="07cac-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="07cac-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="07cac-138">Chrome</span></span>

<span data-ttu-id="07cac-139">Chrome 78 i nowsze dają mylące wyniki testów.</span><span class="sxs-lookup"><span data-stu-id="07cac-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="07cac-140">Te wersje mają tymczasowe ograniczenie w miejscu i pozwalają pliki cookie mniej niż dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="07cac-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="07cac-141">Po włączeniu odpowiednich flag testowych Chrome 76 i 77 dają dokładniejsze wyniki.</span><span class="sxs-lookup"><span data-stu-id="07cac-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="07cac-142">Aby przetestować nowe zachowanie, `chrome://flags/#same-site-by-default-cookies` przełącz do włączonego.</span><span class="sxs-lookup"><span data-stu-id="07cac-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="07cac-143">Chrome 75 i wcześniejsze są zgłaszane `None` do awarii z nowym ustawieniem.</span><span class="sxs-lookup"><span data-stu-id="07cac-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="07cac-144">Aby uzyskać więcej informacji, zobacz [Obsługa starszych przeglądarek](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="07cac-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="07cac-145">Google nie udostępnia starszych wersji Chrome.</span><span class="sxs-lookup"><span data-stu-id="07cac-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="07cac-146">Możesz jednak pobrać starsze wersje Chromium, które wystarczą do testowania.</span><span class="sxs-lookup"><span data-stu-id="07cac-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="07cac-147">Postępuj zgodnie z instrukcjami na [Pobierz Chromium](https://www.chromium.org/getting-involved/download-chromium).</span><span class="sxs-lookup"><span data-stu-id="07cac-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="07cac-148">Chrom 76 Win64</span><span class="sxs-lookup"><span data-stu-id="07cac-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="07cac-149">Chrom 74 Win64</span><span class="sxs-lookup"><span data-stu-id="07cac-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="07cac-150">Safari</span><span class="sxs-lookup"><span data-stu-id="07cac-150">Safari</span></span>

<span data-ttu-id="07cac-151">Safari 12 ściśle wdrożyło poprzedni projekt i `None` kończy się niepowodzeniem, jeśli widzi nową wartość w plikach cookie.</span><span class="sxs-lookup"><span data-stu-id="07cac-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="07cac-152">Należy tego unikać za pomocą kodu wąchania przeglądarki pokazanego w [pomocy technicznej starszych przeglądarek.](#support-older-browsers)</span><span class="sxs-lookup"><span data-stu-id="07cac-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="07cac-153">Upewnij się, że testujesz safari 12 i 13, a także loginy oparte na webkitze w stylu systemu operacyjnego przy użyciu biblioteki uwierzytelniania firmy Microsoft (MSAL), biblioteki uwierzytelniania usługi Active Directory (ADAL) lub niezależnie od tej biblioteki, której używasz.</span><span class="sxs-lookup"><span data-stu-id="07cac-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="07cac-154">Problem jest zależny od podstawowej wersji systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="07cac-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="07cac-155">Wiadomo, że oSX Mojave 10.14 i iOS 12 mają problemy ze zgodnością z nowym zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="07cac-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="07cac-156">Uaktualnienie do OSX Catalina 10.15 lub iOS 13 rozwiązuje problem.</span><span class="sxs-lookup"><span data-stu-id="07cac-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="07cac-157">Safari nie ma obecnie flagi opt-in do testowania nowego zachowania specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="07cac-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="07cac-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="07cac-158">Firefox</span></span>

<span data-ttu-id="07cac-159">Obsługa Firefoksa dla nowego standardu może być przetestowana `about:config` w wersji `network.cookie.sameSite.laxByDefault`68 i nowszej, decydując się na stronie z flagą funkcji .</span><span class="sxs-lookup"><span data-stu-id="07cac-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="07cac-160">W starszych wersjach Firefoksa nie zgłoszono żadnych problemów ze zgodnością.</span><span class="sxs-lookup"><span data-stu-id="07cac-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="07cac-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="07cac-161">Microsoft Edge</span></span>

<span data-ttu-id="07cac-162">Podczas gdy Microsoft `SameSite` Edge obsługuje stary standard, od wersji 44 nie miał żadnych problemów ze zgodnością z nowym standardem.</span><span class="sxs-lookup"><span data-stu-id="07cac-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="07cac-163">Chrom microsoft edge</span><span class="sxs-lookup"><span data-stu-id="07cac-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="07cac-164">Flaga funkcji `edge://flags/#same-site-by-default-cookies`to .</span><span class="sxs-lookup"><span data-stu-id="07cac-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="07cac-165">Podczas testowania systemu Microsoft Edge Chromium 78 nie zaobserwowano żadnych problemów ze zgodnością.</span><span class="sxs-lookup"><span data-stu-id="07cac-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="07cac-166">Elektronów</span><span class="sxs-lookup"><span data-stu-id="07cac-166">Electron</span></span>

<span data-ttu-id="07cac-167">Wersje Electron zawierają starsze wersje Chromium.</span><span class="sxs-lookup"><span data-stu-id="07cac-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="07cac-168">Na przykład wersja Electron używany przez Microsoft Teams jest Chromium 66, który wykazuje starsze zachowanie.</span><span class="sxs-lookup"><span data-stu-id="07cac-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="07cac-169">Wykonaj własne testy zgodności z wersją Electron, z używanej przez twój produkt.</span><span class="sxs-lookup"><span data-stu-id="07cac-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="07cac-170">Aby uzyskać więcej informacji, zobacz [Obsługa starszych przeglądarek](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="07cac-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="07cac-171">Obsługa starszych przeglądarek</span><span class="sxs-lookup"><span data-stu-id="07cac-171">Support older browsers</span></span>

<span data-ttu-id="07cac-172">Norma z `SameSite` 2016 r. nakazywała traktowanie nieznanych wartości jako `SameSite=Strict` wartości.</span><span class="sxs-lookup"><span data-stu-id="07cac-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="07cac-173">W związku z tym wszystkie starsze przeglądarki, które obsługują `SameSite` oryginalny standard `None`może pęknąć, gdy widzą właściwość o wartości .</span><span class="sxs-lookup"><span data-stu-id="07cac-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="07cac-174">Aplikacje sieci Web muszą zaimplementować wąchanie przeglądarki, jeśli zamierzają obsługiwać te stare przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="07cac-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="07cac-175">ASP.NET Core nie implementuje wąchania `User-Agent` przeglądarki, ponieważ wartości nagłówka żądania są wysoce niestabilne i zmieniają się co tydzień.</span><span class="sxs-lookup"><span data-stu-id="07cac-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="07cac-176">Zamiast tego punkt rozszerzenia w zasadach `User-Agent`plików cookie umożliwia dodanie logiki specyficznej dla danej opcji.</span><span class="sxs-lookup"><span data-stu-id="07cac-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="07cac-177">W *Startup.cs*dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="07cac-177">In *Startup.cs*, add the following code:</span></span>

```csharp
private void CheckSameSite(HttpContext httpContext, CookieOptions options)
{
    if (options.SameSite == SameSiteMode.None)
    {
        var userAgent = httpContext.Request.Headers["User-Agent"].ToString();
        // TODO: Use your User Agent library of choice here.
        if (/* UserAgent doesn't support new behavior */)
        {
            options.SameSite = SameSiteMode.Unspecified;
        }
    }
}

public void ConfigureServices(IServiceCollection services)
{
    services.Configure<CookiePolicyOptions>(options =>
    {
        options.MinimumSameSitePolicy = SameSiteMode.Unspecified;
        options.OnAppendCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
        options.OnDeleteCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
    });
}

public void Configure(IApplicationBuilder app)
{
    // Before UseAuthentication or anything else that writes cookies.
    app.UseCookiePolicy();

    app.UseAuthentication();
    // code omitted for brevity
}
```

##### <a name="opt-out-switches"></a><span data-ttu-id="07cac-178">Wyłączniki rezygnacji</span><span class="sxs-lookup"><span data-stu-id="07cac-178">Opt-out switches</span></span>

<span data-ttu-id="07cac-179">Przełącznik `Microsoft.AspNetCore.SuppressSameSiteNone` zgodności umożliwia tymczasowe zrezygnować z nowego ASP.NET podstawowego zachowania plików cookie.</span><span class="sxs-lookup"><span data-stu-id="07cac-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="07cac-180">Dodaj następujące JSON do pliku *runtimeconfig.template.json* w projekcie:</span><span class="sxs-lookup"><span data-stu-id="07cac-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a><span data-ttu-id="07cac-181">Inne wersje</span><span class="sxs-lookup"><span data-stu-id="07cac-181">Other Versions</span></span>

<span data-ttu-id="07cac-182">Powiązane `SameSite` poprawki są nadchodzące dla:</span><span class="sxs-lookup"><span data-stu-id="07cac-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="07cac-183">ASP.NET Rdzenie 2.1, 2.2 i 3.0</span><span class="sxs-lookup"><span data-stu-id="07cac-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="07cac-184">`Microsoft.Owin`4.1</span><span class="sxs-lookup"><span data-stu-id="07cac-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="07cac-185">`System.Web`(dla .NET Framework 4.7.2 i nowszych)</span><span class="sxs-lookup"><span data-stu-id="07cac-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="07cac-186">Kategoria</span><span class="sxs-lookup"><span data-stu-id="07cac-186">Category</span></span>

<span data-ttu-id="07cac-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="07cac-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="07cac-188">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="07cac-188">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieBuilder.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieOptions.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`
- `Overload:Microsoft.AspNetCore.Http.CookieBuilder.SameSite`
- `Overload:Microsoft.AspNetCore.Http.CookieOptions.SameSite`
- `T:Microsoft.AspNetCore.Http.SameSiteMode`
- `T:Microsoft.Net.Http.Headers.SameSiteMode`
- `Overload:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite`

-->
