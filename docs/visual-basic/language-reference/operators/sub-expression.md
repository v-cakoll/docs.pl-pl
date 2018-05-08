---
title: Sub — Wyrażenie (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 602212e664fa3362742fb1ba0dc033610272d3af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="sub-expression-visual-basic"></a>Sub — Wyrażenie (Visual Basic)
Deklaruje parametry i kod, który definiuje procedurę wyrażenia lambda.  
  
## <a name="syntax"></a>Składnia  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`parameterlist`|Opcjonalna. Lista nazwy zmiennych lokalnych, które reprezentują parametry procedury. Nawiasy musi być obecny, nawet wtedy, gdy lista jest pusta. Aby uzyskać więcej informacji, zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`statement`|Wymagana. Jednej instrukcji.|  
|`statements`|Wymagana. Lista instrukcji.|  
  
## <a name="remarks"></a>Uwagi  
 A *wyrażenia lambda* jest to procedura, która nie ma nazwy i który wykonuje jedną lub więcej instrukcji. Można używać wyrażenia lambda w dowolnym służącego typu delegata, z wyjątkiem jako argument `RemoveHandler`. Aby uzyskać więcej informacji dotyczących obiektów delegowanych i korzystanie z wyrażenia lambda z delegatów, zobacz [instrukcji delegata](../../../visual-basic/language-reference/statements/delegate-statement.md) i [swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda  
 Składnia wyrażenia lambda jest podobny do tego standardowe procedury. Różnice są następujące:  
  
-   Wyrażenia lambda nie ma nazwy.  
  
-   Wyrażenia lambda nie może mieć modyfikatora, takich jak `Overloads` lub `Overrides`.  
  
-   Treść wyrażenia lambda jeden wiersz musi być instrukcję nie wyrażenia. Treść może obejmować wywołaniu procedury sub, ale nie wywołanie procedury function.  
  
-   W wyrażeniu lambda albo wszystkie parametry muszą określono można wywnioskować typów danych lub wszystkich parametrów.  
  
-   Opcjonalne i `ParamArray` parametry są niedozwolone w wyrażeniach lambda.  
  
-   Parametry ogólne są niedozwolone w wyrażeniach lambda.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykład wyrażenia lambda, który zapisuje wartość do konsoli. W przykładzie zarówno jeden wiersz i wielowierszowe składnia wyrażenia lambda dla procedury. Aby uzyskać więcej przykładów, zobacz [wyrażenia Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
