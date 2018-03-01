---
title: "Rozszerzanie zabezpieczeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: cdd9b91ba7ff9b1e431f7d9107e72df084ba8af3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="extending-security"></a>Rozszerzanie zabezpieczeń
Aby uwzględnić nowe typy oświadczeń i tokeny niestandardowe, można rozszerzyć infrastruktura zabezpieczeń [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Tematy w tej sekcji opisano, jak to zrobić.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Architektura zabezpieczeń](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)  
 Przeprowadzi Cię przez architekturę [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń systemu.  
  
 [Niestandardowe poświadczenia i weryfikacja poświadczeń](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 Wyjaśniono, jak Model tożsamości jest używany podczas sprawdzania poprawności niestandardowych poświadczeń.  
  
 [Tokeny niestandardowe](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 Wystawione tokeny z zabezpieczeń tokenu usługi (STS) są zwykle tokeny SAML. W tym temacie wyjaśniono, jak utworzyć niestandardowy typ tokenu.  
  
 [Autoryzacja niestandardowa](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 Wyjaśniono, jak wdrożyć przeprowadzania niestandardowej autoryzacji.  
  
 [Przesłanianie tożsamości usługi na potrzeby uwierzytelniania](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 Opisuje sposób zastępowania tożsamości usługi na potrzeby uwierzytelniania.  
  
 [Instrukcje: tworzenie niestandardowego weryfikatora tożsamości klienta](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 Pokazuje, jak można sprawdzić poprawności tożsamości niestandardowej punktu końcowego.  
  
 [Instrukcje: używanie osobnych certyfikatów X.509 do podpisywania i szyfrowania](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 Komunikaty są zwykle podpisane i zaszyfrowane za pomocą jednego certyfikatu. W tym temacie opisano sposób dwa certyfikaty mogą być używane, na żądanie.  
  
 [Instrukcje: zmienianie dostawcy kryptograficznego dla klucza prywatnego certyfikatu X.509](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 Wyjaśniono, jak zmienić dostawcy usług kryptograficznych, umożliwiające uzyskanie klucza prywatnego certyfikatu X.509 i integrowanie dostawcy do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] framework.  
  
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
