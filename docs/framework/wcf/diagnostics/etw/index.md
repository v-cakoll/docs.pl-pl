---
title: "Śledzenie analityczne za pomocą funkcji ETW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a16f66ed8443749764e66d2616ae566ad788d571
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="b39fe-102">Śledzenie analityczne za pomocą funkcji ETW</span><span class="sxs-lookup"><span data-stu-id="b39fe-102">Analytic Tracing with ETW</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="b39fe-103">Śledzenie analityczne daje możliwość przechwytywania informacji diagnostycznych podczas wykonywania [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="b39fe-103"> analytic tracing offers a way to capture diagnostic information during the execution of a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="b39fe-104">zdarzenia śledzenia analitycznego są emitowane w punktach klucza [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stos, aby umożliwić rozwiązywania problemów z [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="b39fe-104"> analytic tracing events are emitted at key points in the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stack to allow troubleshooting of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services in a production environment.</span></span> <span data-ttu-id="b39fe-105">Śledzenie analityczne dla [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług ma minimalny wpływ na wydajność serwera produktu obsługującego [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług te zdarzenia są bardzo wydajnie wysyłanego do sesji zdarzeń śledzenia zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="b39fe-105">Analytic tracing for [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b39fe-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b39fe-106">In This Section</span></span>  
 [<span data-ttu-id="b39fe-107">Omówienie śledzenia analitycznego</span><span class="sxs-lookup"><span data-stu-id="b39fe-107">Analytic Tracing Overview</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 <span data-ttu-id="b39fe-108">W tym artykule omówiono sposób [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] śledzenie analityczne działa w [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b39fe-108">Discusses how [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="b39fe-109">Dynamiczne włączanie śledzenia danych analitycznych</span><span class="sxs-lookup"><span data-stu-id="b39fe-109">Dynamically Enabling Analytic Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="b39fe-110">W tym artykule omówiono sposób włączyć lub wyłączyć śledzenie dynamicznie za pomocą funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="b39fe-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="b39fe-111">Konfigurowanie śledzenia przepływu komunikatów</span><span class="sxs-lookup"><span data-stu-id="b39fe-111">Configuring Message Flow Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 <span data-ttu-id="b39fe-112">Zawiera opis sposobu konfigurowania śledzenia przepływu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="b39fe-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="b39fe-113">Odwołanie do zdarzenia śledzenia analitycznego</span><span class="sxs-lookup"><span data-stu-id="b39fe-113">Analytic Trace Event Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 <span data-ttu-id="b39fe-114">Przedstawia tabelę zdarzeń identyfikatorów ich poziomów zdarzeń, komunikaty o zdarzeniach i słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="b39fe-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b39fe-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b39fe-115">See Also</span></span>  
 [<span data-ttu-id="b39fe-116">Usługi i śledzenie zdarzeń programu WCF dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b39fe-116">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [<span data-ttu-id="b39fe-117">Zdarzenia śledzenia do śledzenia zdarzeń w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="b39fe-117">Tracking Events into Event Tracing in Windows</span></span>](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
