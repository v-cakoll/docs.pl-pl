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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3c9486427660de792091297d2426c970cfe47bc1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="fa7e0-102">Śledzenie analityczne za pomocą funkcji ETW</span><span class="sxs-lookup"><span data-stu-id="fa7e0-102">Analytic Tracing with ETW</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="fa7e0-103">Śledzenie analityczne daje możliwość przechwytywania informacji diagnostycznych podczas wykonywania [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="fa7e0-103"> analytic tracing offers a way to capture diagnostic information during the execution of a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="fa7e0-104">zdarzenia śledzenia analitycznego są emitowane w punktach klucza [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stos, aby umożliwić rozwiązywania problemów z [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="fa7e0-104"> analytic tracing events are emitted at key points in the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] stack to allow troubleshooting of [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services in a production environment.</span></span> <span data-ttu-id="fa7e0-105">Śledzenie analityczne dla [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług ma minimalny wpływ na wydajność serwera produktu obsługującego [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług te zdarzenia są bardzo wydajnie wysyłanego do sesji zdarzeń śledzenia zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="fa7e0-105">Analytic tracing for [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa7e0-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fa7e0-106">In This Section</span></span>  
 [<span data-ttu-id="fa7e0-107">Omówienie śledzenia analitycznego</span><span class="sxs-lookup"><span data-stu-id="fa7e0-107">Analytic Tracing Overview</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 <span data-ttu-id="fa7e0-108">W tym artykule omówiono sposób [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] śledzenie analityczne działa w [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fa7e0-108">Discusses how [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="fa7e0-109">Dynamiczne Włączanie śledzenia danych analitycznych</span><span class="sxs-lookup"><span data-stu-id="fa7e0-109">Dynamically Enabling Analytic Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="fa7e0-110">W tym artykule omówiono sposób włączyć lub wyłączyć śledzenie dynamicznie za pomocą funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="fa7e0-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="fa7e0-111">Konfigurowanie śledzenia przepływu komunikatów</span><span class="sxs-lookup"><span data-stu-id="fa7e0-111">Configuring Message Flow Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 <span data-ttu-id="fa7e0-112">Zawiera opis sposobu konfigurowania śledzenia przepływu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fa7e0-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="fa7e0-113">Odwołanie do zdarzenia śledzenia analitycznego</span><span class="sxs-lookup"><span data-stu-id="fa7e0-113">Analytic Trace Event Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 <span data-ttu-id="fa7e0-114">Przedstawia tabelę zdarzeń identyfikatorów ich poziomów zdarzeń, komunikaty o zdarzeniach i słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="fa7e0-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa7e0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa7e0-115">See Also</span></span>  
 [<span data-ttu-id="fa7e0-116">Usługi WCF i śledzenie zdarzeń systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fa7e0-116">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [<span data-ttu-id="fa7e0-117">Śledzenie zdarzeń do zdarzenia śledzenia w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="fa7e0-117">Tracking Events into Event Tracing in Windows</span></span>](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
