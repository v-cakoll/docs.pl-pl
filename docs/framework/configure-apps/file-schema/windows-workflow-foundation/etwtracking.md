---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: 653693fef92072cb1e6e23234359b765f0f18fc9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940229"
---
# <a name="etwtracking"></a><span data-ttu-id="94850-101">\<etwTracking ></span><span class="sxs-lookup"><span data-stu-id="94850-101">\<etwTracking></span></span>
<span data-ttu-id="94850-102">Zachowanie usługi, które umożliwia usłudze korzystanie z funkcji śledzenia ETW przy użyciu <xref:System.Activities.Tracking.EtwTrackingParticipant>programu.</span><span class="sxs-lookup"><span data-stu-id="94850-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="94850-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="94850-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="94850-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="94850-104">\<behaviors></span></span>  
<span data-ttu-id="94850-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="94850-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="94850-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="94850-106">\<behavior></span></span>  
<span data-ttu-id="94850-107">\<etwTracking ></span><span class="sxs-lookup"><span data-stu-id="94850-107">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94850-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="94850-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94850-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="94850-109">Attributes and Elements</span></span>  
 <span data-ttu-id="94850-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="94850-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94850-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="94850-111">Attributes</span></span>  
  
|<span data-ttu-id="94850-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="94850-112">Attribute</span></span>|<span data-ttu-id="94850-113">Opis</span><span class="sxs-lookup"><span data-stu-id="94850-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94850-114">Nazwa_profilu</span><span class="sxs-lookup"><span data-stu-id="94850-114">profileName</span></span>|<span data-ttu-id="94850-115">Ciąg określający nazwę profilu śledzenia skojarzony z tym działaniem.</span><span class="sxs-lookup"><span data-stu-id="94850-115">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94850-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="94850-116">Child Elements</span></span>  
 <span data-ttu-id="94850-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="94850-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94850-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="94850-118">Parent Elements</span></span>  
  
|<span data-ttu-id="94850-119">Element</span><span class="sxs-lookup"><span data-stu-id="94850-119">Element</span></span>|<span data-ttu-id="94850-120">Opis</span><span class="sxs-lookup"><span data-stu-id="94850-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94850-121">\<zachowanie > w \<usłudze serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="94850-121">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="94850-122">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="94850-122">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94850-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94850-123">Remarks</span></span>  
 <span data-ttu-id="94850-124">Po dodaniu konfiguracji zachowanie, ten element konfiguracji służy do konfigurowania opcji uczestnikiem śledzenia w usłudze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="94850-124">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="94850-125">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="94850-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="94850-126">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="94850-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94850-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="94850-127">Example</span></span>  
 <span data-ttu-id="94850-128">Poniższy przykład konfiguracji przedstawia standardowy Uczestnik śledzenia ETW skonfigurowany w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="94850-128">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="94850-129">Identyfikator dostawcy, którego Uczestnik śledzenia funkcji ETW używa do zapisywania rekordów śledzenia w funkcji ETW,  **\<** jest zdefiniowany w sekcji > diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="94850-129">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="94850-130">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="94850-130">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="94850-131">Jest on definiowany przez atrybut  **\<** ProfileName elementu Add >.</span><span class="sxs-lookup"><span data-stu-id="94850-131">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="94850-132">Po ich zdefiniowaniu Uczestnik śledzenia zostanie dodany do  **\<zachowania usługi etwTracking >** .</span><span class="sxs-lookup"><span data-stu-id="94850-132">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="94850-133">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="94850-133">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="94850-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94850-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="94850-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="94850-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="94850-136">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="94850-136">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
