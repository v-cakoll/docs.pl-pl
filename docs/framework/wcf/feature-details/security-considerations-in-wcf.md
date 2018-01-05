---
title: "Zagadnienia dotyczące zabezpieczeń w programie WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
caps.latest.revision: "49"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f35bd56bdc69f8c57a7e46984778051b57b7a06a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-considerations-in-wcf"></a>Zagadnienia dotyczące zabezpieczeń w programie WCF
Tematy w tej sekcji listy różne elementy związane z zabezpieczeniami wziąć pod uwagę podczas projektowania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Ujawnianie informacji](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 W tym artykule omówiono różne sposoby, czy informacje mogą być ujawniane lub ataku i jak zaradzić.  
  
 [Podniesienie uprawnień](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 Omówienie skutków nadanie uprawnień autoryzacji atakująca poza tymi, które początkowo przyznawane i sposobu zaradzić.  
  
 [Odmowa usługi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 W tym artykule omówiono, co się stanie, gdy system jest nie można przetworzyć wiadomości odpowiednio i sposobie jej unikania.  
  
 [Manipulowanie](../../../../docs/framework/wcf/feature-details/tampering.md)  
 W tym artykule omówiono zmiany wiadomości lub dostarczenia komunikatów i sposobie jej unikania.  
  
 [Ataki oparte na metodzie powtórzeń](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 W tym artykule omówiono, co się stanie, gdy osoba atakująca kopiuje strumienia komunikatów między dwiema stronami i odtwarzaniem strumienia do co najmniej jednej strony oraz sposób ograniczenia tego.  
  
 [Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)  
 W tym artykule omówiono następujące elementy, które mają wpływ na zabezpieczeń podczas implementowania bezpiecznej sesji.  
  
 [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)  
 Wyświetla listę różnych scenariuszy, które nie obsługują określonej proporcji zabezpieczeń i powinna być unikać lub uznane za.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wytyczne dotyczące zabezpieczeń i najlepsze rozwiązania](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md)
