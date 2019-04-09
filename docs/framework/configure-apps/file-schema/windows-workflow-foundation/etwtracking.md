---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: e7614f158826e3522ac8e17d60c1ea65fefc8612
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174450"
---
# <a name="etwtracking"></a><span data-ttu-id="1beaf-101">\<etwTracking ></span><span class="sxs-lookup"><span data-stu-id="1beaf-101">\<etwTracking></span></span>
<span data-ttu-id="1beaf-102">Zachowanie usługi, która umożliwia korzystanie z funkcji ETW śledzenia za pomocą <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="1beaf-102">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
<span data-ttu-id="1beaf-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1beaf-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1beaf-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="1beaf-104">\<behaviors></span></span>  
<span data-ttu-id="1beaf-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1beaf-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="1beaf-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="1beaf-106">\<behavior></span></span>  
<span data-ttu-id="1beaf-107">\<etwTracking ></span><span class="sxs-lookup"><span data-stu-id="1beaf-107">\<etwTracking></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1beaf-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1beaf-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1beaf-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1beaf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1beaf-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1beaf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1beaf-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1beaf-111">Attributes</span></span>  
  
|<span data-ttu-id="1beaf-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1beaf-112">Attribute</span></span>|<span data-ttu-id="1beaf-113">Opis</span><span class="sxs-lookup"><span data-stu-id="1beaf-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1beaf-114">Nazwa_profilu</span><span class="sxs-lookup"><span data-stu-id="1beaf-114">profileName</span></span>|<span data-ttu-id="1beaf-115">Ciąg określający nazwę profilu śledzenia skojarzony z tym działaniem.</span><span class="sxs-lookup"><span data-stu-id="1beaf-115">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1beaf-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1beaf-116">Child Elements</span></span>  
 <span data-ttu-id="1beaf-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="1beaf-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1beaf-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1beaf-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1beaf-119">Element</span><span class="sxs-lookup"><span data-stu-id="1beaf-119">Element</span></span>|<span data-ttu-id="1beaf-120">Opis</span><span class="sxs-lookup"><span data-stu-id="1beaf-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1beaf-121">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="1beaf-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="1beaf-122">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="1beaf-122">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1beaf-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1beaf-123">Remarks</span></span>  
 <span data-ttu-id="1beaf-124">Po dodaniu konfiguracji zachowanie, ten element konfiguracji służy do konfigurowania opcji uczestnikiem śledzenia w usłudze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1beaf-124">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="1beaf-125">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="1beaf-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="1beaf-126">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1beaf-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1beaf-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="1beaf-127">Example</span></span>  
 <span data-ttu-id="1beaf-128">W poniższym przykładzie konfiguracji zawiera standardowe uczestnika śledzenia zdarzeń systemu Windows jest skonfigurowany w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="1beaf-128">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="1beaf-129">Identyfikator dostawcy, który używa uczestnika śledzenia zdarzeń systemu Windows, do zapisywania rekordów śledzenia zdarzeń systemu Windows jest zdefiniowany w  **\<Diagnostyka >** sekcji.</span><span class="sxs-lookup"><span data-stu-id="1beaf-129">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="1beaf-130">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1beaf-130">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="1beaf-131">To jest definiowana za **profileName** atrybutu  **\<Dodaj >** elementu.</span><span class="sxs-lookup"><span data-stu-id="1beaf-131">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="1beaf-132">Te po zdefiniowaniu, śledzenie uczestnika zostanie dodany do  **\<etwTracking >** usługi zachowanie.</span><span class="sxs-lookup"><span data-stu-id="1beaf-132">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="1beaf-133">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1beaf-133">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1beaf-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1beaf-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="1beaf-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="1beaf-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1beaf-136">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="1beaf-136">Tracking Participants</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-participants.md)
