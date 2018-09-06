---
title: 'Porady: tworzenie i uruchamianie długotrwałego uruchamiania przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
ms.openlocfilehash: 2c3368bc73d54f2848cad3c1086b1d9733205d2b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747788"
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a>Porady: tworzenie i uruchamianie długotrwałego uruchamiania przepływu pracy
Jedną z centralnej funkcji Windows Workflow Foundation (WF) jest możliwość w środowisku uruchomieniowym zostaną zachowane, a następnie zwolnij bezczynności przepływy pracy z bazą danych. Kroki opisane w [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) przedstawiono podstawowe informacje dotyczące przepływu pracy hostingu, za pomocą aplikacji konsoli. Przykłady zostały przedstawione począwszy od przepływów pracy, przepływ pracy cyklu życia obsługi i wznawianie zakładek. W celu przedstawienia skutecznie trwałość przepływu pracy, wymagane jest bardziej złożone hosta przepływu pracy, która obsługuje uruchamianie i wznawianie wielu wystąpień przepływu pracy. Ten krok, w tym samouczku przedstawiono sposób tworzenia hosta formularzy Windows, aplikacji, która obsługuje uruchamianie i wznawianie wielu wystąpień przepływu pracy, trwałość przepływu pracy i stanowi podstawę dla zaawansowanych funkcji, takich jak śledzenie i przechowywania wersji, które są przedstawione w kolejnych krokach samouczka.  
  
