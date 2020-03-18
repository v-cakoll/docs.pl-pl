---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968244"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a>HTTP: Zmiana przeglądarki SameSite wpływa na uwierzytelnianie

Niektóre przeglądarki, takie jak Chrome i Firefox, dokonały `SameSite` przełomowych zmian w implementacjach plików cookie. Zmiany mają wpływ na scenariusze uwierzytelniania zdalnego, takie jak OpenID Connect `SameSite=None`i WS-Federation, które muszą zrezygnować, wysyłając . Jednak `SameSite=None` przerwy na iOS 12 i niektórych starszych wersjach innych przeglądarek. Aplikacja musi wąchać te wersje i pominąć `SameSite`.

Aby uzyskać dyskusję na ten temat, zobacz [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.1 Podgląd 1

#### <a name="old-behavior"></a>Stare zachowanie

`SameSite`jest wersją roboczą standardowego rozszerzenia plików cookie HTTP z 2016 r. Jego celem jest złagodzenie fałszerstwa żądań między witrynami (CSRF). Pierwotnie został zaprojektowany jako funkcja, na którą serwery będą wybierać, dodając nowe parametry. ASP.NET Core 2.0 dodał `SameSite`początkową obsługę .

#### <a name="new-behavior"></a>Nowe zachowanie

Google zaproponowałnowy projekt standardu, który nie jest wstecznie kompatybilny. Standard zmienia tryb domyślny `Lax` i dodaje `None` nowy wpis, aby zrezygnować. `Lax` wystarczy dla większości plików cookie aplikacji; jednak przerwy cross-site scenariuszy, takich jak OpenID Connect i WS-Federation logowania. Większość logowania OAuth nie ma wpływu z powodu różnic w sposobie przepływu żądania. Nowy `None` parametr powoduje problemy ze zgodnością z klientami, którzy zaimplementowali poprzedni standard wersji roboczej (na przykład iOS 12). Chrome 80 będzie zawierać zmiany. Zobacz [Aktualizacje tej samej witryny,](https://www.chromium.org/updates/same-site) aby uzyskać oś czasu uruchamiania produktu Chrome.

ASP.NET Core 3.1 został zaktualizowany w `SameSite` celu zaimplementowania nowego zachowania. Aktualizacja ponownie definiuje zachowanie `SameSiteMode.None` do emitują `SameSite=None` i `SameSiteMode.Unspecified` dodaje nową `SameSite` wartość, aby pominąć atrybut. Wszystkie interfejsy API `Unspecified`plików cookie są teraz domyślnie domyślnie używane, chociaż niektóre składniki, które używają plików cookie, ustawiły wartości bardziej szczegółowe dla ich scenariuszy, takich jak korelacja OpenID Connect i pliki cookie nonce.

Aby zapoznać się z innymi ostatnimi zmianami w tym obszarze, zobacz [HTTP: Niektóre ustawienia domyślne tej samej witryny zostały zmienione na Brak](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none). W ASP.NET Core 3.0 większość ustawień <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> domyślnych została zmieniona z (ale nadal przy użyciu poprzedniego standardu).

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zmiany przeglądarki i specyfikacji zgodnie z opisem w poprzednim tekście.

#### <a name="recommended-action"></a>Zalecana akcja

Aplikacje, które współdziałają z witrynami zdalnymi, na przykład za pośrednictwem logowania innych firm, muszą:

* Przetestuj te scenariusze w wielu przeglądarkach.
* Zastosuj ograniczenie wąchania przeglądarki cookie omówione w [pomocy technicznej starszych przeglądarek](#support-older-browsers).

Instrukcje dotyczące testowania i wąchania przeglądarki można znaleźć w poniższej sekcji.

##### <a name="determine-if-youre-affected"></a>Określ, czy dotyczy Cię

Przetestuj aplikację sieci web przy użyciu wersji klienta, która może zdecydować się na nowe zachowanie. Chrome, Firefox i Microsoft Edge Chromium mają nowe flagi funkcji opt-in, które mogą być używane do testowania. Sprawdź, czy aplikacja jest zgodna ze starszymi wersjami klienta po zastosowaniu poprawek, zwłaszcza przeglądarki Safari. Aby uzyskać więcej informacji, zobacz [Obsługa starszych przeglądarek](#support-older-browsers).

##### <a name="chrome"></a>Chrome

Chrome 78 i nowsze dają mylące wyniki testów. Te wersje mają tymczasowe ograniczenie w miejscu i pozwalają pliki cookie mniej niż dwie minuty. Po włączeniu odpowiednich flag testowych Chrome 76 i 77 dają dokładniejsze wyniki. Aby przetestować nowe zachowanie, `chrome://flags/#same-site-by-default-cookies` przełącz do włączonego. Chrome 75 i wcześniejsze są zgłaszane `None` do awarii z nowym ustawieniem. Aby uzyskać więcej informacji, zobacz [Obsługa starszych przeglądarek](#support-older-browsers).

Google nie udostępnia starszych wersji Chrome. Możesz jednak pobrać starsze wersje Chromium, które wystarczą do testowania. Postępuj zgodnie z instrukcjami na [Pobierz Chromium](https://www.chromium.org/getting-involved/download-chromium).

* [Chrom 76 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [Chrom 74 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a>Safari

Safari 12 ściśle wdrożyło poprzedni projekt i `None` kończy się niepowodzeniem, jeśli widzi nową wartość w plikach cookie. Należy tego unikać za pomocą kodu wąchania przeglądarki pokazanego w [pomocy technicznej starszych przeglądarek.](#support-older-browsers) Upewnij się, że testujesz safari 12 i 13, a także loginy oparte na webkitze w stylu systemu operacyjnego przy użyciu biblioteki uwierzytelniania firmy Microsoft (MSAL), biblioteki uwierzytelniania usługi Active Directory (ADAL) lub niezależnie od tej biblioteki, której używasz. Problem jest zależny od podstawowej wersji systemu operacyjnego. Wiadomo, że oSX Mojave 10.14 i iOS 12 mają problemy ze zgodnością z nowym zachowaniem. Uaktualnienie do OSX Catalina 10.15 lub iOS 13 rozwiązuje problem. Safari nie ma obecnie flagi opt-in do testowania nowego zachowania specyfikacji.

##### <a name="firefox"></a>Firefox

Obsługa Firefoksa dla nowego standardu może być przetestowana `about:config` w wersji `network.cookie.sameSite.laxByDefault`68 i nowszej, decydując się na stronie z flagą funkcji . W starszych wersjach Firefoksa nie zgłoszono żadnych problemów ze zgodnością.

##### <a name="microsoft-edge"></a>Microsoft Edge

Podczas gdy Microsoft `SameSite` Edge obsługuje stary standard, od wersji 44 nie miał żadnych problemów ze zgodnością z nowym standardem.

##### <a name="microsoft-edge-chromium"></a>Chrom microsoft edge

Flaga funkcji `edge://flags/#same-site-by-default-cookies`to . Podczas testowania systemu Microsoft Edge Chromium 78 nie zaobserwowano żadnych problemów ze zgodnością.

##### <a name="electron"></a>Elektronów

Wersje Electron zawierają starsze wersje Chromium. Na przykład wersja Electron używany przez Microsoft Teams jest Chromium 66, który wykazuje starsze zachowanie. Wykonaj własne testy zgodności z wersją Electron, z używanej przez twój produkt. Aby uzyskać więcej informacji, zobacz [Obsługa starszych przeglądarek](#support-older-browsers).

##### <a name="support-older-browsers"></a>Obsługa starszych przeglądarek

Norma z `SameSite` 2016 r. nakazywała traktowanie nieznanych wartości jako `SameSite=Strict` wartości. W związku z tym wszystkie starsze przeglądarki, które obsługują `SameSite` oryginalny standard `None`może pęknąć, gdy widzą właściwość o wartości . Aplikacje sieci Web muszą zaimplementować wąchanie przeglądarki, jeśli zamierzają obsługiwać te stare przeglądarki. ASP.NET Core nie implementuje wąchania `User-Agent` przeglądarki, ponieważ wartości nagłówka żądania są wysoce niestabilne i zmieniają się co tydzień. Zamiast tego punkt rozszerzenia w zasadach `User-Agent`plików cookie umożliwia dodanie logiki specyficznej dla danej opcji.

W *Startup.cs*dodaj następujący kod:

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

##### <a name="opt-out-switches"></a>Wyłączniki rezygnacji

Przełącznik `Microsoft.AspNetCore.SuppressSameSiteNone` zgodności umożliwia tymczasowe zrezygnować z nowego ASP.NET podstawowego zachowania plików cookie. Dodaj następujące JSON do pliku *runtimeconfig.template.json* w projekcie:

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a>Inne wersje

Powiązane `SameSite` poprawki są nadchodzące dla:

* ASP.NET Rdzenie 2.1, 2.2 i 3.0
* `Microsoft.Owin`4.1
* `System.Web`(dla .NET Framework 4.7.2 i nowszych)

#### <a name="category"></a>Kategoria

ASP.NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

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
