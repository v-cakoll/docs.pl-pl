---
title: Federacja i wystawione tokeny
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: b6a5411b74b53cb5e3b18cced7fd8fc09e9a9676
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491580"
---
# <a name="federation-and-issued-tokens"></a>Federacja i wystawione tokeny
Z systemu Windows Communication Foundation (WCF), można utworzyć klientów, którzy bezpiecznego komunikowania się z usługami, które implementują specyfikacji WS-Federation i WS-Trust. Specyfikacje umożliwia XML, SOAP i Web Services Description Language (WSDL) zapewniają mechanizmy, które włączyć uwierzytelnianie i autoryzację w obszarach różnych zaufania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Federacja](../../../../docs/framework/wcf/feature-details/federation.md)  
 Zawiera omówienie federacji.  
  
 [Federacja i zaufanie](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 Wyświetla listę problemów projektu pod uwagę podczas tworzenia federacyjnych, usług lub klientów.  
  
 [Instrukcje: tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 W tym artykule opisano tworzenie klienta federacyjnego z programem WCF.  
  
 [Instrukcje: konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 W tym artykule opisano kroki tworzenia usługi federacyjnej.  
  
 [Instrukcje: tworzenie elementu WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 Opisuje sposób skonfigurować klientów i usługi używające `WSFederationHttpBinding`.  
  
 [Instrukcje: tworzenie usługi tokenów zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 W tym artykule opisano kroki tworzenia usługi tokenu zabezpieczającego.  
  
 [Tokeny i oświadczenia języka SAML (Security Assertions Markup Language)](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 Opisuje tokenów zabezpieczeń potwierdzenia Markup Language (SAML), które można rozszerzać i włączyć funkcję do tworzenia zaawansowanych typów oświadczeń.  
  
 [Instrukcje: konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 Opisuje sposób tworzenia lokalnego wystawcy tokenów zabezpieczających.  
  
 [Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
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
 [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Tokeny niestandardowe](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
