---
title: Federacja i wystawione tokeny
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: aa3ed1b68cab19b0464067a2dc8f52be03279f5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="federation-and-issued-tokens"></a>Federacja i wystawione tokeny
Z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], Utwórz klientów komunikujących się bezpiecznie z usługami, które implementują specyfikacji WS-Federation i WS-Trust. Specyfikacje umożliwia XML, SOAP i Web Services Description Language (WSDL) zapewniają mechanizmy, które włączyć uwierzytelnianie i autoryzację w obszarach różnych zaufania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Federacyjna](../../../../docs/framework/wcf/feature-details/federation.md)  
 Zawiera omówienie federacji.  
  
 [Federacja i zaufanie](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 Wyświetla listę problemów projektu pod uwagę podczas tworzenia federacyjnych, usług lub klientów.  
  
 [Porady: Tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 W tym artykule opisano tworzenie klienta federacyjnego z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Porady: Konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 W tym artykule opisano kroki tworzenia usługi federacyjnej.  
  
 [Porady: tworzenie WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 Opisuje sposób skonfigurować klientów i usługi używające `WSFederationHttpBinding`.  
  
 [Porady: Tworzenie usługi tokenów zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 W tym artykule opisano kroki tworzenia usługi tokenu zabezpieczającego.  
  
 [Zabezpieczenia potwierdzenia Markup Language (SAML) tokenów i oświadczeń](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 Opisuje tokenów zabezpieczeń potwierdzenia Markup Language (SAML), które można rozszerzać i włączyć funkcję do tworzenia zaawansowanych typów oświadczeń.  
  
 [Porady: Konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 Opisuje sposób tworzenia lokalnego wystawcy tokenów zabezpieczających.  
  
 [Porady: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Opisuje sposób wyłączania bezpiecznej sesji na `WSFederationHttpBinding`. Wyłączanie bezpiecznej sesji jest niezbędne, podczas tworzenia kolektywu serwerów sieci Web, która wymaga sesji dla każdego klienta.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a>Zobacz też  
 [Autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Tokeny niestandardowe](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
