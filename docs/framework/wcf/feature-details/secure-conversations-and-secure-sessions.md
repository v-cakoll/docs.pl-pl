---
title: Bezpieczne konwersacje i bezpieczne sesje
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c87f53bcaa167dd7b3b039c70129efca43742c1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497610"
---
# <a name="secure-conversations-and-secure-sessions"></a>Bezpieczne konwersacje i bezpieczne sesje
Funkcja Windows Communication Foundation (WCF) jest możliwość nawiązywania bezpiecznej sesji między dwoma punktami końcowymi, które wzajemne uwierzytelnianie i uzgodnić proces podpisów cyfrowych i szyfrowania. Na przykład punkt końcowy usługi może wymagać punktu końcowego klienta do wysyłania tokenu zabezpieczającego ustalane na podstawie certyfikatu X.509 do uwierzytelniania. Po uwierzytelnieniu klient punktu końcowego usługi zwraca token kontekstu zabezpieczeń (SCT) do klienta, który jest następnie używany do zabezpieczania wszystkich kolejnych komunikatów w ramach sesji. Ustanawianie tego bezpiecznej sesji umożliwia zestaw komunikatów, które są wymieniane między dwoma punktami końcowymi będzie bardziej wydajne, ponieważ SCT ma klucz symetryczny. Klucze asymetryczne certyfikatów X.509, które są ustalane, wymagają moc obliczeniową znacznie więcej niż kluczy symetrycznych podczas generowania podpisu cyfrowego lub szyfrowania zestawu danych.  
  
 Zasady ładowania początkowego (zdefiniowany w sekcji pkt 6.2.7 [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) standardowe) zawiera komunikat potwierdzenia zabezpieczeń używany do bezpiecznego kanału i uwierzytelnienia klienta przed RST/SCT i odpowiedź RSTR/SCT wymiany. Niektóre standardowe powiązania WCF ma `Security.Message.EstablishSecurityContext` które kontrolki czy secure konwersacji jest używana. Gdy przy użyciu niestandardowych powiązań ładowania początkowego jest wskazywana przez zagnieżdżenia elementy powiązania zabezpieczeń, za pośrednictwem [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) w pliku konfiguracji lub poprzez wywołanie <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> w kodzie.  
  
 Aby uzyskać więcej informacji o sesji, zobacz [sesji przy użyciu](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Sesje, tworzenie wystąpień i współbieżność](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Instrukcje: tworzenie usługi wymagającej użycia sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
