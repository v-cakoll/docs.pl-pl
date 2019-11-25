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
ms.openlocfilehash: 9261a430642cb4d5ac4507835bd0fd3561bd8c02
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088426"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="a28dc-102">\<element > defaultFtpCachePolicy (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="a28dc-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="a28dc-103">Opisuje, czy buforowanie FTP jest aktywne i opisuje domyślne zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="a28dc-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

<span data-ttu-id="a28dc-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a28dc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a28dc-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a28dc-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="a28dc-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<requestCaching >** ](requestcaching-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a28dc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)</span></span>\
<span data-ttu-id="a28dc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultFtpCachePolicy >**</span><span class="sxs-lookup"><span data-stu-id="a28dc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a28dc-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="a28dc-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a28dc-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a28dc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a28dc-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a28dc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a28dc-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a28dc-111">Attributes</span></span>  
  
|<span data-ttu-id="a28dc-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a28dc-112">Attribute</span></span>|<span data-ttu-id="a28dc-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a28dc-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="a28dc-114">Określa zasady buforowania FTP.</span><span class="sxs-lookup"><span data-stu-id="a28dc-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="a28dc-115">Wartość domyślna to `Default`.</span><span class="sxs-lookup"><span data-stu-id="a28dc-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="a28dc-116">policyLevel — atrybut</span><span class="sxs-lookup"><span data-stu-id="a28dc-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="a28dc-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="a28dc-117">Value</span></span>|<span data-ttu-id="a28dc-118">Opis</span><span class="sxs-lookup"><span data-stu-id="a28dc-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="a28dc-119">Zwraca buforowany zasób, jeśli zasób jest świeży, długość zawartości jest dokładna i atrybuty daty wygaśnięcia, modyfikacji i długości zawartości są obecne.</span><span class="sxs-lookup"><span data-stu-id="a28dc-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="a28dc-120">Zwraca zasób z serwera.</span><span class="sxs-lookup"><span data-stu-id="a28dc-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="a28dc-121">Zwraca buforowany zasób, jeśli długość zawartości jest obecna i jest zgodna z rozmiarem wpisu.</span><span class="sxs-lookup"><span data-stu-id="a28dc-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="a28dc-122">Zwraca buforowany zasób, jeśli długość zawartości jest podana i jest zgodna z rozmiarem wpisu; w przeciwnym razie zasób jest pobierany z serwera i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a28dc-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="a28dc-123">Zwraca buforowany zasób, jeśli sygnatura czasowa zasobu w pamięci podręcznej jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób zostanie pobrany z serwera, zapisany w pamięci podręcznej i zwrócony do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a28dc-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="a28dc-124">Pobiera zasób z serwera, zapisuje go w pamięci podręcznej i zwraca zasób do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a28dc-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="a28dc-125">Jeśli istnieje zasób w pamięci podręcznej, zostanie on usunięty.</span><span class="sxs-lookup"><span data-stu-id="a28dc-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="a28dc-126">Zasób jest pobierany z serwera i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a28dc-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="a28dc-127">Program spełnia żądanie przy użyciu buforowanej kopii zasobu, jeśli sygnatura czasowa jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób zostanie pobrany z serwera, który jest przedstawiony dla obiektu wywołującego i zapisany w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a28dc-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a28dc-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a28dc-128">Child Elements</span></span>  
 <span data-ttu-id="a28dc-129">Brak.</span><span class="sxs-lookup"><span data-stu-id="a28dc-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a28dc-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a28dc-130">Parent Elements</span></span>  
  
|<span data-ttu-id="a28dc-131">Element</span><span class="sxs-lookup"><span data-stu-id="a28dc-131">Element</span></span>|<span data-ttu-id="a28dc-132">Opis</span><span class="sxs-lookup"><span data-stu-id="a28dc-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a28dc-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="a28dc-133">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="a28dc-134">Kontroluje mechanizm buforowania dla żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="a28dc-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a28dc-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a28dc-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="a28dc-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="a28dc-136">Example</span></span>  
 <span data-ttu-id="a28dc-137">Poniższy przykład pokazuje, jak określić zasady buforowania FTP `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="a28dc-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a28dc-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a28dc-138">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="a28dc-139">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="a28dc-139">Network Settings Schema</span></span>](index.md)
