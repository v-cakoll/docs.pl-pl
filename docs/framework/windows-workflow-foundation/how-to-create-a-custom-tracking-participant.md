---
title: 'Porady: Tworzenie niestandardowego uczestnika śledzenia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: a9a83f64b7ea0de275631d7d3b8d2755671223ce
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864485"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="b5c19-102">Porady: Tworzenie niestandardowego uczestnika śledzenia</span><span class="sxs-lookup"><span data-stu-id="b5c19-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="b5c19-103">Śledzenie przepływu pracy zapewnia wgląd w stan wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b5c19-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="b5c19-104">Środowisko wykonawcze przepływów pracy emituje rekordów śledzenia, które opisują przepływ pracy zdarzenia cyklu życia, zdarzenia cyklu życia działań, resumptions zakładki i błędów.</span><span class="sxs-lookup"><span data-stu-id="b5c19-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="b5c19-105">Te rekordy śledzenia są używane przez śledzenia uczestników.</span><span class="sxs-lookup"><span data-stu-id="b5c19-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="b5c19-106">Windows Workflow Foundation (WF) zawiera standardowe śledzenia uczestnika, który zapisuje rekordy śledzenia jako zdarzenia śledzenie zdarzeń dla Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="b5c19-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="b5c19-107">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b5c19-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="b5c19-108">W tym kroku samouczka opisano tworzenie niestandardowego uczestnika śledzenia i profilu śledzenia, który przechwycenie danych wyjściowych `WriteLine` działania, aby mogą być wyświetlane użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="b5c19-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5c19-109">Każdy temat samouczka Wprowadzenie zależy od poprzednich tematach.</span><span class="sxs-lookup"><span data-stu-id="b5c19-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="b5c19-110">Aby ukończyć ten temat, najpierw musisz zakończyć poprzednich tematach.</span><span class="sxs-lookup"><span data-stu-id="b5c19-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="b5c19-111">Aby pobrać wersję inną ukończone lub wyświetlić Przewodnik wideo tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="b5c19-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="b5c19-112">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="b5c19-112">In this topic</span></span>  
  
-   [<span data-ttu-id="b5c19-113">Aby utworzyć niestandardowego uczestnika śledzenia</span><span class="sxs-lookup"><span data-stu-id="b5c19-113">To create the custom tracking participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_CustomTrackingParticipant)  
  
-   [<span data-ttu-id="b5c19-114">Aby utworzyć profil śledzenia i zarejestrować uczestnika śledzenia</span><span class="sxs-lookup"><span data-stu-id="b5c19-114">To create the tracking profile and register the tracking participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile)  
  
-   [<span data-ttu-id="b5c19-115">Aby wyświetlić informacje o śledzeniu</span><span class="sxs-lookup"><span data-stu-id="b5c19-115">To display the tracking information</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_DisplayTracking)  
  
