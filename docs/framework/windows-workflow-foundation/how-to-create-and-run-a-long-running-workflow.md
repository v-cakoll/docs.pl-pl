---
title: 'Instrukcje: Tworzenie i uruchamianie długotrwałego przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 75fa4fcdef9bf8e2773264fff4a8404330909e6b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962339"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a>Instrukcje: Tworzenie i uruchamianie długotrwałego przepływu pracy
Jedną z centralnych funkcji Windows Workflow Foundation (WF) jest zdolność środowiska uruchomieniowego do utrwalania i zwalniania bezczynnych przepływów pracy do bazy danych. Kroki opisane w [temacie How to: Uruchom przepływ pracy](how-to-run-a-workflow.md) przedstawiający podstawowe informacje o hostingu przepływu pracy przy użyciu aplikacji konsolowej. Przedstawiono przykłady uruchamiania przepływów pracy, obsługi cyklu życia przepływu pracy i wznawiania zakładek. W celu efektywnego zademonstrowania trwałości przepływu pracy wymagany jest bardziej złożony host przepływu pracy, który obsługuje uruchamianie i wznawianie wielu wystąpień przepływu pracy. Ten krok w samouczku pokazuje, jak utworzyć aplikację hosta formularza systemu Windows, która obsługuje uruchamianie i wznawianie wielu wystąpień przepływów pracy, trwałości przepływu pracy i stanowi podstawę zaawansowanych funkcji, takich jak śledzenie i przechowywanie wersji przedstawiono w kolejnych krokach samouczka.  
  
