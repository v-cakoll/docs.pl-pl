---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: e949b16f76f20191b84bbbbb6e8b019d913316f0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251830"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="3e187-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="3e187-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="3e187-102">Rejestruje pamięć podręczną tokenów sesji za pomocą usługi lub kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="3e187-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="3e187-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3e187-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3e187-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="3e187-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="3e187-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="3e187-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="3e187-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<pamięć podręczna >** ](caches.md)</span><span class="sxs-lookup"><span data-stu-id="3e187-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="3e187-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sessionSecurityTokenCache >**</span><span class="sxs-lookup"><span data-stu-id="3e187-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e187-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e187-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e187-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3e187-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3e187-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3e187-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e187-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3e187-111">Attributes</span></span>  
  
|<span data-ttu-id="3e187-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3e187-112">Attribute</span></span>|<span data-ttu-id="3e187-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3e187-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e187-114">— typ</span><span class="sxs-lookup"><span data-stu-id="3e187-114">type</span></span>|<span data-ttu-id="3e187-115">Typ, który pochodzi od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="3e187-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e187-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3e187-116">Child Elements</span></span>  
 <span data-ttu-id="3e187-117">Brak</span><span class="sxs-lookup"><span data-stu-id="3e187-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e187-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3e187-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3e187-119">Element</span><span class="sxs-lookup"><span data-stu-id="3e187-119">Element</span></span>|<span data-ttu-id="3e187-120">Opis</span><span class="sxs-lookup"><span data-stu-id="3e187-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e187-121">\<pamięć podręczna ></span><span class="sxs-lookup"><span data-stu-id="3e187-121">\<caches></span></span>](caches.md)|<span data-ttu-id="3e187-122">Rejestruje pamięci podręczne używane przez usługę lub kolekcję programu obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="3e187-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3e187-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e187-123">Example</span></span>  
 <span data-ttu-id="3e187-124">W poniższym kodzie XML przedstawiono konfigurację niestandardowej pamięci podręcznej dla tokenów zabezpieczających<xref:System.IdentityModel.Tokens.SessionSecurityToken>sesji ().</span><span class="sxs-lookup"><span data-stu-id="3e187-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="3e187-125">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` przykładu.</span><span class="sxs-lookup"><span data-stu-id="3e187-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="3e187-126">Aby uzyskać więcej informacji na temat tego przykładu, zobacz [indeks przykładowego kodu WIF](../../../security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="3e187-126">For more information about this sample, see [WIF Code Sample Index](../../../security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e187-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e187-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
