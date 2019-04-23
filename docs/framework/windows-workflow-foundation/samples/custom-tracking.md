---
title: Niestandardowe śledzenie
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: 7e275af046013dcd76cb61c25ace1d96fd7e4b93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307639"
---
# <a name="custom-tracking"></a><span data-ttu-id="2decc-102">Niestandardowe śledzenie</span><span class="sxs-lookup"><span data-stu-id="2decc-102">Custom Tracking</span></span>
<span data-ttu-id="2decc-103">W tym przykładzie pokazano, jak tworzenie niestandardowego uczestnika śledzenia i zapisać zawartość danych śledzenia do konsoli.</span><span class="sxs-lookup"><span data-stu-id="2decc-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="2decc-104">Ponadto w przykładzie pokazano jak emitowanie <xref:System.Activities.Tracking.CustomTrackingRecord> danych zdefiniowane przez obiekty użytkownika jest wypełniony.</span><span class="sxs-lookup"><span data-stu-id="2decc-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="2decc-105">Filtry uczestnika śledzenia opartych na konsoli <xref:System.Activities.Tracking.TrackingRecord> obiektów emitowanych przez przepływ pracy korzystający z profilu śledzenia obiekt utworzony w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2decc-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>

## <a name="sample-details"></a><span data-ttu-id="2decc-106">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="2decc-106">Sample Details</span></span>
 <span data-ttu-id="2decc-107">Windows Workflow Foundation (WF) zapewnia infrastrukturę śledzenia do śledzenia wykonywania wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2decc-107">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="2decc-108">Środowisko uruchomieniowe śledzenia implementuje wystąpienia przepływu pracy, aby emitować zdarzenia związane z cyklem życia przepływu pracy, zdarzenia z działań przepływu pracy i zdarzenia niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2decc-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="2decc-109">W poniższej tabeli przedstawiono podstawowe składniki infrastruktury śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2decc-109">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="2decc-110">Składnik</span><span class="sxs-lookup"><span data-stu-id="2decc-110">Component</span></span>|<span data-ttu-id="2decc-111">Opis</span><span class="sxs-lookup"><span data-stu-id="2decc-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="2decc-112">Śledzenie czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="2decc-112">Tracking runtime</span></span>|<span data-ttu-id="2decc-113">Zapewnia infrastrukturę, aby emitować rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2decc-113">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="2decc-114">Uczestnicy śledzenia</span><span class="sxs-lookup"><span data-stu-id="2decc-114">Tracking participants</span></span>|<span data-ttu-id="2decc-115">Używa rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2decc-115">Consumes the tracking records.</span></span> [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] <span data-ttu-id="2decc-116">dostarczany z śledzenia uczestnika, który zapisuje rekordy śledzenia jako zdarzenia śledzenie zdarzeń dla Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="2decc-116">ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="2decc-117">Profil śledzenia</span><span class="sxs-lookup"><span data-stu-id="2decc-117">Tracking profile</span></span>|<span data-ttu-id="2decc-118">Mechanizm filtrowania, który umożliwia śledzenia uczestnika do subskrybowania dla podzbioru rekordów śledzenia emitowane z wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2decc-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="2decc-119">W poniższej tabeli przedstawiono rekordów śledzenia emitowane przez środowisko wykonawcze przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="2decc-119">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="2decc-120">Rekord śledzenia</span><span class="sxs-lookup"><span data-stu-id="2decc-120">Tracking Record</span></span>|<span data-ttu-id="2decc-121">Opis</span><span class="sxs-lookup"><span data-stu-id="2decc-121">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="2decc-122">Rekordy śledzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2decc-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="2decc-123">W tym artykule opisano cyklu życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2decc-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="2decc-124">Na przykład rekord wystąpienia jest emitowane, gdy przepływ pracy rozpoczyna się lub kończy.</span><span class="sxs-lookup"><span data-stu-id="2decc-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="2decc-125">Stan śledzenia rekordów działań.</span><span class="sxs-lookup"><span data-stu-id="2decc-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="2decc-126">Szczegóły wykonania działania.</span><span class="sxs-lookup"><span data-stu-id="2decc-126">Details activity execution.</span></span> <span data-ttu-id="2decc-127">Te informacje wskazują stan działania przepływu pracy, takie jak kiedy zaplanowano działania lub po zakończeniu działania lub kiedy zostanie wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="2decc-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="2decc-128">Zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="2decc-128">Bookmark resumption record.</span></span>|<span data-ttu-id="2decc-129">Emitowane przy każdym zakładki w ramach wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="2decc-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="2decc-130">Niestandardowe rekordy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2decc-130">Custom Tracking Records.</span></span>|<span data-ttu-id="2decc-131">Tworzenie przepływu pracy można utworzyć niestandardowe rekordy śledzenia i emitować je w ramach działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="2decc-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|

 <span data-ttu-id="2decc-132">Uczestnik śledzenia subskrybuje dla podzbioru emitowany <xref:System.Activities.Tracking.TrackingRecord> obiektów przy użyciu profilów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2decc-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="2decc-133">Profil śledzenia zawiera śledzenia zapytań, zezwalających na subskrypcji dla śledzenia określonego typu rekordu.</span><span class="sxs-lookup"><span data-stu-id="2decc-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="2decc-134">Śledzenie profile można określić w kodzie lub w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2decc-134">Tracking profiles can be specified in code or in configuration.</span></span>

