---
title: Niestandardowe śledzenie
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: 2b100b877bbc8c6d830f09a4a59decffde511511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182838"
---
# <a name="custom-tracking"></a><span data-ttu-id="81177-102">Niestandardowe śledzenie</span><span class="sxs-lookup"><span data-stu-id="81177-102">Custom Tracking</span></span>
<span data-ttu-id="81177-103">W tym przykładzie pokazano, jak utworzyć niestandardowego uczestnika śledzenia i zapisać zawartość danych śledzenia do konsoli.</span><span class="sxs-lookup"><span data-stu-id="81177-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="81177-104">Ponadto w przykładzie pokazano, <xref:System.Activities.Tracking.CustomTrackingRecord> jak emitować obiekty wypełnione danymi zdefiniowanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="81177-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="81177-105">Uczestnik śledzenia oparty na konsoli <xref:System.Activities.Tracking.TrackingRecord> filtruje obiekty emitowane przez przepływ pracy przy użyciu obiektu profilu śledzenia utworzonego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="81177-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>

## <a name="sample-details"></a><span data-ttu-id="81177-106">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="81177-106">Sample Details</span></span>
 <span data-ttu-id="81177-107">Windows Workflow Foundation (WF) zapewnia infrastrukturę śledzenia do śledzenia wykonywania wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="81177-107">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="81177-108">Środowisko uruchomieniowe śledzenia implementuje wystąpienie przepływu pracy do emitowania zdarzeń związanych z cyklem życia przepływu pracy, zdarzeniami z działań przepływu pracy i niestandardowymi zdarzeniami śledzenia.</span><span class="sxs-lookup"><span data-stu-id="81177-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="81177-109">W poniższej tabeli przedstawiono podstawowe składniki infrastruktury śledzenia.</span><span class="sxs-lookup"><span data-stu-id="81177-109">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="81177-110">Składnik</span><span class="sxs-lookup"><span data-stu-id="81177-110">Component</span></span>|<span data-ttu-id="81177-111">Opis</span><span class="sxs-lookup"><span data-stu-id="81177-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="81177-112">Śledzenie środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="81177-112">Tracking runtime</span></span>|<span data-ttu-id="81177-113">Zapewnia infrastrukturę do emitowania rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="81177-113">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="81177-114">Śledzenie uczestników</span><span class="sxs-lookup"><span data-stu-id="81177-114">Tracking participants</span></span>|<span data-ttu-id="81177-115">Zużywa rekordy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="81177-115">Consumes the tracking records.</span></span> <span data-ttu-id="81177-116">Program .NET Framework 4 jest dostarczany z uczestnikiem śledzenia, który zapisuje rekordy śledzenia jako zdarzenia śledzenia zdarzeń dla systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="81177-116">.NET Framework 4 ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="81177-117">Profil śledzenia</span><span class="sxs-lookup"><span data-stu-id="81177-117">Tracking profile</span></span>|<span data-ttu-id="81177-118">Mechanizm filtrowania, który umożliwia uczestnikowi śledzenia subskrybowanie podzbioru rekordów śledzenia emitowanych z wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="81177-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="81177-119">W poniższej tabeli opisano rekordy śledzenia emitujące środowisko wykonawcze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="81177-119">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="81177-120">Rekord śledzenia</span><span class="sxs-lookup"><span data-stu-id="81177-120">Tracking Record</span></span>|<span data-ttu-id="81177-121">Opis</span><span class="sxs-lookup"><span data-stu-id="81177-121">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="81177-122">Rekordy śledzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="81177-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="81177-123">Opisuje cykl życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="81177-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="81177-124">Na przykład rekord wystąpienia jest emitowany po uruchomieniu lub zakończeniu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="81177-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="81177-125">Rekordy śledzenia stanu działania.</span><span class="sxs-lookup"><span data-stu-id="81177-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="81177-126">Szczegóły wykonania działania.</span><span class="sxs-lookup"><span data-stu-id="81177-126">Details activity execution.</span></span> <span data-ttu-id="81177-127">Te rekordy wskazują stan działania przepływu pracy, na przykład kiedy działanie jest zaplanowane lub po zakończeniu działania lub gdy zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="81177-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="81177-128">Rekord wznowienia zakładki.</span><span class="sxs-lookup"><span data-stu-id="81177-128">Bookmark resumption record.</span></span>|<span data-ttu-id="81177-129">Emitowana za każdym razem, gdy zakładka w wystąpieniu przepływu pracy zostanie wznowiona.</span><span class="sxs-lookup"><span data-stu-id="81177-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="81177-130">Niestandardowe rekordy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="81177-130">Custom Tracking Records.</span></span>|<span data-ttu-id="81177-131">Autor przepływu pracy może tworzyć niestandardowe rekordy śledzenia i emitować je w ramach działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="81177-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|

 <span data-ttu-id="81177-132">Uczestnik śledzenia subskrybuje podzbiór <xref:System.Activities.Tracking.TrackingRecord> emitowanych obiektów przy użyciu profilów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="81177-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="81177-133">Profil śledzenia zawiera zapytania śledzenia, które umożliwiają subskrybowanie określonego typu rekordu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="81177-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="81177-134">Profile śledzenia można określić w kodzie lub w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="81177-134">Tracking profiles can be specified in code or in configuration.</span></span>

