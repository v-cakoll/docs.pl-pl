---
title: 'Porady: tworzenie i uruchamianie długi uruchamiania przepływu pracy'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c0043c89-2192-43c9-986d-3ecec4dd8c9c
caps.latest.revision: 40
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c7776c9155ef2c2c5c4ea804285cd67e995ef119
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-and-run-a-long-running-workflow"></a>Porady: tworzenie i uruchamianie długi uruchamiania przepływu pracy
Jedną z centralnej funkcji Windows Workflow Foundation (WF) jest możliwość środowiska uruchomieniowego utrwalić i zwolnić bezczynne przepływy pracy z bazą danych. Kroki opisane w [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md) przedstawiono podstawowe informacje dotyczące obsługi przepływu pracy za pomocą aplikacji konsoli. Przykłady zostały przedstawione początkowy przepływy pracy, programy obsługi cyklu życia przepływu pracy i wznawianie zakładki. W celu zaprezentowania skutecznie utrwalania przepływu pracy, konieczne jest bardziej złożonych hosta przepływu pracy obsługującego uruchamianie i wznawianie wielu wystąpień przepływu pracy. Ten krok samouczka przedstawia sposób tworzenia hosta formularzy systemu Windows, aplikacji, która obsługuje uruchamianie i wznawianie wielu wystąpień przepływu pracy, utrwalania przepływu pracy i stanowi podstawę do zaawansowanych funkcji, takich jak śledzenia i wersjonowania, które są zostało to pokazane w kolejnych krokach samouczka.  
  
> [!NOTE]
>  Ten samouczek kroku oraz kolejnych kroków należy używać wszystkich trzech typów przepływu pracy z [porady: tworzenie przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md). Jeśli nie zostało ukończone wszystkie trzy typy możesz pobrać ukończoną wersję kroki z [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
> [!NOTE]
>  Aby pobrać wersję zakończone lub wyświetlić Przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).  
  
## <a name="in-this-topic"></a>W tym temacie:  
  
-   [Aby utworzyć bazę danych trwałości](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreatePersistenceDatabase)  
  
-   [Można dodać odwołania do zestawów DurableInstancing](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddReference)  
  
-   [Aby utworzyć formularz hosta przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_CreateForm)  
  
-   [Aby dodać właściwości i metody pomocnicze formularza](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods)  
  
-   [Aby skonfigurować Magazyn wystąpienia przepływu pracy obsługi cyklu życia i rozszerzenia](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ConfigureWorkflowApplication)  
  
-   [Aby włączyć uruchamianie i wznawianie wielu typów przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_WorkflowVersionMap)  
  
-   [Aby uruchomić nowy przepływ pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_StartWorkflow)  
  
-   [Aby wznowić przepływ pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_ResumeWorkflow)  
  
-   [Zakończenie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_TerminateWorkflow)  
  
-   [Aby skompilować i uruchomić aplikację](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_BuildAndRun)  
  
###  <a name="BKMK_CreatePersistenceDatabase"></a> Aby utworzyć bazę danych trwałości  
  
1.  Otwórz program SQL Server Management Studio i połączyć się z serwerem lokalnym, na przykład **. \SQLEXPRESS**. Kliknij prawym przyciskiem myszy **baz danych** węzła na serwerze lokalnym, a następnie wybierz **nową bazę danych**. Nazwa nowej bazy danych **WF45GettingStartedTutorial**Zaakceptuj wszystkie inne wartości, a wybierz **OK**.  
  
    > [!NOTE]
    >  Upewnij się, że masz **Create Database** uprawnienia na serwerze lokalnym, przed utworzeniem bazy danych.  
  
