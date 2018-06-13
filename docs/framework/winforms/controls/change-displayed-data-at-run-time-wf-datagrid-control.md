---
title: 'Porady: zmienianie wyświetlanych danych w czasie wykonywania w formancie DataGrid formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
ms.openlocfilehash: 1059f774ae8d2c203d7a4f5c02c597b4686304f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526917"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="5c151-102">Porady: zmienianie wyświetlanych danych w czasie wykonywania w formancie DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5c151-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="5c151-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="5c151-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="5c151-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="5c151-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="5c151-105">Po utworzeniu formularzy systemu Windows <xref:System.Windows.Forms.DataGrid> przy użyciu funkcje czasu projektowania, możesz również dynamicznie zmiany elementów <xref:System.Data.DataSet> obiektu siatki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5c151-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="5c151-106">Może to obejmować zmiany albo poszczególnych wartości w tabeli lub zmiana źródła danych jest powiązany z <xref:System.Windows.Forms.DataGrid> formantu.</span><span class="sxs-lookup"><span data-stu-id="5c151-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="5c151-107">Zmiany w poszczególnych wartości są wykonywane za pomocą <xref:System.Data.DataSet> obiektu nie <xref:System.Windows.Forms.DataGrid> formantu.</span><span class="sxs-lookup"><span data-stu-id="5c151-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="5c151-108">Aby programowo zmienić danych</span><span class="sxs-lookup"><span data-stu-id="5c151-108">To change data programmatically</span></span>  
  
1.  <span data-ttu-id="5c151-109">Określ żądaną tabelę z <xref:System.Data.DataSet> obiekt i żądanego wiersza i pola z tabeli oraz ustaw nowe wartości komórki.</span><span class="sxs-lookup"><span data-stu-id="5c151-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5c151-110">Aby określić w pierwszej tabeli z <xref:System.Data.DataSet> lub pierwszego wiersza tabeli, użyj wartości 0.</span><span class="sxs-lookup"><span data-stu-id="5c151-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="5c151-111">Poniższy przykład przedstawia sposób zmienić drugi wpis pierwszego wiersza w pierwszej tabeli zestawu danych, klikając `Button1`.</span><span class="sxs-lookup"><span data-stu-id="5c151-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="5c151-112"><xref:System.Data.DataSet> (`ds`) I tabele (`0` i `1`) wcześniej zostały utworzone.</span><span class="sxs-lookup"><span data-stu-id="5c151-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
    ```  
  
    ```cpp  
    private:   
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     <span data-ttu-id="5c151-113">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5c151-113">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="5c151-114">W czasie, można użyć wykonywania <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę, aby powiązać <xref:System.Windows.Forms.DataGrid> formantu z innym źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="5c151-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="5c151-115">Na przykład może mieć kilka [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] formantów danych każdy jest połączony z inną bazą danych.</span><span class="sxs-lookup"><span data-stu-id="5c151-115">For example, you may have several [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="5c151-116">Aby programowo zmienić źródła danych</span><span class="sxs-lookup"><span data-stu-id="5c151-116">To change the DataSource programmatically</span></span>  
  
1.  <span data-ttu-id="5c151-117">Ustaw <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę nazwę źródła danych i chcesz powiązać z tabeli.</span><span class="sxs-lookup"><span data-stu-id="5c151-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="5c151-118">Poniższy przykład przedstawia sposób zmienić przy użyciu źródła Data <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] formantu danych (adoPubsAuthors), który jest podłączony do tabeli Autorzy w bazie danych Pubs.</span><span class="sxs-lookup"><span data-stu-id="5c151-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5c151-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c151-119">See Also</span></span>  
 [<span data-ttu-id="5c151-120">Zestawy danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5c151-120">ADO.NET DataSets</span></span>](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 [<span data-ttu-id="5c151-121">Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c151-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="5c151-122">Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c151-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="5c151-123">Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="5c151-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
