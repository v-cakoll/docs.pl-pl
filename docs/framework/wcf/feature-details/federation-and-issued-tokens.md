---
title: Federacja i wystawione tokeny
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: 5ea30c2e9593f289c91a47cc082becf47dedc450
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072788"
---
# <a name="federation-and-issued-tokens"></a>Federacja i wystawione tokeny
Za pomocą Windows Communication Foundation (WCF), możesz utworzyć klientów, które komunikują się bezpiecznie z usługami, które implementują specyfikacji WS-Federation i WS-Trust. Specyfikacje umożliwia XML protokołu SOAP i sieci Web Services Description Language (WSDL) zapewniają mechanizmy, które umożliwiają uwierzytelnianie i autoryzacja w obszarach różnych zaufania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Federacja](../../../../docs/framework/wcf/feature-details/federation.md)  
 Zawiera omówienie federacji.  
  
 [Federacja i zaufanie](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 Wyświetla listę problemów projektowych pod uwagę podczas tworzenia federacyjne usług lub klientów.  
  
 [Instrukcje: tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 W tym artykule opisano tworzenie klienta federacyjnego z programem WCF.  
  
 [Instrukcje: konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 W tym artykule opisano kroki tworzenia usługi federacyjnej.  
  
 [Instrukcje: tworzenie elementu WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 W tym artykule opisano jak skonfigurować klientów i usług, które używają `WSFederationHttpBinding`.  
  
 [Instrukcje: tworzenie usługi tokenów zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 W tym artykule opisano kroki tworzenia usługi tokenów zabezpieczeń.  
  
 [Tokeny i oświadczenia języka SAML (Security Assertions Markup Language)](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 W tym artykule opisano tokenów zabezpieczeń potwierdzenia Markup Language (SAML), czyli rozszerzalne i włącz możliwość tworzenia zaawansowanych typów oświadczeń.  
  
 [Instrukcje: konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 W tym artykule opisano sposób tworzenia lokalnego wystawcy tokenów zabezpieczających.  
  
 [Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Opisuje sposób wyłączanie bezpiecznej sesji na `WSFederationHttpBinding`. Wyłączanie bezpiecznej sesji jest niezbędne, podczas tworzenia kolektywu serwerów sieci Web, która wymaga sesji dla każdego klienta.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a>Zobacz także

- [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Tokeny niestandardowe](../../../../docs/framework/wcf/extending/custom-tokens.md)
- [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
