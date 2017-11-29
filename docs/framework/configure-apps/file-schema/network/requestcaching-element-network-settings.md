---
title: "&lt;requestCaching —&gt; — Element (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f2737e67fe1fe1e33b2600f448b02321f6ce1888
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltrequestcachinggt-element-network-settings"></a><span data-ttu-id="ef775-102">&lt;requestCaching —&gt; — Element (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="ef775-102">&lt;requestCaching&gt; Element (Network Settings)</span></span>
<span data-ttu-id="ef775-103">Określa mechanizm buforowania żądań sieciowych.</span><span class="sxs-lookup"><span data-stu-id="ef775-103">Controls the caching mechanism for network requests.</span></span>  
  
 <span data-ttu-id="ef775-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="ef775-104">\<configuration></span></span>  
<span data-ttu-id="ef775-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="ef775-105">\<system.net></span></span>  
<span data-ttu-id="ef775-106">\<requestCaching — ></span><span class="sxs-lookup"><span data-stu-id="ef775-106">\<requestCaching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef775-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef775-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef775-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ef775-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ef775-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ef775-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef775-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ef775-110">Attributes</span></span>  
  
|<span data-ttu-id="ef775-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ef775-111">Attribute</span></span>|<span data-ttu-id="ef775-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ef775-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="ef775-113">Określa, czy pamięć podręczna zapewnia izolację między informacjami zawartymi w różnych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="ef775-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="ef775-114">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="ef775-114">The default value is `true`.</span></span> <span data-ttu-id="ef775-115">Ta wartość powinna być `false` dla aplikacji warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="ef775-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="ef775-116">Określa, czy buforowanie jest wyłączone dla wszystkich odpowiedzi z sieci Web i nie można zastąpić programowo.</span><span class="sxs-lookup"><span data-stu-id="ef775-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="ef775-117">Jedna z wartości w <xref:System.Net.Cache.RequestCacheLevel> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ef775-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="ef775-118">Wartość domyślna to `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="ef775-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="ef775-119">Określa domyślny czas, po którym zawartość jest oznaczona jako wygasła.</span><span class="sxs-lookup"><span data-stu-id="ef775-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="ef775-120">PolicyLevel, który atrybutu</span><span class="sxs-lookup"><span data-stu-id="ef775-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="ef775-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="ef775-121">Value</span></span>|<span data-ttu-id="ef775-122">Opis</span><span class="sxs-lookup"><span data-stu-id="ef775-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="ef775-123">Zwraca buforowane zasobu, jeśli zasób jest nowa, długość zawartości jest dokładna i wygaśnięcia, modyfikowanie i atrybuty długość zawartości znajdują się.</span><span class="sxs-lookup"><span data-stu-id="ef775-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="ef775-124">Zwraca zasobu z serwera.</span><span class="sxs-lookup"><span data-stu-id="ef775-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="ef775-125">Zwraca buforowane zasobu, jeśli długość zawartości jest obecny i dopasowuje rozmiar wpisu.</span><span class="sxs-lookup"><span data-stu-id="ef775-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="ef775-126">Zwraca buforowane zasobów, jeśli zostanie podana długość zawartości dopasowuje rozmiar wpisu; w przeciwnym razie zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ef775-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="ef775-127">Zwraca buforowane zasobu, jeśli sygnatury czasowej buforowanych zasobów jest taka sama jak sygnatury czasowej zasobu na serwerze; w przeciwnym razie zasób jest pobierane z serwera, przechowywane w pamięci podręcznej i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ef775-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="ef775-128">Pobiera zasób z serwera, jest on przechowywany w pamięci podręcznej i zwraca zasobu do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ef775-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="ef775-129">Jeśli istnieje zasób pamięci podręcznej, jest ono usunięte.</span><span class="sxs-lookup"><span data-stu-id="ef775-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="ef775-130">Zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ef775-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="ef775-131">Spełnia żądania przy użyciu pamięci podręcznej kopię zasobu, jeśli sygnatury czasowej jest taka sama jak sygnatury czasowej zasobu na serwerze; w przeciwnym razie zasób jest pobierane z serwera, przedstawione do obiektu wywołującego i są przechowywane w pamięci podręcznej,</span><span class="sxs-lookup"><span data-stu-id="ef775-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef775-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ef775-132">Child Elements</span></span>  
  
|<span data-ttu-id="ef775-133">Element</span><span class="sxs-lookup"><span data-stu-id="ef775-133">Element</span></span>|<span data-ttu-id="ef775-134">Opis</span><span class="sxs-lookup"><span data-stu-id="ef775-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef775-135">defaulthttpcachepolicy —</span><span class="sxs-lookup"><span data-stu-id="ef775-135">defaultHttpCachePolicy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="ef775-136">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ef775-136">Optional element.</span></span><br /><br /> <span data-ttu-id="ef775-137">Opisuje, czy buforowanie HTTP jest aktywna i opisano domyślne zasad buforowania.</span><span class="sxs-lookup"><span data-stu-id="ef775-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="ef775-138">\<defaultftpcachepolicy — > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="ef775-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="ef775-139">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ef775-139">Optional element.</span></span><br /><br /> <span data-ttu-id="ef775-140">Opisuje, czy buforowanie FTP jest aktywna i opisano domyślne zasad buforowania.</span><span class="sxs-lookup"><span data-stu-id="ef775-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ef775-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ef775-141">Parent Elements</span></span>  
  
|<span data-ttu-id="ef775-142">Element</span><span class="sxs-lookup"><span data-stu-id="ef775-142">Element</span></span>|<span data-ttu-id="ef775-143">Opis</span><span class="sxs-lookup"><span data-stu-id="ef775-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef775-144">System.NET</span><span class="sxs-lookup"><span data-stu-id="ef775-144">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="ef775-145">Zawiera ustawienia, które określają sposób programu .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="ef775-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ef775-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef775-146">Example</span></span>  
 <span data-ttu-id="ef775-147">Poniższy przykład przedstawia sposób wyłączania buforowaniu.</span><span class="sxs-lookup"><span data-stu-id="ef775-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef775-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef775-148">See Also</span></span>  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [<span data-ttu-id="ef775-149">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="ef775-149">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
