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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74283093"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="88bbd-102">\<performanceCounter>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="88bbd-102">\<performanceCounter> Element (Network Settings)</span></span>
<span data-ttu-id="88bbd-103">Włącza lub wyłącza liczniki wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="88bbd-103">Enables or disables networking performance counters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a><span data-ttu-id="88bbd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88bbd-104">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88bbd-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="88bbd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="88bbd-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="88bbd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88bbd-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="88bbd-107">Attributes</span></span>  
  
|<span data-ttu-id="88bbd-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="88bbd-108">Attribute</span></span>|<span data-ttu-id="88bbd-109">Opis</span><span class="sxs-lookup"><span data-stu-id="88bbd-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="88bbd-110">Określa, czy są włączone liczniki wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="88bbd-110">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="88bbd-111">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="88bbd-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88bbd-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="88bbd-112">Child Elements</span></span>  
 <span data-ttu-id="88bbd-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="88bbd-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88bbd-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="88bbd-114">Parent Elements</span></span>  
  
|<span data-ttu-id="88bbd-115">Element</span><span class="sxs-lookup"><span data-stu-id="88bbd-115">Element</span></span>|<span data-ttu-id="88bbd-116">Opis</span><span class="sxs-lookup"><span data-stu-id="88bbd-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88bbd-117">ustawienia</span><span class="sxs-lookup"><span data-stu-id="88bbd-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="88bbd-118">Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="88bbd-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88bbd-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88bbd-119">Remarks</span></span>  
 <span data-ttu-id="88bbd-120">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="88bbd-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="88bbd-121">Liczniki wydajności sieci muszą być włączone w pliku konfiguracji, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="88bbd-121">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="88bbd-122">Wszystkie liczniki wydajności sieci są włączone lub wyłączone przy użyciu jednego ustawienia w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="88bbd-122">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="88bbd-123">Nie można włączyć lub wyłączyć poszczególnych liczników wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="88bbd-123">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="88bbd-124">Aby uzyskać więcej informacji na temat określonych liczników wydajności sieci, zobacz [Network Performance Counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span><span class="sxs-lookup"><span data-stu-id="88bbd-124">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="88bbd-125">Wartością domyślną jest to, że liczniki wydajności sieci są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="88bbd-125">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="88bbd-126"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>Właściwość może służyć do uzyskiwania bieżącej wartości **włączonego** atrybutu z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="88bbd-126">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88bbd-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="88bbd-127">Example</span></span>  
 <span data-ttu-id="88bbd-128">Poniższy przykład pokazuje, jak skonfigurować <xref:System.Net> i powiązane przestrzenie nazw w celu włączenia liczników wydajności sieci.</span><span class="sxs-lookup"><span data-stu-id="88bbd-128">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88bbd-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88bbd-129">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="88bbd-130">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="88bbd-130">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="88bbd-131">Liczniki wydajności sieci</span><span class="sxs-lookup"><span data-stu-id="88bbd-131">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
