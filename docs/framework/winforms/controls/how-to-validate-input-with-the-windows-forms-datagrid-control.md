---
title: 'Instrukcje: Sprawdzanie poprawności danych wejściowych za pomocą kontrolki DataGrid formularzy Windows Forms'
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
ms.openlocfilehash: 55de6fc1ef4fdf94495ddb07f3329ef9d46b5818
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609489"
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="cbd05-102">Instrukcje: Sprawdzanie poprawności danych wejściowych za pomocą kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cbd05-102">How to: Validate Input with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="cbd05-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="cbd05-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="cbd05-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="cbd05-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="cbd05-105">Istnieją dwa typy walidacji danych wejściowych w dostępnych dla formularzy Windows Forms <xref:System.Windows.Forms.DataGrid> kontroli.</span><span class="sxs-lookup"><span data-stu-id="cbd05-105">There are two types of input validation available for the Windows Forms <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="cbd05-106">Jeśli użytkownik próbuje wprowadzić wartość jest typu danych nieodpowiednia dla komórki, na przykład ciąg na liczbę całkowitą, nowa wartość nieprawidłowa jest zastępowany starej wartości.</span><span class="sxs-lookup"><span data-stu-id="cbd05-106">If the user attempts to enter a value that is of an unacceptable data type for the cell, for example a string into an integer, the new invalid value is replaced with the old value.</span></span> <span data-ttu-id="cbd05-107">Tego rodzaju Walidacja danych wejściowych odbywa się automatycznie i nie można dostosować.</span><span class="sxs-lookup"><span data-stu-id="cbd05-107">This kind of input validation is done automatically and cannot be customized.</span></span>  
  
 <span data-ttu-id="cbd05-108">Typ sprawdzania poprawności danych wejściowych może służyć do odrzucenia nie do przyjęcia danych, na przykład wartość 0 w polu, które musi być większa lub równa 1 lub nieodpowiednie ciąg.</span><span class="sxs-lookup"><span data-stu-id="cbd05-108">The other type of input validation can be used to reject any unacceptable data, for example a 0 value in a field that must be greater than or equal to 1, or an inappropriate string.</span></span> <span data-ttu-id="cbd05-109">Odbywa się w zestawie danych, pisząc program obsługi zdarzeń dla <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cbd05-109">This is done in the dataset by writing an event handler for the <xref:System.Data.DataTable.ColumnChanging> or <xref:System.Data.DataTable.RowChanging> event.</span></span> <span data-ttu-id="cbd05-110">W poniższym przykładzie użyto <xref:System.Data.DataTable.ColumnChanging> zdarzenie, ponieważ wartość można zaakceptować jest niedozwolone w szczególności dla kolumny "Product".</span><span class="sxs-lookup"><span data-stu-id="cbd05-110">The example below uses the <xref:System.Data.DataTable.ColumnChanging> event because the unacceptable value is disallowed for the "Product" column in particular.</span></span> <span data-ttu-id="cbd05-111">Można na przykład <xref:System.Data.DataTable.RowChanging> zdarzeń do sprawdzania, czy wartość kolumny "Data zakończenia" jest nowsza niż kolumna "Data rozpoczęcia", w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="cbd05-111">You might use the <xref:System.Data.DataTable.RowChanging> event for checking that the value of an "End Date" column is later than the "Start Date" column in the same row.</span></span>  
  
### <a name="to-validate-user-input"></a><span data-ttu-id="cbd05-112">Aby sprawdzić poprawność danych wejściowych użytkownika</span><span class="sxs-lookup"><span data-stu-id="cbd05-112">To validate user input</span></span>  
  
1.  <span data-ttu-id="cbd05-113">Napisz kod obsługujący <xref:System.Data.DataTable.ColumnChanging> zdarzenia dla odpowiedniej tabeli.</span><span class="sxs-lookup"><span data-stu-id="cbd05-113">Write code to handle the <xref:System.Data.DataTable.ColumnChanging> event for the appropriate table.</span></span> <span data-ttu-id="cbd05-114">Po wykryciu nieodpowiednie dane wejściowe, wywołaj <xref:System.Data.DataRow.SetColumnError%2A> metody <xref:System.Data.DataRow> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cbd05-114">When inappropriate input is detected, call the <xref:System.Data.DataRow.SetColumnError%2A> method of the <xref:System.Data.DataRow> object.</span></span>  
  
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
  
2.  <span data-ttu-id="cbd05-115">Połącz program obsługi zdarzeń do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cbd05-115">Connect the event handler to the event.</span></span>  
  
     <span data-ttu-id="cbd05-116">Formularz miejsce poniżej kod w ramach jednej <xref:System.Windows.Forms.Form.Load> zdarzenia lub jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="cbd05-116">Place the following code within either the form's <xref:System.Windows.Forms.Form.Load> event or its constructor.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cbd05-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbd05-117">See also</span></span>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Data.DataTable.ColumnChanging>
- <xref:System.Data.DataRow.SetColumnError%2A>
- [<span data-ttu-id="cbd05-118">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="cbd05-118">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