> [!NOTE]
> Ten krok samouczka i kolejne kroki używają wszystkich trzech typów [przepływu pracy: Utwórz przepływ pracy](how-to-create-a-workflow.md). Jeśli wszystkie trzy typy nie zostały wykonane, można pobrać ukończoną wersję kroków z [Windows Workflow Foundation (WF45) — wprowadzenie samouczka](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
> [!NOTE]
> Aby pobrać kompletną wersję lub wyświetlić przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
- [Aby utworzyć bazę danych trwałości](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)  
  
- [Aby dodać odwołanie do zestawów DurableInstancing](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)  
  
- [Aby utworzyć formularz hosta przepływu pracy](how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)  
  
- [Aby dodać właściwości i metody pomocnika formularza](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)  
  
- [Aby skonfigurować magazyn wystąpień, programy obsługi cyklu życia przepływu pracy i rozszerzenia](how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)  
  
- [Aby włączyć uruchamianie i wznawianie wielu typów przepływów pracy](how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)  
  
- [Aby uruchomić nowy przepływ pracy](how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)  
  
- [Aby wznowić przepływ pracy](how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)  
  
- [Aby zakończyć przepływ pracy](how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)  
  
- [Aby skompilować i uruchomić aplikację](how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)  
  
### <a name="BKMK_CreatePersistenceDatabase"></a>Aby utworzyć bazę danych trwałości  
  
1. Otwórz SQL Server Management Studio i Połącz się z serwerem lokalnym, na przykład **.\SQLEXPRESS**. Kliknij prawym przyciskiem myszy węzeł **bazy danych** na serwerze lokalnym, a następnie wybierz pozycję **Nowa baza danych**. Nazwa nowej bazy danych **WF45GettingStartedTutorial**, Zaakceptuj wszystkie inne wartości, a następnie wybierz **przycisk OK**.  
  
    > [!NOTE]
    > Przed utworzeniem bazy danych upewnij się, że masz uprawnienia do **tworzenia bazy danych** na serwerze lokalnym.  
  
2. Wybierz polecenie **Otwórz**, **plik** z menu **plik** . Przejdź do następującego folderu:`C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`  
  
     Wybierz poniższe dwa pliki, a następnie kliknij przycisk **Otwórz**.  
  
    - SqlWorkflowInstanceStoreLogic.sql  
  
    - SqlWorkflowInstanceStoreSchema.sql  
  
3. Wybierz **SqlWorkflowInstanceStoreSchema. SQL** z menu **okno** . Upewnij się, że wybrano pozycję **WF45GettingStartedTutorial** na liście rozwijanej **dostępne bazy danych** , a następnie wybierz polecenie **Wykonaj** z menu **zapytania** .  
  
4. Wybierz **SqlWorkflowInstanceStoreLogic. SQL** z menu **okno** . Upewnij się, że wybrano pozycję **WF45GettingStartedTutorial** na liście rozwijanej **dostępne bazy danych** , a następnie wybierz polecenie **Wykonaj** z menu **zapytania** .  
  
    > [!WARNING]
    >  Ważne jest, aby wykonać dwa poprzednie kroki w odpowiedniej kolejności. Jeśli zapytania są wykonywane poza kolejnością, wystąpią błędy i baza danych trwałości nie jest poprawnie skonfigurowana.  
  
### <a name="BKMK_AddReference"></a>Aby dodać odwołanie do zestawów DurableInstancing  
  
1. Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj odwołanie**.  
  
2. Wybierz pozycję **zestawy** z listy **Dodaj odwołanie** , a następnie `DurableInstancing` wpisz w polu **wyszukiwania zestawów** . To filtruje zestawy i ułatwia wybór odpowiednich odwołań.  
  
3. Zaznacz pole wyboru obok pozycji **System. Activities. DurableInstancing** i **System. Runtime. DurableInstancing** z listy **wyników wyszukiwania** , a następnie kliknij przycisk **OK**.  
  
### <a name="BKMK_CreateForm"></a>Aby utworzyć formularz hosta przepływu pracy  
  
> [!NOTE]
> Kroki opisane w tej procedurze opisują sposób ręcznego dodawania i konfigurowania formularza. W razie potrzeby można pobrać pliki rozwiązania dla samouczka i dodać ukończony formularz do projektu. Aby pobrać pliki samouczka, zobacz [Windows Workflow Foundation (WF45) — samouczek wprowadzenie](https://go.microsoft.com/fwlink/?LinkID=248976). Po pobraniu plików kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** i wybierz polecenie **Dodaj odwołanie**. Dodaj odwołanie do **System. Windows. Forms** i **System. Drawing**. Te odwołania są dodawane automatycznie po dodaniu nowego formularza z menu **Dodaj**, **nowy element** , ale należy dodać go ręcznie podczas importowania formularza. Po dodaniu odwołań kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **istniejący element**. Przejdź `Form` do folderu w plikach projektu, wybierz pozycję **WorkflowHostForm.cs** (lub **WorkflowHostForm. vb**), a następnie kliknij przycisk **Dodaj**. Jeśli zdecydujesz się zaimportować formularz, możesz przejść do następnej sekcji, [Aby dodać właściwości i metody pomocnika formularza](how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).  
  
1. Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **nowy element**.  
  
2. Na liście **zainstalowane** szablony wybierz pozycję **formularz systemu Windows**, wpisz `WorkflowHostForm` w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.  
  
3. Skonfiguruj następujące właściwości w formularzu.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |FormBorderStyle|FixedSingle|  
    |MaximizeBox|False|  
    |Rozmiar|400, 420|  
  
4. Dodaj następujące kontrolki do formularza w określonej kolejności i skonfiguruj właściwości jako kierowane.  
  
    |formant|Wartość Wartość|  
    |-------------|---------------------|  
    |**Przycisk**|Nazwij NewGame<br /><br /> Przeniesienie 13, 13<br /><br /> Zmienia 75, 23<br /><br /> Opis Nowa gra|  
    |**Etykieta**|Przeniesienie 94, 18<br /><br /> Opis Zgadywanie liczby z 1 do|  
    |**ComboBox**|Nazwij NumberRange<br /><br /> DropDownStyle: DropDownList<br /><br /> Produktów 10, 100, 1000<br /><br /> Przeniesienie 228, 12<br /><br /> Zmienia 143, 21|  
    |**Etykieta**|Przeniesienie 13, 43<br /><br /> Opis Typ przepływu pracy|  
    |**ComboBox**|Nazwij Menedżer przepływów pracy<br /><br /> DropDownStyle: DropDownList<br /><br /> Produktów StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow, SequentialNumberGuessWorkflow<br /><br /> Przeniesienie 94, 40<br /><br /> Zmienia 277, 21|  
    |**Etykieta**|Nazwij WorkflowVersion<br /><br /> Przeniesienie 13, 362<br /><br /> Opis Wersja przepływu pracy|  
    |**GroupBox**|Przeniesienie 13, 67<br /><br /> Zmienia 358, 287<br /><br /> Opis Rozgrywk|  
  
    > [!NOTE]
    > Podczas dodawania następujących kontrolek należy umieścić je w polu grupy.  
  
    |formant|Wartość Wartość|  
    |-------------|---------------------|  
    |**Etykieta**|Przeniesienie 7, 20<br /><br /> Opis Identyfikator wystąpienia przepływu pracy|  
    |**ComboBox**|Nazwij Identyfikator wystąpienia<br /><br /> DropDownStyle: DropDownList<br /><br /> Przeniesienie 121, 17<br /><br /> Zmienia 227, 21|  
    |**Etykieta**|Przeniesienie 7, 47<br /><br /> Opis Stanie|  
    |**TextBox**|Nazwij Stanie<br /><br /> Przeniesienie 50, 44<br /><br /> Zmienia 65, 20|  
    |**Przycisk**|Nazwij EnterGuess<br /><br /> Przeniesienie 121, 42<br /><br /> Zmienia 75, 23<br /><br /> Opis Wprowadź zgadywanie|  
    |**Przycisk**|Nazwij QuitGame<br /><br /> Przeniesienie 274, 42<br /><br /> Zmienia 75, 23<br /><br /> Opis Spowoduje|  
    |**TextBox**|Nazwij WorkflowStatus<br /><br /> Przeniesienie 10, 73<br /><br /> Multiline Prawda<br /><br /> Trybie Prawda<br /><br /> Paski przewijania Pionow<br /><br /> Zmienia 338, 208|  
  
5. Ustaw właściwość **AcceptButton** formularza na **EnterGuess**.  
  
 Poniższy przykład ilustruje ukończony formularz.  
  
 ![Zrzut ekranu przedstawiający formularz hosta przepływu Windows Workflow Foundation.](./media/how-to-create-and-run-a-long-running-workflow/windows-workflow-foundation-workflowhostform.png)  
  
### <a name="BKMK_AddHelperMethods"></a>Aby dodać właściwości i metody pomocnika formularza  
 Kroki opisane w tej sekcji dodają właściwości i metody pomocnika do klasy form, która konfiguruje interfejs użytkownika formularza do obsługi uruchamiania i wznawiania przepływów pracy dotyczących liczby prób.  
  
1. Kliknij prawym przyciskiem myszy pozycję **WorkflowHostForm** w **Eksplorator rozwiązań** i wybierz polecenie **Wyświetl kod**.  
  
2. Dodaj następujące `using` instrukcje (lub `Imports`) w górnej części pliku z innymi `using` instrukcjami (lub `Imports`).  
  
    ```vb  
    Imports System.Windows.Forms  
    Imports System.Activities.DurableInstancing  
    Imports System.Activities  
    Imports System.Data.SqlClient  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    using System.Activities.DurableInstancing;  
    using System.Activities;  
    using System.Data.SqlClient;  
    using System.IO;  
    ```  
  
3. Dodaj następujące deklaracje elementu członkowskiego do klasy **WorkflowHostForm** .  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    Dim store As SqlWorkflowInstanceStore  
    Dim WorkflowStarting As Boolean  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    SqlWorkflowInstanceStore store;  
    bool WorkflowStarting;  
    ```  
  
    > [!NOTE]
    > Jeśli parametry połączenia są inne, zaktualizuj `connectionString` , aby odwołać się do bazy danych.  
  
4. `WorkflowInstanceId` Dodaj Właściwość`WorkflowFormHost` do klasy.  
  
    ```vb  
    Public ReadOnly Property WorkflowInstanceId() As Guid  
        Get  
            If InstanceId.SelectedIndex = -1 Then  
                Return Guid.Empty  
            Else  
                Return New Guid(InstanceId.SelectedItem.ToString())  
            End If  
        End Get  
    End Property  
    ```  
  
    ```csharp  
    public Guid WorkflowInstanceId  
    {  
        get  
        {  
            return InstanceId.SelectedIndex == -1 ? Guid.Empty : (Guid)InstanceId.SelectedItem;  
        }  
    }  
    ```  
  
     Pole kombi wyświetla listę utrwalonych identyfikatorów wystąpień przepływów pracy, `WorkflowInstanceId` a właściwość zwraca aktualnie wybrany przepływ pracy. `InstanceId`  
  
5. Dodaj procedurę obsługi dla zdarzenia formularza `Load` . Aby dodać procedurę obsługi, przełącz się do **widoku projektu** dla formularza, kliknij ikonę **zdarzenia** w górnej części okna **Właściwości** , a następnie kliknij dwukrotnie przycisk Wczytaj.  
  
    ```vb  
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load  
  
    End Sub  
    ```  
  
    ```csharp  
    private void WorkflowHostForm_Load(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
6. Dodaj następujący kod do `WorkflowHostForm_Load`.  
  
    ```vb  
    'Initialize the store and configure it so that it can be used for  
    'multiple WorkflowApplication instances.  
    store = New SqlWorkflowInstanceStore(connectionString)  
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)  
  
    'Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0  
    WorkflowType.SelectedIndex = 0  
  
    ListPersistedWorkflows()  
    ```  
  
    ```csharp  
    // Initialize the store and configure it so that it can be used for  
    // multiple WorkflowApplication instances.  
    store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);  
  
    // Set default ComboBox selections.  
    NumberRange.SelectedIndex = 0;  
    WorkflowType.SelectedIndex = 0;  
  
    ListPersistedWorkflows();  
    ```  
  
     Gdy formularz `SqlWorkflowInstanceStore` zostanie załadowany, jest skonfigurowany, pole kombi zakres i typ przepływu pracy są ustawiane na wartości domyślne, a wystąpienia utrwalonych przepływów pracy są dodawane `InstanceId` do pola kombi.  
  
7. Dodaj program obsługi dla `InstanceId`. `SelectedIndexChanged` Aby dodać procedurę obsługi, przełącz się **do widoku projektu** dla formularza, zaznacz `InstanceId` pole kombi, kliknij ikonę **zdarzenia** w górnej części okna **Właściwości** , a następnie kliknij dwukrotnie pozycję **SelectedIndexChanged.** .  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
8. Dodaj następujący kod do `InstanceId_SelectedIndexChanged`. Za każdym razem, gdy użytkownik wybierze przepływ pracy za pomocą pola kombi, ta procedura obsługi aktualizuje okno stanu.  
  
    ```vb  
    If InstanceId.SelectedIndex = -1 Then  
        Return  
    End If  
  
    'Clear the status window.  
    WorkflowStatus.Clear()  
  
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
    ```  
  
    ```csharp  
    if (InstanceId.SelectedIndex == -1)  
    {  
        return;  
    }  
  
    // Clear the status window.  
    WorkflowStatus.Clear();  
  
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
    ```  
  
9. Dodaj następującą `ListPersistedWorkflows` metodę do klasy form.  
  
    ```vb  
    Private Sub ListPersistedWorkflows()  
        Using localCon As New SqlConnection(connectionString)  
            Dim localCmd As String = _  
                "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]"  
  
            Dim cmd As SqlCommand = localCon.CreateCommand()  
            cmd.CommandText = localCmd  
            localCon.Open()  
            Using reader As SqlDataReader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
  
                While (reader.Read())  
                    'Get the InstanceId of the persisted Workflow.  
                    Dim id As Guid = Guid.Parse(reader(0).ToString())  
                    InstanceId.Items.Add(id)  
                End While  
            End Using  
        End Using  
    End Sub  
    ```  
  
    ```csharp  
    using (SqlConnection localCon = new SqlConnection(connectionString))  
    {  
        string localCmd =  
            "Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]";  
  
        SqlCommand cmd = localCon.CreateCommand();  
        cmd.CommandText = localCmd;  
        localCon.Open();  
        using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))  
        {  
            while (reader.Read())  
            {  
                // Get the InstanceId of the persisted Workflow  
                Guid id = Guid.Parse(reader[0].ToString());  
                InstanceId.Items.Add(id);  
            }  
        }  
    }  
    ```  
  
     `ListPersistedWorkflows`wysyła zapytanie do magazynu wystąpień dla utrwalonych wystąpień przepływu pracy i dodaje do `cboInstanceId` pola kombi identyfikatory wystąpień.  
  
10. Dodaj następującą `UpdateStatus` metodę i odpowiedni delegat do klasy form. Ta metoda aktualizuje okno stanu w formularzu przy użyciu stanu aktualnie uruchomionego przepływu pracy.  
  
    ```vb  
    Private Delegate Sub UpdateStatusDelegate(msg As String)  
    Public Sub UpdateStatus(msg As String)  
        'We may be on a different thread so we need to  
        'make this call using BeginInvoke.  
        If InvokeRequired Then  
            BeginInvoke(New UpdateStatusDelegate(AddressOf UpdateStatus), msg)  
        Else  
            If Not msg.EndsWith(vbCrLf) Then  
                msg = msg & vbCrLf  
            End If  
  
            WorkflowStatus.AppendText(msg)  
  
            'Ensure that the newly added status is visible.  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length  
            WorkflowStatus.ScrollToCaret()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void UpdateStatusDelegate(string msg);  
    public void UpdateStatus(string msg)  
    {  
        // We may be on a different thread so we need to  
        // make this call using BeginInvoke.  
        if (InvokeRequired)  
        {  
            BeginInvoke(new UpdateStatusDelegate(UpdateStatus), msg);  
        }  
        else  
        {  
            if (!msg.EndsWith("\r\n"))  
            {  
                msg += "\r\n";  
            }  
            WorkflowStatus.AppendText(msg);  
  
            WorkflowStatus.SelectionStart = WorkflowStatus.Text.Length;  
            WorkflowStatus.ScrollToCaret();  
        }  
    }  
    ```  
  
11. Dodaj następującą `GameOver` metodę i odpowiedni delegat do klasy form. Po zakończeniu przepływu pracy ta metoda aktualizuje interfejs użytkownika formularza, usuwając identyfikator wystąpienia ukończonego przepływu pracy z pola kombi **InstanceId** .  
  
    ```vb  
    Private Delegate Sub GameOverDelegate()  
    Private Sub GameOver()  
        If InvokeRequired Then  
            BeginInvoke(New GameOverDelegate(AddressOf GameOver))  
        Else  
            'Remove this instance from the InstanceId combo box.  
            InstanceId.Items.Remove(InstanceId.SelectedItem)  
            InstanceId.SelectedIndex = -1  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private delegate void GameOverDelegate();  
    private void GameOver()  
    {  
        if (InvokeRequired)  
        {  
            BeginInvoke(new GameOverDelegate(GameOver));  
        }  
        else  
        {  
            // Remove this instance from the combo box  
            InstanceId.Items.Remove(InstanceId.SelectedItem);  
            InstanceId.SelectedIndex = -1;  
        }  
    }  
    ```  
  
### <a name="BKMK_ConfigureWorkflowApplication"></a>Aby skonfigurować magazyn wystąpień, programy obsługi cyklu życia przepływu pracy i rozszerzenia  
  
1. `ConfigureWorkflowApplication` Dodaj metodę do klasy form.  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {      
    }  
    ```  
  
     Ta metoda służy do `WorkflowApplication`konfigurowania, dodawania wymaganych rozszerzeń i dodawania programów obsługi dla zdarzeń cyklu życia przepływu pracy.  
  
2. W `ConfigureWorkflowApplication`programie `SqlWorkflowInstanceStore` Określ dla elementu. `WorkflowApplication`  
  
    ```vb  
    'Configure the persistence store.  
    wfApp.InstanceStore = store  
    ```  
  
    ```csharp  
    // Configure the persistence store.  
    wfApp.InstanceStore = store;  
    ```  
  
3. Następnie Utwórz `StringWriter` wystąpienie i Dodaj je `Extensions` do kolekcji `WorkflowApplication`. Po dodaniu do rozszerzeń przechwytuje wszystkie `WriteLine` dane wyjściowe działania. `StringWriter` Gdy przepływ pracy stanie się bezczynny, `WriteLine` dane wyjściowe można wyodrębnić `StringWriter` z i wyświetlić w formularzu.  
  
    ```vb  
    'Add a StringWriter to the extensions. This captures the output  
    'from the WriteLine activities so we can display it in the form.  
    Dim sw As New StringWriter()  
    wfApp.Extensions.Add(sw)  
    ```  
  
    ```csharp  
    // Add a StringWriter to the extensions. This captures the output  
    // from the WriteLine activities so we can display it in the form.  
    StringWriter sw = new StringWriter();  
    wfApp.Extensions.Add(sw);  
    ```  
  
4. Dodaj następującą procedurę obsługi dla `Completed` zdarzenia. Po pomyślnym ukończeniu przepływu pracy Liczba przełączeń podjętych w celu odgadnięcia liczby zostanie wyświetlona w oknie stanu. Jeśli przepływ pracy zakończy działanie, zostanie wyświetlona informacja o wyjątku, która spowodowała zakończenie. Na końcu procedury obsługi `GameOver` wywoływana jest metoda, która usuwa ukończony przepływ pracy z listy przepływów pracy.  
  
    ```vb  
    wfApp.Completed = _  
        Sub(e As WorkflowApplicationCompletedEventArgs)  
            If e.CompletionState = ActivityInstanceState.Faulted Then  
                UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                    e.TerminationException.GetType().FullName, _  
                    e.TerminationException.Message))  
            ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                UpdateStatus("Workflow Canceled.")  
            Else  
                Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
            End If  
            GameOver()  
        End Sub  
    ```  
  
    ```csharp  
    wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
    {  
        if (e.CompletionState == ActivityInstanceState.Faulted)  
        {  
            UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                e.TerminationException.GetType().FullName,  
                e.TerminationException.Message));  
        }  
        else if (e.CompletionState == ActivityInstanceState.Canceled)  
        {  
            UpdateStatus("Workflow Canceled.");  
        }  
        else  
        {  
            int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
            UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
        }  
        GameOver();  
    };  
    ```  
  
5. Dodaj poniższe `Aborted` i `OnUnhandledException` programy obsługi. Metoda nie jest wywoływana `Aborted` z programu obsługi, ponieważ wystąpienie przepływu pracy zostało przerwane, nie kończy się i możliwe jest wznowienie wystąpienia w późniejszym czasie. `GameOver`  
  
    ```vb  
    wfApp.Aborted = _  
        Sub(e As WorkflowApplicationAbortedEventArgs)  
            UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                e.Reason.GetType().FullName, _  
                e.Reason.Message))  
        End Sub  
  
    wfApp.OnUnhandledException = _  
        Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
            UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                e.UnhandledException.GetType().FullName, _  
                e.UnhandledException.Message))  
            GameOver()  
            Return UnhandledExceptionAction.Terminate  
        End Function  
    ```  
  
    ```csharp  
    wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
    {  
        UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                e.Reason.GetType().FullName,  
                e.Reason.Message));  
    };  
  
    wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
    {  
        UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                e.UnhandledException.GetType().FullName,  
                e.UnhandledException.Message));  
        GameOver();  
        return UnhandledExceptionAction.Terminate;  
    };  
    ```  
  
6. Dodaj następujący `PersistableIdle` program obsługi. Ta procedura obsługi pobiera `StringWriter` dodane rozszerzenie, wyodrębnia dane wyjściowe `WriteLine` z działań i wyświetla je w oknie stanu.  
  
    ```vb  
    wfApp.PersistableIdle = _  
        Function(e As WorkflowApplicationIdleEventArgs)  
            'Send the current WriteLine outputs to the status window.  
            Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
            For Each writer In writers  
                UpdateStatus(writer.ToString())  
            Next  
            Return PersistableIdleAction.Unload  
        End Function  
    ```  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        // Send the current WriteLine outputs to the status window.  
        var writers = e.GetInstanceExtensions<StringWriter>();  
        foreach (var writer in writers)  
        {  
            UpdateStatus(writer.ToString());  
        }  
        return PersistableIdleAction.Unload;  
    };  
    ```  
  
     Wyliczenie ma trzy wartości: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, i <xref:System.Activities.PersistableIdleAction.Unload>. <xref:System.Activities.PersistableIdleAction> <xref:System.Activities.PersistableIdleAction.Persist>powoduje, że przepływ pracy ma być trwały, ale nie powoduje jego zwolnienia. <xref:System.Activities.PersistableIdleAction.Unload>powoduje, że przepływ pracy jest trwały i zwalniany.  
  
     Poniższy przykład to metoda zakończona `ConfigureWorkflowApplication` .  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        wfApp.Completed = _  
            Sub(e As WorkflowApplicationCompletedEventArgs)  
                If e.CompletionState = ActivityInstanceState.Faulted Then  
                    UpdateStatus(String.Format("Workflow Terminated. Exception: {0}" & vbCrLf & "{1}", _  
                        e.TerminationException.GetType().FullName, _  
                        e.TerminationException.Message))  
                ElseIf e.CompletionState = ActivityInstanceState.Canceled Then  
                    UpdateStatus("Workflow Canceled.")  
                Else  
                    Dim Turns As Integer = Convert.ToInt32(e.Outputs("Turns"))  
                    UpdateStatus(String.Format("Congratulations, you guessed the number in {0} turns.", Turns))  
                End If  
                GameOver()  
            End Sub  
  
        wfApp.Aborted = _  
            Sub(e As WorkflowApplicationAbortedEventArgs)  
                UpdateStatus(String.Format("Workflow Aborted. Exception: {0}" & vbCrLf & "{1}", _  
                    e.Reason.GetType().FullName, _  
                    e.Reason.Message))  
            End Sub  
  
        wfApp.OnUnhandledException = _  
            Function(e As WorkflowApplicationUnhandledExceptionEventArgs)  
                UpdateStatus(String.Format("Unhandled Exception: {0}" & vbCrLf & "{1}", _  
                    e.UnhandledException.GetType().FullName, _  
                    e.UnhandledException.Message))  
                GameOver()  
                Return UnhandledExceptionAction.Terminate  
            End Function  
  
        wfApp.PersistableIdle = _  
            Function(e As WorkflowApplicationIdleEventArgs)  
                'Send the current WriteLine outputs to the status window.  
                Dim writers = e.GetInstanceExtensions(Of StringWriter)()  
                For Each writer In writers  
                    UpdateStatus(writer.ToString())  
                Next  
                Return PersistableIdleAction.Unload  
            End Function  
    End Sub  
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
  
        wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
        {  
            if (e.CompletionState == ActivityInstanceState.Faulted)  
            {  
                UpdateStatus(string.Format("Workflow Terminated. Exception: {0}\r\n{1}",  
                    e.TerminationException.GetType().FullName,  
                    e.TerminationException.Message));  
            }  
            else if (e.CompletionState == ActivityInstanceState.Canceled)  
            {  
                UpdateStatus("Workflow Canceled.");  
            }  
            else  
            {  
                int Turns = Convert.ToInt32(e.Outputs["Turns"]);  
                UpdateStatus(string.Format("Congratulations, you guessed the number in {0} turns.", Turns));  
            }  
            GameOver();  
        };  
  
        wfApp.Aborted = delegate(WorkflowApplicationAbortedEventArgs e)  
        {  
            UpdateStatus(string.Format("Workflow Aborted. Exception: {0}\r\n{1}",  
                    e.Reason.GetType().FullName,  
                    e.Reason.Message));  
        };  
  
        wfApp.OnUnhandledException = delegate(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            UpdateStatus(string.Format("Unhandled Exception: {0}\r\n{1}",  
                    e.UnhandledException.GetType().FullName,  
                    e.UnhandledException.Message));  
            GameOver();  
            return UnhandledExceptionAction.Terminate;  
        };  
  
        wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
        {  
            // Send the current WriteLine outputs to the status window.  
            var writers = e.GetInstanceExtensions<StringWriter>();  
            foreach (var writer in writers)  
            {  
                UpdateStatus(writer.ToString());  
            }  
            return PersistableIdleAction.Unload;  
        };  
    }  
    ```  
  
### <a name="BKMK_WorkflowVersionMap"></a>Aby włączyć uruchamianie i wznawianie wielu typów przepływów pracy  
 Aby wznowić wystąpienie przepływu pracy, host musi podać definicję przepływu pracy. W tym samouczku istnieją trzy typy przepływów pracy, a kolejne kroki samouczka wprowadzają wiele wersji tych typów. `WorkflowIdentity`umożliwia aplikacji hosta kojarzenie informacji identyfikacyjnych z utrwalonym wystąpieniem przepływu pracy. Kroki opisane w tej sekcji przedstawiają sposób tworzenia klasy narzędzi, która pomaga w mapowaniu tożsamości przepływu pracy z utrwalonego wystąpienia przepływu pracy do odpowiedniej definicji przepływu pracy. Aby uzyskać więcej informacji `WorkflowIdentity` na temat usługi i przechowywania wersji, zobacz [Korzystanie z właściwości WorkflowIdentity i przechowywanie wersji](using-workflowidentity-and-versioning.md).  
  
1. Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **Klasa**. Wpisz `WorkflowVersionMap` tekst w polu **Nazwa** , a następnie kliknij przycisk **Dodaj**.  
  
2. Dodaj następujące `using` instrukcje lub `Imports` na początku pliku z innymi `using` instrukcjami or `Imports` .  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Activities  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Activities;  
    ```  
  
