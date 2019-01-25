---
title: Nie można przekonwertować typu anonimowego na drzewo wyrażenia, ponieważ zawiera on pole wykorzystywane w inicjowaniu innego pola
ms.date: 07/20/2015
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
ms.openlocfilehash: a6ddbaa358709fe306f1529112d1f2bd0a715a91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646948"
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a><span data-ttu-id="1577a-102">Nie można przekonwertować typu anonimowego na drzewo wyrażenia, ponieważ zawiera on pole wykorzystywane w inicjowaniu innego pola</span><span class="sxs-lookup"><span data-stu-id="1577a-102">Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field</span></span>
<span data-ttu-id="1577a-103">Kompilator nie akceptuje konwersja anonimowego na drzewo wyrażenia, po jednej właściwości typu anonimowego służy do inicjowania innej właściwości typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="1577a-103">The compiler does not accept conversion of an anonymous to an expression tree when one property of the anonymous type is used to initialize another property of the anonymous type.</span></span> <span data-ttu-id="1577a-104">Na przykład w poniższym kodzie `Prop1` jest zadeklarowanych na liście inicjowania i następnie użyta jako wartość początkową dla `Prop2`.</span><span class="sxs-lookup"><span data-stu-id="1577a-104">For example, in the following code, `Prop1` is declared in the initialization list and then used as the initial value for `Prop2`.</span></span>  
  
```vb  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="1577a-105">**Identyfikator błędu:** BC36548</span><span class="sxs-lookup"><span data-stu-id="1577a-105">**Error ID:** BC36548</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1577a-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1577a-106">To correct this error</span></span>  
  
-   <span data-ttu-id="1577a-107">Przypisz wartość początkową dla `Prop1` do zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="1577a-107">Assign the initial value for `Prop1` to a local variable.</span></span> <span data-ttu-id="1577a-108">Przypisz tej zmiennej na wartość oba `Prop1` i `Prop2`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1577a-108">Assign that variable to both `Prop1` and `Prop2`, as shown in the following code.</span></span>  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1577a-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1577a-109">See also</span></span>

- [<span data-ttu-id="1577a-110">Typy anonimowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1577a-110">Anonymous Types (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="1577a-111">Drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1577a-111">Expression Trees (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="1577a-112">Instrukcje: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1577a-112">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>](../../programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md)
