---
ms.openlocfilehash: 298cb441bf9fe7daddb30c85f9d7366dc972628c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721713"
---
### <a name="replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines"></a>Zastępowanie źle sformułowanych sekwencji bajtów w formacie UTF-8 następuje po wskazówkach dotyczących standardu Unicode

Gdy <xref:System.Text.UTF8Encoding> Klasa napotka niewłaściwie sformułowaną sekwencję bajtów UTF-8 podczas operacji transkodowania typu "Byte do znaku", zastępuje tę sekwencję znakiem "" (U + znak zastępczy FFFD) w ciągu danych wyjściowych. Program .NET Core 3,0 różni się od poprzednich wersji programu .NET Core i .NET Framework, zgodnie z najlepszymi rozwiązaniami Unicode dotyczącymi wykonywania tego zastąpienia podczas operacji transkodowania.

Jest to część większego nakładu pracy w celu poprawienia obsługi UTF-8 w całym środowisku .NET, w tym w przypadku nowych <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> i <xref:System.Text.Rune?displayProperty=nameWithType> typów. <xref:System.Text.UTF8Encoding>Typ został osiągnięty Ulepszona obsługa błędów Mechanics, tak aby dane wyjściowe były spójne z nowo wprowadzonymi typami.

#### <a name="change-description"></a>Zmień opis

Począwszy od platformy .NET Core 3,0, podczas transkodowania bajtów do znaków, <xref:System.Text.UTF8Encoding> Klasa wykonuje podstawienie znaków na podstawie najlepszych rozwiązań w formacie Unicode. Używany mechanizm podstawiania jest opisany w [standardzie Unicode, w wersji 12,0, sek. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) w nagłówku zatytułowanym _U + FFFD podstawianie z maksymalną częścią_.

To zachowanie ma zastosowanie _tylko_ wtedy, gdy sekwencja bajtów wejściowych zawiera źle sformułowane dane UTF-8. Ponadto jeśli wystąpienie zostało <xref:System.Text.UTF8Encoding> skonstruowane z `throwOnInvalidBytes: true` , `UTF8Encoding` wystąpienie będzie nadal zgłaszać nieprawidłowe dane wejściowe zamiast wykonywać zamianę U + FFFD. Aby uzyskać więcej informacji na temat `UTF8Encoding` konstruktora, zobacz <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)> .

W poniższej tabeli przedstawiono wpływ tej zmiany z nieprawidłowymi danymi wejściowymi 3-bajtowymi:

| Niewłaściwie sformułowane dane wejściowe 3-bajtowe | Dane wyjściowe przed platformą .NET Core 3,0          | Dane wyjściowe rozpoczynające się od platformy .NET Core 3,0        |
|-------------------------|--------------------------------------|-------------------------------------------|
| `[ ED A0 90 ]`          | `[ FFFD FFFD ]`(2-znakowe dane wyjściowe) | `[ FFFD FFFD FFFD ]`(3 znaki wyjściowe) |

3-znakowe dane wyjściowe to preferowane dane wyjściowe, zgodnie z _tabelą 3-9_ poprzednio połączonego pliku PDF w standardzie Unicode.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

W części dewelopera nie jest wymagana żadna akcja.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki platformy .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
