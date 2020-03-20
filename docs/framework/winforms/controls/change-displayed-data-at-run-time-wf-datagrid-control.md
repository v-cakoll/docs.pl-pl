---
title: Zmienianie wyświetlanych danych w czasie wykonywania w formancie DataGrid
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
ms.openlocfilehash: 6b788c10784082a0c74ee09f8cd85d540c670b84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142384"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="4cc88-102">Porady: zmienianie wyświetlanych danych w czasie wykonywania w formancie DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4cc88-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="4cc88-103">Formant <xref:System.Windows.Forms.DataGridView> zastępuje i dodaje funkcjonalność <xref:System.Windows.Forms.DataGrid> do formantu; jednak <xref:System.Windows.Forms.DataGrid> formant jest zachowywany zarówno dla zgodności z powrotem i przyszłego użycia, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="4cc88-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="4cc88-104">Aby uzyskać więcej informacji, zobacz [Różnice między formami Windows DataGridView i DataGrid Formantów](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4cc88-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="4cc88-105">Po utworzeniu formularzy <xref:System.Windows.Forms.DataGrid> systemu Windows przy użyciu funkcji czasu projektowania można <xref:System.Data.DataSet> również dynamicznie zmieniać elementy obiektu siatki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4cc88-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="4cc88-106">Może to obejmować zmiany poszczególnych wartości tabeli lub zmiana źródła <xref:System.Windows.Forms.DataGrid> danych powiązanego z formantem.</span><span class="sxs-lookup"><span data-stu-id="4cc88-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="4cc88-107">Zmiany poszczególnych wartości są <xref:System.Data.DataSet> wykonywane za <xref:System.Windows.Forms.DataGrid> pośrednictwem obiektu, a nie formantu.</span><span class="sxs-lookup"><span data-stu-id="4cc88-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="4cc88-108">Aby programowo zmienić dane</span><span class="sxs-lookup"><span data-stu-id="4cc88-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="4cc88-109">Określ żądaną <xref:System.Data.DataSet> tabelę z obiektu oraz żądany wiersz i pole z tabeli i ustaw komórkę równą nowej wartości.</span><span class="sxs-lookup"><span data-stu-id="4cc88-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4cc88-110">Aby określić pierwszą <xref:System.Data.DataSet> tabelę lub pierwszy wiersz tabeli, użyj 0.</span><span class="sxs-lookup"><span data-stu-id="4cc88-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="4cc88-111">W poniższym przykładzie pokazano, jak zmienić drugi wpis pierwszego wiersza `Button1`pierwszej tabeli zestawu danych, klikając przycisk .</span><span class="sxs-lookup"><span data-stu-id="4cc88-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="4cc88-112">( <xref:System.Data.DataSet> `ds`) i`0` tabele ( i `1`) zostały wcześniej utworzone.</span><span class="sxs-lookup"><span data-stu-id="4cc88-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="4cc88-113">(Visual C#, Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4cc88-113">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="4cc88-114">W czasie wykonywania można <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> użyć metody <xref:System.Windows.Forms.DataGrid> do powiązania formantu z innym źródłem danych.</span><span class="sxs-lookup"><span data-stu-id="4cc88-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="4cc88-115">Na przykład może mieć kilka formantów ADO.NET danych, każdy połączony z inną bazą danych.</span><span class="sxs-lookup"><span data-stu-id="4cc88-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="4cc88-116">Aby zmienić źródło danych programowo</span><span class="sxs-lookup"><span data-stu-id="4cc88-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="4cc88-117">Ustaw <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę na nazwę źródła danych i tabeli, z którą chcesz się powiązać.</span><span class="sxs-lookup"><span data-stu-id="4cc88-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="4cc88-118">Poniższy przykład pokazuje, jak zmienić <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> źródło daty przy użyciu metody na formant danych ADO.NET (adoPubsAuthors), który jest połączony z tabeli Autorzy w bazie danych pubów.</span><span class="sxs-lookup"><span data-stu-id="4cc88-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4cc88-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4cc88-119">See also</span></span>

- [<span data-ttu-id="4cc88-120">Zestawy danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4cc88-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="4cc88-121">Porady: usuwanie lub ukrywanie kolumn w formancie DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4cc88-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="4cc88-122">Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4cc88-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="4cc88-123">Instrukcje: powiązywanie kontrolki DataGrid formularzy Windows Forms ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="4cc88-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
