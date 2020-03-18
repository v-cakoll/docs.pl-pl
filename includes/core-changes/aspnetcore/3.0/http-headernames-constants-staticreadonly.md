---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902006"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP: NagłówkiNames stałych zmienionych na statyczne tylko do odczytu

Począwszy od wersji ASP.NET Core 3.0 `const` Preview `static readonly`5, pola w zmienionym <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> stosunku do .

Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Pola te były `const`kiedyś .

#### <a name="new-behavior"></a>Nowe zachowanie

Te pola `static readonly`są teraz .

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zmiana:

* Zapobiega osadzaniu wartości przez granice złożenia, co pozwala na korekty wartości zgodnie z potrzebami.
* Umożliwia szybsze sprawdzanie równości odwołań.

#### <a name="recommended-action"></a>Zalecana akcja

Ponownie skompilować przeciwko 3.0. Kod źródłowy używający tych pól w następujący sposób nie może już tego zrobić:

* Jako argument atrybutu
* Jako `case` w `switch` oświadczeniu
* Przy definiowaniu innego`const`

Aby obejść zmianę podziału, przełącz się na używanie samodzielnie zdefiniowanych stałych nazw nagłówka lub literałów ciągów.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
