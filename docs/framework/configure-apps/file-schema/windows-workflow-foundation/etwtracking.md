---
title: '&lt;etwTracking&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: f9d1acd5dafb9df181b036db9d3ad783ca618874
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684333"
---
# <a name="ltetwtrackinggt"></a><span data-ttu-id="121c1-102">&lt;etwTracking&gt;</span><span class="sxs-lookup"><span data-stu-id="121c1-102">&lt;etwTracking&gt;</span></span>
<span data-ttu-id="121c1-103">Zachowanie usługi, która umożliwia korzystanie z funkcji ETW śledzenia za pomocą <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="121c1-103">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="121c1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="121c1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="121c1-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="121c1-105">\<behaviors></span></span>  
<span data-ttu-id="121c1-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="121c1-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="121c1-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="121c1-107">\<behavior></span></span>  
<span data-ttu-id="121c1-108">\<etwTracking ></span><span class="sxs-lookup"><span data-stu-id="121c1-108">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="121c1-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="121c1-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="121c1-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="121c1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="121c1-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="121c1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="121c1-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="121c1-112">Attributes</span></span>  
  
|<span data-ttu-id="121c1-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="121c1-113">Attribute</span></span>|<span data-ttu-id="121c1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="121c1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="121c1-115">Nazwa_profilu</span><span class="sxs-lookup"><span data-stu-id="121c1-115">profileName</span></span>|<span data-ttu-id="121c1-116">Ciąg określający nazwę profilu śledzenia skojarzony z tym działaniem.</span><span class="sxs-lookup"><span data-stu-id="121c1-116">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="121c1-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="121c1-117">Child Elements</span></span>  
 <span data-ttu-id="121c1-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="121c1-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="121c1-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="121c1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="121c1-120">Element</span><span class="sxs-lookup"><span data-stu-id="121c1-120">Element</span></span>|<span data-ttu-id="121c1-121">Opis</span><span class="sxs-lookup"><span data-stu-id="121c1-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="121c1-122">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="121c1-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="121c1-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="121c1-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="121c1-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="121c1-124">Remarks</span></span>  
 <span data-ttu-id="121c1-125">Po dodaniu konfiguracji zachowanie, ten element konfiguracji służy do konfigurowania opcji uczestnikiem śledzenia w usłudze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="121c1-125">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="121c1-126">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="121c1-126">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="121c1-127">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="121c1-127">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="121c1-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="121c1-128">Example</span></span>  
 <span data-ttu-id="121c1-129">W poniższym przykładzie konfiguracji zawiera standardowe uczestnika śledzenia zdarzeń systemu Windows jest skonfigurowany w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="121c1-129">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="121c1-130">Identyfikator dostawcy, który używa uczestnika śledzenia zdarzeń systemu Windows, do zapisywania rekordów śledzenia zdarzeń systemu Windows jest zdefiniowany w  **\<Diagnostyka >** sekcji.</span><span class="sxs-lookup"><span data-stu-id="121c1-130">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="121c1-131">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="121c1-131">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="121c1-132">To jest definiowana za **profileName** atrybutu  **\<Dodaj >** elementu.</span><span class="sxs-lookup"><span data-stu-id="121c1-132">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="121c1-133">Te po zdefiniowaniu, śledzenie uczestnika zostanie dodany do  **\<etwTracking >** usługi zachowanie.</span><span class="sxs-lookup"><span data-stu-id="121c1-133">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="121c1-134">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="121c1-134">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="121c1-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="121c1-135">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="121c1-136">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="121c1-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="121c1-137">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="121c1-137">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
