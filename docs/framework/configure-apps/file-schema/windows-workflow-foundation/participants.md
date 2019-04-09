---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: ffc16f78b266b69e80023f177f10ad6f367b5623
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104887"
---
# <a name="participants"></a><span data-ttu-id="06782-101">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="06782-101">\<participants></span></span>
<span data-ttu-id="06782-102">Skonfiguruj listę śledzenia uczestników, które będą wysyłane do śledzenia rekordów jest emitowane bezpośrednio ze środowiska wykonawczego i przetwórz je w sposób są skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="06782-102">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="06782-103">Dotyczy to również zapis do określonych danych wyjściowych (np. PLik, konsoli, ETW), przetwarzania/agregowania rekordy lub dowolną kombinację, który może być wymagane.</span><span class="sxs-lookup"><span data-stu-id="06782-103">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="06782-104">Aby uzyskać więcej informacji śledzenia przepływu pracy i śledzenia uczestników, zobacz [przepływu pracy i śledzenie](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [uczestników śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span><span class="sxs-lookup"><span data-stu-id="06782-104">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="06782-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="06782-105">\<system.serviceModel></span></span>  
<span data-ttu-id="06782-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="06782-106">\<tracking></span></span>  
<span data-ttu-id="06782-107">\<Uczestnicy ></span><span class="sxs-lookup"><span data-stu-id="06782-107">\<participants></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06782-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="06782-108">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06782-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="06782-109">Attributes and Elements</span></span>  
 <span data-ttu-id="06782-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="06782-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06782-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="06782-111">Attributes</span></span>  
 <span data-ttu-id="06782-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="06782-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="06782-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="06782-113">Child Elements</span></span>  
  
|<span data-ttu-id="06782-114">Element</span><span class="sxs-lookup"><span data-stu-id="06782-114">Element</span></span>|<span data-ttu-id="06782-115">Opis</span><span class="sxs-lookup"><span data-stu-id="06782-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06782-116">\<add></span><span class="sxs-lookup"><span data-stu-id="06782-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/add-of-participants.md)|<span data-ttu-id="06782-117">Zawiera ustawienia dla uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="06782-117">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06782-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="06782-118">Parent Elements</span></span>  
  
|<span data-ttu-id="06782-119">Element</span><span class="sxs-lookup"><span data-stu-id="06782-119">Element</span></span>|<span data-ttu-id="06782-120">Opis</span><span class="sxs-lookup"><span data-stu-id="06782-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06782-121">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="06782-121">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/tracking.md)|<span data-ttu-id="06782-122">Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="06782-122">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06782-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06782-123">Remarks</span></span>  
 <span data-ttu-id="06782-124">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="06782-124">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="06782-125">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="06782-125">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="06782-126">Wiele uczestników śledzenia mogą wykorzystywać jednocześnie zdarzeń śledzenia.</span><span class="sxs-lookup"><span data-stu-id="06782-126">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="06782-127">Uczestnik śledzenia mogą być skojarzone z profilem różnych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="06782-127">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="06782-128">Standardowe śledzenia uczestnika, który jest podawany jako który zapisuje rekordy śledzenia sesji funkcji ETW.</span><span class="sxs-lookup"><span data-stu-id="06782-128">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="06782-129">Uczestnika jest skonfigurowany w usłudze przepływu pracy przez dodanie zachowania specyficzny dla śledzenia w PLiku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="06782-129">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="06782-130">Włączanie funkcji ETW śledzenia uczestnika, który umożliwia śledzenia się wyświetlić podglądu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="06782-130">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="06782-131">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="06782-131">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06782-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="06782-132">Example</span></span>  
 <span data-ttu-id="06782-133">W poniższym przykładzie konfiguracji zawiera standardowe uczestnika śledzenia zdarzeń systemu Windows jest skonfigurowany w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="06782-133">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="06782-134">Identyfikator dostawcy, który używa uczestnika śledzenia zdarzeń systemu Windows, do zapisywania rekordów śledzenia zdarzeń systemu Windows jest zdefiniowany w  **\<Diagnostyka >** sekcji.</span><span class="sxs-lookup"><span data-stu-id="06782-134">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="06782-135">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="06782-135">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="06782-136">To jest definiowana za **profileName** atrybutu  **\<Dodaj >** elementu.</span><span class="sxs-lookup"><span data-stu-id="06782-136">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="06782-137">Te po zdefiniowaniu, śledzenie uczestnika zostanie dodany do  **\<etwTracking >** usługi zachowanie.</span><span class="sxs-lookup"><span data-stu-id="06782-137">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="06782-138">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="06782-138">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06782-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06782-139">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="06782-140">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="06782-140">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="06782-141">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="06782-141">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
