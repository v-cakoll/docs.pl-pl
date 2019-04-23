---
title: Bezpieczne konwersacje i bezpieczne sesje
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: 9b2c22d6db5a773bfb3f3a41e458b530fc889d71
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224406"
---
# <a name="secure-conversations-and-secure-sessions"></a>Bezpieczne konwersacje i bezpieczne sesje
Funkcja Windows Communication Foundation (WCF) jest możliwość ustanowienia bezpiecznej sesji między dwa punkty końcowe, które wzajemne uwierzytelnianie i uzgodnić proces podpisów cyfrowych i szyfrowania. Na przykład punktu końcowego usługi może wymagać punkt końcowy klienta, aby wysłać token zabezpieczający, na podstawie certyfikatu X.509 do uwierzytelniania. Po uwierzytelnieniu klienta punktu końcowego usługi zwraca token kontekstu zabezpieczeń (SCT) do klienta, który jest następnie używany do zabezpieczenia wszystkich kolejnych komunikatów w ramach sesji. Ustanowienie tego bezpiecznej sesji umożliwia zestaw komunikatów, które są wymieniane między dwoma punktami końcowymi być bardziej efektywne, ponieważ SCT ma klucz symetryczny. Klucze asymetryczne, o certyfikatach X.509, które są oparte na, wymaga znacznie więcej moc obliczeniową niż klucze symetryczne, podczas generowania podpisu cyfrowego lub szyfrowania zestawu danych.  
  
 Zasady uruchamiania (zdefiniowane w sekcji pkt 6.2.7 [WS SecurityPolicy](https://go.microsoft.com/fwlink/?LinkId=99817) standardowe) zawiera komunikat potwierdzenia zabezpieczeń używany do bezpiecznego kanału i uwierzytelnić klienta wymianę RST/SCT i RSTR/SCT. Masz niektóre standardowe powiązania WCF `Security.Message.EstablishSecurityContext` które kontrolki czy secure konwersacji jest używana. Podczas korzystania z powiązań niestandardowych ładowania początkowego jest wskazywany przez zagnieżdżanie elementów powiązania zabezpieczeń, za pośrednictwem [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) w pliku konfiguracji lub przez wywołanie <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> w kodzie.  
  
 Aby uzyskać więcej informacji o sesjach, zobacz [przy użyciu sesji](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Sesje, tworzenie wystąpień i współbieżność](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [Instrukcje: Tworzenie usługi wymagającej użycia sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
