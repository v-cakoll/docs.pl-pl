---
title: Bezpieczne sesje
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
author: BrucePerlerMS
ms.openlocfilehash: 09c261afb2c64a46fc1f4619c4ec6b2e87b3fbbf
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847389"
---
# <a name="secure-sessions"></a>Bezpieczne sesje
Funkcja Windows Communication Foundation (WCF) jest niezawodne sesje, które gwarantuje, że komunikaty są odbierane w kolejności, w której zostały wysłane. W tematach w tej sekcji omówiono skutki dla bezpieczeństwa wziąć pod uwagę podczas tworzenia niezawodnej sesji. Aby uzyskać więcej informacji o sesjach niezawodnych, zobacz [przy użyciu sesji](../../../../docs/framework/wcf/using-sessions.md).  
  
> [!NOTE]
>  Podczas personifikacji jest wymagane w systemie Windows XP, należy użyć bezpiecznej sesji bez tokenu kontekstu zabezpieczeń stanową (SCT). Stosowania stanowych SCTs personifikacji, <xref:System.InvalidOperationException> zgłaszany. Aby uzyskać więcej informacji, zobacz [nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|||  
|-|-|  
|[Bezpieczne konwersacje i bezpieczne sesje](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|Bezpieczne konwersacje i bezpieczne sesje oznaczają to samo. W tym temacie opisano sposób działania bezpiecznej konwersacji, a kiedy i dlaczego używać wzorca.|  
|[Instrukcje: tworzenie bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|Przedstawiono tworzenie bezpiecznej sesji.|  
|[Instrukcje: tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|Opisano kroki tworzenia kolektywu serwerów sieci Web, który będzie utrzymywać stan i sesje z klientami.|  
|[Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|W tym artykule opisano specjalne zagadnienia dotyczące bezpiecznej sesji.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Sesje, tworzenie wystąpień i współbieżność](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [Projektowanie i implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: włączanie wykrywania powtarzania komunikatu](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [Ataki oparte na metodzie powtórzeń](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [Instrukcje: tworzenie usługi wymagającej użycia sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
