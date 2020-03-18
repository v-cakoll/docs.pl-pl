---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568087"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>.NET Core 3.0 jest zgodny z najlepszymi rozwiązaniami Unicode podczas zastępowania źle sformułowanych sekwencji bajtów UTF-8

Gdy <xref:System.Text.UTF8Encoding> klasa napotka źle sformułowaną sekwencję bajtów UTF-8 podczas operacji transkodowania bajtów na znak, zastąpi tę sekwencję znakiem ' (U+FFFD REPLACEMENT CHARACTER) w ciągu wyjściowym. .NET Core 3.0 różni się od poprzednich wersji programu .NET Core i programu .NET Framework, stosując najlepsze rozwiązanie Unicode dotyczące wykonywania tej wymiany podczas operacji transkodowania.

Jest to część większego wysiłku w celu poprawy obsługi UTF-8 <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> <xref:System.Text.Rune?displayProperty=nameWithType> w całej .NET, w tym przez nowe i typy. Typ <xref:System.Text.UTF8Encoding> otrzymał ulepszoną mechanikę obsługi błędów, dzięki czemu wytwarza dane wyjściowe zgodne z nowo wprowadzonymi typami.

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Core 3.0, podczas transkodowania <xref:System.Text.UTF8Encoding> bajtów do znaków, klasa wykonuje podstawienia znaków na podstawie najlepszych rozwiązań Unicode. Zastosowany mechanizm podmiana jest opisany przez [Standard Unicode, wersja 12.0, S. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) w _nagłówku zatytułowanym U + FFFD Substytucja maksymalnych podczęści_.

To zachowanie ma zastosowanie _tylko_ wtedy, gdy sekwencja bajtów wejściowych zawiera źle sformułowane dane UTF-8. Ponadto jeśli <xref:System.Text.UTF8Encoding> wystąpienie zostało skonstruowane z `throwOnInvalidBytes: true` (zobacz [UTF8Encoding<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>konstruktora dokumentacji]( , `UTF8Encoding` wystąpienie będzie nadal zgłaszać na nieprawidłowe dane wejściowe, a nie wykonać U + FFFD wymiany.

Poniżej przedstawiono wpływ tej zmiany z nieprawidłowym 3-bajtowym wejściem:

|Źle uformowane wejście 3-bajtowe|Dane wyjściowe przed .NET Core 3.0|Wyjście zaczynające się od .NET Core 3.0|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]`(wyjście 2-znakowe)| `[ FFFD FFFD FFFD ]`(wyjście 3-znakowe)|

To wyjście 3-char jest preferowanym wyjściem, zgodnie z _tabelą 3-9_ wcześniej połączonego Unicode Standard PDF.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Deweloper nie jest wymagany żadne działanie.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
