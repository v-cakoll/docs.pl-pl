---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 5c68fe618f965f364a3716c3bc65de5e165b12ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207802"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="f1ca0-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="f1ca0-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="f1ca0-102">Rejestruje pamięci podręcznej dla sesji tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="f1ca0-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f1ca0-103">\<system.identityModel></span></span>  
<span data-ttu-id="f1ca0-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f1ca0-104">\<identityConfiguration></span></span>  
<span data-ttu-id="f1ca0-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="f1ca0-105">\<caches></span></span>  
<span data-ttu-id="f1ca0-106">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="f1ca0-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1ca0-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1ca0-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1ca0-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f1ca0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f1ca0-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1ca0-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f1ca0-110">Attributes</span></span>  
  
|<span data-ttu-id="f1ca0-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f1ca0-111">Attribute</span></span>|<span data-ttu-id="f1ca0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f1ca0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1ca0-113">— typ</span><span class="sxs-lookup"><span data-stu-id="f1ca0-113">type</span></span>|<span data-ttu-id="f1ca0-114">Typ, który pochodzi od klasy <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1ca0-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f1ca0-115">Child Elements</span></span>  
 <span data-ttu-id="f1ca0-116">Brak</span><span class="sxs-lookup"><span data-stu-id="f1ca0-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1ca0-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f1ca0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f1ca0-118">Element</span><span class="sxs-lookup"><span data-stu-id="f1ca0-118">Element</span></span>|<span data-ttu-id="f1ca0-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f1ca0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1ca0-120">\<caches></span><span class="sxs-lookup"><span data-stu-id="f1ca0-120">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="f1ca0-121">Rejestruje pamięci podręcznych, używane przez usługę lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f1ca0-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1ca0-122">Example</span></span>  
 <span data-ttu-id="f1ca0-123">Następujący kody XML pokazuje konfiguracji niestandardowej pamięci podręcznej do przechowywania tokenów zabezpieczających sesji (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="f1ca0-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="f1ca0-124">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="f1ca0-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="f1ca0-125">Aby uzyskać więcej informacji na temat tego przykładu, zobacz [Indeks przykładów kodu programu WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="f1ca0-125">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1ca0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1ca0-126">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
