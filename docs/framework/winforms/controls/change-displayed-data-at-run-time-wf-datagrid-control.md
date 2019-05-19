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
ms.openlocfilehash: 3217680a2bab43124b75529bead97ffcfbb06aea
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882135"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a><span data-ttu-id="69b37-102">Instrukcje: zmienianie wyświetlanych danych w czasie wykonywania w kontrolce DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="69b37-102">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="69b37-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="69b37-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="69b37-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="69b37-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="69b37-105">Po utworzeniu formularze Windows <xref:System.Windows.Forms.DataGrid> przy użyciu funkcje czasu projektowania, również możesz dynamicznie zmieniać elementy <xref:System.Data.DataSet> obiektu siatki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="69b37-105">After you have created a Windows Forms <xref:System.Windows.Forms.DataGrid> using the design-time features, you may also wish to dynamically change elements of the <xref:System.Data.DataSet> object of the grid at run time.</span></span> <span data-ttu-id="69b37-106">Może to obejmować zmiany albo poszczególne wartości w tabeli lub zmienianie źródła danych, który jest powiązany z <xref:System.Windows.Forms.DataGrid> kontroli.</span><span class="sxs-lookup"><span data-stu-id="69b37-106">This can include changes to either individual values of the table or changing which data source is bound to the <xref:System.Windows.Forms.DataGrid> control.</span></span> <span data-ttu-id="69b37-107">Zmiany w poszczególnych wartości są wykonywane za pomocą <xref:System.Data.DataSet> obiektu nie <xref:System.Windows.Forms.DataGrid> kontroli.</span><span class="sxs-lookup"><span data-stu-id="69b37-107">Changes to individual values are done through the <xref:System.Data.DataSet> object, not the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
### <a name="to-change-data-programmatically"></a><span data-ttu-id="69b37-108">Programowe zmienianie danych</span><span class="sxs-lookup"><span data-stu-id="69b37-108">To change data programmatically</span></span>  
  
1. <span data-ttu-id="69b37-109">Określ odpowiednią tabelę z <xref:System.Data.DataSet> obiektu i żądany wiersz pola z tabeli i Ustawianie nowej wartości komórki.</span><span class="sxs-lookup"><span data-stu-id="69b37-109">Specify the desired table from the <xref:System.Data.DataSet> object and the desired row and field from the table and set the cell equal to the new value.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="69b37-110">Aby określić pierwszy spis <xref:System.Data.DataSet> lub pierwszy wiersz w tabeli, użyj wartości 0.</span><span class="sxs-lookup"><span data-stu-id="69b37-110">To specify the first table of the <xref:System.Data.DataSet> or the first row of the table, use 0.</span></span>  
  
     <span data-ttu-id="69b37-111">Poniższy przykład pokazuje, jak zmienić drugi wpis pierwszego wiersza w pierwszej tabeli zestawu danych, klikając `Button1`.</span><span class="sxs-lookup"><span data-stu-id="69b37-111">The following example shows how to change the second entry of the first row of the first table of a dataset by clicking `Button1`.</span></span> <span data-ttu-id="69b37-112"><xref:System.Data.DataSet> (`ds`) I tabele (`0` i `1`) zostały utworzone wcześniej.</span><span class="sxs-lookup"><span data-stu-id="69b37-112">The <xref:System.Data.DataSet> (`ds`) and Tables (`0` and `1`) were previously created.</span></span>  
  
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
  
     <span data-ttu-id="69b37-113">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="69b37-113">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="69b37-114">W czasie, możesz użyć wykonywania <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę, aby powiązać <xref:System.Windows.Forms.DataGrid> kontrolki do innego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="69b37-114">At run time you can use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to bind the <xref:System.Windows.Forms.DataGrid> control to a different data source.</span></span> <span data-ttu-id="69b37-115">Na przykład masz kilka formantów danych ADO.NET, każda jest połączona z inną bazą danych.</span><span class="sxs-lookup"><span data-stu-id="69b37-115">For example, you may have several ADO.NET data controls, each connected to a different database.</span></span>  
  
### <a name="to-change-the-datasource-programmatically"></a><span data-ttu-id="69b37-116">Aby programowo zmienić źródło danych</span><span class="sxs-lookup"><span data-stu-id="69b37-116">To change the DataSource programmatically</span></span>  
  
1. <span data-ttu-id="69b37-117">Ustaw <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę, aby nazwa źródła danych i chcesz powiązać z tabeli.</span><span class="sxs-lookup"><span data-stu-id="69b37-117">Set the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to the name of the data source and table you want to bind to.</span></span>  
  
     <span data-ttu-id="69b37-118">Poniższy przykład pokazuje, jak zmienić źródło daty przy użyciu <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę, aby formant danych ADO.NET (adoPubsAuthors), który jest połączony z tabelą autorów w bazie danych Pubs.</span><span class="sxs-lookup"><span data-stu-id="69b37-118">The following example shows how to change the date source using the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method to an ADO.NET data control (adoPubsAuthors) that is connected to the Authors table in the Pubs database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69b37-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69b37-119">See also</span></span>

- [<span data-ttu-id="69b37-120">Zestawy danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="69b37-120">ADO.NET DataSets</span></span>](../../data/adonet/ado-net-datasets.md)
- [<span data-ttu-id="69b37-121">Instrukcje: Usuń lub ukrywanie kolumn w kontrolce DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="69b37-121">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="69b37-122">Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="69b37-122">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="69b37-123">Instrukcje: Powiązywanie formantu DataGrid formularzy Windows ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="69b37-123">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
