---
title: Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 53f9052555555a5b9dcb038dfee9cd54dc2b4251
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976197"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="dcd52-102">Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="dcd52-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>

<span data-ttu-id="dcd52-103">Wśród możliwych przyczyn tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="dcd52-103">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="dcd52-104">Klient wywołał właściwość lub metodę składnika out-of-process i próbował przekazać odwołanie do obiektu prywatnego jako jednego z argumentów.</span><span class="sxs-lookup"><span data-stu-id="dcd52-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
- <span data-ttu-id="dcd52-105">Składnik poza procesem wywołał metodę wywołania zwrotnego na kliencie i próbował przekazać odwołanie do obiektu prywatnego.</span><span class="sxs-lookup"><span data-stu-id="dcd52-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
- <span data-ttu-id="dcd52-106">Składnik, który podjął próbę przekazania odwołania do prywatnego obiektu jako argument zdarzenia, które było podwyższane.</span><span class="sxs-lookup"><span data-stu-id="dcd52-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
- <span data-ttu-id="dcd52-107">Klient próbował przypisać odwołanie do obiektu prywatnego do argumentu `ByRef` zdarzenia, które obsłużył.</span><span class="sxs-lookup"><span data-stu-id="dcd52-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dcd52-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="dcd52-108">To correct this error</span></span>  
  
1. <span data-ttu-id="dcd52-109">Usuń odwołanie.</span><span class="sxs-lookup"><span data-stu-id="dcd52-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcd52-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcd52-110">See also</span></span>

- [<span data-ttu-id="dcd52-111">Private</span><span class="sxs-lookup"><span data-stu-id="dcd52-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
