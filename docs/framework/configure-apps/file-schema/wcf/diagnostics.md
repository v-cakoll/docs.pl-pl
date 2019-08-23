---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 170cae5b328c86073c1d8e7710bb19e98ab5688c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925880"
---
# <a name="diagnostics"></a><span data-ttu-id="3a9bc-101">\<> diagnostyki</span><span class="sxs-lookup"><span data-stu-id="3a9bc-101">\<diagnostics></span></span>
<span data-ttu-id="3a9bc-102">`diagnostics` Element definiuje ustawienia, które mogą być używane przez administratora na potrzeby inspekcji i kontroli w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="3a9bc-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3a9bc-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3a9bc-104">\<> diagnostyki</span><span class="sxs-lookup"><span data-stu-id="3a9bc-104">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a9bc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a9bc-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a9bc-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3a9bc-106">Attributes and Elements</span></span>  
 <span data-ttu-id="3a9bc-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a9bc-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3a9bc-108">Attributes</span></span>  
  
|<span data-ttu-id="3a9bc-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3a9bc-109">Attribute</span></span>|<span data-ttu-id="3a9bc-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3a9bc-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a9bc-111">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="3a9bc-111">etwProviderId</span></span>|<span data-ttu-id="3a9bc-112">Ciąg określający identyfikator dostawcy śledzenia zdarzeń, który zapisuje zdarzenia do sesji ETW.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-112">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="3a9bc-113">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="3a9bc-113">performanceCounters</span></span>|<span data-ttu-id="3a9bc-114">Określa, czy są włączone liczniki wydajności dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-114">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="3a9bc-115">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="3a9bc-115">Valid values are</span></span><br /><br /> <span data-ttu-id="3a9bc-116">Logowanie Liczniki wydajności są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-116">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="3a9bc-117">-Tylko Service: Włączono tylko liczniki wydajności odpowiednie dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-117">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="3a9bc-118">Całą Liczniki wydajności mogą być wyświetlane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-118">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="3a9bc-119">Wartooć Tworzone jest pojedyncze wystąpienie licznika wydajności _WCF_Admin.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-119">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="3a9bc-120">To wystąpienie jest używane do włączania zbierania danych SQM używanych przez infrastrukturę.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-120">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="3a9bc-121">Żadna z wartości licznika dla tego wystąpienia nie jest aktualizowana i w związku z tym pozostanie równa zero.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-121">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="3a9bc-122">Jest to wartość domyślna, jeśli żadna konfiguracja nie jest obecna dla programu WCF.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-122">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="3a9bc-123">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="3a9bc-123">wmiProviderEnabled</span></span>|<span data-ttu-id="3a9bc-124">Wartość logiczna określająca, czy dostawca WMI dla zestawu jest włączony.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-124">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="3a9bc-125">Dostawca WMI jest wymagany, aby użytkownik mógł uzyskać dostęp do funkcji inspekcji i kontroli programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3a9bc-125">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="3a9bc-126">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-126">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a9bc-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3a9bc-127">Child Elements</span></span>  
  
|<span data-ttu-id="3a9bc-128">Element</span><span class="sxs-lookup"><span data-stu-id="3a9bc-128">Element</span></span>|<span data-ttu-id="3a9bc-129">Opis</span><span class="sxs-lookup"><span data-stu-id="3a9bc-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a9bc-130">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="3a9bc-130">\<endToEndTracing></span></span>](endtoendtracing.md)|<span data-ttu-id="3a9bc-131">Element konfiguracji, który pozwala na włączenie i wyłączenie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-131">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="3a9bc-132">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="3a9bc-132">\<messageLogging></span></span>](messagelogging.md)|<span data-ttu-id="3a9bc-133">Opisuje ustawienia rejestrowania komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-133">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a9bc-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3a9bc-134">Parent Elements</span></span>  
  
|<span data-ttu-id="3a9bc-135">Element</span><span class="sxs-lookup"><span data-stu-id="3a9bc-135">Element</span></span>|<span data-ttu-id="3a9bc-136">Opis</span><span class="sxs-lookup"><span data-stu-id="3a9bc-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a9bc-137">Modelu</span><span class="sxs-lookup"><span data-stu-id="3a9bc-137">serviceModel</span></span>|<span data-ttu-id="3a9bc-138">Element główny wszystkich elementów konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-138">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a9bc-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a9bc-139">Remarks</span></span>  
 <span data-ttu-id="3a9bc-140">`diagnostics` Sekcja definiuje ustawienia diagnostyki dla wszystkich usług znajdujących się w zestawie.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-140">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="3a9bc-141">Nie można definiować oddzielnych ustawień diagnostycznych na poziomie usługi, chyba że w zestawie znajduje się tylko jedna usługa.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-141">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="3a9bc-142">Atrybuty są ustawiane zgodnie z wymaganiami sekcji.</span><span class="sxs-lookup"><span data-stu-id="3a9bc-142">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a9bc-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a9bc-143">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a9bc-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a9bc-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
