---
title: Niestandardowe śledzenia
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d191c9f-62f4-4c63-92dd-cda917fcf254
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 71eb3adaae6a474cf4e0766029c549dfe3a08383
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="custom-tracking"></a><span data-ttu-id="d263f-102">Niestandardowe śledzenia</span><span class="sxs-lookup"><span data-stu-id="d263f-102">Custom Tracking</span></span>
<span data-ttu-id="d263f-103">W tym przykładzie pokazano, jak utworzyć uczestnika niestandardowych śledzenia i zapisanie zawartości dane śledzenia do konsoli.</span><span class="sxs-lookup"><span data-stu-id="d263f-103">This sample demonstrates how to create a custom tracking participant and write the contents of the tracking data to console.</span></span> <span data-ttu-id="d263f-104">Ponadto przykładzie pokazano, jak Emituj <xref:System.Activities.Tracking.CustomTrackingRecord> dane zdefiniowanego przez obiekty wypełnione z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="d263f-104">In addition, the sample demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects populated with user defined data.</span></span> <span data-ttu-id="d263f-105">Filtry uczestnika opartych na konsoli śledzenia <xref:System.Activities.Tracking.TrackingRecord> obiektów emitowanych przez przepływ pracy korzystający z profilu śledzenia obiektu utworzonego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d263f-105">The console-based tracking participant filters the <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow using a tracking profile object created in code.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="d263f-106">Szczegóły próbki</span><span class="sxs-lookup"><span data-stu-id="d263f-106">Sample Details</span></span>  
 <span data-ttu-id="d263f-107">Windows Workflow Foundation (WF) zapewnia infrastrukturę śledzenia do śledzenia wykonywania wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d263f-107">Windows Workflow Foundation (WF) provides a tracking infrastructure to track execution of a workflow instance.</span></span> <span data-ttu-id="d263f-108">Środowisko uruchomieniowe śledzenia implementuje wystąpienia przepływu pracy do wysyłania zdarzeń związanych z cyklem życia przepływu pracy, zdarzenia z działań przepływu pracy i niestandardowych śledzenia zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d263f-108">The tracking runtime implements a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom tracking events.</span></span> <span data-ttu-id="d263f-109">W poniższej tabeli przedstawiono podstawowe składniki infrastruktury śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d263f-109">The following table details the primary components of the tracking infrastructure.</span></span>  
  
|<span data-ttu-id="d263f-110">Składnik</span><span class="sxs-lookup"><span data-stu-id="d263f-110">Component</span></span>|<span data-ttu-id="d263f-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d263f-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d263f-112">Śledzenie czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="d263f-112">Tracking runtime</span></span>|<span data-ttu-id="d263f-113">Zapewnia infrastrukturę do emisji rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d263f-113">Provides the infrastructure to emit tracking records.</span></span>|  
|<span data-ttu-id="d263f-114">Uczestników śledzenia</span><span class="sxs-lookup"><span data-stu-id="d263f-114">Tracking participants</span></span>|<span data-ttu-id="d263f-115">Wykorzystuje rekordy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d263f-115">Consumes the tracking records.</span></span> [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="d263f-116"> jest dostarczany z uczestnika śledzenia, który zapisuje rekordy śledzenia jako zdarzenia funkcji Śledzenie zdarzeń systemu Windows ().</span><span class="sxs-lookup"><span data-stu-id="d263f-116"> ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|  
|<span data-ttu-id="d263f-117">Profil śledzenia</span><span class="sxs-lookup"><span data-stu-id="d263f-117">Tracking profile</span></span>|<span data-ttu-id="d263f-118">Mechanizm filtrowania, który umożliwia śledzenie uczestnika do subskrybowania dla podzestawu rekordów śledzenia wyemitowanego z wystąpieniem przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d263f-118">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|  
  
 <span data-ttu-id="d263f-119">W poniższej tabeli przedstawiono rekordy śledzenia emitowane środowiska uruchomieniowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d263f-119">The following table details the tracking records that the workflow runtime emits.</span></span>  
  
|<span data-ttu-id="d263f-120">Rekord śledzenia</span><span class="sxs-lookup"><span data-stu-id="d263f-120">Tracking Record</span></span>|<span data-ttu-id="d263f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="d263f-121">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="d263f-122">Rejestruje śledzenia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d263f-122">Workflow instance tracking records.</span></span>|<span data-ttu-id="d263f-123">W tym artykule opisano cyklu życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d263f-123">Describes the life cycle of the workflow instance.</span></span> <span data-ttu-id="d263f-124">Na przykład wystąpienia rekord jest emitowany podczas uruchamiania przepływu pracy, lub zakończy.</span><span class="sxs-lookup"><span data-stu-id="d263f-124">For example, an instance record is emitted when the workflow starts or completes.</span></span>|  
|<span data-ttu-id="d263f-125">Stan śledzenia zapisów czynności.</span><span class="sxs-lookup"><span data-stu-id="d263f-125">Activity state Tracking Records.</span></span>|<span data-ttu-id="d263f-126">Szczegóły wykonywania działania.</span><span class="sxs-lookup"><span data-stu-id="d263f-126">Details activity execution.</span></span> <span data-ttu-id="d263f-127">Te rekordy wskazują stan działania przepływu pracy, takie jak kiedy zaplanowano działania lub po ukończeniu działania lub gdy zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="d263f-127">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|  
|<span data-ttu-id="d263f-128">Zakładki wznowienie rekordu.</span><span class="sxs-lookup"><span data-stu-id="d263f-128">Bookmark resumption record.</span></span>|<span data-ttu-id="d263f-129">Emitowane zawsze, gdy zostanie wznowione zakładki w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d263f-129">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|  
|<span data-ttu-id="d263f-130">Śledzenie niestandardowych rekordów.</span><span class="sxs-lookup"><span data-stu-id="d263f-130">Custom Tracking Records.</span></span>|<span data-ttu-id="d263f-131">Autor przepływu pracy można tworzyć niestandardowych rekordów śledzenia i wysyłać je w ramach działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="d263f-131">A workflow author can create Custom Tracking Records and emit them within the custom activity.</span></span>|  
  
 <span data-ttu-id="d263f-132">Subskrybuje uczestnika śledzenia dla podzbioru emitowany <xref:System.Activities.Tracking.TrackingRecord> obiektów przy użyciu profilów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d263f-132">The tracking participant subscribes for a subset of the emitted <xref:System.Activities.Tracking.TrackingRecord> objects using tracking profiles.</span></span> <span data-ttu-id="d263f-133">Profil śledzenia zawiera śledzenia zapytań, które umożliwia subskrybowania śledzenia określonego typu rekordu.</span><span class="sxs-lookup"><span data-stu-id="d263f-133">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="d263f-134">Śledzenie profile można określić w kodzie, lub w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d263f-134">Tracking profiles can be specified in code or in configuration.</span></span>  
  
