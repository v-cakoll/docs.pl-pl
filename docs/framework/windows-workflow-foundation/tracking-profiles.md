---
title: "Profile śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a3b1e96451eb89544d0902a1f3498263dec981a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="tracking-profiles"></a><span data-ttu-id="15163-102">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="15163-102">Tracking Profiles</span></span>
<span data-ttu-id="15163-103">Śledzenie profile zawierają zapytania dotyczące śledzenia, które umożliwiają śledzenie uczestnika do subskrybowanie zdarzeń przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="15163-103">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>  
  
## <a name="tracking-profiles"></a><span data-ttu-id="15163-104">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="15163-104">Tracking Profiles</span></span>  
 <span data-ttu-id="15163-105">Profile śledzenia służą do określania, jakie informacje śledzenia jest emitowany dla wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="15163-105">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="15163-106">Jeśli profil nie jest określona, wszystkie zdarzenia śledzenia są emitowane.</span><span class="sxs-lookup"><span data-stu-id="15163-106">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="15163-107">Jeśli profil jest określony, zdarzenia śledzenia określone w profilu zostanie wyemitowany.</span><span class="sxs-lookup"><span data-stu-id="15163-107">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="15163-108">W zależności od wymagań monitorowania może zapisać profil, który jest bardzo ogólnych, które subskrybuje niewielki zestaw zmian stanu ogólny przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="15163-108">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="15163-109">Z drugiej strony może utworzyć profil bardzo szczegółowe którego wynikowy zdarzenia są sformatowanego odtworzenie przepływu szczegółowe wykonywania później.</span><span class="sxs-lookup"><span data-stu-id="15163-109">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="15163-110">Profile śledzenia pojawiają się jako elementów XML w ramach standardowego [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] pliku konfiguracji lub określona w kodzie.</span><span class="sxs-lookup"><span data-stu-id="15163-110">Tracking profiles manifest themselves as XML elements within a standard [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration file or specified in code.</span></span> <span data-ttu-id="15163-111">Poniższy przykład jest [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] profil w pliku konfiguracji, który umożliwia śledzenie uczestnika do subskrybowania śledzenia `Started` i `Completed` zdarzeń przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="15163-111">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <tracking>    
      <trackingProfile name="Sample Tracking Profile">  
        <workflow activityDefinitionId="*">  
          <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                <state name="Started"/>  
                <state name="Completed"/>  
              </states>  
            </workflowInstanceQuery>  
          </workflowInstanceQueries>  
        </workflow>  
      </trackingProfile>          
    </profiles>  
  </tracking>  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="15163-112">W poniższym przykładzie przedstawiono odpowiednikiem śledzenia profil utworzony przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="15163-112">The following example shows the equivalent tracking profile created using code.</span></span>  
  
```csharp  
TrackingProfile profile = new TrackingProfile()  
{  
    Name = "CustomTrackingProfile",  
    Queries =   
    {  
        new WorkflowInstanceQuery()  
        {  
            // Limit workflow instance tracking records for started and  
            // completed workflow states.  
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },  
        }  
    }  
};  
```  
  
 <span data-ttu-id="15163-113">Śledzenie rekordów są filtrowane w trybie widoczność w profilu śledzenia przy użyciu <xref:System.Activities.Tracking.ImplementationVisibility> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="15163-113">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="15163-114">Działanie złożone jest najwyższego poziomu działanie, które zawiera inne działania, które tworzą jego wykonania.</span><span class="sxs-lookup"><span data-stu-id="15163-114">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="15163-115">Tryb widoczności określa rekordy śledzenia wyemitowanego z złożonego działań w ramach działania przepływu pracy, aby określić, czy działania, które tworzą wdrożenia są śledzone.</span><span class="sxs-lookup"><span data-stu-id="15163-115">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span>  <span data-ttu-id="15163-116">Tryb widoczności zastosuje w śledzenia profilu poziom.</span><span class="sxs-lookup"><span data-stu-id="15163-116">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="15163-117">Filtrowanie rekordów dla poszczególnych działań w przepływie pracy śledzenia jest kontrolowana przez kwerend w profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="15163-117">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="15163-118">Aby uzyskać więcej informacji, zobacz **śledzenia typy zapytań profilu** części tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="15163-118">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>  
  
 <span data-ttu-id="15163-119">Widoczność dwóch trybów określony przez `implementationVisibility` w profilu śledzenia są `RootScope` i `All`.</span><span class="sxs-lookup"><span data-stu-id="15163-119">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="15163-120">Przy użyciu `RootScope` tryb Pomija rekordy śledzenia działań, które tworzą implementacja działania, w przypadku, gdy działanie złożone nie jest elementem głównym przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="15163-120">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span>  <span data-ttu-id="15163-121">Oznacza to, że po dodaniu działania, która jest zaimplementowana przy użyciu innych działań w przepływie pracy i `implementationVisibility` wartość RootScope, śledzić działania najwyższego poziomu w obrębie tego działania złożonego.</span><span class="sxs-lookup"><span data-stu-id="15163-121">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="15163-122">Jeśli działanie jest głównego przepływu pracy, a następnie wykonanie działania jest przepływ pracy się i śledzenie rekordów są emitowane działań, które tworzą implementacji.</span><span class="sxs-lookup"><span data-stu-id="15163-122">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="15163-123">Przy użyciu trybu wszystkich zezwala na wszystkie rekordy śledzenia, aby emitować dla działania głównego i jego działań złożonych.</span><span class="sxs-lookup"><span data-stu-id="15163-123">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>  
  
 <span data-ttu-id="15163-124">Załóżmy na przykład, *MyActivity* jest działania złożonego, którego implementację zawiera dwa działania *działania Activity1* i *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="15163-124">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span>  <span data-ttu-id="15163-125">Gdy to działanie jest dodawany do przepływu pracy i śledzenie jest włączone w profilu śledzenia z `implementationVisibility` ustawioną `RootScope`, śledzenie rekordów są emitowane tylko w przypadku *MyActivity*.</span><span class="sxs-lookup"><span data-stu-id="15163-125">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span>  <span data-ttu-id="15163-126">Jednak żadne rekordy są emitowane działań *działania Activity1* i *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="15163-126">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>  
  
 <span data-ttu-id="15163-127">Jednak jeśli `implementationVisisbility` atrybutu dla profilu śledzenia jest ustawiony na `All`, a następnie rejestruje śledzenia są emitowane nie tylko w przypadku *MyActivity*, ale także dla działań *działania Activity1* i  *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="15163-127">However, if the `implementationVisisbility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>  
  
 <span data-ttu-id="15163-128">`implementationVisibility` Flaga jest stosowana do następujących typów rekordów śledzenia:</span><span class="sxs-lookup"><span data-stu-id="15163-128">The `implementationVisibility` flag applies to following tracking record types:</span></span>  
  
-   <span data-ttu-id="15163-129">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="15163-129">ActivityStateRecord</span></span>  
  
-   <span data-ttu-id="15163-130">FaultPropagationRecord</span><span class="sxs-lookup"><span data-stu-id="15163-130">FaultPropagationRecord</span></span>  
  
-   <span data-ttu-id="15163-131">CancelRequestedRecord</span><span class="sxs-lookup"><span data-stu-id="15163-131">CancelRequestedRecord</span></span>  
  
-   <span data-ttu-id="15163-132">ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="15163-132">ActivityScheduledRecord</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15163-133">CustomTrackingRecords wyemitowanego z implementacji działania nie są odfiltrowywane przez ustawienie implementationVisibility.</span><span class="sxs-lookup"><span data-stu-id="15163-133">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>  
  
 <span data-ttu-id="15163-134">`implementationVisibility` Funkcji jest określony jako <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> na śledzenie profilu w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="15163-134">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>  
  
```  
TrackingProfile sampleTrackingProfile = new TrackingProfile()  
{  
    Name = "Sample Tracking Profile",  
    ImplementationVisibility = ImplementationVisibility.RootScope  
};  
```  
  
 <span data-ttu-id="15163-135">`implementationVisibility` Funkcji jest określony jako <xref:System.Activities.Tracking.ImplementationVisibility.All> w konfiguracji profilu śledzenia plików w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="15163-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>  
  
```xml  
<tracking>  
      <profiles>  
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">  
          <workflow activityDefinitionId="*">  
...  
         </workflow>  
        </trackingProfile>  
      </profiles>  
</tracking>  
```  
  
 <span data-ttu-id="15163-136">`ImplementationVisibility` Ustawienie w profilu śledzenia jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="15163-136">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="15163-137">Domyślnie, jego wartość jest równa `RootScope`.</span><span class="sxs-lookup"><span data-stu-id="15163-137">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="15163-138">Wartości dla tego atrybutu jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="15163-138">The values for this attribute are also case-sensitive.</span></span>  
  
### <a name="tracking-profile-query-types"></a><span data-ttu-id="15163-139">Typy zapytań profilu śledzenia</span><span class="sxs-lookup"><span data-stu-id="15163-139">Tracking Profile Query Types</span></span>  
 <span data-ttu-id="15163-140">Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="15163-140">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="15163-141">Istnieje kilka typów zapytania umożliwiające subskrybować różnych klas <xref:System.Activities.Tracking.TrackingRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="15163-141">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="15163-142">Śledzenie profile można określić w konfiguracji lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="15163-142">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="15163-143">W tym miejscu są najczęściej używane typy zapytań:</span><span class="sxs-lookup"><span data-stu-id="15163-143">Here are the most common query types:</span></span>  
  
-   <span data-ttu-id="15163-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery>-Służy do śledzenia zmiany cyklu życia wystąpienia przepływu pracy, takich jak wcześniej — zostało to pokazane `Started` i `Completed`.</span><span class="sxs-lookup"><span data-stu-id="15163-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="15163-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="15163-145">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
     <span data-ttu-id="15163-146">Stany, które może być subskrybowana są określone w <xref:System.Activities.Tracking.WorkflowInstanceStates> klasy.</span><span class="sxs-lookup"><span data-stu-id="15163-146">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>  
  
     <span data-ttu-id="15163-147">Konfiguracja lub kod używany do subskrybowania śledzenia rekordy na poziomie wystąpienia przepływu pracy `Started` wystąpienie stanu przy użyciu <xref:System.Activities.Tracking.WorkflowInstanceQuery> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="15163-147">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <workflowInstanceQueries>  
        <workflowInstanceQuery>  
          <states>  
            <state name="Started"/>  
          </states>  
        </workflowInstanceQuery>  
    </workflowInstanceQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new WorkflowInstanceQuery()  
            {  
                States = { WorkflowInstanceStates.Started}                                                                     
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="15163-148"><xref:System.Activities.Tracking.ActivityStateQuery>-Służy do śledzenia zmian cyklu życia działań, które tworzą wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="15163-148"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="15163-149">Na przykład może być do śledzenia każdorazowo po ukończeniu działania "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="15163-149">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="15163-150">To zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.ActivityStateRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="15163-150">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="15163-151">Dostępne stany do subskrybowania są określone w <xref:System.Activities.Tracking.ActivityStates>.</span><span class="sxs-lookup"><span data-stu-id="15163-151">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>  
  
     <span data-ttu-id="15163-152">Konfiguracja i kod używany do subskrybowania rekordów śledzenia stanu działania, korzystających z <xref:System.Activities.Tracking.ActivityStateQuery> dla `SendEmailActivity` działania przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="15163-152">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>  
  
    ```xml  
    <activityStateQueries>  
      <activityStateQuery activityName="SendEmailActivity">  
        <states>  
          <state name="Closed"/>  
        </states>  
      </activityStateQuery>  
    </activityStateQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =  
        {  
            new ActivityStateQuery()  
            {                              
                ActivityName = "SendEmailActivity",  
                States = { ActivityStates.Closed }  
            }  
        }  
    };  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="15163-153">Jeśli wiele elementów activityStateQuery mają taką samą nazwę, tylko Stany w ostatnim elemencie są używane w profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="15163-153">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>  
  
