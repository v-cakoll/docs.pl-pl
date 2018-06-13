---
title: Bezpieczne sesje
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1c7229fba8e30632f08834eb36c1fb177de7a294
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497545"
---
# <a name="secure-sessions"></a>Bezpieczne sesje
Funkcja Windows Communication Foundation (WCF) jest niezawodnej sesji, które gwarantuje, że komunikaty są odbierane w kolejności, które zostały wysłane. Tematy w tej sekcji omówiono wpływ zabezpieczenia wziąć pod uwagę podczas tworzenia niezawodnej sesji. Aby uzyskać więcej informacji na temat niezawodnej sesji, zobacz [sesji przy użyciu](../../../../docs/framework/wcf/using-sessions.md).  
  
> [!NOTE]
>  Jeśli wymagane jest personifikacji w systemie Windows XP, należy użyć bezpiecznej sesji bez token kontekstu zabezpieczeń stanową (SCT). Gdy stanowe SCTs są używane z personifikacji, <xref:System.InvalidOperationException> jest generowany. Aby uzyskać więcej informacji, zobacz [nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|||  
|-|-|  
|[Bezpieczne konwersacje i bezpieczne sesje](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|Bezpieczne konwersacje i bezpieczne sesje to samo. W tym temacie opisano sposób bezpiecznej konwersacji działa, oraz kiedy i dlaczego używać ze wzorcem.|  
|[Instrukcje: tworzenie bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|Przedstawiono tworzenie bezpiecznej sesji.|  
|[Instrukcje: tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|Przeprowadzi Cię przez kroki tworzenia kolektywu serwerów sieci Web, które mają być przechowywane w stan i sesje z klientami.|  
|[Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|W tym artykule opisano uwagi dotyczące bezpiecznej sesji.|  
  
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
