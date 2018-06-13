---
title: Transporty w programie Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 6bb8e8b90c26533661684bd403b9ec439f1bb37e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498127"
---
# <a name="transports-in-windows-communication-foundation"></a>Transporty w programie Windows Communication Foundation
Warstwa transportu jest na najniższym poziomie stosu kanału. Transporty główne używane w systemie Windows Communication Foundation (WCF) są HTTP, HTTPS TCP i nazwane potoki. Tematy w tej sekcji omówiono w nim wybierania tych transportów Konfigurowanie transportu i ustawienie właściwości dostrajania.  
  
 Usługi WCF zawiera dodatkowe transportów. Informacje o transporcie MSMQ (MSMQ), zobacz [kolejki i sesje niezawodne](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md). Aby uzyskać informacje o transporcie peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 W tym artykule opisano trzy główne transportu i zagadnienia dotyczące wybranie jednego.  
  
 [Wybieranie kodera komunikatów](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 Zawiera opis czynników, które należy wziąć pod uwagę podczas wybierania element powiązania Kodowanie komunikatu.  
  
 [Strumieniowy transfer komunikatów](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 Zawiera opis sposobu konfigurowania warstwy transportowej w celu przesyłania strumieniowego.  
  
 [Konfigurowanie protokołów HTTP i HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 Zawiera opis sposobu konfigurowania elementy powiązania transportu HTTP i HTTPS.  
  
 [Instrukcje: zastępowanie rezerwacji adresu URL programu WCF ograniczoną rezerwacją](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Informacje dotyczące używania zastrzeżenia WCFURL ograniczone.  
  
 [Przydziały dla transportu](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 Zawiera opis zagadnień w Ustawianie przydziałów dostępne w warstwie transportowej.  
  
 [Praca z translatorami adresów sieciowych i zaporami](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 Zawiera opis sposobu konfigurowania warstwy transportowej, gdy komunikaty są wysyłane lub odbierane za zaporą lub w przypadku translatora adresów sieciowych (NAT).  
  
 [Współużytkowanie portów w składniku Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 Informacje dotyczące używania składnik Udostępnianie portów Net.TCP usługi WCF.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)
