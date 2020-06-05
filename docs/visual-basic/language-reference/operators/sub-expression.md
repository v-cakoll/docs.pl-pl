---
title: Sub, wyrażenie
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: f862730220d0595faecaa915b1eaad2a3cdc0053
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406318"
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
|`parameterlist`|Opcjonalny. Lista nazw zmiennych lokalnych, które reprezentują parametry procedury. Nawiasy muszą być obecne nawet wtedy, gdy lista jest pusta. Aby uzyskać więcej informacji, zobacz [Lista parametrów](../statements/parameter-list.md).|  
|`statement`|Wymagany. Pojedyncza instrukcja.|  
|`statements`|Wymagany. Lista instrukcji.|  
  
## <a name="remarks"></a>Uwagi  
 *Wyrażenie lambda* jest podprocedurą, która nie ma nazwy i która wykonuje co najmniej jedną instrukcję. Wyrażenia lambda można użyć w dowolnym miejscu, w którym można użyć typu delegata, z wyjątkiem argumentu `RemoveHandler` . Aby uzyskać więcej informacji na temat delegatów i użycie wyrażeń lambda z delegatami, zobacz [instrukcja Delegate](../statements/delegate-statement.md) i [Swobodna konwersja delegata](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Składnia wyrażenia lambda  
 Składnia wyrażenia lambda jest podobna do standardowej procedury podrzędnej. Różnice są następujące:  
  
- Wyrażenie lambda nie ma nazwy.  
  
- Wyrażenie lambda nie może mieć modyfikatora, takiego jak `Overloads` lub `Overrides` .  
  
- Treść wyrażenia lambda pojedynczego wiersza musi być instrukcją, a nie wyrażeniem. Treść może składać się z wywołania procedury Sub, ale nie wywołania procedury funkcji.  
  
- W wyrażeniu lambda wszystkie parametry muszą mieć określone typy danych lub wszystkie parametry muszą zostać wywnioskowane.  
  
- Parametry opcjonalne i `ParamArray` są niedozwolone w wyrażeniach lambda.  
  
- Parametry ogólne są niedozwolone w wyrażeniach lambda.  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się przykład wyrażenia lambda, które zapisuje wartość w konsoli. Przykład pokazuje składnię jednowierszową i wieloliniową wyrażenia lambda dla procedury podrzędnej. Aby uzyskać więcej przykładów, zobacz [lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Zobacz też

- [Sub, instrukcja](../statements/sub-statement.md)
- [Wyrażenia lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [Operatory i wyrażenia](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Instrukcje](../../programming-guide/language-features/statements.md)
- [Swobodna konwersja delegatów](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
