---
title: Program WCF i technologia WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: ac888db14ebd21c4aed2f717c1f71bed310b8388
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768735"
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="539a5-102">Program WCF i technologia WebSockets</span><span class="sxs-lookup"><span data-stu-id="539a5-102">WCF and WebSockets</span></span>
<span data-ttu-id="539a5-103">.NET Framework 4.5 wprowadzono obsługę funkcji WebSockets w Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="539a5-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="539a5-104">Gniazda Websocket to wydajne, oparte na standardach technologia, która umożliwia komunikację dwukierunkową przez standardowe porty HTTP 80 i 443.</span><span class="sxs-lookup"><span data-stu-id="539a5-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="539a5-105">Użycie standardowych portów protokołu HTTP umożliwia WebSockets, do komunikacji w sieci Web za pośrednictwem pośredników.</span><span class="sxs-lookup"><span data-stu-id="539a5-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="539a5-106">Dwa nowe powiązania standardowa zostały dodane do obsługi komunikacji za pośrednictwem transportu protokołu WebSocket.</span><span class="sxs-lookup"><span data-stu-id="539a5-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="539a5-107"><xref:System.ServiceModel.NetHttpBinding> i <xref:System.ServiceModel.NetHttpsBinding>.</span><span class="sxs-lookup"><span data-stu-id="539a5-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="539a5-108">Można skonfigurować ustawienia specyficzne dla funkcji WebSockets na <xref:System.ServiceModel.Channels.HttpTransportBindingElement> , uzyskując dostęp do <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="539a5-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="539a5-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="539a5-109">In This Section</span></span>  
 [<span data-ttu-id="539a5-110">Używanie elementu NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="539a5-110">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 <span data-ttu-id="539a5-111">W tym artykule omówiono <xref:System.ServiceModel.NetHttpBinding> i sposobu ich konfigurowania.</span><span class="sxs-lookup"><span data-stu-id="539a5-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="539a5-112">Instrukcje: Tworzenie usługi WCF komunikującej się przez protokół WebSockets</span><span class="sxs-lookup"><span data-stu-id="539a5-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="539a5-113">W tym artykule opisano sposób tworzenia usługi WCF komunikującej się przez protokół Websockets.</span><span class="sxs-lookup"><span data-stu-id="539a5-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="539a5-114">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="539a5-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="539a5-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="539a5-115">Related Sections</span></span>
