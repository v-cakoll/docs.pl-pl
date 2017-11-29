---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 556afe035697ee35d7ba86185b5b768a645c32c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="117f2-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="117f2-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="117f2-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="117f2-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="117f2-104">Opis</span><span class="sxs-lookup"><span data-stu-id="117f2-104">Description</span></span>  
 <span data-ttu-id="117f2-105">System osiągnął limit ustawiony dla przepustnicy ManualFlowControlLimit.</span><span class="sxs-lookup"><span data-stu-id="117f2-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="117f2-106">Wartość przepustnicy można zmienić, modyfikując właściwość ManualFlowControlLimit ServiceHost lub InstanceContext, zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="117f2-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="117f2-107">Ślad jest emitowany, gdy limit kontroli przepływu ręczne początkowo zmniejsza się do 0.</span><span class="sxs-lookup"><span data-stu-id="117f2-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="117f2-108">Kolejne zmiany 0 nie są śledzone.</span><span class="sxs-lookup"><span data-stu-id="117f2-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="117f2-109">Przepływ sterowania limit w kontekście wystąpienia śledzonego raz dla każdego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="117f2-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="117f2-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="117f2-110">See Also</span></span>  
 [<span data-ttu-id="117f2-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="117f2-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="117f2-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="117f2-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="117f2-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="117f2-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
