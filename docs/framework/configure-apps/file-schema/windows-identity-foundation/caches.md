---
title: "&lt;pamięci podręczne&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b9dfa7b2f0952f3f9e224ad51fd4d9c0c263ce04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcachesgt"></a><span data-ttu-id="e566c-102">&lt;pamięci podręczne&gt;</span><span class="sxs-lookup"><span data-stu-id="e566c-102">&lt;caches&gt;</span></span>
<span data-ttu-id="e566c-103">Rejestruje pamięci podręczne tokeny sesji i wykrywania powtórzeń tokenów.</span><span class="sxs-lookup"><span data-stu-id="e566c-103">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="e566c-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="e566c-104">\<system.identityModel></span></span>  
<span data-ttu-id="e566c-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e566c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="e566c-106">\<buforuje ></span><span class="sxs-lookup"><span data-stu-id="e566c-106">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e566c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e566c-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e566c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e566c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e566c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e566c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e566c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e566c-110">Attributes</span></span>  
 <span data-ttu-id="e566c-111">Brak</span><span class="sxs-lookup"><span data-stu-id="e566c-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e566c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e566c-112">Child Elements</span></span>  
  
|<span data-ttu-id="e566c-113">Element</span><span class="sxs-lookup"><span data-stu-id="e566c-113">Element</span></span>|<span data-ttu-id="e566c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e566c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e566c-115">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="e566c-115">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="e566c-116">Rejestruje pamięci podręcznej sesji tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e566c-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="e566c-117">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="e566c-117">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="e566c-118">Rejestruje pamięci podręcznej powtórzeń tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e566c-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e566c-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e566c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e566c-120">Element</span><span class="sxs-lookup"><span data-stu-id="e566c-120">Element</span></span>|<span data-ttu-id="e566c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="e566c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e566c-122">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e566c-122">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="e566c-123">Określa ustawienia tożsamości poziomu usług.</span><span class="sxs-lookup"><span data-stu-id="e566c-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="e566c-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e566c-124">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="e566c-125">Zapewnia token obsługi konfiguracji dla kolekcji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e566c-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e566c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e566c-126">Remarks</span></span>  
 <span data-ttu-id="e566c-127">A `<caches>` elementu można określić na poziomie usługi pod `<identityConfiguration>` element lub na poziomie kolekcji programu obsługi tokenów zabezpieczeń w obszarze `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e566c-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="e566c-128">Ustawienia w kolekcji programu obsługi tokenów zastępują ustawienia określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e566c-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="e566c-129">`<caches>` Reprezentowany przez element <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="e566c-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="e566c-130">Skonfigurowany pamięci podręcznych są reprezentowane przez <xref:System.IdentityModel.Configuration.IdentityModelCaches> klasy.</span><span class="sxs-lookup"><span data-stu-id="e566c-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e566c-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="e566c-131">Example</span></span>  
 <span data-ttu-id="e566c-132">Następujący kod XML przedstawia konfigurację pamięci podręcznej niestandardowy do przechowywania sesji tokenów zabezpieczających (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="e566c-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="e566c-133">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="e566c-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
