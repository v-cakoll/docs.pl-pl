---
title: If...Then...Else — Instrukcja
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
ms.openlocfilehash: f505755caeb9cc3cfeeb1ba83b6de15f48314103
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351162"
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else — Instrukcja (Visual Basic)

Warunkowo wykonuje grupy poleceń w zależności od wartości wyrażenia.

## <a name="syntax"></a>Składnia

```vb
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

Ten artykuł zawiera kilka przykładów, które ilustrują zastosowania instrukcji `If`...`Then`...`Else`:

- [Przykład składni wielowierszowej](#multi-line)
- [Przykład zagnieżdżonej składni](#nested)
- [Przykład składni jednowierszowej](#single-line)

## <a name="parts"></a>Części

`condition` \
Wymagana. Wyrażenia. Należy oszacować do `True` lub `False`lub do typu danych, który jest niejawnie konwertowany do `Boolean`.

Jeśli wyrażenie jest wartością [null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) zmiennej `Boolean`, która zwraca wartość [Nothing](../../../visual-basic/language-reference/nothing.md), warunek jest traktowany tak, jakby wyrażenie jest `False`, a bloki `ElseIf` są oceniane, jeśli istnieją lub jeśli istnieją, blok `Else` jest wykonywany, jeśli istnieje.

`Then` \
Wymagane w składni jednowierszowej; opcjonalne w składni wielowierszowej.

`statements` \
Opcjonalna. Jedna lub więcej instrukcji po `If`...`Then`, które są wykonywane, jeśli `condition` szacuje się `True`.

`elseifcondition` \
Wymagane, jeśli `ElseIf` jest obecny. Wyrażenia. Należy oszacować do `True` lub `False`lub do typu danych, który jest niejawnie konwertowany do `Boolean`.

`elseifstatements` \
Opcjonalna. Jedna lub więcej instrukcji po `ElseIf`...`Then`, które są wykonywane, jeśli `elseifcondition` szacuje się `True`.

`elsestatements` \
Opcjonalna. Jedna lub więcej instrukcji, które są wykonywane, jeśli żadne poprzednie `condition` lub wyrażenie `elseifcondition` nie zwróci `True`.

`End If` \
Kończy wielowierszową wersję `If`...`Then`...`Else` bloku.

## <a name="remarks"></a>Uwagi

### <a name="multiline-syntax"></a>Składnia wielowierszowa

Po napotkaniu instrukcji `If`...`Then`...`Else` `condition` jest testowana. Jeśli `condition` jest `True`, są wykonywane następujące instrukcje `Then`. Jeśli `condition` jest `False`, każda instrukcja `ElseIf` (jeśli istnieje) jest szacowana w kolejności. Po znalezieniu `elseifcondition` `True` są wykonywane instrukcje bezpośrednio po skojarzonych `ElseIf`. Jeśli żaden `elseifcondition` nie jest obliczany do `True`, lub jeśli nie ma żadnych instrukcji `ElseIf`, są wykonywane następujące instrukcje `Else`. Po wykonaniu instrukcji następujących `Then`, `ElseIf`lub `Else`wykonywanie jest kontynuowane przy użyciu instrukcji następujących `End If`.

Klauzule `ElseIf` i `Else` są opcjonalne. W instrukcji `If`...`Then`...`Else` można utworzyć dowolną liczbę klauzul `ElseIf`, ale po klauzuli `ElseIf` nie może wystąpić żadna klauzula `Else`. instrukcje `If`...`Then`...`Else` mogą być zagnieżdżane w obrębie siebie nawzajem.

W składni wielowierszowej instrukcja `If` musi być jedyną instrukcją w pierwszym wierszu. Instrukcje `ElseIf`, `Else`i `End If` mogą być poprzedzone tylko etykietą wiersza. Blok `If`...`Then`...`Else` musi kończyć się instrukcją `End If`.

> [!TIP]
> [Wybór... Instrukcja Case](../../../visual-basic/language-reference/statements/select-case-statement.md) może być bardziej przydatna podczas obliczania pojedynczego wyrażenia, które ma kilka możliwych wartości.

### <a name="single-line-syntax"></a>Składnia jednowierszowa

Można użyć jednowierszowej składni dla jednego warunku z kodem do wykonania, jeśli jest spełniony. Jednak składnia wielowierszowa zapewnia większą strukturę i elastyczność oraz jest łatwiejsza do odczytania, konserwacji i debugowania.

Co następuje po `Then` słowo kluczowe jest badane, aby określić, czy instrukcja jest `If`jednowierszową. Jeśli coś innego niż komentarz pojawia się po `Then` w tym samym wierszu, instrukcja jest traktowana jako jednowierszowa instrukcja `If`. Jeśli nie ma `Then`, musi to być początek `If`wielu wierszy...`Then`...`Else`.

W składni jednowierszowej można wykonać kilka instrukcji w wyniku `If`...`Then` decyzji. Wszystkie instrukcje muszą znajdować się w tym samym wierszu i być rozdzielone średnikami.

## <a name="multiline-syntax-example"></a>Przykład składni wielowierszowej

<a name="multi-line"></a>

Poniższy przykład ilustruje użycie składni wielowierszowej `If`...`Then`...`Else` instrukcji.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>Przykład zagnieżdżonej składni

<a name="nested"></a>

Poniższy przykład zawiera zagnieżdżonych instrukcji `If`...`Then`...`Else`.

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>Przykład składni jednowierszowej

<a name="single-line"></a>Poniższy przykład ilustruje użycie składni jednowierszowej.

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If...Then...#Else, dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Select...Case, instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Struktury decyzji](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If, operator](../../../visual-basic/language-reference/operators/if-operator.md)
