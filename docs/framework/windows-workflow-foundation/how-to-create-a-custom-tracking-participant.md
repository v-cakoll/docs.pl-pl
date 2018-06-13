---
title: 'Porady: Tworzenie niestandardowych śledzenia uczestnika'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 6439a056ec1baccf6c059f779a577723761c489b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519535"
---
# <a name="how-to-create-a-custom-tracking-participant"></a>Porady: Tworzenie niestandardowych śledzenia uczestnika
Śledzenia przepływu pracy zapewnia wgląd w stan wykonywania przepływu pracy. Środowiska uruchomieniowego przepływu pracy emituje rekordy śledzenia, które opisują zdarzenia cyklu życia przepływu pracy, zdarzenia cyklu życia działania zakładki wznawianiu i błędów. Te rekordy śledzenia są używane przez uczestników śledzenia. Windows Workflow Foundation (WF) obejmuje uczestnika standardowe śledzenia, który zapisuje rekordy śledzenia jako zdarzenia funkcji Śledzenie zdarzeń systemu Windows (). Które nie spełnia wymagań, można także napisać uczestnikiem niestandardowe śledzenia. Ten samouczek krok opisuje sposób tworzenia niestandardowych śledzenia uczestnika i profilu śledzenia, który przechwytywania danych wyjściowych `WriteLine` działań, dzięki czemu mogą być wyświetlane dla użytkownika.  
  
> [!NOTE]
>  Każdego tematu w samouczku wprowadzenie zależy od poprzednich tematów. Aby ukończyć w tym temacie, należy wykonać poprzednie tematy. Aby pobrać wersję zakończone lub wyświetlić Przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
-   [Aby utworzyć uczestnika śledzenia niestandardowych](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_CustomTrackingParticipant)  
  
-   [Aby utworzyć profil śledzenia i zarejestrować uczestnika śledzenia](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile)  
  
-   [Aby wyświetlić informacje o śledzeniu](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_DisplayTracking)  
  
