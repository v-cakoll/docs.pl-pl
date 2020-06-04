---
title: Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 36c71cdb345d0fdc0da2b58865a1f11956bcb944
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409975"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="d9696-102">Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="d9696-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>

<span data-ttu-id="d9696-103">Wśród możliwych przyczyn tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="d9696-103">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="d9696-104">Klient wywołał właściwość lub metodę składnika out-of-process i próbował przekazać odwołanie do obiektu prywatnego jako jednego z argumentów.</span><span class="sxs-lookup"><span data-stu-id="d9696-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
- <span data-ttu-id="d9696-105">Składnik poza procesem wywołał metodę wywołania zwrotnego na kliencie i próbował przekazać odwołanie do obiektu prywatnego.</span><span class="sxs-lookup"><span data-stu-id="d9696-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
- <span data-ttu-id="d9696-106">Składnik, który podjął próbę przekazania odwołania do prywatnego obiektu jako argument zdarzenia, które było podwyższane.</span><span class="sxs-lookup"><span data-stu-id="d9696-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
- <span data-ttu-id="d9696-107">Klient próbował przypisać odwołanie do obiektu prywatnego do `ByRef` argumentu zdarzenia, które obsłużył.</span><span class="sxs-lookup"><span data-stu-id="d9696-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d9696-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d9696-108">To correct this error</span></span>  
  
1. <span data-ttu-id="d9696-109">Usuń odwołanie.</span><span class="sxs-lookup"><span data-stu-id="d9696-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9696-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9696-110">See also</span></span>

- [<span data-ttu-id="d9696-111">Użytek</span><span class="sxs-lookup"><span data-stu-id="d9696-111">Private</span></span>](../modifiers/private.md)
