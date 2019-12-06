---
title: Profile śledzenia
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 9217f25ba4499e7ff75020642be387aa79ba27bf
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837626"
---
# <a name="tracking-profiles"></a><span data-ttu-id="a0c64-102">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="a0c64-102">Tracking Profiles</span></span>

<span data-ttu-id="a0c64-103">Profile śledzenia zawierają zapytania śledzenia umożliwiające uczestnikom śledzenia subskrybowanie zdarzeń przepływu pracy, które są emitowane w przypadku zmiany stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a0c64-103">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>

## <a name="tracking-profiles"></a><span data-ttu-id="a0c64-104">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="a0c64-104">Tracking Profiles</span></span>

<span data-ttu-id="a0c64-105">Profile śledzenia służą do określania, które informacje o śledzeniu są emitowane dla wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a0c64-105">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="a0c64-106">Jeśli profil nie zostanie określony, zostaną wyemitowane wszystkie zdarzenia śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a0c64-106">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="a0c64-107">Jeśli określono profil, zdarzenia śledzenia określone w profilu będą emitowane.</span><span class="sxs-lookup"><span data-stu-id="a0c64-107">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="a0c64-108">W zależności od wymagań dotyczących monitorowania można napisać profil, który jest bardzo ogólny, który subskrybuje niewielki zestaw zmian stanu wysokiego poziomu w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="a0c64-108">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="a0c64-109">Z drugiej strony można utworzyć bardzo szczegółowy profil, którego zdarzenia są wystarczająco rozbudowane w celu późniejszego odtworzenia szczegółowego przepływu wykonania.</span><span class="sxs-lookup"><span data-stu-id="a0c64-109">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>

<span data-ttu-id="a0c64-110">Śledzenie profilów jako elementów XML w standardowym pliku konfiguracji .NET Framework lub określonych w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a0c64-110">Tracking profiles manifest themselves as XML elements within a standard .NET Framework configuration file or specified in code.</span></span> <span data-ttu-id="a0c64-111">Poniższy przykład dotyczy profilu śledzenia [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] w pliku konfiguracji, który umożliwia uczestnikom śledzenia subskrybowanie `Started` i `Completed` zdarzeń przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a0c64-111">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>

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

<span data-ttu-id="a0c64-112">Poniższy przykład przedstawia odpowiedni profil śledzenia utworzony przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="a0c64-112">The following example shows the equivalent tracking profile created using code.</span></span>

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

<span data-ttu-id="a0c64-113">Rekordy śledzenia są filtrowane przez tryb widoczności w profilu śledzenia przy użyciu atrybutu <xref:System.Activities.Tracking.ImplementationVisibility>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-113">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="a0c64-114">Działanie złożone to działanie najwyższego poziomu, które zawiera inne działania, które tworzą jego implementację.</span><span class="sxs-lookup"><span data-stu-id="a0c64-114">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="a0c64-115">Tryb widoczności określa rekordy śledzenia emitowane z działań złożonych w ramach działania przepływu pracy, aby określić, czy działania tworzące implementację są śledzone.</span><span class="sxs-lookup"><span data-stu-id="a0c64-115">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span> <span data-ttu-id="a0c64-116">Tryb widoczności dotyczy poziomu profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a0c64-116">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="a0c64-117">Filtrowanie rekordów śledzenia dla poszczególnych działań w ramach przepływu pracy jest kontrolowane przez zapytania w ramach profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a0c64-117">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="a0c64-118">Aby uzyskać więcej informacji, zobacz sekcję **śledzenie typów zapytań profilu** w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="a0c64-118">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>

