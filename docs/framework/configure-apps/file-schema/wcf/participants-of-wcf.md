---
title: <participants>programu WCF
ms.date: 03/30/2017
ms.assetid: d99dbddc-0057-4e18-8e42-f91411d39970
ms.openlocfilehash: 35ed7a49967143838a6f74c51e77c553817bd09a
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855081"
---
# <a name="participants-of-wcf"></a><span data-ttu-id="12740-102">\<Uczestnicy > WCF</span><span class="sxs-lookup"><span data-stu-id="12740-102">\<participants> of WCF</span></span>
<span data-ttu-id="12740-103">Skonfiguruj listę śledzenia uczestników, które będą wysyłane do śledzenia rekordów jest emitowane bezpośrednio ze środowiska wykonawczego i przetwórz je w sposób są skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="12740-103">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="12740-104">Dotyczy to również zapis do określonych danych wyjściowych (np. PLik, konsoli, ETW), przetwarzania/agregowania rekordy lub dowolną kombinację, który może być wymagane.</span><span class="sxs-lookup"><span data-stu-id="12740-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
<span data-ttu-id="12740-105">Aby uzyskać więcej informacji o śledzeniu i śledzeniu przepływów pracy, zobacz [śledzenie przepływu pracy i](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) śledzenie i [Śledzenie uczestników](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="12740-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="12740-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="12740-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="12740-107">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="12740-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="12740-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="12740-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>  
<span data-ttu-id="12740-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Uczestnicy >**</span><span class="sxs-lookup"><span data-stu-id="12740-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12740-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="12740-110">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12740-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="12740-111">Attributes and Elements</span></span>  
 <span data-ttu-id="12740-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="12740-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12740-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="12740-113">Attributes</span></span>  
 <span data-ttu-id="12740-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="12740-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="12740-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="12740-115">Child Elements</span></span>  
  
|<span data-ttu-id="12740-116">Element</span><span class="sxs-lookup"><span data-stu-id="12740-116">Element</span></span>|<span data-ttu-id="12740-117">Opis</span><span class="sxs-lookup"><span data-stu-id="12740-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12740-118">\<add></span><span class="sxs-lookup"><span data-stu-id="12740-118">\<add></span></span>](../windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="12740-119">Zawiera ustawienia dla uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="12740-119">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12740-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="12740-120">Parent Elements</span></span>  
  
|<span data-ttu-id="12740-121">Element</span><span class="sxs-lookup"><span data-stu-id="12740-121">Element</span></span>|<span data-ttu-id="12740-122">Opis</span><span class="sxs-lookup"><span data-stu-id="12740-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12740-123">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="12740-123">\<tracking></span></span>](../windows-workflow-foundation/tracking.md)|<span data-ttu-id="12740-124">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="12740-124">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12740-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="12740-125">Remarks</span></span>  
 <span data-ttu-id="12740-126">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="12740-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="12740-127">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="12740-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="12740-128">Wiele uczestników śledzenia może jednocześnie używać zdarzeń śledzenia.</span><span class="sxs-lookup"><span data-stu-id="12740-128">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="12740-129">Uczestnik śledzenia mogą być skojarzone z profilem różnych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="12740-129">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="12740-130">Standardowe śledzenia uczestnika, który jest podawany jako który zapisuje rekordy śledzenia sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="12740-130">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="12740-131">Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="12740-131">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="12740-132">Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="12740-132">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="12740-133">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="12740-133">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12740-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="12740-134">Example</span></span>  
 <span data-ttu-id="12740-135">Poniższy przykład konfiguracji przedstawia standardowy Uczestnik śledzenia ETW skonfigurowany w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="12740-135">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="12740-136">Identyfikator dostawcy, który używa uczestnika śledzenia zdarzeń systemu Windows do zapisywania rekordów śledzenia zdarzeń systemu Windows jest zdefiniowany w `<diagnostics>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="12740-136">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="12740-137">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="12740-137">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="12740-138">To jest definiowana za pomocą `profileName` atrybutu `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="12740-138">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="12740-139">Te po zdefiniowaniu, śledzenie uczestnika zostanie dodany do `<etwTracking>` usługi zachowanie.</span><span class="sxs-lookup"><span data-stu-id="12740-139">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="12740-140">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="12740-140">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12740-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12740-141">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- [<span data-ttu-id="12740-142">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="12740-142">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="12740-143">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="12740-143">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
