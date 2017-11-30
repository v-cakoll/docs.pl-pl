---
title: "Ciągi interpolowane (Visual Basic)"
ms.date: 10/31/2017
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f865d5a7167847bf869d70a39570413dac271a2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="interpolated-strings-visual-basic-reference"></a>Ciągi interpolowane (odwołanie w Visual Basic)

Użyta do skonstruowania ciągów.  Interpolowane ciąg wygląda jak ciąg szablonu, który zawiera *interpolowane wyrażenia*.  Ciągu interpolowanym zwraca ciąg, który zastępuje interpolowanego wyrażenia, które zawiera ich reprezentacji ciągu. Ta funkcja jest dostępna w języku Visual Basic 14 i nowszych wersjach.

Argumenty ciągu interpolowanym są łatwiejsze do zrozumienia niż [ciąg formatu złożonego](../../../../standard/base-types/composite-formatting.md#composite-format-string).  Na przykład ciągu interpolowanym  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
zawiera dwa interpolowanego wyrażenia, "{name}" i "{godziny: hh}". Ciąg formatu złożonego równoważne jest:

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

Struktura ciągu interpolowanym jest:  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

gdzie: 

- *szerokość pola* jest całkowita wskazującą liczbę znaków w tym polu. Jeśli jest dodatnia, pole jest wyrównany do prawej; Jeśli jest ujemna, wyrównane do lewej. 

- *Ciąg formatu* jest odpowiednia dla typu obiektu jest sformatowana ciągu formatu. Na przykład w przypadku <xref:System.DateTime> wartości, może to być [standardowa Data i godzina ciąg formatu](~/docs/standard/base-types/standard-date-and-time-format-strings.md) takich jak "D" lub "d".

> [!IMPORTANT]
> Nie może zawierać żadnych spacji między `$` i `"` zaczynającym się ciąg. To powoduje wystąpienie błędu kompilatora.

 Można użyć ciągu interpolowanym dowolnym można użyć literału ciągu.  W ciągu interpolowanym jest następuje za każdym razem, który wykonuje kod w ciągu interpolowanym. Dzięki temu można rozdzielić definicji i oceny ciągu interpolowanym.  
  
 Aby uwzględnić nawias klamrowy ("{" lub "}") w ciągu interpolowanym, użyj dwa nawiasy klamrowe, "{{" lub "}}".  Zobacz sekcję niejawne konwersje więcej szczegółów.  

Jeśli w ciągu interpolowanym zawiera znaki o specjalnym znaczeniu w ciągu interpolowanym, takie jak znak cudzysłowu ("), dwukropek (:) lub przecinkami (,), należy wpisywany je Jeśli występują one w tekście literału lub powinny one zostać włączone w wyrażeniu rozdzielone nawiasy, jeśli są one uwzględnione w wyrażeniu interpolowane elementy języka. Poniższy przykład specjalne znaki cudzysłowu, aby je uwzględnić w ciągu wynik i używa nawiasów do rozdzielenia wyrażenie `(age == 1 ? "" : "s")` , aby dwukropkiem nie jest interpretowany jako rozpoczynający się ciągiem formatu.

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a>Niejawne konwersje  

Istnieją trzy niejawne konwersje typów w ciągu interpolowanym:  

1. Konwersja ciągu interpolowanym do <xref:System.String>. Poniższy przykład zwraca ciąg, którego wyrażenia ciągu interpolowanym zostały zastąpione ich reprezentacji ciągu. Na przykład:

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   To końcowy wynik interpretacji ciągu. Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") są konwertowane na jednym nawias klamrowy. 

2. Konwersja ciągu interpolowanym do <xref:System.IFormattable> ciągi zmiennej, która umożliwia tworzenie wielu wyników z zawartością specyficzne dla kultury z jednej <xref:System.IFormattable> wystąpienia. Jest to przydatne w przypadku łącznie z czynności, takich jak poprawne formaty liczb i dat dla poszczególnych kultur.  Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") pozostać jako podwójne nawiasy klamrowe do formatu ciągu wywołując jawnie lub niejawnie <xref:System.Object.ToString> metody.  Wszystkie wyrażenia interpolacji zawarte są konwertowane na {0}, {1} i tak dalej.  

   W poniższym przykładzie użyto odbicia, aby wyświetlić elementy członkowskie, a także wartości pola i właściwości <xref:System.IFormattable> zmiennej, która jest tworzona na podstawie ciągu interpolowanym. Przekazuje również <xref:System.IFormattable> zmienną <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody.

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   Należy pamiętać, że ciągu interpolowanym mogą być kontrolowane tylko przy użyciu odbicia. Jeśli jest przekazywana do ciągu formatowania metody, takie jak <xref:System.Console.WriteLine(System.String)>, jego format elementy zostaną rozwiązane i został zwrócony ciąg wyniku. 

3. Konwersja ciągu interpolowanym do <xref:System.FormattableString> zmienna, która reprezentuje ciąg formatu złożonego. Zapoznanie się ciąg formatu złożone i sposób renderowania w związku z tym ciąg może na przykład pomóc w ochronie przed atakami iniekcji zostały kompilowania zapytania. A <xref:System.FormattableString> obejmuje również:

      - A <xref:System.FormattableString.ToString> przeciążenia, które tworzy ciąg wynik <xref:System.Globalization.CultureInfo.CurrentCulture>.
      
      - A <xref:System.FormattableString.Invariant%2A> metodę, która tworzy ciąg <xref:System.Globalization.CultureInfo.InvariantCulture>.
      
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> metodę, która tworzy ciąg wynik określonej kultury. 
  
    Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") pozostają jako podwójne nawiasy klamrowe, dopóki nie zostanie sformatowany.  Wszystkie wyrażenia interpolacji zawarte są konwertowane na {0}, {1} i tak dalej.  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a>Zobacz też  
f<xref:System.IFormattable?displayProperty=nameWithType>   
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [Dokumentacja języka Visual Basic](index.md)  
 