<span data-ttu-id="a0c64-119">Dwa tryby widoczności określone przez atrybut `implementationVisibility` w profilu śledzenia są `RootScope` i `All`.</span><span class="sxs-lookup"><span data-stu-id="a0c64-119">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="a0c64-120">Użycie trybu `RootScope` powoduje pominięcie rekordów śledzenia dla działań, które tworzą implementację działania w przypadku, gdy działanie złożone nie jest elementem głównym przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a0c64-120">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span> <span data-ttu-id="a0c64-121">Oznacza to, że gdy działanie zaimplementowane przy użyciu innych działań jest dodawane do przepływu pracy, a `implementationVisibility` ustawiona na RootScope, śledzone jest tylko działanie najwyższego poziomu w ramach tego działania złożonego.</span><span class="sxs-lookup"><span data-stu-id="a0c64-121">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="a0c64-122">Jeśli działanie jest elementem głównym przepływu pracy, implementacja działania jest przepływem pracy, a śledzone rekordy są emitowane dla działań, które tworzą implementację.</span><span class="sxs-lookup"><span data-stu-id="a0c64-122">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="a0c64-123">Użycie trybu All zezwala na emisję wszystkich rekordów śledzenia dla działania głównego i wszystkich jego działań złożonych.</span><span class="sxs-lookup"><span data-stu-id="a0c64-123">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>

<span data-ttu-id="a0c64-124">Na przykład załóżmy, że *działanie to złożone działanie,* którego implementacja zawiera dwa działania, *zakończeniu* i *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="a0c64-124">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span> <span data-ttu-id="a0c64-125">Gdy to działanie jest dodawane do przepływu pracy, a funkcja śledzenia jest włączona z profilem śledzenia o `implementationVisibility` ustawionym na `RootScope`, śledzenie rekordów jest emitowane tylko dla *działania*.</span><span class="sxs-lookup"><span data-stu-id="a0c64-125">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span> <span data-ttu-id="a0c64-126">Jednak żadne rekordy nie są emitowane dla działań *zakończeniu* i *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="a0c64-126">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="a0c64-127">Jeśli jednak atrybut `implementationVisibility` dla profilu śledzenia jest ustawiony na `All`, to śledzenie rekordów jest emitowane nie tylko dla *akcji moje działanie*, ale również dla działań *zakończeniu* i *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="a0c64-127">However, if the `implementationVisibility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="a0c64-128">Flaga `implementationVisibility` ma zastosowanie do następujących typów rekordów śledzenia:</span><span class="sxs-lookup"><span data-stu-id="a0c64-128">The `implementationVisibility` flag applies to following tracking record types:</span></span>

- <span data-ttu-id="a0c64-129">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="a0c64-129">ActivityStateRecord</span></span>

- <span data-ttu-id="a0c64-130">FaultPropagationRecord</span><span class="sxs-lookup"><span data-stu-id="a0c64-130">FaultPropagationRecord</span></span>

- <span data-ttu-id="a0c64-131">CancelRequestedRecord</span><span class="sxs-lookup"><span data-stu-id="a0c64-131">CancelRequestedRecord</span></span>

- <span data-ttu-id="a0c64-132">ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="a0c64-132">ActivityScheduledRecord</span></span>

> [!NOTE]
> <span data-ttu-id="a0c64-133">CustomTrackingRecords emitowane z implementacji działania nie są filtrowane przez ustawienie implementationVisibility.</span><span class="sxs-lookup"><span data-stu-id="a0c64-133">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>

<span data-ttu-id="a0c64-134">Funkcja `implementationVisibility` jest określana jako <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> w profilu śledzenia w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a0c64-134">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

<span data-ttu-id="a0c64-135">Funkcja `implementationVisibility` jest określona jako <xref:System.Activities.Tracking.ImplementationVisibility.All> w profilu śledzenia w pliku konfiguracji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a0c64-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>

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

<span data-ttu-id="a0c64-136">Ustawienie `ImplementationVisibility` profilu śledzenia jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="a0c64-136">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="a0c64-137">Domyślnie wartość jest ustawiona na `RootScope`.</span><span class="sxs-lookup"><span data-stu-id="a0c64-137">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="a0c64-138">W wartościach tego atrybutu rozróżniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="a0c64-138">The values for this attribute are also case-sensitive.</span></span>

### <a name="tracking-profile-query-types"></a><span data-ttu-id="a0c64-139">Typy zapytań profilu śledzenia</span><span class="sxs-lookup"><span data-stu-id="a0c64-139">Tracking Profile Query Types</span></span>

<span data-ttu-id="a0c64-140">Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a0c64-140">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="a0c64-141">Istnieje kilka typów zapytań, które umożliwiają subskrybowanie różnych klas obiektów <xref:System.Activities.Tracking.TrackingRecord>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-141">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="a0c64-142">Profile śledzenia można określić w obszarze Konfiguracja lub za poorednictwem kodu.</span><span class="sxs-lookup"><span data-stu-id="a0c64-142">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="a0c64-143">Oto najpopularniejsze typy zapytań:</span><span class="sxs-lookup"><span data-stu-id="a0c64-143">Here are the most common query types:</span></span>

- <span data-ttu-id="a0c64-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> — Użyj tego do śledzenia zmian cyklu życia wystąpienia przepływu pracy, takich jak wcześniej zademonstrowane `Started` i `Completed`.</span><span class="sxs-lookup"><span data-stu-id="a0c64-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="a0c64-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="a0c64-145">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  <span data-ttu-id="a0c64-146">Stany, do których można subskrybować, są określone w klasie <xref:System.Activities.Tracking.WorkflowInstanceStates>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-146">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>

  <span data-ttu-id="a0c64-147">W poniższym przykładzie przedstawiono konfigurację lub kod służący do subskrybowania rekordów śledzenia na poziomie wystąpienia przepływu pracy dla `Started` stanu wystąpienia, przy użyciu <xref:System.Activities.Tracking.WorkflowInstanceQuery>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-147">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>

  ```xml
  <workflowInstanceQueries>
      <workflowInstanceQuery>
        <states>
          <state name="Started"/>
        </states>
      </workflowInstanceQuery>
  </workflowInstanceQueries>
  ```

  ```csharp
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

