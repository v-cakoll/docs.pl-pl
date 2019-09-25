---
ms.openlocfilehash: 0795ee244bf3d1261bbe61dc0c67c3936f427f04
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216347"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>Środowisko .NET Core 3,0 jest zgodne z najlepszymi rozwiązaniami Unicode podczas zamiany niepoprawnie sformułowanych sekwencji bajtów UTF-8

<xref:System.Text.UTF8Encoding> Gdy Klasa napotka niewłaściwie sformułowaną sekwencję bajtów UTF-8 podczas operacji transkodowania typu "Byte-to-Character", zastąpi tę sekwencję znakiem "" (U + znak zastępczy FFFD) w ciągu danych wyjściowych. Program .NET Core 3,0 różni się od poprzednich wersji programu .NET Core i .NET Framework, zgodnie z najlepszymi rozwiązaniami Unicode dotyczącymi wykonywania tego zastąpienia podczas operacji transkodowania.

Jest to część większego nakładu pracy w celu poprawienia obsługi UTF-8 w całym środowisku .NET <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> , <xref:System.Text.Rune?displayProperty=nameWithType> w tym w przypadku nowych i typów. <xref:System.Text.UTF8Encoding> Typ został osiągnięty Ulepszona obsługa błędów Mechanics, tak aby dane wyjściowe były spójne z nowo wprowadzonymi typami.

#### <a name="details"></a>Szczegóły

Począwszy od platformy .NET Core 3,0, podczas transkodowania bajtów do znaków, <xref:System.Text.UTF8Encoding> Klasa wykonuje podstawienie znaków na podstawie najlepszych rozwiązań w formacie Unicode. Używany mechanizm podstawiania jest opisany w [standardzie Unicode, w wersji 12,0, sek. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) w nagłówku zatytułowanym _U + FFFD podstawianie z maksymalną częścią_.

To zachowanie ma zastosowanie _tylko_ wtedy, gdy sekwencja bajtów wejściowych zawiera źle sformułowane dane UTF-8. Ponadto, jeśli <xref:System.Text.UTF8Encoding> wystąpienie zostało skonstruowane przy użyciu `throwOnInvalidBytes: true` (zobacz `UTF8Encoding` dokumentację konstruktora UTF8Encoding] (<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, wystąpienie będzie nadal zgłaszać nieprawidłowe dane wejściowe zamiast wykonywać U + FFFD zastępc.

Poniżej przedstawiono wpływ tej zmiany na nieprawidłowe dane wejściowe 3-bajtowe:

|Niewłaściwie sformułowane dane wejściowe 3-bajtowe|Dane wyjściowe przed platformą .NET Core 3,0|Dane wyjściowe rozpoczynające się od platformy .NET Core 3,0|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]`(2-znakowe dane wyjściowe)| `[ FFFD FFFD FFFD ]`(3 znaki wyjściowe)|

Ten 3-znakowy wynik jest preferowanym wyjściem, zgodnie z _tabelą 3-9_ poprzednio połączonego pliku PDF w standardzie Unicode.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

W części dewelopera nie jest wymagana żadna akcja.

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
