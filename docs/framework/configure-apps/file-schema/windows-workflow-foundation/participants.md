---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: f04a5ee3940986cabc08895452c12ebcfd631694
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947568"
---
# <a name="participants"></a><span data-ttu-id="af251-101">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="af251-101">\<participants></span></span>
<span data-ttu-id="af251-102">Skonfiguruj listę śledzenia uczestników, które będą wysyłane do śledzenia rekordów jest emitowane bezpośrednio ze środowiska wykonawczego i przetwórz je w sposób są skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="af251-102">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="af251-103">Dotyczy to również zapis do określonych danych wyjściowych (np. PLik, konsoli, ETW), przetwarzania/agregowania rekordy lub dowolną kombinację, który może być wymagane.</span><span class="sxs-lookup"><span data-stu-id="af251-103">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="af251-104">Aby uzyskać więcej informacji o śledzeniu i śledzeniu przepływów pracy, zobacz [śledzenie przepływu pracy i](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) śledzenie i [Śledzenie uczestników](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="af251-104">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="af251-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="af251-105">\<system.serviceModel></span></span>  
<span data-ttu-id="af251-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="af251-106">\<tracking></span></span>  
<span data-ttu-id="af251-107">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="af251-107">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af251-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="af251-108">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af251-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="af251-109">Attributes and Elements</span></span>  
 <span data-ttu-id="af251-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="af251-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af251-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="af251-111">Attributes</span></span>  
 <span data-ttu-id="af251-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="af251-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="af251-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="af251-113">Child Elements</span></span>  
  
|<span data-ttu-id="af251-114">Element</span><span class="sxs-lookup"><span data-stu-id="af251-114">Element</span></span>|<span data-ttu-id="af251-115">Opis</span><span class="sxs-lookup"><span data-stu-id="af251-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af251-116">\<add></span><span class="sxs-lookup"><span data-stu-id="af251-116">\<add></span></span>](add-of-participants.md)|<span data-ttu-id="af251-117">Zawiera ustawienia dla uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="af251-117">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="af251-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="af251-118">Parent Elements</span></span>  
  
|<span data-ttu-id="af251-119">Element</span><span class="sxs-lookup"><span data-stu-id="af251-119">Element</span></span>|<span data-ttu-id="af251-120">Opis</span><span class="sxs-lookup"><span data-stu-id="af251-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af251-121">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="af251-121">\<tracking></span></span>](tracking.md)|<span data-ttu-id="af251-122">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="af251-122">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af251-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af251-123">Remarks</span></span>  
 <span data-ttu-id="af251-124">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="af251-124">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="af251-125">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="af251-125">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="af251-126">Wiele uczestników śledzenia może jednocześnie używać zdarzeń śledzenia.</span><span class="sxs-lookup"><span data-stu-id="af251-126">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="af251-127">Uczestnik śledzenia mogą być skojarzone z profilem różnych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="af251-127">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="af251-128">Standardowe śledzenia uczestnika, który jest podawany jako który zapisuje rekordy śledzenia sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="af251-128">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="af251-129">Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="af251-129">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="af251-130">Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af251-130">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="af251-131">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="af251-131">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af251-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="af251-132">Example</span></span>  
 <span data-ttu-id="af251-133">Poniższy przykład konfiguracji przedstawia standardowy Uczestnik śledzenia ETW skonfigurowany w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="af251-133">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="af251-134">Identyfikator dostawcy, którego Uczestnik śledzenia funkcji ETW używa do zapisywania rekordów śledzenia w funkcji ETW,  **\<** jest zdefiniowany w sekcji > diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="af251-134">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="af251-135">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="af251-135">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="af251-136">Jest on definiowany przez atrybut  **\<** ProfileName elementu Add >.</span><span class="sxs-lookup"><span data-stu-id="af251-136">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="af251-137">Po ich zdefiniowaniu Uczestnik śledzenia zostanie dodany do  **\<zachowania usługi etwTracking >** .</span><span class="sxs-lookup"><span data-stu-id="af251-137">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="af251-138">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="af251-138">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="af251-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af251-139">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="af251-140">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="af251-140">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="af251-141">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="af251-141">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
