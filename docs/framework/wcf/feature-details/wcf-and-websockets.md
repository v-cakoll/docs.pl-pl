---
title: Program WCF i technologia WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: ac888db14ebd21c4aed2f717c1f71bed310b8388
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498530"
---
# <a name="wcf-and-websockets"></a>Program WCF i technologia WebSockets
.NET Framework 4.5 wprowadzono obsługę protokołu WebSockets programu Windows Communication Foundation.  Obiekty Websocket jest efektywnego, oparta na standardach technologia, która umożliwia komunikację dwukierunkową za pośrednictwem standardowych portów HTTP 80 i 443. Użycie standardowych portów HTTP umożliwia Websocket do komunikacji w sieci Web za pośrednictwem pośredników.  Dwa nowe standardowe powiązania zostały dodane do obsługi komunikacji za pośrednictwem transportu protokołu WebSocket. <xref:System.ServiceModel.NetHttpBinding> i <xref:System.ServiceModel.NetHttpsBinding>. Można skonfigurować ustawienia specyficzne dla protokołu WebSockets na <xref:System.ServiceModel.Channels.HttpTransportBindingElement> po zalogowaniu się do <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> właściwości.
  
## <a name="in-this-section"></a>W tej sekcji  
 [Używanie elementu NetHttpBinding](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 W tym artykule omówiono <xref:System.ServiceModel.NetHttpBinding> i sposobie konfigurowania go.  
  
 [Instrukcje: tworzenie usługi WCF komunikującej się przez protokół WebSockets](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 Opisuje sposób tworzenia usługi WCF komunikującej się przez protokół Websockets.  
  
## <a name="reference"></a>Tematy pomocy  
  
## <a name="related-sections"></a>Sekcje pokrewne
