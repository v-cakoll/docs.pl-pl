---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968244"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a>HTTP: zmiana SameSite w przeglądarce wpływa na uwierzytelnianie

Niektóre przeglądarki, takie jak Chrome i Firefox, wprowadzają istotne zmiany w implementacjach `SameSite` plików cookie. Zmiany mają wpływ na scenariusze uwierzytelniania zdalnego, takie jak OpenID Connect Connect i WS-Federation, które muszą zrezygnować z `SameSite=None`wysyłania. Jednak `SameSite=None` przerwy w systemie iOS 12 i starszych wersjach innych przeglądarek. Aplikacja musi wyrównać te wersje i pominąć `SameSite`.

Aby zapoznać się z omówieniem tego problemu, zobacz [dotnet/aspnetcore # 14996](https://github.com/dotnet/aspnetcore/issues/14996).

#### <a name="version-introduced"></a>Wprowadzona wersja

3,1 wersja zapoznawcza 1

#### <a name="old-behavior"></a>Stare zachowanie

`SameSite`jest 2016m standardowym rozszerzeniem plików cookie protokołu HTTP. Ma ona na celu ograniczenie fałszerstwa żądań między lokacjami (CSRF). Zostało to pierwotnie zaprojektowane jako funkcja, do której serwery będą dołączane, dodając nowe parametry. ASP.NET Core 2,0 dodano wstępną obsługę `SameSite`elementu.

#### <a name="new-behavior"></a>Nowe zachowanie

Firma Google zaproponowała nowy projekt Standard, który nie jest zgodny z poprzednimi wersjami. Standard zmienia tryb domyślny na `Lax` i dodaje nowy wpis `None` , aby zrezygnować. `Lax` wystarczające dla większości plików cookie aplikacji; spowoduje to jednak przerwanie scenariuszy między lokacjami, takich jak OpenID Connect Connect i logowanie do usługi WS-Federation. Większość logowań uwierzytelniania OAuth nie ma wpływu z powodu różnic w przepływie żądań. Nowy `None` parametr powoduje problemy ze zgodnością klientów, którzy zaimplementowali poprzednią wersję standardową (na przykład system iOS 12). Program Chrome 80 będzie zawierać zmiany. Zobacz [SameSite Updates](https://www.chromium.org/updates/same-site) dla osi czasu uruchamiania produktu Chrome.

ASP.NET Core 3,1 został zaktualizowany, aby zaimplementować nowe `SameSite` zachowanie. `SameSiteMode.None` Aktualizacja ponownie definiuje zachowanie programu, aby emitować `SameSite=None` i dodaje nową wartość `SameSiteMode.Unspecified` w celu pominięcia `SameSite` atrybutu. Wszystkie interfejsy API plików cookie teraz `Unspecified`domyślnie to, chociaż niektóre składniki używające plików cookie ustawiają wartości bardziej specyficzne dla ich scenariuszy, takich jak OpenID Connect Connect korelacji i pliki cookie nonce.

Aby poznać inne ostatnie zmiany w tym obszarze, zobacz [http: niektóre pliki cookie SameSite domyślnie zmienione na none](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none). W ASP.NET Core 3,0 większość wartości domyślnych została zmieniona z <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> na <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (ale nadal korzystasz z wcześniejszego standardu).

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zmiany w przeglądarce i specyfikacji, jak opisano w poprzednim tekście.

#### <a name="recommended-action"></a>Zalecana akcja

Aplikacje, które współdziałają z witrynami zdalnymi, na przykład za pomocą logowania innych firm, muszą:

* Przetestuj te scenariusze w wielu przeglądarkach.
* Zastosuj zasady plików cookie Rozwiązywanie problemów z przeglądarką, omówione w sekcji [Obsługa starszych przeglądarek](#support-older-browsers).

Instrukcje testowania i wykrywania przeglądarki znajdują się w poniższej sekcji.

##### <a name="determine-if-youre-affected"></a>Ustalanie, czy ma to dotyczyć

Przetestuj aplikację sieci Web przy użyciu wersji klienta, która może zrezygnować z nowego zachowania. Przeglądarki Chrome, Firefox i Microsoft Edge chrom All mają nowe flagi funkcji opt, których można użyć do testowania. Sprawdź, czy aplikacja jest zgodna ze starszymi wersjami klienta po zastosowaniu poprawek, szczególnie Safari. Aby uzyskać więcej informacji, zobacz [Obsługa starszych przeglądarek](#support-older-browsers).

##### <a name="chrome"></a>Chrome

Przeglądarki Chrome 78 i nowsze zwracają błędne wyniki testu. Te wersje mają tymczasowe środki zaradcze i zezwalają na pliki cookie mniejsze niż dwie minuty. Po włączeniu odpowiednich flag testów, Chrome 76 i 77 dają dokładniejsze wyniki. Aby przetestować nowe zachowanie, przełącz `chrome://flags/#same-site-by-default-cookies` na włączone. Dla programu Chrome 75 i wcześniejszych zostały zgłoszone niepowodzenie `None` przy użyciu nowego ustawienia. Aby uzyskać więcej informacji, zobacz [Obsługa starszych przeglądarek](#support-older-browsers).

Firma Google nie udostępnia starszych wersji programu Chrome. Można jednak pobrać starsze wersje chromu, które będą wystarczające do testowania. Postępuj zgodnie z instrukcjami podanymi w [pobraniu chromu](https://www.chromium.org/getting-involved/download-chromium).

* [Chrom 76 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [Chrom 74 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a>Safari

Przeglądarka Safari 12 ściśle wdrożyła poprzednią wersję roboczą i kończy się `None` niepowodzeniem, jeśli zobaczy nową wartość w plikach cookie. Należy to uniknąć za pośrednictwem kodu wykrywania przeglądarki wyświetlanego w ramach [obsługi starszych przeglądarek](#support-older-browsers). Zadbaj o przetestowanie przeglądarki Safari 12 i 13 oraz WebKit logowania w stylu systemu operacyjnego przy użyciu biblioteki uwierzytelniania firmy Microsoft (MSAL), Active Directory Authentication Library (ADAL) lub dowolnej używanej biblioteki. Problem jest zależny od podstawowej wersji systemu operacyjnego. OSX Mojave 10,14 i iOS 12 są znane jako problemy ze zgodnością z nowym zachowaniem. Uaktualnienie do OSX Catalina 10,15 lub iOS 13 rozwiązuje problem. Przeglądarka Safari nie ma obecnie flagi zgody na testowanie nowego zachowania specyfikacji.

##### <a name="firefox"></a>Firefox

Obsługę programu Firefox dla nowego standardu można przetestować w wersji 68 i nowszych, wybierając ją `about:config` na stronie z flagą `network.cookie.sameSite.laxByDefault`funkcji. W starszych wersjach programu Firefox nie zgłoszono żadnych problemów ze zgodnością.

##### <a name="microsoft-edge"></a>Microsoft Edge

Mimo że program Microsoft Edge obsługuje `SameSite` stary Standard, w przypadku wersji 44 nie ma żadnych problemów ze zgodnością z nowym standardem.

##### <a name="microsoft-edge-chromium"></a>Microsoft Edge — chrom

Flaga funkcji to `edge://flags/#same-site-by-default-cookies`. Podczas testowania za pomocą programu Microsoft Edge chrom 78 nie zaobserwowano żadnych problemów ze zgodnością.

##### <a name="electron"></a>Elektron

Wersje elektronów obejmują starsze wersje chromu. Na przykład wersja elektronów używana przez program Microsoft teams to chrom 66, który wykazuje starsze zachowanie. Wykonaj własne testy zgodności z wersją elektronów używaną przez produkt. Aby uzyskać więcej informacji, zobacz [Obsługa starszych przeglądarek](#support-older-browsers).

##### <a name="support-older-browsers"></a>Obsługa starszych przeglądarek

Standard 2016 `SameSite` jest przyznany, że nieznane wartości są `SameSite=Strict` traktowane jako wartości. W związku z tym wszystkie starsze przeglądarki, które obsługują oryginalny Standard, mogą zostać przerwane, `SameSite` gdy zobaczysz właściwość o `None`wartości. Aplikacje sieci Web muszą implementować wykrywanie przeglądarki, jeśli zamierzają obsługiwać te stare przeglądarki. ASP.NET Core nie implementuje wykrywania przeglądarki, ponieważ `User-Agent` wartości nagłówka żądania są bardzo niestabilne i zmieniają się co tydzień. Zamiast tego punkt rozszerzenia w zasadach dotyczących plików cookie pozwala na dodawanie `User-Agent`logiki specyficznej.

W *Startup.cs*Dodaj następujący kod:

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

##### <a name="opt-out-switches"></a>Wycofaj przełączniki

Przełącznik `Microsoft.AspNetCore.SuppressSameSiteNone` zgodności umożliwia tymczasowe rezygnację z nowych zachowań plików cookie ASP.NET Core. Dodaj następujący kod JSON do pliku *runtimeconfig. Template. JSON* w projekcie:

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a>Inne wersje

Nastąpi odpowiednie `SameSite` poprawki dla:

* ASP.NET Core 2,1, 2,2 i 3,0
* `Microsoft.Owin`4,1
* `System.Web`(w przypadku .NET Framework 4.7.2 i nowszych)

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
