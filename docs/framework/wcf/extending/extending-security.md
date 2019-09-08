---
title: Rozszerzanie zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 45216493a3afa23f24a085964a2c43e19b197d4b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797123"
---
# <a name="extending-security"></a>Rozszerzanie zabezpieczeń
W celu uwzględnienia nowych typów i tokenów niestandardowych można zwiększyć infrastrukturę zabezpieczeń Windows Communication Foundation (WCF). W tematach w tej sekcji pokazano, jak to zrobić.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
 [Niestandardowe poświadczenia i weryfikacja poświadczeń](custom-credential-and-credential-validation.md)  
 Wyjaśnia, jak model tożsamości jest używany podczas sprawdzania poprawności poświadczeń niestandardowych.  
  
 [Tokeny niestandardowe](custom-tokens.md)  
 Wystawione tokeny z usługi tokenu zabezpieczającego (STS) są zazwyczaj tokenami SAML. W tym temacie wyjaśniono, jak utworzyć niestandardowy typ tokenu.  
  
 [Autoryzacja niestandardowa](custom-authorization.md)  
 Wyjaśnia, jak zaimplementować autoryzację niestandardową.  
  
 [Przesłanianie tożsamości usługi na potrzeby uwierzytelniania](overriding-the-identity-of-a-service-for-authentication.md)  
 Opisuje sposób przesłania tożsamości usługi na potrzeby uwierzytelniania.  
  
 [Instrukcje: Tworzenie niestandardowego weryfikatora tożsamości klienta](how-to-create-a-custom-client-identity-verifier.md)  
 Pokazuje, jak zweryfikować tożsamość niestandardowego punktu końcowego.  
  
 [Instrukcje: Używanie osobnych certyfikatów X. 509 do podpisywania i szyfrowania](how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 Komunikaty są zwykle podpisywane i szyfrowane za pomocą jednego certyfikatu. W tym temacie wyjaśniono, w jaki sposób mogą być używane dwa certyfikaty, jeśli jest to wymagane.  
  
 [Instrukcje: Zmień dostawcę usług kryptograficznych dla klucza prywatnego certyfikatu X. 509](change-cryptographic-provider-x509-certificate-private-key.md)  
 Wyjaśnia, jak zmienić dostawcę usług kryptograficznych używany do udostępniania klucza prywatnego certyfikatu X. 509 oraz jak zintegrować dostawcę z platformą Windows Communication Foundation (WCF).  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zabezpieczenia](../feature-details/security.md)  
  
 [Podstawy programowania przy użyciu programu WCF](../basic-wcf-programming.md)  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd zabezpieczeń](../feature-details/security-overview.md)
