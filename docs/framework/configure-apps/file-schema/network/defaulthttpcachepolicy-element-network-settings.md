---
title: <defaultHttpCachePolicy>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
ms.openlocfilehash: c5029a7d1e53c28d0abb232efdc3e0bd2c9658d4
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088419"
---
# <a name="defaulthttpcachepolicy-element-network-settings"></a><span data-ttu-id="1b846-102">\<element > defaultHttpCachePolicy (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="1b846-102">\<defaultHttpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="1b846-103">Opisuje, czy buforowanie HTTP jest aktywne i opisuje domyślne zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="1b846-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  

<span data-ttu-id="1b846-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1b846-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1b846-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1b846-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="1b846-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<requestCaching >** ](requestcaching-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1b846-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)</span></span>\
<span data-ttu-id="1b846-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultHttpCachePolicy >**</span><span class="sxs-lookup"><span data-stu-id="1b846-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultHttpCachePolicy>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1b846-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b846-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b846-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1b846-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1b846-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1b846-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b846-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1b846-111">Attributes</span></span>  
  
|<span data-ttu-id="1b846-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1b846-112">Attribute</span></span>|<span data-ttu-id="1b846-113">Opis</span><span class="sxs-lookup"><span data-stu-id="1b846-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="1b846-114">Określa maksymalny przedział czasu, po którym obiekt w pamięci podręcznej zostanie oznaczony jako wygasły.</span><span class="sxs-lookup"><span data-stu-id="1b846-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="1b846-115">Określa maksymalny czas poprzedzający obliczony czas Aktualności przed oznaczeniem obiektu w pamięci podręcznej jako wygasły.</span><span class="sxs-lookup"><span data-stu-id="1b846-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="1b846-116">Określa minimalny czas do uwzględnienia w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="1b846-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="1b846-117">Określa, czy zasady buforowania są wykonywane automatycznie, czy pamięć podręczna jest pomijana.</span><span class="sxs-lookup"><span data-stu-id="1b846-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="1b846-118">Wartość domyślna to `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="1b846-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b846-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1b846-119">Child Elements</span></span>  
 <span data-ttu-id="1b846-120">Brak</span><span class="sxs-lookup"><span data-stu-id="1b846-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1b846-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1b846-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1b846-122">Element</span><span class="sxs-lookup"><span data-stu-id="1b846-122">Element</span></span>|<span data-ttu-id="1b846-123">Opis</span><span class="sxs-lookup"><span data-stu-id="1b846-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b846-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="1b846-124">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="1b846-125">Kontroluje mechanizm buforowania dla żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="1b846-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b846-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b846-126">Remarks</span></span>  
 <span data-ttu-id="1b846-127">Wartość atrybutu `policyLevel` jest `BypassCache` lub `Default`.</span><span class="sxs-lookup"><span data-stu-id="1b846-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="1b846-128">Wartości dla elementów `maximumAge`, `maximumStale`i `minimumFresh` są jawnym przedziałem czasu o formacie *d*. *hh*:*mm*:*SS* (dni, godziny, minuty i sekundy) albo stałe `minValue` lub `maxValue`, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="1b846-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1b846-129">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1b846-129">Configuration Files</span></span>  
 <span data-ttu-id="1b846-130">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="1b846-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b846-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b846-131">Example</span></span>  
 <span data-ttu-id="1b846-132">Poniższy przykład pokazuje, jak określić minimalny czas trwania sześciu godzin, maksymalny czas trwania okresu ważności wynoszący dwa dni i maksymalny czas nieodświeżony wynoszący 4 godziny.</span><span class="sxs-lookup"><span data-stu-id="1b846-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b846-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b846-133">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="1b846-134">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="1b846-134">Network Settings Schema</span></span>](index.md)
