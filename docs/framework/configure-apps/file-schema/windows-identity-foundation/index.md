---
title: Schemat konfiguracji programu Windows Identity Foundation
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: 8dc58f3dc68ee226228056e457914c9dfa53cca5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251974"
---
# <a name="windows-identity-foundation-configuration-schema"></a>Schemat konfiguracji programu Windows Identity Foundation

Tematy w tej sekcji zawierają informacje o schemacie konfiguracji programu Windows Identity Foundation (WIF). Możesz również skonfigurować aplikację do korzystania z WIF za pomocą klas udostępnianych przez platformę. Te klasy są zanotowane w sekcjach, które traktują odpowiednie elementy w schemacie. Poniżej przedstawiono podstawową strukturę tagów XML uwidocznioną przez schemat konfiguracji WIF. Atrybuty są pomijane. Wyróżnione Komentarze wskazują główne składniki schematu.  
  
```xml  
<configuration>  
    <system.identityModel>  
        <!-- Service Configuration -->  
        <identityConfiguration>  
            <caches>  
                <sessionSecurityTokenCache />  
                <tokenReplayCache />  
            </caches>  
      
            <certificateValidation>  
                <certificateValidator />   
            </certificateValidation>  
      
            <claimsAuthenticationManager />  
      
            <claimsAuthorizationManager>  
                <optionalConfigurationElement>  
            </claimsAuthorizationManager>  
      
            <claimTypeRequired>  
                <claimType />   
            </claimTypeRequired>  
      
            <tokenReplayDetection />  
      
            <!-- Security Token Handler Collection Configuration -->  
            <securityTokenHandlers>  
                <add>  
                    <!-- Can take an optional configuration element which can be one of  
                         the following or a custom element -->  
                    <samlSecurityTokenHandlerRequirement>  
                        <nameClaimType>  
                        <roleClaimType>   
                    </samlSecurityTokenHandlerRequirement>  
      
                    <sessionSecurityTokenHandlerRequirement />  
                    <x509SecurityTokenHandlerRequirement />  
                    <userNameSecurityTokenHandlerRequirement />  
                </add>  
                <clear />  
                <remove />  
                <securityTokenHandlerConfiguration>  
                    <audienceUris>  
                        <add>  
                        <clear>  
                        <remove>  
                    </audienceUris>  
      
                    <caches>  
                        <sessionSecurityTokenCache />  
                        <tokenReplayCache />  
                    </caches>  
      
                    <certificateValidation>  
                        <certificateValidator>   
                    </certificateValidation>  
      
                    <issuerNameRegistry>  
                        <!-- Can take an optional configuration element which can be   
                             the <trustedIssuers> element to configure a configuration-based  
                             issuer name registry or can be a custom element -->  
                        <trustedIssuers>  
                            <add>  
                            <clear>  
                            <remove>  
                        </trustedIssuers>  
                    </issuerNameRegistry>  
      
                    <issuerTokenResolver />  
                    <serviceTokenResolver />  
                    <tokenReplayDetection />  
                </securityTokenHandlerConfiguration>  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
      
    <system.identityModel.services>  
        <!-- Federation Authentication Configuration -->  
        <federatedAuthentication>  
            <cookieHandler>  
                <chunkedCookieHandler />  
                <customCookieHandler />  
            </cookieHandler>  
      
            <serviceCertificate>  
                <certificateReference>  
            </serviceCertificate>  
      
            <wsFederation />  
        </federatedAuthentication>  
    </system.identityModel.services>  
</configuration>  
```  
  
## <a name="in-this-section"></a>W tej sekcji  

System. IdentityModel > zapewnia konfigurację umożliwiającą włączenie opcji WIF w aplikacjach. [ \<](system-identitymodel.md)  
  
[System. IdentityModel. Services > zapewnia konfigurację pasywnego Federacji przy użyciu WIF. \<](system-identitymodel-services.md) Konfiguruje moduł uwierzytelniania sesji (SAM) i moduł uwierzytelniania federacyjnego (WSFAM).
