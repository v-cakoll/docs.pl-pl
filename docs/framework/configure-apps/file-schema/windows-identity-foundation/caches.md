---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: b1d04280ef993297102d446ba5a7db54e8404dd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750790"
---
# <a name="caches"></a><span data-ttu-id="d31af-101">\<caches></span><span class="sxs-lookup"><span data-stu-id="d31af-101">\<caches></span></span>
<span data-ttu-id="d31af-102">Rejestruje pamięci podręcznych służy do tokenów sesji i wykrywania powtarzania tokenu.</span><span class="sxs-lookup"><span data-stu-id="d31af-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="d31af-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d31af-103">\<system.identityModel></span></span>  
<span data-ttu-id="d31af-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d31af-104">\<identityConfiguration></span></span>  
<span data-ttu-id="d31af-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="d31af-105">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d31af-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d31af-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d31af-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d31af-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d31af-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d31af-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d31af-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d31af-109">Attributes</span></span>  
 <span data-ttu-id="d31af-110">Brak</span><span class="sxs-lookup"><span data-stu-id="d31af-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d31af-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d31af-111">Child Elements</span></span>  
  
|<span data-ttu-id="d31af-112">Element</span><span class="sxs-lookup"><span data-stu-id="d31af-112">Element</span></span>|<span data-ttu-id="d31af-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d31af-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d31af-114">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="d31af-114">\<sessionSecurityTokenCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|<span data-ttu-id="d31af-115">Rejestruje pamięci podręcznej dla sesji tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d31af-115">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="d31af-116">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="d31af-116">\<tokenReplayCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|<span data-ttu-id="d31af-117">Rejestruje pamięci podręcznej powtórzeń tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d31af-117">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d31af-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d31af-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d31af-119">Element</span><span class="sxs-lookup"><span data-stu-id="d31af-119">Element</span></span>|<span data-ttu-id="d31af-120">Opis</span><span class="sxs-lookup"><span data-stu-id="d31af-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d31af-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d31af-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="d31af-122">Określa ustawienia tożsamości na poziomie usługi.</span><span class="sxs-lookup"><span data-stu-id="d31af-122">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="d31af-123">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="d31af-123">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="d31af-124">Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="d31af-124">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d31af-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d31af-125">Remarks</span></span>  
 <span data-ttu-id="d31af-126">A `<caches>` element może być określony na poziomie usługi w ramach `<identityConfiguration>` element lub na poziomie kolekcji programu obsługi tokenów zabezpieczeń w ramach `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d31af-126">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="d31af-127">Ustawienia w kolekcji programu obsługi tokenów zastępują ustawienia określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="d31af-127">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="d31af-128">`<caches>` Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="d31af-128">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="d31af-129">Skonfigurowane pamięci podręczne są reprezentowane przez <xref:System.IdentityModel.Configuration.IdentityModelCaches> klasy.</span><span class="sxs-lookup"><span data-stu-id="d31af-129">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d31af-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="d31af-130">Example</span></span>  
 <span data-ttu-id="d31af-131">Następujący kody XML pokazuje konfiguracji niestandardowej pamięci podręcznej do przechowywania tokenów zabezpieczających sesji (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="d31af-131">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="d31af-132">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="d31af-132">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
