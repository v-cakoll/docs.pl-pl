---
title: "&lt;defaulthttpcachepolicy —&gt; — Element (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f2db2fd10ca20209c21c8add71d8ee4f26951ca6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltdefaulthttpcachepolicygt-element-network-settings"></a><span data-ttu-id="d256c-102">&lt;defaulthttpcachepolicy —&gt; — Element (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="d256c-102">&lt;defaultHttpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="d256c-103">Opisuje, czy buforowanie HTTP jest aktywna i opisano domyślne zasad buforowania.</span><span class="sxs-lookup"><span data-stu-id="d256c-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="d256c-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="d256c-104">\<configuration></span></span>  
<span data-ttu-id="d256c-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="d256c-105">\<system.net></span></span>  
<span data-ttu-id="d256c-106">\<requestCaching — ></span><span class="sxs-lookup"><span data-stu-id="d256c-106">\<requestCaching></span></span>  
<span data-ttu-id="d256c-107">\<defaulthttpcachepolicy — ></span><span class="sxs-lookup"><span data-stu-id="d256c-107">\<defaultHttpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d256c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d256c-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d256c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d256c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d256c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d256c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d256c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d256c-111">Attributes</span></span>  
  
|<span data-ttu-id="d256c-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d256c-112">Attribute</span></span>|<span data-ttu-id="d256c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d256c-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="d256c-114">Określa maksymalny czas, przed obiektu w pamięci podręcznej jest oznaczona jako wygasła.</span><span class="sxs-lookup"><span data-stu-id="d256c-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="d256c-115">Określa maksymalny czas późniejsza niż godzina świeżości obliczaną przed obiektu w pamięci podręcznej jest oznaczona jako wygasła.</span><span class="sxs-lookup"><span data-stu-id="d256c-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="d256c-116">Określa minimalny czas wziąć pod uwagę nowego obiektu w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d256c-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="d256c-117">Określa, czy zasad buforowania odbywa się automatycznie, czy pomijana jest pamięć podręczna.</span><span class="sxs-lookup"><span data-stu-id="d256c-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="d256c-118">Wartość domyślna to `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="d256c-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d256c-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d256c-119">Child Elements</span></span>  
 <span data-ttu-id="d256c-120">Brak</span><span class="sxs-lookup"><span data-stu-id="d256c-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d256c-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d256c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d256c-122">Element</span><span class="sxs-lookup"><span data-stu-id="d256c-122">Element</span></span>|<span data-ttu-id="d256c-123">Opis</span><span class="sxs-lookup"><span data-stu-id="d256c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d256c-124">requestCaching —</span><span class="sxs-lookup"><span data-stu-id="d256c-124">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="d256c-125">Określa mechanizm buforowania żądań sieciowych.</span><span class="sxs-lookup"><span data-stu-id="d256c-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d256c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d256c-126">Remarks</span></span>  
 <span data-ttu-id="d256c-127">Wartość `policyLevel` jest atrybut `BypassCache` lub `Default`.</span><span class="sxs-lookup"><span data-stu-id="d256c-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="d256c-128">Wartości `maximumAge`, `maximumStale`, i `minimumFresh` elementy są albo jawne interwał w formacie *d*. *hh*:*mm*:*ss* (dni, godziny, minuty i sekundy), lub stałe `minValue` lub `maxValue`, gdzie to właściwe.</span><span class="sxs-lookup"><span data-stu-id="d256c-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d256c-129">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d256c-129">Configuration Files</span></span>  
 <span data-ttu-id="d256c-130">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d256c-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d256c-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="d256c-131">Example</span></span>  
 <span data-ttu-id="d256c-132">Poniższy przykład pokazuje, jak określić minimalny czas świeże sześć godzin przez czas maksymalny wiek dwa dni, a maksymalny czas starych czterech godzin.</span><span class="sxs-lookup"><span data-stu-id="d256c-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d256c-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d256c-133">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="d256c-134">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="d256c-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
