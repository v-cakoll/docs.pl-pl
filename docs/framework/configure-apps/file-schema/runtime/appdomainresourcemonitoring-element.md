---
title: <appDomainResourceMonitoring>, element
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71cc69eba17de8465cc7999f334c724e4ec14e7d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705002"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="b7a78-102">\<appDomainResourceMonitoring> Element</span><span class="sxs-lookup"><span data-stu-id="b7a78-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="b7a78-103">Powoduje, że środowisko uruchomieniowe w celu zbierania statystyk na wszystkie domeny aplikacji, w trakcie trwania procesu.</span><span class="sxs-lookup"><span data-stu-id="b7a78-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="b7a78-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="b7a78-104">\<configuration></span></span>  
<span data-ttu-id="b7a78-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="b7a78-105">\<runtime></span></span>  
<span data-ttu-id="b7a78-106">\<appDomainResourceMonitoring></span><span class="sxs-lookup"><span data-stu-id="b7a78-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a78-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7a78-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7a78-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b7a78-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b7a78-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b7a78-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7a78-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b7a78-110">Attributes</span></span>  
  
|<span data-ttu-id="b7a78-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b7a78-111">Attribute</span></span>|<span data-ttu-id="b7a78-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b7a78-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b7a78-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b7a78-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="b7a78-114">Określa, czy środowisko uruchomieniowe zbiera statystyki dotyczące monitorowania zasobów domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b7a78-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b7a78-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="b7a78-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="b7a78-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="b7a78-116">Value</span></span>|<span data-ttu-id="b7a78-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b7a78-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="b7a78-118">Monitorowanie zasobów domeny aplikacji statystyki są zbierane.</span><span class="sxs-lookup"><span data-stu-id="b7a78-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="b7a78-119">Statystyki dotyczące monitorowanie zasobów domeny aplikacji nie są zbierane.</span><span class="sxs-lookup"><span data-stu-id="b7a78-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7a78-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b7a78-120">Child Elements</span></span>  
 <span data-ttu-id="b7a78-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="b7a78-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7a78-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b7a78-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b7a78-123">Element</span><span class="sxs-lookup"><span data-stu-id="b7a78-123">Element</span></span>|<span data-ttu-id="b7a78-124">Opis</span><span class="sxs-lookup"><span data-stu-id="b7a78-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b7a78-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b7a78-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b7a78-126">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b7a78-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7a78-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7a78-127">Remarks</span></span>  
 <span data-ttu-id="b7a78-128">Monitorowanie zasobów domeny aplikacji jest dostępna za pośrednictwem klasy domeny zarządzanej aplikacji, hostingu [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interfejsu i śledzenie zdarzeń dla Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="b7a78-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="b7a78-129">Gdy jest włączone monitorowanie, statystyki są zbierane dla wszystkich domen aplikacji w trakcie trwania procesu.</span><span class="sxs-lookup"><span data-stu-id="b7a78-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="b7a78-130">Aby włączyć monitorowanie z kodu zarządzanego, należy użyć <xref:System.AppDomain.MonitoringIsEnabled%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b7a78-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="b7a78-131">Ten element konfiguracji jest dostępny tylko w [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] i nowszych.</span><span class="sxs-lookup"><span data-stu-id="b7a78-131">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7a78-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="b7a78-132">Example</span></span>  
 <span data-ttu-id="b7a78-133">Poniższy przykład pokazuje, jak umożliwić monitorowanie zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b7a78-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7a78-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7a78-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b7a78-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b7a78-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="b7a78-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b7a78-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
