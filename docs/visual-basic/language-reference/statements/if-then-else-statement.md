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
ms.openlocfilehash: d91a913d515f36a6b974850bc30079b000a919b4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842697"
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

## <a name="quick-links-to-example-code"></a>Szybkie łącza do przykładowego kodu

W tym artykule przedstawiono kilka przykładów, które ilustrują zastosowań `If`... `Then`... `Else` instrukcji:

* [Przykład składni wielowierszowy](#multi-line)
* [Przykład składni zagnieżdżonych](#nested)
* [Przykład składni jednowierszowy](#single-line)

## <a name="parts"></a>Części  
 `condition`  
 Wymagana. wyrażenie. Musi być `True` lub `False`, lub do typu danych, który jest niejawnie konwertowany na `Boolean`.  
  
 Jeśli wyrażenie ma [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` zmiennej, która daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), warunek jest traktowany tak, jakby wyrażenie jest `False` i `Else` blok jest wykonywany.  
  
 `Then`  
 Wymagany w składni pojedynczej linii; Opcjonalnie w wielowierszowym składni.  
  
 `statements`  
 Opcjonalna. Jeden lub więcej następujących instrukcji `If`... `Then` które są wykonywane, jeśli `condition` daje w wyniku `True`.  
  
 `elseifcondition`  
 Jeśli wymagane `ElseIf` jest obecny. wyrażenie. Musi być `True` lub `False`, lub do typu danych, który jest niejawnie konwertowany na `Boolean`.  
  
 `elseifstatements`  
 Opcjonalna. Jeden lub więcej następujących instrukcji `ElseIf`... `Then` które są wykonywane, jeśli `elseifcondition` daje w wyniku `True`.  
  
 `elsestatements`  
 Opcjonalna. Jedna lub więcej instrukcji, które są wykonywane, jeśli nie poprzedniej `condition` lub `elseifcondition` wyrażenie daje w wyniku `True`.  
  
 `End If`  
 Kończy wielowierszowy wersję `If`... `Then`... `Else` bloku.  
  
## <a name="remarks"></a>Uwagi  
  
### <a name="multiline-syntax"></a>Składnia wielowierszowy  
 Gdy `If`... `Then`... `Else` napotkania instrukcji `condition` jest testowana. Jeśli `condition` jest `True`instrukcje po `Then` są wykonywane. Jeśli `condition` jest `False`, każdy `ElseIf` — instrukcja (jeśli istnieją) jest obliczane w kolejności. Gdy `True` `elseifcondition` zostanie znaleziony, instrukcje natychmiast po skojarzonego `ElseIf` są wykonywane. Jeśli nie `elseifcondition` daje w wyniku `True`, lub jeśli występują nie `ElseIf` instrukcji, instrukcje po `Else` są wykonywane. Po wykonaniu następujących instrukcji `Then`, `ElseIf`, lub `Else`, wykonywanie jest kontynuowane przy użyciu następujących instrukcji `End If`.  
  
 `ElseIf` i `Else` klauzule są opcjonalne. Masz tyle `ElseIf` klauzule jako użytkownik ma `If`... `Then`... `Else` instrukcji, ale nie `ElseIf` klauzuli może następować po elemencie `Else` klauzuli. `If`... `Then`... `Else` instrukcje mogą być zagnieżdżone wewnątrz innych.  
  
 W składni wielowierszowy `If` instrukcja musi być jedyną instrukcją w pierwszym wierszu. `ElseIf`, `Else`, I `End If` instrukcji może być poprzedzony tylko etykieta wiersza. `If`... `Then`... `Else` bloku musi się kończyć `End If` instrukcji.  
  
> [!TIP]
>  [Wybierz... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md) mogą być bardziej przydatne podczas oceny pojedyncze wyrażenie, które ma kilka możliwych wartości.  
  
### <a name="single-line-syntax"></a>Składnia jednowierszowy  
 Do wykonania, jeśli to PRAWDA, można użyć składni jeden wiersz dla jednego warunku przy użyciu kodu. Jednak składni wielowierszowe zapewnia więcej struktury i elastyczności i łatwiej odczytać, obsługa i debugowania.  
  
 Poniżej `Then` — słowo kluczowe jest sprawdzane w celu określenia, czy instrukcja jest jeden wiersz `If`. Jeśli coś innego niż komentarz pojawia się po `Then` w tym samym wierszu, instrukcja jest traktowany jako jeden wiersz `If` instrukcji. Jeśli `Then` jest nieobecne, należy go z początku wielu linii `If`... `Then`... `Else`.  
  
 W składni jednowierszowego, może mieć wiele instrukcji wykonane w wyniku `If`... `Then` decyzji. Wszystkie instrukcje musi znajdować się na tym samym wierszu i być rozdzielone średnikami.  

## <a name="multiline-syntax-example"></a>Przykład składni wielowierszowy

<a name="multi-line"></a>
 
 Poniższy przykład ilustruje użycie składni wielowierszowy `If`... `Then`... `Else` instrukcji.  
  
 [!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>Przykład składni zagnieżdżonych

<a name="nested"></a>

 Poniższy przykład zawiera zagnieżdżone `If`... `Then`... `Else` instrukcji.  
  
 [!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>Przykład składni jednowierszowy
  
<a name="single-line"></a> Poniższy przykład ilustruje użycie składni jeden wiersz.  
  
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
