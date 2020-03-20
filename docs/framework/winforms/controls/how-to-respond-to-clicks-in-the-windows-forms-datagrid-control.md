---
title: Odpowiadanie na kliknięcia w formancie datagrid
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Click event [Windows Forms], monitoring in DataGrid controls
- DataGrid control [Windows Forms], examples
- DataGrid control [Windows Forms], returning clicked cell value
- cells [Windows Forms], location in DataGrid
- examples [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], click events
ms.assetid: a0aa204b-8351-4d82-9933-ee21a5c9e409
ms.openlocfilehash: e72d117b12d43ece8c4d05ed29ab45693418eede
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141942"
---
# <a name="how-to-respond-to-clicks-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="d5b17-102">Porady: odpowiadanie na kliknięcia w formancie DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d5b17-102">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="d5b17-103">Formant <xref:System.Windows.Forms.DataGridView> zastępuje i dodaje funkcjonalność <xref:System.Windows.Forms.DataGrid> do formantu; jednak <xref:System.Windows.Forms.DataGrid> formant jest zachowywany zarówno dla zgodności z powrotem i przyszłego użycia, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="d5b17-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="d5b17-104">Aby uzyskać więcej informacji, zobacz [Różnice między formami Windows DataGridView i DataGrid Formantów](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d5b17-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="d5b17-105">Po połączeniu <xref:System.Windows.Forms.DataGrid> formularzy systemu Windows z bazą danych można monitorować, którą komórkę kliknął użytkownik.</span><span class="sxs-lookup"><span data-stu-id="d5b17-105">After the Windows Forms <xref:System.Windows.Forms.DataGrid> is connected to a database, you can monitor which cell the user clicked.</span></span>  
  
### <a name="to-detect-when-the-user-of-the-datagrid-selects-a-different-cell"></a><span data-ttu-id="d5b17-106">Aby wykryć, kiedy użytkownik datagridu wybierze inną komórkę</span><span class="sxs-lookup"><span data-stu-id="d5b17-106">To detect when the user of the DataGrid selects a different cell</span></span>  
  
