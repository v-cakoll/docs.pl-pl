---
title: Bezpieczne konwersacje i bezpieczne sesje
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: 3245c062db003cc387eff7af92fabe1554311c73
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590231"
---
# <a name="secure-conversations-and-secure-sessions"></a>Bezpieczne konwersacje i bezpieczne sesje
Funkcja Windows Communication Foundation (WCF) to możliwość ustanowienia bezpiecznych sesji między dwoma punktami końcowymi, które uwierzytelniają się nawzajem i zgadzają się na proces szyfrowania i podpisu cyfrowego. Na przykład punkt końcowy usługi może wymagać, aby punkt końcowy klienta wysyłał token zabezpieczający oparty na certyfikacie X. 509 na potrzeby uwierzytelniania. Po uwierzytelnieniu klienta punkt końcowy usługi zwraca token kontekstu zabezpieczeń (SCT) z powrotem do klienta, który jest następnie używany do zabezpieczenia wszystkich kolejnych komunikatów w ramach sesji. Ustanowienie tej bezpiecznej sesji powoduje, że zestaw komunikatów, które są wymieniane między dwoma punktami końcowymi, będzie bardziej wydajny, ponieważ SCT ma klucz symetryczny. Klucze asymetryczne, na których oparto certyfikaty X. 509, wymagają znacznie większej mocy obliczeniowej niż klucze symetryczne podczas generowania podpisu cyfrowego lub szyfrowania zestawu danych.  
  
 Zasady ładowania początkowego (zdefiniowane w sekcji 6.2.7 standardu [WS-SecurityPolicy](https://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/ws-securitypolicy-1.2-spec-os.html) ) zawierają potwierdzenia zabezpieczeń komunikatów używane do zabezpieczenia kanału i uwierzytelniania klienta przed parametrem RST/SCT i RSTR/SCT Exchange. Niektóre standardowe powiązania WCF mają `Security.Message.EstablishSecurityContext` Właściwość, która kontroluje, czy jest używana bezpieczna konwersacja. W przypadku korzystania z niestandardowych powiązań Bootstrap jest wskazywany przez zagnieżdżanie elementów powiązań zabezpieczeń, za pośrednictwem [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) w pliku konfiguracyjnym lub przez wywołanie <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> w kodzie.  
  
 Aby uzyskać więcej informacji na temat sesji, zobacz [using Sessions](../using-sessions.md).  
  
## <a name="see-also"></a>Zobacz też

- [Sesje, tworzenie wystąpień i współbieżność](sessions-instancing-and-concurrency.md)
- [Instrukcje: tworzenie usługi wymagającej użycia sesji](how-to-create-a-service-that-requires-sessions.md)
