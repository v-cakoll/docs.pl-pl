---
title: <etwTracking>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
ms.openlocfilehash: d562bd4e3d46a1bdf41fc4065fee926850a49aa1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152174"
---
# \<etwTracking>
<span data-ttu-id="fbd5f-101">Zachowanie usługi, które umożliwia usłudze korzystanie z funkcji śledzenia ETW przy użyciu programu <xref:System.Activities.Tracking.EtwTrackingParticipant> .</span><span class="sxs-lookup"><span data-stu-id="fbd5f-101">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<etwTracking>**  
  
## <a name="syntax"></a><span data-ttu-id="fbd5f-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="fbd5f-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <etwTracking profileName="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbd5f-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fbd5f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="fbd5f-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fbd5f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbd5f-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fbd5f-105">Attributes</span></span>  
  
|<span data-ttu-id="fbd5f-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fbd5f-106">Attribute</span></span>|<span data-ttu-id="fbd5f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fbd5f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fbd5f-108">Nazwa_profilu</span><span class="sxs-lookup"><span data-stu-id="fbd5f-108">profileName</span></span>|<span data-ttu-id="fbd5f-109">Ciąg określający nazwę profilu śledzenia skojarzony z tym działaniem.</span><span class="sxs-lookup"><span data-stu-id="fbd5f-109">A string that specifies the name of the tracking profile associated with this behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fbd5f-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fbd5f-110">Child Elements</span></span>  
 <span data-ttu-id="fbd5f-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="fbd5f-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fbd5f-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fbd5f-112">Parent Elements</span></span>  
  
|<span data-ttu-id="fbd5f-113">Element</span><span class="sxs-lookup"><span data-stu-id="fbd5f-113">Element</span></span>|<span data-ttu-id="fbd5f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="fbd5f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbd5f-115">\<behavior>z\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="fbd5f-115">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="fbd5f-116">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="fbd5f-116">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fbd5f-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fbd5f-117">Remarks</span></span>  
 <span data-ttu-id="fbd5f-118">Po dodaniu konfiguracji zachowanie, ten element konfiguracji służy do konfigurowania opcji uczestnikiem śledzenia w usłudze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fbd5f-118">When added to the service’s behavior configuration, this configuration element configures a tracking participant on a workflow service.</span></span>  
  
 <span data-ttu-id="fbd5f-119">Śledzenie uczestników są stosowane w celu pobrania danych śledzenia emitowane z przepływu pracy i zapisać go w różne nośniki.</span><span class="sxs-lookup"><span data-stu-id="fbd5f-119">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="fbd5f-120">Podobnie dowolny publikować przetwarzania śledzenia, które rekordy można również wykonać w ramach uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fbd5f-120">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbd5f-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="fbd5f-121">Example</span></span>  
 <span data-ttu-id="fbd5f-122">Poniższy przykład konfiguracji przedstawia standardowy Uczestnik śledzenia ETW skonfigurowany w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="fbd5f-122">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="fbd5f-123">Identyfikator dostawcy, którego Uczestnik śledzenia funkcji ETW używa do zapisywania rekordów śledzenia w funkcji ETW, jest zdefiniowany w **\<diagnostics>** sekcji.</span><span class="sxs-lookup"><span data-stu-id="fbd5f-123">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="fbd5f-124">Uczestnik śledzenia ma własny profil skojarzonych z nim do określania subskrybowany do rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fbd5f-124">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="fbd5f-125">Jest on definiowany przez atrybut **ProfileName** **\<add>** elementu.</span><span class="sxs-lookup"><span data-stu-id="fbd5f-125">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="fbd5f-126">Po ich zdefiniowaniu Uczestnik śledzenia zostanie dodany do **\<etwTracking>** zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="fbd5f-126">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="fbd5f-127">Spowoduje to dodanie wybranych uczestników śledzenia do rozszerzeń wystąpienie przepływu pracy, aby zaczynają one odbierać rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fbd5f-127">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fbd5f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fbd5f-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="fbd5f-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="fbd5f-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fbd5f-130">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="fbd5f-130">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