-   [Aby skompilować i uruchomić aplikację](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CustomTrackingParticipant"></a> Aby utworzyć uczestnika śledzenia niestandardowych  
  
1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **klasy**. Typ `StatusTrackingParticipant` do **nazwa** i kliknij **Dodaj**.  
  
2.  Dodaj następujące `using` (lub `Imports`) instrukcje w górnej części pliku z innym `using` (lub `Imports`) instrukcje.  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3.  Modyfikowanie `StatusTrackingParticipant` klasy tak, aby dziedziczyła ona z `TrackingParticipant`.  
  
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
  
4.  Dodaj następujące `Track` zastąpienie metody. Istnieje kilka różnych typów rekordów śledzenia. Dbamy o dane wyjściowe `WriteLine` działań, które są zawarte w działaniu śledzenie rekordów. Jeśli `TrackingRecord` jest `ActivityTrackingRecord` dla `WriteLine` działania, `Text` z `WriteLine` jest dołączany do pliku o nazwie po `InstanceId` przepływu pracy. W tym samouczku plik jest zapisywany do bieżącego folderu aplikacji hosta.  
  
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
  
     Jeśli nie określono żadnego profilu śledzenia, używany jest domyślny profilu śledzenia. Gdy używany jest domyślny profil śledzenia, śledzenie rekordów są emitowane dla wszystkich `ActivityStates`. Ponieważ musimy przechwytywania tekst raz w ramach cyklem życia `WriteLine` działania, możemy tylko Wyodrębnij tekst z `ActivityStates.Executing` stanu. W [utworzyć profilu śledzenia i zarejestrować uczestnika śledzenia](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md#BKMK_TrackingProfile), tworzony jest profil śledzenia, który określa, że tylko `WriteLine` `ActivityStates.Executing` są emitowane rekordów śledzenia.  
  
###  <a name="BKMK_TrackingProfile"></a> Aby utworzyć profil śledzenia i zarejestrować uczestnika śledzenia  
  
1.  Kliknij prawym przyciskiem myszy **WorkflowHostForm** w **Eksploratora rozwiązań** i wybierz polecenie **kod widoku**.  
  
2.  Dodaj następujące `using` (lub `Imports`) instrukcji w górnej części pliku z innym `using` (lub `Imports`) instrukcje.  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3.  Dodaj następujący kod do `ConfigureWorkflowApplication` zaraz po kod, który dodaje `StringWriter` rozszerzeń przepływu pracy i przed przepływu pracy obsługi cyklu życia.  
  
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
  
     Ten profil śledzenia Określa, czy stan tylko działania rekordy `WriteLine` działań w `Executing` stanu są emitowane do uczestnika śledzenia niestandardowych.  
  
     Po dodaniu kod początku `ConfigureWorkflowApplication` będzie wyglądać jak w następującym przykładzie.  
  
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
  
###  <a name="BKMK_DisplayTracking"></a> Aby wyświetlić informacje o śledzeniu  
  
1.  Kliknij prawym przyciskiem myszy **WorkflowHostForm** w **Eksploratora rozwiązań** i wybierz polecenie **kod widoku**.  
  
2.  W `InstanceId_SelectedIndexChanged` obsługi, Dodaj następujący kod bezpośrednio po kodzie Czyści okno stanu.  
  
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
  
     Gdy nowy przepływ pracy jest zaznaczony na liście przepływu pracy, rekordy śledzenia dla tego przepływu pracy są załadowana i wyświetlona w oknie stanu. Poniższy przykład jest wypełniony `InstanceId_SelectedIndexChanged` obsługi.  
  
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
  
###  <a name="BKMK_BuildAndRun"></a> Aby skompilować i uruchomić aplikację  
  
1.  Naciśnij klawisze Ctrl + Shift + B do skompilowania aplikacji.  
  
2.  Naciśnij klawisze Ctrl + F5, aby uruchomić aplikację.  
  
3.  Wybierz zakres guessing gry i typ przepływu pracy, aby rozpocząć, a następnie kliknij przycisk **nowych gier**. Wprowadź wynik w **Guess** polu i kliknij przycisk **Przejdź** można przesłać z wynik. Należy pamiętać, że stan przepływu pracy jest wyświetlany w oknie stanu. Te dane wyjściowe są przechwytywane z `WriteLine` działań. Przełącz do innego przepływu pracy, wybierając jedną z **identyfikator wystąpienia przepływu pracy** pole kombi i Uwaga usunięcie stanu bieżącego przepływu pracy. Przejdź do poprzedniego przepływu pracy i należy pamiętać, że stan został przywrócony, podobnie do poniższego przykładu.  
  
    > [!NOTE]
    >  Po przełączeniu do przepływu pracy, które zostało uruchomione przed włączeniem śledzenia nie stan jest wyświetlany. Jednak jeśli dodatkowych prób, ich stan jest zapisany ponieważ śledzenia jest teraz włączony.  
  
 **Wprowadź liczbę z przedziału od 1 do 10**  
**Twoje wynik jest za duża.**   
**Wprowadź liczbę z przedziału od 1 do 10**    
    > [!NOTE]
    >  Informacje te są przydatne do określenia liczbę losową z zakresu, ale nie zawiera żadnych informacji o jakie prób zostały wprowadzone wcześniej. Te informacje są w następnym kroku [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
     Zanotuj identyfikator wystąpienia przepływu pracy i gry za pośrednictwem do jego zakończenia.  
  
4.  Otwórz Eksploratora Windows i przejdź do **NumberGuessWorkflowHost\bin\debug** folder (lub **bin\release** w zależności od ustawienia projektu). Należy zauważyć, że oprócz projektu istnieje pliki wykonywalne pliki z identyfikatora guid w nazwach plików. Zidentyfikuj ten, który odpowiada identyfikator wystąpienia przepływu pracy z przepływu pracy ukończonych w poprzednim kroku, a następnie otwórz go w Notatniku. Informacje o śledzeniu zawiera informacje podobne do następującego.  
  
 **Wprowadź liczbę z przedziału od 1 do 10**  
**Twoje wynik jest za duża.**   
**Wprowadź liczbę z przedziału od 1 do 10**   
**Twoje wynik jest za duża.**   
**Wprowadź liczbę z przedziału od 1 do 10** oprócz braku prób użytkownika, dane śledzenia nie zawiera informacji o wynik końcowy przepływu pracy. Jest to spowodowane informacje o śledzeniu składa się tylko z tym `WriteLine` danych wyjściowych z przepływu pracy, i końcowe komunikat, który jest wyświetlany jest wykonywane z `Completed` obsługi po zakończeniu przepływu pracy. W następnym kroku samouczka [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), istniejące `WriteLine` działania są modyfikowane, aby wyświetlić liczbę prób użytkownika i dodatkowe `WriteLine` dodaniu działania, które Wyświetla wyniki końcowe. Po te zmiany są zintegrowane, [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) pokazano, jak obsługiwać wiele wersji przepływu pracy w tym samym czasie.