2.  Wybierz **Otwórz**, **pliku** z **pliku** menu. Przejdź do folderu: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`  
  
     Wybierz następujące dwa pliki, a następnie kliknij przycisk **Otwórz**.  
  
    -   SqlWorkflowInstanceStoreLogic.sql  
  
    -   SqlWorkflowInstanceStoreSchema.sql  
  
3.  Wybierz **SqlWorkflowInstanceStoreSchema.sql** z **okna** menu. Upewnij się, że **WF45GettingStartedTutorial** wybrano **dostępnych baz danych** listy rozwijanej i wybierz polecenie **Execute** z **zapytania**menu.  
  
4.  Wybierz **SqlWorkflowInstanceStoreLogic.sql** z **okna** menu. Upewnij się, że **WF45GettingStartedTutorial** wybrano **dostępnych baz danych** listy rozwijanej i wybierz polecenie **Execute** z **zapytania**menu.  
  
    > [!WARNING]
    >  Należy wykonać dwa poprzednie kroki w odpowiedniej kolejności. Jeśli zapytania są wykonywane poza kolejnością, występują błędy, a trwałości bazy danych nie jest poprawnie skonfigurowany.  
  
###  <a name="BKMK_AddReference"></a> Można dodać odwołania do zestawów DurableInstancing  
  
1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie**.  
  
2.  Wybierz **zestawy** z **Dodaj odwołanie** listy i typ `DurableInstancing` do **wyszukiwania zestawów** pole. Filtry zestawy i ułatwia wybierz żądany odwołań.  
  
3.  Zaznacz pole wyboru obok **System.Activities.DurableInstancing** i **System.Runtime.DurableInstancing** z **wyniki wyszukiwania** listy, a następnie kliknij przycisk **OK**.  
  
###  <a name="BKMK_CreateForm"></a> Aby utworzyć formularz hosta przepływu pracy  
  
> [!NOTE]
>  W tej procedurze opisano sposób dodać i skonfigurować ręcznie formularza. W razie potrzeby można pobrać plików rozwiązania samouczka i Dodaj wypełnionego formularza do projektu. Aby pobrać pliki samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976). Po pobraniu plików, kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** i wybierz polecenie **Dodaj odwołanie**. Dodaj odwołanie do **System.Windows.Forms** i **System.Drawing**. Te odwołania są dodawane automatycznie po dodaniu nowego formularza z **Dodaj**, **nowy element** menu, ale należy je dodać ręcznie, podczas importowania formularza. Po dodaniu odwołań, kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **istniejący element**. Przejdź do `Form` folderu plików projektu, zaznacz opcję **WorkflowHostForm.cs** (lub **WorkflowHostForm.vb**) i kliknij przycisk **Dodaj**. Jeśli chcesz zaimportować formularz, a następnie można przejść do następnej sekcji [można dodać właściwości i metody pomocnicze formularza](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md#BKMK_AddHelperMethods).  
  
1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **nowy element**.  
  
2.  W **zainstalowana** szablonów wybierz **formularza systemu Windows**, typ `WorkflowHostForm` w **nazwa** i kliknij **Dodaj**.  
  
3.  W formularzu, należy skonfigurować następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |FormBorderStyle|FixedSingle|  
    |MaximizeBox|False|  
    |Rozmiar|400, 420|  
  
4.  Dodaj następujących formantów do formularza w kolejności określonej i skonfigurować właściwości zgodnie z instrukcją.  
  
    |Formant|Właściwość: wartość|  
    |-------------|---------------------|  
    |**Przycisk**|Nazwa: NewGame<br /><br /> Lokalizacja: 13, 13<br /><br /> Rozmiar: 75, 23<br /><br /> Tekst: Gry nowy|  
    |**Etykieta**|Lokalizacji: 94, 18<br /><br /> Tekst: Liczba z przedziału od 1 do odgadnięcia|  
    |**ComboBox**|Nazwa: NumberRange<br /><br /> Parametr DropDownStyle: Lista DropDownList<br /><br /> Elementy: 10, 100, 1000<br /><br /> Lokalizacja: 228, 12<br /><br /> Rozmiar: 143, 21|  
    |**Etykieta**|Lokalizacji: 13, 43<br /><br /> Tekst: Typ przepływu pracy|  
    |**ComboBox**|Nazwa: WorkflowType<br /><br /> Parametr DropDownStyle: Lista DropDownList<br /><br /> Elementy: SequentialNumberGuessWorkflow StateMachineNumberGuessWorkflow, FlowchartNumberGuessWorkflow,<br /><br /> Lokalizacji: 94, 40<br /><br /> Rozmiar: 277, 21|  
    |**Etykieta**|Nazwa: WorkflowVersion<br /><br /> Lokalizacji: 13, 362<br /><br /> Tekst: Wersja przepływu pracy|  
    |**GroupBox**|Lokalizacji: 13, 67<br /><br /> Rozmiar: 358, 287<br /><br /> Tekst: gry|  
  
    > [!NOTE]
    >  Podczas dodawania z poniższych formantów, umieść je w GroupBox.  
  
    |Formant|Właściwość: wartość|  
    |-------------|---------------------|  
    |**Etykieta**|Lokalizacji: 7, 20<br /><br /> Tekst: Identyfikator wystąpienia przepływu pracy|  
    |**ComboBox**|Nazwa: identyfikator wystąpienia<br /><br /> Parametr DropDownStyle: Lista DropDownList<br /><br /> Lokalizacji: 121, 17<br /><br /> Rozmiar: 227, 21|  
    |**Etykieta**|Lokalizacji: 7, 47<br /><br /> Tekst: odgadnięcia|  
    |**TextBox**|Nazwa: odgadnięcia<br /><br /> Lokalizacji: 50, 44<br /><br /> Rozmiar: 65, 20|  
    |**Przycisk**|Nazwa: EnterGuess<br /><br /> Lokalizacji: 121, 42<br /><br /> Rozmiar: 75, 23<br /><br /> Tekst: Wynik wprowadź|  
    |**Przycisk**|Nazwa: QuitGame<br /><br /> Lokalizacji: 274, 42<br /><br /> Rozmiar: 75, 23<br /><br /> Tekst: Zamknij|  
    |**TextBox**|Nazwa: WorkflowStatus<br /><br /> Lokalizacja: 10, 73<br /><br /> Wiele linii: True<br /><br /> Tylko do odczytu: True<br /><br /> Paski przewijania: pionowe<br /><br /> Rozmiar: 338, 208|  
  
5.  Ustaw **AcceptButton** właściwości formularza, aby **EnterGuess**.  
  
 Poniższy przykład przedstawia wypełnionego formularza.  
  
 ![WF45 Wprowadzenie formularz hosta przepływu pracy samouczek](../../../docs/framework/windows-workflow-foundation/media/wf45gettingstartedtutorialworkflowhostform.png "WF45GettingStartedTutorialWorkflowHostForm")  
  
###  <a name="BKMK_AddHelperMethods"></a> Aby dodać właściwości i metody pomocnicze formularza  
 Kroki opisane w tej sekcji Dodaj właściwości i metody pomocnicze do klasy formularza, które skonfigurować interfejsu użytkownika w postaci do obsługi uruchomiona i wznawianie numer argumentu przepływów pracy.  
  
1.  Kliknij prawym przyciskiem myszy **WorkflowHostForm** w **Eksploratora rozwiązań** i wybierz polecenie **kod widoku**.  
  
2.  Dodaj następujące `using` (lub `Imports`) instrukcje w górnej części pliku z innym `using` (lub `Imports`) instrukcje.  
  
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
    >  Jeśli ciąg połączenia jest inna, należy zaktualizować `connectionString` do odwoływania się do bazy danych.  
  
4.  Dodaj `WorkflowInstanceId` właściwości `WorkflowFormHost` klasy.  
  
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
  
     `InstanceId` Pola kombi zostanie wyświetlona lista identyfikatorów wystąpień utrwalonych przepływów pracy oraz `WorkflowInstanceId` właściwość zwraca aktualnie wybrany przepływ pracy.  
  
5.  Dodaj obsługę formularza `Load` zdarzeń. Aby dodać program obsługi, przełącz się do **widoku Projekt** formularza, kliknij przycisk **zdarzenia** ikony na początku **właściwości** okna, a następnie kliknij dwukrotnie **obciążenia**.  
  
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
  
     Załadowanie formularza, `SqlWorkflowInstanceStore` jest skonfigurowany, pola kombi typ zakresu i przepływu pracy są ustawione na wartości domyślne, a także wystąpień utrwalonych przepływów pracy są dodawane do `InstanceId` pola kombi.  
  
7.  Dodaj `SelectedIndexChanged` obsługę `InstanceId`. Aby dodać program obsługi, przełącz się do **widoku Projekt** formularza, wybierz `InstanceId` pola kombi kliknij **zdarzenia** ikony na początku **właściwości** okna, i Kliknij dwukrotnie **SelectedIndexChanged**.  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
8.  Dodaj następujący kod do `InstanceId_SelectedIndexChanged`. Zawsze, gdy użytkownik wybierze przepływu pracy za pomocą pola kombi ten program obsługi aktualizacji okna stanu.  
  
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
  
9. Dodaj następujące `ListPersistedWorkflows` metodę do klasy formularza.  
  
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
  
     `ListPersistedWorkflows` wysyła kwerendy w magazynie wystąpień dla wystąpień utrwalonych przepływów pracy i dodaje identyfikatorów wystąpienia `cboInstanceId` pola kombi.  
  
10. Dodaj następujące `UpdateStatus` metody oraz odpowiednich delegowanie do klasy formularza. Ta metoda aktualizacji okno stanu w formularzu ze stanem obecnie uruchomiony przepływ pracy.  
  
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
  
11. Dodaj następujące `GameOver` metody oraz odpowiednich delegowanie do klasy formularza. Po zakończeniu przepływu pracy, ta metoda aktualizacji formularza interfejsu użytkownika poprzez usunięcie identyfikator wystąpienia przepływu pracy ukończonych od **InstanceId** pola kombi.  
  
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
  
###  <a name="BKMK_ConfigureWorkflowApplication"></a> Aby skonfigurować Magazyn wystąpienia przepływu pracy obsługi cyklu życia i rozszerzenia  
  
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
  
     Ta metoda umożliwia skonfigurowanie `WorkflowApplication`, dodaje żądanego rozszerzenia i dodaje obsługę zdarzeń cyklu życia przepływu pracy.  
  
2.  W `ConfigureWorkflowApplication`, określ `SqlWorkflowInstanceStore` dla `WorkflowApplication`.  
  
    ```vb  
    'Configure the persistence store.  
    wfApp.InstanceStore = store  
    ```  
  
    ```csharp  
    // Configure the persistence store.  
    wfApp.InstanceStore = store;  
    ```  
  
3.  Następnie należy utworzyć `StringWriter` wystąpienia i dodaj go do `Extensions` kolekcji `WorkflowApplication`. Gdy `StringWriter` zostanie dodany do rozszerzeń zapisywane, wszystkie `WriteLine` dane wyjściowe działania. Gdy przepływ pracy, staje się bezczynny, `WriteLine` można wyodrębnić dane wyjściowe z `StringWriter` i wyświetlane w formularzu.  
  
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
  
4.  Dodaj następujące obsługę `Completed` zdarzeń. Po pomyślnym zakończeniu przepływu pracy, liczba włącza podjęte w celu odgadnięcia się, że liczba jest wyświetlana w oknie stanu. Jeśli przepływ pracy zakończy, informacje o wyjątku, który spowodował przerwanie jest wyświetlany. Po zakończeniu obsługi `GameOver` wywoływana jest metoda, która usuwa z listy przepływu pracy ukończonych przepływów pracy.  
  
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
  
5.  Dodaj następujące `Aborted` i `OnUnhandledException` programów obsługi. `GameOver` Metoda nie jest wywoływana z `Aborted` obsługi, ponieważ gdy wystąpienia przepływu pracy zostało przerwane, nie zakończy i jest możliwe wznowienie wystąpienie w późniejszym czasie.  
  
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
  
6.  Dodaj następujące `PersistableIdle` obsługi. Pobiera ten program obsługi `StringWriter` rozszerzenia, które zostały dodane, wyodrębnia dane wyjściowe z `WriteLine` działań i wyświetla je w oknie stanu.  
  
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
  
     <xref:System.Activities.PersistableIdleAction> Wyliczenie ma trzy wartości: <xref:System.Activities.PersistableIdleAction.None>, <xref:System.Activities.PersistableIdleAction.Persist>, i <xref:System.Activities.PersistableIdleAction.Unload>. <xref:System.Activities.PersistableIdleAction.Persist> przyczyny przepływu pracy, aby utrwalić jednak nie spowoduje zwolnienia przepływu pracy. <xref:System.Activities.PersistableIdleAction.Unload> powoduje, że przepływ pracy do utrwalenia i zostać zwolniony.  
  
     Poniższy przykład jest wypełniony `ConfigureWorkflowApplication` metody.  
  
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
 Aby wznowić wystąpienia przepływu pracy, host musi dostarczyć definicji przepływu pracy. W tym samouczku są trzy typy przepływu pracy, a kolejne kroki samouczka wprowadzić wiele wersji tych typów. `WorkflowIdentity` umożliwia aplikacji hosta skojarzyć z wystąpieniem przepływu pracy utrwalonych informacje identyfikacyjne. Kroki opisane w tej sekcji przedstawiają sposób utworzyć klasę narzędzie pomagające mapowania tożsamości przepływu pracy z wystąpienia utrwalonego przepływu pracy do odpowiedniej definicji przepływu pracy. Aby uzyskać więcej informacji na temat `WorkflowIdentity` i wersji, zobacz [za pomocą właściwości WorkflowIdentity and Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md).  
  
1.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **klasy**. Typ `WorkflowVersionMap` do **nazwa** polu i kliknij przycisk **Dodaj**.  
  
2.  Dodaj następujące `using` lub `Imports` instrukcje w górnej części pliku z innym `using` lub `Imports` instrukcje.  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Activities  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Activities;  
    ```  
  
