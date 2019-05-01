---
title: Transporty w programie Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 6bb8e8b90c26533661684bd403b9ec439f1bb37e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933734"
---
# <a name="transports-in-windows-communication-foundation"></a>Transporty w programie Windows Communication Foundation
Warstwa transportu jest na najniższym poziomie stosu kanału. Główne transportów używane w Windows Communication Foundation (WCF) są HTTP, HTTPS, TCP i nazwane potoki. Tematy w tej sekcji omówiono wybierania tych transportu, konfigurowanie transportu i ustawienie właściwości dostrajania.  
  
 Usługi WCF zawiera dodatkowe transportów. Aby uzyskać informacji na temat transportu MSMQ (MSMQ), zobacz [kolejki i sesje niezawodne](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md). Aby uzyskać informacje o transporcie peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 W tym artykule opisano trzy główne transportu i zagadnienia dotyczące wybierania go.  
  
 [Wybieranie kodera komunikatów](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 Zawiera opis czynników, które należy wziąć pod uwagę podczas wybierania element powiązania Kodowanie komunikatu.  
  
 [Strumieniowy transfer komunikatów](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 W tym artykule opisano sposób konfigurowania warstwy transportowej w celu przesyłania strumieniowego.  
  
 [Konfigurowanie protokołów HTTP i HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 W tym artykule opisano sposób konfigurowania elementów wiązania transportu HTTP i HTTPS.  
  
 [Instrukcje: Zastępowanie rezerwacji adresu URL programu WCF ograniczoną rezerwacją](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Opisuje sposób używania rezerwacje WCFURL z ograniczeniami.  
  
 [Przydziały dla transportu](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 W tym artykule opisano zagadnienia dotyczące ustawiania przydziałów, które są dostępne w warstwie transportowej.  
  
 [Praca z translatorami adresów sieciowych i zaporami](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 W tym artykule opisano sposób konfigurowania warstwy transportowej, gdy komunikaty są wysyłane lub odbierane za zaporą lub w przypadku, gdy występuje translatora adresów sieciowych (NAT).  
  
 [Współużytkowanie portów w składniku Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 Opisuje sposób używania składnika współużytkowania portów Net.TCP funkcji WCF.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)
