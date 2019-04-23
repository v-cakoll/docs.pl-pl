---
title: Operand 'IsNot' typu „typename” można porównać tylko z elementem „Nothing”, ponieważ typ „typename” jest typem zerowalnym
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: f19b8cd5f80ba9fd6d1f5a9162b04ee409e24e28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311893"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="f052b-102">Operand 'IsNot' typu „typename” można porównać tylko z elementem „Nothing”, ponieważ typ „typename” jest typem zerowalnym</span><span class="sxs-lookup"><span data-stu-id="f052b-102">'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>
<span data-ttu-id="f052b-103">Zmienna zadeklarowana jako dopuszczającego wartość null ma zostały porównane z wyrażeniem innych niż `Nothing` przy użyciu `IsNot` operatora.</span><span class="sxs-lookup"><span data-stu-id="f052b-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>  
  
 <span data-ttu-id="f052b-104">**Identyfikator błędu:** BC32128</span><span class="sxs-lookup"><span data-stu-id="f052b-104">**Error ID:** BC32128</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f052b-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f052b-105">To correct this error</span></span>  
  
1. <span data-ttu-id="f052b-106">Do innych niż porównania typu dopuszczającego wartość null do wyrażenia `Nothing` przy użyciu `IsNot` operator, wywołanie `GetType` metody na typ dopuszczający wartość null i porównanie wyniku do wyrażenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f052b-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="f052b-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f052b-107">See also</span></span>

- [<span data-ttu-id="f052b-108">Typy wartości dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="f052b-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="f052b-109">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="f052b-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