3.  Zastąp `WorkflowVersionMap` deklaracji z następujących deklaracją klasy.  
  
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
  
     `WorkflowVersionMap` zawiera trzy tożsamości przepływu pracy, które mapują do trzech definicji przepływu pracy z tego samouczka i jest używany w następujących sekcjach, gdy przepływy pracy są uruchomione i wznowione.  
  
###  <a name="BKMK_StartWorkflow"></a> Aby uruchomić nowy przepływ pracy  
  
1.  Dodaj `Click` obsługę `NewGame`. Aby dodać program obsługi, przełącz się do **widoku Projekt** formularza i kliknij dwukrotnie `NewGame`. A `NewGame_Click` dodaniu obsługi, a widok przełączenie się do widoku kodu formularza. Gdy użytkownik kliknie ten przycisk Nowy przepływ pracy jest uruchomiony.  
  
    ```vb  
    Private Sub NewGame_Click(sender As Object, e As EventArgs) Handles NewGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void NewGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Dodaj następujący kod do obsługi kliknięcia. Ten kod tworzy słownika argumentów wejściowych przepływu pracy, wyznaczaną przez Nazwa argumentu. Ten słownik ma jeden wpis zawierający zakres generowany losowo numer pobierane z zakresu pola kombi.  
  
    ```vb  
    Dim inputs As New Dictionary(Of String, Object)()  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem))  
    ```  
  
    ```csharp  
    var inputs = new Dictionary<string, object>();  
    inputs.Add("MaxNumber", Convert.ToInt32(NumberRange.SelectedItem));  
    ```  
  
3.  Następnie dodaj następujący kod, który uruchamia przepływ pracy. `WorkflowIdentity` i odpowiednio do typu przepływu pracy wybrane definicji przepływu pracy są pobierane przy użyciu `WorkflowVersionMap` Klasa pomocy. Następnie, nowy `WorkflowApplication` wystąpienia jest tworzony przy użyciu definicji przepływu pracy `WorkflowIdentity`i słownika argumentów wejściowych.  
  
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
  
4.  Następnie dodaj następujący kod, który dodaje przepływu pracy do listy przepływu pracy i wyświetla informacje o wersji przepływu pracy w formularzu.  
  
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
  
5.  Wywołanie `ConfigureWorkflowApplication` do skonfigurowania obsługi cyklu życia magazynu, rozszerzenia i przepływu pracy wystąpienia tego `WorkflowApplication` wystąpienia.  
  
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
  
6.  Na koniec wywołania `Run`.  
  
    ```vb  
    'Start the workflow.  
    wfApp.Run()  
    ```  
  
    ```  
    // Start the workflow.  
    wfApp.Run();  
    ```  
  
     Poniższy przykład jest wypełniony `NewGame_Click` obsługi.  
  
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
  
1.  Dodaj `Click` obsługę `EnterGuess`. Aby dodać program obsługi, przełącz się do **widoku Projekt** formularza i kliknij dwukrotnie `EnterGuess`. Gdy użytkownik kliknie przycisk ten przepływ pracy jest wznawiana.  
  
    ```vb  
    Private Sub EnterGuess_Click(sender As Object, e As EventArgs) Handles EnterGuess.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void EnterGuess_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Dodaj następujący kod, aby upewnić się, że przepływ pracy jest zaznaczony na liście przepływu pracy i że wynik użytkownika jest prawidłowy.  
  
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
  
