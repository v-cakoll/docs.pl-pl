---
title: <defaultFtpCachePolicy>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 36d174beea58ff96674bd873bfbcb8be89591669
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674561"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="5c6cf-102">\<defaultFtpCachePolicy> Element (Network Settings)</span><span class="sxs-lookup"><span data-stu-id="5c6cf-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="5c6cf-103">Opisuje, czy buforowanie FTP jest aktywny i w tym artykule opisano domyślne zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="5c6cf-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="5c6cf-104">\<configuration></span></span>  
<span data-ttu-id="5c6cf-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="5c6cf-105">\<system.net></span></span>  
<span data-ttu-id="5c6cf-106">\<requestCaching></span><span class="sxs-lookup"><span data-stu-id="5c6cf-106">\<requestCaching></span></span>  
<span data-ttu-id="5c6cf-107">\<defaultFtpCachePolicy></span><span class="sxs-lookup"><span data-stu-id="5c6cf-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c6cf-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c6cf-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c6cf-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5c6cf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5c6cf-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c6cf-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5c6cf-111">Attributes</span></span>  
  
|<span data-ttu-id="5c6cf-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5c6cf-112">Attribute</span></span>|<span data-ttu-id="5c6cf-113">Opis</span><span class="sxs-lookup"><span data-stu-id="5c6cf-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="5c6cf-114">Określa, FTP, zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="5c6cf-115">Wartość domyślna to `Default`.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="5c6cf-116">policyLevel atrybutu</span><span class="sxs-lookup"><span data-stu-id="5c6cf-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="5c6cf-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="5c6cf-117">Value</span></span>|<span data-ttu-id="5c6cf-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5c6cf-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="5c6cf-119">Zwraca buforowane zasobu, jeśli zasób jest świeże, długość zawartości jest dokładne i wygaśnięcia, modyfikowanie i atrybuty długość zawartości znajdują się.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="5c6cf-120">Zwraca zasobu z serwera.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="5c6cf-121">Zwraca buforowane zasobu, jeśli długość zawartości jest obecna, a także odpowiada rozmiarowi wpisu.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="5c6cf-122">Zwraca buforowane zasobu, jeśli długość zawartości jest dostarczany i odpowiada rozmiarowi wejścia; w przeciwnym razie zasób zostanie pobrana z serwera i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="5c6cf-123">Zwraca buforowane zasobu, jeśli sygnatury czasowej zasobów pamięci podręcznej jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób jest pobierane z serwera, przechowywane w pamięci podręcznej i zwracany do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="5c6cf-124">Pobiera zasób z serwera, jest on przechowywany w pamięci podręcznej i zwraca zasobu do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="5c6cf-125">Jeśli istnieje zasób pamięci podręcznej, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="5c6cf-126">Zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="5c6cf-127">Spełnia żądanie przy użyciu pamięci podręcznej kopię zasobu, jeśli sygnatura czasowa jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób jest pobierane z serwera, przedstawione do obiektu wywołującego i przechowywane w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c6cf-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5c6cf-128">Child Elements</span></span>  
 <span data-ttu-id="5c6cf-129">Brak.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c6cf-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5c6cf-130">Parent Elements</span></span>  
  
|<span data-ttu-id="5c6cf-131">Element</span><span class="sxs-lookup"><span data-stu-id="5c6cf-131">Element</span></span>|<span data-ttu-id="5c6cf-132">Opis</span><span class="sxs-lookup"><span data-stu-id="5c6cf-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c6cf-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="5c6cf-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="5c6cf-134">Określa mechanizm buforowania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c6cf-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c6cf-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c6cf-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c6cf-136">Example</span></span>  
 <span data-ttu-id="5c6cf-137">Poniższy przykład pokazuje, jak określić zasady buforowania FTP `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="5c6cf-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5c6cf-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c6cf-138">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="5c6cf-139">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="5c6cf-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
