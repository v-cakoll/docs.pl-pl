---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: d562bd4e3d46a1bdf41fc4065fee926850a49aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152174"
---
# <a name="etwtracking"></a><span data-ttu-id="3d2a9-101">\<> śledzenia etw</span><span class="sxs-lookup"><span data-stu-id="3d2a9-101">\<etwTracking></span></span>
<span data-ttu-id="3d2a9-102">Zachowanie usługi, które pozwala usłudze korzystać <xref:System.Activities.Tracking.EtwTrackingParticipant>ze śledzenia ETW za pomocą pliku .</span><span class="sxs-lookup"><span data-stu-id="3d2a9-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="3d2a9-103">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3d2a9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3d2a9-104">&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3d2a9-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="3d2a9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<zachowania>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3d2a9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="3d2a9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<usługiZachowady>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3d2a9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="3d2a9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>zachowania**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="3d2a9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="3d2a9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>śledzenia etw**</span><span class="sxs-lookup"><span data-stu-id="3d2a9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d2a9-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d2a9-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d2a9-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3d2a9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3d2a9-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3d2a9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d2a9-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3d2a9-112">Attributes</span></span>  
  
|<span data-ttu-id="3d2a9-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3d2a9-113">Attribute</span></span>|<span data-ttu-id="3d2a9-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3d2a9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3d2a9-115">Nazwa_profilu</span><span class="sxs-lookup"><span data-stu-id="3d2a9-115">profileName</span></span>|<span data-ttu-id="3d2a9-116">Ciąg określający nazwę profilu śledzenia skojarzony z tym działaniem.</span><span class="sxs-lookup"><span data-stu-id="3d2a9-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d2a9-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3d2a9-117">Child Elements</span></span>  
 <span data-ttu-id="3d2a9-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="3d2a9-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3d2a9-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3d2a9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3d2a9-120">Element</span><span class="sxs-lookup"><span data-stu-id="3d2a9-120">Element</span></span>|<span data-ttu-id="3d2a9-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3d2a9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d2a9-122">\<zachowanie> \<usługZachod></span><span class="sxs-lookup"><span data-stu-id="3d2a9-122">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="3d2a9-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="3d2a9-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d2a9-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d2a9-124">Remarks</span></span>  
 <span data-ttu-id="3d2a9-125">Po dodaniu konfiguracji zachowanie, ten element konfiguracji służy do konfigurowania opcji uczestnikiem śledzenia w usłudze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="3d2a9-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="3d2a9-126">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="3d2a9-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="3d2a9-127">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3d2a9-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d2a9-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d2a9-128">Example</span></span>  
 <span data-ttu-id="3d2a9-129">W poniższym przykładzie konfiguracji przedstawiono standardowego uczestnika śledzenia ETW skonfigurowany w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="3d2a9-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="3d2a9-130">Identyfikator dostawcy używany przez uczestnika śledzenia ETW do zapisywania rekordów śledzenia na ETW jest zdefiniowany w sekcji \*\* \<diagnostyki>.\*\*</span><span class="sxs-lookup"><span data-stu-id="3d2a9-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="3d2a9-131">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3d2a9-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="3d2a9-132">Jest to zdefiniowane przez **atrybut profileName** elementu \*\* \<add>.\*\*</span><span class="sxs-lookup"><span data-stu-id="3d2a9-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="3d2a9-133">Po zdefiniowaniu są one uczestnik śledzenia jest dodawany do \*\* \<etwTracking>\*\* zachowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="3d2a9-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="3d2a9-134">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3d2a9-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d2a9-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d2a9-135">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="3d2a9-136">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="3d2a9-136">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3d2a9-137">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="3d2a9-137">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
