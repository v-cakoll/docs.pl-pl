---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 2749bc6c66d491a8a160d98b508fb43aa027b806
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398041"
---
# <a name="diagnostics"></a><span data-ttu-id="086a0-101">\<> diagnostyki</span><span class="sxs-lookup"><span data-stu-id="086a0-101">\<diagnostics></span></span>
<span data-ttu-id="086a0-102">`diagnostics` Element definiuje ustawienia, które mogą być używane przez administratora na potrzeby inspekcji i kontroli w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="086a0-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
<span data-ttu-id="086a0-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="086a0-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="086a0-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="086a0-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="086a0-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<> diagnostyki**</span><span class="sxs-lookup"><span data-stu-id="086a0-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="086a0-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="086a0-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="086a0-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="086a0-107">Attributes and Elements</span></span>  
 <span data-ttu-id="086a0-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="086a0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="086a0-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="086a0-109">Attributes</span></span>  
  
|<span data-ttu-id="086a0-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="086a0-110">Attribute</span></span>|<span data-ttu-id="086a0-111">Opis</span><span class="sxs-lookup"><span data-stu-id="086a0-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="086a0-112">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="086a0-112">etwProviderId</span></span>|<span data-ttu-id="086a0-113">Ciąg określający identyfikator dostawcy śledzenia zdarzeń, który zapisuje zdarzenia do sesji ETW.</span><span class="sxs-lookup"><span data-stu-id="086a0-113">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="086a0-114">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="086a0-114">performanceCounters</span></span>|<span data-ttu-id="086a0-115">Określa, czy są włączone liczniki wydajności dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="086a0-115">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="086a0-116">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="086a0-116">Valid values are</span></span><br /><br /> <span data-ttu-id="086a0-117">Logowanie Liczniki wydajności są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="086a0-117">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="086a0-118">-Tylko Service: Włączono tylko liczniki wydajności odpowiednie dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="086a0-118">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="086a0-119">Całą Liczniki wydajności mogą być wyświetlane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="086a0-119">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="086a0-120">Wartooć Tworzone jest pojedyncze wystąpienie licznika wydajności _WCF_Admin.</span><span class="sxs-lookup"><span data-stu-id="086a0-120">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="086a0-121">To wystąpienie jest używane do włączania zbierania danych SQM używanych przez infrastrukturę.</span><span class="sxs-lookup"><span data-stu-id="086a0-121">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="086a0-122">Żadna z wartości licznika dla tego wystąpienia nie jest aktualizowana i w związku z tym pozostanie równa zero.</span><span class="sxs-lookup"><span data-stu-id="086a0-122">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="086a0-123">Jest to wartość domyślna, jeśli żadna konfiguracja nie jest obecna dla programu WCF.</span><span class="sxs-lookup"><span data-stu-id="086a0-123">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="086a0-124">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="086a0-124">wmiProviderEnabled</span></span>|<span data-ttu-id="086a0-125">Wartość logiczna określająca, czy dostawca WMI dla zestawu jest włączony.</span><span class="sxs-lookup"><span data-stu-id="086a0-125">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="086a0-126">Dostawca WMI jest wymagany, aby użytkownik mógł uzyskać dostęp do funkcji inspekcji i kontroli programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="086a0-126">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="086a0-127">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="086a0-127">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="086a0-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="086a0-128">Child Elements</span></span>  
  
|<span data-ttu-id="086a0-129">Element</span><span class="sxs-lookup"><span data-stu-id="086a0-129">Element</span></span>|<span data-ttu-id="086a0-130">Opis</span><span class="sxs-lookup"><span data-stu-id="086a0-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="086a0-131">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="086a0-131">\<endToEndTracing></span></span>](endtoendtracing.md)|<span data-ttu-id="086a0-132">Element konfiguracji, który pozwala na włączenie i wyłączenie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="086a0-132">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="086a0-133">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="086a0-133">\<messageLogging></span></span>](messagelogging.md)|<span data-ttu-id="086a0-134">Opisuje ustawienia rejestrowania komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="086a0-134">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="086a0-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="086a0-135">Parent Elements</span></span>  
  
|<span data-ttu-id="086a0-136">Element</span><span class="sxs-lookup"><span data-stu-id="086a0-136">Element</span></span>|<span data-ttu-id="086a0-137">Opis</span><span class="sxs-lookup"><span data-stu-id="086a0-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="086a0-138">Modelu</span><span class="sxs-lookup"><span data-stu-id="086a0-138">serviceModel</span></span>|<span data-ttu-id="086a0-139">Element główny wszystkich elementów konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="086a0-139">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="086a0-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="086a0-140">Remarks</span></span>  
 <span data-ttu-id="086a0-141">`diagnostics` Sekcja definiuje ustawienia diagnostyki dla wszystkich usług znajdujących się w zestawie.</span><span class="sxs-lookup"><span data-stu-id="086a0-141">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="086a0-142">Nie można definiować oddzielnych ustawień diagnostycznych na poziomie usługi, chyba że w zestawie znajduje się tylko jedna usługa.</span><span class="sxs-lookup"><span data-stu-id="086a0-142">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="086a0-143">Atrybuty są ustawiane zgodnie z wymaganiami sekcji.</span><span class="sxs-lookup"><span data-stu-id="086a0-143">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="086a0-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="086a0-144">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="086a0-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="086a0-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
