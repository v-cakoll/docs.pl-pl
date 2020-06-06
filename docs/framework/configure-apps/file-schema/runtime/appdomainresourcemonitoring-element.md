---
title: <appDomainResourceMonitoring> Element
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: 3c6092b6c34bb13c0ad0e66df2d3b7e65ac3de7e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154379"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="4bf41-102">\<appDomainResourceMonitoring> Element</span><span class="sxs-lookup"><span data-stu-id="4bf41-102">\<appDomainResourceMonitoring> Element</span></span>
<span data-ttu-id="4bf41-103">Powoduje, że środowisko uruchomieniowe zbiera statystyki dotyczące wszystkich domen aplikacji w procesie przez cały czas trwania procesu.</span><span class="sxs-lookup"><span data-stu-id="4bf41-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a><span data-ttu-id="4bf41-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bf41-104">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4bf41-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4bf41-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4bf41-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4bf41-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4bf41-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4bf41-107">Attributes</span></span>  
  
|<span data-ttu-id="4bf41-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4bf41-108">Attribute</span></span>|<span data-ttu-id="4bf41-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4bf41-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4bf41-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="4bf41-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="4bf41-111">Określa, czy środowisko uruchomieniowe zbiera statystyki dotyczące monitorowania zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4bf41-111">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4bf41-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="4bf41-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="4bf41-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="4bf41-113">Value</span></span>|<span data-ttu-id="4bf41-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4bf41-114">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="4bf41-115">Zbierane są statystyki dotyczące monitorowania zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4bf41-115">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="4bf41-116">Nie są zbierane statystyki dotyczące monitorowania zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4bf41-116">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4bf41-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4bf41-117">Child Elements</span></span>  
 <span data-ttu-id="4bf41-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="4bf41-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4bf41-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4bf41-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4bf41-120">Element</span><span class="sxs-lookup"><span data-stu-id="4bf41-120">Element</span></span>|<span data-ttu-id="4bf41-121">Opis</span><span class="sxs-lookup"><span data-stu-id="4bf41-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4bf41-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4bf41-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4bf41-123">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="4bf41-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bf41-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4bf41-124">Remarks</span></span>  
 <span data-ttu-id="4bf41-125">Monitorowanie zasobów domeny aplikacji jest dostępne za pomocą klasy domeny aplikacji zarządzanej, interfejsu hosta [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) i śledzenia zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="4bf41-125">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="4bf41-126">Po włączeniu monitorowania statystyki są zbierane dla wszystkich domen aplikacji w procesie przez cały czas trwania procesu.</span><span class="sxs-lookup"><span data-stu-id="4bf41-126">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="4bf41-127">Aby włączyć monitorowanie z kodu zarządzanego, użyj <xref:System.AppDomain.MonitoringIsEnabled%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4bf41-127">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="4bf41-128">Ten element konfiguracji jest dostępny tylko w .NET Framework 4 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="4bf41-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bf41-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="4bf41-129">Example</span></span>  
 <span data-ttu-id="4bf41-130">Poniższy przykład pokazuje, jak włączyć monitorowanie zasobów domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4bf41-130">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4bf41-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bf41-131">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4bf41-132">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="4bf41-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4bf41-133">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4bf41-133">Configuration File Schema</span></span>](../index.md)
