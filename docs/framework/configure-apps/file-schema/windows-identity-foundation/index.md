---
title: Schemat konfiguracji programu Windows Identity Foundation
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: 7d6a3b1d0a67eb349fc6c9828e74a50ed621294e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146592"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="0095b-102">Schemat konfiguracji programu Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="0095b-102">Windows Identity Foundation Configuration Schema</span></span>
<span data-ttu-id="0095b-103">Tematy w tej sekcji zawierają informacje dotyczące schematu konfiguracji Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="0095b-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="0095b-104">Można także skonfigurować aplikację do korzystania z programu WIF za pośrednictwem klasy udostępnianych przez platformę.</span><span class="sxs-lookup"><span data-stu-id="0095b-104">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="0095b-105">W ramach tych zajęć zostały wymienione w sekcji, które są traktowane odpowiednie elementy w schemacie.</span><span class="sxs-lookup"><span data-stu-id="0095b-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="0095b-106">Poniższej przedstawiono podstawowe XML tag struktury udostępnianych przez schemat konfiguracji programu WIF.</span><span class="sxs-lookup"><span data-stu-id="0095b-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="0095b-107">Atrybuty są pomijane.</span><span class="sxs-lookup"><span data-stu-id="0095b-107">Attributes are omitted.</span></span> <span data-ttu-id="0095b-108">Wyróżnione komentarze wskazują główne składniki schematu.</span><span class="sxs-lookup"><span data-stu-id="0095b-108">Highlighted comments indicate major components of the schema.</span></span>  
  
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
  
## <a name="in-this-section"></a><span data-ttu-id="0095b-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0095b-109">In This Section</span></span>  
 <span data-ttu-id="0095b-110">[\<system.identityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) opcje konfiguracji udostępnia do włączania środowiska WIF w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="0095b-110">[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
 <span data-ttu-id="0095b-111">[\<system.identityModel.services >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) udostępnia konfigurację dla pasywnego federacyjnej przy użyciu programu WIF.</span><span class="sxs-lookup"><span data-stu-id="0095b-111">[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="0095b-112">Konfiguruje moduł uwierzytelniania sesji (SAM) i moduł uwierzytelniania federacyjnego (WSFAM).</span><span class="sxs-lookup"><span data-stu-id="0095b-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0095b-113">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0095b-113">Related Sections</span></span>  
 <span data-ttu-id="0095b-114">[Konfiguracja, administrację, zarządzanie i](https://msdn.microsoft.com/library/1e03c389-de2c-4096-aaff-86b087e1bea0) w tym artykule opisano sposób konfigurowania i zarządzania aplikacjami programu WIF i usługi.</span><span class="sxs-lookup"><span data-stu-id="0095b-114">[Configuration, Administration, And Management](https://msdn.microsoft.com/library/1e03c389-de2c-4096-aaff-86b087e1bea0) Describes how to configure and manage WIF applications and services.</span></span>
