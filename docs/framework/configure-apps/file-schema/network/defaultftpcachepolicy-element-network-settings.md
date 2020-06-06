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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088426"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="278e6-102">\<defaultFtpCachePolicy>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="278e6-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="278e6-103">Opisuje, czy buforowanie FTP jest aktywne i opisuje domyślne zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="278e6-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="278e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="278e6-104">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="278e6-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="278e6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="278e6-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="278e6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="278e6-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="278e6-107">Attributes</span></span>  
  
|<span data-ttu-id="278e6-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="278e6-108">Attribute</span></span>|<span data-ttu-id="278e6-109">Opis</span><span class="sxs-lookup"><span data-stu-id="278e6-109">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="278e6-110">Określa zasady buforowania FTP.</span><span class="sxs-lookup"><span data-stu-id="278e6-110">Specifies the FTP caching policy.</span></span> <span data-ttu-id="278e6-111">Wartość domyślna to `Default`.</span><span class="sxs-lookup"><span data-stu-id="278e6-111">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="278e6-112">policyLevel — atrybut</span><span class="sxs-lookup"><span data-stu-id="278e6-112">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="278e6-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="278e6-113">Value</span></span>|<span data-ttu-id="278e6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="278e6-114">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="278e6-115">Zwraca buforowany zasób, jeśli zasób jest świeży, długość zawartości jest dokładna i atrybuty daty wygaśnięcia, modyfikacji i długości zawartości są obecne.</span><span class="sxs-lookup"><span data-stu-id="278e6-115">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="278e6-116">Zwraca zasób z serwera.</span><span class="sxs-lookup"><span data-stu-id="278e6-116">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="278e6-117">Zwraca buforowany zasób, jeśli długość zawartości jest obecna i jest zgodna z rozmiarem wpisu.</span><span class="sxs-lookup"><span data-stu-id="278e6-117">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="278e6-118">Zwraca buforowany zasób, jeśli długość zawartości jest podana i jest zgodna z rozmiarem wpisu; w przeciwnym razie zasób jest pobierany z serwera i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="278e6-118">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="278e6-119">Zwraca buforowany zasób, jeśli sygnatura czasowa zasobu w pamięci podręcznej jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób zostanie pobrany z serwera, zapisany w pamięci podręcznej i zwrócony do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="278e6-119">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="278e6-120">Pobiera zasób z serwera, zapisuje go w pamięci podręcznej i zwraca zasób do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="278e6-120">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="278e6-121">Jeśli istnieje zasób w pamięci podręcznej, zostanie on usunięty.</span><span class="sxs-lookup"><span data-stu-id="278e6-121">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="278e6-122">Zasób jest pobierany z serwera i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="278e6-122">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="278e6-123">Program spełnia żądanie przy użyciu buforowanej kopii zasobu, jeśli sygnatura czasowa jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób zostanie pobrany z serwera, który jest przedstawiony dla obiektu wywołującego i zapisany w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="278e6-123">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="278e6-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="278e6-124">Child Elements</span></span>  
 <span data-ttu-id="278e6-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="278e6-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="278e6-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="278e6-126">Parent Elements</span></span>  
  
|<span data-ttu-id="278e6-127">Element</span><span class="sxs-lookup"><span data-stu-id="278e6-127">Element</span></span>|<span data-ttu-id="278e6-128">Opis</span><span class="sxs-lookup"><span data-stu-id="278e6-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="278e6-129">requestCaching</span><span class="sxs-lookup"><span data-stu-id="278e6-129">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="278e6-130">Kontroluje mechanizm buforowania dla żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="278e6-130">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="278e6-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="278e6-131">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="278e6-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="278e6-132">Example</span></span>  
 <span data-ttu-id="278e6-133">Poniższy przykład pokazuje, jak określić zasady buforowania FTP `NoCacheNoStore` .</span><span class="sxs-lookup"><span data-stu-id="278e6-133">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="278e6-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="278e6-134">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="278e6-135">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="278e6-135">Network Settings Schema</span></span>](index.md)
