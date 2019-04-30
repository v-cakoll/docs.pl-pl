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
# <a name="wcf-and-websockets"></a>Program WCF i technologia WebSockets
.NET Framework 4.5 wprowadzono obsługę funkcji WebSockets w Windows Communication Foundation.  Gniazda Websocket to wydajne, oparte na standardach technologia, która umożliwia komunikację dwukierunkową przez standardowe porty HTTP 80 i 443. Użycie standardowych portów protokołu HTTP umożliwia WebSockets, do komunikacji w sieci Web za pośrednictwem pośredników.  Dwa nowe powiązania standardowa zostały dodane do obsługi komunikacji za pośrednictwem transportu protokołu WebSocket. <xref:System.ServiceModel.NetHttpBinding> i <xref:System.ServiceModel.NetHttpsBinding>. Można skonfigurować ustawienia specyficzne dla funkcji WebSockets na <xref:System.ServiceModel.Channels.HttpTransportBindingElement> , uzyskując dostęp do <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> właściwości.
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie elementu NetHttpBinding](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 W tym artykule omówiono <xref:System.ServiceModel.NetHttpBinding> i sposobu ich konfigurowania.  
  
 [Instrukcje: Tworzenie usługi WCF komunikującej się przez protokół WebSockets](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 W tym artykule opisano sposób tworzenia usługi WCF komunikującej się przez protokół Websockets.  
  
## <a name="reference"></a>Tematy pomocy  
  
## <a name="related-sections"></a>Sekcje pokrewne
