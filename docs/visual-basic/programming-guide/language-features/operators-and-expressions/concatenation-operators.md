---
title: Concatenation — Operatory
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: c123438a86a2c3293a99770107d970535fcdbdf8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388793"
---
# <a name="concatenation-operators-in-visual-basic"></a>Operatory łączenia w Visual Basic

Operatory łączenia sprzęga wiele ciągów w jeden ciąg. Istnieją dwa operatory łączenia `+` i `&` . Oba te elementy wykonują podstawową operację łączenia, jak pokazano w poniższym przykładzie.

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

Te operatory mogą również łączyć `String` zmienne, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a>Różnice między dwoma operatorami łączenia

[Operator +](../../../language-reference/operators/addition-operator.md) ma podstawowy cel dodawania dwóch liczb. Może jednak również łączyć argumenty operacji numerycznych z argumentami operacji ciągu. `+`Operator ma złożony zestaw reguł, które określają, czy dodać, połączyć, sygnalizować błąd kompilatora lub zgłosić wyjątek czasu wykonywania <xref:System.InvalidCastException> .

[Operator&](../../../language-reference/operators/concatenation-operator.md) jest zdefiniowany tylko dla `String` operandów i zawsze rozszerza jego operandy do `String` , niezależnie od ustawienia `Option Strict` . `&`Operator jest zalecany w przypadku łączenia ciągów, ponieważ jest zdefiniowany wyłącznie dla ciągów i zmniejsza szanse na wygenerowanie niezamierzonej konwersji.

## <a name="performance-string-and-stringbuilder"></a>Wydajność: ciąg i StringBuilder

Jeśli wykonasz znaczącą liczbę operacji manipulowania dla ciągu, takich jak łączenie, usuwanie i zamiany, wydajność może wynikać z <xref:System.Text.StringBuilder> klasy w <xref:System.Text> przestrzeni nazw. Wykonanie dodatkowej instrukcji w celu utworzenia i zainicjowania <xref:System.Text.StringBuilder> obiektu, a także innej instrukcji Przekształć jej końcową wartość na `String` , ale możesz odzyskać ten czas, ponieważ <xref:System.Text.StringBuilder> może to przyspieszyć.

## <a name="see-also"></a>Zobacz też

- [Option Strict — Instrukcja](../../../language-reference/statements/option-strict-statement.md)
- [Typy metod manipulowania ciągami w Visual Basic](../strings/types-of-string-manipulation-methods.md)
- [Operatory arytmetyczne w Visual Basic](arithmetic-operators.md)
- [Operatory porównania w Visual Basic](comparison-operators.md)
- [Operatory logiczne i bitowe w Visual Basic](logical-and-bitwise-operators.md)
