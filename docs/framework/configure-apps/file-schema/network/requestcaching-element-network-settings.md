---
title: '&lt;requestCaching —&gt; — Element (ustawienia sieci)'
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
ms.openlocfilehash: 3e014c7a47a53a424bbaef51c9acb28e59b43078
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47401306"
---
# <a name="ltrequestcachinggt-element-network-settings"></a><span data-ttu-id="25646-102">&lt;requestCaching —&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="25646-102">&lt;requestCaching&gt; Element (Network Settings)</span></span>
<span data-ttu-id="25646-103">Określa mechanizm buforowania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="25646-103">Controls the caching mechanism for network requests.</span></span>  
  
 <span data-ttu-id="25646-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="25646-104">\<configuration></span></span>  
<span data-ttu-id="25646-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="25646-105">\<system.net></span></span>  
<span data-ttu-id="25646-106">\<requestCaching — ></span><span class="sxs-lookup"><span data-stu-id="25646-106">\<requestCaching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25646-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="25646-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25646-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="25646-108">Attributes and Elements</span></span>  
 <span data-ttu-id="25646-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="25646-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25646-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="25646-110">Attributes</span></span>  
  
|<span data-ttu-id="25646-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="25646-111">Attribute</span></span>|<span data-ttu-id="25646-112">Opis</span><span class="sxs-lookup"><span data-stu-id="25646-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="25646-113">Określa, czy pamięć podręczna zapewnia izolację między informacji o różnych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="25646-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="25646-114">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="25646-114">The default value is `true`.</span></span> <span data-ttu-id="25646-115">Ta wartość powinna być `false` dla aplikacji warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="25646-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="25646-116">Określa, że buforowanie jest wyłączone dla wszystkich odpowiedzi z sieci Web i nie może być zastąpiona programowo.</span><span class="sxs-lookup"><span data-stu-id="25646-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="25646-117">Jedna z wartości w <xref:System.Net.Cache.RequestCacheLevel> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="25646-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="25646-118">Wartość domyślna to `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="25646-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="25646-119">Określa domyślny czas, po którym zawartość jest oznaczona jako wygasła.</span><span class="sxs-lookup"><span data-stu-id="25646-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="25646-120">policyLevel atrybutu</span><span class="sxs-lookup"><span data-stu-id="25646-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="25646-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="25646-121">Value</span></span>|<span data-ttu-id="25646-122">Opis</span><span class="sxs-lookup"><span data-stu-id="25646-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="25646-123">Zwraca buforowane zasobu, jeśli zasób jest świeże, długość zawartości jest dokładne i wygaśnięcia, modyfikowanie i atrybuty długość zawartości znajdują się.</span><span class="sxs-lookup"><span data-stu-id="25646-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="25646-124">Zwraca zasobu z serwera.</span><span class="sxs-lookup"><span data-stu-id="25646-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="25646-125">Zwraca buforowane zasobu, jeśli długość zawartości jest obecna, a także odpowiada rozmiarowi wpisu.</span><span class="sxs-lookup"><span data-stu-id="25646-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="25646-126">Zwraca buforowane zasobu, jeśli długość zawartości jest dostarczany i odpowiada rozmiarowi wejścia; w przeciwnym razie zasób zostanie pobrana z serwera i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="25646-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="25646-127">Zwraca buforowane zasobu, jeśli sygnatury czasowej zasobów pamięci podręcznej jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób zostanie pobrana z serwera, przechowywane w pamięci podręcznej i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="25646-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="25646-128">Pobiera zasób z serwera, jest on przechowywany w pamięci podręcznej i zwraca zasobu do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="25646-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="25646-129">Jeśli istnieje zasób pamięci podręcznej, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="25646-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="25646-130">Zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="25646-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="25646-131">Spełnia żądanie przy użyciu pamięci podręcznej kopię zasobu, jeśli sygnatura czasowa jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób zostanie pobrana z serwera, przedstawione do obiektu wywołującego i jest przechowywany w pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="25646-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25646-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="25646-132">Child Elements</span></span>  
  
|<span data-ttu-id="25646-133">Element</span><span class="sxs-lookup"><span data-stu-id="25646-133">Element</span></span>|<span data-ttu-id="25646-134">Opis</span><span class="sxs-lookup"><span data-stu-id="25646-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25646-135">defaulthttpcachepolicy —</span><span class="sxs-lookup"><span data-stu-id="25646-135">defaultHttpCachePolicy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="25646-136">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="25646-136">Optional element.</span></span><br /><br /> <span data-ttu-id="25646-137">Opisuje, czy buforowanie HTTP jest aktywny i w tym artykule opisano domyślne zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="25646-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="25646-138">\<defaultftpcachepolicy — >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="25646-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="25646-139">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="25646-139">Optional element.</span></span><br /><br /> <span data-ttu-id="25646-140">Opisuje, czy buforowanie FTP jest aktywny i w tym artykule opisano domyślne zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="25646-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25646-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="25646-141">Parent Elements</span></span>  
  
|<span data-ttu-id="25646-142">Element</span><span class="sxs-lookup"><span data-stu-id="25646-142">Element</span></span>|<span data-ttu-id="25646-143">Opis</span><span class="sxs-lookup"><span data-stu-id="25646-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25646-144">przestrzeni nazw System.NET</span><span class="sxs-lookup"><span data-stu-id="25646-144">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="25646-145">Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="25646-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="25646-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="25646-146">Example</span></span>  
 <span data-ttu-id="25646-147">Poniższy przykład pokazuje, jak wyłączyć buforowaniu.</span><span class="sxs-lookup"><span data-stu-id="25646-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="25646-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25646-148">See Also</span></span>  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [<span data-ttu-id="25646-149">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="25646-149">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
