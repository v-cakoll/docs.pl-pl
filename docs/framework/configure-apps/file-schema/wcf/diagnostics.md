---
title: '&lt;Diagnostyka&gt;'
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: de11145620e8fdf96785908df85ab5ecdfd2e25e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524598"
---
# <a name="ltdiagnosticsgt"></a><span data-ttu-id="cabb1-102">&lt;Diagnostyka&gt;</span><span class="sxs-lookup"><span data-stu-id="cabb1-102">&lt;diagnostics&gt;</span></span>
<span data-ttu-id="cabb1-103">`diagnostics` Element definiuje ustawienia używane przez administratora w czasie wykonywania inspekcji i kontroli.</span><span class="sxs-lookup"><span data-stu-id="cabb1-103">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="cabb1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cabb1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cabb1-105">\<Diagnostyka ></span><span class="sxs-lookup"><span data-stu-id="cabb1-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cabb1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cabb1-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics etwProviderId="String"
               performanceCounters="Off/ServiceOnly/All/Default"
               wmiProviderEnabled="Boolean">
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cabb1-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cabb1-107">Attributes and Elements</span></span>  
 <span data-ttu-id="cabb1-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cabb1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cabb1-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cabb1-109">Attributes</span></span>  
  
|<span data-ttu-id="cabb1-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cabb1-110">Attribute</span></span>|<span data-ttu-id="cabb1-111">Opis</span><span class="sxs-lookup"><span data-stu-id="cabb1-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cabb1-112">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="cabb1-112">etwProviderId</span></span>|<span data-ttu-id="cabb1-113">Ciąg określający identyfikator dostawcy śledzenia zdarzeń, który zapisuje zdarzenia do sesji ETW.</span><span class="sxs-lookup"><span data-stu-id="cabb1-113">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="cabb1-114">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="cabb1-114">performanceCounters</span></span>|<span data-ttu-id="cabb1-115">Określa, czy są włączone liczniki wydajności dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="cabb1-115">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="cabb1-116">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="cabb1-116">Valid values are</span></span><br /><br /> <span data-ttu-id="cabb1-117">— Wyłączone: Liczniki wydajności są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="cabb1-117">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="cabb1-118">-ServiceOnly: Tylko liczniki wydajności istotne dla tej usługi jest włączone.</span><span class="sxs-lookup"><span data-stu-id="cabb1-118">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="cabb1-119">— Wszystkie: Liczniki wydajności mogą być wyświetlane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cabb1-119">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="cabb1-120">— Wartość domyślna: _WCF_Admin wystąpienia licznika wydajności pojedynczego zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="cabb1-120">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="cabb1-121">To wystąpienie jest używane do włączenia zbierania danych METRYK dla używana przez infrastrukturę.</span><span class="sxs-lookup"><span data-stu-id="cabb1-121">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="cabb1-122">Brak wartości liczników dla tego wystąpienia są aktualizowane, a w związku z tym pozostanie od zera.</span><span class="sxs-lookup"><span data-stu-id="cabb1-122">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="cabb1-123">Jest wartością domyślną, jeśli konfiguracja nie jest obecny dla usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="cabb1-123">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="cabb1-124">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="cabb1-124">wmiProviderEnabled</span></span>|<span data-ttu-id="cabb1-125">Wartość logiczna określająca, czy włączony jest dostawca usługi WMI dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="cabb1-125">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="cabb1-126">Dostawca usługi WMI jest wymagana dla użytkownika w celu uzyskania dostępu do funkcji inspekcji i kontroli programu Windows Communication Foundation (WCF) w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cabb1-126">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="cabb1-127">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="cabb1-127">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cabb1-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cabb1-128">Child Elements</span></span>  
  
|<span data-ttu-id="cabb1-129">Element</span><span class="sxs-lookup"><span data-stu-id="cabb1-129">Element</span></span>|<span data-ttu-id="cabb1-130">Opis</span><span class="sxs-lookup"><span data-stu-id="cabb1-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cabb1-131">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="cabb1-131">\<endToEndTracing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|<span data-ttu-id="cabb1-132">Element konfiguracji, który umożliwia włączanie i wyłączanie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="cabb1-132">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="cabb1-133">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="cabb1-133">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|<span data-ttu-id="cabb1-134">W tym artykule opisano ustawienia rejestrowania komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="cabb1-134">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cabb1-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cabb1-135">Parent Elements</span></span>  
  
|<span data-ttu-id="cabb1-136">Element</span><span class="sxs-lookup"><span data-stu-id="cabb1-136">Element</span></span>|<span data-ttu-id="cabb1-137">Opis</span><span class="sxs-lookup"><span data-stu-id="cabb1-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cabb1-138">serviceModel</span><span class="sxs-lookup"><span data-stu-id="cabb1-138">serviceModel</span></span>|<span data-ttu-id="cabb1-139">Element główny wszystkich elementów konfiguracji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="cabb1-139">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cabb1-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cabb1-140">Remarks</span></span>  
 <span data-ttu-id="cabb1-141">`diagnostics` Sekcja definiuje ustawienia diagnostyki dla wszystkich usług znajdujących się w zestawie.</span><span class="sxs-lookup"><span data-stu-id="cabb1-141">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="cabb1-142">Nie jest możliwe do definiowania ustawień diagnostycznych oddzielne na poziomie usługi, chyba że istnieje tylko jedna usługa w zestawie.</span><span class="sxs-lookup"><span data-stu-id="cabb1-142">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="cabb1-143">Atrybuty są ustawione zgodnie z wymogami sekcji.</span><span class="sxs-lookup"><span data-stu-id="cabb1-143">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cabb1-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="cabb1-144">Example</span></span>  
  
```xml  
<diagnostics wmiProviderEnabled="false"
             performanceCounters="all">
  <messageLogging logEntireMessage="true"
                  logMalformedMessages="true"
                  logMessagesAtServiceLevel="true"
                  logMessagesAtTransportLevel="true"
                  maxMessagesToLog="42"
                  maxSizeOfMessageToLog="42">
    <filters>
      <clear />
    </filters>
  </messageLogging>
</diagnostics>
```  
  
## <a name="see-also"></a><span data-ttu-id="cabb1-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cabb1-145">See also</span></span>
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
