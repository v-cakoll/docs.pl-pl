---
title: Klasa obiektu delegowanego &#39; &lt;classname&gt; &#39; nie ma metody Invoke, dlatego wyrażenie tego typu nie może być elementem docelowym wywołania metody
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: cc1abba46224772e733780800dd104dfc7ebe9ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588833"
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="1ddd9-102">Klasa obiektu delegowanego &#39; &lt;classname&gt; &#39; nie ma metody Invoke, dlatego wyrażenie tego typu nie może być elementem docelowym wywołania metody</span><span class="sxs-lookup"><span data-stu-id="1ddd9-102">Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="1ddd9-103">Wywołanie `Invoke` za pośrednictwem pełnomocnika nie powiodła się ponieważ `Invoke` nie jest zaimplementowana w klasie obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="1ddd9-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="1ddd9-104">**Identyfikator błędu:** BC30220</span><span class="sxs-lookup"><span data-stu-id="1ddd9-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1ddd9-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="1ddd9-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="1ddd9-106">Upewnij się, że utworzono wystąpienie klasy delegata z `Dim` instrukcji i czy przypisano procedury na wystąpienie obiektu delegowanego z `AddressOf` operatora.</span><span class="sxs-lookup"><span data-stu-id="1ddd9-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2.  <span data-ttu-id="1ddd9-107">Znajdź kod, który implementuje klasie obiektów delegowanych i upewnij się, że implementuje `Invoke` procedury.</span><span class="sxs-lookup"><span data-stu-id="1ddd9-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ddd9-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ddd9-108">See Also</span></span>  
 [<span data-ttu-id="1ddd9-109">Delegaci</span><span class="sxs-lookup"><span data-stu-id="1ddd9-109">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="1ddd9-110">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ddd9-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="1ddd9-111">AddressOf, operator</span><span class="sxs-lookup"><span data-stu-id="1ddd9-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="1ddd9-112">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1ddd9-112">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
