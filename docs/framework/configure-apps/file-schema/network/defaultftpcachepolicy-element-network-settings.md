---
title: '&lt;defaultftpcachepolicy —&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e03fb02bd351058c1fcdedb8367d03318418a12c
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316444"
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a><span data-ttu-id="80776-102">&lt;defaultftpcachepolicy —&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="80776-102">&lt;defaultFtpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="80776-103">Opisuje, czy buforowanie FTP jest aktywny i w tym artykule opisano domyślne zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="80776-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="80776-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="80776-104">\<configuration></span></span>  
<span data-ttu-id="80776-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="80776-105">\<system.net></span></span>  
<span data-ttu-id="80776-106">\<requestCaching — ></span><span class="sxs-lookup"><span data-stu-id="80776-106">\<requestCaching></span></span>  
<span data-ttu-id="80776-107">\<defaultftpcachepolicy — ></span><span class="sxs-lookup"><span data-stu-id="80776-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80776-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="80776-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80776-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="80776-109">Attributes and Elements</span></span>  
 <span data-ttu-id="80776-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="80776-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80776-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="80776-111">Attributes</span></span>  
  
|<span data-ttu-id="80776-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="80776-112">Attribute</span></span>|<span data-ttu-id="80776-113">Opis</span><span class="sxs-lookup"><span data-stu-id="80776-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="80776-114">Określa, FTP, zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="80776-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="80776-115">Wartość domyślna to `Default`.</span><span class="sxs-lookup"><span data-stu-id="80776-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="80776-116">policyLevel atrybutu</span><span class="sxs-lookup"><span data-stu-id="80776-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="80776-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="80776-117">Value</span></span>|<span data-ttu-id="80776-118">Opis</span><span class="sxs-lookup"><span data-stu-id="80776-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="80776-119">Zwraca buforowane zasobu, jeśli zasób jest świeże, długość zawartości jest dokładne i wygaśnięcia, modyfikowanie i atrybuty długość zawartości znajdują się.</span><span class="sxs-lookup"><span data-stu-id="80776-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="80776-120">Zwraca zasobu z serwera.</span><span class="sxs-lookup"><span data-stu-id="80776-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="80776-121">Zwraca buforowane zasobu, jeśli długość zawartości jest obecna, a także odpowiada rozmiarowi wpisu.</span><span class="sxs-lookup"><span data-stu-id="80776-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="80776-122">Zwraca buforowane zasobu, jeśli długość zawartości jest dostarczany i odpowiada rozmiarowi wejścia; w przeciwnym razie zasób zostanie pobrana z serwera i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="80776-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="80776-123">Zwraca buforowane zasobu, jeśli sygnatury czasowej zasobów pamięci podręcznej jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób jest pobierane z serwera, przechowywane w pamięci podręcznej i zwracany do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="80776-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="80776-124">Pobiera zasób z serwera, jest on przechowywany w pamięci podręcznej i zwraca zasobu do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="80776-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="80776-125">Jeśli istnieje zasób pamięci podręcznej, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="80776-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="80776-126">Zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="80776-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="80776-127">Spełnia żądanie przy użyciu pamięci podręcznej kopię zasobu, jeśli sygnatura czasowa jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób jest pobierane z serwera, przedstawione do obiektu wywołującego i przechowywane w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="80776-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80776-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="80776-128">Child Elements</span></span>  
 <span data-ttu-id="80776-129">Brak.</span><span class="sxs-lookup"><span data-stu-id="80776-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80776-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="80776-130">Parent Elements</span></span>  
  
|<span data-ttu-id="80776-131">Element</span><span class="sxs-lookup"><span data-stu-id="80776-131">Element</span></span>|<span data-ttu-id="80776-132">Opis</span><span class="sxs-lookup"><span data-stu-id="80776-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80776-133">requestCaching —</span><span class="sxs-lookup"><span data-stu-id="80776-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="80776-134">Określa mechanizm buforowania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="80776-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80776-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80776-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="80776-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="80776-136">Example</span></span>  
 <span data-ttu-id="80776-137">Poniższy przykład pokazuje, jak określić zasady buforowania FTP `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="80776-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="80776-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80776-138">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="80776-139">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="80776-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