3.  Następnie należy pobrać `WorkflowApplicationInstance` wystąpienia utrwalonego przepływu pracy. A `WorkflowApplicationInstance` reprezentuje wystąpienie utrwalonych przepływów pracy, który nie został jeszcze skojarzony z definicją przepływu pracy. `DefinitionIdentity` z `WorkflowApplicationInstance` zawiera `WorkflowIdentity` wystąpienia utrwalonego przepływu pracy. W tym samouczku `WorkflowVersionMap` klasy narzędzia są używane do mapowania `WorkflowIdentity` do definicji przepływu pracy poprawne. Po pobraniu definicji przepływu pracy `WorkflowApplication` jest tworzony przy użyciu definicji przepływu pracy poprawne.  
  
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
  
4.  Raz `WorkflowApplication` jest tworzony, skonfigurować Magazyn wystąpienia przepływu pracy obsługi cyklu życia i rozszerzeń przez wywołanie metody `ConfigureWorkflowApplication`. Te kroki należy wykonać zawsze nowy `WorkflowApplication` jest tworzony, i musi zostać wykonane przed załadowaniem wystąpienia przepływu pracy do `WorkflowApplication`. Po załadowaniu przepływ pracy zostanie wznowione od wartości wynik użytkownika.  
  
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
  
5.  Na koniec wyczyść pole tekstowe wynik i przygotowanie formularz, aby akceptować inny wynik.  
  
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
  
     Poniższy przykład jest wypełniony `EnterGuess_Click` obsługi.  
  
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
  
