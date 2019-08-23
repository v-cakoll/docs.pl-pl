---
title: 'Instrukcje: Tworzenie niestandardowego uczestnika śledzenia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 280f68c8b762562a56ce96f45f118702fb0e4d76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962398"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="ed1b9-102">Instrukcje: Tworzenie niestandardowego uczestnika śledzenia</span><span class="sxs-lookup"><span data-stu-id="ed1b9-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="ed1b9-103">Śledzenie przepływu pracy zapewnia wgląd w stan wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="ed1b9-104">Środowisko uruchomieniowe przepływu pracy emituje rekordy śledzenia, które opisują zdarzenia cyklu życia przepływu pracy, zdarzenia cyklu życia działań, wznowienia zakładek i błędy.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="ed1b9-105">Te rekordy śledzenia są używane przez Śledzenie uczestników.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="ed1b9-106">Windows Workflow Foundation (WF) obejmuje uczestnika śledzenia standardowego, który zapisuje rekordy śledzenia jako zdarzenia śledzenia zdarzeń systemu Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="ed1b9-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="ed1b9-107">Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="ed1b9-108">W tym kroku opisano sposób tworzenia niestandardowego uczestnika śledzenia i profilu śledzenia, który przechwytuje dane `WriteLine` wyjściowe działań, dzięki czemu mogą one być wyświetlane użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed1b9-109">Każdy temat w samouczku Wprowadzenie zależy od poprzednich tematów.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="ed1b9-110">Aby ukończyć ten temat, należy najpierw wykonać poprzednie tematy.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="ed1b9-111">Aby pobrać kompletną wersję lub wyświetlić przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="ed1b9-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-custom-tracking-participant"></a><span data-ttu-id="ed1b9-112">Aby utworzyć uczestnika śledzenia niestandardowego</span><span class="sxs-lookup"><span data-stu-id="ed1b9-112">To create the custom tracking participant</span></span>  
  
1. <span data-ttu-id="ed1b9-113">Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **Klasa**.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-113">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="ed1b9-114">Wpisz `StatusTrackingParticipant` tekst w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-114">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2. <span data-ttu-id="ed1b9-115">Dodaj następujące `using` instrukcje (lub `Imports`) w górnej części pliku z innymi `using` instrukcjami (lub `Imports`).</span><span class="sxs-lookup"><span data-stu-id="ed1b9-115">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. <span data-ttu-id="ed1b9-116">Zmodyfikuj klasę, aby dziedziczyć po `TrackingParticipant`elemencie. `StatusTrackingParticipant`</span><span class="sxs-lookup"><span data-stu-id="ed1b9-116">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
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
  
