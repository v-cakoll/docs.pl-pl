---
title: "&lt;defaultftpcachepolicy —&gt; — Element (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0c62be73db6d9d0b6ce67dd87021c589502d5fec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a><span data-ttu-id="7ad75-102">&lt;defaultftpcachepolicy —&gt; — Element (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="7ad75-102">&lt;defaultFtpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="7ad75-103">Opisuje, czy buforowanie FTP jest aktywna i opisano domyślne zasad buforowania.</span><span class="sxs-lookup"><span data-stu-id="7ad75-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="7ad75-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="7ad75-104">\<configuration></span></span>  
<span data-ttu-id="7ad75-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="7ad75-105">\<system.net></span></span>  
<span data-ttu-id="7ad75-106">\<requestCaching — ></span><span class="sxs-lookup"><span data-stu-id="7ad75-106">\<requestCaching></span></span>  
<span data-ttu-id="7ad75-107">\<defaultftpcachepolicy — ></span><span class="sxs-lookup"><span data-stu-id="7ad75-107">\<defaultFtpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ad75-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ad75-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ad75-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7ad75-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7ad75-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7ad75-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ad75-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7ad75-111">Attributes</span></span>  
  
|<span data-ttu-id="7ad75-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7ad75-112">Attribute</span></span>|<span data-ttu-id="7ad75-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7ad75-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="7ad75-114">Określa FTP zasad buforowania.</span><span class="sxs-lookup"><span data-stu-id="7ad75-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="7ad75-115">Wartość domyślna to `Default`.</span><span class="sxs-lookup"><span data-stu-id="7ad75-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="7ad75-116">PolicyLevel, który atrybutu</span><span class="sxs-lookup"><span data-stu-id="7ad75-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="7ad75-117">Wartość</span><span class="sxs-lookup"><span data-stu-id="7ad75-117">Value</span></span>|<span data-ttu-id="7ad75-118">Opis</span><span class="sxs-lookup"><span data-stu-id="7ad75-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="7ad75-119">Zwraca buforowane zasobu, jeśli zasób jest nowa, długość zawartości jest dokładna i wygaśnięcia, modyfikowanie i atrybuty długość zawartości znajdują się.</span><span class="sxs-lookup"><span data-stu-id="7ad75-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="7ad75-120">Zwraca zasobu z serwera.</span><span class="sxs-lookup"><span data-stu-id="7ad75-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="7ad75-121">Zwraca buforowane zasobu, jeśli długość zawartości jest obecny i dopasowuje rozmiar wpisu.</span><span class="sxs-lookup"><span data-stu-id="7ad75-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="7ad75-122">Zwraca buforowane zasobów, jeśli zostanie podana długość zawartości dopasowuje rozmiar wpisu; w przeciwnym razie zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7ad75-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="7ad75-123">Zwraca buforowane zasobu, jeśli sygnatury czasowej buforowanych zasobów jest taka sama jak sygnatury czasowej zasobu na serwerze; w przeciwnym razie wartość zasób jest pobierany z serwera, przechowywane w pamięci podręcznej i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7ad75-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="7ad75-124">Pobiera zasób z serwera, jest on przechowywany w pamięci podręcznej i zwraca zasobu do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7ad75-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="7ad75-125">Jeśli istnieje zasób pamięci podręcznej, jest ono usunięte.</span><span class="sxs-lookup"><span data-stu-id="7ad75-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="7ad75-126">Zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7ad75-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="7ad75-127">Spełnia żądania przy użyciu pamięci podręcznej kopię zasobu, jeśli sygnatury czasowej jest taka sama jak sygnatury czasowej zasobu na serwerze; w przeciwnym razie zasób jest pobrane z serwera, przedstawione do obiektu wywołującego i przechowywane w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="7ad75-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ad75-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7ad75-128">Child Elements</span></span>  
 <span data-ttu-id="7ad75-129">Brak.</span><span class="sxs-lookup"><span data-stu-id="7ad75-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ad75-130">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7ad75-130">Parent Elements</span></span>  
  
|<span data-ttu-id="7ad75-131">Element</span><span class="sxs-lookup"><span data-stu-id="7ad75-131">Element</span></span>|<span data-ttu-id="7ad75-132">Opis</span><span class="sxs-lookup"><span data-stu-id="7ad75-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ad75-133">requestCaching —</span><span class="sxs-lookup"><span data-stu-id="7ad75-133">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="7ad75-134">Określa mechanizm buforowania żądań sieciowych.</span><span class="sxs-lookup"><span data-stu-id="7ad75-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ad75-135">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ad75-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ad75-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="7ad75-136">Example</span></span>  
 <span data-ttu-id="7ad75-137">Poniższy przykład przedstawia sposób określić FTP buforowanie zasady `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="7ad75-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7ad75-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ad75-138">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="7ad75-139">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="7ad75-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
