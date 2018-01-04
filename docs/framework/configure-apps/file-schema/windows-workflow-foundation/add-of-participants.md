---
title: "&lt;Dodaj&gt; z &lt;uczestników&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0671f7f792c0b9a54190fa1144fcbe8caf6663e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltparticipantsgt"></a><span data-ttu-id="73a36-102">&lt;Dodaj&gt; z &lt;uczestników&gt;</span><span class="sxs-lookup"><span data-stu-id="73a36-102">&lt;add&gt; of &lt;participants&gt;</span></span>
<span data-ttu-id="73a36-103">Konfigurowanie śledzenia uczestnika nasłuchujący rekordów śledzenia jest emitowane bezpośrednio ze środowiska wykonawczego i przetworzyć je w sposób został skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="73a36-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="73a36-104">Dotyczy to również zapis do określonych danych wyjściowych (np. PLik, konsoli, ETW), przetwarzania/agregowania rekordy lub dowolną kombinację, który może być wymagane.</span><span class="sxs-lookup"><span data-stu-id="73a36-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="73a36-105">Aby uzyskać więcej informacji śledzenia przepływu pracy i uczestników śledzenia, zobacz [przepływu pracy śledzenia i śledzenia](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [uczestników śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="73a36-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="73a36-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="73a36-106">\<system.serviceModel></span></span>  
<span data-ttu-id="73a36-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="73a36-107">\<tracking></span></span>  
<span data-ttu-id="73a36-108">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="73a36-108">\<participants></span></span>  
<span data-ttu-id="73a36-109">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="73a36-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73a36-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="73a36-110">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73a36-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="73a36-111">Attributes and Elements</span></span>  
 <span data-ttu-id="73a36-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="73a36-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73a36-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="73a36-113">Attributes</span></span>  
  
|<span data-ttu-id="73a36-114">Element</span><span class="sxs-lookup"><span data-stu-id="73a36-114">Element</span></span>|<span data-ttu-id="73a36-115">Opis</span><span class="sxs-lookup"><span data-stu-id="73a36-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73a36-116">nazwa</span><span class="sxs-lookup"><span data-stu-id="73a36-116">name</span></span>|<span data-ttu-id="73a36-117">Ciąg określający nazwę uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="73a36-117">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="73a36-118">Nazwa_profilu</span><span class="sxs-lookup"><span data-stu-id="73a36-118">profileName</span></span>|<span data-ttu-id="73a36-119">Ciąg określający nazwę profilu śledzenia, który definiuje rekordów śledzenia uczestnika śledzenia ma subskrypcję.</span><span class="sxs-lookup"><span data-stu-id="73a36-119">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="73a36-120">— typ</span><span class="sxs-lookup"><span data-stu-id="73a36-120">type</span></span>|<span data-ttu-id="73a36-121">Ciąg, który określa typ uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="73a36-121">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73a36-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="73a36-122">Child Elements</span></span>  
 <span data-ttu-id="73a36-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="73a36-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73a36-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="73a36-124">Parent Elements</span></span>  
  
|<span data-ttu-id="73a36-125">Element</span><span class="sxs-lookup"><span data-stu-id="73a36-125">Element</span></span>|<span data-ttu-id="73a36-126">Opis</span><span class="sxs-lookup"><span data-stu-id="73a36-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73a36-127">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="73a36-127">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="73a36-128">Lista śledzenia uczestników</span><span class="sxs-lookup"><span data-stu-id="73a36-128">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73a36-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73a36-129">Remarks</span></span>  
 <span data-ttu-id="73a36-130">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="73a36-130">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="73a36-131">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="73a36-131">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="73a36-132">Wielu uczestników śledzenia można jednocześnie używać zdarzeń śledzenia.</span><span class="sxs-lookup"><span data-stu-id="73a36-132">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="73a36-133">Uczestnik śledzenia mogą być skojarzone z profilem różnych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="73a36-133">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="73a36-134">Standardowe śledzenia uczestnika, który jest podawany jako który zapisuje rekordy śledzenia sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="73a36-134">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="73a36-135">Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="73a36-135">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="73a36-136">Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="73a36-136">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="73a36-137">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="73a36-137">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73a36-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="73a36-138">Example</span></span>  
 <span data-ttu-id="73a36-139">W poniższym przykładzie konfiguracji zawiera standardowe uczestnika śledzenia zdarzeń systemu Windows skonfigurowany w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="73a36-139">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="73a36-140">Identyfikator dostawcy, używanego przez uczestnika śledzenia zdarzeń systemu Windows do zapisywania rekordów śledzenia zdarzeń systemu Windows jest zdefiniowany w  **\<diagnostyki >** sekcji.</span><span class="sxs-lookup"><span data-stu-id="73a36-140">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="73a36-141">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="73a36-141">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="73a36-142">To jest definiowana za pomocą **profileName** atrybutu  **\<Dodaj >** elementu.</span><span class="sxs-lookup"><span data-stu-id="73a36-142">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="73a36-143">Gdy są one zdefiniowane uczestnika śledzenia jest dodawany do  **\<etwTracking >** zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="73a36-143">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="73a36-144">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="73a36-144">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73a36-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73a36-145">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>  
 [<span data-ttu-id="73a36-146">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="73a36-146">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="73a36-147">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="73a36-147">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
