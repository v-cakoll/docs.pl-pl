---
title: Wprowadzenie do kodowania znaków w programie .NET
description: Informacje o kodowaniu i dekodowanie znaków w programie .NET.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 85349e1e1c4eca4dd3ef7980f48350a4145fca24
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599870"
---
# <a name="character-encoding-in-net"></a>Kodowanie znaków na platformie .NET

Ten artykuł zawiera wprowadzenie do systemów kodowania znaków, które są używane przez platformę .NET. W tym artykule wyjaśniono <xref:System.String> , jak,, <xref:System.Char> <xref:System.Text.Rune> i <xref:System.Globalization.StringInfo> typy działają z Unicode, UTF-16 i UTF-8.

Ten *znak* jest używany w tym miejscu w ogólnym sensie, *co czytnik jest postrzegany jako pojedynczy element wyświetlania*. Typowe przykłady to litera "a", symbol "@" i Emoji " 🐂 ". Czasami wygląda na to, że jeden znak jest w rzeczywistości składający się z wielu niezależnych elementów wyświetlanych, ponieważ sekcja w [klastrach Grapheme](#grapheme-clusters) objaśnia.

## <a name="the-string-and-char-types"></a>stringTypy i char

Wystąpienie [string](xref:System.String) klasy reprezentuje jakiś tekst. A `string` jest logicznie sekwencją wartości 16-bitowych, z których każdy jest wystąpieniem [char](xref:System.Char) struktury. [ string . Właściwość length](xref:System.String.Length) zwraca liczbę `char` wystąpień w `string` wystąpieniu.

Poniższa funkcja Przykładowa drukuje wartości w notacji szesnastkowej wszystkich `char` wystąpień w `string` :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

Przekaż string "Hello" do tej funkcji i uzyskasz następujące dane wyjściowe:

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

Każdy znak jest reprezentowany przez pojedynczą `char` wartość. Ten wzorzec ma wartość true w przypadku większości języków świata. Na przykład poniżej przedstawiono dane wyjściowe dla dwóch znaków chińskich, takich jak *nǐ hǎo* i średnia *Hello*:

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

Jednak w przypadku niektórych języków i dla niektórych symboli i Emoji `char` do reprezentowania pojedynczego znaku przyjmuje się dwa wystąpienia. Na przykład Porównaj znaki i `char` wystąpienia w wyrazie oznaczające *Osage* w języku Osage:

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

W poprzednim przykładzie każdy znak z wyjątkiem miejsca jest reprezentowany przez dwa `char` wystąpienia.

Pojedynczy emoji Unicode jest również reprezentowany przez dwa `char` s, jak pokazano w poniższym przykładzie pokazujący OX-emoji:

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

Te przykłady pokazują, że wartość `string.Length` , która wskazuje liczbę `char` wystąpień, nie musi wskazywać liczby wyświetlanych znaków. Pojedyncze `char` wystąpienie przez siebie nie musi reprezentować znaku.

`char`Pary, które są mapowane na pojedynczy znak, są nazywane *parami surogatów*. Aby zrozumieć, jak działają, należy zrozumieć kodowanie Unicode i UTF-16.

## <a name="unicode-code-points"></a>Punkty kodu Unicode

Unicode jest międzynarodowym standardem kodowania do użycia na różnych platformach i w różnych językach i skryptach.

Standard Unicode definiuje ponad 1 100 000 [punktów kodów](https://www.unicode.org/glossary/#code_point). Punkt kodu jest wartością całkowitą, która może być z zakresu od 0 do `U+10FFFF` (dziesiętne 1 114 111). Niektóre punkty kodu są przypisywane do liter, symboli lub emoji. Inne są przypisane do akcji kontrolujących sposób wyświetlania tekstu lub znaków, na przykład z wyprzedzeniem do nowego wiersza. Wiele punktów kodowych nie jest jeszcze przypisanych.

Poniżej przedstawiono kilka przykładów przypisań punktów kodu z linkami do wykresów Unicode, w których są one wyświetlane:

|Wartość dziesiętna|Hex       |Przykład|Opis|
|------:|----------|-------|-----------|
|10     | `U+000A` |Brak| [KANAŁ INFORMACYJNY WIERSZA](https://www.unicode.org/charts/PDF/U0000.pdf) |
|65     | `U+0061` | a | [MAŁA LITERA A](https://www.unicode.org/charts/PDF/U0000.pdf) |
|562    | `U+0232` | Ȳ | [WIELKA LITERA Y Z MACRON](https://www.unicode.org/charts/PDF/U0180.pdf) |
|68 675 | `U+10C43`| 𐱃 | [STARY TURKIC LETTER ORKHON NA](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|127 801| `U+1F339`| 🌹 | [RÓŻAny emoji](https://www.unicode.org/charts/PDF/U1F300.pdf) |

Punkty kodu są zwykle określane przy użyciu składni `U+xxxx` , gdzie `xxxx` jest wartością całkowitą zakodowaną szesnastkowo.

W całym zakresie punktów kodu istnieją dwa podzakresy:

* **Podstawowa płaszczyzna wielojęzyczna (BMP)** w zakresie `U+0000..U+FFFF` . Ten 16-bitowy zakres zapewnia 65 536 punktów kodów, wystarczających do pokrycia większości systemów pisania na świecie.
* **Dodatkowe punkty kodu** z zakresu `U+10000..U+10FFFF` . Ten 21-bitowy zakres oferuje ponad milion dodatkowych punktów kodu, które mogą być używane dla mniej dobrze znanych języków i innych celów, takich jak emoji.

Na poniższym diagramie przedstawiono relację między BMP i dodatkowymi punktami kodu.

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP i dodatkowe punkty kodów":::

## <a name="utf-16-code-units"></a>Jednostki kodu UTF-16

16-bitowy format transformacji Unicode ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) to system kodowania znaków, który używa 16-bitowych *jednostek kodu* do reprezentowania punktów kodu Unicode. .NET używa kodowania UTF-16, aby zakodować tekst w `string` . `char`Wystąpienie reprezentuje jednostkę kodu 16-bitowego.

Pojedyncza jednostka kodowa 16-bitowa może reprezentować dowolny punkt kodu w 16-bitowym zakresie podstawowej płaszczyzny wielojęzycznej. Jednak w przypadku punktu kodu w dodatkowych zakresach `char` są potrzeby dwa wystąpienia.

## <a name="surrogate-pairs"></a>Pary zastępcze

Tłumaczenie wartości 2 16-bitowych na pojedynczą wartość 21-bitową jest obsługiwane przez specjalny zakres nazywany *surogatami punktów kodu*od `U+D800` do `U+DFFF` (dziesiętne 55 296 do 57 343) włącznie.

Na poniższym diagramie przedstawiono relację między kodem BMP i surogatem.

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP i Surogat — punkty kodu":::

Gdy do *górnego* punktu kodowego ( `U+D800..U+DBFF` ) bezpośrednio następuje *dolny* punkt kodowy ( `U+DC00..U+DFFF` ), para jest interpretowana jako dodatkowy punkt kodu przy użyciu następującej formuły:

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

W tej samej formule jest używana notacja dziesiętna:

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

*Górny* punkt kodu wieloskładnikowego nie ma wyższej wartości liczbowej niż *dolny* punkt kodowy. Górny punkt kodowy jest nazywany "wysoki", ponieważ jest używany do obliczania wyższej liczby 11 bitów pełnego zakresu kodów 21-bitowego. Dolny punkt kodowy jest używany do obliczania 10 bitów o mniejszej kolejności.

Na przykład rzeczywisty punkt kodu, który odnosi się do pary zastępczej `0xD83C` i `0xDF39` jest obliczany w następujący sposób:

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

To samo obliczenie przy użyciu notacji dziesiętnej:

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

Powyższy przykład pokazuje, że `"\ud83c\udf39"` jest kodowanie UTF-16 `U+1F339 ROSE ('🌹')` powyżej wymienionego powyżej.

## <a name="unicode-scalar-values"></a>Wartości skalarne Unicode

Wyrażenie " [wartość skalarna Unicode](https://www.unicode.org/glossary/#unicode_scalar_value) " odnosi się do wszystkich punktów kodu innych niż punkty zastępcze kodu. Innymi słowy, wartość skalarna to dowolny punkt kodu, do którego przypisano znak lub można przypisać znak w przyszłości. "Znak" odnosi się do wszystkich elementów, które można przypisać do punktu kodu, co obejmuje takie czynności jak akcje kontrolujące sposób wyświetlania tekstu lub znaków.

Na poniższym diagramie przedstawiono punkty kodów wartości skalarnych.

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Wartości skalarne":::

### <a name="the-rune-type-as-a-scalar-value"></a>RuneTyp jako wartość skalarną

Począwszy od platformy .NET Core 3,0, <xref:System.Text.Rune?displayProperty=fullName> Typ reprezentuje wartość skalarną Unicode. **`Rune`Program nie jest dostępny w programie .NET Core 2. x lub .NET Framework 4. x.**

`Rune`Konstruktory weryfikują, że wystąpienie wyniku jest prawidłową wartością skalarną Unicode, w przeciwnym razie zgłasza wyjątek. Poniższy przykład pokazuje kod, który pomyślnie tworzy wystąpienia `Rune` wystąpień, ponieważ dane wejściowe reprezentują prawidłowe wartości skalarne:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

Poniższy przykład zgłasza wyjątek, ponieważ punkt kodu znajduje się w zakresie surogatu i nie jest częścią pary dwuskładnikowej:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

Poniższy przykład zgłasza wyjątek, ponieważ punkt kodu znajduje się poza dodatkowym zakresem:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="rune-usage-example-changing-letter-case"></a>Runeprzykład użycia: zmiana wielkości liter

Interfejs API, który przyjmuje `char` i zakłada, że pracuje z punktem kodu, który jest wartością skalarną, nie działa poprawnie, jeśli `char` pochodzi z pary zastępczej. Rozważmy na przykład następującą metodę, która wywołuje <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> na każdym z char string :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

Jeśli `input` string zawiera małą literę Deseret `er` ( `𐑉` ), ten kod nie przekonwertuje go na wielkie litery ( `𐐡` ). Kod jest wywoływany `char.ToUpperInvariant` oddzielnie w każdym punkcie kodu zastępczego `U+D801` i `U+DC49` . Ale `U+D801` nie ma wystarczających informacji, aby zidentyfikować je jako małą literę, więc `char.ToUpperInvariant` pozostawia ją samodzielnie. Obsługuje to ten `U+DC49` sam sposób. Wynikiem jest to, że małe litery "𐑉" w `input` string nie są konwertowane na wielkie litery "𐑉".

Poniżej przedstawiono dwie opcje prawidłowej konwersji string na wielkie litery:

* Wywołania <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> na wejściu string zamiast Iterowanie `char` przez- `char` . `string.ToUpperInvariant`Metoda ma dostęp do obu części każdej pary surogatów, więc może prawidłowo obsługiwać wszystkie punkty kodu Unicode.
* Wykonaj iterację przez wartości skalarne Unicode jako `Rune` wystąpienia `char` , a nie wystąpienia, jak pokazano w poniższym przykładzie. Ponieważ `Rune` wystąpienie jest prawidłową wartością skalarną Unicode, można je przesłać do interfejsów API, które oczekują na wartość skalarną. Na przykład wywoływanie, <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> jak pokazano w poniższym przykładzie, daje poprawne wyniki:

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-rune-apis"></a>Inne Rune interfejsy API

`Rune`Typ uwidacznia analogowe wiele `char` interfejsów API. Na przykład następujące metody dublowania statycznych interfejsów API w `char` typie:

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

Aby pobrać nieprzetworzoną wartość skalarną z `Rune` wystąpienia, użyj <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> właściwości.

Aby skonwertować `Rune` wystąpienie z powrotem do sekwencji `char` s, użyj <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> metody lub.

Ponieważ każda wartość skalarna Unicode jest możliwa do zaprezentowania przez pojedynczą `char` lub dwuskładnikową parę, każde `Rune` wystąpienie może być reprezentowane przez co najwyżej 2 `char` wystąpienia. Użyj <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> , aby zobaczyć, ile `char` wystąpień jest wymaganych do reprezentowania `Rune` wystąpienia.

Aby uzyskać więcej informacji na temat `Rune` typu .NET, zobacz [ `Rune` Dokumentacja interfejsu API](xref:System.Text.Rune).

## <a name="grapheme-clusters"></a>Klastry Grapheme

Wygląda na to, że jeden znak może wynikać z kombinacji wielu punktów kodowych, więc bardziej opisowy termin, który jest często używany zamiast "Character", to [Grapheme klastra](https://www.unicode.org/glossary/#grapheme_cluster). Odpowiedni termin w programie .NET to [element tekstowy](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).

Rozważ `string` wystąpienia "a", "o". "i" `👩🏽‍🚒` ". Jeśli system operacyjny obsługuje je zgodnie z definicją standardu Unicode, każde z tych `string` wystąpień jest wyświetlane jako pojedynczy element tekstowy lub klaster Grapheme. Jednak ostatnie dwa są reprezentowane przez więcej niż jeden punkt kodu wartości skalarnej.

* string"A" jest reprezentowane przez jedną wartość skalarną i zawiera jedno `char` wystąpienie.

  * `U+0061 LATIN SMALL LETTER A`

* "I" string jest reprezentowane przez jedną wartość skalarną i zawiera jedno `char` wystąpienie.

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* string"A" wygląda tak samo jak "", ale jest reprezentowane przez dwie wartości skalarne i zawiera dwa `char` wystąpienia.

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* Na koniec string " `👩🏽‍🚒` " jest reprezentowane przez cztery wartości skalarne i zawiera siedem `char` wystąpień.

  * `U+1F469 WOMAN`(zakres dodatkowy, wymaga pary dwuskładnikowej)
  * `U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(zakres dodatkowy, wymaga pary dwuskładnikowej)
  * `U+200D ZERO WIDTH JOINER`
  * `U+1F692 FIRE ENGINE`(zakres dodatkowy, wymaga pary dwuskładnikowej)

W niektórych z powyższych przykładów — takich jak modyfikator łączenia akcentu lub modyfikator odcienia skórki — punkt kodu nie jest wyświetlany jako element autonomiczny na ekranie. Zamiast tego służy do modyfikowania wyglądu elementu tekstowego, który został wcześniej dołączony. Te przykłady pokazują, że może przyjmować wiele wartości skalarnych, aby określić, co myślisz jako pojedynczy "znak" lub "klaster Grapheme".

Aby wyliczyć klastry Grapheme z `string` , należy użyć <xref:System.Globalization.StringInfo> klasy, jak pokazano w poniższym przykładzie. Jeśli znasz język SWIFT, `StringInfo` Typ .NET jest koncepcyjnie podobny do [ `character` typu SWIFT](https://developer.apple.com/documentation/swift/character).

### <a name="example-count-char-rune-and-text-element-instances"></a>Przykład: liczba char , Rune i wystąpienia elementu tekstowego

W interfejsach API platformy .NET klaster Grapheme jest nazywany *elementem tekstowym*. Poniższa metoda pokazuje różnice między elementami `char` , `Rune` i wystąpieniami elementów tekstu w `string` :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

W przypadku uruchomienia tego kodu w .NET Framework lub .NET Core 3,1 lub starszym liczba elementów tekstowych dla znaku emoji zostanie wyświetlona `4` . Jest to spowodowane usterką w `StringInfo` klasie, która została naprawiona w programie .NET 5.

### <a name="example-splitting-string-instances"></a>Przykład: dzielenie string wystąpień

Podczas dzielenia `string` wystąpień należy unikać dzielenia pary zastępczych i klastrów Grapheme. Rozważmy następujący przykład nieprawidłowego kodu, który zamierza wstawiać podziały wierszy co 10 znaków w string :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

Ponieważ ten kod wylicza `char` wystąpienia, para dwuskładnikowa, która ma miejsce na obramowanie międzystrefowe, `char` zostanie podzielona i zostanie dodany nowy wiersz. W tym wstawieniu wprowadzono uszkodzenia danych, ponieważ punkty kodu surogatu są istotne tylko jako pary.

Potencjalne uszkodzenie danych nie jest eliminowane w przypadku wyliczania `Rune` wystąpień (wartości skalarnych) zamiast `char` wystąpień. Zestaw `Rune` wystąpień może utworzyć klaster Grapheme, który ma międzystrefę 10 `char` granic. Jeśli zestaw klastrów Grapheme jest podzielony, nie można go poprawnie zinterpretować.

Lepszym rozwiązaniem jest przerwanie string przez zliczanie klastrów Grapheme lub elementów tekstowych, jak w poniższym przykładzie:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

Jak wspomniano wcześniej, jednak w implementacjach platformy .NET innej niż .NET 5 `StringInfo` Klasa może nieprawidłowo obsłużyć niektóre klastry Grapheme.

## <a name="utf-8-and-utf-32"></a>UTF-8 i UTF-32

Poprzednie sekcje skupiające się na kodowaniu UTF-16, ponieważ są używane przez platformę .NET do kodowania `string` wystąpień. Istnieją inne systemy kodowania dla standardu Unicode- [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) i [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32). Te kodowania wykorzystują odpowiednio 8-bitowe jednostki kodu i 32-bitowe jednostki kodu.

Podobnie jak w przypadku UTF-16, UTF-8 wymaga wielu jednostek kodu do reprezentowania niektórych wartości skalarnych Unicode. Kodowanie UTF-32 może reprezentować dowolną wartość skalarną w jednej jednostce kodu 32-bitowej.

Poniżej przedstawiono kilka przykładów przedstawiających sposób reprezentowania tego samego punktu kodu Unicode w każdym z tych trzech systemów kodowania Unicode:

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

Jak wspomniano wcześniej, pojedyncza jednostka kodu UTF-16 z [pary zastępczej](#surrogate-pairs) jest bezproblemowa. W ten sam sposób pojedyncza jednostka kodu UTF-8 jest bezużyteczne, jeśli jest w sekwencji dwóch, trzech lub czterech używanych do obliczania wartości skalarnej.

### <a name="endianness"></a>Endian

W programie .NET jednostki kodu UTF-16 string są przechowywane w ciągłej pamięci jako sekwencja 16-bitowych liczb całkowitych ( `char` wystąpień). Bity poszczególnych jednostek kodu są ustalane w zależności od liczby [bajtów](https://en.wikipedia.org/wiki/Endianness) bieżącej architektury.

W przypadku architektury little-endian string złożone z punktów kodu UTF-16 `[ D801 DCCC ]` zostałyby ustalone w pamięci jako bajty `[ 0x01, 0xD8, 0xCC, 0xDC ]` . W przypadku architektury big-endian string można ją określić w pamięci jako bajty `[ 0xD8, 0x01, 0xDC, 0xCC ]` .

Systemy komputerowe, które komunikują się ze sobą, muszą wyrazić zgodę na reprezentację danych przekraczających sieć. Większość protokołów sieciowych używa kodowania UTF-8 jako standard podczas przesyłania tekstu, częściowo, aby uniknąć problemów, które mogą wynikać z komputera z dużą liczbą bajtów, komunikując się z komputerem o małej przepustowości. stringSkładowe składające się z punktów kodu UTF-8 `[ F0 90 93 8C ]` będą zawsze reprezentowane jako bajty, `[ 0xF0, 0x90, 0x93, 0x8C ]` niezależnie od liczby bajtów.

Aby użyć UTF-8 do przesyłania tekstu, aplikacje .NET często używają kodu, takiego jak Poniższy przykład:

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

W poprzednim przykładzie metoda [Encoding. UTF8. GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) dekoduje kod UTF-16 `string` do serii wartości skalarnych Unicode, a następnie ponownie koduje te wartości skalarne na UTF-8 i umieszcza wyniki sekwencji w `byte` tablicy. Metoda [Encoding. UTF8. GetString](xref:System.Text.UTF8Encoding.GetString%2A) wykonuje odwrotną transformację, konwertując tablicę UTF-8 `byte` na UTF-16 `string` .

> [!WARNING]
> Ponieważ UTF-8 jest commonplace w Internecie, może być skłonny do odczytu nieprzetworzonych bajtów z sieci i do traktowania danych, tak jakby była to UTF-8. Należy jednak sprawdzić, czy jest on rzeczywiście poprawnie sformułowany. Złośliwy klient może przesłać do usługi źle sformułowany format UTF-8. Jeśli te dane są używane w taki sposób, jakby były poprawnie sformułowane, może to spowodować błędy lub luki w zabezpieczeniach aplikacji. Aby sprawdzić poprawność danych UTF-8, można użyć metody takiej jak `Encoding.UTF8.GetString` , która przeprowadza walidację podczas konwertowania danych przychodzących na `string` .

### <a name="well-formed-encoding"></a>Poprawnie sformułowane kodowanie

Poprawnie sformułowane kodowanie Unicode to string jednostki kodu, które można zdekodować w sposób niejednoznaczny i bez błędu do sekwencji wartości skalarnych Unicode. Poprawnie sformułowane dane można transkodować bez ograniczeń i z powrotem między UTF-8, UTF-16 i UTF-32.

Pytanie, czy sekwencja kodowania jest poprawnie sformułowana, czy nie jest niezwiązana z przydziałami architektury maszyny. Nieprawidłowo sformułowana sekwencja UTF-8 jest źle sformułowana w taki sam sposób na maszynach big-endian i little-endian.

Poniżej przedstawiono kilka przykładów niewłaściwie sformułowanych kodowań:

* W UTF-8 sekwencja `[ 6C C2 61 ]` jest źle sformułowana, ponieważ `C2` nie może następować po niej `61` .

* W UTF-16, sekwencja `[ DC00 DD00 ]` (lub, w języku C#, string `"\udc00\udd00"` ) jest źle sformułowana, ponieważ dolny Surogat `DC00` nie może następować po drugim dolnym surogatie `DD00` .

* W UTF-32 sekwencja `[ 0011ABCD ]` jest źle sformułowana, ponieważ `0011ABCD` znajduje się poza zakresem wartości skalarnych Unicode.

W programie .NET `string` wystąpienia prawie zawsze zawierają poprawnie sformułowane dane UTF-16, ale nie są one gwarantowane. W poniższych przykładach pokazano prawidłowy kod w języku C#, który tworzy nieprawidłowo sformułowane dane UTF-16 w `string` wystąpieniach.

* Nieprawidłowo sformułowany literał:

  ```csharp
  const string s = "\ud800";
  ```

* Podciąg dzielący parę zastępczą:

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

Interfejsy API, takie jak [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) nigdy nie zwracają źle sformułowane `string` wystąpienia. `Encoding.GetString``Encoding.GetBytes`metody i wykrywają źle sformułowane sekwencje w danych wejściowych i wykonują podstawienie znaków podczas generowania danych wyjściowych. Jeśli na przykład [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) w danych wejściowych zostanie wyświetlony bajt inny niż ASCII (poza zakresem u + 0000.. u + 007F), wstawiany jest znak "?" w zwracanym `string` wystąpieniu. [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)zamienia źle sformułowane sekwencje UTF-8 z `U+FFFD REPLACEMENT CHARACTER ('�')` w zwracanym `string` wystąpieniu. Aby uzyskać więcej informacji, zobacz [standard Unicode](https://www.unicode.org/versions/latest/), sekcje 5,22 i 3,9.

Wbudowane `Encoding` klasy można również skonfigurować w taki sposób, aby zgłaszać wyjątek, a nie wykonywać podstawienia znaków, gdy widoczne są źle sformułowane sekwencje. Takie podejście jest często stosowane w aplikacjach z uwzględnieniem zabezpieczeń, w których podstawienie znaków może nie być akceptowalne.

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

Aby uzyskać informacje o sposobach korzystania z wbudowanych `Encoding` klas, zobacz [jak używać klas kodowania znaków w programie .NET](character-encoding.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [Globalizacja i lokalizacja](../globalization-localization/index.md)
