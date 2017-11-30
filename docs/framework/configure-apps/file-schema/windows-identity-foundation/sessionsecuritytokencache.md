---
title: '&lt;sessionSecurityTokenCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: a1d1af398073e15ce7f73b3359366df9e5629ac6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltsessionsecuritytokencachegt"></a><span data-ttu-id="7d7b8-102">&lt;sessionSecurityTokenCache&gt;</span><span class="sxs-lookup"><span data-stu-id="7d7b8-102">&lt;sessionSecurityTokenCache&gt;</span></span>
<span data-ttu-id="7d7b8-103">Rejestruje pamięci podręcznej sesji tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7d7b8-103">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="7d7b8-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="7d7b8-104">\<system.identityModel></span></span>  
<span data-ttu-id="7d7b8-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="7d7b8-105">\<identityConfiguration></span></span>  
<span data-ttu-id="7d7b8-106">\<buforuje ></span><span class="sxs-lookup"><span data-stu-id="7d7b8-106">\<caches></span></span>  
<span data-ttu-id="7d7b8-107">\<sessionSecurityTokenCache ></span><span class="sxs-lookup"><span data-stu-id="7d7b8-107">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d7b8-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d7b8-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d7b8-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7d7b8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7d7b8-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7d7b8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d7b8-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d7b8-111">Attributes</span></span>  
  
|<span data-ttu-id="7d7b8-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7d7b8-112">Attribute</span></span>|<span data-ttu-id="7d7b8-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7d7b8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d7b8-114">— typ</span><span class="sxs-lookup"><span data-stu-id="7d7b8-114">type</span></span>|<span data-ttu-id="7d7b8-115">Typ, który pochodzi z <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="7d7b8-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d7b8-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d7b8-116">Child Elements</span></span>  
 <span data-ttu-id="7d7b8-117">Brak</span><span class="sxs-lookup"><span data-stu-id="7d7b8-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d7b8-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d7b8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7d7b8-119">Element</span><span class="sxs-lookup"><span data-stu-id="7d7b8-119">Element</span></span>|<span data-ttu-id="7d7b8-120">Opis</span><span class="sxs-lookup"><span data-stu-id="7d7b8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d7b8-121">\<buforuje ></span><span class="sxs-lookup"><span data-stu-id="7d7b8-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="7d7b8-122">Rejestruje pamięci podręcznych, używany przez usługę lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7d7b8-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7d7b8-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d7b8-123">Example</span></span>  
 <span data-ttu-id="7d7b8-124">Następujący kod XML przedstawia konfigurację pamięci podręcznej niestandardowy do przechowywania sesji tokenów zabezpieczających (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="7d7b8-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="7d7b8-125">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="7d7b8-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="7d7b8-126">Aby uzyskać więcej informacji dotyczących tego przykładu, zobacz [indeksu przykładowy kod WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="7d7b8-126">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d7b8-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d7b8-127">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
