---
title: Profile śledzenia
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 9723b8fbb0bb8f24e8c9544d8bac8252b2fc763a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182729"
---
# <a name="tracking-profiles"></a><span data-ttu-id="60d95-102">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="60d95-102">Tracking Profiles</span></span>

<span data-ttu-id="60d95-103">Profile śledzenia zawierają zapytania śledzenia, które umożliwiają uczestnikowi śledzenia subskrybowanie zdarzeń przepływu pracy, które są emitowane, gdy stan wystąpienia przepływu pracy zmienia się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="60d95-103">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>

## <a name="tracking-profiles"></a><span data-ttu-id="60d95-104">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="60d95-104">Tracking Profiles</span></span>

<span data-ttu-id="60d95-105">Profile śledzenia służą do określania, które informacje o śledzeniu są emitowane dla wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="60d95-105">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="60d95-106">Jeśli nie określono profilu, wszystkie zdarzenia śledzenia są emitowane.</span><span class="sxs-lookup"><span data-stu-id="60d95-106">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="60d95-107">Jeśli profil zostanie określony, zostaną wyemitowane zdarzenia śledzenia określone w profilu.</span><span class="sxs-lookup"><span data-stu-id="60d95-107">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="60d95-108">W zależności od wymagań monitorowania można napisać profil, który jest bardzo ogólny, który subskrybuje mały zestaw zmian stanu wysokiego poziomu w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="60d95-108">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="60d95-109">Z drugiej strony można utworzyć bardzo szczegółowy profil, którego wynikowe zdarzenia są wystarczająco bogate, aby później odtworzyć szczegółowy przepływ wykonania.</span><span class="sxs-lookup"><span data-stu-id="60d95-109">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>

<span data-ttu-id="60d95-110">Profile śledzenia manifestują się jako elementy XML w standardowym pliku konfiguracyjnym programu .NET Framework lub są określone w kodzie.</span><span class="sxs-lookup"><span data-stu-id="60d95-110">Tracking profiles manifest themselves as XML elements within a standard .NET Framework configuration file or specified in code.</span></span> <span data-ttu-id="60d95-111">Poniższy przykład jest [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] profilu śledzenia w pliku konfiguracji, który umożliwia uczestnikowi śledzenia subskrybować zdarzenia `Started` i `Completed` przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="60d95-111">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>

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

<span data-ttu-id="60d95-112">W poniższym przykładzie przedstawiono równoważny profil śledzenia utworzony przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="60d95-112">The following example shows the equivalent tracking profile created using code.</span></span>

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

<span data-ttu-id="60d95-113">Rekordy śledzenia są filtrowane w trybie widoczności <xref:System.Activities.Tracking.ImplementationVisibility> w profilu śledzenia przy użyciu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="60d95-113">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="60d95-114">Działanie złożone jest działaniem najwyższego poziomu, które zawiera inne działania, które tworzą jego implementację.</span><span class="sxs-lookup"><span data-stu-id="60d95-114">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="60d95-115">Tryb widoczności określa rekordy śledzenia emitowane z działań złożonych w ramach działania przepływu pracy, aby określić, czy działania, które tworzą implementację są śledzone.</span><span class="sxs-lookup"><span data-stu-id="60d95-115">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span> <span data-ttu-id="60d95-116">Tryb widoczności ma zastosowanie na poziomie profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="60d95-116">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="60d95-117">Filtrowanie rekordów śledzenia dla poszczególnych działań w ramach przepływu pracy jest kontrolowane przez zapytania w profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="60d95-117">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="60d95-118">Aby uzyskać więcej informacji, zobacz sekcję **Typy zapytań profilu śledzenia** w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="60d95-118">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>

<span data-ttu-id="60d95-119">Dwa tryby widoczności `implementationVisibility` określone przez atrybut w `RootScope` `All`profilu śledzenia są i .</span><span class="sxs-lookup"><span data-stu-id="60d95-119">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="60d95-120">Za `RootScope` pomocą trybu pomija rekordy śledzenia dla działań, które tworzą implementację działania w przypadku, gdy działanie złożone nie jest głównym przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="60d95-120">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span> <span data-ttu-id="60d95-121">Oznacza to, że gdy działanie, które jest implementowane przy użyciu innych `implementationVisibility` działań jest dodawany do przepływu pracy i zestaw rootscope, tylko działania najwyższego poziomu w ramach tego działania złożonego jest śledzony.</span><span class="sxs-lookup"><span data-stu-id="60d95-121">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="60d95-122">Jeśli działanie jest głównym przepływem pracy, implementacja działania jest samym przepływem pracy i rekordami śledzenia są emitowane dla działań, które tworzą implementację.</span><span class="sxs-lookup"><span data-stu-id="60d95-122">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="60d95-123">Tryb Wszystkie umożliwia emitowanie wszystkich rekordów śledzenia dla działania głównego i wszystkich jego działań złożonych.</span><span class="sxs-lookup"><span data-stu-id="60d95-123">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>

