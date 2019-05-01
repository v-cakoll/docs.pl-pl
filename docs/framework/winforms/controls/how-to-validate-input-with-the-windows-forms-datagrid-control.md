---
title: 'Instrukcje: sprawdzanie poprawności danych wejściowych w kontrolce DataGrid formularzy systemu Windows'
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
ms.openlocfilehash: dc8c8f157e6673c1bddc68bfb511683e6d2b99be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796477"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>Instrukcje: sprawdzanie poprawności danych wejściowych w kontrolce DataGrid formularzy systemu Windows

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz. Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Istnieją dwa typy walidacji danych wejściowych w dostępnych dla formularzy Windows Forms <xref:System.Windows.Forms.DataGrid> kontroli. Jeśli użytkownik próbuje wprowadzić wartość jest typu danych nieodpowiednia dla komórki, na przykład ciąg na liczbę całkowitą, nowa wartość nieprawidłowa jest zastępowany starej wartości. Tego rodzaju Walidacja danych wejściowych odbywa się automatycznie i nie można dostosować.

Typ sprawdzania poprawności danych wejściowych może służyć do odrzucenia nie do przyjęcia danych, na przykład wartość 0 w polu, które musi być większa lub równa 1 lub nieodpowiednie ciąg. Odbywa się w zestawie danych, pisząc program obsługi zdarzeń dla <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> zdarzeń. W poniższym przykładzie użyto <xref:System.Data.DataTable.ColumnChanging> zdarzenie, ponieważ wartość można zaakceptować jest niedozwolone w szczególności dla kolumny "Product". Można na przykład <xref:System.Data.DataTable.RowChanging> zdarzeń do sprawdzania, czy wartość kolumny "Data zakończenia" jest nowsza niż kolumna "Data rozpoczęcia", w tym samym wierszu.

## <a name="to-validate-user-input"></a>Aby sprawdzić poprawność danych wejściowych użytkownika

1. Napisz kod obsługujący <xref:System.Data.DataTable.ColumnChanging> zdarzenia dla odpowiedniej tabeli. Po wykryciu nieodpowiednie dane wejściowe, wywołaj <xref:System.Data.DataRow.SetColumnError%2A> metody <xref:System.Data.DataRow> obiektu.

    ```vb
    Private Sub Customers_ColumnChanging(ByVal sender As Object, _
    ByVal e As System.Data.DataColumnChangeEventArgs)
       ' Only check for errors in the Product column
       If (e.Column.ColumnName.Equals("Product")) Then
          ' Do not allow "Automobile" as a product.
          If CType(e.ProposedValue, String) = "Automobile" Then
             Dim badValue As Object = e.ProposedValue
             e.ProposedValue = "Bad Data"
             e.Row.RowError = "The Product column contains an error"
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

2. Połącz program obsługi zdarzeń do zdarzenia.

    Formularz miejsce poniżej kod w ramach jednej <xref:System.Windows.Forms.Form.Load> zdarzenia lub jego konstruktora.

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

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Data.DataTable.ColumnChanging>
- <xref:System.Data.DataRow.SetColumnError%2A>
- [DataGrid, kontrolka](datagrid-control-windows-forms.md)