-   [<span data-ttu-id="b5c19-116">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="b5c19-116">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CustomTrackingParticipant"></a> <span data-ttu-id="b5c19-117">Aby utworzyć niestandardowego uczestnika śledzenia</span><span class="sxs-lookup"><span data-stu-id="b5c19-117">To create the custom tracking participant</span></span>  
  
1.  <span data-ttu-id="b5c19-118">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **klasy**.</span><span class="sxs-lookup"><span data-stu-id="b5c19-118">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="b5c19-119">Typ `StatusTrackingParticipant` do **nazwa** polu, a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="b5c19-119">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2.  <span data-ttu-id="b5c19-120">Dodaj następujący kod `using` (lub `Imports`) instrukcji w górnej części pliku razem z innymi `using` (lub `Imports`) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b5c19-120">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="b5c19-121">Modyfikowanie `StatusTrackingParticipant` klasy, tak aby dziedziczył z `TrackingParticipant`.</span><span class="sxs-lookup"><span data-stu-id="b5c19-121">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
    ```vb  
    Public Class StatusTrackingParticipant  
        Inherits TrackingParticipant  
  
    End Class  
    ```  
  
    ```csharp  
    class StatusTrackingParticipant : TrackingParticipant  
    {  
    }  
    ```  
  
4.  <span data-ttu-id="b5c19-122">Dodaj następujący kod `Track` zastąpienie metody.</span><span class="sxs-lookup"><span data-stu-id="b5c19-122">Add the following `Track` method override.</span></span> <span data-ttu-id="b5c19-123">Istnieje kilka różnych typów rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b5c19-123">There are several different types of tracking records.</span></span> <span data-ttu-id="b5c19-124">Jesteśmy zainteresowani dane wyjściowe `WriteLine` działań, które są zawarte w działaniu śledzenia rekordów.</span><span class="sxs-lookup"><span data-stu-id="b5c19-124">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="b5c19-125">Jeśli `TrackingRecord` jest `ActivityTrackingRecord` dla `WriteLine` działania `Text` z `WriteLine` jest dołączany do pliku o nazwie po `InstanceId` przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b5c19-125">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="b5c19-126">W tym samouczku plik jest zapisywany do bieżącego folderu aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="b5c19-126">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
    ```vb  
    Protected Overrides Sub Track(record As TrackingRecord, timeout As TimeSpan)  
        Dim asr As ActivityStateRecord = TryCast(record, ActivityStateRecord)  
  
        If Not asr Is Nothing Then  
            If asr.State = ActivityStates.Executing And _  
            asr.Activity.TypeName = "System.Activities.Statements.WriteLine" Then  
  
                'Append the WriteLine output to the tracking  
                'file for this instance.  
                Using writer As StreamWriter = File.AppendText(record.InstanceId.ToString())  
                    writer.WriteLine(asr.Arguments("Text"))  
                    writer.Close()  
                End Using  
            End If  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        ActivityStateRecord asr = record as ActivityStateRecord;  
  
        if (asr != null)  
        {  
            if (asr.State == ActivityStates.Executing &&  
                asr.Activity.TypeName == "System.Activities.Statements.WriteLine")  
            {  
                // Append the WriteLine output to the tracking  
                // file for this instance  
                using (StreamWriter writer = File.AppendText(record.InstanceId.ToString()))  
                {  
                    writer.WriteLine(asr.Arguments["Text"]);  
                    writer.Close();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="b5c19-127">Jeśli nie określono żadnego profilu śledzenia, jest używany domyślny profil śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b5c19-127">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="b5c19-128">Gdy używany jest domyślny profil śledzenia, dla wszystkich są emitowane rekordów śledzenia `ActivityStates`.</span><span class="sxs-lookup"><span data-stu-id="b5c19-128">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="b5c19-129">Ponieważ musimy przechwytywany tekst jeden raz podczas cyklu życia `WriteLine` działania, firma Microsoft tylko wyodrębniania tekstu z `ActivityStates.Executing` stanu.</span><span class="sxs-lookup"><span data-stu-id="b5c19-129">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="b5c19-130">W [utworzyć profil śledzenia i rejestrowania śledzenia uczestnika](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), tworzony jest profil śledzenia, który określa, że tylko `WriteLine` `ActivityStates.Executing` są emitowane rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b5c19-130">In [To create the tracking profile and register the tracking participant](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
###  <a name="BKMK_TrackingProfile"></a> <span data-ttu-id="b5c19-131">Aby utworzyć profil śledzenia i zarejestrować uczestnika śledzenia</span><span class="sxs-lookup"><span data-stu-id="b5c19-131">To create the tracking profile and register the tracking participant</span></span>  
  
1.  <span data-ttu-id="b5c19-132">Kliknij prawym przyciskiem myszy **WorkflowHostForm** w **Eksploratora rozwiązań** i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="b5c19-132">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="b5c19-133">Dodaj następujący kod `using` (lub `Imports`) instrukcji w górnej części pliku razem z innymi `using` (lub `Imports`) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b5c19-133">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3.  <span data-ttu-id="b5c19-134">Dodaj następujący kod do `ConfigureWorkflowApplication` zaraz po kod, który dodaje `StringWriter` rozszerzenia przepływu pracy i przed przepływu pracy obsługi cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="b5c19-134">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
    ```vb  
    'Add the custom tracking participant with a tracking profile  
    'that only emits tracking records for WriteLine activities.  
    Dim query As New ActivityStateQuery()  
    query.ActivityName = "WriteLine"  
    query.States.Add(ActivityStates.Executing)  
    query.Arguments.Add("Text")  
  
    Dim profile As New TrackingProfile()  
    profile.Queries.Add(query)  
  
    Dim stp As New StatusTrackingParticipant()  
    stp.TrackingProfile = profile  
  
    wfApp.Extensions.Add(stp)  
    ```  
  
    ```csharp  
    // Add the custom tracking participant with a tracking profile  
    // that only emits tracking records for WriteLine activities.  
    StatusTrackingParticipant stp = new StatusTrackingParticipant  
    {  
        TrackingProfile = new TrackingProfile  
        {  
            Queries =   
            {  
                new ActivityStateQuery  
                {  
                    ActivityName = "WriteLine",  
                    States = { ActivityStates.Executing },  
                    Arguments = { "Text" }  
                }  
            }  
        }  
    };  
  
    wfApp.Extensions.Add(stp);  
    ```  
  
     <span data-ttu-id="b5c19-135">Ten profil śledzenia Określa, że stan działania tylko rekordy `WriteLine` działań w `Executing` stanu są emitowane do niestandardowego uczestnika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b5c19-135">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="b5c19-136">Po dodaniu kodu początkowego `ConfigureWorkflowApplication` będzie wyglądać podobnie jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b5c19-136">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        'Add the custom tracking participant with a tracking profile  
        'that only emits tracking records for WriteLine activities.  
        Dim query As New ActivityStateQuery()  
        query.ActivityName = "WriteLine"  
        query.States.Add(ActivityStates.Executing)  
        query.Arguments.Add("Text")  
  
        Dim profile As New TrackingProfile()  
        profile.Queries.Add(query)  
  
        Dim stp As New StatusTrackingParticipant()  
        stp.TrackingProfile = profile  
  
        wfApp.Extensions.Add(stp)  
  
        'Workflow lifecycle handlers...  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        // Add the custom tracking participant with a tracking profile  
        // that only emits tracking records for WriteLine activities.  
        StatusTrackingParticipant stp = new StatusTrackingParticipant  
        {  
            TrackingProfile = new TrackingProfile  
            {  
                Queries =   
                {  
                    new ActivityStateQuery  
                    {  
                        ActivityName = "WriteLine",  
                        States = { ActivityStates.Executing },  
                        Arguments = { "Text" }  
                    }  
                }  
            }  
        };  
  
        wfApp.Extensions.Add(stp);  
  
        // Workflow lifecycle handlers...  
    ```  
  
###  <a name="BKMK_DisplayTracking"></a> <span data-ttu-id="b5c19-137">Aby wyświetlić informacje o śledzeniu</span><span class="sxs-lookup"><span data-stu-id="b5c19-137">To display the tracking information</span></span>  
  
1.  <span data-ttu-id="b5c19-138">Kliknij prawym przyciskiem myszy **WorkflowHostForm** w **Eksploratora rozwiązań** i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="b5c19-138">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="b5c19-139">W `InstanceId_SelectedIndexChanged` obsługi, Dodaj następujący kod bezpośrednio po kodzie, która Czyści okno stanu.</span><span class="sxs-lookup"><span data-stu-id="b5c19-139">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
    ```vb  
    'If there is tracking data for this workflow, display it  
    'in the status window.  
    If File.Exists(WorkflowInstanceId.ToString()) Then  
        Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
        UpdateStatus(status)  
    End If  
    ```  
  
    ```csharp  
    // If there is tracking data for this workflow, display it  
    // in the status window.  
    if (File.Exists(WorkflowInstanceId.ToString()))  
    {  
        string status = File.ReadAllText(WorkflowInstanceId.ToString());  
        UpdateStatus(status);  
    }  
    ```  
  
     <span data-ttu-id="b5c19-140">Po wybraniu nowego przepływu pracy na liście przepływów pracy rekordów śledzenia dla tego przepływu pracy są ładowane i wyświetlane w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="b5c19-140">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="b5c19-141">Poniższy przykład jest gotowy `InstanceId_SelectedIndexChanged` programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="b5c19-141">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
        If InstanceId.SelectedIndex = -1 Then  
            Return  
        End If  
  
        'Clear the status window.  
        WorkflowStatus.Clear()  
  
        'If there is tracking data for this workflow, display it  
        'in the status window.  
        If File.Exists(WorkflowInstanceId.ToString()) Then  
            Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
            UpdateStatus(status)  
        End If  
  
        'Get the workflow version and display it.  
        'If the workflow is just starting then this info will not  
        'be available in the persistence store so do not try and retrieve it.  
        If Not WorkflowStarting Then  
            Dim instance As WorkflowApplicationInstance = _  
                WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
            WorkflowVersion.Text = _  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
            'Unload the instance.  
            instance.Abandon()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
        if (InstanceId.SelectedIndex == -1)  
        {  
            return;  
        }  
  
        // Clear the status window.  
        WorkflowStatus.Clear();  
  
        // If there is tracking data for this workflow, display it  
        // in the status window.  
        if (File.Exists(WorkflowInstanceId.ToString()))  
        {  
            string status = File.ReadAllText(WorkflowInstanceId.ToString());  
            UpdateStatus(status);  
        }  
  
        // Get the workflow version and display it.  
        // If the workflow is just starting then this info will not  
        // be available in the persistence store so do not try and retrieve it.  
        if (!WorkflowStarting)  
        {  
            WorkflowApplicationInstance instance =  
                WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
            WorkflowVersion.Text =  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
            // Unload the instance.  
            instance.Abandon();  
        }  
    }  
    ```  
  
###  <a name="BKMK_BuildAndRun"></a> <span data-ttu-id="b5c19-142">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="b5c19-142">To build and run the application</span></span>  
  
1.  <span data-ttu-id="b5c19-143">Naciśnij klawisze Ctrl + Shift + B, aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="b5c19-143">Press Ctrl+Shift+B to build the application.</span></span>  
  
2.  <span data-ttu-id="b5c19-144">Naciśnij klawisze Ctrl + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="b5c19-144">Press Ctrl+F5 to start the application.</span></span>  
  
3.  <span data-ttu-id="b5c19-145">Wybierz zakres do odgadnięcia gier i typ przepływu pracy, aby rozpocząć, a następnie kliknij przycisk **nowych gier**.</span><span class="sxs-lookup"><span data-stu-id="b5c19-145">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="b5c19-146">Wprowadź odgadnięcia w **odgadnięcia** pole, a następnie kliknij przycisk **Przejdź** przesłać przypuszczenie.</span><span class="sxs-lookup"><span data-stu-id="b5c19-146">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="b5c19-147">Należy zauważyć, że stan przepływu pracy jest wyświetlana w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="b5c19-147">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="b5c19-148">Te dane wyjściowe są przechwytywane z `WriteLine` działań.</span><span class="sxs-lookup"><span data-stu-id="b5c19-148">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="b5c19-149">Przełącz się do innego przepływu pracy, wybierając jedną z **identyfikator wystąpienia przepływu pracy** pola kombi i zwróć uwagę, że stan bieżącego przepływu pracy została usunięta.</span><span class="sxs-lookup"><span data-stu-id="b5c19-149">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="b5c19-150">Przejdź z powrotem do poprzedniej przepływu pracy i zwróć uwagę, że stan został przywrócony, podobny do poniższego przykładu.</span><span class="sxs-lookup"><span data-stu-id="b5c19-150">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b5c19-151">Po przełączeniu do przepływu pracy, która została uruchomiona przed włączeniem śledzenia nie stan jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="b5c19-151">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="b5c19-152">Jednak w przypadku wprowadzenia dodatkowych prób ich stan jest zapisać, ponieważ włączono śledzenie.</span><span class="sxs-lookup"><span data-stu-id="b5c19-152">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
 <span data-ttu-id="b5c19-153">**Wprowadź liczbę między 1 a 10**</span><span class="sxs-lookup"><span data-stu-id="b5c19-153">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="b5c19-154">**Przypuszczenie jest zbyt duża.** </span><span class="sxs-lookup"><span data-stu-id="b5c19-154">**Your guess is too high.** </span></span>  
<span data-ttu-id="b5c19-155">**Wprowadź liczbę między 1 a 10**</span><span class="sxs-lookup"><span data-stu-id="b5c19-155">**Please enter a number between 1 and 10**</span></span>    
    > [!NOTE]
    >  <span data-ttu-id="b5c19-156">Te informacje są przydatne do określania zakresu liczb losowych, ale nie zawiera żadnych informacji o jakie prób zostały wprowadzone wcześniej.</span><span class="sxs-lookup"><span data-stu-id="b5c19-156">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="b5c19-157">Te informacje są w następnym kroku [jak: Host wielu wersji przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="b5c19-157">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
     <span data-ttu-id="b5c19-158">Zanotuj identyfikator wystąpienia przepływu pracy i Zagraj w grę za pośrednictwem do jego zakończenia.</span><span class="sxs-lookup"><span data-stu-id="b5c19-158">Make a note of the workflow instance id, and play the game through to its completion.</span></span>  
  
4.  <span data-ttu-id="b5c19-159">Otwórz Eksploratora Windows i przejdź do **NumberGuessWorkflowHost\bin\debug** folder (lub **bin\release** w zależności od ustawień projektu).</span><span class="sxs-lookup"><span data-stu-id="b5c19-159">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="b5c19-160">Należy zauważyć, że oprócz projekt istnieje pliki wykonywalne pliki przy użyciu identyfikatora guid w nazwach plików.</span><span class="sxs-lookup"><span data-stu-id="b5c19-160">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="b5c19-161">Zidentyfikuj ten, który odpowiada identyfikator wystąpienia przepływu pracy z ukończony przepływ pracy w poprzednim kroku, a następnie otwórz go w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="b5c19-161">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="b5c19-162">Informacje o śledzeniu zawiera informacje podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="b5c19-162">The tracking information contains information similar to the following.</span></span>  
  
 <span data-ttu-id="b5c19-163">**Wprowadź liczbę między 1 a 10**</span><span class="sxs-lookup"><span data-stu-id="b5c19-163">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="b5c19-164">**Przypuszczenie jest zbyt duża.** </span><span class="sxs-lookup"><span data-stu-id="b5c19-164">**Your guess is too high.** </span></span>  
<span data-ttu-id="b5c19-165">**Wprowadź liczbę między 1 a 10** </span><span class="sxs-lookup"><span data-stu-id="b5c19-165">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="b5c19-166">**Przypuszczenie jest zbyt duża.** </span><span class="sxs-lookup"><span data-stu-id="b5c19-166">**Your guess is too high.** </span></span>  
<span data-ttu-id="b5c19-167">**Wprowadź liczbę między 1 a 10** oprócz braku prób przez użytkownika, to dane śledzenia nie zawiera informacji na temat ostateczny wynik przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b5c19-167">**Please enter a number between 1 and 10**      In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="b5c19-168">To dlatego informacje o śledzeniu składa się tylko z `WriteLine` danych wyjściowych z przepływu pracy, końcowe komunikat, który jest wyświetlany jest wykonywane to `Completed` obsługi po ukończeniu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b5c19-168">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="b5c19-169">W następnym kroku samouczka [jak: Host wielu wersji przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), istniejące `WriteLine` działań są modyfikowane w celu wyświetlania prób przez użytkownika oraz dodatkowy `WriteLine` dodaniu działania, które Wyświetla wyniki końcowe.</span><span class="sxs-lookup"><span data-stu-id="b5c19-169">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="b5c19-170">Po zintegrowaniu są te zmiany, [jak: Host wielu wersji przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) pokazuje, jak hostowanie wielu wersji przepływu pracy w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="b5c19-170">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
