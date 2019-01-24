---
title: Argument nie może mieć wartości Nothing
ms.date: 07/20/2015
f1_keywords:
- vbrGeneral_ArgumentNullException
ms.assetid: 2abd995b-36a5-45f0-b3c1-6e0c3b31a875
ms.openlocfilehash: 157329c74e9c300f8d4d60d96980f9cb77d0e550
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656131"
---
# <a name="argument-cannot-be-nothing"></a><span data-ttu-id="050c6-102">Argument nie może mieć wartości Nothing</span><span class="sxs-lookup"><span data-stu-id="050c6-102">Argument cannot be Nothing</span></span>
<span data-ttu-id="050c6-103">Wartość null została podana, musi mieć wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="050c6-103">A null value has been supplied for an argument that must have a value.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="050c6-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="050c6-104">To correct this error</span></span>  
  
-   <span data-ttu-id="050c6-105">Może mieć próbowano użyć obiektu bez podawania wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="050c6-105">You might have tried to use an object without providing an instance of the object.</span></span> <span data-ttu-id="050c6-106">W takim przypadku należy użyć `New` — słowo kluczowe, aby utworzyć wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="050c6-106">In such a case, use the `New` keyword to create the instance.</span></span>  
  
-   <span data-ttu-id="050c6-107">Sprawdź, czy wartość jest obliczany poprawnie.</span><span class="sxs-lookup"><span data-stu-id="050c6-107">Check that the value is calculated correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="050c6-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="050c6-108">See also</span></span>
- <xref:System.NullReferenceException>
