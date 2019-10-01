---
title: <requestCaching>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: f0979d2e0caeb0b22b90572aef0ad53235020f1d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697823"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="aeaa7-102">\<requestCaching >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="aeaa7-102">\<requestCaching> Element (Network Settings)</span></span>
<span data-ttu-id="aeaa7-103">Kontroluje mechanizm buforowania dla żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-103">Controls the caching mechanism for network requests.</span></span>  
  
[<span data-ttu-id="aeaa7-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="aeaa7-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="aeaa7-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="aeaa7-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="aeaa7-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<requestCaching >**</span><span class="sxs-lookup"><span data-stu-id="aeaa7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeaa7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="aeaa7-107">Syntax</span></span>  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh.mm.ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aeaa7-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aeaa7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="aeaa7-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aeaa7-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aeaa7-110">Attributes</span></span>  
  
|<span data-ttu-id="aeaa7-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="aeaa7-111">Attribute</span></span>|<span data-ttu-id="aeaa7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="aeaa7-112">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="aeaa7-113">Określa, czy pamięć podręczna zapewnia izolację między informacjami różnych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-113">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="aeaa7-114">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-114">The default value is `true`.</span></span> <span data-ttu-id="aeaa7-115">Ta wartość powinna być `false` dla aplikacji warstwy środkowej.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-115">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="aeaa7-116">Określa, że buforowanie jest wyłączone dla wszystkich odpowiedzi sieci Web i nie może zostać przesłonięte programowo.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-116">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="aeaa7-117">Jedna z wartości w wyliczeniu <xref:System.Net.Cache.RequestCacheLevel>.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-117">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="aeaa7-118">Wartość domyślna to `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-118">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="aeaa7-119">Określa domyślny czas, po którym zawartość jest oznaczona jako wygasła.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-119">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="aeaa7-120">policyLevel — atrybut</span><span class="sxs-lookup"><span data-stu-id="aeaa7-120">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="aeaa7-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="aeaa7-121">Value</span></span>|<span data-ttu-id="aeaa7-122">Opis</span><span class="sxs-lookup"><span data-stu-id="aeaa7-122">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="aeaa7-123">Zwraca buforowany zasób, jeśli zasób jest świeży, długość zawartości jest dokładna i atrybuty daty wygaśnięcia, modyfikacji i długości zawartości są obecne.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-123">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="aeaa7-124">Zwraca zasób z serwera.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-124">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="aeaa7-125">Zwraca buforowany zasób, jeśli długość zawartości jest obecna i jest zgodna z rozmiarem wpisu.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-125">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="aeaa7-126">Zwraca buforowany zasób, jeśli długość zawartości jest podana i jest zgodna z rozmiarem wpisu; w przeciwnym razie zasób jest pobierany z serwera i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-126">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="aeaa7-127">Zwraca buforowany zasób, jeśli sygnatura czasowa zasobu w pamięci podręcznej jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób jest pobierany z serwera, przechowywany w pamięci podręcznej i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-127">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="aeaa7-128">Pobiera zasób z serwera, zapisuje go w pamięci podręcznej i zwraca zasób do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-128">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="aeaa7-129">Jeśli istnieje zasób w pamięci podręcznej, zostanie on usunięty.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-129">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="aeaa7-130">Zasób jest pobierany z serwera i zwracany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-130">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="aeaa7-131">Program spełnia żądanie przy użyciu buforowanej kopii zasobu, jeśli sygnatura czasowa jest taka sama jak sygnatura czasowa zasobu na serwerze; w przeciwnym razie zasób zostanie pobrany z serwera, który jest prezentowany obiektowi wywołującemu, i jest przechowywany w pamięci podręcznej,</span><span class="sxs-lookup"><span data-stu-id="aeaa7-131">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aeaa7-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aeaa7-132">Child Elements</span></span>  
  
|<span data-ttu-id="aeaa7-133">Element</span><span class="sxs-lookup"><span data-stu-id="aeaa7-133">Element</span></span>|<span data-ttu-id="aeaa7-134">Opis</span><span class="sxs-lookup"><span data-stu-id="aeaa7-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aeaa7-135">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="aeaa7-135">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="aeaa7-136">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-136">Optional element.</span></span><br /><br /> <span data-ttu-id="aeaa7-137">Opisuje, czy buforowanie HTTP jest aktywne i opisuje domyślne zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-137">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="aeaa7-138">\<defaultFtpCachePolicy >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="aeaa7-138">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="aeaa7-139">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-139">Optional element.</span></span><br /><br /> <span data-ttu-id="aeaa7-140">Opisuje, czy buforowanie FTP jest aktywne i opisuje domyślne zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-140">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aeaa7-141">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aeaa7-141">Parent Elements</span></span>  
  
|<span data-ttu-id="aeaa7-142">Element</span><span class="sxs-lookup"><span data-stu-id="aeaa7-142">Element</span></span>|<span data-ttu-id="aeaa7-143">Opis</span><span class="sxs-lookup"><span data-stu-id="aeaa7-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aeaa7-144">system.net</span><span class="sxs-lookup"><span data-stu-id="aeaa7-144">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="aeaa7-145">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-145">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aeaa7-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="aeaa7-146">Example</span></span>  
 <span data-ttu-id="aeaa7-147">Poniższy przykład pokazuje, jak wyłączyć wszystkie buforowanie.</span><span class="sxs-lookup"><span data-stu-id="aeaa7-147">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aeaa7-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aeaa7-148">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="aeaa7-149">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="aeaa7-149">Network Settings Schema</span></span>](index.md)
