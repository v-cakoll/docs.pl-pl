---
title: Schemat konfiguracji programu Windows Identity Foundation
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: fddff8428da7efad2823f068e89c6f621283183f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942686"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="11db8-102">Schemat konfiguracji programu Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="11db8-102">Windows Identity Foundation Configuration Schema</span></span>
<span data-ttu-id="11db8-103">Tematy w tej sekcji zawierają informacje o schemacie konfiguracji programu Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="11db8-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="11db8-104">Możesz również skonfigurować aplikację do korzystania z WIF za pomocą klas udostępnianych przez platformę.</span><span class="sxs-lookup"><span data-stu-id="11db8-104">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="11db8-105">Te klasy są zanotowane w sekcjach, które traktują odpowiednie elementy w schemacie.</span><span class="sxs-lookup"><span data-stu-id="11db8-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="11db8-106">Poniżej przedstawiono podstawową strukturę tagów XML uwidocznioną przez schemat konfiguracji WIF.</span><span class="sxs-lookup"><span data-stu-id="11db8-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="11db8-107">Atrybuty są pomijane.</span><span class="sxs-lookup"><span data-stu-id="11db8-107">Attributes are omitted.</span></span> <span data-ttu-id="11db8-108">Wyróżnione Komentarze wskazują główne składniki schematu.</span><span class="sxs-lookup"><span data-stu-id="11db8-108">Highlighted comments indicate major components of the schema.</span></span>  
  
```xml  
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
```  
  
## <a name="in-this-section"></a><span data-ttu-id="11db8-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="11db8-109">In This Section</span></span>  
 <span data-ttu-id="11db8-110">System. IdentityModel > zapewnia konfigurację umożliwiającą włączenie opcji WIF w aplikacjach. [ \<](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="11db8-110">[\<system.identityModel>](system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
 <span data-ttu-id="11db8-111">[System. IdentityModel. Services > zapewnia konfigurację pasywnego Federacji przy użyciu WIF. \<](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="11db8-111">[\<system.identityModel.services>](system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="11db8-112">Konfiguruje moduł uwierzytelniania sesji (SAM) i moduł uwierzytelniania federacyjnego (WSFAM).</span><span class="sxs-lookup"><span data-stu-id="11db8-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>
