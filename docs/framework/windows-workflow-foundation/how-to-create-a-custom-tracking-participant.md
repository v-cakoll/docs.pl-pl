---
title: 'Instrukcje: Tworzenie niestandardowego uczestnika śledzenia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: ea7a598a73f131d8ee33e285a39173fbf84a97f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182911"
---
# <a name="how-to-create-a-custom-tracking-participant"></a>Instrukcje: Tworzenie niestandardowego uczestnika śledzenia
Śledzenie przepływu pracy zapewnia wgląd w stan wykonywania przepływu pracy. Środowisko wykonawcze przepływu pracy emituje rekordy śledzenia, które opisują zdarzenia cyklu życia przepływu pracy, zdarzenia cyklu życia działania, wznowienia zakładek i błędy. Te rekordy śledzenia są używane przez śledzenie uczestników. Windows Workflow Foundation (WF) zawiera standardowego uczestnika śledzenia, który zapisuje rekordy śledzenia jako zdarzenia śledzenia zdarzeń dla systemu Windows (ETW). Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia. W tym kroku samouczka opisano sposób tworzenia niestandardowego uczestnika śledzenia i profilu śledzenia, który przechwytuje dane wyjściowe działań, `WriteLine` dzięki czemu mogą być wyświetlane użytkownikowi.  
  
