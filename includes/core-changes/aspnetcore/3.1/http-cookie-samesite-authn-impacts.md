---
ms.openlocfilehash: b0d093cc30a09b3248cc57a521b386bf581b5451
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552159"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="5d137-101">HTTP: zmiana SameSite w przeglądarce wpływa na uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="5d137-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="5d137-102">Niektóre przeglądarki, takie jak Chrome i Firefox, wprowadzają istotne zmiany w implementacjach `SameSite` plików cookie.</span><span class="sxs-lookup"><span data-stu-id="5d137-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="5d137-103">Zmiany mają wpływ na scenariusze uwierzytelniania zdalnego, takie jak OpenID Connect Connect i WS-Federation, które muszą zrezygnować z wysyłania `SameSite=None`.</span><span class="sxs-lookup"><span data-stu-id="5d137-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="5d137-104">Jednak `SameSite=None` przerwy w systemie iOS 12 i starszych wersjach innych przeglądarek.</span><span class="sxs-lookup"><span data-stu-id="5d137-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="5d137-105">Aplikacja musi wyrównać te wersje i pominąć `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="5d137-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="5d137-106">Aby zapoznać się z omówieniem tego problemu, zobacz [ASPNET/AspNetCore # 14996](https://github.com/aspnet/AspNetCore/issues/14996).</span><span class="sxs-lookup"><span data-stu-id="5d137-106">For discussion on this issue, see [aspnet/AspNetCore#14996](https://github.com/aspnet/AspNetCore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5d137-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="5d137-107">Version introduced</span></span>

<span data-ttu-id="5d137-108">3,1 wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="5d137-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5d137-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="5d137-109">Old behavior</span></span>

<span data-ttu-id="5d137-110">`SameSite` to 2016 standardowe rozszerzenie do plików cookie protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5d137-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="5d137-111">Ma ona na celu ograniczenie fałszerstwa żądań między lokacjami (CSRF).</span><span class="sxs-lookup"><span data-stu-id="5d137-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="5d137-112">Zostało to pierwotnie zaprojektowane jako funkcja, do której serwery będą dołączane, dodając nowe parametry.</span><span class="sxs-lookup"><span data-stu-id="5d137-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="5d137-113">ASP.NET Core 2,0 dodano wstępną obsługę `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="5d137-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5d137-114">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="5d137-114">New behavior</span></span>

<span data-ttu-id="5d137-115">Firma Google zaproponowała nowy projekt Standard, który nie jest zgodny z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="5d137-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="5d137-116">Standard zmienia domyślny tryb na `Lax` i dodaje nowy wpis, `None` wycofać. `Lax` wystarczające dla większości plików cookie aplikacji; spowoduje to jednak przerwanie scenariuszy między lokacjami, takich jak OpenID Connect Connect i logowanie do usługi WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="5d137-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="5d137-117">Większość logowań uwierzytelniania OAuth nie ma wpływu z powodu różnic w przepływie żądań.</span><span class="sxs-lookup"><span data-stu-id="5d137-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="5d137-118">Nowy parametr `None` powoduje problemy ze zgodnością z klientami, którzy zaimplementowali poprzednią wersję standardową (na przykład system iOS 12).</span><span class="sxs-lookup"><span data-stu-id="5d137-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="5d137-119">Program Chrome 80 będzie zawierać zmiany.</span><span class="sxs-lookup"><span data-stu-id="5d137-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="5d137-120">Zobacz [SameSite Updates](https://www.chromium.org/updates/same-site) dla osi czasu uruchamiania produktu Chrome.</span><span class="sxs-lookup"><span data-stu-id="5d137-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="5d137-121">ASP.NET Core 3,1 został zaktualizowany w celu zaimplementowania nowego zachowania `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="5d137-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="5d137-122">Aktualizacja ponownie definiuje zachowanie `SameSiteMode.None`, aby emitować `SameSite=None` i dodaje nową wartość `SameSiteMode.Unspecified`, aby pominąć atrybut `SameSite`.</span><span class="sxs-lookup"><span data-stu-id="5d137-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="5d137-123">Wszystkie interfejsy API plików cookie teraz domyślnie `Unspecified`, chociaż niektóre składniki używające plików cookie ustawiają wartości bardziej specyficzne dla ich scenariuszy, takich jak OpenID Connect Connect korelacji i pliki cookie nonce.</span><span class="sxs-lookup"><span data-stu-id="5d137-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="5d137-124">Aby poznać inne ostatnie zmiany w tym obszarze, zobacz [http: niektóre pliki cookie SameSite domyślnie zmienione na none](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span><span class="sxs-lookup"><span data-stu-id="5d137-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="5d137-125">W ASP.NET Core 3,0 większość wartości domyślnych została zmieniona z <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> na <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (ale nadal używa wcześniejszego standardu).</span><span class="sxs-lookup"><span data-stu-id="5d137-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5d137-126">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="5d137-126">Reason for change</span></span>

<span data-ttu-id="5d137-127">Zmiany w przeglądarce i specyfikacji, jak opisano w poprzednim tekście.</span><span class="sxs-lookup"><span data-stu-id="5d137-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5d137-128">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="5d137-128">Recommended action</span></span>

<span data-ttu-id="5d137-129">Aplikacje, które współdziałają z witrynami zdalnymi, na przykład za pomocą logowania innych firm, muszą:</span><span class="sxs-lookup"><span data-stu-id="5d137-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="5d137-130">Przetestuj te scenariusze w wielu przeglądarkach.</span><span class="sxs-lookup"><span data-stu-id="5d137-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="5d137-131">Zastosuj zasady plików cookie Rozwiązywanie problemów z przeglądarką, omówione w sekcji [Obsługa starszych przeglądarek](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="5d137-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="5d137-132">Instrukcje testowania i wykrywania przeglądarki znajdują się w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="5d137-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="5d137-133">Ustalanie, czy ma to dotyczyć</span><span class="sxs-lookup"><span data-stu-id="5d137-133">Determine if you're affected</span></span>

<span data-ttu-id="5d137-134">Przetestuj aplikację sieci Web przy użyciu wersji klienta, która może zrezygnować z nowego zachowania.</span><span class="sxs-lookup"><span data-stu-id="5d137-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="5d137-135">Przeglądarki Chrome, Firefox i Microsoft Edge chrom All mają nowe flagi funkcji opt, których można użyć do testowania.</span><span class="sxs-lookup"><span data-stu-id="5d137-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="5d137-136">Sprawdź, czy aplikacja jest zgodna ze starszymi wersjami klienta po zastosowaniu poprawek, szczególnie Safari.</span><span class="sxs-lookup"><span data-stu-id="5d137-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="5d137-137">Aby uzyskać więcej informacji, zobacz [Obsługa starszych przeglądarek](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="5d137-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="5d137-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="5d137-138">Chrome</span></span>

<span data-ttu-id="5d137-139">Przeglądarki Chrome 78 i nowsze zwracają błędne wyniki testu.</span><span class="sxs-lookup"><span data-stu-id="5d137-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="5d137-140">Te wersje mają tymczasowe środki zaradcze i zezwalają na pliki cookie mniejsze niż dwie minuty.</span><span class="sxs-lookup"><span data-stu-id="5d137-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="5d137-141">Po włączeniu odpowiednich flag testów, Chrome 76 i 77 dają dokładniejsze wyniki.</span><span class="sxs-lookup"><span data-stu-id="5d137-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="5d137-142">Aby przetestować nowe zachowanie, przełącz `chrome://flags/#same-site-by-default-cookies` na włączone.</span><span class="sxs-lookup"><span data-stu-id="5d137-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="5d137-143">Program Chrome 75 i jego wcześniejsze wersje zostały zgłoszone w celu niepowodzenia z nowym ustawieniem `None`.</span><span class="sxs-lookup"><span data-stu-id="5d137-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="5d137-144">Aby uzyskać więcej informacji, zobacz [Obsługa starszych przeglądarek](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="5d137-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="5d137-145">Firma Google nie udostępnia starszych wersji programu Chrome.</span><span class="sxs-lookup"><span data-stu-id="5d137-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="5d137-146">Można jednak pobrać starsze wersje chromu, które będą wystarczające do testowania.</span><span class="sxs-lookup"><span data-stu-id="5d137-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="5d137-147">Postępuj zgodnie z instrukcjami podanymi w [pobraniu chromu](https://www.chromium.org/getting-involved/download-chromium).</span><span class="sxs-lookup"><span data-stu-id="5d137-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="5d137-148">Chrom 76 Win64</span><span class="sxs-lookup"><span data-stu-id="5d137-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="5d137-149">Chrom 74 Win64</span><span class="sxs-lookup"><span data-stu-id="5d137-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="5d137-150">Safari</span><span class="sxs-lookup"><span data-stu-id="5d137-150">Safari</span></span>

<span data-ttu-id="5d137-151">Przeglądarka Safari 12 ściśle wdrożyła poprzednią wersję roboczą i kończy się niepowodzeniem, jeśli zobaczy nową wartość `None` w plikach cookie.</span><span class="sxs-lookup"><span data-stu-id="5d137-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="5d137-152">Należy to uniknąć za pośrednictwem kodu wykrywania przeglądarki wyświetlanego w ramach [obsługi starszych przeglądarek](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="5d137-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="5d137-153">Zadbaj o przetestowanie przeglądarki Safari 12 i 13 oraz WebKit logowania w stylu systemu operacyjnego przy użyciu biblioteki uwierzytelniania firmy Microsoft (MSAL), Active Directory Authentication Library (ADAL) lub dowolnej używanej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5d137-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="5d137-154">Problem jest zależny od podstawowej wersji systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="5d137-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="5d137-155">OSX Mojave 10,14 i iOS 12 są znane jako problemy ze zgodnością z nowym zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="5d137-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="5d137-156">Uaktualnienie do OSX Catalina 10,15 lub iOS 13 rozwiązuje problem.</span><span class="sxs-lookup"><span data-stu-id="5d137-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="5d137-157">Przeglądarka Safari nie ma obecnie flagi zgody na testowanie nowego zachowania specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="5d137-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="5d137-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="5d137-158">Firefox</span></span>

<span data-ttu-id="5d137-159">Obsługę programu Firefox dla nowego standardu można przetestować w wersji 68 i nowszych, wybierając ją na stronie `about:config` z flagą funkcji `network.cookie.sameSite.laxByDefault`.</span><span class="sxs-lookup"><span data-stu-id="5d137-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="5d137-160">W starszych wersjach programu Firefox nie zgłoszono żadnych problemów ze zgodnością.</span><span class="sxs-lookup"><span data-stu-id="5d137-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="5d137-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="5d137-161">Microsoft Edge</span></span>

<span data-ttu-id="5d137-162">Podczas gdy program Microsoft Edge obsługuje stary Standard `SameSite` w wersji 44, nie miał żadnych problemów ze zgodnością z nowym standardem.</span><span class="sxs-lookup"><span data-stu-id="5d137-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="5d137-163">Microsoft Edge — chrom</span><span class="sxs-lookup"><span data-stu-id="5d137-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="5d137-164">Flaga funkcji jest `edge://flags/#same-site-by-default-cookies`.</span><span class="sxs-lookup"><span data-stu-id="5d137-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="5d137-165">Podczas testowania za pomocą programu Microsoft Edge chrom 78 nie zaobserwowano żadnych problemów ze zgodnością.</span><span class="sxs-lookup"><span data-stu-id="5d137-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="5d137-166">Elektron</span><span class="sxs-lookup"><span data-stu-id="5d137-166">Electron</span></span>

<span data-ttu-id="5d137-167">Wersje elektronów obejmują starsze wersje chromu.</span><span class="sxs-lookup"><span data-stu-id="5d137-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="5d137-168">Na przykład wersja elektronów używana przez program Microsoft teams to chrom 66, który wykazuje starsze zachowanie.</span><span class="sxs-lookup"><span data-stu-id="5d137-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="5d137-169">Wykonaj własne testy zgodności z wersją elektronów używaną przez produkt.</span><span class="sxs-lookup"><span data-stu-id="5d137-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="5d137-170">Aby uzyskać więcej informacji, zobacz [Obsługa starszych przeglądarek](#support-older-browsers).</span><span class="sxs-lookup"><span data-stu-id="5d137-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="5d137-171">Obsługa starszych przeglądarek</span><span class="sxs-lookup"><span data-stu-id="5d137-171">Support older browsers</span></span>

<span data-ttu-id="5d137-172">W standardzie 2016 `SameSite` jest przyznany, że nieznane wartości są traktowane jako `SameSite=Strict` wartości.</span><span class="sxs-lookup"><span data-stu-id="5d137-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="5d137-173">W związku z tym wszystkie starsze przeglądarki, które obsługują oryginalny Standard, mogą zostać przerwane, gdy zobaczysz Właściwość `SameSite` o wartości `None`.</span><span class="sxs-lookup"><span data-stu-id="5d137-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="5d137-174">Aplikacje sieci Web muszą implementować wykrywanie przeglądarki, jeśli zamierzają obsługiwać te stare przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="5d137-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="5d137-175">ASP.NET Core nie implementuje wykrywania przeglądarki, ponieważ wartości nagłówka żądania `User-Agent` są bardzo niestabilne i zmieniają się co tydzień.</span><span class="sxs-lookup"><span data-stu-id="5d137-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="5d137-176">Zamiast tego punkt rozszerzenia w zasadach dotyczących plików cookie umożliwia dodawanie logiki specyficznej dla `User-Agent`.</span><span class="sxs-lookup"><span data-stu-id="5d137-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="5d137-177">W *Startup.cs*Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="5d137-177">In *Startup.cs*, add the following code:</span></span>

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

##### <a name="opt-out-switches"></a><span data-ttu-id="5d137-178">Wycofaj przełączniki</span><span class="sxs-lookup"><span data-stu-id="5d137-178">Opt-out switches</span></span>

<span data-ttu-id="5d137-179">Przełącznik zgodności `Microsoft.AspNetCore.SuppressSameSiteNone` umożliwia tymczasowe rezygnację z nowych zachowań plików cookie ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5d137-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="5d137-180">Dodaj następujący kod JSON do pliku *runtimeconfig. Template. JSON* w projekcie:</span><span class="sxs-lookup"><span data-stu-id="5d137-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{ 
  "configProperties": { 
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true" 
  } 
}
```

##### <a name="other-versions"></a><span data-ttu-id="5d137-181">Inne wersje</span><span class="sxs-lookup"><span data-stu-id="5d137-181">Other Versions</span></span>

<span data-ttu-id="5d137-182">Powiązane poprawki `SameSite` są nachodzące dla:</span><span class="sxs-lookup"><span data-stu-id="5d137-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="5d137-183">ASP.NET Core 2,1, 2,2 i 3,0</span><span class="sxs-lookup"><span data-stu-id="5d137-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="5d137-184">`Microsoft.Owin` 4,1</span><span class="sxs-lookup"><span data-stu-id="5d137-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="5d137-185">`System.Web` (dla .NET Framework 4.7.2 i nowszych)</span><span class="sxs-lookup"><span data-stu-id="5d137-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="5d137-186">Kategoria</span><span class="sxs-lookup"><span data-stu-id="5d137-186">Category</span></span>

<span data-ttu-id="5d137-187">Platforma ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5d137-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5d137-188">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="5d137-188">Affected APIs</span></span>

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
