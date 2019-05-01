---
title: Klasa obiektu delegowanego „<classname>” nie ma metody Invoke, dlatego wyrażenie tego typu nie może być elementem docelowym wywołania metody
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 3fe164d868ee7bde0e687e1d592f4d5a17565aea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803639"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="faa05-102">Klasa obiektu delegowanego\<nazwa_klasy >' nie ma metody Invoke, dlatego wyrażenie tego typu nie może być elementem docelowym wywołania metody</span><span class="sxs-lookup"><span data-stu-id="faa05-102">Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="faa05-103">Wywołanie `Invoke` za pośrednictwem delegata nie powiodła się ponieważ `Invoke` nie jest zaimplementowana w klasie delegata.</span><span class="sxs-lookup"><span data-stu-id="faa05-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="faa05-104">**Identyfikator błędu:** BC30220</span><span class="sxs-lookup"><span data-stu-id="faa05-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="faa05-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="faa05-105">To correct this error</span></span>  
  
1. <span data-ttu-id="faa05-106">Upewnij się, że utworzono wystąpienie klasy delegata z `Dim` poufności i że procedury została przypisana do wystąpienia delegata z `AddressOf` operatora.</span><span class="sxs-lookup"><span data-stu-id="faa05-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2. <span data-ttu-id="faa05-107">Znajdź kod, który implementuje klasa obiektu delegowanego i upewnij się, ponieważ implementuje on `Invoke` procedury.</span><span class="sxs-lookup"><span data-stu-id="faa05-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa05-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="faa05-108">See also</span></span>

- [<span data-ttu-id="faa05-109">Delegaty</span><span class="sxs-lookup"><span data-stu-id="faa05-109">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="faa05-110">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="faa05-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="faa05-111">AddressOf, operator</span><span class="sxs-lookup"><span data-stu-id="faa05-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="faa05-112">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="faa05-112">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
