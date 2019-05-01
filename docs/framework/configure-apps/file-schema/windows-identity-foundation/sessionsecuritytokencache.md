---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 5c68fe618f965f364a3716c3bc65de5e165b12ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793799"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="c835e-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="c835e-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="c835e-102">Rejestruje pamięci podręcznej dla sesji tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c835e-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="c835e-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="c835e-103">\<system.identityModel></span></span>  
<span data-ttu-id="c835e-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c835e-104">\<identityConfiguration></span></span>  
<span data-ttu-id="c835e-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="c835e-105">\<caches></span></span>  
<span data-ttu-id="c835e-106">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="c835e-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c835e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c835e-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c835e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c835e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c835e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c835e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c835e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c835e-110">Attributes</span></span>  
  
|<span data-ttu-id="c835e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c835e-111">Attribute</span></span>|<span data-ttu-id="c835e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c835e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c835e-113">— typ</span><span class="sxs-lookup"><span data-stu-id="c835e-113">type</span></span>|<span data-ttu-id="c835e-114">Typ, który pochodzi od klasy <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="c835e-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c835e-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c835e-115">Child Elements</span></span>  
 <span data-ttu-id="c835e-116">Brak</span><span class="sxs-lookup"><span data-stu-id="c835e-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c835e-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c835e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c835e-118">Element</span><span class="sxs-lookup"><span data-stu-id="c835e-118">Element</span></span>|<span data-ttu-id="c835e-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c835e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c835e-120">\<caches></span><span class="sxs-lookup"><span data-stu-id="c835e-120">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="c835e-121">Rejestruje pamięci podręcznych, używane przez usługę lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c835e-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c835e-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="c835e-122">Example</span></span>  
 <span data-ttu-id="c835e-123">Następujący kody XML pokazuje konfiguracji niestandardowej pamięci podręcznej do przechowywania tokenów zabezpieczających sesji (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span><span class="sxs-lookup"><span data-stu-id="c835e-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="c835e-124">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="c835e-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="c835e-125">Aby uzyskać więcej informacji na temat tego przykładu, zobacz [Indeks przykładów kodu programu WIF](../../../../../docs/framework/security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="c835e-125">For more information about this sample, see [WIF Code Sample Index](../../../../../docs/framework/security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c835e-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c835e-126">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
