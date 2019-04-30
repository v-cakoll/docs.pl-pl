---
title: Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 04124ca044ad8dbff58f85230d7e10ea336d41e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751699"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="64fec-102">Właściwość lub wywołanie metody nie może zawierać odwołania do obiektu prywatnego jako do argumentu lub jako do wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="64fec-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="64fec-103">Wśród możliwe przyczyny tego błędu są:</span><span class="sxs-lookup"><span data-stu-id="64fec-103">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="64fec-104">Klient wywoływane właściwości lub metody składnika spoza procesu i Próbowano przekazać odwołanie do obiektu prywatnego jako jeden z argumentów.</span><span class="sxs-lookup"><span data-stu-id="64fec-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
- <span data-ttu-id="64fec-105">Składnik spoza procesu wywołano metodę wywołania zwrotnego na jego klienta i Próbowano przekazać odwołanie do obiektu prywatnego.</span><span class="sxs-lookup"><span data-stu-id="64fec-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
- <span data-ttu-id="64fec-106">Składnik spoza procesu próbował przekazać odwołanie do obiektu prywatnego jako argument zdarzenia, który został on wywoływanie.</span><span class="sxs-lookup"><span data-stu-id="64fec-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
- <span data-ttu-id="64fec-107">Klient próbował przypisać odwołanie do obiektu prywatnego `ByRef` argument był on obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="64fec-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="64fec-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="64fec-108">To correct this error</span></span>  
  
1. <span data-ttu-id="64fec-109">Usuń odwołanie.</span><span class="sxs-lookup"><span data-stu-id="64fec-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64fec-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64fec-110">See also</span></span>

- [<span data-ttu-id="64fec-111">Private</span><span class="sxs-lookup"><span data-stu-id="64fec-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