3. Zastąp `WorkflowVersionMap` deklarację klasy następującą deklaracją.  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
        End Sub  
  
        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity  
            Return map(identity)  
        End Function  
  
        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String  
            Return identity.ToString()  
        End Function  
    End Module  
    ```  
  
    ```csharp  
    public static class WorkflowVersionMap  
    {  
        static Dictionary<WorkflowIdentity, Activity> map;  
  
        // Current version identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity;  
        static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
        }  
  
        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)  
        {  
            return map[identity];  
        }  
  
        public static string GetIdentityDescription(WorkflowIdentity identity)  
        {          
            return identity.ToString();  
       }  
    }  
    ```  
  
     `WorkflowVersionMap`zawiera trzy tożsamości przepływu pracy, które są mapowane na trzy definicje przepływu pracy z tego samouczka i są używane w poniższych sekcjach, gdy przepływy pracy są uruchamiane i wznawiane.  
  
### <a name="BKMK_StartWorkflow"></a>Aby uruchomić nowy przepływ pracy  
  
1. Dodaj program obsługi dla `NewGame`. `Click` Aby dodać procedurę obsługi, przełącz się do **widoku projektu** dla formularza i kliknij `NewGame`dwukrotnie. Dodano `NewGame_Click` procedurę obsługi, a widok jest przełączany do widoku kodu formularza. Za każdym razem, gdy użytkownik kliknie ten przycisk, zostanie uruchomiony nowy przepływ pracy.  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2. Dodaj następujący kod do programu obsługi kliknij. Ten kod tworzy słownik argumentów wejściowych dla przepływu pracy, który jest poprzedzony przez nazwę argumentu. Ten słownik zawiera jeden wpis zawierający zakres losowo wygenerowanego numeru pobrany z pola kombi zakres.  
  
    ```vb  
    Dim inputs As New Dictionary(Of String, Object)()  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
    ```  
  
    ```csharp  
    var inputs = new Dictionary<string, object>();  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
    ```  
  
3. Następnie Dodaj następujący kod, który uruchamia przepływ pracy. Definicja przepływu pracy `WorkflowVersionMap` iodpowiadającytypowiwybranegoprzepływupracysąpobieraneprzyużyciu`WorkflowIdentity` klasy pomocnika. Następnie nowe `WorkflowApplication` wystąpienie jest tworzone przy użyciu definicji przepływu pracy, `WorkflowIdentity`i słownika argumentów wejściowych.  
  
    ```vb  
    Dim identity As WorkflowIdentity = Nothing  
    Select Case WorkflowType.SelectedItem.ToString()  
        Case "SequentialNumberGuessWorkflow"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
        Case "StateMachineNumberGuessWorkflow"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
        Case "FlowchartNumberGuessWorkflow"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
    End Select  
  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
    Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
    ```  
  
    ```csharp  
    WorkflowIdentity identity = null;  
    switch (WorkflowType.SelectedItem.ToString())  
    {  
        case "SequentialNumberGuessWorkflow":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
            break;  
  
        case "StateMachineNumberGuessWorkflow":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
            break;  
  
        case "FlowchartNumberGuessWorkflow":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
            break;  
    };  
  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
    WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
    ```  
  
4. Następnie Dodaj następujący kod, który dodaje przepływ pracy do listy przepływów pracy i wyświetla informacje o wersji przepływu pracy w formularzu.  
  
    ```vb  
    'Add the workflow to the list and display the version information.  
    WorkflowStarting = True  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
    WorkflowVersion.Text = identity.ToString()  
    WorkflowStarting = False  
    ```  
  
    ```csharp  
    // Add the workflow to the list and display the version information.  
    WorkflowStarting = true;  
    InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
    WorkflowVersion.Text = identity.ToString();  
    WorkflowStarting = false;  
    ```  
  
5. Wywołaj `ConfigureWorkflowApplication` , aby skonfigurować magazyn wystąpień, rozszerzenia i obsługę cyklu życia przepływu pracy dla `WorkflowApplication` tego wystąpienia.  
  
    ```vb  
    'Configure the instance store, extensions, and   
    'workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
    ```  
  
    ```csharp  
    // Configure the instance store, extensions, and   
    // workflow lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp);  
    ```  
  
6. Na koniec Wywołaj metodę `Run`.  
  
    ```vb  
    'Start the workflow.  
    wfApp.Run()  
    ```  
  
    ```  
    // Start the workflow.  
    wfApp.Run();  
    ```  
  
     Poniższy przykład to zakończono `NewGame_Click` procedurę obsługi.  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
        'Start a new workflow.  
        Dim inputs As New Dictionary(Of String, Object)()  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
  
        Dim identity As WorkflowIdentity = Nothing  
        Select Case WorkflowType.SelectedItem.ToString()  
            Case "SequentialNumberGuessWorkflow"  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
            Case "StateMachineNumberGuessWorkflow"  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
            Case "FlowchartNumberGuessWorkflow"  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
        End Select  
  
        Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(identity)  
  
        Dim wfApp = New WorkflowApplication(wf, inputs, identity)  
  
        'Add the workflow to the list and display the version information.  
        WorkflowStarting = True  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id)  
        WorkflowVersion.Text = identity.ToString()  
        WorkflowStarting = False  
  
        'Configure the instance store, extensions, and   
        'workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Start the workflow.  
        wfApp.Run()  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
        var inputs = new Dictionary<string, object>();  
        inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
  
        WorkflowIdentity identity = null;  
        switch (WorkflowType.SelectedItem.ToString())  
        {  
            case "SequentialNumberGuessWorkflow":  
                identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
                break;  
  
            case "StateMachineNumberGuessWorkflow":  
                identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
                break;  
  
            case "FlowchartNumberGuessWorkflow":  
                identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
                break;  
        };  
  
        Activity wf = WorkflowVersionMap.GetWorkflowDefinition(identity);  
  
        WorkflowApplication wfApp = new WorkflowApplication(wf, inputs, identity);  
  
        // Add the workflow to the list and display the version information.  
        WorkflowStarting = true;  
        InstanceId.SelectedIndex = InstanceId.Items.Add(wfApp.Id);  
        WorkflowVersion.Text = identity.ToString();  
        WorkflowStarting = false;  
  
        // Configure the instance store, extensions, and   
        // workflow lifecycle handlers.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Start the workflow.  
        wfApp.Run();  
    }  
    ```  
  
