---
title: "Zabezpieczanie usług i klientów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 52e07a83f5a1b84abc46f00e6fd6e80e4b9a2622
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="securing-services-and-clients"></a>Zabezpieczanie usług i klientów
Informacje przedstawione w tej sekcji koncentruje się na programowania zabezpieczeń w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Ogólnie rzecz biorąc w tym wybranie odpowiedniego powiązania dostarczane przez system, ustawianie właściwości elementu zabezpieczeń, a następnie ustawić właściwości zachowania usługi, które decydują, jak poświadczenia są pobierane do użytku przez usługi lub klienta. Te techniki obejmować wymagania dotyczące zabezpieczeń większości użytkowników w przypadku większości scenariuszy, jak pokazano w [typowe scenariusze zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Jeśli dany scenariusz wymaga więcej funkcji, należy najpierw sprawdzić [możliwości zabezpieczeń powiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); Jeśli rozwiązanie nie jest widoczna, zobacz [rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md). Jeśli tworzysz (lub współpracy z) system używający sformatowanego oświadczeń, zobacz Tematy w [autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 Omówienie modelu programowania, używany do zabezpieczania komunikatów.  
  
 [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 Przegląd sposobu zabezpieczania komunikatów za pośrednictwem warstwy transportowej.  
  
 [Zabezpieczenia komunikatów](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 Podsumowuje przyczyny przy użyciu zabezpieczeń na poziomie komunikatu w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
 [Bezpieczne sesje](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 Omówienie zagadnień wymagana, gdy Zabezpieczanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sesji.  
  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 Wyjaśnienie niektórych typowych zadań, które są wymagane podczas korzystania z certyfikatów X.509.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [Rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [Typowe scenariusze zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [Powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [Możliwości zabezpieczeń powiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [Rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
