---
title: Niestandardowe śledzenie
ms.date: 03/30/2017
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
ms.openlocfilehash: 0d9bd9262c6fc13a36fb7736245fa244ee61d8c3
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710885"
---
# <a name="custom-tracking"></a><span data-ttu-id="b428d-102">Niestandardowe śledzenie</span><span class="sxs-lookup"><span data-stu-id="b428d-102">Custom Tracking</span></span>
<span data-ttu-id="b428d-103">Ten przykład pokazuje, jak utworzyć niestandardowego uczestnika śledzenia i zapisać zawartość śledzenia danych w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="b428d-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="b428d-104">Ponadto przykład pokazuje, jak emitować obiekty <xref:System.Activities.Tracking.CustomTrackingRecord> wypełnione danymi zdefiniowanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b428d-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="b428d-105">Uczestnik śledzenia oparty na konsoli filtruje <xref:System.Activities.Tracking.TrackingRecord> obiekty emitowane przez przepływ pracy przy użyciu obiektu profil śledzenia utworzonego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b428d-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>

## <a name="sample-details"></a><span data-ttu-id="b428d-106">Przykładowe szczegóły</span><span class="sxs-lookup"><span data-stu-id="b428d-106">Sample Details</span></span>
 <span data-ttu-id="b428d-107">Windows Workflow Foundation (WF) oferuje infrastrukturę śledzenia do śledzenia wykonywania wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b428d-107">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="b428d-108">Środowisko uruchomieniowe śledzenia implementuje wystąpienie przepływu pracy, aby emitować zdarzenia związane z cyklem życia przepływu pracy, zdarzenia z działań przepływu pracy i niestandardowe zdarzenia śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b428d-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="b428d-109">W poniższej tabeli przedstawiono podstawowe składniki infrastruktury śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b428d-109">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="b428d-110">Składnik</span><span class="sxs-lookup"><span data-stu-id="b428d-110">Component</span></span>|<span data-ttu-id="b428d-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b428d-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="b428d-112">Śledzenie środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b428d-112">Tracking runtime</span></span>|<span data-ttu-id="b428d-113">Udostępnia infrastrukturę do emisji rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b428d-113">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="b428d-114">Śledzenie uczestników</span><span class="sxs-lookup"><span data-stu-id="b428d-114">Tracking participants</span></span>|<span data-ttu-id="b428d-115">Używa rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b428d-115">Consumes the tracking records.</span></span> <span data-ttu-id="b428d-116">.NET Framework 4 dostarcza uczestnika śledzenia, który zapisuje rekordy śledzenia jako zdarzenia śledzenia zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="b428d-116">.NET Framework 4 ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="b428d-117">Profil śledzenia</span><span class="sxs-lookup"><span data-stu-id="b428d-117">Tracking profile</span></span>|<span data-ttu-id="b428d-118">Mechanizm filtrowania umożliwiający uczestnikom śledzenia subskrybowanie podzbioru rekordów śledzenia emitowanych z wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b428d-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="b428d-119">W poniższej tabeli przedstawiono szczegółowe informacje o rekordach śledzenia, które są emitowane przez środowisko uruchomieniowe przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b428d-119">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="b428d-120">Rekord śledzenia</span><span class="sxs-lookup"><span data-stu-id="b428d-120">Tracking Record</span></span>|<span data-ttu-id="b428d-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b428d-121">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="b428d-122">Rekordy śledzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b428d-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="b428d-123">Opisuje cykl życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b428d-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="b428d-124">Na przykład rekord wystąpienia jest emitowany, gdy przepływ pracy zostanie uruchomiony lub zakończony.</span><span class="sxs-lookup"><span data-stu-id="b428d-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="b428d-125">Rekordy śledzenia stanu działania.</span><span class="sxs-lookup"><span data-stu-id="b428d-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="b428d-126">Szczegóły wykonywania działania.</span><span class="sxs-lookup"><span data-stu-id="b428d-126">Details activity execution.</span></span> <span data-ttu-id="b428d-127">Te rekordy wskazują stan działania przepływu pracy, np. Kiedy działanie zostało zaplanowane lub gdy działanie zostało zakończone lub gdy zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="b428d-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="b428d-128">Rekord wznowienia zakładki.</span><span class="sxs-lookup"><span data-stu-id="b428d-128">Bookmark resumption record.</span></span>|<span data-ttu-id="b428d-129">Emitowane za każdym razem, gdy zostanie wznowiona Zakładka w wystąpieniu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b428d-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="b428d-130">Niestandardowe rekordy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b428d-130">Custom Tracking Records.</span></span>|<span data-ttu-id="b428d-131">Autor przepływu pracy może tworzyć niestandardowe rekordy śledzenia i emitować je w ramach działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b428d-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|

 <span data-ttu-id="b428d-132">Uczestnik śledzenia subskrybuje podzbiór wyemitowanych <xref:System.Activities.Tracking.TrackingRecord> obiektów przy użyciu profilów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b428d-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="b428d-133">Profil śledzenia zawiera kwerendy śledzenia, które umożliwiają subskrybowanie określonego typu rekordu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b428d-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="b428d-134">Profile śledzenia można określić w kodzie lub w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b428d-134">Tracking profiles can be specified in code or in configuration.</span></span>