-   <span data-ttu-id="15163-154"><xref:System.Activities.Tracking.ActivityScheduledQuery>— To zapytanie umożliwia śledzenie działania zaplanowane do uruchomienia przez działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="15163-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="15163-155">Zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.ActivityScheduledRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="15163-155">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>  
  
     <span data-ttu-id="15163-156">Konfiguracja i kod używany do subskrybowania rekordy związane z `SendEmailActivity` działanie podrzędne planowany przy użyciu <xref:System.Activities.Tracking.ActivityScheduledQuery> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="15163-156">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <activityScheduledQueries>  
      <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
     </activityScheduledQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new ActivityScheduledQuery()  
            {  
                ActivityName = "ProcessNotificationsActivity",  
                ChildActivityName = "SendEmailActivity"  
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="15163-157"><xref:System.Activities.Tracking.FaultPropagationQuery>-Służy do śledzenia Obsługa błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="15163-157"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="15163-158">Zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.FaultPropagationRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="15163-158">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>  
  
     <span data-ttu-id="15163-159">Konfiguracja i kod używany do subskrybowania rekordy powiązane z użyciem propagacji błędów <xref:System.Activities.Tracking.FaultPropagationQuery> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="15163-159">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <faultPropagationQueries>  
      <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />  
    </faultPropagationQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =  
        {  
            new FaultPropagationQuery()  
            {  
                FaultSourceActivityName = "SendEmailActivity",  
                FaultHandlerActivityName = "NotificationsFaultHandler"  
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="15163-160"><xref:System.Activities.Tracking.CancelRequestedQuery>— Umożliwia śledzenie żądań, aby anulować działanie podrzędne przez działania nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="15163-160"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="15163-161">Zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.CancelRequestedRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="15163-161">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>  
  
     <span data-ttu-id="15163-162">Konfiguracja i kod używany do subskrybowania rekordy powiązane z użyciem anulowania działania <xref:System.Activities.Tracking.CancelRequestedQuery> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="15163-162">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <cancelRequestedQueries>  
      <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
    </cancelRequestedQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new CancelRequestedQuery()  
            {  
                ActivityName = "ProcessNotificationsActivity",  
                ChildActivityName = "SendEmailActivity"  
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="15163-163"><xref:System.Activities.Tracking.CustomTrackingQuery>-Służy do śledzenia zdarzeń zdefiniowanych w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="15163-163"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="15163-164">Zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="15163-164">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>  
  
     <span data-ttu-id="15163-165">Konfiguracja i kod używany do subskrybowania rekordy związane z śledzenia niestandardowych rekordów przy użyciu <xref:System.Activities.Tracking.CustomTrackingQuery> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="15163-165">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <customTrackingQueries>  
      <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />  
    </customTrackingQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new CustomTrackingQuery()   
            {  
                Name = "EmailAddress",  
                ActivityName = "SendEmailActivity"  
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="15163-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery>-Służy do śledzenia wznowienie zakładki w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="15163-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="15163-167">To zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.BookmarkResumptionRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="15163-167">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>  
  
     <span data-ttu-id="15163-168">Konfiguracja i kod używany do subskrybowania rekordy powiązane z użyciem wznowienie zakładki <xref:System.Activities.Tracking.BookmarkResumptionQuery> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="15163-168">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <bookmarkResumptionQueries>  
      <bookmarkResumptionQuery name="SentEmailBookmark" />  
    </bookmarkResumptionQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new BookmarkResumptionQuery()  
            {  
                Name = "sentEmailBookmark"  
            }  
        }  
    };  
    ```  
  
### <a name="annotations"></a><span data-ttu-id="15163-169">Adnotacje</span><span class="sxs-lookup"><span data-stu-id="15163-169">Annotations</span></span>  
 <span data-ttu-id="15163-170">Adnotacje umożliwiają arbitralnie tag śledzenia rekordów o wartości, które mogą być skonfigurowane po czas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="15163-170">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="15163-171">Na przykład może być kilka rekordów śledzenia między kilka przepływy pracy, aby być oznaczane "Serwera poczty" == "Poczty serwer1".</span><span class="sxs-lookup"><span data-stu-id="15163-171">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="15163-172">To ułatwia znalezienie wszystkich rekordów z tym znacznikiem podczas wykonywania zapytania rekordów śledzenia później.</span><span class="sxs-lookup"><span data-stu-id="15163-172">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
 <span data-ttu-id="15163-173">Aby to zrobić, adnotacja została dodana do zapytania śledzenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="15163-173">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="15163-174">Jak utworzyć profil śledzenia</span><span class="sxs-lookup"><span data-stu-id="15163-174">How to Create a Tracking Profile</span></span>  
 <span data-ttu-id="15163-175">Elementy zapytania śledzenia są używane do tworzenia profilu śledzenia przy użyciu pliku konfiguracji XML lub [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]kodu.</span><span class="sxs-lookup"><span data-stu-id="15163-175">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]code.</span></span>  <span data-ttu-id="15163-176">Oto przykład profilu śledzenia, który został utworzony przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="15163-176">Here is an example of a tracking profile created using a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <tracking>  
    <profiles>  
      <trackingProfile name="Sample Tracking Profile ">  
        <workflow activityDefinitionId="*">  
          <!--Specify the tracking profile query elements to subscribe for tracking records-->  
        </workflow>  
      </trackingProfile>  
    </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
> [!WARNING]
>  <span data-ttu-id="15163-177">Przy użyciu hosta usługi przepływu pracy WF profilu śledzenia jest zwykle utworzona przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="15163-177">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="15163-178">Istnieje również możliwość utworzenia profilu śledzenia z kodu przy użyciu profilu śledzenia i śledzenie zapytania interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="15163-178">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>  
  
 <span data-ttu-id="15163-179">Skonfigurowany jako plik konfiguracyjny XML profilu jest stosowany do uczestnika śledzenia przy użyciu rozszerzenia zachowania.</span><span class="sxs-lookup"><span data-stu-id="15163-179">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="15163-180">To jest dodawane do obiektu WorkflowServiceHost, zgodnie z opisem w dalszej części artykułu [Konfigurowanie śledzenia przepływu pracy](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="15163-180">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
 <span data-ttu-id="15163-181">Poziom szczegółowości śledzenia rekordy emitowane przez hosta jest określana przez ustawienia konfiguracji w profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="15163-181">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="15163-182">Uczestnik śledzenia subskrybuje śledzenie rekordów przez dodanie zapytania do profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="15163-182">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="15163-183">Aby subskrybować wszystkie rekordy śledzenia, należy określić wszystkie zapytania dotyczące śledzenia przy użyciu profilu śledzenia "*" w polach Nazwa każdego zapytania.</span><span class="sxs-lookup"><span data-stu-id="15163-183">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "*" in the name fields in each of the queries.</span></span>  
  
 <span data-ttu-id="15163-184">Poniżej przedstawiono niektóre typowe przykłady śledzenia profilów.</span><span class="sxs-lookup"><span data-stu-id="15163-184">Here are some of the common examples of tracking profiles.</span></span>  
  
-   <span data-ttu-id="15163-185">Profil śledzenia uzyskanie rekordów wystąpienia przepływu pracy i usterek.</span><span class="sxs-lookup"><span data-stu-id="15163-185">A tracking profile to obtain workflow instance records and faults.</span></span>  
  
```xml  
<trackingProfile name="Instance and Fault Records">  
  <workflow activityDefinitionId="*">  
    <workflowInstanceQueries>  
      <workflowInstanceQuery>  
        <states>  
          <state name="*" />  
        </states>  
      </workflowInstanceQuery>  
    </workflowInstanceQueries>  
    <activityStateQueries>  
      <activityStateQuery activityName="*">  
        <states>  
          <state name="Faulted"/>  
        </states>  
      </activityStateQuery>  
    </activityStateQueries>  
  </workflow>  
</trackingProfile>  
```  
  
1.  <span data-ttu-id="15163-186">Profil śledzenia można uzyskać wszystkie rekordy śledzenia niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="15163-186">A tracking profile to obtain all custom tracking records.</span></span>  
  
```xml  
<trackingProfile name="Instance_And_Custom_Records">  
  <workflow activityDefinitionId="*">  
    <customTrackingQueries>  
      <customTrackingQuery name="*" activityName="*" />  
    </customTrackingQueries>  
  </workflow>  
</trackingProfile>  
```  
  
## <a name="see-also"></a><span data-ttu-id="15163-187">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15163-187">See Also</span></span>  
 [<span data-ttu-id="15163-188">Śledzenie SQL</span><span class="sxs-lookup"><span data-stu-id="15163-188">SQL Tracking</span></span>](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)  
 [<span data-ttu-id="15163-189">Windows Server AppFabric monitorowania</span><span class="sxs-lookup"><span data-stu-id="15163-189">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="15163-190">Monitorowanie aplikacji przy użyciu rozwiązania AppFabric</span><span class="sxs-lookup"><span data-stu-id="15163-190">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
