---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 697c20d1f526cb376c2430f0006349f7d8f9b2f1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257945"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="6b0c4-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="6b0c4-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="6b0c4-102">Rejestruje pamięci podręcznej dla sesji tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6b0c4-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="6b0c4-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="6b0c4-103">\<system.identityModel></span></span>  
<span data-ttu-id="6b0c4-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="6b0c4-104">\<identityConfiguration></span></span>  
<span data-ttu-id="6b0c4-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="6b0c4-105">\<caches></span></span>  
<span data-ttu-id="6b0c4-106">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="6b0c4-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b0c4-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b0c4-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b0c4-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6b0c4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6b0c4-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6b0c4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b0c4-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6b0c4-110">Attributes</span></span>  
  
|<span data-ttu-id="6b0c4-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6b0c4-111">Attribute</span></span>|<span data-ttu-id="6b0c4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6b0c4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b0c4-113">— typ</span><span class="sxs-lookup"><span data-stu-id="6b0c4-113">type</span></span>|<span data-ttu-id="6b0c4-114">Typ, który pochodzi od klasy <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="6b0c4-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b0c4-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6b0c4-115">Child Elements</span></span>  
 <span data-ttu-id="6b0c4-116">Brak</span><span class="sxs-lookup"><span data-stu-id="6b0c4-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b0c4-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6b0c4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6b0c4-118">Element</span><span class="sxs-lookup"><span data-stu-id="6b0c4-118">Element</span></span>|<span data-ttu-id="6b0c4-119">Opis</span><span class="sxs-lookup"><span data-stu-id="6b0c4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b0c4-120">\<caches></span><span class="sxs-lookup"><span data-stu-id="6b0c4-120">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="6b0c4-121">Rejestruje pamięci podręcznych, używane przez usługę lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6b0c4-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6b0c4-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b0c4-122">Example</span></span>  
 <span data-ttu-id="6b0c4-123">Następujący kody XML pokazuje konfiguracji niestandardowej pamięci podręcznej do przechowywania tokenów zabezpieczających sesji (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="6b0c4-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="6b0c4-124">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="6b0c4-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="6b0c4-125">Aby uzyskać więcej informacji na temat tego przykładu, zobacz [Indeks przykładów kodu programu WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="6b0c4-125">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b0c4-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b0c4-126">See also</span></span>
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