### <a name="custom-tracking-participant"></a><span data-ttu-id="b428d-135">Uczestnik śledzenia niestandardowego</span><span class="sxs-lookup"><span data-stu-id="b428d-135">Custom Tracking Participant</span></span>
 <span data-ttu-id="b428d-136">Interfejs API uczestnika śledzenia umożliwia rozszerzenie środowiska uruchomieniowego śledzenia przy użyciu dostarczonego przez użytkownika uczestnika śledzenia, który może uwzględniać logikę niestandardową do obsługi <xref:System.Activities.Tracking.TrackingRecord> obiektów emitowanych przez środowisko uruchomieniowe przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b428d-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>

 <span data-ttu-id="b428d-137">Aby napisać uczestnika śledzenia, użytkownik musi zaimplementować <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="b428d-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="b428d-138">W od<xref:System.Activities.Tracking.TrackingParticipant.Track%2A> Metoda musi być implementowana przez uczestnika niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="b428d-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="b428d-139">Ta metoda jest wywoływana, gdy <xref:System.Activities.Tracking.TrackingRecord> jest emitowany przez środowisko uruchomieniowe przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b428d-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>

```csharp
public abstract class TrackingParticipant
{
    protected TrackingParticipant();

    public virtual TrackingProfile TrackingProfile { get; set; }
    public abstract void Track(TrackingRecord record, TimeSpan timeout);
}
```

 <span data-ttu-id="b428d-140">Pełny Uczestnik śledzenia jest implementowany w pliku ConsoleTrackingParticipant.cs.</span><span class="sxs-lookup"><span data-stu-id="b428d-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.</span></span> <span data-ttu-id="b428d-141">Poniższy przykład kodu jest metodą <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> niestandardowego uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b428d-141">The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>

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

 <span data-ttu-id="b428d-142">Poniższy przykład kodu dodaje uczestnika konsoli do przepływu pracy źródło.</span><span class="sxs-lookup"><span data-stu-id="b428d-142">The following code example adds the console participant to the workflow invoker.</span></span>

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

### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="b428d-143">Emitowanie niestandardowych rekordów śledzenia</span><span class="sxs-lookup"><span data-stu-id="b428d-143">Emitting Custom Tracking Records</span></span>
 <span data-ttu-id="b428d-144">Ten przykład ilustruje również możliwość emitowania <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów z niestandardowego działania przepływu pracy:</span><span class="sxs-lookup"><span data-stu-id="b428d-144">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>

- <span data-ttu-id="b428d-145">Obiekty <xref:System.Activities.Tracking.CustomTrackingRecord> są tworzone i wypełniane danymi zdefiniowanymi przez użytkownika, które są wymagane do emisji z rekordem.</span><span class="sxs-lookup"><span data-stu-id="b428d-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>

- <span data-ttu-id="b428d-146"><xref:System.Activities.Tracking.CustomTrackingRecord> jest emitowany przez wywołanie metody Track <xref:System.Activities.ActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="b428d-146">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>

 <span data-ttu-id="b428d-147">W poniższym przykładzie pokazano, jak emitować <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów w działaniu niestandardowym.</span><span class="sxs-lookup"><span data-stu-id="b428d-147">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>

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

#### <a name="to-use-this-sample"></a><span data-ttu-id="b428d-148">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="b428d-148">To use this sample</span></span>

1. <span data-ttu-id="b428d-149">Za pomocą programu Visual Studio 2010 Otwórz plik rozwiązania CustomTrackingSample. sln.</span><span class="sxs-lookup"><span data-stu-id="b428d-149">Using Visual Studio 2010, open the CustomTrackingSample.sln solution file.</span></span>

2. <span data-ttu-id="b428d-150">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b428d-150">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="b428d-151">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="b428d-151">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b428d-152">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b428d-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b428d-153">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="b428d-153">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="b428d-154">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b428d-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b428d-155">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b428d-155">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="b428d-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b428d-156">See also</span></span>

- [<span data-ttu-id="b428d-157">Przykłady monitorowania oprogramowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="b428d-157">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
