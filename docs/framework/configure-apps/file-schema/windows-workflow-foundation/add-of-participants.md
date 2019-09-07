---
title: <add> dla <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: 479430abd06561cc294b3da3d0922b737364b50f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398933"
---
# <a name="add-of-participants"></a><span data-ttu-id="35ba9-102">\<Dodaj > \<uczestników ></span><span class="sxs-lookup"><span data-stu-id="35ba9-102">\<add> of \<participants></span></span>
<span data-ttu-id="35ba9-103">Konfigurowanie śledzenia uczestnika nasłuchujący rekordów śledzenia jest emitowane bezpośrednio ze środowiska wykonawczego i przetworzyć je w sposób został skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="35ba9-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="35ba9-104">Dotyczy to również zapis do określonych danych wyjściowych (np. PLik, konsoli, ETW), przetwarzania/agregowania rekordy lub dowolną kombinację, który może być wymagane.</span><span class="sxs-lookup"><span data-stu-id="35ba9-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="35ba9-105">Aby uzyskać więcej informacji o śledzeniu i śledzeniu przepływów pracy, zobacz [śledzenie przepływu pracy i](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) śledzenie i [Śledzenie uczestników](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="35ba9-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="35ba9-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="35ba9-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="35ba9-107">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="35ba9-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="35ba9-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="35ba9-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="35ba9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Uczestnicy >** ](participants.md)</span><span class="sxs-lookup"><span data-stu-id="35ba9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participants>**](participants.md)</span></span>\
<span data-ttu-id="35ba9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="35ba9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35ba9-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="35ba9-111">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35ba9-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="35ba9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="35ba9-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="35ba9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35ba9-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="35ba9-114">Attributes</span></span>  
  
|<span data-ttu-id="35ba9-115">Element</span><span class="sxs-lookup"><span data-stu-id="35ba9-115">Element</span></span>|<span data-ttu-id="35ba9-116">Opis</span><span class="sxs-lookup"><span data-stu-id="35ba9-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="35ba9-117">nazwa</span><span class="sxs-lookup"><span data-stu-id="35ba9-117">name</span></span>|<span data-ttu-id="35ba9-118">Ciąg określający nazwę uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="35ba9-118">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="35ba9-119">Nazwa_profilu</span><span class="sxs-lookup"><span data-stu-id="35ba9-119">profileName</span></span>|<span data-ttu-id="35ba9-120">Ciąg określający nazwę profilu śledzenia, który definiuje rekordów śledzenia uczestnika śledzenia ma subskrypcję.</span><span class="sxs-lookup"><span data-stu-id="35ba9-120">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="35ba9-121">— typ</span><span class="sxs-lookup"><span data-stu-id="35ba9-121">type</span></span>|<span data-ttu-id="35ba9-122">Ciąg, który określa typ uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="35ba9-122">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35ba9-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="35ba9-123">Child Elements</span></span>  
 <span data-ttu-id="35ba9-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="35ba9-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35ba9-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="35ba9-125">Parent Elements</span></span>  
  
|<span data-ttu-id="35ba9-126">Element</span><span class="sxs-lookup"><span data-stu-id="35ba9-126">Element</span></span>|<span data-ttu-id="35ba9-127">Opis</span><span class="sxs-lookup"><span data-stu-id="35ba9-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35ba9-128">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="35ba9-128">\<participants></span></span>](participants.md)|<span data-ttu-id="35ba9-129">Lista śledzenia uczestników</span><span class="sxs-lookup"><span data-stu-id="35ba9-129">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35ba9-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35ba9-130">Remarks</span></span>  
 <span data-ttu-id="35ba9-131">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="35ba9-131">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="35ba9-132">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="35ba9-132">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="35ba9-133">Wiele uczestników śledzenia może jednocześnie używać zdarzeń śledzenia.</span><span class="sxs-lookup"><span data-stu-id="35ba9-133">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="35ba9-134">Uczestnik śledzenia mogą być skojarzone z profilem różnych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="35ba9-134">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="35ba9-135">Standardowe śledzenia uczestnika, który jest podawany jako który zapisuje rekordy śledzenia sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="35ba9-135">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="35ba9-136">Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="35ba9-136">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="35ba9-137">Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="35ba9-137">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="35ba9-138">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="35ba9-138">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35ba9-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="35ba9-139">Example</span></span>  
 <span data-ttu-id="35ba9-140">Poniższy przykład konfiguracji przedstawia standardowy Uczestnik śledzenia ETW skonfigurowany w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="35ba9-140">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="35ba9-141">Identyfikator dostawcy, którego Uczestnik śledzenia funkcji ETW używa do zapisywania rekordów śledzenia w funkcji ETW,  **\<** jest zdefiniowany w sekcji > diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="35ba9-141">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="35ba9-142">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="35ba9-142">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="35ba9-143">Jest on definiowany przez  **\<** atrybut **ProfileName** elementu Add >.</span><span class="sxs-lookup"><span data-stu-id="35ba9-143">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="35ba9-144">Po ich zdefiniowaniu Uczestnik śledzenia zostanie dodany do  **\<zachowania usługi etwTracking >** .</span><span class="sxs-lookup"><span data-stu-id="35ba9-144">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="35ba9-145">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="35ba9-145">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="35ba9-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35ba9-146">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="35ba9-147">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="35ba9-147">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="35ba9-148">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="35ba9-148">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
