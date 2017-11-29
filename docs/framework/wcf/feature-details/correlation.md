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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d15609db250e4743ae2a7a1b6c3c355600704f02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="correlation"></a><span data-ttu-id="1ea6a-102">Korelacja</span><span class="sxs-lookup"><span data-stu-id="1ea6a-102">Correlation</span></span>
<span data-ttu-id="1ea6a-103">Aplikacje usług przepływu pracy komunikować się z innymi usługami, jest ważne, czy wiadomości między nimi są wysyłane do wystąpienia przepływu pracy odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="1ea6a-103">When workflow service applications communicate with other services, it is important that messages between them are dispatched to the appropriate workflow instance.</span></span> <span data-ttu-id="1ea6a-104">Korelacji udostępnia mechanizm dla tego.</span><span class="sxs-lookup"><span data-stu-id="1ea6a-104">Correlation provides the mechanism for this.</span></span> <span data-ttu-id="1ea6a-105">Tematy w tej sekcji zawierają omówienie korelacji i jak z niego korzystać w scenariuszach usługi innego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1ea6a-105">The topics in this section provide an overview of correlation and how to use it in different workflow service scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ea6a-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1ea6a-106">In This Section</span></span>  
 [<span data-ttu-id="1ea6a-107">Przegląd korelacji</span><span class="sxs-lookup"><span data-stu-id="1ea6a-107">Correlation Overview</span></span>](../../../../docs/framework/wcf/feature-details/correlation-overview.md)  
 <span data-ttu-id="1ea6a-108">Zawiera omówienie typów korelacji dostępne w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ea6a-108">Provides an overview of the types of correlation available in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="1ea6a-109">Wymiana kontekstu</span><span class="sxs-lookup"><span data-stu-id="1ea6a-109">Context Exchange</span></span>](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)  
 <span data-ttu-id="1ea6a-110">W tym artykule opisano korelacja wymiany kontekstu.</span><span class="sxs-lookup"><span data-stu-id="1ea6a-110">Describes context exchange correlation.</span></span>  
  
 [<span data-ttu-id="1ea6a-111">Niezawodna komunikacja dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="1ea6a-111">Durable Duplex</span></span>](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md)  
 <span data-ttu-id="1ea6a-112">W tym artykule opisano niezawodna korelacja dwukierunkowa.</span><span class="sxs-lookup"><span data-stu-id="1ea6a-112">Describes durable duplex correlation.</span></span>  
  
 [<span data-ttu-id="1ea6a-113">Na podstawie zawartości</span><span class="sxs-lookup"><span data-stu-id="1ea6a-113">Content Based</span></span>](../../../../docs/framework/wcf/feature-details/content-based-correlation.md)  
 <span data-ttu-id="1ea6a-114">W tym artykule opisano na podstawie zawartości korelacji.</span><span class="sxs-lookup"><span data-stu-id="1ea6a-114">Describes content-based correlation.</span></span>  
  
 [<span data-ttu-id="1ea6a-115">"Żądanie-odpowiedź"</span><span class="sxs-lookup"><span data-stu-id="1ea6a-115">Request-Reply</span></span>](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)  
 <span data-ttu-id="1ea6a-116">W tym artykule opisano korelacja żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1ea6a-116">Describes request-reply correlation.</span></span>  
  
 [<span data-ttu-id="1ea6a-117">Korelacja rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="1ea6a-117">Troubleshooting Correlation</span></span>](../../../../docs/framework/wcf/feature-details/troubleshooting-correlation.md)  
 <span data-ttu-id="1ea6a-118">Udostępnia metody dla korelacja rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="1ea6a-118">Provides methods for troubleshooting correlation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea6a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ea6a-119">See Also</span></span>  
 <xref:System.ServiceModel.Activities.CorrelationHandle>  
 <xref:System.ServiceModel.Activities.Send>  
 <xref:System.ServiceModel.Activities.Receive>  
 <xref:System.ServiceModel.CorrelationQuery>  
 [<span data-ttu-id="1ea6a-120">Korelacja na podstawie zawartości</span><span class="sxs-lookup"><span data-stu-id="1ea6a-120">Content-Based Correlation</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/content-based-correlation.md)  
 [<span data-ttu-id="1ea6a-121">Kalkulator skorelowane</span><span class="sxs-lookup"><span data-stu-id="1ea6a-121">Correlated Calculator</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/correlated-calculator.md)
