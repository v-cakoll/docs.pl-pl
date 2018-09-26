---
title: '&lt;defaulthttpcachepolicy —&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1e1b27cb8c0df4450c1a08151af19913b65fc2b3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47172927"
---
# <a name="ltdefaulthttpcachepolicygt-element-network-settings"></a><span data-ttu-id="4728b-102">&lt;defaulthttpcachepolicy —&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="4728b-102">&lt;defaultHttpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="4728b-103">Opisuje, czy buforowanie HTTP jest aktywny i w tym artykule opisano domyślne zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="4728b-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="4728b-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="4728b-104">\<configuration></span></span>  
<span data-ttu-id="4728b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4728b-105">\<system.net></span></span>  
<span data-ttu-id="4728b-106">\<requestCaching — ></span><span class="sxs-lookup"><span data-stu-id="4728b-106">\<requestCaching></span></span>  
<span data-ttu-id="4728b-107">\<defaulthttpcachepolicy — ></span><span class="sxs-lookup"><span data-stu-id="4728b-107">\<defaultHttpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4728b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="4728b-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4728b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4728b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4728b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4728b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4728b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4728b-111">Attributes</span></span>  
  
|<span data-ttu-id="4728b-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4728b-112">Attribute</span></span>|<span data-ttu-id="4728b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4728b-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="4728b-114">Określa maksymalny czas, zanim obiektu w pamięci podręcznej, jest ona oznaczona jako wygasła.</span><span class="sxs-lookup"><span data-stu-id="4728b-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="4728b-115">Określa maksymalny czas późniejsza niż godzina świeżości obliczaną przed obiektu w pamięci podręcznej, jest ona oznaczona jako wygasła.</span><span class="sxs-lookup"><span data-stu-id="4728b-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="4728b-116">Określa minimalny czas dla obiektu w pamięci podręcznej do być traktowany jako świeży.</span><span class="sxs-lookup"><span data-stu-id="4728b-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="4728b-117">Określa, czy zasady buforowania jest automatycznie, czy pomijana jest pamięć podręczna.</span><span class="sxs-lookup"><span data-stu-id="4728b-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="4728b-118">Wartość domyślna to `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="4728b-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4728b-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4728b-119">Child Elements</span></span>  
 <span data-ttu-id="4728b-120">Brak</span><span class="sxs-lookup"><span data-stu-id="4728b-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4728b-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4728b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4728b-122">Element</span><span class="sxs-lookup"><span data-stu-id="4728b-122">Element</span></span>|<span data-ttu-id="4728b-123">Opis</span><span class="sxs-lookup"><span data-stu-id="4728b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4728b-124">requestCaching —</span><span class="sxs-lookup"><span data-stu-id="4728b-124">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="4728b-125">Określa mechanizm buforowania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="4728b-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4728b-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4728b-126">Remarks</span></span>  
 <span data-ttu-id="4728b-127">Wartość `policyLevel` atrybut ma wartość `BypassCache` lub `Default`.</span><span class="sxs-lookup"><span data-stu-id="4728b-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="4728b-128">Wartości `maximumAge`, `maximumStale`, i `minimumFresh` elementy są albo jawne przedział czasu mający godziny formatu *d*. *hh*:*mm*:*ss* (dni, godziny, minuty i sekundy), lub stałe `minValue` lub `maxValue`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="4728b-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4728b-129">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4728b-129">Configuration Files</span></span>  
 <span data-ttu-id="4728b-130">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="4728b-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4728b-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="4728b-131">Example</span></span>  
 <span data-ttu-id="4728b-132">Poniższy przykład pokazuje, jak określić minimalny czas od nowa, sześć godzin przez czas maksymalny wiek dwóch dni i maksymalny czas stałe wynoszące cztery godziny.</span><span class="sxs-lookup"><span data-stu-id="4728b-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4728b-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4728b-133">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="4728b-134">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="4728b-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
