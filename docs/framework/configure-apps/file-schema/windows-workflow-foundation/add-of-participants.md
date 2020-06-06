---
title: <add> dla <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: 61832edbf7d206d6a5f7a85619eb17ebc010c193
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152362"
---
# <a name="add-of-participants"></a><span data-ttu-id="e20f5-102">\<add> dla \<participants></span><span class="sxs-lookup"><span data-stu-id="e20f5-102">\<add> of \<participants></span></span>
<span data-ttu-id="e20f5-103">Konfigurowanie śledzenia uczestnika nasłuchujący rekordów śledzenia jest emitowane bezpośrednio ze środowiska wykonawczego i przetworzyć je w sposób został skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="e20f5-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="e20f5-104">Dotyczy to również zapis do określonych danych wyjściowych (np. PLik, konsoli, ETW), przetwarzania/agregowania rekordy lub dowolną kombinację, który może być wymagane.</span><span class="sxs-lookup"><span data-stu-id="e20f5-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="e20f5-105">Aby uzyskać więcej informacji o śledzeniu i śledzeniu przepływów pracy, zobacz [śledzenie przepływu pracy i](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) śledzenie i [Śledzenie uczestników](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="e20f5-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participants>**](participants.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="e20f5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e20f5-106">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e20f5-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e20f5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e20f5-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e20f5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e20f5-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e20f5-109">Attributes</span></span>  
  
|<span data-ttu-id="e20f5-110">Element</span><span class="sxs-lookup"><span data-stu-id="e20f5-110">Element</span></span>|<span data-ttu-id="e20f5-111">Opis</span><span class="sxs-lookup"><span data-stu-id="e20f5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e20f5-112">name</span><span class="sxs-lookup"><span data-stu-id="e20f5-112">name</span></span>|<span data-ttu-id="e20f5-113">Ciąg określający nazwę uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e20f5-113">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="e20f5-114">Nazwa_profilu</span><span class="sxs-lookup"><span data-stu-id="e20f5-114">profileName</span></span>|<span data-ttu-id="e20f5-115">Ciąg określający nazwę profilu śledzenia, który definiuje rekordów śledzenia uczestnika śledzenia ma subskrypcję.</span><span class="sxs-lookup"><span data-stu-id="e20f5-115">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="e20f5-116">typ</span><span class="sxs-lookup"><span data-stu-id="e20f5-116">type</span></span>|<span data-ttu-id="e20f5-117">Ciąg, który określa typ uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e20f5-117">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e20f5-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e20f5-118">Child Elements</span></span>  
 <span data-ttu-id="e20f5-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="e20f5-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e20f5-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e20f5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e20f5-121">Element</span><span class="sxs-lookup"><span data-stu-id="e20f5-121">Element</span></span>|<span data-ttu-id="e20f5-122">Opis</span><span class="sxs-lookup"><span data-stu-id="e20f5-122">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](participants.md)|<span data-ttu-id="e20f5-123">Lista śledzenia uczestników</span><span class="sxs-lookup"><span data-stu-id="e20f5-123">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e20f5-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e20f5-124">Remarks</span></span>  
 <span data-ttu-id="e20f5-125">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="e20f5-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="e20f5-126">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e20f5-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="e20f5-127">Wiele uczestników śledzenia może jednocześnie używać zdarzeń śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e20f5-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="e20f5-128">Uczestnik śledzenia mogą być skojarzone z profilem różnych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e20f5-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="e20f5-129">Standardowe śledzenia uczestnika, który jest podawany jako który zapisuje rekordy śledzenia sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="e20f5-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="e20f5-130">Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e20f5-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="e20f5-131">Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e20f5-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="e20f5-132">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e20f5-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e20f5-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="e20f5-133">Example</span></span>  
 <span data-ttu-id="e20f5-134">Poniższy przykład konfiguracji przedstawia standardowy Uczestnik śledzenia ETW skonfigurowany w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="e20f5-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="e20f5-135">Identyfikator dostawcy, którego Uczestnik śledzenia funkcji ETW używa do zapisywania rekordów śledzenia w funkcji ETW, jest zdefiniowany w **\<diagnostics>** sekcji.</span><span class="sxs-lookup"><span data-stu-id="e20f5-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="e20f5-136">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e20f5-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="e20f5-137">Jest on definiowany przez atrybut **ProfileName** **\<add>** elementu.</span><span class="sxs-lookup"><span data-stu-id="e20f5-137">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="e20f5-138">Po ich zdefiniowaniu Uczestnik śledzenia zostanie dodany do **\<etwTracking>** zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="e20f5-138">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="e20f5-139">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e20f5-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile"/>
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e20f5-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e20f5-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="e20f5-141">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e20f5-141">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e20f5-142">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="e20f5-142">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
