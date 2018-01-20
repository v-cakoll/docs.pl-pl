---
title: '&lt;performanceCounter&gt; elementu (ustawienia sieciowe)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c50bf9e882ade86e70db217a75fef2a893c45572
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltperformancecountergt-element-network-settings"></a><span data-ttu-id="148b9-102">&lt;performanceCounter&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="148b9-102">&lt;performanceCounter&gt; Element (Network Settings)</span></span>
<span data-ttu-id="148b9-103">Włącza lub wyłącza liczniki wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="148b9-103">Enables or disables networking performance counters.</span></span>  
  
 <span data-ttu-id="148b9-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="148b9-104">\<configuration></span></span>  
<span data-ttu-id="148b9-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="148b9-105">\<system.net></span></span>  
<span data-ttu-id="148b9-106">\<Ustawienia ></span><span class="sxs-lookup"><span data-stu-id="148b9-106">\<settings></span></span>  
<span data-ttu-id="148b9-107">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="148b9-107">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="148b9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="148b9-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="148b9-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="148b9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="148b9-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="148b9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="148b9-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="148b9-111">Attributes</span></span>  
  
|<span data-ttu-id="148b9-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="148b9-112">Attribute</span></span>|<span data-ttu-id="148b9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="148b9-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="148b9-114">Określa, czy są włączone liczniki wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="148b9-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="148b9-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="148b9-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="148b9-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="148b9-116">Child Elements</span></span>  
 <span data-ttu-id="148b9-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="148b9-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="148b9-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="148b9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="148b9-119">Element</span><span class="sxs-lookup"><span data-stu-id="148b9-119">Element</span></span>|<span data-ttu-id="148b9-120">Opis</span><span class="sxs-lookup"><span data-stu-id="148b9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="148b9-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="148b9-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="148b9-122">Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="148b9-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="148b9-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="148b9-123">Remarks</span></span>  
 <span data-ttu-id="148b9-124">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="148b9-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="148b9-125">Liczniki wydajności sieci muszą być włączone w pliku konfiguracji do użycia.</span><span class="sxs-lookup"><span data-stu-id="148b9-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="148b9-126">Wszystkie sieci liczniki wydajności są włączone lub wyłączone przy użyciu jednego ustawienia w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="148b9-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="148b9-127">Poszczególne sieci liczniki wydajności nie może być włączona lub wyłączona.</span><span class="sxs-lookup"><span data-stu-id="148b9-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="148b9-128">Aby uzyskać więcej informacji na określonej sieci liczniki wydajności, zobacz [sieci liczniki wydajności](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd).</span><span class="sxs-lookup"><span data-stu-id="148b9-128">For more information on the specific networking performance counters, see [Networking Performance Counters](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd).</span></span>  
  
 <span data-ttu-id="148b9-129">Wartość domyślna to, że wydajność sieci, które liczniki są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="148b9-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="148b9-130"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> Właściwości można pobrać wartości bieżącego **włączone** atrybutu z plików zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="148b9-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="148b9-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="148b9-131">Example</span></span>  
 <span data-ttu-id="148b9-132">Poniższy przykład przedstawia sposób konfigurowania <xref:System.Net> i związanych z przestrzeni nazw, aby włączyć liczniki wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="148b9-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="148b9-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="148b9-133">See Also</span></span>  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="148b9-134">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="148b9-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="148b9-135">Liczniki wydajności sieci</span><span class="sxs-lookup"><span data-stu-id="148b9-135">Networking Performance Counters</span></span>](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd)
