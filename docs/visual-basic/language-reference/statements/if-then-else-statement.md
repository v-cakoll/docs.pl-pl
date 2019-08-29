---
title: If...Then...Else — Instrukcja (Visual Basic)
ms.date: 04/16/2018
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
ms.openlocfilehash: e0b365afaa8cf7dff130cf01d2937be629e5f7a8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106518"
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else — Instrukcja (Visual Basic)

Warunkowo wykonuje grupy poleceń w zależności od wartości wyrażenia.

## <a name="syntax"></a>Składnia

```
' Multiline syntax:
If condition [ Then ]
    [ statements ]
[ ElseIf elseifcondition [ Then ]
    [ elseifstatements ] ]
[ Else
    [ elsestatements ] ]
End If

' Single-line syntax:
If condition Then [ statements ] [ Else [ elsestatements ] ]
```

## <a name="quick-links-to-example-code"></a>Szybkie linki do przykładowego kodu

Ten artykuł zawiera kilka przykładów ilustrujących zastosowanie `If`... `Then`... `Else` instrukcja:

- [Przykład składni wielowierszowej](#multi-line)
- [Przykład zagnieżdżonej składni](#nested)
- [Przykład składni jednowierszowej](#single-line)

## <a name="parts"></a>Części

`condition` \
Wymagane. Wyrażenia. Należy oszacować do `True` lub `False`, lub do typu danych, który jest niejawnie konwertowany `Boolean`na.

Jeśli wyrażenie jest zmienną dopuszczającą [wartość null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` , która zwraca wartość [Nothing](../../../visual-basic/language-reference/nothing.md), warunek jest traktowany jak `False` `Else` wtedy, gdy wyrażenie jest i jest wykonywane.

`Then` \
Wymagane w składni jednowierszowej; opcjonalne w składni wielowierszowej.

`statements` \
Opcjonalny. Jedna lub więcej instrukcji po `If`... są wykonywane, jeśli `condition` są oceniane `True`. `Then`

`elseifcondition` \
Wymagane, `ElseIf` jeśli jest obecny. Wyrażenia. Należy oszacować do `True` lub `False`, lub do typu danych, który jest niejawnie konwertowany `Boolean`na.

`elseifstatements` \
Opcjonalny. Jedna lub więcej instrukcji po `ElseIf`... są wykonywane, jeśli `elseifcondition` są oceniane `True`. `Then`

`elsestatements` \
Opcjonalny. Jedna lub więcej instrukcji, które są wykonywane, jeśli `condition` nie `elseifcondition` zostanie obliczone `True`wyrażenie Previous lub.

`End If` \
Kończy wielowierszową wersję programu `If`... `Then`... `Else` blok.

## <a name="remarks"></a>Uwagi

### <a name="multiline-syntax"></a>Składnia wielowierszowa

`If`Gdy... `Then`... Napotkano instrukcję, `condition` jest testowana. `Else` Jeśli `condition` `Then` jest `True`, są wykonywane poniższe instrukcje. Jeśli `condition` jest `False`, każda`ElseIf` instrukcja (jeśli istnieje) jest szacowana w kolejności. Gdy zostanie znaleziony, są wykonywane instrukcje bezpośrednio po skojarzonych z `ElseIf`nimi. `True` `elseifcondition` Jeśli wartość `elseifcondition` nie jest równa `True`lub nie ma żadnych `ElseIf` instrukcji, są wykonywane poniższe `Else` instrukcje. Po wykonaniu instrukcji poniżej `Then` `ElseIf`, lub `Else`, wykonywanie jest kontynuowane przy użyciu instrukcji `End If`poniżej.

Klauzule `Else`isąopcjonalne. `ElseIf` Można utworzyć dowolną liczbę `ElseIf` klauzul `If`w... `Then`... Instrukcja, ale żadna `ElseIf` `Else` klauzula nie może występować po klauzuli. `Else` `If`... `Then`... `Else` instrukcje mogą być zagnieżdżane w obrębie siebie nawzajem.

W składni `If` wielowierszowej instrukcja musi być jedyną instrukcją w pierwszym wierszu. Instrukcje `ElseIf`, `Else` i`End If` mogą być poprzedzone tylko etykietą wiersza. `If`... `Then`... blok musi kończyć `End If` się instrukcją. `Else`

> [!TIP]
> [Wybór... Instrukcja Case](../../../visual-basic/language-reference/statements/select-case-statement.md) może być bardziej przydatna podczas obliczania pojedynczego wyrażenia, które ma kilka możliwych wartości.

### <a name="single-line-syntax"></a>Składnia jednowierszowa

Można użyć jednowierszowej składni dla jednego warunku z kodem do wykonania, jeśli jest spełniony. Jednak składnia wielowierszowa zapewnia większą strukturę i elastyczność oraz jest łatwiejsza do odczytania, konserwacji i debugowania.

Co następuje po `Then` zbadaniu słowa kluczowego, aby określić, czy instrukcja jest pojedynczą linią. `If` Jeśli coś innego niż komentarz występuje `Then` w tym samym wierszu, instrukcja jest traktowana jako jednowierszowa `If` instrukcja. Jeśli `Then` jest nieobecny, musi to być początek wielu wierszy `If`... `Then`... `Else`.

W składni jednowierszowej można wykonać kilka instrukcji w wyniku `If`... `Then` decyzja. Wszystkie instrukcje muszą znajdować się w tym samym wierszu i być rozdzielone średnikami.

## <a name="multiline-syntax-example"></a>Przykład składni wielowierszowej

<a name="multi-line"></a>

Poniższy przykład ilustruje użycie składni `If`wielowierszowej... `Then`... `Else` instrukcja.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>Przykład zagnieżdżonej składni

<a name="nested"></a>

Poniższy przykład zawiera zagnieżdżonych `If`... `Then`... `Else` instrukcji.

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>Przykład składni jednowierszowej

<a name="single-line"></a>Poniższy przykład ilustruje użycie składni jednowierszowej.

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If...Then...#Else, dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Instrukcja Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Struktury decyzji](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If, operator](../../../visual-basic/language-reference/operators/if-operator.md)