> [!NOTE]
>  Ten samouczek kroku oraz kolejnych kroków należy używać wszystkich trzech typów przepływu pracy z [porady: Tworzenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md). Jeśli nie została ukończona wszystkich trzech typów możesz pobrać pełną wersję z procedury [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
> [!NOTE]
>  Aby pobrać wersję inną ukończone lub wyświetlić Przewodnik wideo tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
-   [Aby utworzyć bazę danych stanów trwałych](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)  
  
-   [Można dodać odwołania do zestawów DurableInstancing](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)  
  
-   [Aby utworzyć formularz hosta przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)  
  
-   [Aby dodać właściwości i metody pomocnicze formularza](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)  
  
-   [Aby skonfigurować Magazyn wystąpień przepływu pracy cyklu życia obsługi i rozszerzenia](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)  
  
-   [Aby włączyć uruchamianie i wznawianie wielu typów przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)  
  
-   [Aby uruchomić nowy przepływ pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)  
  
-   [Aby wznowić przepływ pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)  
  
-   [Aby zakończyć przepływ pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)  
  
-   [Aby skompilować i uruchomić aplikację](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CreatePersistenceDatabase"></a> Aby utworzyć bazę danych stanów trwałych  
  
1.  Otwórz program SQL Server Management Studio i połącz się z serwera lokalnego, na przykład **. \SQLEXPRESS**. Kliknij prawym przyciskiem myszy **baz danych** węzła na serwerze lokalnym, a następnie wybierz **nową bazę danych**. Nadaj nazwę nowej bazy danych **WF45GettingStartedTutorial**, Zaakceptuj pozostałe wartości i wybierz **OK**.  
  
    > [!NOTE]
    >  Upewnij się, że masz **Create Database** uprawnień na serwerze lokalnym przed utworzeniem bazy danych.  
  
2.  Wybierz **Otwórz**, **pliku** z **pliku** menu. Przejdź do następującego folderu: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`  
  
     Wybierz następujące dwa pliki, a następnie kliknij przycisk **Otwórz**.  
  
    -   SqlWorkflowInstanceStoreLogic.sql  
  
    -   SqlWorkflowInstanceStoreSchema.sql  
  
3.  Wybierz **SqlWorkflowInstanceStoreSchema.sql** z **okna** menu. Upewnij się, że **WF45GettingStartedTutorial** wybrano **baz danych dostępności** listy rozwijanej i wybierz polecenie **Execute** z **zapytania**menu.  
  
4.  Wybierz **SqlWorkflowInstanceStoreLogic.sql** z **okna** menu. Upewnij się, że **WF45GettingStartedTutorial** wybrano **baz danych dostępności** listy rozwijanej i wybierz polecenie **Execute** z **zapytania**menu.  
  
    > [!WARNING]
    >  Należy wykonać dwa poprzednie kroki w odpowiedniej kolejności. Jeśli zapytania są wykonywane poza kolejnością, wystąpią błędy, a baza danych stanów trwałych nie jest poprawnie skonfigurowany.  
  
###  <a name="BKMK_AddReference"></a> Można dodać odwołania do zestawów DurableInstancing  
  
1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie**.  
  
2.  Wybierz **zestawy** z **Dodaj odwołanie** listy, a typ `DurableInstancing` do **wyszukiwania zestawów** pole. Filtry zestawów i ułatwia wybierz żądane odwołania.  
  
3.  Zaznacz pole wyboru obok pozycji **System.Activities.DurableInstancing** i **System.Runtime.DurableInstancing** z **wyniki wyszukiwania** listy, a następnie kliknij przycisk **OK**.  
  
###  <a name="BKMK_CreateForm"></a> Aby utworzyć formularz hosta przepływu pracy  
  
> [!NOTE]
>  W tej procedurze opisano sposób dodawania i konfigurowania formularza ręcznie. Jeśli to konieczne, można pobrać plików rozwiązania dla tego samouczka i Dodaj wypełniony formularz do projektu. Aby pobrać pliki samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](https://go.microsoft.com/fwlink/?LinkID=248976). Po pobraniu plików, kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** i wybierz polecenie **Dodaj odwołanie**. Dodaj odwołanie do **System.Windows.Forms** i **System.Drawing**. Te odwołania są dodawane automatycznie po dodaniu nowego formularza z **Dodaj**, **nowy element** menu, ale musisz ręcznie dodać podczas importowania formularza. Po dodaniu odwołania, kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **istniejący element**. Przejdź do `Form` folderu w plikach projektu, wybierz opcję **WorkflowHostForm.cs** (lub **WorkflowHostForm.vb**) i kliknij przycisk **Dodaj**. Jeśli decydujesz się zaimportować formularza, a następnie w dół do następnej sekcji, możesz pominąć [można dodać właściwości i metody pomocnicze formularza](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).  
  
1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **nowy element**.  
  
2.  W **zainstalowane** szablonów wybierz **formularza Windows**, typ `WorkflowHostForm` w **nazwa** polu, a następnie kliknij przycisk **Dodaj**.  
  
3.  W formularzu, należy skonfigurować następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |FormBorderStyle|FixedSingle|  
    |MaximizeBox|False|  
    |Rozmiar|400, 420|  
  
4.  Dodaj następujące formanty do formularza w kolejności określonej i skonfigurować właściwości, zgodnie z instrukcją.  
  
    |Formant|Właściwość: wartość|  
    |-------------|---------------------|  
    |**Przycisk**|Nazwa: NewGame<br /><br /> Lokalizacja: 13, 13<br /><br /> Rozmiar: 75, 23<br /><br /> Tekst: Gra nowy|  
    |**Etykieta**|Lokalizacja: 94, 18<br /><br /> Tekst: Odgadnięcia liczba z przedziału od 1 do|  
    |**ComboBox**|Nazwa: NumberRange<br /><br /> Parametr DropDownStyle: kontrolki DropDownList<br /><br /> Elementy: 10, 100, 1000<br /><br /> Lokalizacja: 228, 12<br /><br /> Rozmiar: 143, 21|  
    |**Etykieta**|Lokalizacja: 13, 43<br /><br /> Tekst: Typ przepływu pracy|  
    |**ComboBox**|Nazwa: WorkflowType<br /><br /> Parametr DropDownStyle: kontrolki DropDownList<br /><br /> Elementy: SequentialNumberGuessWorkflow StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow,<br /><br /> Lokalizacja: 94, 40<br /><br /> Rozmiar: 277, 21|  
    |**Etykieta**|Nazwa: WorkflowVersion<br /><br /> Lokalizacja: 13, 362<br /><br /> Tekst: Wersja przepływu pracy|  
    |**GroupBox**|Lokalizacja: 13, 67<br /><br /> Rozmiar: 358, 287<br /><br /> Tekst: gra|  
  
    > [!NOTE]
    >  Dodając następujące elementy sterujące, umieść je w GroupBox.  
  
    |Formant|Właściwość: wartość|  
    |-------------|---------------------|  
    |**Etykieta**|Lokalizacja: 7, 20<br /><br /> Tekst: Identyfikator wystąpienia przepływu pracy|  
    |**ComboBox**|Nazwa: InstanceId<br /><br /> Parametr DropDownStyle: kontrolki DropDownList<br /><br /> Lokalizacja: 121, 17<br /><br /> Rozmiar: 227, 21|  
    |**Etykieta**|Lokalizacja: 7, 47<br /><br /> Tekst: odgadnięcia|  
    |**TextBox**|Nazwa: odgadnięcia<br /><br /> Lokalizacja: 50, 44<br /><br /> Rozmiar: 65, 20|  
    |**Przycisk**|Nazwa: EnterGuess<br /><br /> Lokalizacja: 121, 42<br /><br /> Rozmiar: 75, 23<br /><br /> Tekst: Wprowadź odgadnięcia|  
    |**Przycisk**|Nazwa: QuitGame<br /><br /> Lokalizacja: 274, 42<br /><br /> Rozmiar: 75, 23<br /><br /> Tekst: Zamknij|  
    |**TextBox**|Nazwa: element WorkflowStatus<br /><br /> Lokalizacja: 10, 73<br /><br /> Wiele linii: True<br /><br /> Tylko do odczytu: True<br /><br /> Paski przewijania: pionowa<br /><br /> Rozmiar: 338, 208|  
  
5.  Ustaw **AcceptButton** właściwości formularza w celu **EnterGuess**.  
  
 Poniższy przykład ilustruje wypełniony formularz.  
  
 ![WF45 Wprowadzenie formularz hosta samouczek przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")  
  
###  <a name="BKMK_AddHelperMethods"></a> Aby dodać właściwości i metody pomocnicze formularza  
 Kroki opisane w tej sekcji Dodaj właściwości i metody pomocnicze do skonfigurowanego interfejsu użytkownika formularza, do obsługi uruchomiona i wznawianie numer odgadnięcia przepływy pracy klasy formularza.  
  
1.  Kliknij prawym przyciskiem myszy **WorkflowHostForm** w **Eksploratora rozwiązań** i wybierz polecenie **Wyświetl kod**.  
  
2.  Dodaj następujący kod `using` (lub `Imports`) instrukcji w górnej części pliku razem z innymi `using` (lub `Imports`) instrukcji.  
  
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
  
3.  Dodaj następujące deklaracje elementu członkowskiego do **WorkflowHostForm** klasy.  
  
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
    >  Jeśli ciąg połączenia jest inna, zaktualizuj `connectionString` do odwoływania się do bazy danych.  
  
4.  Dodaj `WorkflowInstanceId` właściwość `WorkflowFormHost` klasy.  
  
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
  
     `InstanceId` Polu kombi zawiera listę identyfikatorów wystąpień utrwalonych przepływów pracy oraz `WorkflowInstanceId` właściwość zwraca aktualnie wybranego przepływu pracy.  
  
5.  Dodawanie obsługi dla formularza `Load` zdarzeń. Aby dodać program obsługi, przełącz się do **widoku projektu** formularza, kliknij przycisk **zdarzenia** ikonę u góry **właściwości** okna, a następnie kliknij dwukrotnie plik **obciążenia**.  
  
    ```vb  
    Private Sub WorkflowHostForm_Load(sender As Object, e As EventArgs) Handles Me.Load  
  
    End Sub  
    ```  
  
    ```csharp  
    private void WorkflowHostForm_Load(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
6.  Dodaj następujący kod do `WorkflowHostForm_Load`.  
  
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
  
     Podczas ładowania formularza, `SqlWorkflowInstanceStore` jest skonfigurowany, pola kombi typu zakres i przepływu pracy są ustawione wartości domyślne, a wystąpienia utrwalonych przepływu pracy są dodawane do `InstanceId` pola kombi.  
  
7.  Dodaj `SelectedIndexChanged` Obsługa `InstanceId`. Aby dodać program obsługi, przełącz się do **widoku projektu** w formularzu Wybierz `InstanceId` pola kombi, kliknij przycisk **zdarzenia** ikony w górnej części **właściwości** okna, i Kliknij dwukrotnie **selectedindexchanged**.  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
8.  Dodaj następujący kod do `InstanceId_SelectedIndexChanged`. Zawsze, gdy użytkownik wybierze przepływu pracy za pomocą pola kombi ten program obsługi aktualizacji w oknie stanu.  
  
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
  
9. Dodaj następujący kod `ListPersistedWorkflows` metodę do klasy formularza.  
  
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
  
     `ListPersistedWorkflows` zapytania w sklepie wystąpienia dla wystąpienia przepływu pracy utrwalonych i dodaje identyfikatorów wystąpień do `cboInstanceId` pola kombi.  
  
10. Dodaj następujący kod `UpdateStatus` metody i delegata odpowiedniej klasy formularza. Ta metoda aktualizuje okno stanu w formularzu ze stanem obecnie uruchomiony przepływ pracy.  
  
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
  
11. Dodaj następujący kod `GameOver` metody i delegata odpowiedniej klasy formularza. Po zakończeniu przepływu pracy, ta metoda aktualizuje formularza interfejsu użytkownika przez usunięcie identyfikatora wystąpienia przepływu pracy, ukończonej z **InstanceId** pola kombi.  
  
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
  
###  <a name="BKMK_ConfigureWorkflowApplication"></a> Aby skonfigurować Magazyn wystąpień przepływu pracy cyklu życia obsługi i rozszerzenia  
  
1.  Dodaj `ConfigureWorkflowApplication` metodę do klasy formularza.  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
  
    End Sub  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {      
    }  
    ```  
  
     Ta metoda umożliwia skonfigurowanie `WorkflowApplication`, dodaje rozszerzenia żądaną i dodaje programy obsługi zdarzeń cyklu życia przepływu pracy.  
  
2.  W `ConfigureWorkflowApplication`, określ `SqlWorkflowInstanceStore` dla `WorkflowApplication`.  
  
    ```vb  
    'Configure the persistence store.  
    wfApp.InstanceStore = store  
    ```  
  
    ```csharp  
    // Configure the persistence store.  
    wfApp.InstanceStore = store;  
    ```  
  
3.  Następnie należy utworzyć `StringWriter` wystąpienia i dodać go do `Extensions` zbiór `WorkflowApplication`. Gdy `StringWriter` jest dodawany do rozszerzeń przechwytuje wszystkie `WriteLine` wyjście działania. Gdy przepływ pracy staje się nieaktywna, `WriteLine` dane wyjściowe można wyodrębnić z `StringWriter` i wyświetlane w formularzu.  
  
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
  
4.  Dodaj następujący program obsługi dla `Completed` zdarzeń. Po pomyślnym ukończeniu przepływu pracy liczba włącza podjęte w celu odgadnięcia, że liczba zostanie wyświetlone okno stanu. Informacje o wyjątku, który spowodował przerwanie jest wyświetlany, jeśli kończy się przepływu pracy. Na koniec obsługi `GameOver` wywoływana jest metoda, która usuwa ukończony przepływ pracy z listy przepływów pracy.  
  
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
  
5.  Dodaj następujący kod `Aborted` i `OnUnhandledException` programów obsługi. `GameOver` Metoda nie jest wywoływana z `Aborted` obsługi gdy wystąpienie przepływu pracy zostało przerwane, nie kończy, dlatego można wznowić wystąpienia w późniejszym czasie.  
  
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
  
6.  Dodaj następujący kod `PersistableIdle` programu obsługi. Pobiera ten program obsługi `StringWriter` rozszerzenia, który został dodany, wyodrębnia dane wyjściowe z `WriteLine` działań i wyświetla go w oknie stanu.  
  
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
  
     <xref:System.Activities.PersistableIdleAction> Wyliczenie ma trzy wartości: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, i <xref:System.Activities.PersistableIdleAction.Unload>. <xref:System.Activities.PersistableIdleAction.Persist> powoduje, że przepływ pracy, aby utrwalić, ale go nie powoduje przepływ pracy, aby zwolnić. <xref:System.Activities.PersistableIdleAction.Unload> powoduje, że przepływ pracy, aby utrwalić i zostać zwolniony.  
  
     Poniższy przykład jest gotowy `ConfigureWorkflowApplication` metody.  
  
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
  
###  <a name="BKMK_WorkflowVersionMap"></a> Aby włączyć uruchamianie i wznawianie wielu typów przepływu pracy  
 Aby wznowić działanie wystąpienia przepływu pracy, host musi podać definicję przepływu pracy. W ramach tego samouczka istnieją trzy typy przepływu pracy, a kolejne kroki samouczka wprowadzenie wielu wersji tego typu. `WorkflowIdentity` umożliwia aplikacji hosta skojarzyć informacje identyfikacyjne z istniejącym wystąpieniem przepływu pracy. Kroki opisane w tej sekcji pokazują, jak utworzyć klasę użytkową uzyskanymi mapowania tożsamości przepływu pracy z istniejącym wystąpieniem przepływu pracy do odpowiedniej definicji przepływu pracy. Aby uzyskać więcej informacji na temat `WorkflowIdentity` i przechowywania wersji, zobacz [przy użyciu obiektu WorkflowIdentity i wersjonowanie](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).  
  
1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **klasy**. Typ `WorkflowVersionMap` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.  
  
2.  Dodaj następujący kod `using` lub `Imports` instrukcji w górnej części pliku razem z innymi `using` lub `Imports` instrukcji.  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Activities  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Activities;  
    ```  
  
3.  Zastąp `WorkflowVersionMap` deklaracji z następującą deklarację klasy.  
  
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
  
     `WorkflowVersionMap` zawiera trzy tożsamości przepływu pracy, które mapują do trzech definicji przepływu pracy z tego samouczka i jest używana w poniższych sekcjach, gdy rozpoczyna się przepływy pracy i wznowić.  
  
###  <a name="BKMK_StartWorkflow"></a> Aby uruchomić nowy przepływ pracy  
  
1.  Dodaj `Click` Obsługa `NewGame`. Aby dodać program obsługi, przełącz się do **widoku projektu** formularza, a następnie kliknij dwukrotnie plik `NewGame`. A `NewGame_Click` dodaniu programu obsługi i widoku przełącza do widoku kodu formularza. Gdy użytkownik kliknie ten przycisk Nowy przepływ pracy został uruchomiony.  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Dodaj następujący kod programem obsługi kliknięcia. Ten kod tworzy słownik argumenty wejściowe dla przepływu pracy, kluczach nazwę argumentu. Tego słownika ma jeden wpis, zawierający zakres generowany losowo numer pobierane pole kombi zakresu.  
  
    ```vb  
    Dim inputs As New Dictionary(Of String, Object)()  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
    ```  
  
    ```csharp  
    var inputs = new Dictionary<string, object>();  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
    ```  
  
3.  Następnie dodaj następujący kod, który uruchamia przepływ pracy. `WorkflowIdentity` i definicji przepływu pracy, odpowiadający typowi wybrane przepływu pracy są pobierane przy użyciu `WorkflowVersionMap` Klasa pomocy. Następnie, nowy `WorkflowApplication` przy użyciu definicji przepływu pracy, tworzone jest wystąpienie `WorkflowIdentity`i słownika argumentów wejściowych.  
  
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
  
4.  Następnie dodaj następujący kod, który dodaje przepływu pracy do listy przepływów pracy i wyświetla informacje o wersji przepływu pracy na formularzu.  
  
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
  
5.  Wywołaj `ConfigureWorkflowApplication` do skonfigurowania obsługi cyklu życia magazynu, rozszerzenia i przepływ pracy wystąpienie tego `WorkflowApplication` wystąpienia.  
  
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
  
6.  Na koniec Wywołaj `Run`.  
  
    ```vb  
    'Start the workflow.  
    wfApp.Run()  
    ```  
  
    ```  
    // Start the workflow.  
    wfApp.Run();  
    ```  
  
     Poniższy przykład jest gotowy `NewGame_Click` programu obsługi.  
  
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
  
###  <a name="BKMK_ResumeWorkflow"></a> Aby wznowić przepływ pracy  
  
1.  Dodaj `Click` Obsługa `EnterGuess`. Aby dodać program obsługi, przełącz się do **widoku projektu** formularza, a następnie kliknij dwukrotnie plik `EnterGuess`. Gdy użytkownik kliknie ten przycisk, przepływ pracy zostanie wznowione.  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Dodaj następujący kod, aby upewnić się, że przepływ pracy jest zaznaczony na liście przepływów pracy i że odgadnięcia użytkownika jest prawidłowy.  
  
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
  
3.  Następnie należy pobrać `WorkflowApplicationInstance` z istniejącym wystąpieniem przepływu pracy. A `WorkflowApplicationInstance` reprezentuje utrwalonego wystąpienia przepływu pracy, który nie został jeszcze skojarzony z definicją przepływu pracy. `DefinitionIdentity` z `WorkflowApplicationInstance` zawiera `WorkflowIdentity` z istniejącym wystąpieniem przepływu pracy. W tym samouczku `WorkflowVersionMap` klasy narzędzie służy do mapowania `WorkflowIdentity` do definicji poprawne przepływu pracy. Po pobraniu definicji przepływu pracy `WorkflowApplication` jest tworzony przy użyciu definicji przepływu pracy poprawne.  
  
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
  
4.  Gdy `WorkflowApplication` jest utworzony, skonfiguruj magazyn wystąpień przepływu pracy cyklu życia obsługi i rozszerzeń, wywołując `ConfigureWorkflowApplication`. Te kroki należy wykonać każdym nowej `WorkflowApplication` zostanie utworzony, muszą być wykonywane przed wystąpieniem przepływu pracy jest ładowany do `WorkflowApplication`. Po załadowaniu przepływ pracy zostanie wznowione odgadnięcia użytkownika.  
  
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
  
5.  Na koniec wyczyść pole tekstowe odgadnięcia i przygotować formularz, aby akceptować inny wynik.  
  
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
  
     Poniższy przykład jest gotowy `EnterGuess_Click` programu obsługi.  
  
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
  
###  <a name="BKMK_TerminateWorkflow"></a> Aby zakończyć przepływ pracy  
  
1.  Dodaj `Click` Obsługa `QuitGame`. Aby dodać program obsługi, przełącz się do **widoku projektu** formularza, a następnie kliknij dwukrotnie plik `QuitGame`. Gdy użytkownik kliknie ten przycisk aktualnie wybranego przepływu pracy zostało przerwane.  
  
    ```vb  
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void QuitGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Dodaj następujący kod do `QuitGame_Click` programu obsługi. Ten kod najpierw sprawdza, upewnij się, że przepływ pracy jest zaznaczony na liście przepływów pracy. A następnie ładuje utrwalonego wystąpienia do `WorkflowApplicationInstance`, używa `DefinitionIdentity` do określenia definicji przepływu pracy poprawne, a następnie inicjuje `WorkflowApplication`. Następnie rozszerzenia i obsługi cyklu życia przepływu pracy są skonfigurowane przy użyciu wywołania do `ConfigureWorkflowApplication`. Raz `WorkflowApplication` jest skonfigurowany, jej załadowaniu, a następnie `Terminate` jest wywoływana.  
  
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
  
###  <a name="BKMK_BuildAndRun"></a> Aby skompilować i uruchomić aplikację  
  
1.  Kliknij dwukrotnie **Program.cs** (lub **Module1.vb**) w **Eksploratora rozwiązań** Aby wyświetlić kod.  
  
2.  Dodaj następujący kod `using` (lub `Imports`) instrukcji w górnej części pliku razem z innymi `using` (lub `Imports`) instrukcji.  
  
    ```vb  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3.  Usunąć lub skomentować istniejącego przepływu pracy obsługującego kod z [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)i zastąp go następującym kodem.  
  
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
  
4.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **właściwości**. W **aplikacji** określ **aplikacji Windows** dla **typ danych wyjściowych**. Ten krok jest opcjonalny, ale jeśli go nie zostanie zastosowane oprócz formularzu zostanie wyświetlone okno konsoli.  
  
5.  Naciśnij klawisze Ctrl + Shift + B, aby skompilować aplikację.  
  
6.  Upewnij się, że **NumberGuessWorkflowHost** jest ustawiony jako aplikacja do uruchomienia, a następnie naciśnij klawisz Ctrl + F5, aby uruchomić aplikację.  
  
7.  Wybierz zakres do odgadnięcia gier i typ przepływu pracy, aby rozpocząć, a następnie kliknij przycisk **nowych gier**. Wprowadź odgadnięcia w **odgadnięcia** pole, a następnie kliknij przycisk **Przejdź** przesłać przypuszczenie. Należy pamiętać, że dane wyjściowe z `WriteLine` działania jest wyświetlany w formularzu.  
  
8.  Uruchom wiele przepływów pracy przy użyciu typów innego przepływu pracy i liczba zakresów, wprowadzić kilka prób i przełączać się między przepływami pracy, wybierając z **identyfikator wystąpienia przepływu pracy** listy.  
  
     Należy pamiętać, że przełączenie do nowego przepływu pracy liczbę poprzednich prób i postęp przepływu pracy nie są wyświetlane w oknie stanu. Powodów, dla którego stan nie jest dostępna jest, ponieważ nie jest przechwytywane i zapisane w dowolnym miejscu. W następnym kroku samouczka [porady: Tworzenie niestandardowego uczestnika śledzenia](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md), Utwórz niestandardowe śledzenia uczestnika, który zapisuje te informacje.
