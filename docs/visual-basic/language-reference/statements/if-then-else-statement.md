---
title: "If...Then...Else — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 898b72055345e88ca35f805de211c0c57cd74200
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else — Instrukcja (Visual Basic)
Warunkowo wykonuje grupy poleceń w zależności od wartości wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
' Multiple-line syntax:  
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
  
## <a name="parts"></a>Części  
 `condition`  
 Wymagany. Wyrażenie. Musi być `True` lub `False`, lub umożliwiają niejawnej konwersji na typ danych `Boolean`.  
  
 Jeśli wyrażenie jest [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` zmiennej, która daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), warunek jest traktowana tak, jakby to wyrażenie nie jest `True`i `Else` blok wykonywane.  
  
 `Then`  
 Wymagany w składni pojedynczej linii; Opcjonalnie w wielu wierszach składni.  
  
 `statements`  
 Opcjonalny. Jeden lub więcej następujących instrukcji `If`... `Then` wdrożeniowych Jeśli `condition` daje w wyniku `True`.  
  
 `elseifcondition`  
 Jeśli wymagane `ElseIf` jest obecny. Wyrażenie. Musi być `True` lub `False`, lub umożliwiają niejawnej konwersji na typ danych `Boolean`.  
  
 `elseifstatements`  
 Opcjonalny. Jeden lub więcej następujących instrukcji `ElseIf`... `Then` wdrożeniowych Jeśli `elseifcondition` daje w wyniku `True`.  
  
 `elsestatements`  
 Opcjonalny. Co najmniej jeden instrukcji, które są wykonywane, jeśli nie poprzedniej `condition` lub `elseifcondition` wyrażenie daje w wyniku `True`.  
  
 `End If`  
 Kończy `If`... `Then`... `Else` bloku.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="multiple-line-syntax"></a>Składnia wielu linii  
 Gdy `If`... `Then`... `Else` napotkano instrukcji `condition` jest testowana. Jeśli `condition` jest `True`, instrukcji `Then` są wykonywane. Jeśli `condition` jest `False`, każdy `ElseIf` instrukcji (jeśli istnieją) są oceniane w kolejności. Gdy `True``elseifcondition` zostanie znaleziony, natychmiast po skojarzone instrukcje `ElseIf` są wykonywane. Jeśli nie `elseifcondition` daje w wyniku `True`, lub jeśli występują nie `ElseIf` instrukcje, instrukcji `Else` są wykonywane. Po wykonaniu następujące instrukcje `Then`, `ElseIf`, lub `Else`, wykonanie będzie kontynuowane przy użyciu następujących instrukcji `End If`.  
  
 `ElseIf` i `Else` klauzule są opcjonalne. Może mieć tyle `ElseIf` klauzule jako użytkownik ma `If`... `Then`... `Else` instrukcji, ale nie `ElseIf` klauzula może występować po `Else` klauzuli. `If`... `Then`... `Else` instrukcje mogą być zagnieżdżone wewnątrz innych.  
  
 W wielu wierszach składni `If` instrukcja musi być jedyną instrukcją w pierwszym wierszu. `ElseIf`, `Else`, I `End If` instrukcje mogą być poprzedzone tylko etykiety linii. `If`... `Then`... `Else` musi się kończyć bloku `End If` instrukcji.  
  
> [!TIP]
>  [Wybierz... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md) może być bardziej użyteczne podczas oceny jedno wyrażenie, które ma kilka możliwych wartości.  
  
## <a name="single-line-syntax"></a>Składnia jeden wiersz  
 Za pomocą składni jeden wiersz dla testów krótkie, proste. Jednak składni wielowierszowe zapewnia więcej struktury i elastyczność i ułatwia odczytu, obsługa i debugowania.  
  
 Jakie następujące `Then` — słowo kluczowe jest sprawdzony w celu określenia, czy instrukcja jest jeden wiersz `If`. Jeśli jest inny niż komentarz za `Then` w tym samym wierszu, instrukcja jest traktowane jako jeden wiersz `If` instrukcji. Jeśli `Then` jest nieobecne, musi być uruchomienia wielu linii `If`... `Then`... `Else`.  
  
 W składni jeden wiersz może mieć wiele instrukcji wykonane w wyniku `If`... `Then` decyzji. Wszystkie instrukcje musi znajdować się na tym samym wierszu i być oddzielone dwukropkiem.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie składni wielowierszowe `If`... `Then`... `Else` instrukcji.  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera zagnieżdżone `If`... `Then`... `Else` instrukcje.  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie składni jeden wiersz.  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [#If... Then... #Else — dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Wybierz... Case-instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Struktury decyzji](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Jeśli — Operator](../../../visual-basic/language-reference/operators/if-operator.md)
