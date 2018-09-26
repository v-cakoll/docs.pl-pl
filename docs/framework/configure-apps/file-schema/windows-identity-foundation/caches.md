---
title: '&lt;Pamięci podręczne&gt;'
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: a91a389e53354e4f5b26e1510fc2f025300d65cc
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192683"
---
# <a name="ltcachesgt"></a><span data-ttu-id="8d86e-102">&lt;Pamięci podręczne&gt;</span><span class="sxs-lookup"><span data-stu-id="8d86e-102">&lt;caches&gt;</span></span>
<span data-ttu-id="8d86e-103">Rejestruje pamięci podręcznych służy do tokenów sesji i wykrywania powtarzania tokenu.</span><span class="sxs-lookup"><span data-stu-id="8d86e-103">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="8d86e-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8d86e-104">\<system.identityModel></span></span>  
<span data-ttu-id="8d86e-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8d86e-105">\<identityConfiguration></span></span>  
<span data-ttu-id="8d86e-106">\<pamięci podręczne ></span><span class="sxs-lookup"><span data-stu-id="8d86e-106">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d86e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d86e-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d86e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8d86e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8d86e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8d86e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d86e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8d86e-110">Attributes</span></span>  
 <span data-ttu-id="8d86e-111">Brak</span><span class="sxs-lookup"><span data-stu-id="8d86e-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d86e-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8d86e-112">Child Elements</span></span>  
  
|<span data-ttu-id="8d86e-113">Element</span><span class="sxs-lookup"><span data-stu-id="8d86e-113">Element</span></span>|<span data-ttu-id="8d86e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8d86e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d86e-115">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="8d86e-115">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="8d86e-116">Rejestruje pamięci podręcznej dla sesji tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="8d86e-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="8d86e-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="8d86e-117">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="8d86e-118">Rejestruje pamięci podręcznej powtórzeń tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="8d86e-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d86e-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8d86e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8d86e-120">Element</span><span class="sxs-lookup"><span data-stu-id="8d86e-120">Element</span></span>|<span data-ttu-id="8d86e-121">Opis</span><span class="sxs-lookup"><span data-stu-id="8d86e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d86e-122">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8d86e-122">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="8d86e-123">Określa ustawienia tożsamości na poziomie usługi.</span><span class="sxs-lookup"><span data-stu-id="8d86e-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="8d86e-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8d86e-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="8d86e-125">Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="8d86e-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d86e-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d86e-126">Remarks</span></span>  
 <span data-ttu-id="8d86e-127">A `<caches>` element może być określony na poziomie usługi w ramach `<identityConfiguration>` element lub na poziomie kolekcji programu obsługi tokenów zabezpieczeń w ramach `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="8d86e-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="8d86e-128">Ustawienia w kolekcji programu obsługi tokenów zastępują ustawienia określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="8d86e-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="8d86e-129">`<caches>` Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="8d86e-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="8d86e-130">Skonfigurowane pamięci podręczne są reprezentowane przez <xref:System.IdentityModel.Configuration.IdentityModelCaches> klasy.</span><span class="sxs-lookup"><span data-stu-id="8d86e-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d86e-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d86e-131">Example</span></span>  
 <span data-ttu-id="8d86e-132">Następujący kody XML pokazuje konfiguracji niestandardowej pamięci podręcznej do przechowywania tokenów zabezpieczających sesji (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="8d86e-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="8d86e-133">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="8d86e-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
