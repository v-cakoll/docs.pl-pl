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
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028108"
---
# <a name="ltdefaulthttpcachepolicygt-element-network-settings"></a><span data-ttu-id="c17b4-102">&lt;defaulthttpcachepolicy —&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="c17b4-102">&lt;defaultHttpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="c17b4-103">Opisuje, czy buforowanie HTTP jest aktywny i w tym artykule opisano domyślne zasady buforowania.</span><span class="sxs-lookup"><span data-stu-id="c17b4-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="c17b4-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="c17b4-104">\<configuration></span></span>  
<span data-ttu-id="c17b4-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="c17b4-105">\<system.net></span></span>  
<span data-ttu-id="c17b4-106">\<requestCaching — ></span><span class="sxs-lookup"><span data-stu-id="c17b4-106">\<requestCaching></span></span>  
<span data-ttu-id="c17b4-107">\<defaulthttpcachepolicy — ></span><span class="sxs-lookup"><span data-stu-id="c17b4-107">\<defaultHttpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c17b4-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c17b4-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c17b4-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c17b4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c17b4-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c17b4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c17b4-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c17b4-111">Attributes</span></span>  
  
|<span data-ttu-id="c17b4-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c17b4-112">Attribute</span></span>|<span data-ttu-id="c17b4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c17b4-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="c17b4-114">Określa maksymalny czas, zanim obiektu w pamięci podręcznej, jest ona oznaczona jako wygasła.</span><span class="sxs-lookup"><span data-stu-id="c17b4-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="c17b4-115">Określa maksymalny czas późniejsza niż godzina świeżości obliczaną przed obiektu w pamięci podręcznej, jest ona oznaczona jako wygasła.</span><span class="sxs-lookup"><span data-stu-id="c17b4-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="c17b4-116">Określa minimalny czas dla obiektu w pamięci podręcznej do być traktowany jako świeży.</span><span class="sxs-lookup"><span data-stu-id="c17b4-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="c17b4-117">Określa, czy zasady buforowania jest automatycznie, czy pomijana jest pamięć podręczna.</span><span class="sxs-lookup"><span data-stu-id="c17b4-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="c17b4-118">Wartość domyślna to `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="c17b4-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c17b4-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c17b4-119">Child Elements</span></span>  
 <span data-ttu-id="c17b4-120">Brak</span><span class="sxs-lookup"><span data-stu-id="c17b4-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c17b4-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c17b4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c17b4-122">Element</span><span class="sxs-lookup"><span data-stu-id="c17b4-122">Element</span></span>|<span data-ttu-id="c17b4-123">Opis</span><span class="sxs-lookup"><span data-stu-id="c17b4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c17b4-124">requestCaching —</span><span class="sxs-lookup"><span data-stu-id="c17b4-124">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="c17b4-125">Określa mechanizm buforowania żądań sieci.</span><span class="sxs-lookup"><span data-stu-id="c17b4-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c17b4-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c17b4-126">Remarks</span></span>  
 <span data-ttu-id="c17b4-127">Wartość `policyLevel` atrybut ma wartość `BypassCache` lub `Default`.</span><span class="sxs-lookup"><span data-stu-id="c17b4-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="c17b4-128">Wartości `maximumAge`, `maximumStale`, i `minimumFresh` elementy są albo jawne przedział czasu mający godziny formatu *d*. *hh*:*mm*:*ss* (dni, godziny, minuty i sekundy), lub stałe `minValue` lub `maxValue`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c17b4-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c17b4-129">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c17b4-129">Configuration Files</span></span>  
 <span data-ttu-id="c17b4-130">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c17b4-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c17b4-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="c17b4-131">Example</span></span>  
 <span data-ttu-id="c17b4-132">Poniższy przykład pokazuje, jak określić minimalny czas od nowa, sześć godzin przez czas maksymalny wiek dwóch dni i maksymalny czas stałe wynoszące cztery godziny.</span><span class="sxs-lookup"><span data-stu-id="c17b4-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c17b4-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c17b4-133">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="c17b4-134">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="c17b4-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
