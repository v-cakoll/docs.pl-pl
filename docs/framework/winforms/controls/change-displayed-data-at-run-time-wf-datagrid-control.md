---
title: 'Instrukcje: zmienianie wyświetlanych danych w czasie wykonywania w kontrolce DataGrid formularzy systemu Windows'
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
ms.openlocfilehash: c7bf70a67729744f4cf96318f6b270a5ea81b812
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917722"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="c446b-102">Instrukcje: zmienianie wyświetlanych danych w czasie wykonywania w kontrolce DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c446b-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="c446b-103">Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="c446b-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="c446b-104">Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="c446b-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="c446b-105">Po utworzeniu Windows Forms <xref:System.Windows.Forms.DataGrid> przy użyciu funkcji czasu projektowania może być również konieczne dynamiczne zmianę elementów <xref:System.Data.DataSet> obiektu siatki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c446b-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="c446b-106">Może to obejmować zmiany poszczególnych wartości tabeli lub zmiany źródła danych powiązanego <xref:System.Windows.Forms.DataGrid> z kontrolką.</span><span class="sxs-lookup"><span data-stu-id="c446b-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="c446b-107">Zmiany poszczególnych wartości są wykonywane za pomocą <xref:System.Data.DataSet> obiektu, a <xref:System.Windows.Forms.DataGrid> nie formantu.</span><span class="sxs-lookup"><span data-stu-id="c446b-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="c446b-108">Aby programowo zmienić dane</span><span class="sxs-lookup"><span data-stu-id="c446b-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="c446b-109">Określ odpowiednią tabelę z <xref:System.Data.DataSet> obiektu i żądany wiersz i pole z tabeli i ustaw komórkę równą nowej wartości.</span><span class="sxs-lookup"><span data-stu-id="c446b-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c446b-110">Aby określić pierwszą tabelę <xref:System.Data.DataSet> lub pierwszy wiersz tabeli, należy użyć 0.</span><span class="sxs-lookup"><span data-stu-id="c446b-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="c446b-111">Poniższy przykład pokazuje, jak zmienić drugi wpis pierwszego wiersza w pierwszej tabeli zestawu danych, klikając pozycję `Button1`.</span><span class="sxs-lookup"><span data-stu-id="c446b-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="c446b-112">Zostały utworzone`ds`wcześniej`0` () i tabele `1`(i). <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="c446b-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="c446b-113">(Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c446b-113">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="c446b-114">W czasie wykonywania można użyć metody, <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> aby <xref:System.Windows.Forms.DataGrid> powiązać formant z innym źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="c446b-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="c446b-115">Na przykład może istnieć kilka ADO.NETch kontrolek danych połączonych z inną bazą danych.</span><span class="sxs-lookup"><span data-stu-id="c446b-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="c446b-116">Aby programowo zmienić źródło danych</span><span class="sxs-lookup"><span data-stu-id="c446b-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="c446b-117"><xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> Ustaw metodę na nazwę źródła danych i tabeli, do której chcesz utworzyć powiązanie.</span><span class="sxs-lookup"><span data-stu-id="c446b-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="c446b-118">Poniższy przykład pokazuje, jak zmienić źródło daty przy użyciu <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody do kontrolki danych ADO.NET (adoPubsAuthors), która jest połączona z tabelą autorów w bazie danych pubs.</span><span class="sxs-lookup"><span data-stu-id="c446b-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c446b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c446b-119">See also</span></span>

- [<span data-ttu-id="c446b-120">Zestawy danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c446b-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="c446b-121">Instrukcje: Usuwanie lub ukrywanie kolumn w kontrolce DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c446b-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="c446b-122">Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c446b-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="c446b-123">Instrukcje: Powiązywanie kontrolki DataGrid Windows Forms ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="c446b-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
