---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: bffa6361df5a50748f45aa3004f7a307ad516d7b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84580492"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="401ee-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="401ee-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>
<span data-ttu-id="401ee-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="401ee-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="401ee-104">Opis</span><span class="sxs-lookup"><span data-stu-id="401ee-104">Description</span></span>  
 <span data-ttu-id="401ee-105">System osiągnął limit ustawiony dla ograniczenia ManualFlowControlLimit.</span><span class="sxs-lookup"><span data-stu-id="401ee-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="401ee-106">Wartość dławienia można zmienić, modyfikując właściwość ManualFlowControlLimit na serwerze ServiceHost lub InstanceContext, zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="401ee-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="401ee-107">Ślad jest emitowany, gdy limit ręcznego sterowania przepływem został początkowo zmniejszony do wartości 0.</span><span class="sxs-lookup"><span data-stu-id="401ee-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="401ee-108">Kolejne zmiany w wartości 0 nie są śledzone.</span><span class="sxs-lookup"><span data-stu-id="401ee-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="401ee-109">Limit sterowania przepływem dla kontekstu wystąpienia jest śledzony jednokrotnie dla każdego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="401ee-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="401ee-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="401ee-110">See also</span></span>

- [<span data-ttu-id="401ee-111">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="401ee-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="401ee-112">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="401ee-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="401ee-113">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="401ee-113">Administration and Diagnostics</span></span>](../index.md)
