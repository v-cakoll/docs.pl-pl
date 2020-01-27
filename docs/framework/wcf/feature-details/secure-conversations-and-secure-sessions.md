---
title: Bezpieczne konwersacje i bezpieczne sesje
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: 887b2e6e6553a910de046950514869907519cf35
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746452"
---
# <a name="secure-conversations-and-secure-sessions"></a>Bezpieczne konwersacje i bezpieczne sesje
Funkcja Windows Communication Foundation (WCF) to możliwość ustanowienia bezpiecznych sesji między dwoma punktami końcowymi, które uwierzytelniają się nawzajem i zgadzają się na proces szyfrowania i podpisu cyfrowego. Na przykład punkt końcowy usługi może wymagać, aby punkt końcowy klienta wysyłał token zabezpieczający oparty na certyfikacie X. 509 na potrzeby uwierzytelniania. Po uwierzytelnieniu klienta punkt końcowy usługi zwraca token kontekstu zabezpieczeń (SCT) z powrotem do klienta, który jest następnie używany do zabezpieczenia wszystkich kolejnych komunikatów w ramach sesji. Ustanowienie tej bezpiecznej sesji powoduje, że zestaw komunikatów, które są wymieniane między dwoma punktami końcowymi, będzie bardziej wydajny, ponieważ SCT ma klucz symetryczny. Klucze asymetryczne, na których oparto certyfikaty X. 509, wymagają znacznie większej mocy obliczeniowej niż klucze symetryczne podczas generowania podpisu cyfrowego lub szyfrowania zestawu danych.  
  
 Zasady ładowania początkowego (zdefiniowane w sekcji 6.2.7 standardu [WS-SecurityPolicy](https://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/ws-securitypolicy-1.2-spec-os.html) ) zawierają potwierdzenia zabezpieczeń komunikatów używane do zabezpieczenia kanału i uwierzytelniania klienta przed parametrem RST/SCT i RSTR/SCT Exchange. Niektóre standardowe powiązania WCF mają właściwość `Security.Message.EstablishSecurityContext`, która kontroluje, czy jest używana bezpieczna konwersacja. W przypadku korzystania z niestandardowych powiązań Bootstrap jest wskazywany przez zagnieżdżanie elementów powiązań zabezpieczeń za pośrednictwem [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) w pliku konfiguracyjnym lub przez wywoływanie <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> w kodzie.  
  
 Aby uzyskać więcej informacji na temat sesji, zobacz [using Sessions](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Sesje, tworzenie wystąpień i współbieżność](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [Instrukcje: tworzenie usługi wymagającej użycia sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