- <span data-ttu-id="a0c64-148"><xref:System.Activities.Tracking.ActivityStateQuery> — Użyj tego do śledzenia zmian cyklu życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a0c64-148"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="a0c64-149">Na przykład możesz chcieć śledzić każde działanie "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a0c64-149">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="a0c64-150">To zapytanie jest niezbędne do subskrybowania <xref:System.Activities.Tracking.ActivityStateRecord> obiektów <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-150">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="a0c64-151">Dostępne Stany subskrybowania są określone w <xref:System.Activities.Tracking.ActivityStates>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-151">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>

  <span data-ttu-id="a0c64-152">W poniższym przykładzie przedstawiono konfigurację i kod służący do subskrybowania rekordów śledzenia stanu działań, które używają <xref:System.Activities.Tracking.ActivityStateQuery> dla działania `SendEmailActivity`.</span><span class="sxs-lookup"><span data-stu-id="a0c64-152">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>

  ```xml
  <activityStateQueries>
    <activityStateQuery activityName="SendEmailActivity">
      <states>
        <state name="Closed"/>
      </states>
    </activityStateQuery>
  </activityStateQueries>
  ```

  ```csharp
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
  > <span data-ttu-id="a0c64-153">Jeśli wiele elementów activityStateQuery ma taką samą nazwę, tylko Stany w ostatnim elemencie są używane w profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a0c64-153">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>

- <span data-ttu-id="a0c64-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> — to zapytanie umożliwia śledzenie działania zaplanowanych do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a0c64-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="a0c64-155">Zapytanie jest niezbędne do subskrybowania <xref:System.Activities.Tracking.ActivityScheduledRecord> obiektów <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-155">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>

  <span data-ttu-id="a0c64-156">W poniższym przykładzie przedstawiono konfigurację i kod służący do subskrybowania rekordów związanych z `SendEmailActivity`m działaniem podrzędnym, które jest planowane przy użyciu <xref:System.Activities.Tracking.ActivityScheduledQuery>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-156">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>

  ```xml
  <activityScheduledQueries>
    <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </activityScheduledQueries>
  ```

  ```csharp
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