- <span data-ttu-id="d5b17-107">W <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> programie obsługi zdarzeń napisz kod, aby odpowiednio odpowiedzieć.</span><span class="sxs-lookup"><span data-stu-id="d5b17-107">In the <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> event handler, write code to respond appropriately.</span></span>  
  
    ```vb  
    Private Sub myDataGrid_CurrentCellChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles myDataGrid.CurrentCellChanged  
       MessageBox.Show("Col is " & myDataGrid.CurrentCell.ColumnNumber _  
          & ", Row is " & myDataGrid.CurrentCell.RowNumber _  
          & ", Value is " & myDataGrid.Item(myDataGrid.CurrentCell))  
    End Sub  
    ```  
  
    ```csharp  
    private void myDataGrid_CurrentCellChanged(object sender,
    System.EventArgs e)  
    {  
       MessageBox.Show ("Col is " + myDataGrid.CurrentCell.ColumnNumber  
          + ", Row is " + myDataGrid.CurrentCell.RowNumber
          + ", Value is " + myDataGrid[myDataGrid.CurrentCell] );  
    }  
    ```  
  
     <span data-ttu-id="d5b17-108">(Visual C#) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d5b17-108">(Visual C#) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.myDataGrid.CurrentCellChanged += new  
       System.EventHandler(this.myDataGrid_CurrentCellChanged);  
    ```  
  
### <a name="to-determine-which-part-of-the-datagrid-the-user-clicked"></a><span data-ttu-id="d5b17-109">Aby ustalić, która część datagridu użytkownik kliknął</span><span class="sxs-lookup"><span data-stu-id="d5b17-109">To determine which part of the DataGrid the user clicked</span></span>  
  
- <span data-ttu-id="d5b17-110">Wywołanie <xref:System.Windows.Forms.DataGrid.HitTest%2A> metody w odpowiednim programie obsługi <xref:System.Windows.Forms.Control.MouseDown> zdarzeń, takich jak dla lub <xref:System.Windows.Forms.Control.Click> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d5b17-110">Call the <xref:System.Windows.Forms.DataGrid.HitTest%2A> method in an appropriate event handler, such as for the <xref:System.Windows.Forms.Control.MouseDown> or <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
     <span data-ttu-id="d5b17-111">Metoda <xref:System.Windows.Forms.DataGrid.HitTest%2A> zwraca <xref:System.Windows.Forms.DataGrid.HitTestInfo> obiekt zawierający wiersz i kolumnę kliknowanego obszaru.</span><span class="sxs-lookup"><span data-stu-id="d5b17-111">The <xref:System.Windows.Forms.DataGrid.HitTest%2A> method returns a <xref:System.Windows.Forms.DataGrid.HitTestInfo> object that contains the row and column of a clicked area.</span></span>  
  
    ```vb  
    Private Sub myDataGrid_MouseDown(ByVal sender As Object, _  
    ByVal e As MouseEventArgs) Handles myDataGrid.MouseDown  
       Dim myGrid As DataGrid = CType(sender, DataGrid)  
       Dim hti As System.Windows.Forms.DataGrid.HitTestInfo  
       hti = myGrid.HitTest(e.X, e.Y)  
       Dim message As String = "You clicked "  
  
       Select Case hti.Type  
          Case System.Windows.Forms.DataGrid.HitTestType.None  
             message &= "the background."  
          Case System.Windows.Forms.DataGrid.HitTestType.Cell  
             message &= "cell at row " & hti.Row & ", col " & hti.Column  
          Case System.Windows.Forms.DataGrid.HitTestType.ColumnHeader  
             message &= "the column header for column " & hti.Column  
          Case System.Windows.Forms.DataGrid.HitTestType.RowHeader  
             message &= "the row header for row " & hti.Row  
          Case System.Windows.Forms.DataGrid.HitTestType.ColumnResize  
             message &= "the column resizer for column " & hti.Column  
          Case System.Windows.Forms.DataGrid.HitTestType.RowResize  
             message &= "the row resizer for row " & hti.Row  
          Case System.Windows.Forms.DataGrid.HitTestType.Caption  
             message &= "the caption"  
          Case System.Windows.Forms.DataGrid.HitTestType.ParentRows  
             message &= "the parent row"  
       End Select  
  
       Console.WriteLine(message)  
    End Sub  
    ```  
  
    ```csharp  
    private void myDataGrid_MouseDown(object sender,
    System.Windows.Forms.MouseEventArgs e)  
    {  
       DataGrid myGrid = (DataGrid) sender;  
       System.Windows.Forms.DataGrid.HitTestInfo hti;  
       hti = myGrid.HitTest(e.X, e.Y);  
       string message = "You clicked ";  
  
       switch (hti.Type)
       {  
          case System.Windows.Forms.DataGrid.HitTestType.None :  
             message += "the background.";  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.Cell :  
             message += "cell at row " + hti.Row + ", col " + hti.Column;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.ColumnHeader :  
             message += "the column header for column " + hti.Column;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.RowHeader :  
             message += "the row header for row " + hti.Row;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.ColumnResize :  
             message += "the column resizer for column " + hti.Column;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.RowResize :  
             message += "the row resizer for row " + hti.Row;  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.Caption :  
             message += "the caption";  
             break;  
          case System.Windows.Forms.DataGrid.HitTestType.ParentRows :  
             message += "the parent row";  
             break;  
          }  
  
          Console.WriteLine(message);  
    }  
    ```  
  
     <span data-ttu-id="d5b17-112">(Visual C#) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d5b17-112">(Visual C#) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.myDataGrid.MouseDown += new  
       System.Windows.Forms.MouseEventHandler  
       (this.myDataGrid_MouseDown);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d5b17-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5b17-113">See also</span></span>

- [<span data-ttu-id="d5b17-114">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="d5b17-114">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="d5b17-115">Instrukcje: zmienianie wyświetlanych danych w czasie wykonywania w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5b17-115">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)
