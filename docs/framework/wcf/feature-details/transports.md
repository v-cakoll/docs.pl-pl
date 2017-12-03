---
title: Transporty w programie Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9275f1812111365ed6b0fb3be6957cd9ca883fdf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="transports-in-windows-communication-foundation"></a>Transporty w programie Windows Communication Foundation
Warstwa transportu jest na najniższym poziomie stosu kanału. Transporty główny używany w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] są HTTP, HTTPS TCP i nazwane potoki. Tematy w tej sekcji omówiono w nim wybierania tych transportów Konfigurowanie transportu i ustawienie właściwości dostrajania.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zawiera dodatkowe transportów. Informacje o transporcie MSMQ (MSMQ), zobacz [kolejki i sesje niezawodne](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md). Aby uzyskać informacje o transporcie peer-to-peer, zobacz [sieci Peer-to-Peer](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wybieranie transportu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 W tym artykule opisano trzy główne transportu i zagadnienia dotyczące wybranie jednego.  
  
 [Wybieranie kodera komunikatów](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 Zawiera opis czynników, które należy wziąć pod uwagę podczas wybierania element powiązania Kodowanie komunikatu.  
  
 [Strumieniowy Transfer komunikatów](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 Zawiera opis sposobu konfigurowania warstwy transportowej w celu przesyłania strumieniowego.  
  
 [Konfigurowanie protokołów HTTP i HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 Zawiera opis sposobu konfigurowania elementy powiązania transportu HTTP i HTTPS.  
  
 [Porady: Zastąp rezerwację adresu URL programu WCF ograniczoną rezerwacją](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Informacje dotyczące używania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zastrzeżenia ograniczone adresu URL.  
  
 [Przydziały dla transportu](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 Zawiera opis zagadnień w Ustawianie przydziałów dostępne w warstwie transportowej.  
  
 [Praca z translatorami adresów sieciowych i zapór](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 Zawiera opis sposobu konfigurowania warstwy transportowej, gdy komunikaty są wysyłane lub odbierane za zaporą lub w przypadku translatora adresów sieciowych (NAT).  
  
 [Udostępniania portów Net.TCP](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 Informacje dotyczące używania składnik Udostępnianie portów Net.TCP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)
