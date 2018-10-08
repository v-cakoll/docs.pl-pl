---
title: '&lt;performanceCounter&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 259d8e0297025d496b3a10c3ef3ec2b3c96cffaa
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48849792"
---
# <a name="ltperformancecountergt-element-network-settings"></a><span data-ttu-id="22ca0-102">&lt;performanceCounter&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="22ca0-102">&lt;performanceCounter&gt; Element (Network Settings)</span></span>
<span data-ttu-id="22ca0-103">Włącza lub wyłącza liczniki wydajności funkcji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="22ca0-103">Enables or disables networking performance counters.</span></span>  
  
 <span data-ttu-id="22ca0-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="22ca0-104">\<configuration></span></span>  
<span data-ttu-id="22ca0-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="22ca0-105">\<system.net></span></span>  
<span data-ttu-id="22ca0-106">\<Ustawienia ></span><span class="sxs-lookup"><span data-stu-id="22ca0-106">\<settings></span></span>  
<span data-ttu-id="22ca0-107">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="22ca0-107">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22ca0-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="22ca0-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22ca0-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="22ca0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="22ca0-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="22ca0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22ca0-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="22ca0-111">Attributes</span></span>  
  
|<span data-ttu-id="22ca0-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="22ca0-112">Attribute</span></span>|<span data-ttu-id="22ca0-113">Opis</span><span class="sxs-lookup"><span data-stu-id="22ca0-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="22ca0-114">Określa, czy są włączone liczniki wydajności funkcji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="22ca0-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="22ca0-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="22ca0-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22ca0-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="22ca0-116">Child Elements</span></span>  
 <span data-ttu-id="22ca0-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="22ca0-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22ca0-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="22ca0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="22ca0-119">Element</span><span class="sxs-lookup"><span data-stu-id="22ca0-119">Element</span></span>|<span data-ttu-id="22ca0-120">Opis</span><span class="sxs-lookup"><span data-stu-id="22ca0-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22ca0-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="22ca0-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="22ca0-122">Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="22ca0-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22ca0-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22ca0-123">Remarks</span></span>  
 <span data-ttu-id="22ca0-124">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="22ca0-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="22ca0-125">Liczniki wydajności sieci muszą być włączone w pliku konfiguracji do użycia.</span><span class="sxs-lookup"><span data-stu-id="22ca0-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="22ca0-126">Wszystkie liczniki wydajności funkcji sieciowych są włączone lub wyłączone przy użyciu pojedynczego ustawienia w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="22ca0-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="22ca0-127">Poszczególne liczniki wydajności funkcji sieciowych nie może być włączona lub wyłączona.</span><span class="sxs-lookup"><span data-stu-id="22ca0-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="22ca0-128">Aby uzyskać więcej informacji na temat określonych liczniki wydajności funkcji sieciowych, zobacz [liczniki wydajności funkcji sieciowych](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking).</span><span class="sxs-lookup"><span data-stu-id="22ca0-128">For more information on the specific networking performance counters, see [Networking Performance Counters](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking).</span></span>  
  
 <span data-ttu-id="22ca0-129">Wartość domyślna to tego wydajność sieci, które liczniki są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="22ca0-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="22ca0-130"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> Właściwość może służyć do uzyskania bieżącej wartości **włączone** atrybut z właściwych plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="22ca0-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22ca0-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="22ca0-131">Example</span></span>  
 <span data-ttu-id="22ca0-132">Poniższy przykład przedstawia sposób konfigurowania <xref:System.Net> i pokrewnych przestrzeniach nazw, aby włączyć liczniki wydajności funkcji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="22ca0-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22ca0-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22ca0-133">See Also</span></span>  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="22ca0-134">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="22ca0-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="22ca0-135">Liczniki wydajności funkcji sieciowych</span><span class="sxs-lookup"><span data-stu-id="22ca0-135">Networking Performance Counters</span></span>](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking)