###  <a name="BKMK_TerminateWorkflow"></a> Zakończenie przepływu pracy  
  
1.  Dodaj `Click` obsługę `QuitGame`. Aby dodać program obsługi, przełącz się do **widoku Projekt** formularza i kliknij dwukrotnie `QuitGame`. Gdy użytkownik kliknie ten przycisk aktualnie wybrany przepływ pracy zostanie zakończony.  
  
    ```vb  
    Private Sub QuitGame_Click(sender As Object, e As EventArgs) Handles QuitGame.Click  
  
    End Sub  
    ```  
  
    ```csharp  
    private void QuitGame_Click(object sender, EventArgs e)  
    {  
  
    }  
    ```  
  
2.  Dodaj następujący kod do `QuitGame_Click` obsługi. Ten kod najpierw sprawdza, upewnij się, że przepływ pracy jest zaznaczony na liście przepływu pracy. Następnie ładuje trwałego wystąpienia do `WorkflowApplicationInstance`, używa `DefinitionIdentity` do określenia definicji przepływu pracy poprawne, a następnie inicjuje `WorkflowApplication`. Obok rozszerzeń i obsługi cyklu życia przepływu pracy są skonfigurowane przy użyciu wywołania do `ConfigureWorkflowApplication`. Raz `WorkflowApplication` jest skonfigurowany, załadowaniu go, a następnie `Terminate` jest wywoływana.  
  
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
  
