---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252162"
---
# <a name="caches"></a><span data-ttu-id="acde6-101">\<pamięć podręczna ></span><span class="sxs-lookup"><span data-stu-id="acde6-101">\<caches></span></span>
<span data-ttu-id="acde6-102">Rejestruje pamięci podręczne używane do tokenów sesji i wykrywania powtarzania tokenu.</span><span class="sxs-lookup"><span data-stu-id="acde6-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
<span data-ttu-id="acde6-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="acde6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="acde6-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="acde6-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="acde6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="acde6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="acde6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<pamięć podręczna >**</span><span class="sxs-lookup"><span data-stu-id="acde6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acde6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="acde6-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="acde6-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="acde6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="acde6-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="acde6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="acde6-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="acde6-110">Attributes</span></span>  
 <span data-ttu-id="acde6-111">Brak</span><span class="sxs-lookup"><span data-stu-id="acde6-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="acde6-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="acde6-112">Child Elements</span></span>  
  
|<span data-ttu-id="acde6-113">Element</span><span class="sxs-lookup"><span data-stu-id="acde6-113">Element</span></span>|<span data-ttu-id="acde6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="acde6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="acde6-115">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="acde6-115">\<sessionSecurityTokenCache></span></span>](sessionsecuritytokencache.md)|<span data-ttu-id="acde6-116">Rejestruje pamięć podręczną tokenów sesji za pomocą usługi lub kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="acde6-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="acde6-117">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="acde6-117">\<tokenReplayCache></span></span>](tokenreplaycache.md)|<span data-ttu-id="acde6-118">Rejestruje pamięć podręczną powtarzania tokenów za pomocą usługi lub kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="acde6-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="acde6-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="acde6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="acde6-120">Element</span><span class="sxs-lookup"><span data-stu-id="acde6-120">Element</span></span>|<span data-ttu-id="acde6-121">Opis</span><span class="sxs-lookup"><span data-stu-id="acde6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="acde6-122">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="acde6-122">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="acde6-123">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="acde6-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="acde6-124">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="acde6-124">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="acde6-125">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="acde6-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acde6-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="acde6-126">Remarks</span></span>  
 <span data-ttu-id="acde6-127">Element można określić na poziomie usługi `<identityConfiguration>` pod elementem lub na poziomie kolekcji `<securityTokenHandlerConfiguration>` programu obsługi tokenów zabezpieczających w ramach elementu. `<caches>`</span><span class="sxs-lookup"><span data-stu-id="acde6-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="acde6-128">Ustawienia w kolekcji obsługi tokenów zastępują te określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="acde6-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="acde6-129">Element jest reprezentowany <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> przez klasę. `<caches>`</span><span class="sxs-lookup"><span data-stu-id="acde6-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="acde6-130">Skonfigurowane pamięci podręczne są reprezentowane przez <xref:System.IdentityModel.Configuration.IdentityModelCaches> klasę.</span><span class="sxs-lookup"><span data-stu-id="acde6-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acde6-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="acde6-131">Example</span></span>  
 <span data-ttu-id="acde6-132">W poniższym kodzie XML przedstawiono konfigurację niestandardowej pamięci podręcznej dla tokenów zabezpieczających<xref:System.IdentityModel.Tokens.SessionSecurityToken>sesji ().</span><span class="sxs-lookup"><span data-stu-id="acde6-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="acde6-133">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` przykładu.</span><span class="sxs-lookup"><span data-stu-id="acde6-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