### <a name="BKMK_ResumeWorkflow"></a>Aby wznowić przepływ pracy  
  
1. Dodaj program obsługi dla `EnterGuess`. `Click` Aby dodać procedurę obsługi, przełącz się do **widoku projektu** dla formularza i kliknij `EnterGuess`dwukrotnie. Za każdym razem, gdy użytkownik kliknie ten przycisk, przepływ pracy zostaje wznowiony.  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2. Dodaj następujący kod, aby upewnić się, że przepływ pracy został wybrany na liście przepływów pracy i czy jego wartość jest prawidłowa.  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim userGuess As Integer  
    If Not Int32.TryParse(Guess.Text, userGuess) Then  
        MessageBox.Show("Please enter an integer.")  
        Guess.SelectAll()  
        Guess.Focus()  
        Return  
    End If  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    int guess;  
    if (!Int32.TryParse(Guess.Text, out guess))  
    {  
        MessageBox.Show("Please enter an integer.");  
        Guess.SelectAll();  
        Guess.Focus();  
        return;  
    }  
    ```  
  
3. Następnie Pobierz `WorkflowApplicationInstance` wystąpienie utrwalonego przepływu pracy. `WorkflowApplicationInstance` Reprezentuje wystąpienie utrwalonego przepływu pracy, które nie zostało jeszcze skojarzone z definicją przepływu pracy. `DefinitionIdentity` Z`WorkflowApplicationInstance`zawierawystąpieniautrwalonegoprzepływupracy. `WorkflowIdentity` W tym samouczku `WorkflowVersionMap` Klasa narzędzi służy do `WorkflowIdentity` mapowania do odpowiedniej definicji przepływu pracy. Po pobraniu `WorkflowApplication` definicji przepływu pracy jest ona tworzona przy użyciu prawidłowej definicji przepływu pracy.  
  
    ```vb  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = _  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
    ```  
  
    ```csharp  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf =  
        WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
    ```  
  
4. Po utworzeniu należy skonfigurować magazyn wystąpień, programy obsługi cyklu życia przepływu pracy i rozszerzenia przez wywołanie `ConfigureWorkflowApplication`. `WorkflowApplication` Te kroki należy wykonać za każdym razem, gdy `WorkflowApplication` tworzony jest nowy, i muszą one zostać wykonane przed załadowaniem wystąpienia przepływu pracy `WorkflowApplication`do. Po załadowaniu przepływu pracy zostanie on wznowiony z przypuszczeniem użytkownika.  
  
    ```vb  
    'Configure the extensions and lifecycle handlers.  
    'Do this before the instance is loaded. Once the instance is  
    'loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", userGuess)  
    ```  
  
    ```csharp  
    // Configure the extensions and lifecycle handlers.  
    // Do this before the instance is loaded. Once the instance is  
    // loaded it is too late to add extensions.  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Resume the workflow.  
    wfApp.ResumeBookmark("EnterGuess", guess);  
    ```  
  
5. Na koniec wyczyść pole tekstowe odgadnięcie i Przygotuj formularz do zaakceptowania innego argumentu.  
  
    ```vb  
    'Clear the Guess textbox.  
    Guess.Clear()  
    Guess.Focus()  
    ```  
  
    ```csharp  
    // Clear the Guess textbox.  
    Guess.Clear();  
    Guess.Focus();  
    ```  
  
     Poniższy przykład to zakończono `EnterGuess_Click` procedurę obsługi.  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
        If WorkflowInstanceId = Guid.Empty Then  
            MessageBox.Show("Please select a workflow.")  
            Return  
        End If  
  
        Dim userGuess As Integer  
        If Not Int32.TryParse(Guess.Text, userGuess) Then  
            MessageBox.Show("Please enter an integer.")  
            Guess.SelectAll()  
            Guess.Focus()  
            Return  
        End If  
  
        Dim instance As WorkflowApplicationInstance = _  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
        'Use the persisted WorkflowIdentity to retrieve the correct workflow  
        'definition from the dictionary.  
        Dim wf As Activity = _  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
        'Associate the WorkflowApplication with the correct definition  
        Dim wfApp As WorkflowApplication = _  
            New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
        'Configure the extensions and lifecycle handlers.  
        'Do this before the instance is loaded. Once the instance is  
        'loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp)  
  
        'Load the workflow.  
        wfApp.Load(instance)  
  
        'Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", userGuess)  
  
        'Clear the Guess textbox.  
        Guess.Clear()  
        Guess.Focus()  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
        if (WorkflowInstanceId == Guid.Empty)  
        {  
            MessageBox.Show("Please select a workflow.");  
            return;  
        }  
  
        int guess;  
        if (!Int32.TryParse(Guess.Text, out guess))  
        {  
            MessageBox.Show("Please enter an integer.");  
            Guess.SelectAll();  
            Guess.Focus();  
            return;  
        }  
  
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
        // Use the persisted WorkflowIdentity to retrieve the correct workflow  
        // definition from the dictionary.  
        Activity wf =  
            WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
        // Associate the WorkflowApplication with the correct definition  
        WorkflowApplication wfApp =  
            new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
        // Configure the extensions and lifecycle handlers.  
        // Do this before the instance is loaded. Once the instance is  
        // loaded it is too late to add extensions.  
        ConfigureWorkflowApplication(wfApp);  
  
        // Load the workflow.  
        wfApp.Load(instance);  
  
        // Resume the workflow.  
        wfApp.ResumeBookmark("EnterGuess", guess);  
  
        // Clear the Guess textbox.  
        Guess.Clear();  
        Guess.Focus();  
    }  
    ```  
  
