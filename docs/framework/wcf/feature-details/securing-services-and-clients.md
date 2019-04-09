---
title: Zabezpieczanie usług i klientów
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: e455c7a48e1484d5acdcc5f6cdc9098997a3ba83
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120734"
---
# <a name="securing-services-and-clients"></a>Zabezpieczanie usług i klientów
Informacje przedstawione w tej sekcji skupiono się na programowaniu zabezpieczeń w Windows Communication Foundation (WCF). Ogólnie rzecz biorąc w tym wybranie odpowiedniego powiązania dostarczane przez system, ustawienie właściwości elementu zabezpieczeń, a następnie ustawić właściwości zachowania usług, które określają sposób, jak pobrać poświadczenia do użycia przez usługę lub klienta. Techniki te obejmują wymagania dotyczące zabezpieczeń większości użytkowników w przypadku większości scenariuszy, jak pokazano na [typowe scenariusze zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Jeśli dany scenariusz wymaga więcej funkcji, należy najpierw sprawdzić [możliwości zabezpieczeń powiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); Jeśli rozwiązanie nie jest widoczny, zobacz [rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md). Jeśli tworzysz (lub współdziałanie z) system, który korzysta z zaawansowanych oświadczeń, zobacz Tematy w [autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 Omówienie modelu programowania, używany do zabezpieczenia wiadomości.  
  
 [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 Omówienie sposobu Zabezpieczanie komunikatów za pośrednictwem warstwy transportowej.  
  
 [Zabezpieczenia komunikatów](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 Zawiera podsumowanie powody do korzystania z zabezpieczeń na poziomie komunikatu w Windows Communication Foundation (WCF).  
  
 [Bezpieczne sesje](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 Omówienie zagadnień, wymagany, gdy zabezpieczania sesji programu WCF.  
  
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
  
 [Wiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [Możliwości zabezpieczeń wiązań niestandardowych](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [Rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>Zobacz także

- [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