### <a name="custom-tracking-participant"></a><span data-ttu-id="d263f-135">Niestandardowe śledzenia uczestnika</span><span class="sxs-lookup"><span data-stu-id="d263f-135">Custom Tracking Participant</span></span>  
 <span data-ttu-id="d263f-136">Uczestnik śledzenia interfejsu API umożliwia rozszerzenie środowiska uruchomieniowego śledzenia z uczestnika śledzenia podane przez użytkownika, które mogą uwzględniać niestandardowej logiki do obsługi <xref:System.Activities.Tracking.TrackingRecord> obiektów emitowanych przez środowisko wykonawcze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d263f-136">The tracking participant API allows extension of the tracking runtime with a user provided tracking participant that can include custom logic to handle <xref:System.Activities.Tracking.TrackingRecord> objects emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="d263f-137">Można zapisać do śledzenia uczestnika użytkownik musi implementować <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="d263f-137">To write a tracking participant the user must implement <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="d263f-138">W szczególności <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> — metoda musi być implementowana przez uczestnika niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d263f-138">Specifically, the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method has to be implemented by the custom participant.</span></span> <span data-ttu-id="d263f-139">Ta metoda jest wywoływana, gdy <xref:System.Activities.Tracking.TrackingRecord> są emitowane przez środowisko uruchomieniowe przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d263f-139">This method is called when a <xref:System.Activities.Tracking.TrackingRecord> is emitted by the workflow runtime.</span></span>  
  
```csharp  
public abstract class TrackingParticipant  
{  
    protected TrackingParticipant();  
  
    public virtual TrackingProfile TrackingProfile { get; set; }  
    public abstract void Track(TrackingRecord record, TimeSpan timeout);  
}  
```  
  
 <span data-ttu-id="d263f-140">Uczestnik pełną śledzenia jest zaimplementowana w pliku ConsoleTrackingParticipant.cs. Następujący przykładowy kod to <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> metoda uczestnika śledzenia niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d263f-140">The complete tracking participant is implemented in the ConsoleTrackingParticipant.cs file.The following code example is the <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> method for the custom tracking participant.</span></span>  
  
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
  
 <span data-ttu-id="d263f-141">Poniższy przykładowy kod dodaje uczestnika konsoli do wywołującego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d263f-141">The following code example adds the console participant to the workflow invoker.</span></span>  
  
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
  
### <a name="emitting-custom-tracking-records"></a><span data-ttu-id="d263f-142">Emitowanie śledzenia niestandardowych rekordów</span><span class="sxs-lookup"><span data-stu-id="d263f-142">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="d263f-143">W tym przykładzie przedstawiono również możliwość Emituj <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów z działania niestandardowego przepływu pracy:</span><span class="sxs-lookup"><span data-stu-id="d263f-143">This sample also demonstrates the ability to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects from a custom workflow activity:</span></span>  
  
-   <span data-ttu-id="d263f-144"><xref:System.Activities.Tracking.CustomTrackingRecord> Obiekty są tworzone i wypełniane przy użyciu danych zdefiniowane przez użytkownika wymagane jest, aby emitować z rekordem.</span><span class="sxs-lookup"><span data-stu-id="d263f-144">The <xref:System.Activities.Tracking.CustomTrackingRecord> objects are created and populated with user-defined data that is desired to be emitted with the record.</span></span>  
  
-   <span data-ttu-id="d263f-145"><xref:System.Activities.Tracking.CustomTrackingRecord> Są emitowane przez wywołanie metody Śledź <xref:System.Activities.ActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="d263f-145">The <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted by calling the track method of the <xref:System.Activities.ActivityContext>.</span></span>  
  
 <span data-ttu-id="d263f-146">W poniższym przykładzie pokazano sposób Emituj <xref:System.Activities.Tracking.CustomTrackingRecord> obiektów w ramach działania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="d263f-146">The following example demonstrates how to emit <xref:System.Activities.Tracking.CustomTrackingRecord> objects within a custom activity.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d263f-147">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="d263f-147">To use this sample</span></span>  
  
1.  <span data-ttu-id="d263f-148">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania CustomTrackingSample.sln.</span><span class="sxs-lookup"><span data-stu-id="d263f-148">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CustomTrackingSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="d263f-149">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="d263f-149">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="d263f-150">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="d263f-150">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d263f-151">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d263f-151">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d263f-152">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="d263f-152">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d263f-153">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="d263f-153">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d263f-154">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d263f-154">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\CustomTracking`  
  
## <a name="see-also"></a><span data-ttu-id="d263f-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d263f-155">See Also</span></span>  
 [<span data-ttu-id="d263f-156">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="d263f-156">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
