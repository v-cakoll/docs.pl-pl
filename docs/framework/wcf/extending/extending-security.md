---
title: Rozszerzanie zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 2d2f1997534a33f246c85501e66b6aa8a684445f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190700"
---
# <a name="extending-security"></a>Rozszerzanie zabezpieczeń
Aby uwzględnić nowe oświadczenia i tokeny niestandardowe, można rozszerzyć infrastruktura zabezpieczeń programu Windows Communication Foundation (WCF). Tematy w tej sekcji pokazano, jak to zrobić.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Architektura zabezpieczeń](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)  
 Przedstawiono architekturę co system zabezpieczeń programu WCF.  
  
 [Niestandardowe poświadczenia i weryfikacja poświadczeń](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 W tym artykule wyjaśniono, jak Model tożsamości jest używany podczas sprawdzania poprawności niestandardowych poświadczeń.  
  
 [Tokeny niestandardowe](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 Wystawionych tokenów z Usługa tokenu zabezpieczającego (STS) zazwyczaj są tokeny SAML. W tym temacie wyjaśniono, jak utworzyć niestandardowy typ tokenu.  
  
 [Autoryzacja niestandardowa](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 Wyjaśnia, jak zaimplementować niestandardowy autoryzacji.  
  
 [Przesłanianie tożsamości usługi na potrzeby uwierzytelniania](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 W tym artykule opisano sposób zastąpienia tożsamości usługi na potrzeby uwierzytelniania.  
  
 [Instrukcje: tworzenie niestandardowego weryfikatora tożsamości klienta](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 Pokazuje, jak w celu weryfikowania tożsamości niestandardowego punktu końcowego.  
  
 [Instrukcje: używanie osobnych certyfikatów X.509 do podpisywania i szyfrowania](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 Komunikaty są zwykle podpisane i szyfrowane za pomocą jednego certyfikatu. W tym temacie wyjaśniono, jak dwa certyfikaty mogą być używane, gdy jest to wymagane.  
  
 [Instrukcje: zmienianie dostawcy kryptograficznego dla klucza prywatnego certyfikatu X.509](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 Wyjaśnia, jak zmienić dostawcy usług kryptograficznych, używane do zapewnienia klucza prywatnego certyfikatu X.509 oraz integrować dostawcę w ramach usług Windows Communication Foundation (WCF).  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
