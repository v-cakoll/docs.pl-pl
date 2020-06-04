---
title: If...Then...Else, instrukcja
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
ms.openlocfilehash: 0884b71c24742286e695e720add9d00dd4bfe52b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404592"
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

Ten artykuł zawiera kilka przykładów ilustrujących zastosowanie `If` ... `Then` ...`Else` Merge

- [Przykład składni wielowierszowej](#multi-line)
- [Przykład zagnieżdżonej składni](#nested)
- [Przykład składni jednowierszowej](#single-line)

## <a name="parts"></a>Części

`condition` \
Wymagany. Wyrażenia. Należy oszacować do `True` lub `False` , lub do typu danych, który jest niejawnie konwertowany na `Boolean` .

Jeśli wyrażenie jest zmienną [dopuszczającą wartość null](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` , która zwraca wartość [Nothing](../nothing.md), warunek jest traktowany tak, jakby wyrażenie ma wartość `False` , a `ElseIf` bloki są oceniane, jeśli istnieją, lub `Else` Jeśli blok jest wykonywany, jeśli istnieje.

`Then` \
Wymagane w składni jednowierszowej; opcjonalne w składni wielowierszowej.

`statements` \
Opcjonalny. Jedna lub więcej instrukcji `If` `Then` , które są wykonywane, jeśli są `condition` oceniane `True` .

`elseifcondition` \
Wymagane, jeśli `ElseIf` jest obecny. Wyrażenia. Należy oszacować do `True` lub `False` , lub do typu danych, który jest niejawnie konwertowany na `Boolean` .

`elseifstatements` \
Opcjonalny. Jedna lub więcej instrukcji `ElseIf` `Then` , które są wykonywane, jeśli są `elseifcondition` oceniane `True` .

`elsestatements` \
Opcjonalny. Jedna lub więcej instrukcji, które są wykonywane, jeśli nie zostanie `condition` `elseifcondition` obliczone wyrażenie Previous lub `True` .

`End If` \
Kończy wielowierszową wersję programu `If` ... `Then` ...`Else` odblokowan.

## <a name="remarks"></a>Uwagi

### <a name="multiline-syntax"></a>Składnia wielowierszowa

Gdy `If` ... `Then` ...`Else` Napotkano instrukcję, `condition` jest testowana. Jeśli `condition` jest `True` , `Then` są wykonywane poniższe instrukcje. Jeśli `condition` jest `False` , każda `ElseIf` instrukcja (jeśli istnieje) jest szacowana w kolejności. Gdy `True` `elseifcondition` zostanie znaleziony, są wykonywane instrukcje bezpośrednio po skojarzonych z nimi `ElseIf` . Jeśli `elseifcondition` wartość nie jest równa lub nie ma `True` żadnych `ElseIf` instrukcji, są wykonywane poniższe instrukcje `Else` . Po wykonaniu instrukcji poniżej `Then` , `ElseIf` lub `Else` , wykonywanie jest kontynuowane przy użyciu instrukcji poniżej `End If` .

`ElseIf` `Else` Klauzule i są opcjonalne. Można utworzyć dowolną liczbę `ElseIf` klauzul w `If` ... `Then` ...`Else` Instrukcja, ale żadna `ElseIf` klauzula nie może występować po `Else` klauzuli. `If`...`Then` ...`Else` instrukcje mogą być zagnieżdżane w obrębie siebie nawzajem.

W składni wielowierszowej `If` instrukcja musi być jedyną instrukcją w pierwszym wierszu. `ElseIf`Instrukcje, `Else` i `End If` mogą być poprzedzone tylko etykietą wiersza. `If`... `Then` ...`Else` blok musi kończyć się `End If` instrukcją.

> [!TIP]
> [Wybór... Instrukcja Case](select-case-statement.md) może być bardziej przydatna podczas obliczania pojedynczego wyrażenia, które ma kilka możliwych wartości.

### <a name="single-line-syntax"></a>Składnia jednowierszowa

Można użyć jednowierszowej składni dla jednego warunku z kodem do wykonania, jeśli jest spełniony. Jednak składnia wielowierszowa zapewnia większą strukturę i elastyczność oraz jest łatwiejsza do odczytania, konserwacji i debugowania.

Co następuje po `Then` zbadaniu słowa kluczowego, aby określić, czy instrukcja jest pojedynczą linią `If` . Jeśli coś innego niż komentarz występuje `Then` w tym samym wierszu, instrukcja jest traktowana jako jednowierszowa `If` instrukcja. Jeśli `Then` jest nieobecny, musi to być początek wielu wierszy `If` ... `Then` ...`Else`.

W składni jednowierszowej można wykonać kilka instrukcji w wyniku `If` ... `Then` decyzja. Wszystkie instrukcje muszą znajdować się w tym samym wierszu i być rozdzielone średnikami.

## <a name="multiline-syntax-example"></a>Przykład składni wielowierszowej

<a name="multi-line"></a>

Poniższy przykład ilustruje użycie składni wielowierszowej `If` ... `Then` ...`Else` Merge.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>Przykład zagnieżdżonej składni

<a name="nested"></a>

Poniższy przykład zawiera zagnieżdżonych `If` ... `Then` ...`Else` zatwierdzeni.

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>Przykład składni jednowierszowej

<a name="single-line"></a>Poniższy przykład ilustruje użycie składni jednowierszowej.

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If... Then... #Else — dyrektywy](../directives/if-then-else-directives.md)
- [Select...Case, instrukcja](select-case-statement.md)
- [Zagnieżdżone struktury sterujące](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Struktury decyzji](../../programming-guide/language-features/control-flow/decision-structures.md)
- [Operatory logiczne i bitowe w Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If, operator](../operators/if-operator.md)
