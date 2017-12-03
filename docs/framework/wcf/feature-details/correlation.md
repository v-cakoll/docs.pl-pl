---
title: Korelacja
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60151f6c-19b7-47af-9cdc-76c2ac95f301
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fc1608cc4e746af56e7d89237f0c1f5e6cc3bc7e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="correlation"></a><span data-ttu-id="2bca9-102">Korelacja</span><span class="sxs-lookup"><span data-stu-id="2bca9-102">Correlation</span></span>
<span data-ttu-id="2bca9-103">Aplikacje usług przepływu pracy komunikować się z innymi usługami, jest ważne, czy wiadomości między nimi są wysyłane do wystąpienia przepływu pracy odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="2bca9-103">When workflow service applications communicate with other services, it is important that messages between them are dispatched to the appropriate workflow instance.</span></span> <span data-ttu-id="2bca9-104">Korelacji udostępnia mechanizm dla tego.</span><span class="sxs-lookup"><span data-stu-id="2bca9-104">Correlation provides the mechanism for this.</span></span> <span data-ttu-id="2bca9-105">Tematy w tej sekcji zawierają omówienie korelacji i jak z niego korzystać w scenariuszach usługi innego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2bca9-105">The topics in this section provide an overview of correlation and how to use it in different workflow service scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2bca9-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2bca9-106">In This Section</span></span>  
 [<span data-ttu-id="2bca9-107">Przegląd korelacji</span><span class="sxs-lookup"><span data-stu-id="2bca9-107">Correlation Overview</span></span>](../../../../docs/framework/wcf/feature-details/correlation-overview.md)  
 <span data-ttu-id="2bca9-108">Zawiera omówienie typów korelacji dostępne w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2bca9-108">Provides an overview of the types of correlation available in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="2bca9-109">Wymiana kontekstu</span><span class="sxs-lookup"><span data-stu-id="2bca9-109">Context Exchange</span></span>](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)  
 <span data-ttu-id="2bca9-110">W tym artykule opisano korelacja wymiany kontekstu.</span><span class="sxs-lookup"><span data-stu-id="2bca9-110">Describes context exchange correlation.</span></span>  
  
 [<span data-ttu-id="2bca9-111">Niezawodna komunikacja dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="2bca9-111">Durable Duplex</span></span>](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md)  
 <span data-ttu-id="2bca9-112">W tym artykule opisano niezawodna korelacja dwukierunkowa.</span><span class="sxs-lookup"><span data-stu-id="2bca9-112">Describes durable duplex correlation.</span></span>  
  
 [<span data-ttu-id="2bca9-113">Na podstawie zawartości</span><span class="sxs-lookup"><span data-stu-id="2bca9-113">Content Based</span></span>](../../../../docs/framework/wcf/feature-details/content-based-correlation.md)  
 <span data-ttu-id="2bca9-114">W tym artykule opisano na podstawie zawartości korelacji.</span><span class="sxs-lookup"><span data-stu-id="2bca9-114">Describes content-based correlation.</span></span>  
  
 [<span data-ttu-id="2bca9-115">"Żądanie-odpowiedź"</span><span class="sxs-lookup"><span data-stu-id="2bca9-115">Request-Reply</span></span>](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)  
 <span data-ttu-id="2bca9-116">W tym artykule opisano korelacja żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2bca9-116">Describes request-reply correlation.</span></span>  
  
 [<span data-ttu-id="2bca9-117">Korelacja rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="2bca9-117">Troubleshooting Correlation</span></span>](../../../../docs/framework/wcf/feature-details/troubleshooting-correlation.md)  
 <span data-ttu-id="2bca9-118">Udostępnia metody dla korelacja rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="2bca9-118">Provides methods for troubleshooting correlation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bca9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bca9-119">See Also</span></span>  
 <xref:System.ServiceModel.Activities.CorrelationHandle>  
 <xref:System.ServiceModel.Activities.Send>  
 <xref:System.ServiceModel.Activities.Receive>  
 <xref:System.ServiceModel.CorrelationQuery>  
 [<span data-ttu-id="2bca9-120">Korelacja na podstawie zawartości</span><span class="sxs-lookup"><span data-stu-id="2bca9-120">Content-Based Correlation</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md)  
 [<span data-ttu-id="2bca9-121">Kalkulator skorelowane</span><span class="sxs-lookup"><span data-stu-id="2bca9-121">Correlated Calculator</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)