### <a name="BKMK_TerminateWorkflow"></a>Aby zakończyć przepływ pracy  
  
1. Dodaj program obsługi dla `QuitGame`. `Click` Aby dodać procedurę obsługi, przełącz się do **widoku projektu** dla formularza i kliknij `QuitGame`dwukrotnie. Za każdym razem, gdy użytkownik kliknie ten przycisk, aktualnie wybrany przepływ pracy zostanie zakończony.  
  
    ```vb  
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void QuitGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2. Dodaj następujący kod do `QuitGame_Click` procedury obsługi. Ten kod najpierw sprawdza, czy przepływ pracy został wybrany na liście przepływów pracy. Następnie ładuje wystąpienie utrwalone do `WorkflowApplicationInstance`, `DefinitionIdentity` używa do określenia prawidłowej definicji przepływu pracy `WorkflowApplication`, a następnie inicjuje. Kolejne rozszerzenia i programy obsługi cyklu życia przepływu pracy są skonfigurowane z wywołaniem `ConfigureWorkflowApplication`do. Po skonfigurowaniu jest on ładowany, a następnie `Terminate` wywoływany. `WorkflowApplication`  
  
    ```vb  
    If WorkflowInstanceId = Guid.Empty Then  
        MessageBox.Show("Please select a workflow.")  
        Return  
    End If  
  
    Dim instance As WorkflowApplicationInstance = _  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
    'Use the persisted WorkflowIdentity to retrieve the correct workflow  
    'definition from the dictionary.  
    Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity)  
  
    'Associate the WorkflowApplication with the correct definition.  
    Dim wfApp As WorkflowApplication = _  
        New WorkflowApplication(wf, instance.DefinitionIdentity)  
  
    'Configure the extensions and lifecycle handlers.  
    ConfigureWorkflowApplication(wfApp)  
  
    'Load the workflow.  
    wfApp.Load(instance)  
  
    'Terminate the workflow.  
    wfApp.Terminate("User resigns.")  
    ```  
  
    ```csharp  
    if (WorkflowInstanceId == Guid.Empty)  
    {  
        MessageBox.Show("Please select a workflow.");  
        return;  
    }  
  
    WorkflowApplicationInstance instance =  
        WorkflowApplication.GetInstance(WorkflowInstanceId, store);  
  
    // Use the persisted WorkflowIdentity to retrieve the correct workflow  
    // definition from the dictionary.  
    Activity wf = WorkflowVersionMap.GetWorkflowDefinition(instance.DefinitionIdentity);  
  
    // Associate the WorkflowApplication with the correct definition  
    WorkflowApplication wfApp =  
        new WorkflowApplication(wf, instance.DefinitionIdentity);  
  
    // Configure the extensions and lifecycle handlers  
    ConfigureWorkflowApplication(wfApp);  
  
    // Load the workflow.  
    wfApp.Load(instance);  
  
    // Terminate the workflow.  
    wfApp.Terminate("User resigns.");  
    ```  
  
### <a name="BKMK_BuildAndRun"></a>Aby skompilować i uruchomić aplikację  
  
1. Kliknij dwukrotnie pozycję **program.cs** (lub **Module1. vb**) w **Eksplorator rozwiązań** , aby wyświetlić kod.  
  
2. Dodaj następującą `using` instrukcję (lub `Imports`) w górnej części pliku z innymi `using` instrukcjami (lub `Imports`).  
  
    ```vb  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3. Usuń lub Skomentuj istniejący kod hostingu przepływu pracy z [: Uruchom przepływ pracy](how-to-run-a-workflow.md)i zastąp go następującym kodem.  
  
    ```vb  
    Sub Main()  
        Application.EnableVisualStyles()  
        Application.Run(New WorkflowHostForm())  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        Application.EnableVisualStyles();  
        Application.Run(new WorkflowHostForm());  
    }  
    ```  
  
