---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 5ad75ae18772d6e7c724f2cbf40c1e3083d5c345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941962"
---
# <a name="caches"></a><span data-ttu-id="7c7fc-101">\<pamięć podręczna ></span><span class="sxs-lookup"><span data-stu-id="7c7fc-101">\<caches></span></span>
<span data-ttu-id="7c7fc-102">Rejestruje pamięci podręczne używane do tokenów sesji i wykrywania powtarzania tokenu.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="7c7fc-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7c7fc-103">\<system.identityModel></span></span>  
<span data-ttu-id="7c7fc-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7c7fc-104">\<identityConfiguration></span></span>  
<span data-ttu-id="7c7fc-105">\<pamięć podręczna ></span><span class="sxs-lookup"><span data-stu-id="7c7fc-105">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c7fc-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c7fc-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c7fc-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7c7fc-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7c7fc-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c7fc-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7c7fc-109">Attributes</span></span>  
 <span data-ttu-id="7c7fc-110">Brak</span><span class="sxs-lookup"><span data-stu-id="7c7fc-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7c7fc-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7c7fc-111">Child Elements</span></span>  
  
|<span data-ttu-id="7c7fc-112">Element</span><span class="sxs-lookup"><span data-stu-id="7c7fc-112">Element</span></span>|<span data-ttu-id="7c7fc-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7c7fc-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c7fc-114">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="7c7fc-114">\<sessionSecurityTokenCache></span></span>](sessionsecuritytokencache.md)|<span data-ttu-id="7c7fc-115">Rejestruje pamięć podręczną tokenów sesji za pomocą usługi lub kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-115">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="7c7fc-116">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="7c7fc-116">\<tokenReplayCache></span></span>](tokenreplaycache.md)|<span data-ttu-id="7c7fc-117">Rejestruje pamięć podręczną powtarzania tokenów za pomocą usługi lub kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-117">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7c7fc-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7c7fc-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7c7fc-119">Element</span><span class="sxs-lookup"><span data-stu-id="7c7fc-119">Element</span></span>|<span data-ttu-id="7c7fc-120">Opis</span><span class="sxs-lookup"><span data-stu-id="7c7fc-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c7fc-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7c7fc-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="7c7fc-122">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-122">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="7c7fc-123">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="7c7fc-123">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="7c7fc-124">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-124">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c7fc-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c7fc-125">Remarks</span></span>  
 <span data-ttu-id="7c7fc-126">Element można określić na poziomie usługi `<identityConfiguration>` pod elementem lub na poziomie kolekcji `<securityTokenHandlerConfiguration>` programu obsługi tokenów zabezpieczających w ramach elementu. `<caches>`</span><span class="sxs-lookup"><span data-stu-id="7c7fc-126">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="7c7fc-127">Ustawienia w kolekcji obsługi tokenów zastępują te określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-127">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="7c7fc-128">Element jest reprezentowany <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> przez klasę. `<caches>`</span><span class="sxs-lookup"><span data-stu-id="7c7fc-128">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="7c7fc-129">Skonfigurowane pamięci podręczne są reprezentowane przez <xref:System.IdentityModel.Configuration.IdentityModelCaches> klasę.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-129">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c7fc-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c7fc-130">Example</span></span>  
 <span data-ttu-id="7c7fc-131">W poniższym kodzie XML przedstawiono konfigurację niestandardowej pamięci podręcznej dla tokenów zabezpieczających<xref:System.IdentityModel.Tokens.SessionSecurityToken>sesji ().</span><span class="sxs-lookup"><span data-stu-id="7c7fc-131">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="7c7fc-132">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` przykładu.</span><span class="sxs-lookup"><span data-stu-id="7c7fc-132">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
