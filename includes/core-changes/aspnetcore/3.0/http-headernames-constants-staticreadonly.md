---
ms.openlocfilehash: e0d0a680915f14c2d33f1864ad5ad05aff3dde5f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393902"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP: stałe HeaderNames zmienione do statycznego tylko do odczytu

Począwszy od ASP.NET Core 3,0 wersja zapoznawcza 5, pola w <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> zmieniły się z `const` na `static readonly`.

W przypadku dyskusji zobacz [ASPNET/AspNetCore # 9514](https://github.com/aspnet/AspNetCore/issues/9514).

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

#### <a name="recommended-action"></a>Zalecana akcja

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
