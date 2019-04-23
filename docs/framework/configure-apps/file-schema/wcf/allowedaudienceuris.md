---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: f758fc8e0934f56f9593246497d8aba5084c4a79
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143354"
---
# <a name="allowedaudienceuris"></a>\<allowedAudienceUris>
Reprezentuje kolekcję docelowych URI, dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczeń może być kierowany aby były uważane za prawidłowe przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienia.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<issuedTokenAuthentication>  
\<allowedAudienceUris>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)|Dodaje identyfikator Uri elementu docelowego dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenu zabezpieczeń może być kierowany aby były uważane za prawidłowe przez <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wystąpienia.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|Określa token wydany jako poświadczenie usługi.|  
  
## <a name="remarks"></a>Uwagi  
 Należy używać tej kolekcji w federacyjnej aplikacji, która korzysta z usługi tokenu zabezpieczającego (STS) wysyłający <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokenów zabezpieczających. Gdy Usługa STS wystawia token zabezpieczający, można określić identyfikator URI usługi sieci Web, dla których token zabezpieczający jest przeznaczony przez dodanie <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpieczającego. Umożliwiająca <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> odbiorcy usługi sieci Web sprawdzić, czy token zabezpieczeń jest przeznaczony dla tej usługi sieci Web, określając, że ten test ma się zdarzyć, wykonując następujące czynności:  
  
-   Ustaw `audienceUriMode` atrybutu `<issuedTokenAuthentication>` do <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> lub <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly>.  
  
-   Określ zbiór prawidłowe identyfikatory URI, dodając identyfikatory URI do tej kolekcji.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Aby uzyskać więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [jak: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)
- [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
