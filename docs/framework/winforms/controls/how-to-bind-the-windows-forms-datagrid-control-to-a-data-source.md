---
title: 'Instrukcje: wiązanie kontrolki DataGrid formularzy systemu Windows ze źródłem danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- bound controls [Windows Forms], DataGrid control
- Windows Forms controls, data binding
- bound controls [Windows Forms]
- data-bound controls [Windows Forms], DataGrid
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
ms.openlocfilehash: bac24c2dd622ea780408e902d08708ac09561044
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922726"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="e1351-102">Instrukcje: wiązanie kontrolki DataGrid formularzy systemu Windows ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="e1351-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
> <span data-ttu-id="e1351-103">Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="e1351-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="e1351-104">Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e1351-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="e1351-105">Formant Windows Forms <xref:System.Windows.Forms.DataGrid> jest specjalnie zaprojektowany do wyświetlania informacji ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="e1351-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="e1351-106">Można powiązać formant w czasie wykonywania, wywołując <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="e1351-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="e1351-107">Mimo że można wyświetlać dane z różnych źródeł danych, najbardziej typowe źródła to zestawy danych i ich widoki.</span><span class="sxs-lookup"><span data-stu-id="e1351-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="e1351-108">W celu programowego powiązania formantu DataGrid z danymi</span><span class="sxs-lookup"><span data-stu-id="e1351-108">To data-bind the DataGrid control programmatically</span></span>  
  
1. <span data-ttu-id="e1351-109">Napisz kod, aby wypełnić zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="e1351-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="e1351-110">Jeśli źródłem danych jest zestaw danych lub widok danych oparty na tabeli zestawu danych, Dodaj kod do formularza, aby wypełnić zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="e1351-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="e1351-111">Dokładny kod, którego używasz, zależy od tego, gdzie zestaw danych pobiera dane.</span><span class="sxs-lookup"><span data-stu-id="e1351-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="e1351-112">Jeśli zestaw danych jest wypełniany bezpośrednio z bazy danych, zazwyczaj wywoływana jest `Fill` Metoda adaptera danych, tak jak w poniższym przykładzie, który wypełnia zestaw danych o nazwie: `DsCategories1`</span><span class="sxs-lookup"><span data-stu-id="e1351-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="e1351-113">Jeśli zestaw danych jest wypełniany z poziomu usługi sieci Web XML, zazwyczaj tworzysz wystąpienie usługi w kodzie, a następnie Wywołaj jedną z jej metod, aby zwrócić zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="e1351-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="e1351-114">Następnie należy scalić zestaw danych z usługi sieci Web XML do lokalnego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="e1351-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="e1351-115">W poniższym przykładzie pokazano, jak utworzyć wystąpienie usługi sieci Web XML o nazwie `CategoriesService`, `GetCategories` wywołać metodę i scalić zestaw danych w lokalnym zestawie danych o nazwie `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="e1351-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =   
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2. <span data-ttu-id="e1351-116">Wywołaj <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metodę kontrolki,przekazującjądoźródładanychielementuczłonkowskiegodanych.<xref:System.Windows.Forms.DataGrid></span><span class="sxs-lookup"><span data-stu-id="e1351-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="e1351-117">Jeśli nie musisz jawnie przekazać elementu członkowskiego danych, Przekaż pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="e1351-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e1351-118">Jeśli powiążesz siatkę po raz pierwszy, możesz ustawić kontrolkę <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> jej właściwości.</span><span class="sxs-lookup"><span data-stu-id="e1351-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="e1351-119">Nie można jednak resetować tych właściwości po ich ustawieniu.</span><span class="sxs-lookup"><span data-stu-id="e1351-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="e1351-120">Dlatego zaleca się, aby zawsze używać <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e1351-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="e1351-121">Poniższy przykład pokazuje, jak można programowo powiązać z tabelą Customers w zestawie danych o nazwie `DsCustomers1`:</span><span class="sxs-lookup"><span data-stu-id="e1351-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="e1351-122">Jeśli tabela Customers jest jedyną tabelą w zestawie danych, możesz alternatywnie powiązać siatkę w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e1351-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. <span data-ttu-id="e1351-123">Obowiązkowe Dodaj odpowiednie style tabeli i Style kolumn do siatki.</span><span class="sxs-lookup"><span data-stu-id="e1351-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="e1351-124">Jeśli nie ma żadnych stylów tabeli, zostanie wyświetlona tabela, ale z minimalnym formatowaniem i wszystkimi kolumnami widocznymi.</span><span class="sxs-lookup"><span data-stu-id="e1351-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1351-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1351-125">See also</span></span>

- [<span data-ttu-id="e1351-126">DataGrid, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="e1351-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="e1351-127">Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1351-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="e1351-128">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="e1351-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="e1351-129">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1351-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
