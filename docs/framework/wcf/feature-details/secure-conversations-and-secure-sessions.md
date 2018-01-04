---
title: Bezpieczne konwersacje i bezpieczne sesje
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d519640c40daf248a01a19f0450f3aea8de6cc04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="secure-conversations-and-secure-sessions"></a>Bezpieczne konwersacje i bezpieczne sesje
Funkcja [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] jest możliwość nawiązywania bezpiecznej sesji między dwoma punktami końcowymi, które wzajemne uwierzytelnianie i uzgodnić proces podpisów cyfrowych i szyfrowania. Na przykład punkt końcowy usługi może wymagać punktu końcowego klienta do wysyłania tokenu zabezpieczającego ustalane na podstawie certyfikatu X.509 do uwierzytelniania. Po uwierzytelnieniu klient punktu końcowego usługi zwraca token kontekstu zabezpieczeń (SCT) do klienta, który jest następnie używany do zabezpieczania wszystkich kolejnych komunikatów w ramach sesji. Ustanawianie tego bezpiecznej sesji umożliwia zestaw komunikatów, które są wymieniane między dwoma punktami końcowymi będzie bardziej wydajne, ponieważ SCT ma klucz symetryczny. Klucze asymetryczne certyfikatów X.509, które są ustalane, wymagają moc obliczeniową znacznie więcej niż kluczy symetrycznych podczas generowania podpisu cyfrowego lub szyfrowania zestawu danych.  
  
 Zasady ładowania początkowego (zdefiniowany w sekcji pkt 6.2.7 [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) standardowe) zawiera komunikat potwierdzenia zabezpieczeń używany do bezpiecznego kanału i uwierzytelnienia klienta przed RST/SCT i odpowiedź RSTR/SCT wymiany. Niektóre [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] standardowe powiązania ma `Security.Message.EstablishSecurityContext` które kontrolki czy secure konwersacji jest używana. Gdy przy użyciu niestandardowych powiązań ładowania początkowego jest wskazywana przez zagnieżdżenia elementy powiązania zabezpieczeń, za pośrednictwem [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) w pliku konfiguracji lub poprzez wywołanie <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> w kodzie.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]sesje, zobacz [sesji przy użyciu](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Sesje, tworzenie wystąpień i współbieżność](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Instrukcje: tworzenie usługi wymagającej użycia sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
