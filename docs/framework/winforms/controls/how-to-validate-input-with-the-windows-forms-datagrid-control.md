---
title: Sprawdzanie poprawności danych wejściowych za pomocą kontrolki DataGrid
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
ms.openlocfilehash: 3958089007401d2e977c9c96f07c9196e6216596
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728301"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a>Porady: sprawdzanie poprawności danych wejściowych w formancie DataGrid formularzy systemu Windows

> [!NOTE]
> Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości. Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Dostępne są dwa typy walidacji danych wejściowych dla kontrolki <xref:System.Windows.Forms.DataGrid> Windows Forms. Jeśli użytkownik spróbuje wprowadzić wartość, która ma nieakceptowalny typ danych dla komórki, na przykład ciąg do liczby całkowitej, Nowa nieprawidłowa wartość zostanie zastąpiona starą wartością. Ten rodzaj walidacji danych wejściowych jest wykonywany automatycznie i nie można go dostosować.

Inny typ walidacji danych wejściowych może służyć do odrzucania wszelkich nieakceptowalnych danych, na przykład 0 wartość w polu, które musi być większe lub równe 1 lub nieodpowiedniemu ciągowi. W tym celu należy napisać program obsługi zdarzeń dla zdarzenia <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging>. Poniższy przykład używa zdarzenia <xref:System.Data.DataTable.ColumnChanging>, ponieważ nieakceptowalna wartość jest niedozwolona dla kolumny "Product" w szczególności. Możesz użyć zdarzenia <xref:System.Data.DataTable.RowChanging>, aby sprawdzić, czy wartość kolumny "Data końcowa" jest późniejsza niż kolumna "Data rozpoczęcia" w tym samym wierszu.

## <a name="to-validate-user-input"></a>Aby sprawdzić poprawność danych wejściowych użytkownika

1. Napisz kod, aby obsłużyć zdarzenie <xref:System.Data.DataTable.ColumnChanging> dla odpowiedniej tabeli. Gdy wykryto Nieodpowiedni dane wejściowe, wywołaj metodę <xref:System.Data.DataRow.SetColumnError%2A> obiektu <xref:System.Data.DataRow>.

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

2. Połącz procedurę obsługi zdarzeń ze zdarzeniem.

    Umieść poniższy kod w ramach zdarzenia <xref:System.Windows.Forms.Form.Load> lub jego konstruktora.

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
