---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 3fc7828d399555f7c459f6dd067ce9a24b8998b6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108033"
---
# <a name="diagnostics"></a><span data-ttu-id="07a14-101">\<Diagnostyka ></span><span class="sxs-lookup"><span data-stu-id="07a14-101">\<diagnostics></span></span>
<span data-ttu-id="07a14-102">`diagnostics` Element definiuje ustawienia używane przez administratora w czasie wykonywania inspekcji i kontroli.</span><span class="sxs-lookup"><span data-stu-id="07a14-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="07a14-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="07a14-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="07a14-104">\<Diagnostyka ></span><span class="sxs-lookup"><span data-stu-id="07a14-104">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07a14-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="07a14-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07a14-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="07a14-106">Attributes and Elements</span></span>  
 <span data-ttu-id="07a14-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="07a14-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07a14-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="07a14-108">Attributes</span></span>  
  
|<span data-ttu-id="07a14-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="07a14-109">Attribute</span></span>|<span data-ttu-id="07a14-110">Opis</span><span class="sxs-lookup"><span data-stu-id="07a14-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="07a14-111">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="07a14-111">etwProviderId</span></span>|<span data-ttu-id="07a14-112">Ciąg określający identyfikator dostawcy śledzenia zdarzeń, który zapisuje zdarzenia do sesji ETW.</span><span class="sxs-lookup"><span data-stu-id="07a14-112">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="07a14-113">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="07a14-113">performanceCounters</span></span>|<span data-ttu-id="07a14-114">Określa, czy są włączone liczniki wydajności dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="07a14-114">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="07a14-115">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="07a14-115">Valid values are</span></span><br /><br /> <span data-ttu-id="07a14-116">— Wyłączone: Liczniki wydajności są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="07a14-116">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="07a14-117">-ServiceOnly: Tylko liczniki wydajności istotne dla tej usługi jest włączone.</span><span class="sxs-lookup"><span data-stu-id="07a14-117">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="07a14-118">— Wszystkie: Liczniki wydajności mogą być wyświetlane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="07a14-118">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="07a14-119">— Wartość domyślna: _WCF_Admin wystąpienia licznika wydajności pojedynczego zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="07a14-119">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="07a14-120">To wystąpienie jest używane do włączenia zbierania danych METRYK dla używana przez infrastrukturę.</span><span class="sxs-lookup"><span data-stu-id="07a14-120">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="07a14-121">Brak wartości liczników dla tego wystąpienia są aktualizowane, a w związku z tym pozostanie od zera.</span><span class="sxs-lookup"><span data-stu-id="07a14-121">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="07a14-122">Jest wartością domyślną, jeśli konfiguracja nie jest obecny dla usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="07a14-122">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="07a14-123">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="07a14-123">wmiProviderEnabled</span></span>|<span data-ttu-id="07a14-124">Wartość logiczna określająca, czy włączony jest dostawca usługi WMI dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="07a14-124">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="07a14-125">Dostawca usługi WMI jest wymagana dla użytkownika w celu uzyskania dostępu do funkcji inspekcji i kontroli programu Windows Communication Foundation (WCF) w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="07a14-125">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="07a14-126">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="07a14-126">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07a14-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="07a14-127">Child Elements</span></span>  
  
|<span data-ttu-id="07a14-128">Element</span><span class="sxs-lookup"><span data-stu-id="07a14-128">Element</span></span>|<span data-ttu-id="07a14-129">Opis</span><span class="sxs-lookup"><span data-stu-id="07a14-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07a14-130">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="07a14-130">\<endToEndTracing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|<span data-ttu-id="07a14-131">Element konfiguracji, który umożliwia włączanie i wyłączanie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="07a14-131">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="07a14-132">\<messageLogging></span><span class="sxs-lookup"><span data-stu-id="07a14-132">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|<span data-ttu-id="07a14-133">W tym artykule opisano ustawienia rejestrowania komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="07a14-133">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="07a14-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="07a14-134">Parent Elements</span></span>  
  
|<span data-ttu-id="07a14-135">Element</span><span class="sxs-lookup"><span data-stu-id="07a14-135">Element</span></span>|<span data-ttu-id="07a14-136">Opis</span><span class="sxs-lookup"><span data-stu-id="07a14-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07a14-137">serviceModel</span><span class="sxs-lookup"><span data-stu-id="07a14-137">serviceModel</span></span>|<span data-ttu-id="07a14-138">Element główny wszystkich elementów konfiguracji programu WCF.</span><span class="sxs-lookup"><span data-stu-id="07a14-138">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07a14-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07a14-139">Remarks</span></span>  
 <span data-ttu-id="07a14-140">`diagnostics` Sekcja definiuje ustawienia diagnostyki dla wszystkich usług znajdujących się w zestawie.</span><span class="sxs-lookup"><span data-stu-id="07a14-140">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="07a14-141">Nie jest możliwe do definiowania ustawień diagnostycznych oddzielne na poziomie usługi, chyba że istnieje tylko jedna usługa w zestawie.</span><span class="sxs-lookup"><span data-stu-id="07a14-141">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="07a14-142">Atrybuty są ustawione zgodnie z wymogami sekcji.</span><span class="sxs-lookup"><span data-stu-id="07a14-142">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07a14-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="07a14-143">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07a14-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07a14-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
