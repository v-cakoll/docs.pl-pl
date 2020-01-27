---
title: Zabezpieczanie usług i klientów
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: 719ab26198bd7b83310025e03e541fa11b109612
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746413"
---
# <a name="securing-services-and-clients"></a>Zabezpieczanie usług i klientów
Informacje przedstawione w tej sekcji koncentrują się na zabezpieczeniach programistycznych w programie Windows Communication Foundation (WCF). Ogólnie rzecz biorąc, obejmuje to wybranie odpowiedniego powiązania dostarczonego przez system, ustawienie właściwości elementu zabezpieczeń, a następnie ustawienie właściwości zachowań usługi, które określają sposób pobierania poświadczeń do użycia przez usługę lub klienta. Te techniki obejmują wymagania dotyczące zabezpieczeń większości użytkowników w większości scenariuszy, jak pokazano w [typowych scenariuszach zabezpieczeń](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Jeśli scenariusz wymaga większej liczby możliwości, należy najpierw zapoznać [się z funkcjami zabezpieczeń i powiązaniami niestandardowymi](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); Jeśli rozwiązanie nie jest widoczne, zobacz [rozszerzanie zabezpieczeń](../../../../docs/framework/wcf/extending/extending-security.md). W przypadku tworzenia (lub współpracy z programem) systemu, który używa rozbudowanych oświadczeń, zapoznaj się z tematami w temacie [autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 Omówienie modelu programowania używanego do zabezpieczania wiadomości.  
  
 [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 Omówienie sposobów zabezpieczania komunikatów za pomocą warstwy transportowej.  
  
 [Zabezpieczenia komunikatów](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 Podsumowuje przyczyny używania zabezpieczeń na poziomie komunikatów w Windows Communication Foundation (WCF).  
  
 [Bezpieczne sesje](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 Omówienie zagadnień wymaganych podczas zabezpieczania sesji programu WCF.  
  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 Wyjaśnienie niektórych typowych zadań wymaganych w przypadku używania certyfikatów X. 509.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