> [!NOTE]
> Każdy temat w samouczku Wprowadzenie zależy od poprzednich tematów. Aby ukończyć ten temat, należy najpierw ukończyć poprzednie tematy. Aby pobrać ukończoną wersję lub wyświetlić przewodnik wideo z samouczka, zobacz [Windows Workflow Foundation (WF45) - Wprowadzenie samouczek](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="to-create-the-custom-tracking-participant"></a>Aby utworzyć niestandardowego uczestnika śledzenia  
  
1. Kliknij prawym przyciskiem myszy **pozycję NumberGuessWorkflowHost** w **Eksploratorze rozwiązań** i wybierz polecenie **Dodaj** **klasę**. Wpisz `StatusTrackingParticipant` w polu **Nazwa,** a następnie kliknij przycisk **Dodaj**.  
  
2. Dodaj następujące `using` instrukcje (lub) `Imports`w górnej części `using` pliku `Imports`z innymi (lub) instrukcji.  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. Zmodyfikuj `StatusTrackingParticipant` klasę `TrackingParticipant`tak, aby dziedziczyła z .  
  
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
  
4. Dodaj następujące `Track` zastąpienie metody. Istnieje kilka różnych typów rekordów śledzenia. Jesteśmy zainteresowani wynikami działań, `WriteLine` które są zawarte w rekordach śledzenia aktywności. Jeśli `TrackingRecord` jest `ActivityTrackingRecord` dla `WriteLine` działania, `Text` jest `WriteLine` dołączany do pliku nazwanego `InstanceId` po przepływie pracy. W tym samouczku plik jest zapisywany w bieżącym folderze aplikacji hosta.  
  
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
  
     Jeśli nie określono profilu śledzenia, używany jest domyślny profil śledzenia. Gdy używany jest domyślny profil śledzenia, rekordy `ActivityStates`śledzenia są emitowane dla wszystkich . Ponieważ wystarczy przechwycić tekst jeden raz w `WriteLine` trakcie cyklu życia działania, tylko wyodrębnić tekst ze `ActivityStates.Executing` stanu. W [Aby utworzyć profil śledzenia i zarejestrować uczestnika śledzenia,](#to-create-the-tracking-profile-and-register-the-tracking-participant)tworzony `WriteLine` `ActivityStates.Executing` jest profil śledzenia, który określa, że emitowane są tylko rekordy śledzenia.  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a>Aby utworzyć profil śledzenia i zarejestrować uczestnika śledzenia  
  
1. Kliknij prawym przyciskiem myszy **pozycję WorkflowHostForm** w **Eksploratorze rozwiązań** i wybierz polecenie **Wyświetl kod**.  
  
2. Dodaj `using` następującą `Imports`(lub) instrukcję w górnej `using` części `Imports`pliku z innymi (lub) instrukcji.  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. Dodaj następujący kod `ConfigureWorkflowApplication` do kodu, który `StringWriter` dodaje do rozszerzeń przepływu pracy i przed obsługi cyklu życia przepływu pracy.  
  
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
  
     Ten profil śledzenia określa, że `WriteLine` tylko rekordy `Executing` stanu działania dla działań w stanie są emitowane do niestandardowego uczestnika śledzenia.  
  
     Po dodaniu kodu, `ConfigureWorkflowApplication` początek będzie wyglądać jak w poniższym przykładzie.  
  
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
  
## <a name="to-display-the-tracking-information"></a>Aby wyświetlić informacje o śledzeniu  
  
1. Kliknij prawym przyciskiem myszy **pozycję WorkflowHostForm** w **Eksploratorze rozwiązań** i wybierz polecenie **Wyświetl kod**.  
  
2. W `InstanceId_SelectedIndexChanged` programie obsługi dodaj następujący kod bezpośrednio po kodzie, który czyści okno stanu.  
  
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
  
     Po wybraniu nowego przepływu pracy na liście przepływu pracy rekordy śledzenia dla tego przepływu pracy są ładowane i wyświetlane w oknie stanu. Poniższy przykład jest `InstanceId_SelectedIndexChanged` ukończony program obsługi.  
  
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
  
## <a name="to-build-and-run-the-application"></a>Aby skompilować i uruchomić aplikację  
  
1. Naciśnij klawisze Ctrl+Shift+B, aby utworzyć aplikację.  
  
2. Naciśnij klawisze Ctrl+F5, aby uruchomić aplikację.  
  
3. Wybierz zakres gry zgadywania i typ przepływu pracy, aby rozpocząć, a następnie kliknij przycisk **Nowa gra**. Wprowadź przypuszczenie w polu **Odgadnij** i kliknij przycisk **Przejdź,** aby przesłać swoje przypuszczenie. Należy zauważyć, że stan przepływu pracy jest wyświetlany w oknie stanu. To dane wyjściowe `WriteLine` są przechwytywane z działań. Przełącz się do innego przepływu pracy, wybierając jeden z pola kombi **identyfikatora wystąpienia przepływu pracy** i zwróć uwagę, że stan bieżącego przepływu pracy jest usuwany. Przełącz się z powrotem do poprzedniego przepływu pracy i zwróć uwagę, że stan zostanie przywrócony, podobnie jak w poniższym przykładzie.  
  
    > [!NOTE]
    > Jeśli przełączysz się do przepływu pracy, który został uruchomiony przed włączeniem śledzenia, nie jest wyświetlany żaden stan. Jeśli jednak zrobisz dodatkowe domysły, ich stan zostanie zapisany, ponieważ śledzenie jest teraz włączone.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    > [!NOTE]
    > Te informacje są przydatne do określania zakresu liczby losowej, ale nie zawierają żadnych informacji o tym, co zostało wcześniej dokonane. Te informacje znajdują się w następnym [kroku, Jak: Hostowanie wielu wersji przepływu pracy side-by-side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

    Zanotuj identyfikator wystąpienia przepływu pracy i zagraj w grę aż do jej zakończenia.
  
4. Otwórz Eksploratora Windows i przejdź do folderu **NumberGuessWorkflowHost\bin\debug** (lub **bin\release** w zależności od ustawień projektu). Należy zauważyć, że oprócz plików wykonywalnych projektu znajdują się pliki z nazwami plików guid. Zidentyfikuj ten, który odpowiada identyfikatorowi wystąpienia przepływu pracy z ukończonego przepływu pracy w poprzednim kroku i otwórz go w Notatniku. Informacje o śledzeniu zawierają informacje podobne do następujących.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    Oprócz braku odgadnięcia użytkownika te dane śledzenia nie zawierają informacji o ostatecznym odgadnięciu przepływu pracy. Dzieje się tak, ponieważ informacje `WriteLine` o śledzeniu składają się tylko z danych wyjściowych `Completed` z przepływu pracy, a komunikat końcowy, który jest wyświetlany, odbywa się tak z programu obsługi po zakończeniu przepływu pracy. W następnym kroku samouczka [Jak: Host wiele wersji przepływu pracy side-by-side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), istniejące `WriteLine` działania są modyfikowane w celu `WriteLine` wyświetlenia odgadnięcia użytkownika i dodaje się dodatkowe działanie, które wyświetla wyniki końcowe. Po zintegrowaniu tych [zmian, Jak: Host wiele wersji przepływu pracy side-by-side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) pokazuje, jak hostować wiele wersji przepływu pracy w tym samym czasie.
