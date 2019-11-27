---
title: Sub — Wyrażenie
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: d284e629ea0b0a4e9b6eb9e098612bb07c38723b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350898"
---
# <a name="sub-expression-visual-basic"></a>Sub — Wyrażenie (Visual Basic)
Deklaruje parametry i kod, który definiuje podprocedure wyrażenie lambda.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`parameterlist`|Opcjonalna. Lista nazw zmiennych lokalnych, które reprezentują parametry procedury. Nawiasy muszą być obecne nawet wtedy, gdy lista jest pusta. Aby uzyskać więcej informacji, zobacz [Lista parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`statement`|Wymagana. Pojedyncza instrukcja.|  
|`statements`|Wymagana. Lista instrukcji.|  
  
## <a name="remarks"></a>Uwagi  
 *Wyrażenie lambda* jest podprocedurą, która nie ma nazwy i która wykonuje co najmniej jedną instrukcję. Możesz użyć wyrażenia lambda wszędzie, że można użyć typu delegata, z wyjątkiem jako argumentu `RemoveHandler`. Aby uzyskać więcej informacji na temat delegatów i użycie wyrażeń lambda z delegatami, zobacz [instrukcja Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) i [Swobodna konwersja delegata](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda  
 Składnia wyrażenia lambda jest podobna do standardowej procedury podrzędnej. Różnice są następujące:  
  
- Wyrażenie lambda nie ma nazwy.  
  
- Wyrażenie lambda nie może mieć modyfikatora, takiego jak `Overloads` lub `Overrides`.  
  
- Treść wyrażenia lambda pojedynczego wiersza musi być instrukcją, a nie wyrażeniem. Treść może składać się z wywołania procedury Sub, ale nie wywołania procedury funkcji.  
  
- W wyrażeniu lambda wszystkie parametry muszą mieć określone typy danych lub wszystkie parametry muszą zostać wywnioskowane.  
  
- Parametry opcjonalne i `ParamArray` są niedozwolone w wyrażeniach lambda.  
  
- Parametry ogólne są niedozwolone w wyrażeniach lambda.  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się przykład wyrażenia lambda, które zapisuje wartość w konsoli. Przykład pokazuje składnię jednowierszową i wieloliniową wyrażenia lambda dla procedury podrzędnej. Aby uzyskać więcej przykładów, zobacz [lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Zobacz także

- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Wyrażenia lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
- [Swobodna konwersja delegatów](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