- <span data-ttu-id="a0c64-157"><xref:System.Activities.Tracking.FaultPropagationQuery> — Użyj tego do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="a0c64-157"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="a0c64-158">Zapytanie jest niezbędne do subskrybowania <xref:System.Activities.Tracking.FaultPropagationRecord> obiektów <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-158">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>

  <span data-ttu-id="a0c64-159">W poniższym przykładzie przedstawiono konfigurację i kod służący do subskrybowania rekordów związanych z propagacją błędów przy użyciu <xref:System.Activities.Tracking.FaultPropagationQuery>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-159">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>

  ```xml
  <faultPropagationQueries>
    <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />
  </faultPropagationQueries>
  ```

  ```csharp
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

- <span data-ttu-id="a0c64-160"><xref:System.Activities.Tracking.CancelRequestedQuery> — Użyj tego do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a0c64-160"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a0c64-161">Zapytanie jest niezbędne do subskrybowania <xref:System.Activities.Tracking.CancelRequestedRecord> obiektów <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-161">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>

  <span data-ttu-id="a0c64-162">W poniższym przykładzie przedstawiono konfigurację i kod służący do subskrybowania rekordów związanych z anulowaniem działania przy użyciu <xref:System.Activities.Tracking.CancelRequestedQuery>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-162">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>

  ```xml
  <cancelRequestedQueries>
    <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </cancelRequestedQueries>
  ```

  ```csharp
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

- <span data-ttu-id="a0c64-163"><xref:System.Activities.Tracking.CustomTrackingQuery> — Użyj tego do śledzenia zdarzeń zdefiniowanych w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="a0c64-163"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="a0c64-164">Zapytanie jest niezbędne do subskrybowania <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-164">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>

  <span data-ttu-id="a0c64-165">W poniższym przykładzie przedstawiono konfigurację i kod służący do subskrybowania rekordów związanych z niestandardowymi rekordami śledzenia przy użyciu <xref:System.Activities.Tracking.CustomTrackingQuery>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-165">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>

  ```xml
  <customTrackingQueries>
    <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />
  </customTrackingQueries>
  ```

  ```csharp
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

- <span data-ttu-id="a0c64-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> — Użyj tej metody, aby śledzić wznowienie zakładki w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a0c64-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="a0c64-167">To zapytanie jest niezbędne do subskrybowania <xref:System.Activities.Tracking.BookmarkResumptionRecord> obiektów <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-167">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>

  <span data-ttu-id="a0c64-168">W poniższym przykładzie przedstawiono konfigurację i kod służący do subskrybowania rekordów związanych z wznowieniem zakładek przy użyciu <xref:System.Activities.Tracking.BookmarkResumptionQuery>.</span><span class="sxs-lookup"><span data-stu-id="a0c64-168">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>

  ```xml
  <bookmarkResumptionQueries>
    <bookmarkResumptionQuery name="SentEmailBookmark" />
  </bookmarkResumptionQueries>
  ```

  ```csharp
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

### <a name="annotations"></a><span data-ttu-id="a0c64-169">Adnotacje</span><span class="sxs-lookup"><span data-stu-id="a0c64-169">Annotations</span></span>

<span data-ttu-id="a0c64-170">Adnotacje umożliwiają arbitralnie tag śledzenia rekordów o wartości, które mogą być skonfigurowane po czas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a0c64-170">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="a0c64-171">Na przykład może być konieczne kilka rekordów śledzenia w kilku przepływach pracy, które mają być otagowane przy użyciu "serwer poczty" = = "wiadomość serwer1".</span><span class="sxs-lookup"><span data-stu-id="a0c64-171">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="a0c64-172">To ułatwia znalezienie wszystkich rekordów z tym znacznikiem podczas wykonywania zapytania rekordów śledzenia później.</span><span class="sxs-lookup"><span data-stu-id="a0c64-172">This makes it easy to find all records with this tag when querying tracking records later.</span></span>

