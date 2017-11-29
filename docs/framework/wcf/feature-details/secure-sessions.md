---
title: Bezpieczne sesje
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 724ea72c52296c448ead80a8f357235d625f5842
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="secure-sessions"></a>Bezpieczne sesje
Funkcja [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to niezawodnej sesji, które gwarantują, komunikaty są odbierane w kolejności wysłania. Tematy w tej sekcji omówiono wpływ zabezpieczenia wziąć pod uwagę podczas tworzenia niezawodnej sesji. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]niezawodne sesje, zobacz [sesji przy użyciu](../../../../docs/framework/wcf/using-sessions.md).  
  
> [!NOTE]
>  Jeśli wymagane jest personifikacji w systemie Windows XP, należy użyć bezpiecznej sesji bez token kontekstu zabezpieczeń stanową (SCT). Gdy stanowe SCTs są używane z personifikacji, <xref:System.InvalidOperationException> jest generowany. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nieobsługiwanych scenariuszy](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|||  
|-|-|  
|[Bezpieczne konwersacje i bezpieczne sesje](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|Bezpieczne konwersacje i bezpieczne sesje to samo. W tym temacie opisano sposób bezpiecznej konwersacji działa, oraz kiedy i dlaczego używać ze wzorcem.|  
|[Porady: tworzenie bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|Przedstawiono tworzenie bezpiecznej sesji.|  
|[Porady: tworzenie kontekstu zabezpieczeń tokenu dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|Przeprowadzi Cię przez kroki tworzenia kolektywu serwerów sieci Web, które mają być przechowywane w stan i sesje z klientami.|  
|[Zagadnienia dotyczące zabezpieczeń dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|W tym artykule opisano uwagi dotyczące bezpiecznej sesji.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Sesje, tworzenie wystąpień i współbieżność](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [Projektowanie i Implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Włączanie wykrywania powtarzania komunikatu](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [Ataki](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [Porady: Tworzenie usługi wymagającej użycia sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