### <a name="custom-tracking-participant"></a><span data-ttu-id="81177-135">Uczestnik śledzenia niestandardowego</span><span class="sxs-lookup"><span data-stu-id="81177-135">Custom Tracking Participant</span></span>
 <span data-ttu-id="81177-136">Interfejs API uczestnika śledzenia umożliwia rozszerzenie środowiska wykonawczego śledzenia z użytkownikiem <xref:System.Activities.Tracking.TrackingRecord> pod warunkiem uczestnika śledzenia, który może zawierać niestandardową logikę do obsługi obiektów emitowanych przez środowisko wykonawcze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="81177-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>

 <span data-ttu-id="81177-137">Aby napisać uczestnika śledzenia, <xref:System.Activities.Tracking.TrackingParticipant>użytkownik musi zaimplementować .</span><span class="sxs-lookup"><span data-stu-id="81177-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="81177-138">W szczególności <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metoda musi być zaimplementowana przez uczestnika niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="81177-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="81177-139">Ta metoda jest <xref:System.Activities.Tracking.TrackingRecord> wywoływana, gdy jest emitowany przez środowisko wykonawcze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="81177-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 <span data-ttu-id="81177-140">Uczestnik śledzenia całego jest implementowany w pliku ConsoleTrackingParticipant.cs.</span><span class="sxs-lookup"><span data-stu-id="81177-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.</span></span> <span data-ttu-id="81177-141">Poniższy przykład kodu <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> jest metodą dla niestandardowego uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="81177-141">The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>

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

 <span data-ttu-id="81177-142">Poniższy przykład kodu dodaje uczestnika konsoli do invoker przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="81177-142">The following code example adds the console participant to the workflow invoker.</span></span>

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

### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="81177-143">Emitowanie niestandardowych rekordów śledzenia</span><span class="sxs-lookup"><span data-stu-id="81177-143">Emitting Custom Tracking Records</span></span>
 <span data-ttu-id="81177-144">W tym przykładzie pokazano <xref:System.Activities.Tracking.CustomTrackingRecord> również możliwość emitowania obiektów z niestandardowego działania przepływu pracy:</span><span class="sxs-lookup"><span data-stu-id="81177-144">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>

- <span data-ttu-id="81177-145">Obiekty <xref:System.Activities.Tracking.CustomTrackingRecord> są tworzone i wypełniane danymi zdefiniowanymi przez użytkownika, które mają być emitowane wraz z rekordem.</span><span class="sxs-lookup"><span data-stu-id="81177-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>

- <span data-ttu-id="81177-146">Jest <xref:System.Activities.Tracking.CustomTrackingRecord> emitowany przez wywołanie metody <xref:System.Activities.ActivityContext>ścieżki .</span><span class="sxs-lookup"><span data-stu-id="81177-146">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>

 <span data-ttu-id="81177-147">W poniższym przykładzie <xref:System.Activities.Tracking.CustomTrackingRecord> pokazano, jak emitować obiekty w ramach działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="81177-147">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="81177-148">Aby użyć tej próbki</span><span class="sxs-lookup"><span data-stu-id="81177-148">To use this sample</span></span>

1. <span data-ttu-id="81177-149">Za pomocą programu Visual Studio 2010 otwórz plik rozwiązania CustomTrackingSample.sln.</span><span class="sxs-lookup"><span data-stu-id="81177-149">Using Visual Studio 2010, open the CustomTrackingSample.sln solution file.</span></span>

2. <span data-ttu-id="81177-150">Aby utworzyć rozwiązanie, naciśnij klawisze CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="81177-150">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="81177-151">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="81177-151">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="81177-152">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="81177-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="81177-153">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="81177-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="81177-154">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="81177-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81177-155">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="81177-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="81177-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81177-156">See also</span></span>

- <span data-ttu-id="81177-157">[Próbki monitorowania AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="81177-157">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
