---
title: Ataki oparte na metodzie powtórzeń
ms.date: 03/30/2017
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
ms.openlocfilehash: fefcb533cedb5405736ecda70c6879ebe00b8b49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186761"
---
# <a name="replay-attacks"></a>Ataki oparte na metodzie powtórzeń
A *powtarzania atak* występuje, gdy osoba atakująca kopiuje strumienia komunikatów między dwiema stronami i odtwarza strumienia do jednego lub więcej stron. Chyba że skorygowane, komputery, które podlegają ataku przetwarzania strumienia jako wiarygodnego wiadomości, co w zakresie zły konsekwencje, takie jak nadmiarowe zamówienia elementu.  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a>Powiązania mogą paść ofiarą ataków odbicia  
 *Odbicie ataków* są odtworzenie nadawcy wiadomości tak, jakby pochodzą z odbiornika jako odpowiedzi. Standardowa *wykrywania powtarzania* w Windows Communication Foundation (WCF) mechanizm nie automatycznie obsługuje ten.  
  
 Odbicie ataków zostały skorygowane domyślnie, ponieważ model usług WCF dodaje identyfikator podpisanej wiadomości do komunikatów żądań i oczekuje, że zalogowany `relates-to` nagłówek wiadomości odpowiedzi. W związku z tym komunikat żądania nie może być powtórzone w odpowiedzi. W scenariuszach zabezpieczoną wiadomość niezawodne (RM) zostały skorygowane odbicie ataków, ponieważ:  
  
-   Tworzenie sekwencji i schematów komunikatów odpowiedzi sekwencji Utwórz są różne.  
  
-   Simpleks sekwencji sekwencję wiadomości, przysyłane przez klienta nie można odtworzyć powrotu do tego, ponieważ klient nie może rozpoznać takich wiadomości.  
  
-   Dwukierunkowe sekwencji sekwencji dwa identyfikatory muszą być unikatowe. W związku z tym wychodzącej wiadomości sekwencji nie może być powtórzone zwrotnym w formie wiadomości przychodzących sekwencji (wszystkich sekwencji nagłówki i treść są podpisane, zbyt).  
  
 Tylko powiązań, które są podatne na ataki odbicia są bez WS-Addressing: powiązań niestandardowych, które WS-Addressing wyłączone i użyj symetrycznego opartego na kluczu zabezpieczeń. <xref:System.ServiceModel.BasicHttpBinding> Nie jest używana WS-Addressing domyślnie, ale nie używa zabezpieczeń opartych na klucz symetryczny w sposób, który umożliwia są narażone na atak.  
  
 Środki zaradcze dla niestandardowego powiązania jest ustanowienie nie kontekstu zabezpieczeń lub będzie wymagał nagłówków WS-Addressing.  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a>Kolektywu serwerów sieci Web: Osoba atakująca odtworzenie żądania do wielu węzłów  
 Klient używa usługi, która jest wdrażana w ramach farmy sieci Web. Osoba atakująca odtwarza żądania, który został wysłany do jednego węzła w farmie do innego węzła w farmie. Ponadto jeśli usługa zostanie ponownie uruchomiony, pamięci podręcznej powtórzeń jest opróżniany, pozwalając osobie atakującej na żądanie oparte na metodzie powtórzeń. (Pamięć podręczna zawiera wartości podpisu używane wcześniej wyświetlany komunikat i uniemożliwia odtworzenie, dzięki czemu te podpisy, które mogą być użyte tylko raz. Pamięci podręczne powtarzania nie są współdzielone w ramach farmy sieci Web.)  
  
 Środki zaradcze obejmują:  
  
-   Komunikat tryb zabezpieczeń za pomocą tokenów kontekstu zabezpieczeń stanową (z lub bez bezpiecznej konwersacji włączona). Aby uzyskać więcej informacji, zobacz [jak: Utwórz kontekst zabezpieczeń tokenu dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
-   Skonfiguruj usługę do użycia zabezpieczenia na poziomie transportu.  
  
## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Ujawnianie informacji](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Podniesienie uprawnień](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Odmowa usługi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Manipulowanie](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
