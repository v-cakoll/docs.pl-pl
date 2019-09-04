---
title: <appDomainResourceMonitoring>, element
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1395ee64d94e33693344b678c7a949665f994079
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252822"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="0d892-102">\<appDomainResourceMonitoring, element ></span><span class="sxs-lookup"><span data-stu-id="0d892-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="0d892-103">Powoduje, że środowisko uruchomieniowe zbiera statystyki dotyczące wszystkich domen aplikacji w procesie przez cały czas trwania procesu.</span><span class="sxs-lookup"><span data-stu-id="0d892-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
<span data-ttu-id="0d892-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d892-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0d892-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d892-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="0d892-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainResourceMonitoring>**</span><span class="sxs-lookup"><span data-stu-id="0d892-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d892-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d892-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d892-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0d892-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0d892-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0d892-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d892-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0d892-110">Attributes</span></span>  
  
|<span data-ttu-id="0d892-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0d892-111">Attribute</span></span>|<span data-ttu-id="0d892-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0d892-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0d892-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0d892-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="0d892-114">Określa, czy środowisko uruchomieniowe zbiera statystyki dotyczące monitorowania zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0d892-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0d892-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="0d892-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="0d892-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="0d892-116">Value</span></span>|<span data-ttu-id="0d892-117">Opis</span><span class="sxs-lookup"><span data-stu-id="0d892-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="0d892-118">Zbierane są statystyki dotyczące monitorowania zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0d892-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="0d892-119">Nie są zbierane statystyki dotyczące monitorowania zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0d892-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d892-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0d892-120">Child Elements</span></span>  
 <span data-ttu-id="0d892-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="0d892-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d892-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0d892-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0d892-123">Element</span><span class="sxs-lookup"><span data-stu-id="0d892-123">Element</span></span>|<span data-ttu-id="0d892-124">Opis</span><span class="sxs-lookup"><span data-stu-id="0d892-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0d892-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d892-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0d892-126">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0d892-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d892-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d892-127">Remarks</span></span>  
 <span data-ttu-id="0d892-128">Monitorowanie zasobów domeny aplikacji jest dostępne za pomocą klasy domeny aplikacji zarządzanej, interfejsu hosta [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) i śledzenia zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="0d892-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="0d892-129">Po włączeniu monitorowania statystyki są zbierane dla wszystkich domen aplikacji w procesie przez cały czas trwania procesu.</span><span class="sxs-lookup"><span data-stu-id="0d892-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="0d892-130">Aby włączyć monitorowanie z kodu zarządzanego, użyj <xref:System.AppDomain.MonitoringIsEnabled%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d892-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="0d892-131">Ten element konfiguracji jest dostępny tylko w .NET Framework 4 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="0d892-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d892-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d892-132">Example</span></span>  
 <span data-ttu-id="0d892-133">Poniższy przykład pokazuje, jak włączyć monitorowanie zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0d892-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d892-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d892-134">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0d892-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="0d892-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0d892-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0d892-136">Configuration File Schema</span></span>](../index.md)
