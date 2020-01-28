---
title: Powiązywanie formantu DataGrid ze źródłem danych
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
ms.openlocfilehash: 2634a6bd8ace36bcf7a49120162474a8c04b2b83
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746684"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="9208f-102">Porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="9208f-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
> <span data-ttu-id="9208f-103">Formant <xref:System.Windows.Forms.DataGridView> zamienia i dodaje funkcje do kontrolki <xref:System.Windows.Forms.DataGrid>; Niemniej jednak kontrolka <xref:System.Windows.Forms.DataGrid> jest zachowywana na potrzeby zgodności z poprzednimi wersjami i w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="9208f-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="9208f-104">Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="9208f-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="9208f-105">Kontrolka <xref:System.Windows.Forms.DataGrid> Windows Forms jest przeznaczona specjalnie do wyświetlania informacji ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="9208f-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="9208f-106">Można powiązać formant w czasie wykonywania, wywołując metodę <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="9208f-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="9208f-107">Mimo że można wyświetlać dane z różnych źródeł danych, najbardziej typowe źródła to zestawy danych i ich widoki.</span><span class="sxs-lookup"><span data-stu-id="9208f-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="9208f-108">W celu programowego powiązania formantu DataGrid z danymi</span><span class="sxs-lookup"><span data-stu-id="9208f-108">To data-bind the DataGrid control programmatically</span></span>  
  
1. <span data-ttu-id="9208f-109">Napisz kod, aby wypełnić zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="9208f-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="9208f-110">Jeśli źródłem danych jest zestaw danych lub widok danych oparty na tabeli zestawu danych, Dodaj kod do formularza, aby wypełnić zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="9208f-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="9208f-111">Dokładny kod, którego używasz, zależy od tego, gdzie zestaw danych pobiera dane.</span><span class="sxs-lookup"><span data-stu-id="9208f-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="9208f-112">Jeśli zestaw danych jest wypełniany bezpośrednio z bazy danych, zazwyczaj wywoływana jest metoda `Fill` adaptera danych, tak jak w poniższym przykładzie, który wypełnia zestaw danych o nazwie `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="9208f-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="9208f-113">Jeśli zestaw danych jest wypełniany z poziomu usługi sieci Web XML, zazwyczaj tworzysz wystąpienie usługi w kodzie, a następnie Wywołaj jedną z jej metod, aby zwrócić zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="9208f-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="9208f-114">Następnie należy scalić zestaw danych z usługi sieci Web XML do lokalnego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="9208f-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="9208f-115">Poniższy przykład pokazuje, jak utworzyć wystąpienie usługi sieci Web XML o nazwie `CategoriesService`, wywołać metodę `GetCategories` i scalić zestaw danych z lokalnym zestawem danych o nazwie `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="9208f-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
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
  
2. <span data-ttu-id="9208f-116">Wywołaj metodę <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> formantu <xref:System.Windows.Forms.DataGrid>, przekazując ją do źródła danych i elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="9208f-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="9208f-117">Jeśli nie musisz jawnie przekazać elementu członkowskiego danych, Przekaż pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="9208f-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9208f-118">Jeśli powiążesz siatkę po raz pierwszy, możesz ustawić właściwości <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> formantu.</span><span class="sxs-lookup"><span data-stu-id="9208f-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="9208f-119">Nie można jednak resetować tych właściwości po ich ustawieniu.</span><span class="sxs-lookup"><span data-stu-id="9208f-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="9208f-120">Dlatego zaleca się, aby zawsze używać metody <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>.</span><span class="sxs-lookup"><span data-stu-id="9208f-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="9208f-121">Poniższy przykład pokazuje, jak można programowo powiązać z tabelą Customers w zestawie danych o nazwie `DsCustomers1`:</span><span class="sxs-lookup"><span data-stu-id="9208f-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="9208f-122">Jeśli tabela Customers jest jedyną tabelą w zestawie danych, możesz alternatywnie powiązać siatkę w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9208f-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. <span data-ttu-id="9208f-123">Obowiązkowe Dodaj odpowiednie style tabeli i Style kolumn do siatki.</span><span class="sxs-lookup"><span data-stu-id="9208f-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="9208f-124">Jeśli nie ma żadnych stylów tabeli, zostanie wyświetlona tabela, ale z minimalnym formatowaniem i wszystkimi kolumnami widocznymi.</span><span class="sxs-lookup"><span data-stu-id="9208f-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9208f-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9208f-125">See also</span></span>

- [<span data-ttu-id="9208f-126">DataGrid, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="9208f-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="9208f-127">Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9208f-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="9208f-128">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="9208f-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="9208f-129">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9208f-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
