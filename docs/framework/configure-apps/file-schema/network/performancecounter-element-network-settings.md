---
title: <performanceCounter> — Element (Ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 4603a942788d31a049196fb699d07a13551fa443
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279763"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="cce60-102">\<performanceCounter >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="cce60-102">\<performanceCounter> Element (Network Settings)</span></span>
<span data-ttu-id="cce60-103">Włącza lub wyłącza liczniki wydajności funkcji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="cce60-103">Enables or disables networking performance counters.</span></span>  
  
 <span data-ttu-id="cce60-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="cce60-104">\<configuration></span></span>  
<span data-ttu-id="cce60-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="cce60-105">\<system.net></span></span>  
<span data-ttu-id="cce60-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="cce60-106">\<settings></span></span>  
<span data-ttu-id="cce60-107">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="cce60-107">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cce60-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="cce60-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cce60-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cce60-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cce60-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cce60-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cce60-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cce60-111">Attributes</span></span>  
  
|<span data-ttu-id="cce60-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cce60-112">Attribute</span></span>|<span data-ttu-id="cce60-113">Opis</span><span class="sxs-lookup"><span data-stu-id="cce60-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="cce60-114">Określa, czy są włączone liczniki wydajności funkcji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="cce60-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="cce60-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="cce60-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cce60-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cce60-116">Child Elements</span></span>  
 <span data-ttu-id="cce60-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="cce60-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cce60-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cce60-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cce60-119">Element</span><span class="sxs-lookup"><span data-stu-id="cce60-119">Element</span></span>|<span data-ttu-id="cce60-120">Opis</span><span class="sxs-lookup"><span data-stu-id="cce60-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cce60-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="cce60-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="cce60-122">Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cce60-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cce60-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cce60-123">Remarks</span></span>  
 <span data-ttu-id="cce60-124">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="cce60-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="cce60-125">Liczniki wydajności sieci muszą być włączone w pliku konfiguracji do użycia.</span><span class="sxs-lookup"><span data-stu-id="cce60-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="cce60-126">Wszystkie liczniki wydajności funkcji sieciowych są włączone lub wyłączone przy użyciu pojedynczego ustawienia w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cce60-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="cce60-127">Poszczególne liczniki wydajności funkcji sieciowych nie może być włączona lub wyłączona.</span><span class="sxs-lookup"><span data-stu-id="cce60-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="cce60-128">Aby uzyskać więcej informacji na temat określonych liczniki wydajności funkcji sieciowych, zobacz [liczniki wydajności funkcji sieciowych](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking).</span><span class="sxs-lookup"><span data-stu-id="cce60-128">For more information on the specific networking performance counters, see [Networking Performance Counters](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking).</span></span>  
  
 <span data-ttu-id="cce60-129">Wartość domyślna to tego wydajność sieci, które liczniki są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="cce60-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="cce60-130"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> Właściwość może służyć do uzyskania bieżącej wartości **włączone** atrybut z właściwych plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cce60-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cce60-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="cce60-131">Example</span></span>  
 <span data-ttu-id="cce60-132">Poniższy przykład przedstawia sposób konfigurowania <xref:System.Net> i pokrewnych przestrzeniach nazw, aby włączyć liczniki wydajności funkcji sieciowych.</span><span class="sxs-lookup"><span data-stu-id="cce60-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cce60-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cce60-133">See also</span></span>
- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="cce60-134">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="cce60-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="cce60-135">Liczniki wydajności funkcji sieciowych</span><span class="sxs-lookup"><span data-stu-id="cce60-135">Networking Performance Counters</span></span>](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking)
