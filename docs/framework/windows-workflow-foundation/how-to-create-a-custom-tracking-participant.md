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
# <a name="how-to-create-a-custom-tracking-participant"></a>Instrukcje: Tworzenie niestandardowego uczestnika śledzenia
Śledzenie przepływu pracy zapewnia wgląd w stan wykonywania przepływu pracy. Środowisko uruchomieniowe przepływu pracy emituje rekordy śledzenia, które opisują zdarzenia cyklu życia przepływu pracy, zdarzenia cyklu życia działań, wznowienia zakładek i błędy. Te rekordy śledzenia są używane przez Śledzenie uczestników. Windows Workflow Foundation (WF) obejmuje uczestnika śledzenia standardowego, który zapisuje rekordy śledzenia jako zdarzenia śledzenia zdarzeń systemu Windows (ETW). Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia. W tym kroku opisano sposób tworzenia niestandardowego uczestnika śledzenia i profilu śledzenia, który przechwytuje dane `WriteLine` wyjściowe działań, dzięki czemu mogą one być wyświetlane użytkownikowi.  
  
> [!NOTE]
> Każdy temat w samouczku Wprowadzenie zależy od poprzednich tematów. Aby ukończyć ten temat, należy najpierw wykonać poprzednie tematy. Aby pobrać kompletną wersję lub wyświetlić przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="to-create-the-custom-tracking-participant"></a>Aby utworzyć uczestnika śledzenia niestandardowego  
  
1. Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **Klasa**. Wpisz `StatusTrackingParticipant` tekst w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.  
  
2. Dodaj następujące `using` instrukcje (lub `Imports`) w górnej części pliku z innymi `using` instrukcjami (lub `Imports`).  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. Zmodyfikuj klasę, aby dziedziczyć po `TrackingParticipant`elemencie. `StatusTrackingParticipant`  
  
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
  
