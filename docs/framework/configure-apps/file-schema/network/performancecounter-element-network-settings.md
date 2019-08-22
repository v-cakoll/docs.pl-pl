---
title: <performanceCounter>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 05aac6c1ed3c04bce263a45cafdb9bec906bd75b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664061"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="42911-102">\<performanceCounter >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="42911-102">\<performanceCounter> Element (Network Settings)</span></span>
<span data-ttu-id="42911-103">Włącza lub wyłącza liczniki wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="42911-103">Enables or disables networking performance counters.</span></span>  
  
 <span data-ttu-id="42911-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="42911-104">\<configuration></span></span>  
<span data-ttu-id="42911-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="42911-105">\<system.net></span></span>  
<span data-ttu-id="42911-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="42911-106">\<settings></span></span>  
<span data-ttu-id="42911-107">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="42911-107">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42911-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="42911-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42911-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="42911-109">Attributes and Elements</span></span>  
 <span data-ttu-id="42911-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="42911-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42911-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="42911-111">Attributes</span></span>  
  
|<span data-ttu-id="42911-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="42911-112">Attribute</span></span>|<span data-ttu-id="42911-113">Opis</span><span class="sxs-lookup"><span data-stu-id="42911-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="42911-114">Określa, czy są włączone liczniki wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="42911-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="42911-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="42911-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42911-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="42911-116">Child Elements</span></span>  
 <span data-ttu-id="42911-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="42911-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42911-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="42911-118">Parent Elements</span></span>  
  
|<span data-ttu-id="42911-119">Element</span><span class="sxs-lookup"><span data-stu-id="42911-119">Element</span></span>|<span data-ttu-id="42911-120">Opis</span><span class="sxs-lookup"><span data-stu-id="42911-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42911-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="42911-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="42911-122">Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="42911-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42911-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42911-123">Remarks</span></span>  
 <span data-ttu-id="42911-124">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="42911-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="42911-125">Liczniki wydajności sieci muszą być włączone w pliku konfiguracji, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="42911-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="42911-126">Wszystkie liczniki wydajności sieci są włączone lub wyłączone przy użyciu jednego ustawienia w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="42911-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="42911-127">Nie można włączyć lub wyłączyć poszczególnych liczników wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="42911-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="42911-128">Aby uzyskać więcej informacji na temat określonych liczników wydajności sieci, zobacz [Network Performance Counters](../../../debug-trace-profile/performance-counters.md#networking).</span><span class="sxs-lookup"><span data-stu-id="42911-128">For more information on the specific networking performance counters, see [Networking Performance Counters](../../../debug-trace-profile/performance-counters.md#networking).</span></span>  
  
 <span data-ttu-id="42911-129">Wartością domyślną jest to, że liczniki wydajności sieci są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="42911-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="42911-130">Właściwość może służyć do uzyskiwania bieżącej wartości włączonego atrybutu z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="42911-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42911-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="42911-131">Example</span></span>  
 <span data-ttu-id="42911-132">Poniższy przykład pokazuje, <xref:System.Net> jak skonfigurować i powiązane przestrzenie nazw w celu włączenia liczników wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="42911-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="42911-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42911-133">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="42911-134">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="42911-134">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="42911-135">Liczniki wydajności sieci</span><span class="sxs-lookup"><span data-stu-id="42911-135">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking)
