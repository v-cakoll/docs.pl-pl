---
title: Śledzenie analityczne za pomocą funkcji ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: dd745730ca186b9489c547f790c546e95bf96372
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798092"
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="ed796-102">Śledzenie analityczne za pomocą funkcji ETW</span><span class="sxs-lookup"><span data-stu-id="ed796-102">Analytic Tracing with ETW</span></span>
<span data-ttu-id="ed796-103">Śledzenie analityczne Windows Communication Foundation (WCF) oferuje sposób przechwytywania informacji diagnostycznych podczas wykonywania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="ed796-103">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="ed796-104">Zdarzenia śledzenia analitycznego WCF są emitowane w kluczowych punktach w stosie WCF, aby umożliwić Rozwiązywanie problemów z usługami WCF w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="ed796-104">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="ed796-105">Śledzenie analityczne dla usług WCF ma minimalny wpływ na wydajność serwera produktu, który obsługuje [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] usługi WCF, ponieważ te zdarzenia są bardzo wydajnie emitowane do sesji śledzenia zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="ed796-105">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ed796-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ed796-106">In This Section</span></span>  
 [<span data-ttu-id="ed796-107">Omówienie śledzenia analitycznego</span><span class="sxs-lookup"><span data-stu-id="ed796-107">Analytic Tracing Overview</span></span>](analytic-tracing-overview.md)  
 <span data-ttu-id="ed796-108">W [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)]tym artykule omówiono sposób działania śledzenia analitycznego WCF.</span><span class="sxs-lookup"><span data-stu-id="ed796-108">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="ed796-109">Dynamiczne włączanie śledzenia danych analitycznych</span><span class="sxs-lookup"><span data-stu-id="ed796-109">Dynamically Enabling Analytic Tracing</span></span>](dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="ed796-110">W tym artykule omówiono sposób dynamicznego włączania lub wyłączania śledzenia przy użyciu funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="ed796-110">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="ed796-111">Konfigurowanie śledzenia przepływu komunikatów</span><span class="sxs-lookup"><span data-stu-id="ed796-111">Configuring Message Flow Tracing</span></span>](configuring-message-flow-tracing.md)  
 <span data-ttu-id="ed796-112">Opisuje sposób konfigurowania śledzenia przepływu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="ed796-112">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="ed796-113">Odwołanie do zdarzenia śledzenia analitycznego</span><span class="sxs-lookup"><span data-stu-id="ed796-113">Analytic Trace Event Reference</span></span>](analytic-trace-event-reference.md)  
 <span data-ttu-id="ed796-114">Pokazuje tabelę identyfikatorów zdarzeń z ich poziomami zdarzeń, komunikatami zdarzeń i słowami kluczowymi.</span><span class="sxs-lookup"><span data-stu-id="ed796-114">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed796-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed796-115">See also</span></span>

- [<span data-ttu-id="ed796-116">Usługi i śledzenie zdarzeń programu WCF dla systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ed796-116">WCF Services and Event Tracing for Windows</span></span>](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [<span data-ttu-id="ed796-117">Zdarzenia śledzenia do śledzenia zdarzeń w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="ed796-117">Tracking Events into Event Tracing in Windows</span></span>](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
