---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: b812673ac1c015adde357d3c0707d85643aad3e9
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47401379"
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="55372-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="55372-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="55372-103">Rejestruje pamięci podręcznej dla sesji tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="55372-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="55372-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="55372-104">\<system.identityModel></span></span>  
<span data-ttu-id="55372-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="55372-105">\<identityConfiguration></span></span>  
<span data-ttu-id="55372-106">\<pamięci podręczne ></span><span class="sxs-lookup"><span data-stu-id="55372-106">\<caches></span></span>  
<span data-ttu-id="55372-107">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="55372-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55372-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="55372-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55372-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="55372-109">Attributes and Elements</span></span>  
 <span data-ttu-id="55372-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="55372-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55372-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="55372-111">Attributes</span></span>  
  
|<span data-ttu-id="55372-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="55372-112">Attribute</span></span>|<span data-ttu-id="55372-113">Opis</span><span class="sxs-lookup"><span data-stu-id="55372-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="55372-114">— typ</span><span class="sxs-lookup"><span data-stu-id="55372-114">type</span></span>|<span data-ttu-id="55372-115">Typ, który pochodzi od klasy <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="55372-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55372-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="55372-116">Child Elements</span></span>  
 <span data-ttu-id="55372-117">Brak</span><span class="sxs-lookup"><span data-stu-id="55372-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55372-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="55372-118">Parent Elements</span></span>  
  
|<span data-ttu-id="55372-119">Element</span><span class="sxs-lookup"><span data-stu-id="55372-119">Element</span></span>|<span data-ttu-id="55372-120">Opis</span><span class="sxs-lookup"><span data-stu-id="55372-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55372-121">\<pamięci podręczne ></span><span class="sxs-lookup"><span data-stu-id="55372-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="55372-122">Rejestruje pamięci podręcznych, używane przez usługę lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="55372-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="55372-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="55372-123">Example</span></span>  
 <span data-ttu-id="55372-124">Następujący kody XML pokazuje konfiguracji niestandardowej pamięci podręcznej do przechowywania tokenów zabezpieczających sesji (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="55372-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="55372-125">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="55372-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="55372-126">Aby uzyskać więcej informacji na temat tego przykładu, zobacz [Indeks przykładów kodu programu WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="55372-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="55372-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55372-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
