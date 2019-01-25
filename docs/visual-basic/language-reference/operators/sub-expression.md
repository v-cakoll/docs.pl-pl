---
title: Sub — Wyrażenie (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: d27ca262aa2349d34d78844e0aea0f96a1ced65c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496312"
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
|`statement`|Wymagana. Pojedynczą instrukcję.|  
|`statements`|Wymagana. Lista instrukcji.|  
  
## <a name="remarks"></a>Uwagi  
 A *wyrażenia lambda* jest to procedura, która nie ma nazwy i który wykonuje jedną lub więcej instrukcji. Użyć wyrażenia lambda w dowolnym miejscu, typu delegata, można użyć z wyjątkiem jako argument do `RemoveHandler`. Aby uzyskać więcej informacji na temat delegatów i użycie wyrażeń lambda z obiektów delegowanych, zobacz [instrukcji delegata](../../../visual-basic/language-reference/statements/delegate-statement.md) i [swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda  
 Składnia wyrażenia lambda przypomina w przypadku standardowe procedury. Różnice są następujące:  
  
-   Wyrażenie lambda nie ma nazwy.  
  
-   Wyrażenie lambda nie może mieć modyfikatora, takich jak `Overloads` lub `Overrides`.  
  
-   Treść wyrażenia lambda w pojedynczej linii musi być instrukcja nie wyrażenia. Treść może składać się po wywołaniu procedury sub, ale nie po wywołaniu procedury function.  
  
-   W wyrażeniu lambda albo wszystkie parametry muszą określono można wywnioskować typów danych lub wszystkich parametrów.  
  
-   Opcjonalne i `ParamArray` parametry są niedozwolone w wyrażeniach lambda.  
  
-   Parametry ogólne są niedozwolone w wyrażeniach lambda.  
  
## <a name="example"></a>Przykład  
 Oto przykład wyrażenie lambda, która zapisuje wartości do konsoli. W przykładzie pokazano oba jeden wiersz i wielowierszowe składnia wyrażenia lambda do procedurę. Aby uzyskać więcej przykładów, zobacz [wyrażeń Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
- [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
