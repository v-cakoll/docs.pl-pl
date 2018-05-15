---
title: Śledzenie analityczne za pomocą funkcji ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: 210418b8a8765a1fc59658e9df57c92ce087c95f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="9d3a1-102">Śledzenie analityczne za pomocą funkcji ETW</span><span class="sxs-lookup"><span data-stu-id="9d3a1-102">Analytic Tracing with ETW</span></span>
<span data-ttu-id="9d3a1-103">Śledzenie analityczne Windows Communication Foundation (WCF) daje możliwość przechwytywania informacji diagnostycznych podczas wykonywania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="9d3a1-103">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="9d3a1-104">Zdarzenia śledzenia analitycznego WCF są emitowane po klucz wskazuje na stosie WCF umożliwia rozwiązywanie problemów z usług WCF w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="9d3a1-104">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="9d3a1-105">Śledzenie analityczne dla usług WCF ma minimalny wpływ na wydajność serwera produktu obsługującego [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] usług WCF, jak te zdarzenia są bardzo wydajnie wysyłanego do sesji zdarzeń śledzenia zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="9d3a1-105">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d3a1-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9d3a1-106">In This Section</span></span>  
 [<span data-ttu-id="9d3a1-107">Omówienie śledzenia analitycznego</span><span class="sxs-lookup"><span data-stu-id="9d3a1-107">Analytic Tracing Overview</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 <span data-ttu-id="9d3a1-108">W tym artykule omówiono, jak działa śledzenie analityczne WCF w [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9d3a1-108">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="9d3a1-109">Dynamiczne włączanie śledzenia danych analitycznych</span><span class="sxs-lookup"><span data-stu-id="9d3a1-109">Dynamically Enabling Analytic Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="9d3a1-110">W tym artykule omówiono sposób włączyć lub wyłączyć śledzenie dynamicznie za pomocą funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="9d3a1-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="9d3a1-111">Konfigurowanie śledzenia przepływu komunikatów</span><span class="sxs-lookup"><span data-stu-id="9d3a1-111">Configuring Message Flow Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 <span data-ttu-id="9d3a1-112">Zawiera opis sposobu konfigurowania śledzenia przepływu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="9d3a1-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="9d3a1-113">Odwołanie do zdarzenia śledzenia analitycznego</span><span class="sxs-lookup"><span data-stu-id="9d3a1-113">Analytic Trace Event Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 <span data-ttu-id="9d3a1-114">Przedstawia tabelę zdarzeń identyfikatorów ich poziomów zdarzeń, komunikaty o zdarzeniach i słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="9d3a1-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d3a1-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d3a1-115">See Also</span></span>  
 [<span data-ttu-id="9d3a1-116">Usługi i śledzenie zdarzeń programu WCF dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9d3a1-116">WCF Services and Event Tracing for Windows</span></span>](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [<span data-ttu-id="9d3a1-117">Zdarzenia śledzenia do śledzenia zdarzeń w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="9d3a1-117">Tracking Events into Event Tracing in Windows</span></span>](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
