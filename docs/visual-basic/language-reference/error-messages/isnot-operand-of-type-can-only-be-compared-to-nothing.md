---
title: '&#39;IsNot&#39; operand typu &#39;typename&#39; można porównywać tylko z &#39;nic&#39;, ponieważ &#39;typename&#39; jest typem zerowalnym'
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 44cc17c73b476e5e322b9b58b021bc7bcd63167f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a>&#39;IsNot&#39; operand typu &#39;typename&#39; można porównywać tylko z &#39;nic&#39;, ponieważ &#39;typename&#39; jest typem zerowalnym
Zmienna zadeklarowana jako wartości null ma zostały w porównaniu do wyrażenia innych niż `Nothing` przy użyciu `IsNot` operatora.  
  
 **Identyfikator błędu:** BC32128  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Do innych niż porównania typu dopuszczającego wartości null do wyrażenia `Nothing` za pomocą `IsNot` podmiot, wywołania `GetType` metody na typ dopuszczający wartość null i porównanie wyniku do wyrażenia, jak pokazano w poniższym przykładzie.  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy wartości dopuszczających wartości null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)