4. <span data-ttu-id="ed1b9-117">Dodaj poniższe `Track` przesłonięcie metody.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-117">Add the following `Track` method override.</span></span> <span data-ttu-id="ed1b9-118">Istnieje kilka różnych typów rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-118">There are several different types of tracking records.</span></span> <span data-ttu-id="ed1b9-119">Interesuje Cię dane wyjściowe `WriteLine` działań, które znajdują się w rekordach śledzenia aktywności.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-119">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="ed1b9-120">`TrackingRecord` Jeśli `WriteLine` jestto`Text` działanie `InstanceId` dla działania ,`WriteLine` jest dołączane do pliku o nazwie po przepływie pracy. `ActivityTrackingRecord`</span><span class="sxs-lookup"><span data-stu-id="ed1b9-120">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="ed1b9-121">W tym samouczku plik jest zapisywany w bieżącym folderze aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-121">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
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
  
     <span data-ttu-id="ed1b9-122">Gdy nie określono profilu śledzenia, używany jest domyślny profil śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-122">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="ed1b9-123">W przypadku użycia domyślnego profilu śledzenia rekordy śledzenia są emitowane dla wszystkich `ActivityStates`.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-123">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="ed1b9-124">Ponieważ potrzebujemy tylko jednokrotnego przechwycenia tekstu podczas cyklu życia `WriteLine` działania, wyodrębnimy tylko tekst `ActivityStates.Executing` ze stanu.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-124">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="ed1b9-125">W programie w [celu utworzenia profilu śledzenia i zarejestrowania uczestnika śledzenia](#to-create-the-tracking-profile-and-register-the-tracking-participant)zostanie utworzony profil śledzenia, który określa, `WriteLine` że są emitowane tylko `ActivityStates.Executing` śledzone rekordy.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-125">In [To create the tracking profile and register the tracking participant](#to-create-the-tracking-profile-and-register-the-tracking-participant), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a><span data-ttu-id="ed1b9-126">Aby utworzyć profil śledzenia i zarejestrować uczestnika śledzenia</span><span class="sxs-lookup"><span data-stu-id="ed1b9-126">To create the tracking profile and register the tracking participant</span></span>  
  
1. <span data-ttu-id="ed1b9-127">Kliknij prawym przyciskiem myszy pozycję **WorkflowHostForm** w **Eksplorator rozwiązań** i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-127">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="ed1b9-128">Dodaj następującą `using` instrukcję (lub `Imports`) w górnej części pliku z innymi `using` instrukcjami (lub `Imports`).</span><span class="sxs-lookup"><span data-stu-id="ed1b9-128">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. <span data-ttu-id="ed1b9-129">Dodaj następujący kod do `ConfigureWorkflowApplication` tuż po kodzie, który `StringWriter` dodaje do rozszerzeń przepływu pracy i przed obsługą cyklu życia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-129">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
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
  
     <span data-ttu-id="ed1b9-130">Ten profil śledzenia Określa, że tylko rekordy stanu działania `WriteLine` dla działań `Executing` w stanie są emitowane do uczestnika niestandardowego śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-130">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="ed1b9-131">Po dodaniu kodu początek `ConfigureWorkflowApplication` będzie wyglądał jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-131">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
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
  
## <a name="to-display-the-tracking-information"></a><span data-ttu-id="ed1b9-132">Aby wyświetlić informacje o śledzeniu</span><span class="sxs-lookup"><span data-stu-id="ed1b9-132">To display the tracking information</span></span>  
  
1. <span data-ttu-id="ed1b9-133">Kliknij prawym przyciskiem myszy pozycję **WorkflowHostForm** w **Eksplorator rozwiązań** i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-133">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="ed1b9-134">W programie `InstanceId_SelectedIndexChanged` obsługi Dodaj następujący kod bezpośrednio po kodzie, który czyści okno stanu.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-134">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
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
  
     <span data-ttu-id="ed1b9-135">Po wybraniu nowego przepływu pracy na liście przepływów pracy rekordy śledzenia dla tego przepływu pracy są ładowane i wyświetlane w oknie stanu.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-135">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="ed1b9-136">Poniższy przykład to zakończono `InstanceId_SelectedIndexChanged` procedurę obsługi.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-136">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
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
  
## <a name="to-build-and-run-the-application"></a><span data-ttu-id="ed1b9-137">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="ed1b9-137">To build and run the application</span></span>  
  
1. <span data-ttu-id="ed1b9-138">Naciśnij klawisze CTRL + SHIFT + B, aby skompilować aplikację.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-138">Press Ctrl+Shift+B to build the application.</span></span>  
  
2. <span data-ttu-id="ed1b9-139">Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-139">Press Ctrl+F5 to start the application.</span></span>  
  
3. <span data-ttu-id="ed1b9-140">Wybierz zakres dla gry do odgadnięcia i typ przepływu pracy do uruchomienia, a następnie kliknij pozycję **Nowa gra**.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-140">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="ed1b9-141">Wprowadź wartość w polu **zgadywanie** i kliknij pozycję **Przejdź** , aby przesłać przypuszczenie.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-141">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="ed1b9-142">Należy zauważyć, że w oknie stanu jest wyświetlany stan przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-142">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="ed1b9-143">Te dane wyjściowe są przechwytywane `WriteLine` z działań.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-143">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="ed1b9-144">Przejdź do innego przepływu pracy, wybierając go z pola kombi **Identyfikator wystąpienia przepływu pracy** i pamiętaj, że bieżący przepływ pracy jest usuwany.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-144">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="ed1b9-145">Przełącz się z powrotem do poprzedniego przepływu pracy i pamiętaj, że stan jest przywrócony, podobnie jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-145">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ed1b9-146">Jeśli przełączysz się do przepływu pracy, który został uruchomiony przed włączeniem śledzenia, stan nie jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-146">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="ed1b9-147">Jeśli jednak wprowadzisz dodatkowe odgadnięcia, ich stan jest zapisywany, ponieważ śledzenie jest teraz włączone.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-147">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```
    
    > [!NOTE]
    > <span data-ttu-id="ed1b9-148">Te informacje są przydatne do określania zakresu liczby losowej, ale nie zawierają żadnych informacji o tym, jakie odgadnięcia zostały wcześniej wykonane.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-148">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="ed1b9-149">Te informacje są w następnym kroku [: Hostowanie wielu wersji przepływu pracy obok](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)siebie.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-149">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    <span data-ttu-id="ed1b9-150">Zanotuj identyfikator wystąpienia przepływu pracy, a następnie Odtwórz grę do końca.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-150">Make a note of the workflow instance id, and play the game through to its completion.</span></span>
  
4. <span data-ttu-id="ed1b9-151">Otwórz Eksploratora Windows i przejdź do folderu **NumberGuessWorkflowHost\bin\debug** (lub **bin\Release** w zależności od ustawień projektu).</span><span class="sxs-lookup"><span data-stu-id="ed1b9-151">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="ed1b9-152">Należy pamiętać, że oprócz plików wykonywalnych projektu istnieją pliki z nazwami plików GUID.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-152">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="ed1b9-153">Zidentyfikuj ten, który odpowiada identyfikatorowi wystąpienia przepływu pracy z ukończonego przepływu pracy w poprzednim kroku, i otwórz go w Notatniku.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-153">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="ed1b9-154">Informacje o śledzeniu zawierają informacje podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-154">The tracking information contains information similar to the following.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    <span data-ttu-id="ed1b9-155">Poza brakiem prób użytkownika, dane śledzenia nie zawierają informacji o końcowej próbie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-155">In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="ed1b9-156">Wynika to z faktu, że informacje o śledzeniu obejmują tylko `WriteLine` dane wyjściowe z przepływu pracy, a końcowy komunikat, który jest wyświetlany, jest wykonywany `Completed` z programu obsługi po zakończeniu przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-156">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="ed1b9-157">W następnym kroku samouczka [: Hostowanie wielu wersji przepływu pracy obok](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)siebie, istniejące `WriteLine` działania są modyfikowane w celu wyświetlenia odgadnięcia użytkownika i dodawane jest dodatkowe `WriteLine` działanie, które wyświetla końcowe wyniki.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-157">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="ed1b9-158">Po zintegrowaniu tych zmian należy [: Hostowanie wielu wersji przepływu pracy obok siebie](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) pokazuje, jak hostować wiele wersji przepływu pracy w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="ed1b9-158">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
