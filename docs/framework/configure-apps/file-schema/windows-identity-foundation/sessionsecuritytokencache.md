---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0b0d3c01a81f110f79f64d75aa2ab2ff2873fedd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755048"
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="e8963-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="e8963-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="e8963-103">Rejestruje pamięci podręcznej sesji tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e8963-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="e8963-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e8963-104">\<system.identityModel></span></span>  
<span data-ttu-id="e8963-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e8963-105">\<identityConfiguration></span></span>  
<span data-ttu-id="e8963-106">\<buforuje ></span><span class="sxs-lookup"><span data-stu-id="e8963-106">\<caches></span></span>  
<span data-ttu-id="e8963-107">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="e8963-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8963-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8963-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8963-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e8963-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e8963-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e8963-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8963-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e8963-111">Attributes</span></span>  
  
|<span data-ttu-id="e8963-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e8963-112">Attribute</span></span>|<span data-ttu-id="e8963-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e8963-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8963-114">— typ</span><span class="sxs-lookup"><span data-stu-id="e8963-114">type</span></span>|<span data-ttu-id="e8963-115">Typ, który pochodzi z <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="e8963-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8963-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e8963-116">Child Elements</span></span>  
 <span data-ttu-id="e8963-117">Brak</span><span class="sxs-lookup"><span data-stu-id="e8963-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8963-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e8963-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e8963-119">Element</span><span class="sxs-lookup"><span data-stu-id="e8963-119">Element</span></span>|<span data-ttu-id="e8963-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e8963-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8963-121">\<buforuje ></span><span class="sxs-lookup"><span data-stu-id="e8963-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="e8963-122">Rejestruje pamięci podręcznych, używany przez usługę lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e8963-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e8963-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8963-123">Example</span></span>  
 <span data-ttu-id="e8963-124">Następujący kod XML przedstawia konfigurację pamięci podręcznej niestandardowy do przechowywania sesji tokenów zabezpieczających (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="e8963-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="e8963-125">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="e8963-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="e8963-126">Aby uzyskać więcej informacji dotyczących tego przykładu, zobacz [indeksu przykładowy kod WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="e8963-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8963-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8963-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
