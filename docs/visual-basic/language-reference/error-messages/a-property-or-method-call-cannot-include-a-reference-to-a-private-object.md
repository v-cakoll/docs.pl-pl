---
title: Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 5f0740af49bb369be87a1a33973b67f59acf3ab6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700835"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="66a1d-102">Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="66a1d-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="66a1d-103">Wśród możliwe przyczyny tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="66a1d-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="66a1d-104">Klient wywoływane właściwości lub metody składnika spoza procesu i Próbowano przekazać odwołanie do obiektu prywatnego jako jeden z argumentów.</span><span class="sxs-lookup"><span data-stu-id="66a1d-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
-   <span data-ttu-id="66a1d-105">Składnik spoza procesu wywołano metodę wywołania zwrotnego na jego klienta i Próbowano przekazać odwołanie do obiektu prywatnego.</span><span class="sxs-lookup"><span data-stu-id="66a1d-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
-   <span data-ttu-id="66a1d-106">Składnik spoza procesu próbował przekazać odwołanie do obiektu prywatnego jako argument zdarzenia, który został on wywoływanie.</span><span class="sxs-lookup"><span data-stu-id="66a1d-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
-   <span data-ttu-id="66a1d-107">Klient próbował przypisać odwołanie do obiektu prywatnego `ByRef` argument był on obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="66a1d-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="66a1d-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="66a1d-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="66a1d-109">Usuń odwołanie.</span><span class="sxs-lookup"><span data-stu-id="66a1d-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a1d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66a1d-110">See also</span></span>
- [<span data-ttu-id="66a1d-111">Private</span><span class="sxs-lookup"><span data-stu-id="66a1d-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
