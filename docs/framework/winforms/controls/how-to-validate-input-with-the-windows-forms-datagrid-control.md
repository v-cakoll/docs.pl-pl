---
title: "Porady: sprawdzanie poprawności danych wejściowych w formancie DataGrid formularzy systemu Windows"
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
helpviewer_keywords:
- DataGrid control [Windows Forms], examples
- user input [Windows Forms], validating
- examples [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], validating input
- validation [Windows Forms], user input
ms.assetid: f1e9c3a0-d0a1-4893-a615-b4b0db046c63
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f5e0c366f71f602be2bb1508a6abb00d3d0c83ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-input-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="bbaab-102">Porady: sprawdzanie poprawności danych wejściowych w formancie DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bbaab-102">How to: Validate Input with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="bbaab-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="bbaab-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="bbaab-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="bbaab-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="bbaab-105">Dostępne są dwa typy sprawdzania poprawności danych wejściowych dla formularzy systemu Windows <xref:System.Windows.Forms.DataGrid> formantu.</span><span class="sxs-lookup"><span data-stu-id="bbaab-105">There are two types of input validation available for the Windows Forms <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="bbaab-106">Jeśli użytkownik próbuje wpisz wartość, która ma typ danych nie do przyjęcia dla komórki, na przykład ciąg na liczbę całkowitą z zakresu stara wartość jest zastępowany nowe nieprawidłową wartość.</span><span class="sxs-lookup"><span data-stu-id="bbaab-106">If the user attempts to enter a value that is of an unacceptable data type for the cell, for example a string into an integer, the new invalid value is replaced with the old value.</span></span> <span data-ttu-id="bbaab-107">Tego rodzaju sprawdzania poprawności danych wejściowych odbywa się automatycznie i nie można dostosować.</span><span class="sxs-lookup"><span data-stu-id="bbaab-107">This kind of input validation is done automatically and cannot be customized.</span></span>  
  
 <span data-ttu-id="bbaab-108">Typ sprawdzania poprawności danych wejściowych może służyć do odrzucania niedopuszczalne danych, na przykład wartość 0 w polu musi być większa lub równa 1 lub niewłaściwe ciągu.</span><span class="sxs-lookup"><span data-stu-id="bbaab-108">The other type of input validation can be used to reject any unacceptable data, for example a 0 value in a field that must be greater than or equal to 1, or an inappropriate string.</span></span> <span data-ttu-id="bbaab-109">Jest to realizowane w zestawie danych przez program obsługi zdarzeń dla zapisu <xref:System.Data.DataTable.ColumnChanging> lub <xref:System.Data.DataTable.RowChanging> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="bbaab-109">This is done in the dataset by writing an event handler for the <xref:System.Data.DataTable.ColumnChanging> or <xref:System.Data.DataTable.RowChanging> event.</span></span> <span data-ttu-id="bbaab-110">Poniższym przykładzie użyto <xref:System.Data.DataTable.ColumnChanging> zdarzenie, ponieważ można zaakceptować wartości jest niedozwolone w szczególności dla kolumny "Product".</span><span class="sxs-lookup"><span data-stu-id="bbaab-110">The example below uses the <xref:System.Data.DataTable.ColumnChanging> event because the unacceptable value is disallowed for the "Product" column in particular.</span></span> <span data-ttu-id="bbaab-111">Można na przykład <xref:System.Data.DataTable.RowChanging> zdarzeń do sprawdzania, czy wartość kolumny "Data zakończenia" jest nowsza niż kolumna "Data rozpoczęcia" w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="bbaab-111">You might use the <xref:System.Data.DataTable.RowChanging> event for checking that the value of an "End Date" column is later than the "Start Date" column in the same row.</span></span>  
  
### <a name="to-validate-user-input"></a><span data-ttu-id="bbaab-112">Aby sprawdzić poprawność danych wejściowych użytkownika</span><span class="sxs-lookup"><span data-stu-id="bbaab-112">To validate user input</span></span>  
  
1.  <span data-ttu-id="bbaab-113">Napisać kod obsługujący <xref:System.Data.DataTable.ColumnChanging> zdarzenia dla odpowiedniej tabeli.</span><span class="sxs-lookup"><span data-stu-id="bbaab-113">Write code to handle the <xref:System.Data.DataTable.ColumnChanging> event for the appropriate table.</span></span> <span data-ttu-id="bbaab-114">Po wykryciu nieodpowiednie dane wejściowe, wywołaj <xref:System.Data.DataRow.SetColumnError%2A> metody <xref:System.Data.DataRow> obiektu.</span><span class="sxs-lookup"><span data-stu-id="bbaab-114">When inappropriate input is detected, call the <xref:System.Data.DataRow.SetColumnError%2A> method of the <xref:System.Data.DataRow> object.</span></span>  
  
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
  
2.  <span data-ttu-id="bbaab-115">Połącz program obsługi zdarzeń do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="bbaab-115">Connect the event handler to the event.</span></span>  
  
     <span data-ttu-id="bbaab-116">Formularz miejsce poniżej kod albo <xref:System.Windows.Forms.Form.Load> zdarzenia lub jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="bbaab-116">Place the following code within either the form's <xref:System.Windows.Forms.Form.Load> event or its constructor.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bbaab-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbaab-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <xref:System.Data.DataTable.ColumnChanging>  
 <xref:System.Data.DataRow.SetColumnError%2A>  
 [<span data-ttu-id="bbaab-118">DataGrid — formant</span><span class="sxs-lookup"><span data-stu-id="bbaab-118">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
