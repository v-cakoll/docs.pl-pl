---
title: "Nie można przekonwertować typu anonimowego na drzewo wyrażenia, ponieważ zawiera on pole wykorzystywane w inicjowaniu innego pola"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords:
- BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c2cf8a40060359393807cfb648c46fef9ed853af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a><span data-ttu-id="5f8d9-102">Nie można przekonwertować typu anonimowego na drzewo wyrażenia, ponieważ zawiera on pole wykorzystywane w inicjowaniu innego pola</span><span class="sxs-lookup"><span data-stu-id="5f8d9-102">Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field</span></span>
<span data-ttu-id="5f8d9-103">Kompilator nie akceptuje konwersja anonimowego na drzewo wyrażenia, po jednej właściwości typu anonimowego jest używane do inicjowania innej właściwości typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="5f8d9-103">The compiler does not accept conversion of an anonymous to an expression tree when one property of the anonymous type is used to initialize another property of the anonymous type.</span></span> <span data-ttu-id="5f8d9-104">Na przykład w poniższym kodzie `Prop1` jest zadeklarowany w liście inicjowania i następnie używany jako początkowa wartość `Prop2`.</span><span class="sxs-lookup"><span data-stu-id="5f8d9-104">For example, in the following code, `Prop1` is declared in the initialization list and then used as the initial value for `Prop2`.</span></span>  
  
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
  
 <span data-ttu-id="5f8d9-105">**Identyfikator błędu:** BC36548</span><span class="sxs-lookup"><span data-stu-id="5f8d9-105">**Error ID:** BC36548</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5f8d9-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="5f8d9-106">To correct this error</span></span>  
  
-   <span data-ttu-id="5f8d9-107">Przypisz wartość początkową `Prop1` do zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="5f8d9-107">Assign the initial value for `Prop1` to a local variable.</span></span> <span data-ttu-id="5f8d9-108">Przypisanie zmiennej zarówno `Prop1` i `Prop2`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5f8d9-108">Assign that variable to both `Prop1` and `Prop2`, as shown in the following code.</span></span>  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5f8d9-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f8d9-109">See Also</span></span>  
 [<span data-ttu-id="5f8d9-110">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="5f8d9-110">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="5f8d9-111">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="5f8d9-111">Expression Trees</span></span>](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [<span data-ttu-id="5f8d9-112">Porady: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych</span><span class="sxs-lookup"><span data-stu-id="5f8d9-112">How to: Use Expression Trees to Build Dynamic Queries</span></span>](http://msdn.microsoft.com/library/1e37e0cc-eef3-48bb-8b69-3adabf322735)
