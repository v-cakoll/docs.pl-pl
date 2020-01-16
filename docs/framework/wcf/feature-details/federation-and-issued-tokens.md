---
title: Federacja i wystawione tokeny
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: d566388279f9210f70ebdb5c42512aea0425a47e
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964590"
---
# <a name="federation-and-issued-tokens"></a>Federacja i wystawione tokeny
Program Windows Communication Foundation (WCF) umożliwia tworzenie klientów, którzy komunikują się bezpiecznie z usługami, które implementują specyfikacje WS-Federation i WS-Trust. Specyfikacje wykorzystują XML, SOAP i Web Services Description Language (WSDL), aby zapewnić mechanizmy umożliwiające uwierzytelnianie i autoryzację w różnych obszarach zaufania.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Federacja](../../../../docs/framework/wcf/feature-details/federation.md)  
 Zawiera przegląd Federacji.  
  
 [Federacja i zaufanie](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 Wyświetla listę problemów projektowych, które należy wziąć pod uwagę podczas tworzenia usług federacyjnych lub klientów.  
  
 [Instrukcje: tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 Zawiera opis podstaw tworzenia klienta federacyjnego przy użyciu programu WCF.  
  
 [Instrukcje: konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 Opisuje kroki tworzenia usługi federacyjnej.  
  
 [Instrukcje: tworzenie elementu WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 Opisuje sposób konfigurowania klientów i usług korzystających z `WSFederationHttpBinding`.  
  
 [Instrukcje: tworzenie usługi tokenów zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 W tym artykule opisano kroki tworzenia usługi tokenu zabezpieczającego.  
  
 [Tokeny i oświadczenia języka SAML (Security Assertions Markup Language)](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 Opisuje tokeny języka SAML (Security Assertions Markup Language), które są rozszerzalne i umożliwiają tworzenie rozbudowanych typów zgłoszeń.  
  
 [Instrukcje: konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 Opisuje sposób tworzenia lokalnego wystawcy tokenów zabezpieczających.  
  
 [Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Opisuje sposób wyłączania bezpiecznych sesji na `WSFederationHttpBinding`. Podczas tworzenia kolektywu serwerów sieci Web wymagającego sesji dla każdego klienta należy wyłączyć bezpieczne sesje.  
  
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
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
