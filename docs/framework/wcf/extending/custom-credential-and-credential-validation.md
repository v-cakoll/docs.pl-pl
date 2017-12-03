---
title: "Niestandardowe poświadczenia i walidacja poświadczeń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 021a4e206a5abfb3508e8e548114de7e61dd2d04
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-credential-and-credential-validation"></a>Niestandardowe poświadczenia i walidacja poświadczeń
Zabezpieczenia w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] jest oparte na wymianie poświadczeń między usług i klientów. Większość scenariuszy zabezpieczeń można spełnić przy użyciu popularnych typów poświadczeń, takie jak Windows (Kerberos), nazwę użytkownika i hasła i certyfikatów. Jednak jeśli nowy typ poświadczeń jest wymagane, tematy w tej sekcji opisano sposób obsługi i weryfikowanie nowych typów.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 Opis sposobu dostosowywania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] weryfikacji przez dziedziczenie z <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy.  
  
 [Wskazówki: Tworzenie niestandardowego klienta i poświadczeń usługi](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 Pokazuje, jak rozszerzyć <xref:System.ServiceModel.Description.ClientCredentials> i <xref:System.ServiceModel.Description.ServiceCredentials> klasy w celu uwzględnienia nowych poświadczeń typów. Jest to pierwszy z serii tematów, które umożliwiają tworzenie niestandardowych poświadczeń.  
  
 [Jak: utworzyć dostawcę tokenu zabezpieczającego niestandardowych](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 Wyjaśniono, jak utworzyć dostawcę tokenu zabezpieczającego do obsługi nowych typów poświadczeń i zwrócić nowe tokeny dla poświadczenia. Jest to drugi tematu w serii.  
  
 [Porady: tworzenie wystawcy uwierzytelnienia tokenu zabezpieczeń niestandardowych](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 Wyjaśnia sposób tworzenia niestandardowego wystawcy uwierzytelnienia do nowego typu poświadczeń uwierzytelniania. Jest to trzeci tematu w serii.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Uwierzytelnianie](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [Autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczeń](../../../../docs/framework/wcf/feature-details/security.md)
