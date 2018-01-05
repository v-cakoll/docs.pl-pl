---
title: "Porady: powiązanie danych z formantem MaskedTextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
- data binding [Windows Forms], MaskedTextBox control [Windows Forms]
- MaskedTextBox control [Windows Forms], binding data
ms.assetid: 34b29f07-e8df-48d4-b08b-53fcca524708
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb3fd4038634969d34be4514f4d314cf5d7513e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-data-to-the-maskedtextbox-control"></a>Porady: powiązanie danych z formantem MaskedTextBox
Można powiązać danych <xref:System.Windows.Forms.MaskedTextBox> sterować tak samo jak do żadnego formantu formularzy systemu Windows. Jednak jeśli format danych w bazie danych nie jest zgodny z formatu oczekiwanego przez definicję maski, należy sformatować dane. Poniższa procedura pokazuje, jak to zrobić przy użyciu <xref:System.Windows.Forms.Binding.Format> i <xref:System.Windows.Forms.Binding.Parse> zdarzenia <xref:System.Windows.Forms.Binding> klasy, aby wyświetlić numer telefonu oddzielne i telefonu rozszerzenie pola bazy danych jako pojedyncze pole można edytować.  
  
 Poniższa procedura wymaga dostępu do bazy danych programu SQL Server o bazie danych Northwind zainstalowane.  
  
### <a name="to-bind-data-to-a-maskedtextbox-control"></a>Wiązanie danych z formantem MaskedTextBox  
  
1.  Utwórz nowy projekt formularzy systemu Windows.  
  
2.  Przeciągnij dwa <xref:System.Windows.Forms.TextBox> formantów do formularza; nazwa je `FirstName` i `LastName`.  
  
3.  Przeciągnij <xref:System.Windows.Forms.MaskedTextBox> sterowania do formularza; nadaj mu nazwę `PhoneMask`.  
  
4.  Ustaw <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwość `PhoneMask` do `(000) 000-0000 x9999`.  
  
5.  Dodaj następujące przestrzeni nazw importuje do formularza.  
  
    ```csharp  
    using System.Data.SqlClient;  
    ```  
  
    ```vb  
    Imports System.Data.SqlClient  
    ```  
  
6.  Kliknij prawym przyciskiem myszy formularz, a następnie wybierz pozycję **kod widoku**. Umieść ten kod w dowolnym miejscu w klasie formularza.  
  
    ```csharp  
    Binding currentBinding, phoneBinding;  
    DataSet employeesTable = new DataSet();  
    SqlConnection sc;  
    SqlDataAdapter dataConnect;  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        DoMaskBinding();  
    }  
  
    private void DoMaskBinding()  
    {  
        try  
        {  
            sc = new SqlConnection("Data Source=CLIENTUE;Initial Catalog=NORTHWIND;Integrated Security=SSPI");  
            sc.Open();  
        }  
        catch (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
            return;  
        }  
  
        dataConnect = new SqlDataAdapter("SELECT * FROM Employees", sc);  
        dataConnect.Fill(employeesTable, "Employees");  
  
        // Now bind MaskedTextBox to appropriate field. Note that we must create the Binding objects  
        // before adding them to the control - otherwise, we won't get a Format event on the   
        // initial load.   
        try  
        {  
            currentBinding = new Binding("Text", employeesTable, "Employees.FirstName");  
            firstName.DataBindings.Add(currentBinding);  
  
            currentBinding = new Binding("Text", employeesTable, "Employees.LastName");  
            lastName.DataBindings.Add(currentBinding);  
  
            phoneBinding =new Binding("Text", employeesTable, "Employees.HomePhone");  
            // We must add the event handlers before we bind, or the Format event will not get called  
            // for the first record.  
            phoneBinding.Format += new ConvertEventHandler(phoneBinding_Format);  
            phoneBinding.Parse += new ConvertEventHandler(phoneBinding_Parse);  
            phoneMask.DataBindings.Add(phoneBinding);  
        }  
        catch (Exception ex)  
        {  
            MessageBox.Show(ex.Message);  
            return;  
        }  
    }  
    ```  
  
    ```vb  
    Dim WithEvents CurrentBinding, PhoneBinding As Binding  
    Dim EmployeesTable As New DataSet()  
    Dim sc As SqlConnection  
    Dim DataConnect As SqlDataAdapter  
  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        DoMaskedBinding()  
    End Sub  
  
    Private Sub DoMaskedBinding()  
        Try  
            sc = New SqlConnection("Data Source=SERVERNAME;Initial Catalog=NORTHWIND;Integrated Security=SSPI")  
            sc.Open()  
        Catch ex As Exception  
            MessageBox.Show(ex.Message)  
            Exit Sub  
        End Try  
  
        DataConnect = New SqlDataAdapter("SELECT * FROM Employees", sc)  
        DataConnect.Fill(EmployeesTable, "Employees")  
  
        ' Now bind MaskedTextBox to appropriate field. Note that we must create the Binding objects  
        ' before adding them to the control - otherwise, we won't get a Format event on the   
        ' initial load.  
        Try  
            CurrentBinding = New Binding("Text", EmployeesTable, "Employees.FirstName")  
            firstName.DataBindings.Add(CurrentBinding)  
            CurrentBinding = New Binding("Text", EmployeesTable, "Employees.LastName")  
            lastName.DataBindings.Add(CurrentBinding)  
            PhoneBinding = New Binding("Text", EmployeesTable, "Employees.HomePhone")  
            PhoneMask.DataBindings.Add(PhoneBinding)  
        Catch ex As Exception  
            MessageBox.Show(ex.Message)  
            Application.Exit()  
        End Try  
    End Sub  
    ```  
  
