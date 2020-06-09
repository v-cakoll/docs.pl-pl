---
title: Transporty w programie Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 077d63d8038b245a68083611897c1e6c68971071
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598674"
---
# <a name="transports-in-windows-communication-foundation"></a>Transporty w programie Windows Communication Foundation
Warstwa transportu jest na najniższym poziomie stosu kanału. Główne transporty używane w Windows Communication Foundation (WCF) to HTTP, HTTPS, TCP i nazwane potoki. W tematach w tej sekcji omówiono wybór między tymi transportami, Konfigurowanie transportu i Ustawianie właściwości dostrajania.  
  
 Usługa WCF oferuje dodatkowe transporty. Aby uzyskać informacje na temat transportu usługi kolejkowania komunikatów (MSMQ), zobacz [kolejki i sesje niezawodne](queues-and-reliable-sessions.md). Aby uzyskać informacje o transportach równorzędnych, zobacz [sieci peer-to-](peer-to-peer-networking.md)peer.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wybieranie transportu](choosing-a-transport.md)  
 Opisuje trzy główne transporty i zagadnienia związane z wybraniem jednej z nich.  
  
 [Wybieranie kodera komunikatów](choosing-a-message-encoder.md)  
 Opisuje czynniki, które należy wziąć pod uwagę podczas wybierania elementu powiązania kodowania komunikatów.  
  
 [Strumieniowy transfer komunikatów](streaming-message-transfer.md)  
 Opisuje sposób konfigurowania warstwy transportu na potrzeby przesyłania strumieniowego.  
  
 [Konfigurowanie protokołów HTTP i HTTPS](configuring-http-and-https.md)  
 Opisuje sposób konfigurowania elementów powiązania transportu HTTP i HTTPS.  
  
 [Instrukcje: Zastępowanie rezerwacji adresu URL programu WCF ograniczoną rezerwacją](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 Opisuje, jak używać rezerwacji z ograniczeniami WCFURL.  
  
 [Przydziały dla transportu](transport-quotas.md)  
 Opisuje zagadnienia dotyczące ustawiania przydziałów dostępnych w warstwie transportowej.  
  
 [Praca z translatorami adresów sieciowych i zaporami](working-with-nats-and-firewalls.md)  
 Opisuje sposób konfigurowania warstwy transportu w przypadku, gdy komunikaty są wysyłane lub odbierane za zaporą lub w przypadku obecności translacji adresów sieciowych (NAT).  
  
 [Współużytkowanie portów w składniku Net.TCP](net-tcp-port-sharing.md)  
 Opisuje, jak używać składnika do udostępniania portów Net. TCP programu WCF.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Powiązania](bindings.md)  
  
 [Rozszerzanie powiązań](../extending/extending-bindings.md)
