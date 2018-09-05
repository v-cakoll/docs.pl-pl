---
title: Profile śledzenia
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 6651b79a474125f57c1cad773ae858dc7654d58a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43532526"
---
# <a name="tracking-profiles"></a><span data-ttu-id="e778e-102">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="e778e-102">Tracking Profiles</span></span>
<span data-ttu-id="e778e-103">Śledzenie profile zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e778e-103">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>  
  
## <a name="tracking-profiles"></a><span data-ttu-id="e778e-104">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="e778e-104">Tracking Profiles</span></span>  
 <span data-ttu-id="e778e-105">Profile śledzenia są używane do określania, jakie informacje śledzenia jest emitowane dla wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e778e-105">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="e778e-106">Jeśli profil nie jest określony, wszystkie zdarzenia śledzenia są emitowane.</span><span class="sxs-lookup"><span data-stu-id="e778e-106">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="e778e-107">Jeśli profil jest określony, zdarzenia śledzenia określone w profilu będzie emitowane.</span><span class="sxs-lookup"><span data-stu-id="e778e-107">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="e778e-108">W zależności od wymagań dotyczących monitorowania może zapisu profil, który jest bardzo ogólny, które subskrybuje niewielkiego zestawu zmian stanu wysokiego poziomu w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="e778e-108">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="e778e-109">Z drugiej strony można utworzyć bardzo szczegółowe profil którego wynikowego zdarzenia są rozbudowanych, odtworzenie przepływ wykonania szczegółowe później.</span><span class="sxs-lookup"><span data-stu-id="e778e-109">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="e778e-110">Profile śledzenia objawy elementy XML w ramach standardowej [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] pliku konfiguracji lub określone w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e778e-110">Tracking profiles manifest themselves as XML elements within a standard [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration file or specified in code.</span></span> <span data-ttu-id="e778e-111">Poniższy przykład jest [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] profil w pliku konfiguracji, który umożliwia śledzenia uczestnika do subskrybowania śledzenia `Started` i `Completed` zdarzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e778e-111">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
  
 <span data-ttu-id="e778e-112">Poniższy przykład pokazuje odpowiednik śledzenia profil został utworzony przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="e778e-112">The following example shows the equivalent tracking profile created using code.</span></span>  
  
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
  
 <span data-ttu-id="e778e-113">Rekordy śledzenia są filtrowane w trybie widoczność w profilu śledzenia przy użyciu <xref:System.Activities.Tracking.ImplementationVisibility> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e778e-113">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="e778e-114">Działanie złożone jest czynnością najwyższego poziomu, zawierający innych działań, które tworzą jego wykonania.</span><span class="sxs-lookup"><span data-stu-id="e778e-114">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="e778e-115">Określa tryb widoczności, rekordów śledzenia emitowane z złożonych działań wewnątrz działania elementu przepływu pracy, aby określić, jeśli działania, które tworzą implementację są śledzone.</span><span class="sxs-lookup"><span data-stu-id="e778e-115">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span>  <span data-ttu-id="e778e-116">Tryb widoczności odnosi się na śledzenie poziomu profilu.</span><span class="sxs-lookup"><span data-stu-id="e778e-116">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="e778e-117">Filtrowanie rekordów dla poszczególnych działań w przepływie pracy śledzenia jest kontrolowane przez zapytania w profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e778e-117">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="e778e-118">Aby uzyskać więcej informacji, zobacz **śledzenie typów zapytań profilu** sekcji tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e778e-118">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>  
  
 <span data-ttu-id="e778e-119">Tryby widoczność dwie określone przez `implementationVisibility` atrybutu w profilu śledzenia `RootScope` i `All`.</span><span class="sxs-lookup"><span data-stu-id="e778e-119">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="e778e-120">Za pomocą `RootScope` tryb Pomija rekordy śledzenia działań, które tworzą implementację działanie w przypadku, gdy działanie złożone nie jest głównym przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e778e-120">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span>  <span data-ttu-id="e778e-121">Oznacza to, że po dodaniu działania, który jest implementowany przy użyciu innych działań w przepływie pracy i `implementationVisibility` wartość RootScope, działanie najwyższego poziomu w ramach tego działania złożonego jest śledzone.</span><span class="sxs-lookup"><span data-stu-id="e778e-121">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="e778e-122">Jeśli działanie jest głównym przepływu pracy, a następnie wykonanie działania jest przepływ pracy wraz z śledzenia rekordów, które są emitowane dla działań, które tworzą implementację.</span><span class="sxs-lookup"><span data-stu-id="e778e-122">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="e778e-123">Przy użyciu trybu wszystkich zezwala na wszystkich rekordów śledzenia emitowane dla działania głównego i wszystkich jego działań złożonych.</span><span class="sxs-lookup"><span data-stu-id="e778e-123">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>  
  
 <span data-ttu-id="e778e-124">Na przykład, załóżmy, że *MyActivity* jest czynnością złożonego, którego implementacja zawiera dwa działania *działania Activity1* i *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="e778e-124">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span>  <span data-ttu-id="e778e-125">Gdy to działanie jest dodawany do przepływu pracy i śledzenia włączono profil śledzenia z `implementationVisibility` równa `RootScope`, tylko w przypadku są emitowane rekordów śledzenia *MyActivity*.</span><span class="sxs-lookup"><span data-stu-id="e778e-125">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span>  <span data-ttu-id="e778e-126">Jednak żadne rekordy nie są emitowane działań *działania Activity1* i *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="e778e-126">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>  
  
 <span data-ttu-id="e778e-127">Jednak jeśli `implementationVisisbility` atrybutu dla profilu śledzenia jest ustawiony na `All`, a następnie są emitowane rekordów śledzenia nie tylko *MyActivity*, ale również dla działań *działania Activity1* i  *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="e778e-127">However, if the `implementationVisisbility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>  
  
 <span data-ttu-id="e778e-128">`implementationVisibility` Flaga ma zastosowanie do następujące typy rekordów śledzenia:</span><span class="sxs-lookup"><span data-stu-id="e778e-128">The `implementationVisibility` flag applies to following tracking record types:</span></span>  
  
-   <span data-ttu-id="e778e-129">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="e778e-129">ActivityStateRecord</span></span>  
  
-   <span data-ttu-id="e778e-130">FaultPropagationRecord</span><span class="sxs-lookup"><span data-stu-id="e778e-130">FaultPropagationRecord</span></span>  
  
-   <span data-ttu-id="e778e-131">CancelRequestedRecord</span><span class="sxs-lookup"><span data-stu-id="e778e-131">CancelRequestedRecord</span></span>  
  
-   <span data-ttu-id="e778e-132">ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="e778e-132">ActivityScheduledRecord</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e778e-133">CustomTrackingRecords emitowane przez implementację działania nie są odfiltrowywane przez ustawienie implementationVisibility.</span><span class="sxs-lookup"><span data-stu-id="e778e-133">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>  
  
 <span data-ttu-id="e778e-134">`implementationVisibility` Funkcji jest określony jako <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> śledzenia profilu w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e778e-134">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>  
  
```  
TrackingProfile sampleTrackingProfile = new TrackingProfile()  
{  
    Name = "Sample Tracking Profile",  
    ImplementationVisibility = ImplementationVisibility.RootScope  
};  
```  
  
 <span data-ttu-id="e778e-135">`implementationVisibility` Funkcji jest określony jako <xref:System.Activities.Tracking.ImplementationVisibility.All> w profilu śledzenia w konfiguracji pliku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e778e-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>  
  
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
  
 <span data-ttu-id="e778e-136">`ImplementationVisibility` Ustawienie w profilu śledzenia jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e778e-136">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="e778e-137">Domyślnie, jej wartość jest równa `RootScope`.</span><span class="sxs-lookup"><span data-stu-id="e778e-137">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="e778e-138">Wartości dla tego atrybutu jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="e778e-138">The values for this attribute are also case-sensitive.</span></span>  
  
### <a name="tracking-profile-query-types"></a><span data-ttu-id="e778e-139">Typy zapytań profilu śledzenia</span><span class="sxs-lookup"><span data-stu-id="e778e-139">Tracking Profile Query Types</span></span>  
 <span data-ttu-id="e778e-140">Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e778e-140">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="e778e-141">Istnieje kilka typów zapytania, które umożliwiają subskrybować różnymi klasami <xref:System.Activities.Tracking.TrackingRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e778e-141">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="e778e-142">Śledzenie profile można określić w konfiguracji lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="e778e-142">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="e778e-143">Poniżej przedstawiono najbardziej typowych zapytań:</span><span class="sxs-lookup"><span data-stu-id="e778e-143">Here are the most common query types:</span></span>  
  
-   <span data-ttu-id="e778e-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> — Umożliwia śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak wcześniej — pokazano `Started` i `Completed`.</span><span class="sxs-lookup"><span data-stu-id="e778e-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="e778e-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="e778e-145">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
     <span data-ttu-id="e778e-146">Stany, które mogą być subskrybowane są określone w <xref:System.Activities.Tracking.WorkflowInstanceStates> klasy.</span><span class="sxs-lookup"><span data-stu-id="e778e-146">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>  
  
     <span data-ttu-id="e778e-147">Konfiguracja lub kod używany do subskrybowania rekordów dla śledzenia na poziomie wystąpienia przepływu pracy `Started` wystąpienie stanu za pomocą <xref:System.Activities.Tracking.WorkflowInstanceQuery> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e778e-147">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>  
  
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
  
-   <span data-ttu-id="e778e-148"><xref:System.Activities.Tracking.ActivityStateQuery> — Ten służy do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e778e-148"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="e778e-149">Na przykład chcesz do śledzenia za każdym razem, gdy kończy działanie "Wyślij wiadomość E-Mail", w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e778e-149">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="e778e-150">To zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.ActivityStateRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e778e-150">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="e778e-151">Stany do subskrybowania są wyszczególnione w <xref:System.Activities.Tracking.ActivityStates>.</span><span class="sxs-lookup"><span data-stu-id="e778e-151">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>  
  
     <span data-ttu-id="e778e-152">Konfiguracja i kod używany do subskrybowania rekordów śledzenia stanu działania, korzystających z <xref:System.Activities.Tracking.ActivityStateQuery> dla `SendEmailActivity` działania przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e778e-152">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>  
  
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
    >  <span data-ttu-id="e778e-153">Jeśli wiele elementów activityStateQuery mają taką samą nazwę, tylko Stany w ostatnim elemencie są używane w profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e778e-153">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>  
  
-   <span data-ttu-id="e778e-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> — To zapytanie pozwala do śledzenia działania zaplanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e778e-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="e778e-155">Zapytanie jest niezbędne dla <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.ActivityScheduledRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e778e-155">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>  
  
     <span data-ttu-id="e778e-156">Konfiguracja i kod używany do subskrybowania rekordów związanych z `SendEmailActivity` działania podrzędnego zaplanowanej przy użyciu <xref:System.Activities.Tracking.ActivityScheduledQuery> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e778e-156">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>  
  
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
  
-   <span data-ttu-id="e778e-157"><xref:System.Activities.Tracking.FaultPropagationQuery> — Ten służy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="e778e-157"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e778e-158">Zapytanie jest niezbędne dla <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.FaultPropagationRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e778e-158">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>  
  
     <span data-ttu-id="e778e-159">Konfiguracja i kod używany do subskrybowania rekordów związanych z propagacji błędów <xref:System.Activities.Tracking.FaultPropagationQuery> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e778e-159">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>  
  
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
  
-   <span data-ttu-id="e778e-160"><xref:System.Activities.Tracking.CancelRequestedQuery> — Ten służy do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e778e-160"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="e778e-161">Zapytanie jest niezbędne dla <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.CancelRequestedRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e778e-161">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>  
  
     <span data-ttu-id="e778e-162">Konfiguracja i kod używany do subskrybowania rekordów związanych z anulowania działania <xref:System.Activities.Tracking.CancelRequestedQuery> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e778e-162">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>  
  
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
  
-   <span data-ttu-id="e778e-163"><xref:System.Activities.Tracking.CustomTrackingQuery> — Ten służy do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="e778e-163"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="e778e-164">Zapytanie jest niezbędne dla <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e778e-164">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>  
  
     <span data-ttu-id="e778e-165">Konfiguracja i kod używany do subskrybowania rekordów powiązanych śledzenia niestandardowe rekordów przy użyciu <xref:System.Activities.Tracking.CustomTrackingQuery> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e778e-165">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>  
  
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
  
-   <span data-ttu-id="e778e-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> — Ten służy do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e778e-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="e778e-167">To zapytanie jest niezbędne do <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.BookmarkResumptionRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e778e-167">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>  
  
     <span data-ttu-id="e778e-168">Konfiguracja i kod używany do subskrybowania rekordów związanych z wznowienie zakładki <xref:System.Activities.Tracking.BookmarkResumptionQuery> przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e778e-168">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>  
  
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
  
### <a name="annotations"></a><span data-ttu-id="e778e-169">Adnotacje</span><span class="sxs-lookup"><span data-stu-id="e778e-169">Annotations</span></span>  
 <span data-ttu-id="e778e-170">Adnotacje umożliwiają arbitralnie tag śledzenia rekordów o wartości, które mogą być skonfigurowane po czas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e778e-170">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="e778e-171">Na przykład może być kilka rekordów śledzenia na kilka przepływy pracy służące do być oznakowane za pomocą "Serwer poczty" == "Serwer1 poczty".</span><span class="sxs-lookup"><span data-stu-id="e778e-171">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="e778e-172">To ułatwia znalezienie wszystkich rekordów z tym znacznikiem podczas wykonywania zapytania rekordów śledzenia później.</span><span class="sxs-lookup"><span data-stu-id="e778e-172">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
 <span data-ttu-id="e778e-173">Aby to osiągnąć, adnotacja jest dodawany do zapytania śledzenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e778e-173">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>  
  
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
  
### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="e778e-174">Jak utworzyć profil śledzenia</span><span class="sxs-lookup"><span data-stu-id="e778e-174">How to Create a Tracking Profile</span></span>  
 <span data-ttu-id="e778e-175">Elementy zapytania śledzenia są używane do tworzenia profilu śledzenia przy użyciu pliku konfiguracji XML lub [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]kodu.</span><span class="sxs-lookup"><span data-stu-id="e778e-175">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]code.</span></span>  <span data-ttu-id="e778e-176">Poniżej przedstawiono przykład profilu śledzenia, który został utworzony przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e778e-176">Here is an example of a tracking profile created using a configuration file.</span></span>  
  
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
>  <span data-ttu-id="e778e-177">Dla programu WF przy użyciu hosta usługi przepływu pracy profilu śledzenia jest zwykle tworzony, przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e778e-177">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="e778e-178">Istnieje również możliwość tworzenia profilu śledzenia przy użyciu kodu przy użyciu profilu śledzenia i śledzenia interfejsu API zapytań.</span><span class="sxs-lookup"><span data-stu-id="e778e-178">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>  
  
 <span data-ttu-id="e778e-179">Profil, który został skonfigurowany jako plik konfiguracyjny XML jest stosowany do śledzenia uczestnika, za pomocą rozszerzenia zachowania.</span><span class="sxs-lookup"><span data-stu-id="e778e-179">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="e778e-180">To jest dodawany do klasy WorkflowServiceHost zgodnie z opisem w dalszej części [Konfigurowanie śledzenia przepływu pracy](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="e778e-180">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
 <span data-ttu-id="e778e-181">Poziom szczegółowości rekordów śledzenia emitowane przez hosta jest określana przez ustawienia konfiguracji w profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e778e-181">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="e778e-182">Subskrybuje uczestnikiem śledzenia do śledzenia rekordów przez dodanie zapytania do profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e778e-182">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="e778e-183">Aby subskrybować wszystkie rekordy śledzenia, należy określić wszystkie zapytania śledzenia przy użyciu profilu śledzenia "\*" w polach Nazwa we wszystkich zapytań.</span><span class="sxs-lookup"><span data-stu-id="e778e-183">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "\*" in the name fields in each of the queries.</span></span>  
  
 <span data-ttu-id="e778e-184">Poniżej przedstawiono niektóre typowe przykłady śledzenie profile.</span><span class="sxs-lookup"><span data-stu-id="e778e-184">Here are some of the common examples of tracking profiles.</span></span>  
  
-   <span data-ttu-id="e778e-185">Profil śledzenia do uzyskania rekordów wystąpienia przepływu pracy i usterek.</span><span class="sxs-lookup"><span data-stu-id="e778e-185">A tracking profile to obtain workflow instance records and faults.</span></span>  
  
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
  
1.  <span data-ttu-id="e778e-186">Profil śledzenia można uzyskać wszystkie niestandardowe rekordy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e778e-186">A tracking profile to obtain all custom tracking records.</span></span>  
  
```xml  
<trackingProfile name="Instance_And_Custom_Records">  
  <workflow activityDefinitionId="*">  
    <customTrackingQueries>  
      <customTrackingQuery name="*" activityName="*" />  
    </customTrackingQueries>  
  </workflow>  
</trackingProfile>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e778e-187">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e778e-187">See Also</span></span>  
 [<span data-ttu-id="e778e-188">Śledzenie SQL</span><span class="sxs-lookup"><span data-stu-id="e778e-188">SQL Tracking</span></span>](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)  
 [<span data-ttu-id="e778e-189">Windows Server AppFabric monitorowania</span><span class="sxs-lookup"><span data-stu-id="e778e-189">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="e778e-190">Monitorowanie aplikacji przy użyciu rozwiązania AppFabric</span><span class="sxs-lookup"><span data-stu-id="e778e-190">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
