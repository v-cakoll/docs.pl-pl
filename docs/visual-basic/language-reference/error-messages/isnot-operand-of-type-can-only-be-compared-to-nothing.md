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
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a><span data-ttu-id="131f0-102">&#39;IsNot&#39; operand typu &#39;typename&#39; można porównywać tylko z &#39;nic&#39;, ponieważ &#39;typename&#39; jest typem zerowalnym</span><span class="sxs-lookup"><span data-stu-id="131f0-102">&#39;IsNot&#39; operand of type &#39;typename&#39; can only be compared to &#39;Nothing&#39;, because &#39;typename&#39; is a nullable type</span></span>
<span data-ttu-id="131f0-103">Zmienna zadeklarowana jako wartości null ma zostały w porównaniu do wyrażenia innych niż `Nothing` przy użyciu `IsNot` operatora.</span><span class="sxs-lookup"><span data-stu-id="131f0-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>  
  
 <span data-ttu-id="131f0-104">**Identyfikator błędu:** BC32128</span><span class="sxs-lookup"><span data-stu-id="131f0-104">**Error ID:** BC32128</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="131f0-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="131f0-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="131f0-106">Do innych niż porównania typu dopuszczającego wartości null do wyrażenia `Nothing` za pomocą `IsNot` podmiot, wywołania `GetType` metody na typ dopuszczający wartość null i porównanie wyniku do wyrażenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="131f0-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="131f0-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="131f0-107">See Also</span></span>  
 [<span data-ttu-id="131f0-108">Typy wartości dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="131f0-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="131f0-109">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="131f0-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