<span data-ttu-id="a0c64-173">Aby to osiągnąć, adnotacja jest dodawana do zapytania śledzenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a0c64-173">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>

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

### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="a0c64-174">Jak utworzyć profil śledzenia</span><span class="sxs-lookup"><span data-stu-id="a0c64-174">How to Create a Tracking Profile</span></span>

<span data-ttu-id="a0c64-175">Elementy zapytania śledzenia są używane do tworzenia profilu śledzenia przy użyciu pliku konfiguracyjnego XML lub kodu [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0c64-175">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]code.</span></span> <span data-ttu-id="a0c64-176">Oto przykład profilu śledzenia utworzonego przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a0c64-176">Here is an example of a tracking profile created using a configuration file.</span></span>

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
> <span data-ttu-id="a0c64-177">W przypadku WF przy użyciu hosta usługi przepływu pracy profil śledzenia jest zwykle tworzony przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a0c64-177">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="a0c64-178">Istnieje również możliwość utworzenia profilu śledzenia z kodem przy użyciu profilu śledzenia i interfejsu API zapytań śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a0c64-178">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>

<span data-ttu-id="a0c64-179">Profil skonfigurowany jako plik konfiguracji XML jest stosowany do śledzenia uczestnika przy użyciu rozszerzenia zachowania.</span><span class="sxs-lookup"><span data-stu-id="a0c64-179">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="a0c64-180">Ten element jest dodawany do obiektu WorkflowServiceHost zgodnie z opisem w dalszej części [Konfigurowanie śledzenia dla przepływu pracy](configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="a0c64-180">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](configuring-tracking-for-a-workflow.md).</span></span>

<span data-ttu-id="a0c64-181">Poziom szczegółowości rekordów śledzenia emitowanych przez hosta jest określany przez ustawienia konfiguracji w ramach profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a0c64-181">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="a0c64-182">Uczestnik śledzenia subskrybuje śledzenie rekordów przez dodawanie zapytań do profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a0c64-182">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="a0c64-183">Aby subskrybować wszystkie rekordy śledzenia, profil śledzenia musi określać wszystkie zapytania śledzenia przy użyciu "\*" w polach nazw w poszczególnych zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="a0c64-183">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "\*" in the name fields in each of the queries.</span></span>

<span data-ttu-id="a0c64-184">Poniżej przedstawiono niektóre typowe przykłady profilów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a0c64-184">Here are some of the common examples of tracking profiles.</span></span>

- <span data-ttu-id="a0c64-185">Profil śledzenia umożliwiający uzyskanie rekordów wystąpień przepływu pracy i błędów.</span><span class="sxs-lookup"><span data-stu-id="a0c64-185">A tracking profile to obtain workflow instance records and faults.</span></span>

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

- <span data-ttu-id="a0c64-186">Profil śledzenia umożliwiający uzyskanie wszystkich niestandardowych rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a0c64-186">A tracking profile to obtain all custom tracking records.</span></span>

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a><span data-ttu-id="a0c64-187">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0c64-187">See also</span></span>

- [<span data-ttu-id="a0c64-188">Śledzenie SQL</span><span class="sxs-lookup"><span data-stu-id="a0c64-188">SQL Tracking</span></span>](./samples/sql-tracking.md)
- <span data-ttu-id="a0c64-189">[Monitorowanie aplikacji sieci szkieletowej systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a0c64-189">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="a0c64-190">[Monitorowanie aplikacji przy użyciu sieci szkieletowej aplikacji](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a0c64-190">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
