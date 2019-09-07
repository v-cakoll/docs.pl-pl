---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: 368b37f3ff10b660260ddd5735c70b8d72063e11
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398710"
---
# <a name="participants"></a><span data-ttu-id="2c91f-101">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="2c91f-101">\<participants></span></span>
<span data-ttu-id="2c91f-102">Skonfiguruj listę śledzenia uczestników, które będą wysyłane do śledzenia rekordów jest emitowane bezpośrednio ze środowiska wykonawczego i przetwórz je w sposób są skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="2c91f-102">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="2c91f-103">Dotyczy to również zapis do określonych danych wyjściowych (np. PLik, konsoli, ETW), przetwarzania/agregowania rekordy lub dowolną kombinację, który może być wymagane.</span><span class="sxs-lookup"><span data-stu-id="2c91f-103">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="2c91f-104">Aby uzyskać więcej informacji o śledzeniu i śledzeniu przepływów pracy, zobacz [śledzenie przepływu pracy i](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) śledzenie i [Śledzenie uczestników](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="2c91f-104">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="2c91f-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2c91f-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2c91f-106">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="2c91f-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="2c91f-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="2c91f-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="2c91f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Uczestnicy >**</span><span class="sxs-lookup"><span data-stu-id="2c91f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c91f-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c91f-109">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c91f-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2c91f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2c91f-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2c91f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c91f-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2c91f-112">Attributes</span></span>  
 <span data-ttu-id="2c91f-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="2c91f-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2c91f-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2c91f-114">Child Elements</span></span>  
  
|<span data-ttu-id="2c91f-115">Element</span><span class="sxs-lookup"><span data-stu-id="2c91f-115">Element</span></span>|<span data-ttu-id="2c91f-116">Opis</span><span class="sxs-lookup"><span data-stu-id="2c91f-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c91f-117">\<add></span><span class="sxs-lookup"><span data-stu-id="2c91f-117">\<add></span></span>](add-of-participants.md)|<span data-ttu-id="2c91f-118">Zawiera ustawienia dla uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2c91f-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c91f-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2c91f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2c91f-120">Element</span><span class="sxs-lookup"><span data-stu-id="2c91f-120">Element</span></span>|<span data-ttu-id="2c91f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="2c91f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c91f-122">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="2c91f-122">\<tracking></span></span>](tracking.md)|<span data-ttu-id="2c91f-123">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2c91f-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c91f-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c91f-124">Remarks</span></span>  
 <span data-ttu-id="2c91f-125">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="2c91f-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="2c91f-126">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2c91f-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="2c91f-127">Wiele uczestników śledzenia może jednocześnie używać zdarzeń śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2c91f-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="2c91f-128">Uczestnik śledzenia mogą być skojarzone z profilem różnych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2c91f-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="2c91f-129">Standardowe śledzenia uczestnika, który jest podawany jako który zapisuje rekordy śledzenia sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="2c91f-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="2c91f-130">Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2c91f-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="2c91f-131">Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2c91f-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="2c91f-132">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2c91f-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c91f-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c91f-133">Example</span></span>  
 <span data-ttu-id="2c91f-134">Poniższy przykład konfiguracji przedstawia standardowy Uczestnik śledzenia ETW skonfigurowany w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="2c91f-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="2c91f-135">Identyfikator dostawcy, którego Uczestnik śledzenia funkcji ETW używa do zapisywania rekordów śledzenia w funkcji ETW,  **\<** jest zdefiniowany w sekcji > diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="2c91f-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="2c91f-136">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2c91f-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="2c91f-137">Jest on definiowany przez  **\<** atrybut **ProfileName** elementu Add >.</span><span class="sxs-lookup"><span data-stu-id="2c91f-137">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="2c91f-138">Po ich zdefiniowaniu Uczestnik śledzenia zostanie dodany do  **\<zachowania usługi etwTracking >** .</span><span class="sxs-lookup"><span data-stu-id="2c91f-138">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="2c91f-139">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2c91f-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c91f-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c91f-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="2c91f-141">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="2c91f-141">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2c91f-142">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="2c91f-142">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
