---
title: '&lt;requestCaching —&gt; — Element (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9c0c8d80182931f9ac14e687a337b7be55a5a9a5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltrequestcachinggt-element-network-settings"></a><span data-ttu-id="4523b-102">&lt;requestCaching —&gt; — Element (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="4523b-102">&lt;requestCaching&gt; Element (Network Settings)</span></span>
<span data-ttu-id="4523b-103">Określa mechanizm buforowania żądań sieciowych.</span><span class="sxs-lookup"><span data-stu-id="4523b-103">Controls the caching mechanism for network requests.</span></span>  
  
 <span data-ttu-id="4523b-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="4523b-104">\<configuration></span></span>  
<span data-ttu-id="4523b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4523b-105">\<system.net></span></span>  
<span data-ttu-id="4523b-106">\<requestCaching — ></span><span class="sxs-lookup"><span data-stu-id="4523b-106">\<requestCaching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4523b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4523b-107">Syntax</span></span>  
  
```xml  
      <requestCaching>  
        isPrivateCache ="true|false"  
        disableAllCaching="true|false"  
        defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
        unspecifiedMaximumAge= "d.hh.mm.ss">  
          <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
          <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
      </requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4523b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4523b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4523b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4523b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4523b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4523b-110">Attributes</span></span>  
  
|<span data-ttu-id="4523b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4523b-111">Attribute</span></span>|<span data-ttu-id="4523b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4523b-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="4523b-113">Określa, czy pamięć podręczna zapewnia izolację między informacjami zawartymi w różnych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="4523b-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="4523b-114">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="4523b-114">The default value is `true`.</span></span> <span data-ttu-id="4523b-115">Ta wartość powinna być `false` dla aplikacji warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="4523b-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="4523b-116">Określa, czy buforowanie jest wyłączone dla wszystkich odpowiedzi z sieci Web i nie można zastąpić programowo.</span><span class="sxs-lookup"><span data-stu-id="4523b-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="4523b-117">Jedna z wartości w <xref:System.Net.Cache.RequestCacheLevel> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4523b-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="4523b-118">Wartość domyślna to `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="4523b-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="4523b-119">Określa domyślny czas, po którym zawartość jest oznaczona jako wygasła.</span><span class="sxs-lookup"><span data-stu-id="4523b-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="4523b-120">PolicyLevel, który atrybutu</span><span class="sxs-lookup"><span data-stu-id="4523b-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="4523b-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="4523b-121">Value</span></span>|<span data-ttu-id="4523b-122">Opis</span><span class="sxs-lookup"><span data-stu-id="4523b-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="4523b-123">Zwraca buforowane zasobu, jeśli zasób jest nowa, długość zawartości jest dokładna i wygaśnięcia, modyfikowanie i atrybuty długość zawartości znajdują się.</span><span class="sxs-lookup"><span data-stu-id="4523b-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="4523b-124">Zwraca zasobu z serwera.</span><span class="sxs-lookup"><span data-stu-id="4523b-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="4523b-125">Zwraca buforowane zasobu, jeśli długość zawartości jest obecny i dopasowuje rozmiar wpisu.</span><span class="sxs-lookup"><span data-stu-id="4523b-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="4523b-126">Zwraca buforowane zasobów, jeśli zostanie podana długość zawartości dopasowuje rozmiar wpisu; w przeciwnym razie zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4523b-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="4523b-127">Zwraca buforowane zasobu, jeśli sygnatury czasowej buforowanych zasobów jest taka sama jak sygnatury czasowej zasobu na serwerze; w przeciwnym razie zasób jest pobierane z serwera, przechowywane w pamięci podręcznej i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4523b-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="4523b-128">Pobiera zasób z serwera, jest on przechowywany w pamięci podręcznej i zwraca zasobu do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4523b-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="4523b-129">Jeśli istnieje zasób pamięci podręcznej, jest ono usunięte.</span><span class="sxs-lookup"><span data-stu-id="4523b-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="4523b-130">Zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4523b-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="4523b-131">Spełnia żądania przy użyciu pamięci podręcznej kopię zasobu, jeśli sygnatury czasowej jest taka sama jak sygnatury czasowej zasobu na serwerze; w przeciwnym razie zasób jest pobierane z serwera, przedstawione do obiektu wywołującego i są przechowywane w pamięci podręcznej,</span><span class="sxs-lookup"><span data-stu-id="4523b-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4523b-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4523b-132">Child Elements</span></span>  
  
|<span data-ttu-id="4523b-133">Element</span><span class="sxs-lookup"><span data-stu-id="4523b-133">Element</span></span>|<span data-ttu-id="4523b-134">Opis</span><span class="sxs-lookup"><span data-stu-id="4523b-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4523b-135">defaulthttpcachepolicy —</span><span class="sxs-lookup"><span data-stu-id="4523b-135">defaultHttpCachePolicy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="4523b-136">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4523b-136">Optional element.</span></span><br /><br /> <span data-ttu-id="4523b-137">Opisuje, czy buforowanie HTTP jest aktywna i opisano domyślne zasad buforowania.</span><span class="sxs-lookup"><span data-stu-id="4523b-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="4523b-138">\<defaultftpcachepolicy — > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="4523b-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="4523b-139">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4523b-139">Optional element.</span></span><br /><br /> <span data-ttu-id="4523b-140">Opisuje, czy buforowanie FTP jest aktywna i opisano domyślne zasad buforowania.</span><span class="sxs-lookup"><span data-stu-id="4523b-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4523b-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4523b-141">Parent Elements</span></span>  
  
|<span data-ttu-id="4523b-142">Element</span><span class="sxs-lookup"><span data-stu-id="4523b-142">Element</span></span>|<span data-ttu-id="4523b-143">Opis</span><span class="sxs-lookup"><span data-stu-id="4523b-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4523b-144">System.NET</span><span class="sxs-lookup"><span data-stu-id="4523b-144">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="4523b-145">Zawiera ustawienia, które określają sposób programu .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="4523b-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4523b-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="4523b-146">Example</span></span>  
 <span data-ttu-id="4523b-147">Poniższy przykład przedstawia sposób wyłączania buforowaniu.</span><span class="sxs-lookup"><span data-stu-id="4523b-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4523b-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4523b-148">See Also</span></span>  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [<span data-ttu-id="4523b-149">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="4523b-149">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
