---
title: Wprowadzenie do kodowania znaków w .NET
description: Dowiedz się więcej o kodowaniu i dekodowaniu znaków w .NET.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 34b1577f8bcea80c1f41b6f9605bf47d132fdb4f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134445"
---
# <a name="character-encoding-in-net"></a>Kodowanie znaków w .NET

Ten artykuł zawiera wprowadzenie do systemów kodowania znaków, które są używane przez .NET. W artykule <xref:System.String>wyjaśniono, jak , <xref:System.Char>, <xref:System.Text.Rune>i <xref:System.Globalization.StringInfo> typy działają z Unicode, UTF-16 i UTF-8.

Termin *znak* jest używany tutaj w ogólnym znaczeniu *tego, co czytelnik postrzega jako pojedynczy element wyświetlania*. Typowymi przykładami są litera "a", symbol "@" i emoji " ".🐂 Czasami to, co wygląda jak jeden znak, składa się z wielu niezależnych elementów wyświetlania, jak wyjaśnia sekcja na [klastrach grafem.](#grapheme-clusters)

## <a name="the-string-and-char-types"></a>Typy ciągów i znaków

Wystąpienie klasy [string](xref:System.String) reprezentuje jakiś tekst. A `string` jest logicznie sekwencji wartości 16-bitowych, z których każdy jest wystąpieniem struktury [char.](xref:System.Char) [Ciąg. Właściwość Length](xref:System.String.Length) zwraca `char` liczbę wystąpień w wystąpieniu. `string`

Następująca funkcja przykładu drukuje wartości w notacji szesnastkowej `char` `string`wszystkich wystąpień w:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

Przekaż ciąg "Hello" do tej funkcji i otrzymasz następujące dane wyjściowe:

```csharp
PrintChars("Hello");
```

```output
"Hello".Length = 5
s[0] = 'H' ('\u0048')
s[1] = 'e' ('\u0065')
s[2] = 'l' ('\u006c')
s[3] = 'l' ('\u006c')
s[4] = 'o' ('\u006f')
```

Każdy znak jest reprezentowany `char` przez jedną wartość. Ten wzorzec odnosi się do większości języków świata. Na przykład, oto dane wyjściowe dla dwóch chińskich znaków, które brzmią jak *n ho* i oznaczają *Hello:*

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

Jednak w przypadku niektórych języków oraz dla niektórych `char` symboli i emotikonów potrzeba dwóch wystąpień, aby reprezentować pojedynczy znak. Na przykład porównaj `char` znaki i wystąpienia w słowie, co oznacza *Osage* w języku Osage:

```csharp
PrintChars("𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟");
```

```output
"𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟".Length = 17
s[0] = '�' ('\ud801')
s[1] = '�' ('\udccf')
s[2] = '�' ('\ud801')
s[3] = '�' ('\udcd8')
s[4] = '�' ('\ud801')
s[5] = '�' ('\udcfb')
s[6] = '�' ('\ud801')
s[7] = '�' ('\udcd8')
s[8] = '�' ('\ud801')
s[9] = '�' ('\udcfb')
s[10] = '�' ('\ud801')
s[11] = '�' ('\udcdf')
s[12] = ' ' ('\u0020')
s[13] = '�' ('\ud801')
s[14] = '�' ('\udcbb')
s[15] = '�' ('\ud801')
s[16] = '�' ('\udcdf')
```

W poprzednim przykładzie każdy znak z wyjątkiem spacji jest reprezentowany przez dwa `char` wystąpienia.

Pojedynczy emoji Unicode jest również `char`reprezentowany przez dwa s, jak widać w poniższym przykładzie przedstawiającym emotikony wół:

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

Te przykłady pokazują, `string.Length`że wartość , która `char` wskazuje liczbę wystąpień, niekoniecznie wskazuje liczbę wyświetlanych znaków. Pojedyncze `char` wystąpienie samo w sobie nie musi reprezentować znaku.

Pary `char` mapowane na pojedynczy znak są nazywane *parami zastępczymi*. Aby zrozumieć, jak działają, musisz zrozumieć kodowanie Unicode i UTF-16.

## <a name="unicode-code-points"></a>Punkty kodu Unicode

Unicode jest międzynarodowym standardem kodowania do użytku na różnych platformach oraz w różnych językach i skryptach.

Standard Unicode definiuje ponad 1,1 miliona [punktów kodu](https://www.unicode.org/glossary/#code_point). Punkt kodu jest wartością całkowitą, która może `U+10FFFF` wynosić od 0 do (dziesiętne 1,114,111). Niektóre punkty kodu są przypisywane do liter, symboli lub emotikonów. Inne są przypisywane do akcji, które kontrolują sposób wyświetlania tekstu lub znaków, takich jak przechodzenie do nowego wiersza. Wiele punktów kodu nie są jeszcze przypisane.

Oto kilka przykładów przypisań punktów kodu z łączami do wykresów Unicode, w których się pojawiają:

|Wartość dziesiętna|Hex       |Przykład|Opis|
|------:|----------|-------|-----------|
|10     | `U+000A` |Nie dotyczy| [POSUW LINIOWY](https://www.unicode.org/charts/PDF/U0000.pdf) |
|65     | `U+0061` | a | [ŁACIŃSKA MAŁA LITERA A](https://www.unicode.org/charts/PDF/U0000.pdf) |
|562    | `U+0232` | z o.o. | [WIELKA LITERA Y Z MACRONEM](https://www.unicode.org/charts/PDF/U0180.pdf) |
|68,675 | `U+10C43`| 𐱃 | [STARY LIST TURECKI ORKHON W](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|127,801| `U+1F339`| 🌹 | [RÓŻA emoji](https://www.unicode.org/charts/PDF/U1F300.pdf) |

Punkty kodu są zwyczajowo określane przy użyciu `U+xxxx`składni , gdzie `xxxx` jest wartością całkowitą zakodowaną przez szesnastkową.

W pełnym zakresie punktów kodu znajdują się dwa podzakresy:

* **Podstawowa płaszczyzna wielojęzyczna (BMP)** w zakresie `U+0000..U+FFFF`. Ten 16-bitowy zakres zapewnia 65 536 punktów kodu, co wystarcza na pokrycie większości światowych systemów pisania.
* **Dodatkowe punkty kodu** w `U+10000..U+10FFFF`zakresie . Ten zakres 21-bitowy zapewnia ponad milion dodatkowych punktów kodu, które mogą być używane w mniej znanych językach i innych celach, takich jak emotikony.

Na poniższym diagramie przedstawiono relację między BMP a dodatkowymi punktami kodu.

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP i dodatkowe punkty kodowe":::

## <a name="utf-16-code-units"></a>Jednostki kodu UTF-16

16-bitowy format transformacji Unicode[(UTF-16)](https://www.unicode.org/faq/utf_bom.html#UTF16)to system kodowania znaków, który używa 16-bitowych *jednostek kodu* do reprezentowania punktów kodu Unicode. Program .NET używa utf-16 do zakodowania tekstu w pliku `string`. Wystąpienie `char` reprezentuje jednostkę kodu 16-bitowego.

Pojedyncza 16-bitowa jednostka kodu może reprezentować dowolny punkt kodu w 16-bitowym zakresie podstawowej płaszczyzny wielojęzycznej. Ale dla punktu kodu w zakresie `char` uzupełniającym potrzebne są dwa wystąpienia.

## <a name="surrogate-pairs"></a>Pary zastępcze

Translacja dwóch 16-bitowych wartości na pojedynczą wartość 21-bitową jest ułatwiona `U+D800` `U+DFFF` przez specjalny zakres zwany *punktami kodu zastępczego*, od (dziesiętne 55 296 do 57 343), włącznie.

Na poniższym diagramie przedstawiono relację między BMP i zastępczych punktów kodu.

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP i zastępcze punkty kodu":::

Gdy po *wysokim zastępczym* punkcie kodu (`U+D800..U+DBFF`) natychmiast`U+DC00..U+DFFF`następuje niski punkt kodu *zastępczego* ( ), para jest interpretowana jako dodatkowy punkt kodu przy użyciu następującej formuły:

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

Oto ta sama formuła z notacją dziesiętną:

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

*Wysoki* punkt kodu zastępczego nie ma wyższej wartości liczbowej niż *niski* punkt kodu zastępczego. Wysoki punkt kodu zastępczego jest nazywany "wysokim", ponieważ jest używany do obliczania wyższego rzędu 11 bitów pełnego zakresu punktów kodu 21-bitowego. Niski punkt kodu zastępczego jest używany do obliczania niższego rzędu 10 bitów.

Na przykład rzeczywisty punkt kodu, który `0xD83C` odpowiada `0xDF39` parze zastępczej i jest obliczany w następujący sposób:

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

Oto te same obliczenia przy użyciu notacji dziesiętnej:

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

W poprzednim przykładzie `"\ud83c\udf39"` pokazano, że jest UTF-16 kodowania punktu `U+1F339 ROSE ('🌹')` kodu wspomniano wcześniej.

## <a name="unicode-scalar-values"></a>Wartości skalarne Unicode

Termin [Wartość skalarna Unicode](https://www.unicode.org/glossary/#unicode_scalar_value) odnosi się do wszystkich punktów kodu innych niż punkty kodu zastępczego. Innymi słowy wartość skalarna jest dowolnym punktem kodu, który jest przypisany znak lub może być przypisany znak w przyszłości. "Znak" odnosi się tutaj do wszystkiego, co można przypisać do punktu kodu, który zawiera takie rzeczy, jak akcje, które kontrolują sposób wyświetlania tekstu lub znaków.

Na poniższym diagramie przedstawiono skalarne punkty kodu wartości.

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Wartości skalarne":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a>Typ Rune jako wartość skalarna

Począwszy od .NET Core 3.0, <xref:System.Text.Rune?displayProperty=fullName> typ reprezentuje wartość skalarną Unicode. **`Rune`nie jest dostępna w programach .NET Core 2.x lub .NET Framework 4.x.**

Konstruktory `Rune` sprawdzają, czy wynikowe wystąpienie jest prawidłową wartością skalarną Unicode, w przeciwnym razie zgłaszają wyjątek. Poniższy przykład pokazuje kod, `Rune` który pomyślnie wystąpienia wystąpień, ponieważ dane wejściowe reprezentuje prawidłowe wartości skalarne:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

Poniższy przykład zgłasza wyjątek, ponieważ punkt kodu znajduje się w zakresie zastępczym i nie jest częścią pary zastępczej:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

Poniższy przykład zgłasza wyjątek, ponieważ punkt kodu wykracza poza zakres uzupełniający:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>Runeprzykład użycia: zmiana litery

Interfejs API, `char` który przyjmuje i zakłada, że pracuje z punktem kodu, który `char` jest wartością skalarną, nie działa poprawnie, jeśli jest z pary zastępczej. Rozważmy na przykład następującą <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> metodę, która wywołuje każdą char w: string

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

`input` string Jeśli zawiera literę Deseret `er` (`𐑉`), ten kod nie konwertuje`𐐡`go na wielkie litery ( ). Kod wywołuje `char.ToUpperInvariant` oddzielnie dla każdego `U+D801` zastępczego punktu kodu i `U+DC49`. Ale `U+D801` nie ma wystarczającej ilości informacji, aby zidentyfikować je `char.ToUpperInvariant` jako małe litery, więc pozostawia go w spokoju. I radzi `U+DC49` sobie w ten sam sposób. W rezultacie małe litery "♡" w literach `input` string nie są konwertowane na wielkie litery .-."

Oto dwie opcje poprawnej string konwersji liter na wielkie litery:

* <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> Wezwiej string dane wejściowe, a nie iteracyjne `char`-by-`char`. Metoda `string.ToUpperInvariant` ma dostęp do obu części każdej pary zastępczej, dzięki czemu może obsługiwać wszystkie punkty kodu Unicode poprawnie.
* Iteracji za pośrednictwem wartości skalarnych Unicode jako `Rune` wystąpień zamiast `char` wystąpień, jak pokazano w poniższym przykładzie. Ponieważ `Rune` wystąpienie jest prawidłową wartością skalarną Unicode, może być przekazywana do interfejsów API, które oczekują, że będą działać na wartości skalarnej. Na przykład <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> wywołanie, jak pokazano w poniższym przykładzie daje poprawne wyniki:

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a>Inne Rune interfejsy API

Typ `Rune` udostępnia analogi wielu interfejsów `char` API. Na przykład następujące metody dublowania statycznych `char` interfejsów API na typ:

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

Aby uzyskać surową wartość `Rune` skalarną <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> z wystąpienia, należy użyć właściwości.

Aby przekonwertować `Rune` wystąpienie `char`z <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> powrotem <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> do sekwencji s, użyj lub metody.

Ponieważ każda wartość skalarna Unicode `char` jest reprezentowana przez `Rune` parę pojedynczą lub zastępczą, `char` każde wystąpienie może być reprezentowane przez co najwyżej 2 wystąpienia. Użyj, <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> aby `char` zobaczyć, ile wystąpień `Rune` są wymagane do reprezentowania wystąpienia.

Aby uzyskać więcej informacji `Rune` na temat typu .NET, zobacz [ `Rune` odwołanie do interfejsu API](xref:System.Text.Rune).

## <a name="grapheme-clusters"></a>Klastry grafeme

To, co wygląda jak jeden znak, może wynikać z połączenia wielu punktów kodu, więc bardziej opisowym terminem, który jest często używany zamiast "znaku", jest [klaster grafem](https://www.unicode.org/glossary/#grapheme_cluster). Równoważnym terminem w .NET jest [element tekstowy](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).

Rozważmy `string` wystąpienia "a", "á". "á" i`👩🏽‍🚒`" ". Jeśli system operacyjny obsługuje je zgodnie z normą Unicode, każde z tych `string` wystąpień jest wyświetlane jako pojedynczy element tekstowy lub klaster grafem. Ale dwa ostatnie są reprezentowane przez więcej niż jeden punkt kodu wartości skalarnej.

* "a" string jest reprezentowana przez jedną wartość `char` skalarną i zawiera jedno wystąpienie.

  * `U+0061 LATIN SMALL LETTER A`

* "á" string jest reprezentowana przez jedną wartość `char` skalarną i zawiera jedno wystąpienie.

  * `U+00E1 LATIN SMALL LETTER E WITH ACUTE`

* string "á" wygląda tak samo jak "á", ale jest reprezentowana `char` przez dwie wartości skalarne i zawiera dwa wystąpienia.

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* Na koniec string "`👩🏽‍🚒`" jest reprezentowany przez cztery `char` wartości skalarne i zawiera siedem wystąpień.

  * `U+1F469 WOMAN`(zakres dodatkowy, wymaga pary zastępczej)
  * `U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(zakres dodatkowy, wymaga pary zastępczej)
  * `U+200D ZERO WIDTH JOINER`
  * `U+1F692 FIRE ENGINE`(zakres dodatkowy, wymaga pary zastępczej)

W niektórych z powyższych przykładów , takich jak modyfikator akcentu łączącego lub modyfikator odcienia karnacji, punkt kodu nie jest wyświetlany jako element autonomiczny na ekranie. Przeciwnie służy do modyfikowania wyglądu elementu tekstowego, który przyszedł przed nim. Te przykłady pokazują, że może potrwać wiele wartości skalarnych, aby uzupełnić to, co myślimy o jako pojedynczy "znak" lub "klaster grafeme".

Aby wyliczyć klastry grafeme `string`, <xref:System.Globalization.StringInfo> użyj klasy, jak pokazano w poniższym przykładzie. Jeśli znasz program Swift, typ `StringInfo` .NET jest koncepcyjnie podobny do [ `character` typu Swift.](https://developer.apple.com/documentation/swift/character)

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a>Przykład: charliczba Rune, i wystąpienia elementów tekstowych

W interfejsach API platformy .NET klaster grafemowy jest nazywany *elementem tekstowym*. Poniższa metoda pokazuje różnice `char` `Rune`między wystąpieniami elementu tekstowego i tekstowymi `string`w :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

Jeśli ten kod zostanie uruchomiony w programach .NET Framework lub .NET Core 3.1 lub wcześniejszych, liczba elementów tekstowych dla emoji zostanie wyświetlony `4`. Wynika to z błędu `StringInfo` w klasie, który jest naprawiony w .NET 5.

### <a name="example-splitting-opno-locstring-instances"></a>Przykład: dzielenie string wystąpień

Podczas dzielenia `string` wystąpień należy unikać dzielenia par zastępczych i klastrów grafem. Rozważmy następujący przykład nieprawidłowego kodu, który zamierza wstawić podziały wiersza co 10 znaków w : string

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

Ponieważ ten kod wylicza `char` wystąpienia, para zastępcza, która dzieje`char` się osieroconych 10-granica zostanie podzielona i nowywierek między nimi. To wstawianie wprowadza uszkodzenie danych, ponieważ zastępcze punkty kodu mają znaczenie tylko jako pary.

Możliwość uszkodzenia danych nie jest eliminowana, jeśli `Rune` wyliczasz wystąpienia (wartości skalarne) zamiast wystąpień. `char` Zestaw wystąpień `Rune` może stanowić klaster grafem, który przecina`char` granicę 10. Jeśli zestaw klastra grafemu jest podzielony, nie można go poprawnie zinterpretować.

Lepszym rozwiązaniem jest przerwanie string klastrów grafeme lub elementów tekstowych, jak w poniższym przykładzie:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

Jak wspomniano wcześniej, jednak w implementacjach .NET innych `StringInfo` niż .NET 5, klasa może obsługiwać niektóre klastry grafeme niepoprawnie.

## <a name="utf-8-and-utf-32"></a>UTF-8 i UTF-32

Poprzednie sekcje koncentruje się na UTF-16, ponieważ to, co `string` .NET używa do kodowania wystąpień. Istnieją inne systemy kodowania dla Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) i [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32). Kodowania te używają jednostek kodu 8-bitowego i jednostek kodu 32-bitowego, odpowiednio.

Podobnie jak UTF-16, UTF-8 wymaga wielu jednostek kodu do reprezentowania niektórych wartości skalarnych Unicode. UTF-32 może reprezentować dowolną wartość skalarną w pojedynczej jednostce kodu 32-bitowego.

Oto kilka przykładów pokazujących, jak ten sam punkt kodu Unicode jest reprezentowany w każdym z tych trzech systemów kodowania Unicode:

```
Scalar: U+0061 LATIN SMALL LETTER A ('a')
UTF-8 : [ 61 ]           (1x  8-bit code unit  = 8 bits total)
UTF-16: [ 0061 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000061 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+0429 CYRILLIC CAPITAL LETTER SHCHA ('Щ')
UTF-8 : [ D0 A9 ]        (2x  8-bit code units = 16 bits total)
UTF-16: [ 0429 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000429 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+A992 JAVANESE LETTER GA ('ꦒ')
UTF-8 : [ EA A6 92 ]     (3x  8-bit code units = 24 bits total)
UTF-16: [ A992 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 0000A992 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+104CC OSAGE CAPITAL LETTER TSHA ('𐓌')
UTF-8 : [ F0 90 93 8C ]  (4x  8-bit code units = 32 bits total)
UTF-16: [ D801 DCCC ]    (2x 16-bit code units = 32 bits total)
UTF-32: [ 000104CC ]     (1x 32-bit code unit  = 32 bits total)
```

Jak wspomniano wcześniej, pojedyncza jednostka kodu UTF-16 z [pary zastępczej](#surrogate-pairs) jest bez znaczenia sama w sobie. W ten sam sposób pojedyncza jednostka kodu UTF-8 jest sama w sobie bez znaczenia, jeśli jest w sekwencji dwóch, trzech lub czterech używanych do obliczania wartości skalarnej.

### <a name="endianness"></a>Endianness (Endianness)

W .NET jednostki kodu UTF-16 string są przechowywane w ciągłej pamięci jako sekwencja 16-bitowych liczby całkowite (wystąpień).`char` Bity poszczególnych jednostek kodu są określone zgodnie z [endianness](https://en.wikipedia.org/wiki/Endianness) bieżącej architektury.

Na architekturze mało endian, string składający się z punktów `[ D801 DCCC ]` kodu UTF-16 będzie `[ 0x01, 0xD8, 0xCC, 0xDC ]`określone w pamięci jako bajty . Na architekturze big-endian, że to samo string będzie `[ 0xD8, 0x01, 0xDC, 0xCC ]`określone w pamięci jako bajty .

Systemy komputerowe, które komunikują się ze sobą, muszą uzgodnić reprezentację danych przecinających przewód. Większość protokołów sieciowych używa UTF-8 jako standardu podczas przesyłania tekstu, częściowo w celu uniknięcia problemów, które mogą wynikać z komunikacji maszyny wielkofemiańskiego z maszyną małotuzyjną. Składający string się z punktów `[ F0 90 93 8C ]` kodu UTF-8 zawsze będą `[ 0xF0, 0x90, 0x93, 0x8C ]` reprezentowane jako bajty, niezależnie od endianness.

Aby użyć UTF-8 do przesyłania tekstu, aplikacje .NET często używają kodu, takiego jak w poniższym przykładzie:

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

W poprzednim przykładzie metoda [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) dekoduje UTF-16 `string` z powrotem do serii wartości skalarnych Unicode, a następnie ponownie koduje te wartości `byte` skalarne w UTF-8 i umieszcza wynikową sekwencję w tablicy. Metoda [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) wykonuje odwrotną transformację, konwertując `byte` tablicę UTF-8 `string`na UTF-16 .

> [!WARNING]
> Ponieważ UTF-8 jest powszechne w Internecie, może być kuszące, aby odczytać surowe bajty z przewodu i traktować dane tak, jakby to było UTF-8. Należy jednak sprawdzić, czy jest on rzeczywiście dobrze uformowany. Złośliwy klient może przesłać źle sformułowane UTF-8 do usługi. Jeśli działasz na tych danych tak, jakby były dobrze sformułowane, może to spowodować błędy lub luki w zabezpieczeniach w aplikacji. Aby sprawdzić poprawność danych UTF-8, `Encoding.UTF8.GetString`można użyć metody, takiej jak , `string`która będzie przeprowadzać sprawdzanie poprawności podczas konwertowania danych przychodzących na plik .

### <a name="well-formed-encoding"></a>Dobrze uformowane kodowanie

Dobrze sformułowane kodowanie Unicode string jest jednostkami kodu, które mogą być dekodowane jednoznacznie i bez błędu w sekwencji wartości skalarnych Unicode. Dobrze uformowane dane mogą być transkodowane swobodnie tam iz powrotem między UTF-8, UTF-16 i UTF-32.

Pytanie, czy sekwencja kodowania jest dobrze sformułowana, czy nie, nie jest związane z endianness architektury maszyny. Źle ukształtowana sekwencja UTF-8 jest źle uformowana w ten sam sposób zarówno na maszynach big-endian, jak i mało endiańskich.

Oto kilka przykładów źle sformułowanych kodowania:

* W UTF-8 sekwencja `[ 6C C2 61 ]` jest źle `C2` sformułowana, `61`ponieważ nie można następować po .

* `[ DC00 DD00 ]` W UTF-16 sekwencja (lub w języku string `"\udc00\udd00"`C#,) jest źle `DC00` sformułowana, ponieważ `DD00`nie można następować po niskim surogatem.

* W UTF-32 sekwencja `[ 0011ABCD ]` jest źle `0011ABCD` sformułowana, ponieważ znajduje się poza zakresem wartości skalarnych Unicode.

W .NET `string` wystąpienia prawie zawsze zawierają dobrze sformułowane dane UTF-16, ale nie jest to gwarantowane. Poniższe przykłady pokazują prawidłowy kod języka C#, który tworzy `string` źle sformułowane dane UTF-16 w wystąpieniach.

* Źle sformułowany dosłowny:

  ```csharp
  const string s = "\ud800";
  ```

* Podciąg, który dzieli parę zastępczą:

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

Interfejsy API [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) jak nigdy `string` nie zwracają źle sformułowane wystąpienia. `Encoding.GetString`i `Encoding.GetBytes` metody wykrywają źle sformułowane sekwencje w danych wejściowych i wykonują podstawienie znaków podczas generowania danych wyjściowych. Na przykład [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) jeśli widzi bajt non-ASCII w danych wejściowych (poza zakresem U + 0000..U + 007F), wstawia '?' do zwróconego `string` wystąpienia. [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)zastępuje źle sformułowane sekwencje UTF-8 `U+FFFD REPLACEMENT CHARACTER ('�')` `string` w zwróconym wystąpieniu. Aby uzyskać więcej informacji, zobacz [Standard Unicode](https://www.unicode.org/versions/latest/), Sekcje 5.22 i 3.9.

Wbudowane klasy `Encoding` można również skonfigurować, aby zgłosić wyjątek, a nie wykonywać podstawienia znaków, gdy nieuformowane sekwencje są widoczne. Takie podejście jest często używane w aplikacjach wrażliwych na zabezpieczenia, gdzie podstawianie znaków może być nie do przyjęcia.

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

Aby uzyskać informacje dotyczące używania `Encoding` wbudowanych klas, zobacz [Jak używać klas kodowania znaków w .NET](character-encoding.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [Globalizacja i lokalizacja](../../../docs/standard/globalization-localization/index.md)
