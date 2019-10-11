---
ms.openlocfilehash: db1d09c8c9e606b5327a42977a74a74703282d84
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237429"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a>Środowisko .NET Core 3,0 jest zgodne z najlepszymi rozwiązaniami Unicode podczas zamiany niepoprawnie sformułowanych sekwencji bajtów UTF-8

Gdy Klasa <xref:System.Text.UTF8Encoding> napotyka niewłaściwie sformułowaną sekwencję bajtów UTF-8 w trakcie operacji transkodowania typu "Byte do znaków", zastąpi tę sekwencję znakiem "" (U + znak ZASTĘPCZy FFFD) w ciągu danych wyjściowych. Program .NET Core 3,0 różni się od poprzednich wersji programu .NET Core i .NET Framework, zgodnie z najlepszymi rozwiązaniami Unicode dotyczącymi wykonywania tego zastąpienia podczas operacji transkodowania.

Jest to część większego nakładu pracy w celu poprawienia obsługi UTF-8 w całym środowisku .NET, w tym w przypadku nowych typów <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> i <xref:System.Text.Rune?displayProperty=nameWithType>. Typ <xref:System.Text.UTF8Encoding> otrzymał ulepszoną obsługę błędów Mechanics, dzięki czemu generuje dane wyjściowe zgodne z nowo wprowadzonymi typami.

#### <a name="change-description"></a>Zmień opis

Począwszy od platformy .NET Core 3,0, podczas transkodowania bajtów do znaków, Klasa <xref:System.Text.UTF8Encoding> wykonuje podstawienie znaków na podstawie najlepszych rozwiązań w formacie Unicode. Używany mechanizm podstawiania jest opisany w [standardzie Unicode, w wersji 12,0, sek. 3,9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) w nagłówku zatytułowanym _U + FFFD podstawianie z maksymalną częścią_.

To zachowanie ma zastosowanie _tylko_ wtedy, gdy sekwencja bajtów wejściowych zawiera źle sformułowane dane UTF-8. Ponadto jeśli wystąpienie <xref:System.Text.UTF8Encoding> zostało skonstruowane z `throwOnInvalidBytes: true` (patrz [dokumentacja konstruktora UTF8Encoding] (<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, wystąpienie `UTF8Encoding` będzie nadal zgłaszać na nieprawidłowe dane wejściowe zamiast wykonywać zamianę U + FFFD.

Poniżej przedstawiono wpływ tej zmiany na nieprawidłowe dane wejściowe 3-bajtowe:

|Niewłaściwie sformułowane dane wejściowe 3-bajtowe|Dane wyjściowe przed platformą .NET Core 3,0|Dane wyjściowe rozpoczynające się od platformy .NET Core 3,0|
|---|---|---|
| `[ ED A0 90 ]` | `[ FFFD FFFD ]` (2-znakowe dane wyjściowe)| `[ FFFD FFFD FFFD ]` (3-znakowe wyjście)|

Ten 3-znakowy wynik jest preferowanym wyjściem, zgodnie z _tabelą 3-9_ poprzednio połączonego pliku PDF w standardzie Unicode.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

W części dewelopera nie jest wymagana żadna akcja.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Narażone interfejsy API

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
