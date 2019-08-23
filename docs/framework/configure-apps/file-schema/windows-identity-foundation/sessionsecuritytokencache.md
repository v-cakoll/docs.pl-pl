---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 9be3bf980c3756678d26d8652271113d4daaba43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943710"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="24af9-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="24af9-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="24af9-102">Rejestruje pamięć podręczną tokenów sesji za pomocą usługi lub kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="24af9-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="24af9-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="24af9-103">\<system.identityModel></span></span>  
<span data-ttu-id="24af9-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="24af9-104">\<identityConfiguration></span></span>  
<span data-ttu-id="24af9-105">\<pamięć podręczna ></span><span class="sxs-lookup"><span data-stu-id="24af9-105">\<caches></span></span>  
<span data-ttu-id="24af9-106">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="24af9-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24af9-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="24af9-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24af9-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="24af9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="24af9-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="24af9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24af9-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="24af9-110">Attributes</span></span>  
  
|<span data-ttu-id="24af9-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="24af9-111">Attribute</span></span>|<span data-ttu-id="24af9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="24af9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24af9-113">— typ</span><span class="sxs-lookup"><span data-stu-id="24af9-113">type</span></span>|<span data-ttu-id="24af9-114">Typ, który pochodzi od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="24af9-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24af9-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="24af9-115">Child Elements</span></span>  
 <span data-ttu-id="24af9-116">Brak</span><span class="sxs-lookup"><span data-stu-id="24af9-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24af9-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="24af9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="24af9-118">Element</span><span class="sxs-lookup"><span data-stu-id="24af9-118">Element</span></span>|<span data-ttu-id="24af9-119">Opis</span><span class="sxs-lookup"><span data-stu-id="24af9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24af9-120">\<pamięć podręczna ></span><span class="sxs-lookup"><span data-stu-id="24af9-120">\<caches></span></span>](caches.md)|<span data-ttu-id="24af9-121">Rejestruje pamięci podręczne używane przez usługę lub kolekcję programu obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="24af9-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="24af9-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="24af9-122">Example</span></span>  
 <span data-ttu-id="24af9-123">W poniższym kodzie XML przedstawiono konfigurację niestandardowej pamięci podręcznej dla tokenów zabezpieczających<xref:System.IdentityModel.Tokens.SessionSecurityToken>sesji ().</span><span class="sxs-lookup"><span data-stu-id="24af9-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="24af9-124">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` przykładu.</span><span class="sxs-lookup"><span data-stu-id="24af9-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="24af9-125">Aby uzyskać więcej informacji na temat tego przykładu, zobacz [indeks przykładowego kodu WIF](../../../security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="24af9-125">For more information about this sample, see [WIF Code Sample Index](../../../security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="24af9-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24af9-126">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