2.  Dodaj następujące `using` (lub `Imports`) instrukcji w górnej części pliku z innym `using` (lub `Imports`) instrukcje.  
  
    ```vb  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
3.  Usuń lub komentarz istniejący kod z obsługującym przepływ pracy [porady: uruchamianie przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)i zastąp go następującym kodem.  
  
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
  
4.  Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **właściwości**. W **aplikacji** karcie, określ **aplikacji systemu Windows** dla **Output typu**. Ten krok jest opcjonalny, ale jeśli nie występuje w oknie konsoli zostanie wyświetlony oprócz formularza.  
  
5.  Naciśnij klawisze Ctrl + Shift + B do skompilowania aplikacji.  
  
6.  Upewnij się, że **NumberGuessWorkflowHost** jest ustawiony jako aplikacja do uruchomienia, a następnie naciśnij klawisz Ctrl + F5, aby uruchomić aplikację.  
  
7.  Wybierz zakres guessing gry i typ przepływu pracy, aby rozpocząć, a następnie kliknij przycisk **nowych gier**. Wprowadź wynik w **Guess** polu i kliknij przycisk **Przejdź** można przesłać z wynik. Należy pamiętać, że dane wyjściowe z `WriteLine` działania jest wyświetlana w formularzu.  
  
8.  Uruchom kilka przepływów pracy za pomocą typów innego przepływu pracy i liczba zakresów, wprowadź niektórych prób, a następnie przełączać się między przepływami pracy, wybierając z **identyfikator wystąpienia przepływu pracy** listy.  
  
     Należy pamiętać, że przełączenie do nowego przepływu pracy poprzednich prób i postęp przepływu pracy nie są wyświetlane w oknie stanu. Przyczyny stanu nie jest dostępna jest ponieważ zostaną zebrane i nie zapisano w dowolnym miejscu. W następnym kroku samouczka [porady: Tworzenie niestandardowych uczestnika śledzenia](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md), Utwórz uczestnika niestandardowych śledzenia, który zapisuje te informacje.
