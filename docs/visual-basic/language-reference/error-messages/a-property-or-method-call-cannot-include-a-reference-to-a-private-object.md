---
title: Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 1f36526eab1bc0964bf89398b6e0f3e74d09fdc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583828"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="728bc-102">Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="728bc-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="728bc-103">Wśród możliwych przyczyn tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="728bc-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="728bc-104">Klient wywoływane właściwości lub metody składnika poza procesem i próbował przekazać odwołanie do obiektu prywatnego jako jeden z argumentów.</span><span class="sxs-lookup"><span data-stu-id="728bc-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
-   <span data-ttu-id="728bc-105">Składnik poza procesem wywołać metodę wywołania zwrotnego dla klienta i próbował przekazać odwołanie do obiektu prywatnego.</span><span class="sxs-lookup"><span data-stu-id="728bc-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
-   <span data-ttu-id="728bc-106">Składnik poza procesem Próbowano przekazać odwołanie do obiektu prywatnego jako argument zdarzenia, który został wywoływanie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="728bc-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
-   <span data-ttu-id="728bc-107">Klient próbował przypisać odwołania do obiektu prywatnego `ByRef` argument był on obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="728bc-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="728bc-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="728bc-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="728bc-109">Usuń odwołanie.</span><span class="sxs-lookup"><span data-stu-id="728bc-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="728bc-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="728bc-110">See Also</span></span>  
 [<span data-ttu-id="728bc-111">Private</span><span class="sxs-lookup"><span data-stu-id="728bc-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
