---
title: Ciągi interpolowane (Visual Basic)
ms.date: 10/31/2017
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 313e74d5ce252884f1df2479ef1db8b4b24b5cce
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799268"
---
# <a name="interpolated-strings-visual-basic-reference"></a>Ciągi interpolowane (odwołanie w Visual Basic)

Używane do konstruowania ciągów.  Ciąg interpolowany wygląda jak ciąg szablonu, który zawiera *wyrażeń interpolowanych*.  Ciąg interpolowany zwraca ciąg, który zastępuje wyrażenia interpolowane, które zawiera ich reprezentacji ciągu. Ta funkcja jest dostępna w języku Visual Basic, 14 i nowszych wersjach.

Argumenty ciągu interpolowanego są łatwiejsze do zrozumienia niż [ciąg formatu złożonego](../../../../standard/base-types/composite-formatting.md#composite-format-string).  Na przykład ciąg interpolowany  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
zawiera dwa wyrażenia interpolowane "{name}" i "{godzin: hh}". Ciąg formatu złożonego równoważne jest następujący:

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

Struktura ciągu interpolowanego jest:  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

gdzie: 

- *szerokość pola* jest liczbą całkowitą ze znakiem, który określa liczbę znaków w polu. Jeśli jest dodatnią, pole jest wyrównany do prawej; Jeśli jest negatywny, wyrównane do lewej. 

- *Ciąg formatu* jest ciągiem formatu odpowiedniego dla typu formatowanego obiektu. Na przykład w przypadku <xref:System.DateTime> wartości, może to być [ciąg formatu standardowego daty i godziny](~/docs/standard/base-types/standard-date-and-time-format-strings.md) takich jak "D" lub "d".

> [!IMPORTANT]
> Nie może mieć dowolny biały obszar między `$` i `"` którego początkowe ciągu. To powoduje wystąpienie błędu kompilatora.

 Można użyć ciągu interpolowanego dowolnym można użyć literału ciągu.  Ciąg interpolowany jest oceniany każdorazowo, gdy wykonuje kod za pomocą ciągu interpolowanym. Dzięki temu można oddzielić definicję i oceny w ciągu interpolowanym.  
  
 Aby uwzględnić nawias klamrowy ("{" lub "}") w ciągu interpolowanym, użyj dwa nawiasy klamrowe, "{{" lub "}}".  Zobacz sekcję konwersje niejawne, aby uzyskać więcej informacji.  

Jeśli ciąg interpolowany zawiera inne znaki przy użyciu specjalnego znaczenia w ciągu interpolowanym, takie jak znak cudzysłowu ("), dwukropek (:) lub przecinka (,), należy wyjściowym je czy występują one w tekst dosłowny, powinny one zostać włączone w wyrażeniu rozdzielone nawiasy, jeśli są one elementy języka zawarte w wyrażeniu interpolowanym. Poniższy przykład zmienia znaczenie znaków cudzysłowu, aby je uwzględnić w ciągu wynikowym i używa nawiasów do ograniczania wyrażenie `(age == 1 ? "" : "s")` tak, że po dwukropku nie jest interpretowany jako początek ciągu formatu.

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a>Niejawne konwersje  

Istnieją trzy niejawne konwersje typów z ciągu interpolowanego:  

1. Konwersja ciągu interpolowanego do <xref:System.String>. Poniższy przykład zwraca ciąg, którego wyrażenia ciągu interpolowanego zostały zastąpione ich reprezentacji ciągu. Na przykład:

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   Jest to końcowy wynik interpretacji ciągu. Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") są konwertowane na Pojedynczy nawias klamrowy. 

2. Konwersja ciągu interpolowanego do <xref:System.IFormattable> zmiennej, która umożliwia tworzenie wielu wyników ciągi z zawartością specyficzne dla kultury z jednej <xref:System.IFormattable> wystąpienia. Jest to przydatne, w tym takich zadań jak poprawne formaty liczb i dat dla poszczególnych kultur.  Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") pozostają podwójne nawiasy klamrowe do momentu sformatować ciąg przez wywołanie metody jawnie lub niejawnie <xref:System.Object.ToString> metody.  Wszystkie wyrażenia interpolacji zawarte są konwertowane na {0}, {1}i tak dalej.  

   W poniższym przykładzie użyto odbicia, aby wyświetlić elementy członkowskie, a także wartości pola i właściwości <xref:System.IFormattable> zmiennej, która jest tworzona na podstawie ciągu interpolowanym. Przekazuje także <xref:System.IFormattable> zmienną <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody.

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   Należy pamiętać, że ciągu interpolowanego może być kontrolowane tylko przy użyciu odbicia. Jeśli zostanie on przekazany do ciągu formatowania metody, takie jak <xref:System.Console.WriteLine(System.String)>, jego elementami formatu są rozwiązywane i zwracany ciąg wyniku. 

3. Konwersja ciągu interpolowanego do <xref:System.FormattableString> zmienna, która reprezentuje ciąg formatu złożonego. Inspekcja ciąg formatu złożonego i sposób renderowania w wyniku ciągu może na przykład pomóc w ochronie przed atakami iniekcji w przypadku kompilowania zapytania. A <xref:System.FormattableString> obejmowały:

      - A <xref:System.FormattableString.ToString> przeciążenia, które tworzy ciąg wyniku <xref:System.Globalization.CultureInfo.CurrentCulture>.
      
      - A <xref:System.FormattableString.Invariant%2A> metodę, która tworzy ciąg <xref:System.Globalization.CultureInfo.InvariantCulture>.
      
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, która daje ciąg wynikowy dla określonej kultury. 
  
    Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") pozostają podwójne nawiasy klamrowe do momentu formatowania.  Wszystkie wyrażenia interpolacji zawarte są konwertowane na {0}, {1}i tak dalej.  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a>Zobacz też  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [Dokumentacja języka Visual Basic](index.md)  
 