### <a name="custom-tracking-participant"></a><span data-ttu-id="2decc-135">Niestandardowego uczestnika śledzenia</span><span class="sxs-lookup"><span data-stu-id="2decc-135">Custom Tracking Participant</span></span>
 <span data-ttu-id="2decc-136">Uczestnik śledzenia interfejsu API umożliwia rozszerzenie środowiska uruchomieniowego śledzenia z uczestnika śledzenia dostarczone przez użytkownika, który może zawierać niestandardowej logiki do obsługi <xref:System.Activities.Tracking.TrackingRecord> obiektów emitowanych przez środowisko wykonawcze przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="2decc-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>

 <span data-ttu-id="2decc-137">Można zapisać do śledzenia uczestnika użytkownik musi implementować <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="2decc-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="2decc-138">W szczególności <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metoda musi być implementowana przez uczestnikiem niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="2decc-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="2decc-139">Ta metoda jest wywoływana, gdy <xref:System.Activities.Tracking.TrackingRecord> są emitowane przez środowisko wykonawcze przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="2decc-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 <span data-ttu-id="2decc-140">Pełną śledzenia uczestnika, który jest wdrażany w pliku ConsoleTrackingParticipant.cs. Poniższy przykład kodu jest <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metodę dla niestandardowego uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2decc-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>

```csharp
protected override void Track(TrackingRecord record, TimeSpan timeout)
{
    ...
    WorkflowInstanceRecord workflowInstanceRecord = record as WorkflowInstanceRecord;
    if (workflowInstanceRecord != null)
    {
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,
            " Workflow InstanceID: {0} Workflow instance state: {1}",
            record.InstanceId, workflowInstanceRecord.State));
    }

    ActivityStateRecord activityStateRecord = record as ActivityStateRecord;
    if (activityStateRecord != null)
    {
        IDictionary<String, object> variables = activityStateRecord.Variables;
        StringBuilder vars = new StringBuilder();

        if (variables.Count > 0)
        {
            vars.AppendLine("\n\tVariables:");
            foreach (KeyValuePair<string, object> variable in variables)
            {
                vars.AppendLine(String.Format(
                    "\t\tName: {0} Value: {1}", variable.Key, variable.Value));
            }
        }
        Console.WriteLine(String.Format(CultureInfo.InvariantCulture,
            " :Activity DisplayName: {0} :ActivityInstanceState: {1} {2}",
                activityStateRecord.Activity.Name, activityStateRecord.State,
            ((variables.Count > 0) ? vars.ToString() : String.Empty)));
    }

    CustomTrackingRecord customTrackingRecord = record as CustomTrackingRecord;

    if ((customTrackingRecord != null) && (customTrackingRecord.Data.Count > 0))
    {
        ...
    }
    Console.WriteLine();

}
```

 <span data-ttu-id="2decc-141">Poniższy przykład kodu dodaje uczestnika konsoli do wywoływania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2decc-141">The following code example adds the console participant to the workflow invoker.</span></span>

```csharp
ConsoleTrackingParticipant customTrackingParticipant = new ConsoleTrackingParticipant()
{
    ...
    // The tracking profile is set here, refer to Program.CS
...
}

WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
```

### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="2decc-142">Emitowanie niestandardowe rekordy śledzenia</span><span class="sxs-lookup"><span data-stu-id="2decc-142">Emitting Custom Tracking Records</span></span>
 <span data-ttu-id="2decc-143">Niniejszy przykład pokazuje także możliwość emisji <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów z działanie niestandardowego przepływu pracy:</span><span class="sxs-lookup"><span data-stu-id="2decc-143">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>

-   <span data-ttu-id="2decc-144"><xref:System.Activities.Tracking.CustomTrackingRecord> Obiekty są tworzone i wypełniane przy użyciu danych zdefiniowane przez użytkownika, którego pożądany jest emitowane z rekordem.</span><span class="sxs-lookup"><span data-stu-id="2decc-144">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>

-   <span data-ttu-id="2decc-145"><xref:System.Activities.Tracking.CustomTrackingRecord> Są emitowane przez wywołanie metody śledzenia <xref:System.Activities.ActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="2decc-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>

 <span data-ttu-id="2decc-146">W poniższym przykładzie pokazano sposób emitować <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów w ramach działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="2decc-146">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>

```csharp
// Create the Custom Tracking Record
CustomTrackingRecord customRecord = new CustomTrackingRecord("OrderIn")
{
    Data =
    {
        {"OrderId", 200},
        {"OrderDate", "20 Aug 2001"}
    }
};

// Emit custom tracking record
context.Track(customRecord);
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="2decc-147">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="2decc-147">To use this sample</span></span>

1. <span data-ttu-id="2decc-148">Za pomocą programu Visual Studio 2010, otwórz plik rozwiązania CustomTrackingSample.sln.</span><span class="sxs-lookup"><span data-stu-id="2decc-148">Using Visual Studio 2010, open the CustomTrackingSample.sln solution file.</span></span>

2. <span data-ttu-id="2decc-149">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="2decc-149">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="2decc-150">Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="2decc-150">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="2decc-151">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2decc-151">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2decc-152">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2decc-152">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2decc-153">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="2decc-153">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2decc-154">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2decc-154">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="2decc-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2decc-155">See also</span></span>

- [<span data-ttu-id="2decc-156">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="2decc-156">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
