---
title: Program WCF i technologia WebSockets
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e84bf7a94a6a6fa980e223daf0a6c7aaf489bb6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="306d3-102">Program WCF i technologia WebSockets</span><span class="sxs-lookup"><span data-stu-id="306d3-102">WCF and WebSockets</span></span>
<span data-ttu-id="306d3-103">.NET Framework 4.5 wprowadzono obsługę protokołu WebSockets programu Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="306d3-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="306d3-104">Obiekty Websocket jest efektywnego, oparta na standardach technologia, która umożliwia komunikację dwukierunkową za pośrednictwem standardowych portów HTTP 80 i 443.</span><span class="sxs-lookup"><span data-stu-id="306d3-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="306d3-105">Użycie standardowych portów HTTP umożliwia Websocket do komunikacji w sieci Web za pośrednictwem pośredników.</span><span class="sxs-lookup"><span data-stu-id="306d3-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="306d3-106">Dwa nowe standardowe powiązania zostały dodane do obsługi komunikacji za pośrednictwem transportu protokołu WebSocket.</span><span class="sxs-lookup"><span data-stu-id="306d3-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="306d3-107"><xref:System.ServiceModel.NetHttpBinding>i <xref:System.ServiceModel.NetHttpsBinding>.</span><span class="sxs-lookup"><span data-stu-id="306d3-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="306d3-108">Można skonfigurować ustawienia specyficzne dla protokołu WebSockets na <xref:System.ServiceModel.Channels.HttpTransportBindingElement> po zalogowaniu się do <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="306d3-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="306d3-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="306d3-109">In This Section</span></span>  
 [<span data-ttu-id="306d3-110">Używanie elementu NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="306d3-110">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 <span data-ttu-id="306d3-111">W tym artykule omówiono <xref:System.ServiceModel.NetHttpBinding> i sposobie konfigurowania go.</span><span class="sxs-lookup"><span data-stu-id="306d3-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="306d3-112">Instrukcje: tworzenie usługi WCF komunikującej się przez protokół WebSockets</span><span class="sxs-lookup"><span data-stu-id="306d3-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="306d3-113">Opisuje sposób tworzenia usługi WCF komunikującej się przez protokół Websockets.</span><span class="sxs-lookup"><span data-stu-id="306d3-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="306d3-114">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="306d3-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="306d3-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="306d3-115">Related Sections</span></span>
