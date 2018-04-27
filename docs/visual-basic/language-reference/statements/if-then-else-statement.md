---
title: If...Then...Else — Instrukcja (Visual Basic)
ms.date: 04/16/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: conceptual
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
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1080a17cfcc493175c1e2f3527837030b4254bc2
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
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

## <a name="quick-links-to-example-code"></a>Szybkie linki do przykładowy kod

Ten artykuł zawiera przykłady ilustrujące zastosowań `If`... `Then`... `Else` instrukcji:

* [Przykład składni wielowierszowy](#multi-line)
* [Przykład składni zagnieżdżonych](#nested)
* [Przykład składni jeden wiersz](#single-line)

## <a name="parts"></a>Części  
 `condition`  
 Wymagana. Wyrażenie. Musi być `True` lub `False`, lub umożliwiają niejawnej konwersji na typ danych `Boolean`.  
  
 Jeśli wyrażenie jest [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` zmiennej, która daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), warunek jest traktowany jako wyrażenie `False` i `Else` bloku jest wykonywana.  
  
 `Then`  
 Wymagany w składni pojedynczej linii; Opcjonalnie w wielowierszowym składni.  
  
 `statements`  
 Opcjonalna. Jeden lub więcej następujących instrukcji `If`... `Then` wdrożeniowych Jeśli `condition` daje w wyniku `True`.  
  
 `elseifcondition`  
 Jeśli wymagane `ElseIf` jest obecny. Wyrażenie. Musi być `True` lub `False`, lub umożliwiają niejawnej konwersji na typ danych `Boolean`.  
  
 `elseifstatements`  
 Opcjonalna. Jeden lub więcej następujących instrukcji `ElseIf`... `Then` wdrożeniowych Jeśli `elseifcondition` daje w wyniku `True`.  
  
 `elsestatements`  
 Opcjonalna. Co najmniej jeden instrukcji, które są wykonywane, jeśli nie poprzedniej `condition` lub `elseifcondition` wyrażenie daje w wyniku `True`.  
  
 `End If`  
 Kończy wielowierszowy wersja `If`... `Then`... `Else` bloku.  
  
## <a name="remarks"></a>Uwagi  
  
### <a name="multiline-syntax"></a>Wielowierszowy składni  
 Gdy `If`... `Then`... `Else` napotkano instrukcji `condition` jest testowana. Jeśli `condition` jest `True`, instrukcji `Then` są wykonywane. Jeśli `condition` jest `False`, każdy `ElseIf` instrukcji (jeśli istnieją) są oceniane w kolejności. Gdy `True` `elseifcondition` zostanie znaleziony, natychmiast po skojarzone instrukcje `ElseIf` są wykonywane. Jeśli nie `elseifcondition` daje w wyniku `True`, lub jeśli występują nie `ElseIf` instrukcje, instrukcji `Else` są wykonywane. Po wykonaniu następujące instrukcje `Then`, `ElseIf`, lub `Else`, wykonanie będzie kontynuowane przy użyciu następujących instrukcji `End If`.  
  
 `ElseIf` i `Else` klauzule są opcjonalne. Może mieć tyle `ElseIf` klauzule jako użytkownik ma `If`... `Then`... `Else` instrukcji, ale nie `ElseIf` klauzula może występować po `Else` klauzuli. `If`... `Then`... `Else` instrukcje mogą być zagnieżdżone wewnątrz innych.  
  
 W wielowierszowym składni `If` instrukcja musi być jedyną instrukcją w pierwszym wierszu. `ElseIf`, `Else`, I `End If` instrukcje mogą być poprzedzone tylko etykiety linii. `If`... `Then`... `Else` musi się kończyć bloku `End If` instrukcji.  
  
> [!TIP]
>  [Wybierz... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md) może być bardziej użyteczne podczas oceny jedno wyrażenie, które ma kilka możliwych wartości.  
  
### <a name="single-line-syntax"></a>Składnia jeden wiersz  
 Za pomocą składni jeden wiersz dla jednego warunku kod do wykonania w przypadku wartości true. Jednak składni wielowierszowe zapewnia więcej struktury i elastyczność i jest łatwiej odczytywać, obsługa i debugowania.  
  
 Jakie następujące `Then` — słowo kluczowe jest sprawdzony w celu określenia, czy instrukcja jest jeden wiersz `If`. Jeśli jest inny niż komentarz za `Then` w tym samym wierszu, instrukcja jest traktowane jako jeden wiersz `If` instrukcji. Jeśli `Then` jest nieobecne, musi być uruchomienia wielu linii `If`... `Then`... `Else`.  
  
 W składni jeden wiersz może mieć wiele instrukcji wykonane w wyniku `If`... `Then` decyzji. Wszystkie instrukcje musi znajdować się na tym samym wierszu i być oddzielone dwukropkiem.  

## <a name="multiline-syntax-example"></a>Przykład składni wielowierszowy

<a name="multi-line"></a>
 
 Poniższy przykład przedstawia użycie składni wielowierszowy `If`... `Then`... `Else` instrukcji.  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb?highlight=11,14,17,19)]

## <a name="nested-syntax-example"></a>Przykład składni zagnieżdżonych

<a name="nested"></a>

 Poniższy przykład zawiera zagnieżdżone `If`... `Then`... `Else` instrukcje.  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb?highlight=14,15,17,19,20,21,23,25,26,28)]

## <a name="single-line-syntax-example"></a>Przykład składni jeden wiersz
  
<a name="single-line"></a> Poniższy przykład przedstawia użycie składni jeden wiersz.  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb?highlight=18)]
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [#If...Then...#Else, dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Select...Case, instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [Zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [Struktury decyzji](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [If, operator](../../../visual-basic/language-reference/operators/if-operator.md)
