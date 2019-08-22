---
title: Ciągi interpolowane (Visual Basic)
ms.date: 10/31/2017
ms.openlocfilehash: b9dd055154c86da370a984a465ed412f1fd9908c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666950"
---
# <a name="interpolated-strings-visual-basic-reference"></a>Ciągi interpolowane (odwołanie Visual Basic)

Używane do konstruowania ciągów.  Ciąg interpolowany wygląda jak ciąg szablonu, który zawiera *interpolowane wyrażenia*.  Ciąg interpolowany zwraca ciąg, który zastępuje interpolowane wyrażenia, które zawiera z ich reprezentacją ciągu. Ta funkcja jest dostępna w wersji Visual Basic 14 i nowszych.

Argumenty interpolowanego ciągu są łatwiejsze do zrozumienia niż [ciąg formatu złożonego](../../../../standard/base-types/composite-formatting.md#composite-format-string).  Na przykład ciąg interpolowany

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

zawiera dwa wyrażenia interpolowane "{name}" i "{hours: gg}". Równoważny ciąg formatu złożonego to:

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours);
```

Struktura ciągu interpolowanego jest:

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

gdzie:

- *pole-Width* jest ze znakiem liczby całkowitej, która wskazuje liczbę znaków w polu. Jeśli wartość jest dodatnia, pole jest wyrównane do prawej; w przypadku wartości ujemnych wyrównanych do lewej.

- *ciąg formatu* jest ciągiem formatu odpowiednim dla typu formatowanego obiektu. Na przykład dla <xref:System.DateTime> wartości może to być [standardowy ciąg formatu daty i godziny](../../../../standard/base-types/standard-date-and-time-format-strings.md) , taki jak "d" lub "d".

> [!IMPORTANT]
> Nie można mieć żadnego odstępu między `$` `"` i, który uruchamia ciąg. Powoduje to błąd kompilatora.

Możesz użyć ciągu interpolowanego wszędzie tam, gdzie można użyć literału ciągu.  Ciąg interpolowany jest oceniany za każdym razem, gdy wykonywany jest kod z ciągiem interpolowanym. Pozwala to na oddzielenie definicji i oceny ciągu interpolowanego.

Aby dołączyć nawias klamrowy ("{" lub "}") w ciągu interpolowanym, użyj dwóch nawiasów klamrowych "{{" lub "}}".  Aby uzyskać więcej informacji, zobacz sekcję konwersje niejawne.

Jeśli ciąg interpolowany zawiera inne znaki o specjalnym znaczeniu w ciągu interpolowanym, takim jak cudzysłów ("), dwukropek (:) lub przecinek (,), powinny być wyprowadzane w przypadku wystąpienia tekstu w postaci literału lub powinny być zawarte w wyrażeniu ograniczonym przez nawiasy, jeśli są elementami języka zawartymi w wyrażeniu interpolowanym. Poniższy przykład wyprowadza znaki cudzysłowu, aby uwzględnić je w ciągu wynikowym, i używa nawiasów, aby rozdzielić wyrażenie `(age == 1 ? "" : "s")` tak, aby dwukropek nie był interpretowany jako początkowy ciąg formatu.

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a>Niejawne konwersje

Istnieją trzy niejawne konwersje typów z ciągu interpolowanego:

1. Konwersja ciągu interpolowanego na <xref:System.String>. Poniższy przykład zwraca ciąg, którego interpolowane wyrażenia ciągu zostały zastąpione ich reprezentacją ciągu. Na przykład:

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   Jest to ostateczny wynik interpretacji ciągu. Wszystkie wystąpienia podwójnych nawiasów klamrowych ("{{" i "}}") są konwertowane na pojedynczy nawias klamrowy.

2. Konwersja ciągu interpolowanego na <xref:System.IFormattable> zmienną, która umożliwia tworzenie wielu ciągów wynikowych z zawartością specyficzną dla kultury z jednego <xref:System.IFormattable> wystąpienia. Jest to przydatne do uwzględniania takich elementów jak poprawne formaty liczbowe i daty dla poszczególnych kultur.  Wszystkie wystąpienia podwójnych nawiasów klamrowych ("{{" i "}}") pozostają jako podwójne nawiasy klamrowe do momentu formatowania ciągu przez jawne lub niejawne wywołanie <xref:System.Object.ToString> metody.  Wszystkie zawarte wyrażenia interpolacji są konwertowane na {0}, {1}, i tak dalej.

   Poniższy przykład używa odbicia, aby wyświetlić elementy członkowskie, a także wartości <xref:System.IFormattable> pól i właściwości zmiennej, która jest tworzona na podstawie interpolowanego ciągu. Przekazuje <xref:System.IFormattable> również zmienną <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> do metody.

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   Należy zauważyć, że ciąg interpolowany może być sprawdzany tylko przy użyciu odbicia. Jeśli zostanie przekazana do metody formatowania ciągu, na przykład <xref:System.Console.WriteLine(System.String)>, jego elementy formatu są rozwiązane i zwracany jest ciąg wynikowy.

3. Konwersja ciągu interpolowanego na <xref:System.FormattableString> zmienną, która reprezentuje ciąg formatu złożonego. Sprawdzanie ciągu formatu złożonego i sposób renderowania jako ciąg wynikowy może na przykład ułatwić ochronę przed atakami polegającymi na iniekcji w przypadku tworzenia zapytania. Obejmuje <xref:System.FormattableString> również:

      - Przeciążenie generujące ciąg wynikowy <xref:System.Globalization.CultureInfo.CurrentCulture>dla. <xref:System.FormattableString.ToString>

      - Metoda, która tworzy ciąg <xref:System.Globalization.CultureInfo.InvariantCulture>dla elementu. <xref:System.FormattableString.Invariant%2A>

      - <xref:System.FormattableString.ToString(System.IFormatProvider)> Metoda, która tworzy ciąg wynikowy dla określonej kultury.

    Wszystkie wystąpienia podwójnych nawiasów klamrowych ("{{" i "}}") pozostają jako podwójne nawiasy klamrowe, dopóki nie sformatujesz.  Wszystkie zawarte wyrażenia interpolacji są konwertowane na {0}, {1}, i tak dalej.

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [Dokumentacja języka Visual Basic](index.md)
