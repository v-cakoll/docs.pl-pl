---
title: "Ciągi interpolowane (C#)"
ms.date: 10/18/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0569636bde875d2d0d8921a544273f3214d05188
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="interpolated-strings-c-reference"></a>Ciągi interpolowane (odwołanie w C#)

Użyta do skonstruowania ciągów.  Interpolowane ciąg wygląda jak ciąg szablonu, który zawiera *interpolowane wyrażenia*.  Ciągu interpolowanym zwraca ciąg, który zastępuje interpolowanego wyrażenia, które zawiera ich reprezentacji ciągu. Ta funkcja jest dostępna w C# 6 i nowsze wersje.

Argumenty ciągu interpolowanym są łatwiejsze do zrozumienia niż [ciąg formatu złożonego](../../../standard/base-types/composite-formatting.md#composite-format-string).  Na przykład ciągu interpolowanym  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}");
```  
zawiera dwa interpolowanego wyrażenia, "{name}" i "{godziny: hh}". Ciąg formatu złożonego równoważne jest:

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

Struktura ciągu interpolowanym jest:  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

gdzie: 

- *szerokość pola* jest całkowita wskazującą liczbę znaków w tym polu. Jeśli jest dodatnia, pole jest wyrównany do prawej; Jeśli jest ujemna, wyrównane do lewej. 

- *Ciąg formatu* jest odpowiednia dla typu obiektu jest sformatowana ciągu formatu. Na przykład w przypadku <xref:System.DateTime> wartości, może to być standardowa Data i godzina ciąg formatu, takie jak "D" lub "d".

> [!IMPORTANT]
> Nie może zawierać żadnych spacji między `$` i `"` zaczynającym się ciąg. To powoduje błąd w czasie kompilacji.

 Można użyć ciągu interpolowanym dowolnym można użyć literału ciągu.  W ciągu interpolowanym jest następuje za każdym razem, który wykonuje kod w ciągu interpolowanym. Dzięki temu można rozdzielić definicji i oceny ciągu interpolowanym.  
  
 Aby uwzględnić nawias klamrowy ("{" lub "}") w ciągu interpolowanym, użyj dwa nawiasy klamrowe, "{{" lub "}}".  Zobacz sekcję niejawne konwersje więcej szczegółów.  

Jeśli w ciągu interpolowanym zawiera znaki o specjalnym znaczeniu w ciągu interpolowanym, takie jak znak cudzysłowu ("), dwukropek (:) lub przecinkami (,), należy wpisywany je Jeśli występują one w tekście literału lub powinny one zostać włączone w wyrażeniu rozdzielone nawiasy, jeśli są one uwzględnione w wyrażeniu interpolowane elementy języka. Poniższy przykład specjalne znaki cudzysłowu, aby je uwzględnić w ciągu wynik i używa nawiasów do rozdzielenia wyrażenie `(age == 1 ? "" : "s")` , aby dwukropkiem nie jest interpretowany jako rozpoczynający się ciągiem formatu.

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

Użyj ciągi interpolowane z Verbatim `$` następuje znak `@` znaków. Aby uzyskać więcej informacji na temat ciągi verbatim zobacz [ciąg](string.md) tematu. Następujący kod to zmodyfikowana wersja poprzedniego fragmentu przy użyciu ciągu dosłownego wyrażenia interpolowane:

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings5.cs#1)]  

Zmiany formatowania są niezbędne, ponieważ ciągi verbatim podlega `\` sekwencje specjalne.

> [!IMPORTANT]
> `$` Token musi występować przed `@` token w ciągu interpolowanym dosłownego wyrażenia.


## <a name="implicit-conversions"></a>Niejawne konwersje  

Istnieją trzy niejawne konwersje typów w ciągu interpolowanym:  

1. Konwersja ciągu interpolowanym do <xref:System.String>. Poniższy przykład zwraca ciąg, którego wyrażenia ciągu interpolowanym zostały zastąpione ich reprezentacji ciągu. Na przykład:

   [!code-csharp[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   To końcowy wynik interpretacji ciągu. Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") są konwertowane na jednym nawias klamrowy. 

2. Konwersja ciągu interpolowanym do <xref:System.IFormattable> ciągi zmiennej, która umożliwia tworzenie wielu wyników z zawartością specyficzne dla kultury z jednej <xref:System.IFormattable> wystąpienia. Jest to przydatne w przypadku łącznie z czynności, takich jak poprawne formaty liczb i dat dla poszczególnych kultur.  Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") pozostać jako podwójne nawiasy klamrowe do formatu ciągu wywołując jawnie lub niejawnie <xref:System.Object.ToString> metody.  Wszystkie wyrażenia interpolacji zawarte są konwertowane na {0}, {1} i tak dalej.  

   W poniższym przykładzie użyto odbicia, aby wyświetlić elementy członkowskie, a także wartości pola i właściwości <xref:System.IFormattable> zmiennej, która jest tworzona na podstawie ciągu interpolowanym. Przekazuje również <xref:System.IFormattable> zmienną <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody.

   [!code-csharp[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   Należy pamiętać, że ciągu interpolowanym mogą być kontrolowane tylko przy użyciu odbicia. Jeśli jest przekazywana do ciągu formatowania metody, takie jak <xref:System.Console.WriteLine(System.String)>, jego format elementy zostaną rozwiązane i został zwrócony ciąg wyniku. 

3. Konwersja ciągu interpolowanym do <xref:System.FormattableString> zmienna, która reprezentuje ciąg formatu złożonego. Zapoznanie się ciąg formatu złożone i sposób renderowania w związku z tym ciąg może na przykład pomóc w ochronie przed atakami iniekcji zostały kompilowania zapytania. <xref:System.FormattableString> zawiera również <xref:System.FormattableString.ToString> przeciążenia, które pozwalają tworzyć ciągów wynikowych dla <xref:System.Globalization.CultureInfo.InvariantCulture> i <xref:System.Globalization.CultureInfo.CurrentCulture>.  Wszystkie wystąpienia podwójne nawiasy klamrowe ("{{" i "}}") pozostają podwójne nawiasy klamrowe, dopóki nie zostanie sformatowany.  Wszystkie wyrażenia interpolacji zawarte są konwertowane na {0}, {1} i tak dalej.  

   [!code-csharp[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a>Specyfikacja języka  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
