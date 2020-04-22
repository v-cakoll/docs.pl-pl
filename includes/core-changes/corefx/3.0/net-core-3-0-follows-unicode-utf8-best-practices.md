---
ms.openlocfilehash: 843c78bb4e4f88d9ac58308a91ab8278364c9580
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021583"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>Program .NET Core 3.0 jest zgodny z najlepszymi rozwiązaniami firmy Unicode podczas zastępowania źle sformułowanych sekwencji bajtów UTF-8

Gdy <xref:System.Text.UTF8Encoding> klasa napotka źle sformułowaną sekwencję bajtów UTF-8 podczas operacji transkodowania bajt-znak, zastąpi tę sekwencję znakiem ' ' (U+ FFFD REPLACEMENT CHARACTER) w ciągu wyjściowym. Program .NET Core 3.0 różni się od poprzednich wersji programu .NET Core i programu .NET Framework, postępując zgodnie z najlepszą praktyką unicode dla wykonywania tej wymiany podczas operacji transkodowania.

Jest to część większego wysiłku, aby poprawić utf-8 obsługi <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> w <xref:System.Text.Rune?displayProperty=nameWithType> całej .NET, w tym przez nowe i typy. Typ <xref:System.Text.UTF8Encoding> został ulepszony mechanika obsługi błędów, tak aby produkować dane wyjściowe zgodne z nowo wprowadzonych typów.

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Core 3.0, podczas transkodowania bajtów do znaków, <xref:System.Text.UTF8Encoding> klasa wykonuje podstawienie znaków na podstawie najlepszych rozwiązań Unicode. Stosowany mechanizm zastępowania jest opisany przez [Standard Unicode, wersja 12.0, sek.](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) _U+FFFD Substitution of Maximal Subparts_

To zachowanie ma zastosowanie _tylko_ wtedy, gdy sekwencja bajtów wejściowych zawiera źle sformułowane dane UTF-8. <xref:System.Text.UTF8Encoding> Ponadto jeśli wystąpienie zostało skonstruowane `throwOnInvalidBytes: true` za pomocą (zobacz [UTF8Wcoding<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>konstruktora dokumentacji]( , `UTF8Encoding` wystąpienie będzie nadal rzucać na nieprawidłowe dane wejściowe, a nie wykonać zastąpienie U + FFFD.

Poniżej przedstawiono wpływ tej zmiany z nieprawidłowym wejściem 3-bajtowym:

|Źle sformułowane wejście 3-bajtowe|Wyjście przed .NET Core 3.0|Wyjście zaczynające się od .NET Core 3.0|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]`(wyjście 2-znakowe)| `[ FFFD FFFD FFFD ]`(wyjście 3-znakowe)|

To wyjście 3-char jest preferowanym wyjściem, zgodnie z _tabelą 3-9_ wcześniej połączonego standardu Unicode PDF.

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Nie jest wymagana żadna akcja ze strony dewelopera.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki .NET

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
