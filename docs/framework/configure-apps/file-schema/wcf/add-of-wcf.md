---
title: <add> w WCF
ms.date: 03/30/2017
ms.assetid: c196f6d7-77f6-4266-973c-305b2b4dd8a2
ms.openlocfilehash: e9ece03ec9376e6a428ac6a82a3f26020f64d744
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673852"
---
# <a name="add-of-wcf"></a><span data-ttu-id="00eac-102">\<Dodaj > w WCF</span><span class="sxs-lookup"><span data-stu-id="00eac-102">\<add> of WCF</span></span>
<span data-ttu-id="00eac-103">Konfigurowanie śledzenia uczestnika nasłuchujący rekordów śledzenia jest emitowane bezpośrednio ze środowiska wykonawczego i przetworzyć je w sposób został skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="00eac-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="00eac-104">Dotyczy to również zapis do określonych danych wyjściowych (np. PLik, konsoli, ETW), przetwarzania/agregowania rekordy lub dowolną kombinację, który może być wymagane.</span><span class="sxs-lookup"><span data-stu-id="00eac-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="00eac-105">Aby uzyskać więcej informacji śledzenia przepływu pracy i śledzenia uczestników, zobacz [przepływu pracy i śledzenie](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [uczestników śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="00eac-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 <span data-ttu-id="00eac-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="00eac-106">\<system.serviceModel></span></span>  
<span data-ttu-id="00eac-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="00eac-107">\<tracking></span></span>  
<span data-ttu-id="00eac-108">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="00eac-108">\<participants></span></span>  
<span data-ttu-id="00eac-109">\<add></span><span class="sxs-lookup"><span data-stu-id="00eac-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00eac-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="00eac-110">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00eac-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="00eac-111">Attributes and Elements</span></span>  
 <span data-ttu-id="00eac-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="00eac-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00eac-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="00eac-113">Attributes</span></span>  
  
|<span data-ttu-id="00eac-114">Element</span><span class="sxs-lookup"><span data-stu-id="00eac-114">Element</span></span>|<span data-ttu-id="00eac-115">Opis</span><span class="sxs-lookup"><span data-stu-id="00eac-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="00eac-116">nazwa</span><span class="sxs-lookup"><span data-stu-id="00eac-116">name</span></span>|<span data-ttu-id="00eac-117">Ciąg określający nazwę uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="00eac-117">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="00eac-118">Nazwa_profilu</span><span class="sxs-lookup"><span data-stu-id="00eac-118">profileName</span></span>|<span data-ttu-id="00eac-119">Ciąg określający nazwę profilu śledzenia, który definiuje rekordów śledzenia uczestnika śledzenia ma subskrypcję.</span><span class="sxs-lookup"><span data-stu-id="00eac-119">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="00eac-120">— typ</span><span class="sxs-lookup"><span data-stu-id="00eac-120">type</span></span>|<span data-ttu-id="00eac-121">Ciąg, który określa typ uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="00eac-121">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00eac-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="00eac-122">Child Elements</span></span>  
 <span data-ttu-id="00eac-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="00eac-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00eac-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="00eac-124">Parent Elements</span></span>  
  
|<span data-ttu-id="00eac-125">Element</span><span class="sxs-lookup"><span data-stu-id="00eac-125">Element</span></span>|<span data-ttu-id="00eac-126">Opis</span><span class="sxs-lookup"><span data-stu-id="00eac-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00eac-127">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="00eac-127">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|<span data-ttu-id="00eac-128">Lista śledzenia uczestników</span><span class="sxs-lookup"><span data-stu-id="00eac-128">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00eac-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00eac-129">Remarks</span></span>  
 <span data-ttu-id="00eac-130">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="00eac-130">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="00eac-131">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="00eac-131">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="00eac-132">Wiele uczestników śledzenia mogą wykorzystywać jednocześnie zdarzeń śledzenia.</span><span class="sxs-lookup"><span data-stu-id="00eac-132">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="00eac-133">Uczestnik śledzenia mogą być skojarzone z profilem różnych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="00eac-133">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="00eac-134">Standardowe śledzenia uczestnika, który jest podawany jako który zapisuje rekordy śledzenia sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="00eac-134">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="00eac-135">Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="00eac-135">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="00eac-136">Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="00eac-136">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="00eac-137">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="00eac-137">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00eac-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="00eac-138">Example</span></span>  
 <span data-ttu-id="00eac-139">W poniższym przykładzie konfiguracji zawiera standardowe uczestnika śledzenia zdarzeń systemu Windows jest skonfigurowany w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="00eac-139">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="00eac-140">Identyfikator dostawcy, który używa uczestnika śledzenia zdarzeń systemu Windows do zapisywania rekordów śledzenia zdarzeń systemu Windows jest zdefiniowany w `<diagnostics>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="00eac-140">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="00eac-141">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="00eac-141">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="00eac-142">To jest definiowana za pomocą `profileName` atrybutu `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="00eac-142">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="00eac-143">Te po zdefiniowaniu, śledzenie uczestnika zostanie dodany do `<etwTracking>` usługi zachowanie.</span><span class="sxs-lookup"><span data-stu-id="00eac-143">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="00eac-144">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="00eac-144">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0" />
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile" />
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="00eac-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00eac-145">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="00eac-146">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="00eac-146">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="00eac-147">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="00eac-147">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
