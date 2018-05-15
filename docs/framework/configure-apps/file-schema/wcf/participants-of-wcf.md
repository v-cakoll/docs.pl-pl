---
title: '&lt;participants&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
ms.openlocfilehash: 093ed0ed51c068fe0a999dc5f7b7a3adec39ae77
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltparticipantsgt-of-wcf"></a><span data-ttu-id="9d3dd-102">&lt;participants&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="9d3dd-102">&lt;participants&gt; of WCF</span></span>
<span data-ttu-id="9d3dd-103">Skonfiguruj listę śledzenia uczestników, które będą wysyłane do śledzenia rekordów jest emitowane bezpośrednio ze środowiska wykonawczego i przetwórz je w sposób są skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="9d3dd-104">Dotyczy to również zapis do określonych danych wyjściowych (np. PLik, konsoli, ETW), przetwarzania/agregowania rekordy lub dowolną kombinację, który może być wymagane.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="9d3dd-105">Aby uzyskać więcej informacji śledzenia przepływu pracy i uczestników śledzenia, zobacz [przepływu pracy śledzenia i śledzenia](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [uczestników śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="9d3dd-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 <span data-ttu-id="9d3dd-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9d3dd-106">\<system.serviceModel></span></span>  
<span data-ttu-id="9d3dd-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="9d3dd-107">\<tracking></span></span>  
<span data-ttu-id="9d3dd-108">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="9d3dd-108">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d3dd-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d3dd-109">Syntax</span></span>  
  
```xml
   <tracking>    <participants>       <add name="String"            profileName="String"           type="String" />    </participants> </tracking>   
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d3dd-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9d3dd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9d3dd-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d3dd-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9d3dd-112">Attributes</span></span>  
 <span data-ttu-id="9d3dd-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d3dd-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9d3dd-114">Child Elements</span></span>  
  
|<span data-ttu-id="9d3dd-115">Element</span><span class="sxs-lookup"><span data-stu-id="9d3dd-115">Element</span></span>|<span data-ttu-id="9d3dd-116">Opis</span><span class="sxs-lookup"><span data-stu-id="9d3dd-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d3dd-117">\<add></span><span class="sxs-lookup"><span data-stu-id="9d3dd-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="9d3dd-118">Zawiera ustawienia dla uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d3dd-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9d3dd-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9d3dd-120">Element</span><span class="sxs-lookup"><span data-stu-id="9d3dd-120">Element</span></span>|<span data-ttu-id="9d3dd-121">Opis</span><span class="sxs-lookup"><span data-stu-id="9d3dd-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d3dd-122">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="9d3dd-122">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="9d3dd-123">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d3dd-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d3dd-124">Remarks</span></span>  
 <span data-ttu-id="9d3dd-125">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="9d3dd-126">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="9d3dd-127">Wielu uczestników śledzenia można jednocześnie używać zdarzeń śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="9d3dd-128">Uczestnik śledzenia mogą być skojarzone z profilem różnych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="9d3dd-129">Standardowe śledzenia uczestnika, który jest podawany jako który zapisuje rekordy śledzenia sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="9d3dd-130">Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="9d3dd-131">Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="9d3dd-132">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d3dd-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d3dd-133">Example</span></span>  
 <span data-ttu-id="9d3dd-134">W poniższym przykładzie konfiguracji zawiera standardowe uczestnika śledzenia zdarzeń systemu Windows skonfigurowany w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="9d3dd-135">Identyfikator dostawcy, który używa uczestnika śledzenia zdarzeń systemu Windows do zapisywania rekordów śledzenia zdarzeń systemu Windows jest zdefiniowany w `<diagnostics>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="9d3dd-136">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="9d3dd-137">To jest definiowana za pomocą `profileName` atrybutu `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-137">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="9d3dd-138">Te po zdefiniowaniu, śledzenie uczestnika zostanie dodany do `<etwTracking>` usługi zachowanie.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-138">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="9d3dd-139">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9d3dd-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d3dd-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d3dd-140">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>  
 [<span data-ttu-id="9d3dd-141">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9d3dd-141">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9d3dd-142">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="9d3dd-142">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
