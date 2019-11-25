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
ms.openlocfilehash: 58a2bf5118a3a2cd9c33301eca5dcc751c2351bf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283093"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="88f51-102">\<element > performanceCounter (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="88f51-102">\<performanceCounter> Element (Network Settings)</span></span>
<span data-ttu-id="88f51-103">Włącza lub wyłącza liczniki wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="88f51-103">Enables or disables networking performance counters.</span></span>  

<span data-ttu-id="88f51-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="88f51-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="88f51-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="88f51-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="88f51-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](settings-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="88f51-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>\
<span data-ttu-id="88f51-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<liczniki wydajności >**</span><span class="sxs-lookup"><span data-stu-id="88f51-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="88f51-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="88f51-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88f51-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="88f51-109">Attributes and Elements</span></span>  
 <span data-ttu-id="88f51-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="88f51-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88f51-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="88f51-111">Attributes</span></span>  
  
|<span data-ttu-id="88f51-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="88f51-112">Attribute</span></span>|<span data-ttu-id="88f51-113">Opis</span><span class="sxs-lookup"><span data-stu-id="88f51-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="88f51-114">Określa, czy są włączone liczniki wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="88f51-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="88f51-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="88f51-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88f51-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="88f51-116">Child Elements</span></span>  
 <span data-ttu-id="88f51-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="88f51-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88f51-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="88f51-118">Parent Elements</span></span>  
  
|<span data-ttu-id="88f51-119">Element</span><span class="sxs-lookup"><span data-stu-id="88f51-119">Element</span></span>|<span data-ttu-id="88f51-120">Opis</span><span class="sxs-lookup"><span data-stu-id="88f51-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88f51-121">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="88f51-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="88f51-122">Konfiguruje podstawowe opcje sieci dla przestrzeni nazw <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="88f51-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88f51-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88f51-123">Remarks</span></span>  
 <span data-ttu-id="88f51-124">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="88f51-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="88f51-125">Liczniki wydajności sieci muszą być włączone w pliku konfiguracji, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="88f51-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="88f51-126">Wszystkie liczniki wydajności sieci są włączone lub wyłączone przy użyciu jednego ustawienia w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="88f51-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="88f51-127">Nie można włączyć lub wyłączyć poszczególnych liczników wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="88f51-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="88f51-128">Aby uzyskać więcej informacji na temat określonych liczników wydajności sieci, zobacz [Network Performance Counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span><span class="sxs-lookup"><span data-stu-id="88f51-128">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="88f51-129">Wartością domyślną jest to, że liczniki wydajności sieci są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="88f51-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="88f51-130">Właściwość <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> może służyć do uzyskiwania bieżącej wartości **włączonego** atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="88f51-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88f51-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="88f51-131">Example</span></span>  
 <span data-ttu-id="88f51-132">Poniższy przykład pokazuje, jak skonfigurować <xref:System.Net> i powiązane przestrzenie nazw w celu włączenia liczników wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="88f51-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88f51-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88f51-133">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="88f51-134">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="88f51-134">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="88f51-135">Liczniki wydajności sieci</span><span class="sxs-lookup"><span data-stu-id="88f51-135">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
