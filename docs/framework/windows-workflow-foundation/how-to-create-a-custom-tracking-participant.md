---
title: 'Instrukcje: Tworzenie niestandardowego uczestnika śledzenia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 64320a8f4799e79f54348e5381ed2d8ed49d496b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975692"
---
# <a name="how-to-create-a-custom-tracking-participant"></a>Instrukcje: Tworzenie niestandardowego uczestnika śledzenia
Śledzenie przepływu pracy zapewnia wgląd w stan wykonywania przepływu pracy. Środowisko wykonawcze przepływów pracy emituje rekordów śledzenia, które opisują przepływ pracy zdarzenia cyklu życia, zdarzenia cyklu życia działań, resumptions zakładki i błędów. Te rekordy śledzenia są używane przez śledzenia uczestników. Windows Workflow Foundation (WF) zawiera standardowe śledzenia uczestnika, który zapisuje rekordy śledzenia jako zdarzenia śledzenie zdarzeń dla Windows (ETW). Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia. W tym kroku samouczka opisano tworzenie niestandardowego uczestnika śledzenia i profilu śledzenia, który przechwycenie danych wyjściowych `WriteLine` działania, aby mogą być wyświetlane użytkownikowi.  
  
> [!NOTE]
>  Każdy temat samouczka Wprowadzenie zależy od poprzednich tematach. Aby ukończyć ten temat, najpierw musisz zakończyć poprzednich tematach. Aby pobrać wersję inną ukończone lub wyświetlić Przewodnik wideo tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="to-create-the-custom-tracking-participant"></a>Aby utworzyć niestandardowego uczestnika śledzenia  
  
1. Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **klasy**. Typ `StatusTrackingParticipant` do **nazwa** polu, a następnie kliknij przycisk **Dodaj**.  
  
2. Dodaj następujący kod `using` (lub `Imports`) instrukcji w górnej części pliku razem z innymi `using` (lub `Imports`) instrukcji.  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. Modyfikowanie `StatusTrackingParticipant` klasy, tak aby dziedziczył z `TrackingParticipant`.  
  
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
  