4. Kliknij prawym przyciskiem myszy pozycję **NumberGuessWorkflowHost** w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**. Na karcie **aplikacja** Określ **aplikację systemu Windows** dla **typu danych wyjściowych**. Ten krok jest opcjonalny, ale jeśli nie jest zastosowana, okno konsoli jest wyświetlane oprócz formularza.  
  
5. Naciśnij klawisze CTRL + SHIFT + B, aby skompilować aplikację.  
  
6. Upewnij się, że **NumberGuessWorkflowHost** jest ustawiony jako aplikacja startowa, a następnie naciśnij klawisze CTRL + F5, aby uruchomić aplikację.  
  
7. Wybierz zakres dla gry do odgadnięcia i typ przepływu pracy do uruchomienia, a następnie kliknij pozycję **Nowa gra**. Wprowadź wartość w polu **zgadywanie** i kliknij pozycję **Przejdź** , aby przesłać przypuszczenie. Należy zauważyć, że dane wyjściowe `WriteLine` działań są wyświetlane w formularzu.  
  
8. Rozpocznij pracę z kilkoma przepływami pracy przy użyciu różnych typów i zakresów liczbowych, wprowadź liczbę prób i przełączaj się między przepływami pracy, wybierając z listy **Identyfikator wystąpienia przepływu pracy** .  
  
     Należy pamiętać, że po przełączeniu do nowego przepływu pracy poprzednie wartości i postęp przepływu pracy nie są wyświetlane w oknie stanu. Przyczyna stanu jest niedostępna, ponieważ nie jest ona przechwycona i zapisana w dowolnym miejscu. W następnym kroku samouczka [: Utwórz niestandardowego uczestnika](how-to-create-a-custom-tracking-participant.md)śledzenia, tworząc niestandardowego uczestnika śledzenia, który zapisuje te informacje.
