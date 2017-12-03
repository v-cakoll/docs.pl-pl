---
title: Manipulowanie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 96ab38de1fb2a932fefd4e37cbfab3d9bfbea616
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="tampering"></a>Manipulowanie
*Manipulowanie* jest czynnością, zmienianie lub dostarczenia komunikatów wiadomości i za pomocą zmieniony komunikatu do celów innych niż to, co zostało przeznaczone.  
  
## <a name="do-not-disable-ws-addressing"></a>Nie można wyłączyć usługi WS-Addressing  
 Specyfikacja WS-Addressing zawiera nagłówki adresów dla każdej wiadomości, dzięki czemu adresat wiadomości sprawdzić nadawcy wiadomości. Tę funkcję można wyłączyć, ustawiając <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> właściwości <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
 Gdy tryb zabezpieczeń jest ustawiony na komunikat i WS-Addressing jest wyłączona, osoba atakująca może wykonać żądania z klienta i wysyłania go do innej usługi, a drugi usługi nie ma możliwości ustalenia, czy komunikat pochodzi z oryginalnego klienta. W efekcie pierwszej usługi mogą podawać się klienta po rozmowie z drugiego usługi.  
  
 Aby temu zaradzić, nigdy nie ustawiono <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> właściwości <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>i unikaj używania <xref:System.ServiceModel.Channels.MessageVersion>, takich jak statycznych <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> właściwość, która ustawia <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> właściwości <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Zagadnienia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Ujawnienie informacji](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Podniesienie uprawnień](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Odmowa usługi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 [Ataki](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
