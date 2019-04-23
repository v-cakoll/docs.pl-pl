---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: fb69c3c737a0e77b05e08ab8d8282069feb069bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095688"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="1d033-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="1d033-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="1d033-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="1d033-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="1d033-104">Opis</span><span class="sxs-lookup"><span data-stu-id="1d033-104">Description</span></span>  
 <span data-ttu-id="1d033-105">System osiągnął limit ustawiony dla ograniczania ManualFlowControlLimit.</span><span class="sxs-lookup"><span data-stu-id="1d033-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="1d033-106">Wartość ograniczenia przepustowości można zmienić, modyfikując właściwość ManualFlowControlLimit ServiceHost lub obiekt InstanceContext, jeśli ma to zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="1d033-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="1d033-107">Ślad jest emitowane, gdy limit kontroli przepływu ręczne początkowo jest ograniczona do 0.</span><span class="sxs-lookup"><span data-stu-id="1d033-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="1d033-108">Kolejne zmiany na wartość 0 nie są śledzone.</span><span class="sxs-lookup"><span data-stu-id="1d033-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="1d033-109">Przepływ sterowania limit w kontekście wystąpienia śledzona jest jeden raz dla każdego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="1d033-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d033-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d033-110">See also</span></span>

- [<span data-ttu-id="1d033-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="1d033-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="1d033-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="1d033-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="1d033-113">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="1d033-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
