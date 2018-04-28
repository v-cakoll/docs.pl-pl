---
title: Ataki oparte na metodzie powtórzeń
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4e827c51378b9f75835b9b98280b4995d2cae2fc
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="replay-attacks"></a>Ataki oparte na metodzie powtórzeń
A *powtarzania ataku* występuje, gdy osoba atakująca kopiuje strumienia komunikatów między dwiema stronami i odtwarzaniem strumienia do jednego lub więcej stron. Chyba że skorygowane, komputery mogą ulec ataku przetworzyć strumienia jako istotnych wiadomości, co w zakresie zły konsekwencje, takie jak nadmiarowe zamówień elementu.  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a>Powiązania mogą być narażone na ataki odbicia  
 *Odbicie ataków* są odtworzenie nadawcy wiadomości tak, jakby pochodzą od odbiornika jako odpowiedź. Standardowe *wykrywania powtarzania* w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mechanizmu nie automatycznie obsługuje to.  
  
 Odbicie ataków zostały skorygowane domyślnie, ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model usługi dodaje identyfikator podpisanej wiadomości do komunikatów żądań i oczekuje zalogowany `relates-to` nagłówka wiadomości odpowiedzi. W związku z tym komunikat żądania nie może być powtórzone w odpowiedzi. W scenariuszach zabezpieczoną wiadomość niezawodnej (RM) odbicia ataki są niewielkie, ponieważ:  
  
-   Tworzenie sekwencji i Utwórz sekwencji odpowiedzi komunikat schematy są różne.  
  
-   Jednostronne sekwencji komunikatów sekwencji, których klient wysyła nie odtwarzany powrotu do tego, ponieważ klient nie może zrozumieć takich wiadomości.  
  
-   Dupleks sekwencji dwóch sekwencji identyfikatory muszą być unikatowe. W związku z tym wiadomości wychodzącej sekwencji nie może być powtórzone zwrotnym w formie wiadomości przychodzących sekwencji (wszystkie nagłówki sekwencji i treść są podpisywane, zbyt).  
  
 Tylko powiązania, które są narażone na ataki odbicia są bez WS-Addressing: niestandardowego powiązania, które WS-Addressing wyłączone i użyj symetrycznego opartego na kluczach zabezpieczeń. <xref:System.ServiceModel.BasicHttpBinding> Nie jest używana WS-Addressing domyślnie, ale nie używa zabezpieczenia oparte na klucza symetrycznego w taki sposób, który pozwala być narażone na atak.  
  
 Środki zaradcze dla niestandardowego powiązania jest ustanawia kontekstu zabezpieczeń lub wymagają nagłówków WS-Addressing.  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a>Kolektywu serwerów sieci Web: Żądanie odtworzenie atakująca wiele węzłów  
 Klient używa usługi, która jest zaimplementowana na farmie sieci Web. Osoba atakująca odtwarzaniem żądanie wysłane do jednego węzła w farmie do innego węzła w farmie. Ponadto po uruchomieniu usługi pamięci podręcznej powtórzeń jest opróżniany, co pozwala osobie atakującej powtarzania żądania. (Pamięć podręczna zawiera wartości podpisu używane wcześniej widziany komunikat i uniemożliwia odtworzenie, więc te podpisy mogą być użyte tylko raz. Pamięci podręczne powtarzania nie są udostępniane na farmie sieci Web.)  
  
 Następujące czynniki:  
  
-   Komunikat tryb zabezpieczeń za pomocą tokenów kontekstów zabezpieczeń stanową (z lub bez bezpiecznej konwersacji włączona). Aby uzyskać więcej informacji, zobacz [porady: Tworzenie tokenu kontekstu zabezpieczeń dla bezpieczną sesję](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
-   Skonfiguruj usługę, aby użyć zabezpieczeń na poziomie transportu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Ujawnianie informacji](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Podniesienie uprawnień](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Odmowa usługi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Manipulowanie](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
