---
title: Zmiana wyświetlanych danych w czasie wykonywania w formancie DataGrid
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
ms.openlocfilehash: f91e2ea01ef4a52dd649efed70319017efb8368a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740587"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="6decc-102">Porady: zmienianie wyświetlanych danych w czasie wykonywania w formancie DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6decc-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="6decc-103">Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="6decc-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="6decc-104">Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="6decc-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="6decc-105">Po utworzeniu <xref:System.Windows.Forms.DataGrid> Windows Forms przy użyciu funkcji czasu projektowania, można również dynamicznie zmieniać elementy obiektu <xref:System.Data.DataSet> siatki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6decc-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="6decc-106">Może to obejmować zmiany poszczególnych wartości tabeli lub zmianę źródła danych powiązanego z kontrolką <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="6decc-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="6decc-107">Zmiany poszczególnych wartości są wykonywane za pomocą obiektu <xref:System.Data.DataSet>, a nie formantu <xref:System.Windows.Forms.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="6decc-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="6decc-108">Aby programowo zmienić dane</span><span class="sxs-lookup"><span data-stu-id="6decc-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="6decc-109">Określ żądaną tabelę z obiektu <xref:System.Data.DataSet> i żądany wiersz i pole z tabeli i ustaw komórkę równą nowej wartości.</span><span class="sxs-lookup"><span data-stu-id="6decc-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6decc-110">Aby określić pierwszą tabelę <xref:System.Data.DataSet> lub pierwszy wiersz tabeli, należy użyć 0.</span><span class="sxs-lookup"><span data-stu-id="6decc-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="6decc-111">Poniższy przykład pokazuje, jak zmienić drugi wpis pierwszego wiersza w pierwszej tabeli zestawu danych, klikając `Button1`.</span><span class="sxs-lookup"><span data-stu-id="6decc-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="6decc-112">Wcześniej utworzono <xref:System.Data.DataSet> (`ds`) i tabele (`0` i `1`).</span><span class="sxs-lookup"><span data-stu-id="6decc-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="6decc-113">(Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6decc-113">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="6decc-114">W czasie wykonywania można użyć metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>, aby powiązać formant <xref:System.Windows.Forms.DataGrid> z innym źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="6decc-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="6decc-115">Na przykład może istnieć kilka ADO.NETch kontrolek danych połączonych z inną bazą danych.</span><span class="sxs-lookup"><span data-stu-id="6decc-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="6decc-116">Aby programowo zmienić źródło danych</span><span class="sxs-lookup"><span data-stu-id="6decc-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="6decc-117">Ustaw metodę <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> na nazwę źródła danych i tabeli, do której chcesz utworzyć powiązanie.</span><span class="sxs-lookup"><span data-stu-id="6decc-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="6decc-118">Poniższy przykład pokazuje, jak zmienić źródło danych przy użyciu metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> na ADO.NET (adoPubsAuthors), która jest połączona z tabelą autorów w bazie danych pubs.</span><span class="sxs-lookup"><span data-stu-id="6decc-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6decc-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6decc-119">See also</span></span>

- [<span data-ttu-id="6decc-120">Zestawy danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6decc-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="6decc-121">Instrukcje: usuwanie lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6decc-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="6decc-122">Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6decc-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="6decc-123">Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="6decc-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
