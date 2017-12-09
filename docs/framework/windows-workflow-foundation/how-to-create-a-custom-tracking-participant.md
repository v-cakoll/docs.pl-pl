---
title: "Porady: Tworzenie niestandardowych śledzenia uczestnika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4818b43c447dbe279a67f372dc846b3b07ecd998
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="008fc-102">Porady: Tworzenie niestandardowych śledzenia uczestnika</span><span class="sxs-lookup"><span data-stu-id="008fc-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="008fc-103">Śledzenia przepływu pracy zapewnia wgląd w stan wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="008fc-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="008fc-104">Środowiska uruchomieniowego przepływu pracy emituje rekordy śledzenia, które opisują zdarzenia cyklu życia przepływu pracy, zdarzenia cyklu życia działania zakładki wznawianiu i błędów.</span><span class="sxs-lookup"><span data-stu-id="008fc-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="008fc-105">Te rekordy śledzenia są używane przez uczestników śledzenia.</span><span class="sxs-lookup"><span data-stu-id="008fc-105">These tracking records are consumed by tracking participants.</span></span> [!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="008fc-106">obejmuje uczestnika standardowe śledzenia, który zapisuje rekordy śledzenia jako zdarzenia funkcji Śledzenie zdarzeń systemu Windows ().</span><span class="sxs-lookup"><span data-stu-id="008fc-106"> includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="008fc-107">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="008fc-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="008fc-108">Ten samouczek krok opisuje sposób tworzenia niestandardowych śledzenia uczestnika i profilu śledzenia, który przechwytywania danych wyjściowych `WriteLine` działań, dzięki czemu mogą być wyświetlane dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="008fc-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="008fc-109">Każdego tematu w samouczku wprowadzenie zależy od poprzednich tematów.</span><span class="sxs-lookup"><span data-stu-id="008fc-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="008fc-110">Aby ukończyć w tym temacie, należy wykonać poprzednie tematy.</span><span class="sxs-lookup"><span data-stu-id="008fc-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="008fc-111">Aby pobrać wersję zakończone lub wyświetlić Przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="008fc-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="008fc-112">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="008fc-112">In this topic</span></span>  
  
-   [<span data-ttu-id="008fc-113">Aby utworzyć uczestnika śledzenia niestandardowych</span><span class="sxs-lookup"><span data-stu-id="008fc-113">To create the custom tracking participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_CustomTrackingParticipant)  
  
-   [<span data-ttu-id="008fc-114">Aby utworzyć profil śledzenia i zarejestrować uczestnika śledzenia</span><span class="sxs-lookup"><span data-stu-id="008fc-114">To create the tracking profile and register the tracking participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile)  
  
-   [<span data-ttu-id="008fc-115">Aby wyświetlić informacje o śledzeniu</span><span class="sxs-lookup"><span data-stu-id="008fc-115">To display the tracking information</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_DisplayTracking)  
  
