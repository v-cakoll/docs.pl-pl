---
title: Operatory łączenia w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: 124f0ca0cd01d7fd218fd89dfb78e70fe8aad9e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864941"
---
# <a name="concatenation-operators-in-visual-basic"></a>Operatory łączenia w Visual Basic
Concatenation — operatory Dołącz do wielu ciągów w jeden ciąg. Istnieją dwa operatory łączenia, `+` i `&`. Zarówno przeprowadzenie operacji łączenia podstawowe, jak w poniższym przykładzie pokazano.  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 Te operatory również można łączyć ze sobą `String` zmiennych, jak w poniższym przykładzie pokazano.  
  
 [!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a>Różnice między dwa operatory łączenia  
 [+ — Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) ma głównym celem dodanie dwóch liczb. Jednak można również połączyć operandy liczbową argumentów ciągu. `+` Operator ma złożonego zestawu reguł, które określają, czy dodawanie, łączenie, zasygnalizować błąd kompilatora lub zgłosić środowiska wykonawczego <xref:System.InvalidCastException> wyjątku.  
  
 [& — Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) jest zdefiniowane tylko dla `String` argumentów i zawsze rozszerza się jego operandy `String`, niezależnie od ustawienia `Option Strict`. `&` Operator jest zalecane dla ciągów, ponieważ zdefiniowano wyłącznie dla ciągów i zmniejsza ryzyko generowania konwersję niezamierzone.  
  
## <a name="performance-string-and-stringbuilder"></a>Wydajność: Parametry i StringBuilder  
 Jeśli to zrobisz, znaczna liczba manipulacje na ciąg, takie jak konkatenacji, usuwania i zamiany, wydajność może być zysk z <xref:System.Text.StringBuilder> klasy w <xref:System.Text> przestrzeni nazw. Zajmuje dodatkowy instrukcji, aby utworzyć i zainicjować <xref:System.Text.StringBuilder> obiekt i innej instrukcji jego końcowa wartość, aby przekonwertować `String`, ale może odzyskać to czas, ponieważ <xref:System.Text.StringBuilder> może działać szybciej.  
  
## <a name="see-also"></a>Zobacz także

- [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Typy metod manipulowania ciągami w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)
- [Operatory arytmetyczne w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operatory porównania w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
