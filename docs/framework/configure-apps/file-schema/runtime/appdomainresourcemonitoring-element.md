---
title: <appDomainResourceMonitoring>, element
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154379"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="c1801-102">\<element>> monitorowania> appDomainResource</span><span class="sxs-lookup"><span data-stu-id="c1801-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="c1801-103">Nakazuje środowiska wykonawczego do zbierania statystyk dotyczących wszystkich domen aplikacji w procesie przez cały okres procesu.</span><span class="sxs-lookup"><span data-stu-id="c1801-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
<span data-ttu-id="c1801-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c1801-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c1801-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="c1801-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="c1801-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<>monitorowania aplikacji DomaineResourceMonitoring**</span><span class="sxs-lookup"><span data-stu-id="c1801-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1801-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1801-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1801-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c1801-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c1801-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c1801-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1801-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c1801-110">Attributes</span></span>  
  
|<span data-ttu-id="c1801-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c1801-111">Attribute</span></span>|<span data-ttu-id="c1801-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c1801-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c1801-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="c1801-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c1801-114">Określa, czy środowisko wykonawcze zbiera statystyki monitorowania zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c1801-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c1801-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="c1801-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="c1801-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="c1801-116">Value</span></span>|<span data-ttu-id="c1801-117">Opis</span><span class="sxs-lookup"><span data-stu-id="c1801-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="c1801-118">Zbierane są statystyki monitorowania zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c1801-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="c1801-119">Statystyki monitorowania zasobów domeny aplikacji nie są zbierane.</span><span class="sxs-lookup"><span data-stu-id="c1801-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1801-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c1801-120">Child Elements</span></span>  
 <span data-ttu-id="c1801-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="c1801-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1801-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c1801-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c1801-123">Element</span><span class="sxs-lookup"><span data-stu-id="c1801-123">Element</span></span>|<span data-ttu-id="c1801-124">Opis</span><span class="sxs-lookup"><span data-stu-id="c1801-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c1801-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c1801-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c1801-126">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c1801-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1801-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1801-127">Remarks</span></span>  
 <span data-ttu-id="c1801-128">Monitorowanie zasobów domeny aplikacji jest dostępne za pośrednictwem klasy domeny aplikacji zarządzanej, hostingu interfejsu [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) i śledzenia zdarzeń dla systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="c1801-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="c1801-129">Gdy monitorowanie jest włączone, statystyki są zbierane dla wszystkich domen aplikacji w procesie przez cały okres procesu.</span><span class="sxs-lookup"><span data-stu-id="c1801-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="c1801-130">Aby włączyć monitorowanie z kodu <xref:System.AppDomain.MonitoringIsEnabled%2A> zarządzanego, należy użyć właściwości.</span><span class="sxs-lookup"><span data-stu-id="c1801-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="c1801-131">Ten element konfiguracji jest dostępny tylko w programie .NET Framework 4 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="c1801-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1801-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1801-132">Example</span></span>  
 <span data-ttu-id="c1801-133">W poniższym przykładzie pokazano, jak włączyć monitorowanie zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c1801-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1801-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1801-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c1801-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c1801-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c1801-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c1801-136">Configuration File Schema</span></span>](../index.md)