7.  Dodawanie obsługi zdarzeń <xref:System.Windows.Forms.Binding.Format> i <xref:System.Windows.Forms.Binding.Parse> zdarzenia o połączeniu i oddziel `PhoneNumber` i `Extension` pola powiązane z <xref:System.Data.DataSet>.  
  
    ```csharp  
    private void phoneBinding_Format(Object sender, ConvertEventArgs e)  
    {  
        String ext;  
  
        DataRowView currentRow = (DataRowView)BindingContext[employeesTable, "Employees"].Current;  
        if (currentRow["Extension"] == null)   
        {  
            ext = "";  
        } else   
        {  
            ext = currentRow["Extension"].ToString();  
        }  
  
        e.Value = e.Value.ToString().Trim() + " x" + ext;  
    }  
  
    private void phoneBinding_Parse(Object sender, ConvertEventArgs e)  
    {  
        String phoneNumberAndExt = e.Value.ToString();  
  
        int extIndex = phoneNumberAndExt.IndexOf("x");  
        String ext = phoneNumberAndExt.Substring(extIndex).Trim();  
        String phoneNumber = phoneNumberAndExt.Substring(0, extIndex).Trim();  
  
        //Get the current binding object, and set the new extension manually.   
        DataRowView currentRow = (DataRowView)BindingContext[employeesTable, "Employees"].Current;  
        // Remove the "x" from the extension.  
        currentRow["Extension"] = ext.Substring(1);  
  
        //Return the phone number.  
        e.Value = phoneNumber;  
    }  
    ```  
  
    ```vb  
    Private Sub PhoneBinding_Format(ByVal sender As Object, ByVal e As ConvertEventArgs) Handles PhoneBinding.Format  
        Dim Ext As String  
  
        Dim CurrentRow As DataRowView = CType(Me.BindingContext(EmployeesTable, "Employees").Current, DataRowView)  
        If (CurrentRow("Extension") Is Nothing) Then  
            Ext = ""  
        Else  
            Ext = CurrentRow("Extension").ToString()  
        End If  
  
        e.Value = e.Value.ToString().Trim() & " x" & Ext  
    End Sub  
  
    Private Sub PhoneBinding_Parse(ByVal sender As Object, ByVal e As ConvertEventArgs) Handles PhoneBinding.Parse  
        Dim PhoneNumberAndExt As String = e.Value.ToString()  
  
        Dim ExtIndex As Integer = PhoneNumberAndExt.IndexOf("x")  
        Dim Ext As String = PhoneNumberAndExt.Substring(ExtIndex).Trim()  
        Dim PhoneNumber As String = PhoneNumberAndExt.Substring(0, ExtIndex).Trim()  
  
        ' Get the current binding object, and set the new extension manually.   
        Dim CurrentRow As DataRowView = CType(Me.BindingContext(EmployeesTable, "Employees").Current, DataRowView)  
        ' Remove the "x" from the extension.  
        CurrentRow("Extension") = CObj(Ext.Substring(1))  
  
        ' Return the phone number.  
        e.Value = PhoneNumber  
    End Sub  
    ```  
  
8.  Dodaj dwa <xref:System.Windows.Forms.Button> formantów w formularzu. Nazwa je `previousButton` i `nextButton`. Kliknij dwukrotnie każdy przycisk, aby dodać <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń, a następnie wypełnij obsługę zdarzeń, jak pokazano w poniższym przykładzie kodu.  
  
    ```csharp  
    private void previousButton_Click(object sender, EventArgs e)  
    {  
        BindingContext[employeesTable, "Employees"].Position = BindingContext[employeesTable, "Employees"].Position - 1;  
    }  
  
    private void nextButton_Click(object sender, EventArgs e)  
    {  
        BindingContext[employeesTable, "Employees"].Position = BindingContext[employeesTable, "Employees"].Position + 1;  
    }  
    ```  
  
    ```vb  
    Private Sub PreviousButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles PreviousButton.Click  
        Me.BindingContext(EmployeesTable, "Employees").Position = Me.BindingContext(EmployeesTable, "Employees").Position - 1  
    End Sub  
  
    Private Sub NextButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles NextButton.Click  
        Me.BindingContext(EmployeesTable, "Employees").Position = Me.BindingContext(EmployeesTable, "Employees").Position + 1  
    End Sub  
    ```  
  
9. Uruchom próbkę. Edytuj dane i użyj **Wstecz** i **dalej** przycisków, aby zobaczyć, czy dane jest prawidłowo utrwalony na <xref:System.Data.DataSet>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod jest pełny kod wyświetlania wynikającą z wykonaniu poprzedniej procedury.  
  
 [!code-cpp[MaskedTextBoxData#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/MaskedTextBoxData/cpp/form1.cpp#1)]
 [!code-csharp[MaskedTextBoxData#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/MaskedTextBoxData/CS/form1.cs#1)]
 [!code-vb[MaskedTextBoxData#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/MaskedTextBoxData/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Utwórz [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] lub [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] projektu.  
  
-   Dodaj <xref:System.Windows.Forms.TextBox> i <xref:System.Windows.Forms.MaskedTextBox> formanty do formularza, zgodnie z opisem w poprzedniej procedurze.  
  
-   Otwórz plik kodu źródłowego dla projektu domyślnego formularza.  
  
-   Zastąp kod przedstawiony w poprzedniej sekcji 'Code' kodu źródłowego w tym pliku.  
  
-   Kompilowanie aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: praca z kontrolką MaskedTextBox](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)