<span data-ttu-id="60d95-124">Załóżmy na przykład, że *MyActivity* jest działaniem złożonym, którego implementacja zawiera dwa działania: *Activity1* i *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="60d95-124">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span> <span data-ttu-id="60d95-125">Gdy to działanie zostanie dodane do przepływu pracy, a `implementationVisibility` śledzenie `RootScope`jest włączone z profilem śledzenia z ustawionym na , rekordy śledzenia są emitowane tylko dla *MyActivity*.</span><span class="sxs-lookup"><span data-stu-id="60d95-125">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span> <span data-ttu-id="60d95-126">Jednak dla działań *Activity1* i *Activity2*nie są emitowane żadne rekordy.</span><span class="sxs-lookup"><span data-stu-id="60d95-126">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="60d95-127">Jeśli jednak `implementationVisibility` atrybut profilu śledzenia jest ustawiony `All`na , a następnie rekordy śledzenia są emitowane nie tylko dla *MyActivity,* ale także dla działań *Activity1* i *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="60d95-127">However, if the `implementationVisibility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="60d95-128">Flaga `implementationVisibility` dotyczy następujących typów rekordów śledzenia:</span><span class="sxs-lookup"><span data-stu-id="60d95-128">The `implementationVisibility` flag applies to following tracking record types:</span></span>

- <span data-ttu-id="60d95-129">Activitystaterecord</span><span class="sxs-lookup"><span data-stu-id="60d95-129">ActivityStateRecord</span></span>

- <span data-ttu-id="60d95-130">Faultpropagationrecord</span><span class="sxs-lookup"><span data-stu-id="60d95-130">FaultPropagationRecord</span></span>

- <span data-ttu-id="60d95-131">Cancelrequestedrecord</span><span class="sxs-lookup"><span data-stu-id="60d95-131">CancelRequestedRecord</span></span>

- <span data-ttu-id="60d95-132">Activityscheduledrecord</span><span class="sxs-lookup"><span data-stu-id="60d95-132">ActivityScheduledRecord</span></span>

> [!NOTE]
> <span data-ttu-id="60d95-133">CustomTrackingRecords emitowane z implementacji działania nie są odfiltrowywały przez implementacjęStawianie.</span><span class="sxs-lookup"><span data-stu-id="60d95-133">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>

<span data-ttu-id="60d95-134">Funkcja `implementationVisibility` jest określona <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> jako profil śledzenia w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="60d95-134">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

<span data-ttu-id="60d95-135">Funkcja `implementationVisibility` jest określona <xref:System.Activities.Tracking.ImplementationVisibility.All> jako profil śledzenia w pliku konfiguracyjnym w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="60d95-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>

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

<span data-ttu-id="60d95-136">Ustawienie `ImplementationVisibility` w profilu śledzenia jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="60d95-136">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="60d95-137">Domyślnie jego wartość jest `RootScope`ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="60d95-137">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="60d95-138">W wartościach dla tego atrybutu jest również rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="60d95-138">The values for this attribute are also case-sensitive.</span></span>

### <a name="tracking-profile-query-types"></a><span data-ttu-id="60d95-139">Typy zapytań profilu śledzenia</span><span class="sxs-lookup"><span data-stu-id="60d95-139">Tracking Profile Query Types</span></span>

<span data-ttu-id="60d95-140">Profile śledzenia mają strukturę jako deklaratywne subskrypcji dla śledzenia rekordy, które umożliwiają zapytania dla rekordów śledzenie wersję wykonawczą przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="60d95-140">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="60d95-141">Istnieje kilka typów zapytań, które umożliwiają subskrybowanie różnych klas <xref:System.Activities.Tracking.TrackingRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="60d95-141">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="60d95-142">Profile śledzenia można określić w konfiguracji lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="60d95-142">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="60d95-143">Oto najczęściej spotykane typy zapytań:</span><span class="sxs-lookup"><span data-stu-id="60d95-143">Here are the most common query types:</span></span>

- <span data-ttu-id="60d95-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery>- Użyj tego do śledzenia zmian cyklu życia wystąpienia `Started` `Completed`przepływu pracy, takich jak wcześniej zademonstrowane i .</span><span class="sxs-lookup"><span data-stu-id="60d95-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="60d95-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="60d95-145">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  <span data-ttu-id="60d95-146">Stany, które można subskrybować są <xref:System.Activities.Tracking.WorkflowInstanceStates> określone w klasie.</span><span class="sxs-lookup"><span data-stu-id="60d95-146">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>

  <span data-ttu-id="60d95-147">Konfiguracja lub kod używany do subskrybowania rekordów `Started` śledzenia na <xref:System.Activities.Tracking.WorkflowInstanceQuery> poziomie wystąpienia przepływu pracy dla stanu wystąpienia przy użyciu stanu jest wyświetlany w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="60d95-147">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="60d95-148"><xref:System.Activities.Tracking.ActivityStateQuery>- Użyj tego do śledzenia zmian cyklu życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="60d95-148"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="60d95-149">Na przykład można śledzić za każdym razem, gdy działanie "Wyślij e-mail" zostanie ukończone w wystąpieniu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="60d95-149">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="60d95-150">Ta kwerenda jest <xref:System.Activities.Tracking.TrackingParticipant> niezbędna do <xref:System.Activities.Tracking.ActivityStateRecord> subskrybowania obiektów.</span><span class="sxs-lookup"><span data-stu-id="60d95-150">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="60d95-151">Dostępne stany do subskrybowania <xref:System.Activities.Tracking.ActivityStates>są określone w .</span><span class="sxs-lookup"><span data-stu-id="60d95-151">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>

  <span data-ttu-id="60d95-152">Konfiguracja i kod używany do subskrybowania <xref:System.Activities.Tracking.ActivityStateQuery> rekordów `SendEmailActivity` śledzenia stanu działania, które używają dla działania jest pokazany w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="60d95-152">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>

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
  > <span data-ttu-id="60d95-153">Jeśli wiele activityStateQuery elementy mają taką samą nazwę, tylko stany w ostatnim elemencie są używane w profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="60d95-153">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>

- <span data-ttu-id="60d95-154"><xref:System.Activities.Tracking.ActivityScheduledQuery>- Ta kwerenda umożliwia śledzenie działania zaplanowanego do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="60d95-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="60d95-155">Kwerenda jest niezbędna <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.ActivityScheduledRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="60d95-155">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>

  <span data-ttu-id="60d95-156">Konfiguracja i kod używany do subskrybowania rekordów związanych z aktywnością podrzędną `SendEmailActivity` zaplanowaną <xref:System.Activities.Tracking.ActivityScheduledQuery> przy użyciu jest pokazany w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="60d95-156">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="60d95-157"><xref:System.Activities.Tracking.FaultPropagationQuery>- Użyj tego do śledzenia obsługi usterek występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="60d95-157"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="60d95-158">Kwerenda jest niezbędna <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.FaultPropagationRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="60d95-158">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>

  <span data-ttu-id="60d95-159">Konfiguracja i kod używany do subskrybowania rekordów <xref:System.Activities.Tracking.FaultPropagationQuery> związanych z propagacją błędów za pomocą jest pokazany w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="60d95-159">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="60d95-160"><xref:System.Activities.Tracking.CancelRequestedQuery>- Użyj tego do śledzenia żądań anulowania działania podrzędnego przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="60d95-160"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="60d95-161">Kwerenda jest niezbędna <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.CancelRequestedRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="60d95-161">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>

  <span data-ttu-id="60d95-162">Konfiguracja i kod używany do subskrybowania <xref:System.Activities.Tracking.CancelRequestedQuery> rekordów związanych z anulowaniem działania przy użyciu jest pokazany w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="60d95-162">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="60d95-163"><xref:System.Activities.Tracking.CustomTrackingQuery>- Użyj tego do śledzenia zdarzeń, które można zdefiniować w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="60d95-163"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="60d95-164">Kwerenda jest niezbędna <xref:System.Activities.Tracking.TrackingParticipant> do subskrybowania <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów.</span><span class="sxs-lookup"><span data-stu-id="60d95-164">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>

  <span data-ttu-id="60d95-165">Konfiguracja i kod używany do subskrybowania rekordów związanych z niestandardowymi rekordami śledzenia za pomocą <xref:System.Activities.Tracking.CustomTrackingQuery> jest pokazany w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="60d95-165">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="60d95-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery>- Użyj tego, aby śledzić wznowienie zakładki w wystąpieniu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="60d95-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="60d95-167">Ta kwerenda jest <xref:System.Activities.Tracking.TrackingParticipant> niezbędna do <xref:System.Activities.Tracking.BookmarkResumptionRecord> subskrybowania obiektów.</span><span class="sxs-lookup"><span data-stu-id="60d95-167">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>

  <span data-ttu-id="60d95-168">Konfiguracja i kod używany do subskrybowania rekordów <xref:System.Activities.Tracking.BookmarkResumptionQuery> związanych z wznowieni zakładówek owanie przy użyciu jest pokazany w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="60d95-168">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>

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

### <a name="annotations"></a><span data-ttu-id="60d95-169">Adnotacje</span><span class="sxs-lookup"><span data-stu-id="60d95-169">Annotations</span></span>

<span data-ttu-id="60d95-170">Adnotacje umożliwiają arbitralnie tag śledzenia rekordów o wartości, które mogą być skonfigurowane po czas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="60d95-170">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="60d95-171">Na przykład można dodać kilka rekordów śledzenia w kilku przepływach pracy tagiem "Serwer poczty" == "Serwer poczty1".</span><span class="sxs-lookup"><span data-stu-id="60d95-171">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="60d95-172">To ułatwia znalezienie wszystkich rekordów z tym znacznikiem podczas wykonywania zapytania rekordów śledzenia później.</span><span class="sxs-lookup"><span data-stu-id="60d95-172">This makes it easy to find all records with this tag when querying tracking records later.</span></span>

<span data-ttu-id="60d95-173">Aby to osiągnąć, adnotacja jest dodawana do kwerendy śledzącej, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="60d95-173">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>

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

### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="60d95-174">Jak utworzyć profil śledzenia</span><span class="sxs-lookup"><span data-stu-id="60d95-174">How to Create a Tracking Profile</span></span>

<span data-ttu-id="60d95-175">Elementy zapytania śledzenia są używane do tworzenia profilu śledzenia przy [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] użyciu pliku konfiguracyjnego XML lub kodu.</span><span class="sxs-lookup"><span data-stu-id="60d95-175">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] code.</span></span> <span data-ttu-id="60d95-176">Oto przykład profilu śledzenia utworzonego przy użyciu pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="60d95-176">Here is an example of a tracking profile created using a configuration file.</span></span>

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
> <span data-ttu-id="60d95-177">W przypadku WF przy użyciu hosta usługi przepływ pracy profil śledzenia jest zazwyczaj tworzony przy użyciu pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="60d95-177">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="60d95-178">Istnieje również możliwość utworzenia profilu śledzenia z kodem przy użyciu profilu śledzenia i śledzenia interfejsu API kwerendy.</span><span class="sxs-lookup"><span data-stu-id="60d95-178">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>

<span data-ttu-id="60d95-179">Profil skonfigurowany jako plik konfiguracyjny XML jest stosowany do uczestnika śledzenia przy użyciu rozszerzenia zachowania.</span><span class="sxs-lookup"><span data-stu-id="60d95-179">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="60d95-180">Zostanie on dodany do workflowServiceHost zgodnie z opisem w dalszej sekcji [Konfigurowanie śledzenia dla przepływu pracy](configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="60d95-180">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](configuring-tracking-for-a-workflow.md).</span></span>

<span data-ttu-id="60d95-181">Szczegółowość rekordów śledzenia emitowanych przez hosta zależy od ustawień konfiguracji w profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="60d95-181">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="60d95-182">Uczestnik śledzenia subskrybuje rekordy śledzenia, dodając zapytania do profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="60d95-182">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="60d95-183">Aby zasubskrybować wszystkie rekordy śledzenia, profil śledzenia musi\*określić wszystkie zapytania śledzenia za pomocą " " w polach nazw w każdym z kwerend.</span><span class="sxs-lookup"><span data-stu-id="60d95-183">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "\*" in the name fields in each of the queries.</span></span>

<span data-ttu-id="60d95-184">Oto niektóre z typowych przykładów profili śledzenia.</span><span class="sxs-lookup"><span data-stu-id="60d95-184">Here are some of the common examples of tracking profiles.</span></span>

- <span data-ttu-id="60d95-185">Profil śledzenia w celu uzyskania rekordów wystąpienia przepływu pracy i usterek.</span><span class="sxs-lookup"><span data-stu-id="60d95-185">A tracking profile to obtain workflow instance records and faults.</span></span>

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

- <span data-ttu-id="60d95-186">Profil śledzenia w celu uzyskania wszystkich niestandardowych rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="60d95-186">A tracking profile to obtain all custom tracking records.</span></span>

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a><span data-ttu-id="60d95-187">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60d95-187">See also</span></span>

- [<span data-ttu-id="60d95-188">Śledzenie SQL</span><span class="sxs-lookup"><span data-stu-id="60d95-188">SQL Tracking</span></span>](./samples/sql-tracking.md)
- <span data-ttu-id="60d95-189">[Monitorowanie sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="60d95-189">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="60d95-190">[Monitorowanie aplikacji za pomocą sieci szkieletowej aplikacji](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="60d95-190">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
