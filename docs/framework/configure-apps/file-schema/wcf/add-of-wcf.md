---
title: <add>programu WCF
ms.date: 03/30/2017
ms.assetid: c196f6d7-77f6-4266-973c-305b2b4dd8a2
ms.openlocfilehash: 0b21bdabc76ec4853a0f2664cdd3cead149417a1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850299"
---
# <a name="add-of-wcf"></a><span data-ttu-id="66e97-102">\<Dodawanie > WCF</span><span class="sxs-lookup"><span data-stu-id="66e97-102">\<add> of WCF</span></span>
<span data-ttu-id="66e97-103">Konfigurowanie śledzenia uczestnika nasłuchujący rekordów śledzenia jest emitowane bezpośrednio ze środowiska wykonawczego i przetworzyć je w sposób został skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="66e97-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="66e97-104">Dotyczy to również zapis do określonych danych wyjściowych (np. PLik, konsoli, ETW), przetwarzania/agregowania rekordy lub dowolną kombinację, który może być wymagane.</span><span class="sxs-lookup"><span data-stu-id="66e97-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="66e97-105">Aby uzyskać więcej informacji o śledzeniu i śledzeniu przepływów pracy, zobacz [śledzenie przepływu pracy i](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) śledzenie i [Śledzenie uczestników](../../../windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="66e97-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="66e97-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="66e97-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="66e97-107">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="66e97-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="66e97-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="66e97-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="66e97-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Uczestnicy >** ](participants-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="66e97-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participants>**](participants-of-wcf.md)</span></span>\
<span data-ttu-id="66e97-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="66e97-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e97-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="66e97-111">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66e97-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="66e97-112">Attributes and Elements</span></span>  
 <span data-ttu-id="66e97-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="66e97-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66e97-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="66e97-114">Attributes</span></span>  
  
|<span data-ttu-id="66e97-115">Element</span><span class="sxs-lookup"><span data-stu-id="66e97-115">Element</span></span>|<span data-ttu-id="66e97-116">Opis</span><span class="sxs-lookup"><span data-stu-id="66e97-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="66e97-117">nazwa</span><span class="sxs-lookup"><span data-stu-id="66e97-117">name</span></span>|<span data-ttu-id="66e97-118">Ciąg określający nazwę uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="66e97-118">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="66e97-119">Nazwa_profilu</span><span class="sxs-lookup"><span data-stu-id="66e97-119">profileName</span></span>|<span data-ttu-id="66e97-120">Ciąg określający nazwę profilu śledzenia, który definiuje rekordów śledzenia uczestnika śledzenia ma subskrypcję.</span><span class="sxs-lookup"><span data-stu-id="66e97-120">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="66e97-121">— typ</span><span class="sxs-lookup"><span data-stu-id="66e97-121">type</span></span>|<span data-ttu-id="66e97-122">Ciąg, który określa typ uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="66e97-122">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66e97-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="66e97-123">Child Elements</span></span>  
 <span data-ttu-id="66e97-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="66e97-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66e97-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="66e97-125">Parent Elements</span></span>  
  
|<span data-ttu-id="66e97-126">Element</span><span class="sxs-lookup"><span data-stu-id="66e97-126">Element</span></span>|<span data-ttu-id="66e97-127">Opis</span><span class="sxs-lookup"><span data-stu-id="66e97-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66e97-128">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="66e97-128">\<participants></span></span>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="66e97-129">Lista śledzenia uczestników</span><span class="sxs-lookup"><span data-stu-id="66e97-129">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66e97-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66e97-130">Remarks</span></span>  
 <span data-ttu-id="66e97-131">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="66e97-131">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="66e97-132">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="66e97-132">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="66e97-133">Wiele uczestników śledzenia może jednocześnie używać zdarzeń śledzenia.</span><span class="sxs-lookup"><span data-stu-id="66e97-133">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="66e97-134">Uczestnik śledzenia mogą być skojarzone z profilem różnych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="66e97-134">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="66e97-135">Standardowe śledzenia uczestnika, który jest podawany jako który zapisuje rekordy śledzenia sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="66e97-135">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="66e97-136">Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="66e97-136">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="66e97-137">Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="66e97-137">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="66e97-138">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="66e97-138">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66e97-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="66e97-139">Example</span></span>  
 <span data-ttu-id="66e97-140">Poniższy przykład konfiguracji przedstawia standardowy Uczestnik śledzenia ETW skonfigurowany w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="66e97-140">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="66e97-141">Identyfikator dostawcy, który używa uczestnika śledzenia zdarzeń systemu Windows do zapisywania rekordów śledzenia zdarzeń systemu Windows jest zdefiniowany w `<diagnostics>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="66e97-141">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="66e97-142">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="66e97-142">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="66e97-143">To jest definiowana za pomocą `profileName` atrybutu `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="66e97-143">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="66e97-144">Te po zdefiniowaniu, śledzenie uczestnika zostanie dodany do `<etwTracking>` usługi zachowanie.</span><span class="sxs-lookup"><span data-stu-id="66e97-144">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="66e97-145">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="66e97-145">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="66e97-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66e97-146">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="66e97-147">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="66e97-147">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="66e97-148">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="66e97-148">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
