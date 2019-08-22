---
title: <appDomainResourceMonitoring>, element
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b82be30c18cde361aa412ee1b631c8368c8de1b3
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663929"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="66720-102">\<appDomainResourceMonitoring, element ></span><span class="sxs-lookup"><span data-stu-id="66720-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="66720-103">Powoduje, że środowisko uruchomieniowe zbiera statystyki dotyczące wszystkich domen aplikacji w procesie przez cały czas trwania procesu.</span><span class="sxs-lookup"><span data-stu-id="66720-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="66720-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="66720-104">\<configuration></span></span>  
<span data-ttu-id="66720-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="66720-105">\<runtime></span></span>  
<span data-ttu-id="66720-106">\<appDomainResourceMonitoring ></span><span class="sxs-lookup"><span data-stu-id="66720-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66720-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="66720-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66720-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="66720-108">Attributes and Elements</span></span>  
 <span data-ttu-id="66720-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="66720-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66720-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="66720-110">Attributes</span></span>  
  
|<span data-ttu-id="66720-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="66720-111">Attribute</span></span>|<span data-ttu-id="66720-112">Opis</span><span class="sxs-lookup"><span data-stu-id="66720-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="66720-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="66720-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="66720-114">Określa, czy środowisko uruchomieniowe zbiera statystyki dotyczące monitorowania zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="66720-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="66720-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="66720-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="66720-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="66720-116">Value</span></span>|<span data-ttu-id="66720-117">Opis</span><span class="sxs-lookup"><span data-stu-id="66720-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="66720-118">Zbierane są statystyki dotyczące monitorowania zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="66720-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="66720-119">Nie są zbierane statystyki dotyczące monitorowania zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="66720-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66720-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="66720-120">Child Elements</span></span>  
 <span data-ttu-id="66720-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="66720-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66720-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="66720-122">Parent Elements</span></span>  
  
|<span data-ttu-id="66720-123">Element</span><span class="sxs-lookup"><span data-stu-id="66720-123">Element</span></span>|<span data-ttu-id="66720-124">Opis</span><span class="sxs-lookup"><span data-stu-id="66720-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="66720-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="66720-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="66720-126">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="66720-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66720-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66720-127">Remarks</span></span>  
 <span data-ttu-id="66720-128">Monitorowanie zasobów domeny aplikacji jest dostępne za pomocą klasy domeny aplikacji zarządzanej, interfejsu hosta [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) i śledzenia zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="66720-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="66720-129">Po włączeniu monitorowania statystyki są zbierane dla wszystkich domen aplikacji w procesie przez cały czas trwania procesu.</span><span class="sxs-lookup"><span data-stu-id="66720-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="66720-130">Aby włączyć monitorowanie z kodu zarządzanego, użyj <xref:System.AppDomain.MonitoringIsEnabled%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="66720-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="66720-131">Ten element konfiguracji jest dostępny tylko w .NET Framework 4 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="66720-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66720-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="66720-132">Example</span></span>  
 <span data-ttu-id="66720-133">Poniższy przykład pokazuje, jak włączyć monitorowanie zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="66720-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="66720-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66720-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="66720-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="66720-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="66720-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="66720-136">Configuration File Schema</span></span>](../index.md)
