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
ms.openlocfilehash: ab268e513e6f019ed651c94deb5e423cfcca7587
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="concatenation-operators-in-visual-basic"></a>Operatory łączenia w Visual Basic
Operatory łączenia dołączenie wielu ciągów w jednym ciągu. Istnieją dwa operatory łączenia, `+` i `&`. Zarówno przeprowadzenia operacji łączenia podstawowe, jak przedstawiono na poniższym przykładzie.  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 Tych operatorów również można łączyć ze sobą `String` zmiennych, jak przedstawiono na poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a>Różnice między dwa operatory łączenia  
 [Operatora +](../../../../visual-basic/language-reference/operators/addition-operator.md) ma swoje podstawowe przeznaczenie dodanie dwóch liczb. Jednak można również łączyć liczbowych argumenty ciągu argumentów. `+` Operator ma złożonego zestawu reguł, które określają, czy dodać, Połącz, sygnału wystąpi błąd kompilatora lub zgłaszać środowiska wykonawczego <xref:System.InvalidCastException> wyjątku.  
  
 [& — Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) jest zdefiniowana tylko dla `String` argumentów i zawsze rozszerzenie argumentów do `String`, niezależnie od ustawienia `Option Strict`. `&` Operator jest zalecane dla ciągów, ponieważ zdefiniowano wyłącznie do ciągów i zmniejsza ryzyko generowania niezamierzone konwersji.  
  
## <a name="performance-string-and-stringbuilder"></a>Wydajność: String i StringBuilder  
 Jeśli to zrobisz, duża liczba manipulacje na ciąg znaków, takich jak łączenie, usuwanie i wystąpienia, wydajność może zysków z <xref:System.Text.StringBuilder> klasy w <xref:System.Text> przestrzeni nazw. Trwa dodatkowe instrukcje Utwórz i zainicjuj <xref:System.Text.StringBuilder> obiektu, a inny instrukcji można przekonwertować jego wartości końcowej na `String`, ale tym razem może odzyskać, ponieważ <xref:System.Text.StringBuilder> może działać szybciej.  
  
## <a name="see-also"></a>Zobacz też  
 [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Typy metod manipulowania ciągami w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)  
 [Operatory arytmetyczne w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Operatory porównania w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Operatory logiczne i bitowe w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
