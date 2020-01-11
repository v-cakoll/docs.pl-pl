---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902006"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP: stałe HeaderNames zmienione do statycznego tylko do odczytu

Począwszy od ASP.NET Core 3,0 wersja zapoznawcza 5, pola w <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> zmienione z `const` na `static readonly`.

Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Te pola używane do `const`.

#### <a name="new-behavior"></a>Nowe zachowanie

Te pola są teraz `static readonly`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zmiana:

* Zapobiega osadzaniu wartości między granicami zestawów, umożliwiając korektę wartości zgodnie z wymaganiami.
* Umożliwia szybsze sprawdzanie równości odwołań.

#### <a name="recommended-action"></a>Zalecane działanie

Kompiluj ponownie z 3,0. Kod źródłowy korzystający z tych pól w następujących sposobach nie może już być taki:

* Jako argument atrybutu
* Jako `case` w instrukcji `switch`
* Podczas definiowania innego `const`

Aby obejść istotną zmianę, należy przełączyć się do użycia samodzielnych stałych nazw nagłówka lub literałów ciągów.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
