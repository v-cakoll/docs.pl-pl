---
title: 'Porady: sprawdzanie poprawności danych wejściowych w formancie DataGrid formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid control [Windows Forms], examples
- user input [Windows Forms], validating
- examples [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], validating input
- validation [Windows Forms], user input
ms.assetid: f1e9c3a0-d0a1-4893-a615-b4b0db046c63
ms.openlocfilehash: a01cb90b7cba596dafa56963dcf9c489deb3e21a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>Porady: sprawdzanie poprawności danych wejściowych w formancie DataGrid formularzy systemu Windows
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Dostępne są dwa typy sprawdzania poprawności danych wejściowych dla formularzy systemu Windows <xref:System.Windows.Forms.DataGrid> formantu. Jeśli użytkownik próbuje wpisz wartość, która ma typ danych nie do przyjęcia dla komórki, na przykład ciąg na liczbę całkowitą z zakresu stara wartość jest zastępowany nowe nieprawidłową wartość. Tego rodzaju sprawdzania poprawności danych wejściowych odbywa się automatycznie i nie można dostosować.  
  
 Typ sprawdzania poprawności danych wejściowych może służyć do odrzucania niedopuszczalne danych, na przykład wartość 0 w polu musi być większa lub równa 1 lub niewłaściwe ciągu. Jest to realizowane w zestawie danych przez program obsługi zdarzeń dla zapisu <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> zdarzeń. Poniższym przykładzie użyto <xref:System.Data.DataTable.ColumnChanging> zdarzenie, ponieważ można zaakceptować wartości jest niedozwolone w szczególności dla kolumny "Product". Można na przykład <xref:System.Data.DataTable.RowChanging> zdarzeń do sprawdzania, czy wartość kolumny "Data zakończenia" jest nowsza niż kolumna "Data rozpoczęcia" w tym samym wierszu.  
  
### <a name="to-validate-user-input"></a>Aby sprawdzić poprawność danych wejściowych użytkownika  
  
1.  Napisać kod obsługujący <xref:System.Data.DataTable.ColumnChanging> zdarzenia dla odpowiedniej tabeli. Po wykryciu nieodpowiednie dane wejściowe, wywołaj <xref:System.Data.DataRow.SetColumnError%2A> metody <xref:System.Data.DataRow> obiektu.  
  
    ```vb  
    Private Sub Customers_ColumnChanging(ByVal sender As Object, _  
    ByVal e As System.Data.DataColumnChangeEventArgs)  
       ' Only check for errors in the Product column  
       If (e.Column.ColumnName.Equals("Product")) Then  
          ' Do not allow "Automobile" as a product.  
          If CType(e.ProposedValue, String) = "Automobile" Then  
             Dim badValue As Object = e.ProposedValue  
             e.ProposedValue = "Bad Data"  
             e.Row.RowError = "The Product column contians an error"  
             e.Row.SetColumnError(e.Column, "Product cannot be " & _  
             CType(badValue, String))  
          End If  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    //Handle column changing events on the Customers table  
    private void Customers_ColumnChanging(object sender, System.Data.DataColumnChangeEventArgs e) {  
  
       //Only check for errors in the Product column  
       if (e.Column.ColumnName.Equals("Product")) {  
  
          //Do not allow "Automobile" as a product  
          if (e.ProposedValue.Equals("Automobile")) {  
             object badValue = e.ProposedValue;  
             e.ProposedValue = "Bad Data";  
             e.Row.RowError = "The Product column contains an error";  
             e.Row.SetColumnError(e.Column, "Product cannot be " + badValue);  
          }  
       }  
    }  
    ```  
  
2.  Połącz program obsługi zdarzeń do zdarzenia.  
  
     Formularz miejsce poniżej kod albo <xref:System.Windows.Forms.Form.Load> zdarzenia lub jego konstruktora.  
  
    ```vb  
    ' Assumes the grid is bound to a dataset called customersDataSet1  
    ' with a table called Customers.  
    ' Put this code in the form's Load event or its constructor.  
    AddHandler customersDataSet1.Tables("Customers").ColumnChanging, AddressOf Customers_ColumnChanging  
    ```  
  
    ```csharp  
    // Assumes the grid is bound to a dataset called customersDataSet1  
    // with a table called Customers.  
    // Put this code in the form's Load event or its constructor.  
    customersDataSet1.Tables["Customers"].ColumnChanging += new DataColumnChangeEventHandler(this.Customers_ColumnChanging);  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Data.DataTable.ColumnChanging>  
 <xref:System.Data.DataRow.SetColumnError%2A>  
 [DataGrid, kontrolka](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