4. Dodaj poniższe `Track` przesłonięcie metody. Istnieje kilka różnych typów rekordów śledzenia. Interesuje Cię dane wyjściowe `WriteLine` działań, które znajdują się w rekordach śledzenia aktywności. `TrackingRecord` Jeśli `WriteLine` jestto`Text` działanie `InstanceId` dla działania ,`WriteLine` jest dołączane do pliku o nazwie po przepływie pracy. `ActivityTrackingRecord` W tym samouczku plik jest zapisywany w bieżącym folderze aplikacji hosta.  
  
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
  
     Gdy nie określono profilu śledzenia, używany jest domyślny profil śledzenia. W przypadku użycia domyślnego profilu śledzenia rekordy śledzenia są emitowane dla wszystkich `ActivityStates`. Ponieważ potrzebujemy tylko jednokrotnego przechwycenia tekstu podczas cyklu życia `WriteLine` działania, wyodrębnimy tylko tekst `ActivityStates.Executing` ze stanu. W programie w [celu utworzenia profilu śledzenia i zarejestrowania uczestnika śledzenia](#to-create-the-tracking-profile-and-register-the-tracking-participant)zostanie utworzony profil śledzenia, który określa, `WriteLine` że są emitowane tylko `ActivityStates.Executing` śledzone rekordy.  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a>Aby utworzyć profil śledzenia i zarejestrować uczestnika śledzenia  
  
1. Kliknij prawym przyciskiem myszy pozycję **WorkflowHostForm** w **Eksplorator rozwiązań** i wybierz polecenie **Wyświetl kod**.  
  
2. Dodaj następującą `using` instrukcję (lub `Imports`) w górnej części pliku z innymi `using` instrukcjami (lub `Imports`).  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. Dodaj następujący kod do `ConfigureWorkflowApplication` tuż po kodzie, który `StringWriter` dodaje do rozszerzeń przepływu pracy i przed obsługą cyklu życia przepływu pracy.  
  
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
  
     Ten profil śledzenia Określa, że tylko rekordy stanu działania `WriteLine` dla działań `Executing` w stanie są emitowane do uczestnika niestandardowego śledzenia.  
  
     Po dodaniu kodu początek `ConfigureWorkflowApplication` będzie wyglądał jak w poniższym przykładzie.  
  
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
  
1. Kliknij prawym przyciskiem myszy pozycję **WorkflowHostForm** w **Eksplorator rozwiązań** i wybierz polecenie **Wyświetl kod**.  
  
2. W programie `InstanceId_SelectedIndexChanged` obsługi Dodaj następujący kod bezpośrednio po kodzie, który czyści okno stanu.  
  
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
  
     Po wybraniu nowego przepływu pracy na liście przepływów pracy rekordy śledzenia dla tego przepływu pracy są ładowane i wyświetlane w oknie stanu. Poniższy przykład to zakończono `InstanceId_SelectedIndexChanged` procedurę obsługi.  
  
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
  
1. Naciśnij klawisze CTRL + SHIFT + B, aby skompilować aplikację.  
  
2. Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.  
  
3. Wybierz zakres dla gry do odgadnięcia i typ przepływu pracy do uruchomienia, a następnie kliknij pozycję **Nowa gra**. Wprowadź wartość w polu **zgadywanie** i kliknij pozycję **Przejdź** , aby przesłać przypuszczenie. Należy zauważyć, że w oknie stanu jest wyświetlany stan przepływu pracy. Te dane wyjściowe są przechwytywane `WriteLine` z działań. Przejdź do innego przepływu pracy, wybierając go z pola kombi **Identyfikator wystąpienia przepływu pracy** i pamiętaj, że bieżący przepływ pracy jest usuwany. Przełącz się z powrotem do poprzedniego przepływu pracy i pamiętaj, że stan jest przywrócony, podobnie jak w poniższym przykładzie.  
  
    > [!NOTE]
    > Jeśli przełączysz się do przepływu pracy, który został uruchomiony przed włączeniem śledzenia, stan nie jest wyświetlany. Jeśli jednak wprowadzisz dodatkowe odgadnięcia, ich stan jest zapisywany, ponieważ śledzenie jest teraz włączone.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```
    
    > [!NOTE]
    > Te informacje są przydatne do określania zakresu liczby losowej, ale nie zawierają żadnych informacji o tym, jakie odgadnięcia zostały wcześniej wykonane. Te informacje są w następnym kroku [: Hostowanie wielu wersji przepływu pracy obok](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)siebie.

    Zanotuj identyfikator wystąpienia przepływu pracy, a następnie Odtwórz grę do końca.
  
4. Otwórz Eksploratora Windows i przejdź do folderu **NumberGuessWorkflowHost\bin\debug** (lub **bin\Release** w zależności od ustawień projektu). Należy pamiętać, że oprócz plików wykonywalnych projektu istnieją pliki z nazwami plików GUID. Zidentyfikuj ten, który odpowiada identyfikatorowi wystąpienia przepływu pracy z ukończonego przepływu pracy w poprzednim kroku, i otwórz go w Notatniku. Informacje o śledzeniu zawierają informacje podobne do następujących.  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    Poza brakiem prób użytkownika, dane śledzenia nie zawierają informacji o końcowej próbie przepływu pracy. Wynika to z faktu, że informacje o śledzeniu obejmują tylko `WriteLine` dane wyjściowe z przepływu pracy, a końcowy komunikat, który jest wyświetlany, jest wykonywany `Completed` z programu obsługi po zakończeniu przepływu pracy. W następnym kroku samouczka [: Hostowanie wielu wersji przepływu pracy obok](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)siebie, istniejące `WriteLine` działania są modyfikowane w celu wyświetlenia odgadnięcia użytkownika i dodawane jest dodatkowe `WriteLine` działanie, które wyświetla końcowe wyniki. Po zintegrowaniu tych zmian należy [: Hostowanie wielu wersji przepływu pracy obok siebie](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) pokazuje, jak hostować wiele wersji przepływu pracy w tym samym czasie.
