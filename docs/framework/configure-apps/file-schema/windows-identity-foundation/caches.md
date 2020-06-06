---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252162"
---
# \<caches>
<span data-ttu-id="6fc2f-101">Rejestruje pamięci podręczne używane do tokenów sesji i wykrywania powtarzania tokenu.</span><span class="sxs-lookup"><span data-stu-id="6fc2f-101">Registers the caches used for session tokens and token replay detection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a><span data-ttu-id="6fc2f-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fc2f-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fc2f-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6fc2f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="6fc2f-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6fc2f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fc2f-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6fc2f-105">Attributes</span></span>  
 <span data-ttu-id="6fc2f-106">Brak</span><span class="sxs-lookup"><span data-stu-id="6fc2f-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6fc2f-107">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6fc2f-107">Child Elements</span></span>  
  
|<span data-ttu-id="6fc2f-108">Element</span><span class="sxs-lookup"><span data-stu-id="6fc2f-108">Element</span></span>|<span data-ttu-id="6fc2f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="6fc2f-109">Description</span></span>|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|<span data-ttu-id="6fc2f-110">Rejestruje pamięć podręczną tokenów sesji za pomocą usługi lub kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="6fc2f-110">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[\<tokenReplayCache>](tokenreplaycache.md)|<span data-ttu-id="6fc2f-111">Rejestruje pamięć podręczną powtarzania tokenów za pomocą usługi lub kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="6fc2f-111">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6fc2f-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6fc2f-112">Parent Elements</span></span>  
  
|<span data-ttu-id="6fc2f-113">Element</span><span class="sxs-lookup"><span data-stu-id="6fc2f-113">Element</span></span>|<span data-ttu-id="6fc2f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="6fc2f-114">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="6fc2f-115">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="6fc2f-115">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="6fc2f-116">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="6fc2f-116">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fc2f-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6fc2f-117">Remarks</span></span>  
 <span data-ttu-id="6fc2f-118">`<caches>`Element można określić na poziomie usługi pod `<identityConfiguration>` elementem lub na poziomie kolekcji programu obsługi tokenów zabezpieczających w ramach `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6fc2f-118">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="6fc2f-119">Ustawienia w kolekcji obsługi tokenów zastępują te określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="6fc2f-119">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="6fc2f-120">`<caches>`Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> klasę.</span><span class="sxs-lookup"><span data-stu-id="6fc2f-120">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="6fc2f-121">Skonfigurowane pamięci podręczne są reprezentowane przez <xref:System.IdentityModel.Configuration.IdentityModelCaches> klasę.</span><span class="sxs-lookup"><span data-stu-id="6fc2f-121">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fc2f-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="6fc2f-122">Example</span></span>  
 <span data-ttu-id="6fc2f-123">W poniższym kodzie XML przedstawiono konfigurację niestandardowej pamięci podręcznej dla tokenów zabezpieczających sesji ( <xref:System.IdentityModel.Tokens.SessionSecurityToken> ).</span><span class="sxs-lookup"><span data-stu-id="6fc2f-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="6fc2f-124">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` przykładu.</span><span class="sxs-lookup"><span data-stu-id="6fc2f-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
