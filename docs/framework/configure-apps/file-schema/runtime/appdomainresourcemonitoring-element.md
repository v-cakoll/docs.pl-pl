---
title: "&lt;appdomainresourcemonitoring —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58caa7458d96ca7bb9088b607a83b2d6be667cae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltappdomainresourcemonitoringgt-element"></a><span data-ttu-id="3613c-102">&lt;appdomainresourcemonitoring —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="3613c-102">&lt;appDomainResourceMonitoring&gt; Element</span></span>
<span data-ttu-id="3613c-103">Powoduje, że środowiska uruchomieniowego w celu zbierania statystyk we wszystkich domenach aplikacji w trakcie cyklu życia procesu.</span><span class="sxs-lookup"><span data-stu-id="3613c-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="3613c-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="3613c-104">\<configuration></span></span>  
<span data-ttu-id="3613c-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="3613c-105">\<runtime></span></span>  
<span data-ttu-id="3613c-106">\<appdomainresourcemonitoring — ></span><span class="sxs-lookup"><span data-stu-id="3613c-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3613c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3613c-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3613c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3613c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3613c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3613c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3613c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3613c-110">Attributes</span></span>  
  
|<span data-ttu-id="3613c-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3613c-111">Attribute</span></span>|<span data-ttu-id="3613c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3613c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3613c-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="3613c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3613c-114">Określa, czy środowisko uruchomieniowe zbiera statystyki dotyczące monitorowania zasobów domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3613c-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3613c-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="3613c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3613c-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="3613c-116">Value</span></span>|<span data-ttu-id="3613c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="3613c-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="3613c-118">Statystyki dotyczące monitorowania zasobów domen aplikacji są zbierane.</span><span class="sxs-lookup"><span data-stu-id="3613c-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="3613c-119">Statystyki dotyczące monitorowania zasobów domen aplikacji nie są zbierane.</span><span class="sxs-lookup"><span data-stu-id="3613c-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3613c-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3613c-120">Child Elements</span></span>  
 <span data-ttu-id="3613c-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="3613c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3613c-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3613c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3613c-123">Element</span><span class="sxs-lookup"><span data-stu-id="3613c-123">Element</span></span>|<span data-ttu-id="3613c-124">Opis</span><span class="sxs-lookup"><span data-stu-id="3613c-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3613c-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3613c-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3613c-126">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="3613c-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3613c-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3613c-127">Remarks</span></span>  
 <span data-ttu-id="3613c-128">Monitorowanie zasobów domen aplikacji jest dostępna za pośrednictwem klasy domeny zarządzanej aplikacji, hostingu [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interfejsu i śledzenie zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="3613c-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="3613c-129">Gdy jest włączone monitorowanie, statystyki są zbierane dla wszystkich domen aplikacji w trakcie cyklu życia procesu.</span><span class="sxs-lookup"><span data-stu-id="3613c-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="3613c-130">Aby włączyć monitorowanie z kodu zarządzanego, użyj <xref:System.AppDomain.MonitoringIsEnabled%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3613c-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="3613c-131">Ten element konfiguracji jest dostępny tylko w [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] i nowszych.</span><span class="sxs-lookup"><span data-stu-id="3613c-131">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3613c-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="3613c-132">Example</span></span>  
 <span data-ttu-id="3613c-133">Poniższy przykład przedstawia sposób włączania monitorowania zasobów domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3613c-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3613c-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3613c-134">See Also</span></span>  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="3613c-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3613c-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="3613c-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3613c-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