4. Dodaj następujący kod `Track` zastąpienie metody. Istnieje kilka różnych typów rekordów śledzenia. Jesteśmy zainteresowani dane wyjściowe `WriteLine` działań, które są zawarte w działaniu śledzenia rekordów. Jeśli `TrackingRecord` jest `ActivityTrackingRecord` dla `WriteLine` działania `Text` z `WriteLine` jest dołączany do pliku o nazwie po `InstanceId` przepływu pracy. W tym samouczku plik jest zapisywany do bieżącego folderu aplikacji hosta.  
  
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
  
     Jeśli nie określono żadnego profilu śledzenia, jest używany domyślny profil śledzenia. Gdy używany jest domyślny profil śledzenia, dla wszystkich są emitowane rekordów śledzenia `ActivityStates`. Ponieważ musimy przechwytywany tekst jeden raz podczas cyklu życia `WriteLine` działania, firma Microsoft tylko wyodrębniania tekstu z `ActivityStates.Executing` stanu. W [utworzyć profil śledzenia i rejestrowania śledzenia uczestnika](#to-create-the-tracking-profile-and-register-the-tracking-participant), tworzony jest profil śledzenia, który określa, że tylko `WriteLine` `ActivityStates.Executing` są emitowane rekordów śledzenia.  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a>Aby utworzyć profil śledzenia i zarejestrować uczestnika śledzenia  
  
1. Kliknij prawym przyciskiem myszy **WorkflowHostForm** w **Eksploratora rozwiązań** i wybierz polecenie **Wyświetl kod**.  
  
2. Dodaj następujący kod `using` (lub `Imports`) instrukcji w górnej części pliku razem z innymi `using` (lub `Imports`) instrukcji.  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. Dodaj następujący kod do `ConfigureWorkflowApplication` zaraz po kod, który dodaje `StringWriter` rozszerzenia przepływu pracy i przed przepływu pracy obsługi cyklu życia.  
  
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
  
     Ten profil śledzenia Określa, że stan działania tylko rekordy `WriteLine` działań w `Executing` stanu są emitowane do niestandardowego uczestnika śledzenia.  
  
     Po dodaniu kodu początkowego `ConfigureWorkflowApplication` będzie wyglądać podobnie jak w poniższym przykładzie.  
  
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
  
1. Kliknij prawym przyciskiem myszy **WorkflowHostForm** w **Eksploratora rozwiązań** i wybierz polecenie **Wyświetl kod**.  
  
2. W `InstanceId_SelectedIndexChanged` obsługi, Dodaj następujący kod bezpośrednio po kodzie, która Czyści okno stanu.  
  
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
  
     Po wybraniu nowego przepływu pracy na liście przepływów pracy rekordów śledzenia dla tego przepływu pracy są ładowane i wyświetlane w oknie stanu. Poniższy przykład jest gotowy `InstanceId_SelectedIndexChanged` programu obsługi.  
  
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
  
1. Naciśnij klawisze Ctrl + Shift + B, aby skompilować aplikację.  
  
2. Naciśnij klawisze Ctrl + F5, aby uruchomić aplikację.  
  
3. Wybierz zakres do odgadnięcia gier i typ przepływu pracy, aby rozpocząć, a następnie kliknij przycisk **nowych gier**. Wprowadź odgadnięcia w **odgadnięcia** pole, a następnie kliknij przycisk **Przejdź** przesłać przypuszczenie. Należy zauważyć, że stan przepływu pracy jest wyświetlana w oknie stanu. Te dane wyjściowe są przechwytywane z `WriteLine` działań. Przełącz się do innego przepływu pracy, wybierając jedną z **identyfikator wystąpienia przepływu pracy** pola kombi i zwróć uwagę, że stan bieżącego przepływu pracy została usunięta. Przejdź z powrotem do poprzedniej przepływu pracy i zwróć uwagę, że stan został przywrócony, podobny do poniższego przykładu.  
  
    > [!NOTE]
    > Po przełączeniu do przepływu pracy, która została uruchomiona przed włączeniem śledzenia nie stan jest wyświetlany. Jednak w przypadku wprowadzenia dodatkowych prób ich stan jest zapisać, ponieważ włączono śledzenie.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```
    
    > [!NOTE]
    > Te informacje są przydatne do określania zakresu liczb losowych, ale nie zawiera żadnych informacji o jakie prób zostały wprowadzone wcześniej. Te informacje są w następnym kroku [jak: Hostowanie wielu wersji przepływu pracy Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

    Zanotuj identyfikator wystąpienia przepływu pracy i Zagraj w grę za pośrednictwem do jego zakończenia.
  
4. Otwórz Eksploratora Windows i przejdź do **NumberGuessWorkflowHost\bin\debug** folder (lub **bin\release** w zależności od ustawień projektu). Należy zauważyć, że oprócz projekt istnieje pliki wykonywalne pliki przy użyciu identyfikatora guid w nazwach plików. Zidentyfikuj ten, który odpowiada identyfikator wystąpienia przepływu pracy z ukończony przepływ pracy w poprzednim kroku, a następnie otwórz go w Notatniku. Informacje o śledzeniu zawiera informacje podobne do następujących.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    Oprócz braku prób przez użytkownika to dane śledzenia nie zawiera informacji na temat ostateczny wynik przepływu pracy. To dlatego informacje o śledzeniu składa się tylko z `WriteLine` danych wyjściowych z przepływu pracy, końcowe komunikat, który jest wyświetlany jest wykonywane to `Completed` obsługi po ukończeniu przepływu pracy. W następnym kroku samouczka [jak: Hostowanie wielu wersji przepływu pracy Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), istniejące `WriteLine` działań są modyfikowane w celu wyświetlania prób przez użytkownika oraz dodatkowy `WriteLine` dodaniu działania, który wyświetla wyniki końcowe. Po zintegrowaniu są te zmiany, [jak: Hostowanie wielu wersji przepływu pracy Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) pokazuje, jak hostowanie wielu wersji przepływu pracy w tym samym czasie.