-   [<span data-ttu-id="008fc-116">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="008fc-116">To build and run the application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CustomTrackingParticipant"></a><span data-ttu-id="008fc-117">Aby utworzyć uczestnika śledzenia niestandardowych</span><span class="sxs-lookup"><span data-stu-id="008fc-117">To create the custom tracking participant</span></span>  
  
1.  <span data-ttu-id="008fc-118">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **klasy**.</span><span class="sxs-lookup"><span data-stu-id="008fc-118">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="008fc-119">Typ `StatusTrackingParticipant` do **nazwa** i kliknij **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="008fc-119">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2.  <span data-ttu-id="008fc-120">Dodaj następujące `using` (lub `Imports`) instrukcje w górnej części pliku z innym `using` (lub `Imports`) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="008fc-120">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="008fc-121">Modyfikowanie `StatusTrackingParticipant` klasy tak, aby dziedziczyła ona z `TrackingParticipant`.</span><span class="sxs-lookup"><span data-stu-id="008fc-121">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
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
  
4.  <span data-ttu-id="008fc-122">Dodaj następujące `Track` zastąpienie metody.</span><span class="sxs-lookup"><span data-stu-id="008fc-122">Add the following `Track` method override.</span></span> <span data-ttu-id="008fc-123">Istnieje kilka różnych typów rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="008fc-123">There are several different types of tracking records.</span></span> <span data-ttu-id="008fc-124">Dbamy o dane wyjściowe `WriteLine` działań, które są zawarte w działaniu śledzenie rekordów.</span><span class="sxs-lookup"><span data-stu-id="008fc-124">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="008fc-125">Jeśli `TrackingRecord` jest `ActivityTrackingRecord` dla `WriteLine` działania, `Text` z `WriteLine` jest dołączany do pliku o nazwie po `InstanceId` przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="008fc-125">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="008fc-126">W tym samouczku plik jest zapisywany do bieżącego folderu aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="008fc-126">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
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
  
     <span data-ttu-id="008fc-127">Jeśli nie określono żadnego profilu śledzenia, używany jest domyślny profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="008fc-127">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="008fc-128">Gdy używany jest domyślny profil śledzenia, śledzenie rekordów są emitowane dla wszystkich `ActivityStates`.</span><span class="sxs-lookup"><span data-stu-id="008fc-128">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="008fc-129">Ponieważ musimy przechwytywania tekst raz w ramach cyklem życia `WriteLine` działania, możemy tylko Wyodrębnij tekst z `ActivityStates.Executing` stanu.</span><span class="sxs-lookup"><span data-stu-id="008fc-129">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="008fc-130">W [utworzyć profilu śledzenia i zarejestrować uczestnika śledzenia](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), tworzony jest profil śledzenia, który określa, że tylko `WriteLine` `ActivityStates.Executing` są emitowane rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="008fc-130">In [To create the tracking profile and register the tracking participant](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
###  <a name="BKMK_TrackingProfile"></a><span data-ttu-id="008fc-131">Aby utworzyć profil śledzenia i zarejestrować uczestnika śledzenia</span><span class="sxs-lookup"><span data-stu-id="008fc-131">To create the tracking profile and register the tracking participant</span></span>  
  
1.  <span data-ttu-id="008fc-132">Kliknij prawym przyciskiem myszy **WorkflowHostForm** w **Eksploratora rozwiązań** i wybierz polecenie **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="008fc-132">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="008fc-133">Dodaj następujące `using` (lub `Imports`) instrukcji w górnej części pliku z innym `using` (lub `Imports`) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="008fc-133">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3.  <span data-ttu-id="008fc-134">Dodaj następujący kod do `ConfigureWorkflowApplication` zaraz po kod, który dodaje `StringWriter` rozszerzeń przepływu pracy i przed przepływu pracy obsługi cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="008fc-134">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
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
  
     <span data-ttu-id="008fc-135">Ten profil śledzenia Określa, czy stan tylko działania rekordy `WriteLine` działań w `Executing` stanu są emitowane do uczestnika śledzenia niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="008fc-135">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="008fc-136">Po dodaniu kod początku `ConfigureWorkflowApplication` będzie wyglądać jak w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="008fc-136">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
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
  
###  <a name="BKMK_DisplayTracking"></a><span data-ttu-id="008fc-137">Aby wyświetlić informacje o śledzeniu</span><span class="sxs-lookup"><span data-stu-id="008fc-137">To display the tracking information</span></span>  
  
1.  <span data-ttu-id="008fc-138">Kliknij prawym przyciskiem myszy **WorkflowHostForm** w **Eksploratora rozwiązań** i wybierz polecenie **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="008fc-138">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="008fc-139">W `InstanceId_SelectedIndexChanged` obsługi, Dodaj następujący kod bezpośrednio po kodzie Czyści okno stanu.</span><span class="sxs-lookup"><span data-stu-id="008fc-139">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
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
  
     <span data-ttu-id="008fc-140">Gdy nowy przepływ pracy jest zaznaczony na liście przepływu pracy, rekordy śledzenia dla tego przepływu pracy są załadowana i wyświetlona w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="008fc-140">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="008fc-141">Poniższy przykład jest wypełniony `InstanceId_SelectedIndexChanged` obsługi.</span><span class="sxs-lookup"><span data-stu-id="008fc-141">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
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
  
###  <a name="BKMK_BuildAndRun"></a><span data-ttu-id="008fc-142">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="008fc-142">To build and run the application</span></span>  
  
1.  <span data-ttu-id="008fc-143">Naciśnij klawisze Ctrl + Shift + B do skompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="008fc-143">Press Ctrl+Shift+B to build the application.</span></span>  
  
2.  <span data-ttu-id="008fc-144">Naciśnij klawisze Ctrl + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="008fc-144">Press Ctrl+F5 to start the application.</span></span>  
  
3.  <span data-ttu-id="008fc-145">Wybierz zakres guessing gry i typ przepływu pracy, aby rozpocząć, a następnie kliknij przycisk **nowych gier**.</span><span class="sxs-lookup"><span data-stu-id="008fc-145">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="008fc-146">Wprowadź wynik w **Guess** polu i kliknij przycisk **Przejdź** można przesłać z wynik.</span><span class="sxs-lookup"><span data-stu-id="008fc-146">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="008fc-147">Należy pamiętać, że stan przepływu pracy jest wyświetlany w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="008fc-147">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="008fc-148">Te dane wyjściowe są przechwytywane z `WriteLine` działań.</span><span class="sxs-lookup"><span data-stu-id="008fc-148">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="008fc-149">Przełącz do innego przepływu pracy, wybierając jedną z **identyfikator wystąpienia przepływu pracy** pole kombi i Uwaga usunięcie stanu bieżącego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="008fc-149">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="008fc-150">Przejdź do poprzedniego przepływu pracy i należy pamiętać, że stan został przywrócony, podobnie do poniższego przykładu.</span><span class="sxs-lookup"><span data-stu-id="008fc-150">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="008fc-151">Po przełączeniu do przepływu pracy, które zostało uruchomione przed włączeniem śledzenia nie stan jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="008fc-151">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="008fc-152">Jednak jeśli dodatkowych prób, ich stan jest zapisany ponieważ śledzenia jest teraz włączony.</span><span class="sxs-lookup"><span data-stu-id="008fc-152">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
 <span data-ttu-id="008fc-153">**Wprowadź liczbę z przedziału od 1 do 10**</span><span class="sxs-lookup"><span data-stu-id="008fc-153">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="008fc-154">**Twoje wynik jest za duża.** </span><span class="sxs-lookup"><span data-stu-id="008fc-154">**Your guess is too high.** </span></span>  
<span data-ttu-id="008fc-155">**Wprowadź liczbę z przedziału od 1 do 10**</span><span class="sxs-lookup"><span data-stu-id="008fc-155">**Please enter a number between 1 and 10**</span></span>    
    > [!NOTE]
    >  <span data-ttu-id="008fc-156">Informacje te są przydatne do określenia liczbę losową z zakresu, ale nie zawiera żadnych informacji o jakie prób zostały wprowadzone wcześniej.</span><span class="sxs-lookup"><span data-stu-id="008fc-156">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="008fc-157">Te informacje są w następnym kroku [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="008fc-157">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
     <span data-ttu-id="008fc-158">Zanotuj identyfikator wystąpienia przepływu pracy i gry za pośrednictwem do jego zakończenia.</span><span class="sxs-lookup"><span data-stu-id="008fc-158">Make a note of the workflow instance id, and play the game through to its completion.</span></span>  
  
4.  <span data-ttu-id="008fc-159">Otwórz Eksploratora Windows i przejdź do **NumberGuessWorkflowHost\bin\debug** folder (lub **bin\release** w zależności od ustawienia projektu).</span><span class="sxs-lookup"><span data-stu-id="008fc-159">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="008fc-160">Należy zauważyć, że oprócz projektu istnieje pliki wykonywalne pliki z identyfikatora guid w nazwach plików.</span><span class="sxs-lookup"><span data-stu-id="008fc-160">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="008fc-161">Zidentyfikuj ten, który odpowiada identyfikator wystąpienia przepływu pracy z przepływu pracy ukończonych w poprzednim kroku, a następnie otwórz go w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="008fc-161">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="008fc-162">Informacje o śledzeniu zawiera informacje podobne do następującego.</span><span class="sxs-lookup"><span data-stu-id="008fc-162">The tracking information contains information similar to the following.</span></span>  
  
 <span data-ttu-id="008fc-163">**Wprowadź liczbę z przedziału od 1 do 10**</span><span class="sxs-lookup"><span data-stu-id="008fc-163">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="008fc-164">**Twoje wynik jest za duża.** </span><span class="sxs-lookup"><span data-stu-id="008fc-164">**Your guess is too high.** </span></span>  
<span data-ttu-id="008fc-165">**Wprowadź liczbę z przedziału od 1 do 10** </span><span class="sxs-lookup"><span data-stu-id="008fc-165">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="008fc-166">**Twoje wynik jest za duża.** </span><span class="sxs-lookup"><span data-stu-id="008fc-166">**Your guess is too high.** </span></span>  
<span data-ttu-id="008fc-167">**Wprowadź liczbę z przedziału od 1 do 10** oprócz braku prób użytkownika, dane śledzenia nie zawiera informacji o wynik końcowy przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="008fc-167">**Please enter a number between 1 and 10**      In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="008fc-168">Jest to spowodowane informacje o śledzeniu składa się tylko z tym `WriteLine` danych wyjściowych z przepływu pracy, i końcowe komunikat, który jest wyświetlany jest wykonywane z `Completed` obsługi po zakończeniu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="008fc-168">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="008fc-169">W następnym kroku samouczka [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), istniejące `WriteLine` działania są modyfikowane, aby wyświetlić liczbę prób użytkownika i dodatkowe `WriteLine` dodaniu działania, które Wyświetla wyniki końcowe.</span><span class="sxs-lookup"><span data-stu-id="008fc-169">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="008fc-170">Po te zmiany są zintegrowane, [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) pokazano, jak obsługiwać wiele wersji przepływu pracy w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="008fc-170">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
