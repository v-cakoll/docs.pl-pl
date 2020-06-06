---
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 2749bc6c66d491a8a160d98b508fb43aa027b806
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398041"
---
# \<diagnostics>
<span data-ttu-id="d5100-101">`diagnostics`Element definiuje ustawienia, które mogą być używane przez administratora na potrzeby inspekcji i kontroli w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d5100-101">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="d5100-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5100-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5100-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d5100-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d5100-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d5100-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5100-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d5100-105">Attributes</span></span>  
  
|<span data-ttu-id="d5100-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d5100-106">Attribute</span></span>|<span data-ttu-id="d5100-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d5100-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d5100-108">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="d5100-108">etwProviderId</span></span>|<span data-ttu-id="d5100-109">Ciąg określający identyfikator dostawcy śledzenia zdarzeń, który zapisuje zdarzenia do sesji ETW.</span><span class="sxs-lookup"><span data-stu-id="d5100-109">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="d5100-110">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="d5100-110">performanceCounters</span></span>|<span data-ttu-id="d5100-111">Określa, czy są włączone liczniki wydajności dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="d5100-111">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="d5100-112">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="d5100-112">Valid values are</span></span><br /><br /> <span data-ttu-id="d5100-113">-Off: Liczniki wydajności są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="d5100-113">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="d5100-114">-Tylko do-Service: włączono tylko liczniki wydajności odpowiednie dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="d5100-114">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="d5100-115">-All: Liczniki wydajności mogą być wyświetlane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d5100-115">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="d5100-116">-Domyślnie: utworzono pojedyncze wystąpienie licznika wydajności _WCF_Admin.</span><span class="sxs-lookup"><span data-stu-id="d5100-116">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="d5100-117">To wystąpienie jest używane do włączania zbierania danych SQM używanych przez infrastrukturę.</span><span class="sxs-lookup"><span data-stu-id="d5100-117">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="d5100-118">Żadna z wartości licznika dla tego wystąpienia nie jest aktualizowana i w związku z tym pozostanie równa zero.</span><span class="sxs-lookup"><span data-stu-id="d5100-118">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="d5100-119">Jest to wartość domyślna, jeśli żadna konfiguracja nie jest obecna dla programu WCF.</span><span class="sxs-lookup"><span data-stu-id="d5100-119">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="d5100-120">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="d5100-120">wmiProviderEnabled</span></span>|<span data-ttu-id="d5100-121">Wartość logiczna określająca, czy dostawca WMI dla zestawu jest włączony.</span><span class="sxs-lookup"><span data-stu-id="d5100-121">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="d5100-122">Dostawca WMI jest wymagany, aby użytkownik mógł uzyskać dostęp do funkcji inspekcji i kontroli programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d5100-122">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="d5100-123">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="d5100-123">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5100-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d5100-124">Child Elements</span></span>  
  
|<span data-ttu-id="d5100-125">Element</span><span class="sxs-lookup"><span data-stu-id="d5100-125">Element</span></span>|<span data-ttu-id="d5100-126">Opis</span><span class="sxs-lookup"><span data-stu-id="d5100-126">Description</span></span>|  
|-------------|-----------------|  
|[\<endToEndTracing>](endtoendtracing.md)|<span data-ttu-id="d5100-127">Element konfiguracji, który pozwala na włączenie i wyłączenie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="d5100-127">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[\<messageLogging>](messagelogging.md)|<span data-ttu-id="d5100-128">Opisuje ustawienia rejestrowania komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="d5100-128">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d5100-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d5100-129">Parent Elements</span></span>  
  
|<span data-ttu-id="d5100-130">Element</span><span class="sxs-lookup"><span data-stu-id="d5100-130">Element</span></span>|<span data-ttu-id="d5100-131">Opis</span><span class="sxs-lookup"><span data-stu-id="d5100-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d5100-132">Modelu</span><span class="sxs-lookup"><span data-stu-id="d5100-132">serviceModel</span></span>|<span data-ttu-id="d5100-133">Element główny wszystkich elementów konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="d5100-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5100-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5100-134">Remarks</span></span>  
 <span data-ttu-id="d5100-135">`diagnostics`Sekcja definiuje ustawienia diagnostyki dla wszystkich usług znajdujących się w zestawie.</span><span class="sxs-lookup"><span data-stu-id="d5100-135">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="d5100-136">Nie można definiować oddzielnych ustawień diagnostycznych na poziomie usługi, chyba że w zestawie znajduje się tylko jedna usługa.</span><span class="sxs-lookup"><span data-stu-id="d5100-136">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="d5100-137">Atrybuty są ustawiane zgodnie z wymaganiami sekcji.</span><span class="sxs-lookup"><span data-stu-id="d5100-137">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5100-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5100-138">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5100-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5100-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
