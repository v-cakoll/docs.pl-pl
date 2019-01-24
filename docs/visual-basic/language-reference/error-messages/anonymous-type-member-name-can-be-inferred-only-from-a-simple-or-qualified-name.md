---
title: Nazwę członka typu anonimowego można wywnioskować tylko na podstawie prostej lub kwalifikowanej nazwy bez argumentów
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: 4d91b7a3c57db38fde3cf371773e8d64834a8f72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715273"
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="dc7e9-102">Nazwę członka typu anonimowego można wywnioskować tylko na podstawie prostej lub kwalifikowanej nazwy bez argumentów</span><span class="sxs-lookup"><span data-stu-id="dc7e9-102">Anonymous type member name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="dc7e9-103">Nie można wywnioskować nazwę członka typu anonimowego z wyrażenie złożone.</span><span class="sxs-lookup"><span data-stu-id="dc7e9-103">You cannot infer an anonymous type member name from a complex expression.</span></span>  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 <span data-ttu-id="dc7e9-104">Aby uzyskać więcej informacji na temat źródeł, z których można typy anonimowe i nie można wywnioskować nazwy elementów członkowskich i typy, zobacz [jak: Wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span><span class="sxs-lookup"><span data-stu-id="dc7e9-104">For more information about sources from which anonymous types can and cannot infer member names and types, see [How to: Infer Property Names and Types in Anonymous Type Declarations](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).</span></span>  
  
 <span data-ttu-id="dc7e9-105">**Identyfikator błędu:** BC36556</span><span class="sxs-lookup"><span data-stu-id="dc7e9-105">**Error ID:** BC36556</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dc7e9-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="dc7e9-106">To correct this error</span></span>  
  
-   <span data-ttu-id="dc7e9-107">Przypisz wyrażenia na nazwę elementu członkowskiego, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="dc7e9-107">Assign the expression to a member name, as shown in the following code:</span></span>  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dc7e9-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc7e9-108">See also</span></span>
- [<span data-ttu-id="dc7e9-109">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="dc7e9-109">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="dc7e9-110">Instrukcje: Wnioskowanie nazw właściwości i typów w deklaracjach typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="dc7e9-110">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
