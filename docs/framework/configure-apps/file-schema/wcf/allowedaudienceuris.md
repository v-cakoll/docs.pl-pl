---
title: <allowedAudienceUris>
ms.date: 03/30/2017
ms.assetid: 0f4dc73d-d95d-4193-9755-7df4cf2b8e1c
ms.openlocfilehash: 03888600a89d72f5216c8c8cac21c9da96879ba8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919974"
---
# <a name="allowedaudienceuris"></a>\<allowedAudienceUris>
Reprezentuje kolekcję docelowych identyfikatorów URI, dla których <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można je było traktować jako prawidłowe <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> przez wystąpienie.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<serviceBehaviors>  
\<> zachowania  
\<serviceCredentials>  
\<issuedTokenAuthentication >  
\<allowedAudienceUris>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<allowedAudienceUris>
  <add allowedAudienceUri="String" />
</allowedAudienceUris>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](add-of-allowedaudienceuris.md)|Dodaje docelowy identyfikator URI, dla którego <xref:System.IdentityModel.Tokens.SamlSecurityToken> może być przeznaczony token zabezpieczający, aby można go było traktować jako ważny <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> przez wystąpienie.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication >](issuedtokenauthentication-of-servicecredentials.md)|Określa token wystawiony jako poświadczenie usługi.|  
  
## <a name="remarks"></a>Uwagi  
 Tej kolekcji należy używać w aplikacji federacyjnej, która używa usługi tokenu zabezpieczającego (STS), która wystawia <xref:System.IdentityModel.Tokens.SamlSecurityToken> tokeny zabezpieczające. Gdy usługa STS wystawia token zabezpieczający, może określić identyfikator URI usług sieci Web, dla których jest przeznaczony token zabezpieczający poprzez dodanie <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> do tokenu zabezpieczającego. Dzięki temu <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> usługa sieci Web odbiorcy może sprawdzić, czy wystawiony token zabezpieczający jest przeznaczony dla tej usługi sieci Web, określając, że to sprawdzenie powinno nastąpić, wykonując następujące czynności:  
  
- `audienceUriMode` Ustaw atrybut<xref:System.IdentityModel.Selectors.AudienceUriMode.Always> na lub .<xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> `<issuedTokenAuthentication>`  
  
- Określ zestaw prawidłowych identyfikatorów URI, dodając identyfikatory URI do tej kolekcji.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.  
  
 Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji [, zobacz How to: Skonfiguruj poświadczenia na usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>
- <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>
- [\<issuedTokenAuthentication >](issuedtokenauthentication-of-servicecredentials.md)
- [\<add>](add-of-allowedaudienceuris.md)
- [Zachowania zabezpieczeń](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Zabezpieczanie usług i klientów](../../../wcf/feature-details/securing-services-and-clients.md)
- [Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
