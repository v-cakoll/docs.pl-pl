---
ms.openlocfilehash: 492d3e61acff31d3d6858a1c27cf353b04a05e36
ms.sourcegitcommit: d4f7ba08f2a45a9dbef53be597eed6d4a9410f29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86401981"
---
### <a name="security-cookie-name-encoding-removed"></a>Zabezpieczenia: kodowanie nazwy pliku cookie zostało usunięte

[Standard plików cookie protokołu HTTP](https://tools.ietf.org/html/rfc6265#section-4.1.1) zezwala tylko na określone znaki w nazwach i wartościach plików cookie. Aby zapewnić obsługę niedozwolonych znaków, ASP.NET Core:

* Kodowanie podczas tworzenia pliku cookie odpowiedzi.
* Dekoduje podczas odczytywania pliku cookie żądania.

W ASP.NET Core 5,0 to zachowanie kodowania zostało zmienione w odpowiedzi na problem z zabezpieczeniami.

Aby zapoznać się z omówieniem, zobacz sekcję dotyczącą usługi GitHub wydaj [/aspnetcore # 23578](https://github.com/dotnet/aspnetcore/issues/23578).

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 8

#### <a name="old-behavior"></a>Stare zachowanie

Nazwy plików cookie odpowiedzi są zakodowane. Nazwy plików cookie żądania są zdekodowane.

#### <a name="new-behavior"></a>Nowe zachowanie

Kodowanie i dekodowanie nazw plików cookie zostało usunięte. W przypadku wcześniejszych [obsługiwanych wersji](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ASP.NET Core zespół planuje wyeliminować problem związany z dekodowaniem. Ponadto wywołanie <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> z nieprawidłową nazwą pliku cookie zgłasza wyjątek typu <xref:System.ArgumentException> . Kodowanie i dekodowanie wartości plików cookie pozostaje niezmienione.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Wykryto problem w [wielu strukturach sieci Web](https://github.com/advisories/GHSA-j6w9-fv6q-3q52). Kodowanie i dekodowanie może umożliwić atakującemu obejście funkcji zabezpieczeń o nazwie [prefiksy plików cookie](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) przez sfałszowanie zarezerwowanych prefiksów, takich jak `__Host-` z wartościami zakodowanymi, takimi jak `__%48ost-` . Atak wymaga dodatkowego luki w zabezpieczeniach w celu dodania sfałszowanych plików cookie, takich jak usterka skryptów między lokacjami (XSS), w witrynie sieci Web. Te prefiksy nie są domyślnie używane w ASP.NET Core lub `Microsoft.Owin` bibliotekach lub szablonach.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli przenosisz projekty do ASP.NET Core 5,0 lub nowszego, upewnij się, że ich nazwy plików cookie są zgodne z [wymaganiami dotyczącymi specyfikacji tokenu](https://tools.ietf.org/html/rfc2616#section-2.2): znaki ASCII z wyjątkiem formantów i separatorów `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` . Użycie znaków innych niż ASCII w nazwach plików cookie lub innych nagłówkach HTTP może spowodować wystąpienie wyjątku z serwera lub być niepoprawnie przeprowadzona przez klienta.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinRequest.Cookies?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinResponse.Cookies?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
