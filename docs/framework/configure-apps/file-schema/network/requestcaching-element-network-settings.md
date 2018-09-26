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
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083192"
---
# <a name="ltrequestcachinggt-element-network-settings"></a><span data-ttu-id="3dfc9-102">&lt;requestCaching —&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="3dfc9-102">&lt;requestCaching&gt; Element (Network Settings)</span></span>
<span data-ttu-id="3dfc9-103">Określa mechanizm buforowania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-103">Controls the caching mechanism for network requests.</span></span>  
  
 <span data-ttu-id="3dfc9-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="3dfc9-104">\<configuration></span></span>  
<span data-ttu-id="3dfc9-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="3dfc9-105">\<system.net></span></span>  
<span data-ttu-id="3dfc9-106">\<requestCaching — ></span><span class="sxs-lookup"><span data-stu-id="3dfc9-106">\<requestCaching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dfc9-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3dfc9-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3dfc9-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3dfc9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3dfc9-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3dfc9-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3dfc9-110">Attributes</span></span>  
  
|<span data-ttu-id="3dfc9-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3dfc9-111">Attribute</span></span>|<span data-ttu-id="3dfc9-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3dfc9-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="3dfc9-113">Określa, czy pamięć podręczna zapewnia izolację między informacji o różnych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="3dfc9-114">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-114">The default value is `true`.</span></span> <span data-ttu-id="3dfc9-115">Ta wartość powinna być `false` dla aplikacji warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="3dfc9-116">Określa, że buforowanie jest wyłączone dla wszystkich odpowiedzi z sieci Web i nie może być zastąpiona programowo.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="3dfc9-117">Jedna z wartości w <xref:System.Net.Cache.RequestCacheLevel> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="3dfc9-118">Wartość domyślna to `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="3dfc9-119">Określa domyślny czas, po którym zawartość jest oznaczona jako wygasła.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="3dfc9-120">policyLevel atrybutu</span><span class="sxs-lookup"><span data-stu-id="3dfc9-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="3dfc9-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="3dfc9-121">Value</span></span>|<span data-ttu-id="3dfc9-122">Opis</span><span class="sxs-lookup"><span data-stu-id="3dfc9-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="3dfc9-123">Zwraca buforowane zasobu, jeśli zasób jest świeże, długość zawartości jest dokładne i wygaśnięcia, modyfikowanie i atrybuty długość zawartości znajdują się.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="3dfc9-124">Zwraca zasobu z serwera.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="3dfc9-125">Zwraca buforowane zasobu, jeśli długość zawartości jest obecna, a także odpowiada rozmiarowi wpisu.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="3dfc9-126">Zwraca buforowane zasobu, jeśli długość zawartości jest dostarczany i odpowiada rozmiarowi wejścia; w przeciwnym razie zasób zostanie pobrana z serwera i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="3dfc9-127">Zwraca buforowane zasobu, jeśli sygnatury czasowej zasobów pamięci podręcznej jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób zostanie pobrana z serwera, przechowywane w pamięci podręcznej i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="3dfc9-128">Pobiera zasób z serwera, jest on przechowywany w pamięci podręcznej i zwraca zasobu do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="3dfc9-129">Jeśli istnieje zasób pamięci podręcznej, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="3dfc9-130">Zasób jest pobierane z serwera i jest zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="3dfc9-131">Spełnia żądanie przy użyciu pamięci podręcznej kopię zasobu, jeśli sygnatura czasowa jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób zostanie pobrana z serwera, przedstawione do obiektu wywołującego i jest przechowywany w pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="3dfc9-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3dfc9-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3dfc9-132">Child Elements</span></span>  
  
|<span data-ttu-id="3dfc9-133">Element</span><span class="sxs-lookup"><span data-stu-id="3dfc9-133">Element</span></span>|<span data-ttu-id="3dfc9-134">Opis</span><span class="sxs-lookup"><span data-stu-id="3dfc9-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3dfc9-135">defaulthttpcachepolicy —</span><span class="sxs-lookup"><span data-stu-id="3dfc9-135">defaultHttpCachePolicy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="3dfc9-136">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-136">Optional element.</span></span><br /><br /> <span data-ttu-id="3dfc9-137">Opisuje, czy buforowanie HTTP jest aktywny i w tym artykule opisano domyślne zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="3dfc9-138">\<defaultftpcachepolicy — >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="3dfc9-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="3dfc9-139">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-139">Optional element.</span></span><br /><br /> <span data-ttu-id="3dfc9-140">Opisuje, czy buforowanie FTP jest aktywny i w tym artykule opisano domyślne zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3dfc9-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3dfc9-141">Parent Elements</span></span>  
  
|<span data-ttu-id="3dfc9-142">Element</span><span class="sxs-lookup"><span data-stu-id="3dfc9-142">Element</span></span>|<span data-ttu-id="3dfc9-143">Opis</span><span class="sxs-lookup"><span data-stu-id="3dfc9-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3dfc9-144">przestrzeni nazw System.NET</span><span class="sxs-lookup"><span data-stu-id="3dfc9-144">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="3dfc9-145">Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3dfc9-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="3dfc9-146">Example</span></span>  
 <span data-ttu-id="3dfc9-147">Poniższy przykład pokazuje, jak wyłączyć buforowaniu.</span><span class="sxs-lookup"><span data-stu-id="3dfc9-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3dfc9-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3dfc9-148">See Also</span></span>  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [<span data-ttu-id="3dfc9-149">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="3dfc9-149">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
