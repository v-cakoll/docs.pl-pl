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
ms.openlocfilehash: 789478cafc4ed7506d34fb4198531d437683075d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583296"
---
# <a name="concatenation-operators-in-visual-basic"></a>Operatory łączenia w Visual Basic

Operatory łączenia sprzęga wiele ciągów w jeden ciąg. Istnieją dwa operatory łączenia, `+` i `&`. Oba te elementy wykonują podstawową operację łączenia, jak pokazano w poniższym przykładzie.

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

Te operatory mogą również łączyć zmienne `String`, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a>Różnice między dwoma operatorami łączenia

[Operator +](../../../../visual-basic/language-reference/operators/addition-operator.md) ma podstawowy cel dodawania dwóch liczb. Może jednak również łączyć argumenty operacji numerycznych z argumentami operacji ciągu. Operator `+` ma złożony zestaw reguł, które określają, czy dodać, połączyć, sygnalizować błąd kompilatora lub zgłosić wyjątek <xref:System.InvalidCastException> czasu wykonywania.

[Operator &](../../../../visual-basic/language-reference/operators/concatenation-operator.md) jest zdefiniowany tylko dla argumentów operacji `String` i zawsze rozszerza jego operandy do `String`, niezależnie od ustawienia `Option Strict`. Operator `&` jest zalecany w przypadku łączenia ciągów, ponieważ jest zdefiniowany wyłącznie dla ciągów i zmniejsza szanse na wygenerowanie niezamierzonej konwersji.

## <a name="performance-string-and-stringbuilder"></a>Wydajność: ciąg i StringBuilder

Jeśli wykonasz znaczną liczbę operacji manipulowania dla ciągu, takich jak łączenie, usuwanie i zamiany, wydajność może wynikać z klasy <xref:System.Text.StringBuilder> w przestrzeni nazw <xref:System.Text>. Wykonanie dodatkowej instrukcji w celu utworzenia i zainicjowania obiektu <xref:System.Text.StringBuilder> oraz innej instrukcji w celu przekonwertowania jej końcowej wartości na `String`, ale może to spowodować, że <xref:System.Text.StringBuilder> może działać szybciej.

## <a name="see-also"></a>Zobacz także

- [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Typy metod manipulowania ciągami w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)
- [Operatory arytmetyczne w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operatory porównania w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
