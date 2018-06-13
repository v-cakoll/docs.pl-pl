---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: a6b4e369d2d22d2441b3896321b7c152e21d967b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33483334"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="5c244-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="5c244-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="5c244-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="5c244-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="5c244-104">Opis</span><span class="sxs-lookup"><span data-stu-id="5c244-104">Description</span></span>  
 <span data-ttu-id="5c244-105">System osiągnął limit ustawiony dla przepustnicy ManualFlowControlLimit.</span><span class="sxs-lookup"><span data-stu-id="5c244-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="5c244-106">Wartość przepustnicy można zmienić, modyfikując właściwość ManualFlowControlLimit ServiceHost lub InstanceContext, zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="5c244-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="5c244-107">Ślad jest emitowany, gdy limit kontroli przepływu ręczne początkowo zmniejsza się do 0.</span><span class="sxs-lookup"><span data-stu-id="5c244-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="5c244-108">Kolejne zmiany 0 nie są śledzone.</span><span class="sxs-lookup"><span data-stu-id="5c244-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="5c244-109">Przepływ sterowania limit w kontekście wystąpienia śledzonego raz dla każdego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="5c244-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c244-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c244-110">See Also</span></span>  
 [<span data-ttu-id="5c244-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="5c244-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="5c244-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="5c244-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="5c244-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="5c244-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
