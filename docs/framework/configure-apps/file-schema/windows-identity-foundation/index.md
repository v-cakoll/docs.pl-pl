---
title: Schemat konfiguracji programu Windows Identity Foundation
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: 14d596ae77019932d169e1a84732fb8522bfc46c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152726"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="0ecd4-102">Schemat konfiguracji programu Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="0ecd4-102">Windows Identity Foundation Configuration Schema</span></span>

<span data-ttu-id="0ecd4-103">Tematy w tej sekcji zawierają informacje o schemacie konfiguracji programu Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="0ecd4-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="0ecd4-104">Możesz również skonfigurować aplikację do korzystania z WIF za pomocą klas udostępnianych przez platformę.</span><span class="sxs-lookup"><span data-stu-id="0ecd4-104">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="0ecd4-105">Te klasy są zanotowane w sekcjach, które traktują odpowiednie elementy w schemacie.</span><span class="sxs-lookup"><span data-stu-id="0ecd4-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="0ecd4-106">Poniżej przedstawiono podstawową strukturę tagów XML uwidocznioną przez schemat konfiguracji WIF.</span><span class="sxs-lookup"><span data-stu-id="0ecd4-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="0ecd4-107">Atrybuty są pomijane.</span><span class="sxs-lookup"><span data-stu-id="0ecd4-107">Attributes are omitted.</span></span> <span data-ttu-id="0ecd4-108">Wyróżnione Komentarze wskazują główne składniki schematu.</span><span class="sxs-lookup"><span data-stu-id="0ecd4-108">Highlighted comments indicate major components of the schema.</span></span>  
  
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
  
## <a name="in-this-section"></a><span data-ttu-id="0ecd4-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0ecd4-109">In This Section</span></span>  

<span data-ttu-id="0ecd4-110">[\<system.identityModel>](system-identitymodel.md)Zapewnia konfigurację umożliwiającą włączanie opcji WIF w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="0ecd4-110">[\<system.identityModel>](system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
<span data-ttu-id="0ecd4-111">[\<system.identityModel.services>](system-identitymodel-services.md)Zapewnia konfigurację pasywnego Federacji przy użyciu WIF.</span><span class="sxs-lookup"><span data-stu-id="0ecd4-111">[\<system.identityModel.services>](system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="0ecd4-112">Konfiguruje moduł uwierzytelniania sesji (SAM) i moduł uwierzytelniania federacyjnego (WSFAM).</span><span class="sxs-lookup"><span data-stu-id="0ecd4-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>
