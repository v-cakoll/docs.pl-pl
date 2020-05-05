---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902006"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP: stałe HeaderNames zmienione do statycznego tylko do odczytu

Począwszy od ASP.NET Core 3,0 wersja zapoznawcza 5, <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> pola w `const` obszarze `static readonly`zmieniono z na.

Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Te pola, które są `const`używane.

#### <a name="new-behavior"></a>Nowe zachowanie

Te pola są teraz `static readonly`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zmiana:

* Zapobiega osadzaniu wartości między granicami zestawów, umożliwiając korektę wartości zgodnie z wymaganiami.
* Umożliwia szybsze sprawdzanie równości odwołań.

#### <a name="recommended-action"></a>Zalecana akcja

Kompiluj ponownie z 3,0. Kod źródłowy korzystający z tych pól w następujących sposobach nie może już być taki:

* Jako argument atrybutu
* Jako `switch` instrukcja `case` w instrukcji
* Podczas definiowania innego`const`

Aby obejść istotną zmianę, należy przełączyć się do użycia samodzielnych stałych nazw nagłówka lub literałów ciągów.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
