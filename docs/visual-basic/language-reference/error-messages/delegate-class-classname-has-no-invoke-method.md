---
title: "Klasa delegata &#39; &lt;classname&gt;&#39; nie ma metody Invoke, dlatego wyrażenie tego typu nie może być elementem docelowym wywołania metody"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55d0e2442807e25737d90ac4b45a59b9d3e73037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="777f0-102">Klasa delegata &#39; &lt;classname&gt;&#39; nie ma metody Invoke, dlatego wyrażenie tego typu nie może być elementem docelowym wywołania metody</span><span class="sxs-lookup"><span data-stu-id="777f0-102">Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="777f0-103">Wywołanie `Invoke` za pośrednictwem pełnomocnika nie powiodła się ponieważ `Invoke` nie jest zaimplementowana w klasie obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="777f0-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="777f0-104">**Identyfikator błędu:** BC30220</span><span class="sxs-lookup"><span data-stu-id="777f0-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="777f0-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="777f0-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="777f0-106">Upewnij się, że utworzono wystąpienie klasy delegata z `Dim` instrukcji i czy przypisano procedury na wystąpienie obiektu delegowanego z `AddressOf` operatora.</span><span class="sxs-lookup"><span data-stu-id="777f0-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2.  <span data-ttu-id="777f0-107">Znajdź kod, który implementuje klasie obiektów delegowanych i upewnij się, że implementuje `Invoke` procedury.</span><span class="sxs-lookup"><span data-stu-id="777f0-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="777f0-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="777f0-108">See Also</span></span>  
 [<span data-ttu-id="777f0-109">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="777f0-109">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="777f0-110">Delegate — instrukcja</span><span class="sxs-lookup"><span data-stu-id="777f0-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="777f0-111">AddressOf — Operator</span><span class="sxs-lookup"><span data-stu-id="777f0-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="777f0-112">Dim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="777f0-112">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
