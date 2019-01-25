---
title: '&#39;Jest&#39; wymaga argumentów operacji, które mają typ referencyjny, ale ten argument operacji ma typ wartości &#39; &lt;typename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 0b3f80e98087e455ec730dea8c57478528e9259c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722923"
---
# <a name="39is39-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-39lttypenamegt39"></a>&#39;Jest&#39; wymaga argumentów operacji, które mają typ referencyjny, ale ten argument operacji ma typ wartości &#39; &lt;typename&gt;&#39;
`Is` Operator porównania określa, czy dwie zmienne do obiektu odnoszą się do tego samego wystąpienia. To porównanie nie jest zdefiniowany dla typów wartości.  
  
 **Identyfikator błędu:** BC30020  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj operatora porównania arytmetyczne odpowiednie lub `Like` operator do porównywania dwóch typów wartości.  
  
## <a name="see-also"></a>Zobacz także
- [Is, operator](../../../visual-basic/language-reference/operators/is-operator.md)
- [Like, operator](../../../visual-basic/language-reference/operators/like-operator.md)
- [Operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md)
