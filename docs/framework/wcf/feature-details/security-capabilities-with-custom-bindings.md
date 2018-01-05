---
title: "Możliwości zabezpieczeń powiązań niestandardowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2f26e68b9654ccd565328003596e324558f7505f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-capabilities-with-custom-bindings"></a>Możliwości zabezpieczeń powiązań niestandardowych
Najbardziej typowych zadań zabezpieczeń można wykonać za pomocą jednego powiązania dostarczane przez system. Jeśli potrzebujesz większej kontroli, jednak można utworzyć niestandardowego powiązania z <xref:System.ServiceModel.Channels.SecurityBindingElement>, zgodnie z objaśnieniem w tych tematach. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]powiązania niestandardowe, zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 W tym artykule opisano tryby uwierzytelniania, które są możliwe za pomocą niestandardowego powiązania.  
  
 [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 Opisuje podstawowe kroki tworzenia niestandardowego powiązania z elementem zabezpieczeń.  
  
 [Instrukcje: tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 Opisuje sposób tworzenia elementu zabezpieczeń dla określonego trybu uwierzytelniania.  
  
 [Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Opisuje sposób wyłączania bezpiecznej sesji podczas tworzenia usługi federacyjnej.  
  
 [Instrukcje: włączanie wykrywania powtarzania komunikatu](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 Opisuje sposób określania, gdy wystąpi atak powtarzania.  
  
 [Instrukcje: tworzenie poświadczeń pomocniczych](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 Opisuje sposób dostarczania obsługi poświadczeń z usługą, jeśli usługa wymaga.  
  
 [Instrukcje: konfigurowanie potwierdzenia sygnatury](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 Opisuje czynności, aby potwierdzić podpisów do cyfrowego podpisywania wiadomości.  
  
 [Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 Opisuje sposób ustawiania maksymalny dozwolony czas różnica między usługą i klienta.  
  
 [Instrukcje: wyłączanie szyfrowania podpisów cyfrowych](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 W tym artykule opisano, jak wyłączyć szyfrowanie podpisów cyfrowych może mieć poprawiać wydajność.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<Zabezpieczenia >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Omówienie poziomów ochrony](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
