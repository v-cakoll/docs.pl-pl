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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 49b41e27847005c7187435229e030994df10df26
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="5a878-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="5a878-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="5a878-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="5a878-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="5a878-104">Opis</span><span class="sxs-lookup"><span data-stu-id="5a878-104">Description</span></span>  
 <span data-ttu-id="5a878-105">System osiągnął limit ustawiony dla przepustnicy ManualFlowControlLimit.</span><span class="sxs-lookup"><span data-stu-id="5a878-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="5a878-106">Wartość przepustnicy można zmienić, modyfikując właściwość ManualFlowControlLimit ServiceHost lub InstanceContext, zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="5a878-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="5a878-107">Ślad jest emitowany, gdy limit kontroli przepływu ręczne początkowo zmniejsza się do 0.</span><span class="sxs-lookup"><span data-stu-id="5a878-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="5a878-108">Kolejne zmiany 0 nie są śledzone.</span><span class="sxs-lookup"><span data-stu-id="5a878-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="5a878-109">Przepływ sterowania limit w kontekście wystąpienia śledzonego raz dla każdego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="5a878-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a878-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a878-110">See Also</span></span>  
 [<span data-ttu-id="5a878-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="5a878-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="5a878-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="5a878-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="5a878-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="5a878-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
