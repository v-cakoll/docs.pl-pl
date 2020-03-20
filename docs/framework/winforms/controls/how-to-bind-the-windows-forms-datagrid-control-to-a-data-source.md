---
title: Powiąż formant datagrid ze źródłem danych
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
ms.openlocfilehash: 42514c6a0ab9cf912a32b13675a069976632ece5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182242"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="9fe5d-102">Porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="9fe5d-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
> <span data-ttu-id="9fe5d-103">Formant <xref:System.Windows.Forms.DataGridView> zastępuje i dodaje funkcjonalność <xref:System.Windows.Forms.DataGrid> do formantu; jednak <xref:System.Windows.Forms.DataGrid> formant jest zachowywany zarówno dla zgodności z powrotem i przyszłego użycia, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="9fe5d-104">Aby uzyskać więcej informacji, zobacz [Różnice między formami Windows DataGridView i DataGrid Formantów](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="9fe5d-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="9fe5d-105">Formant <xref:System.Windows.Forms.DataGrid> Formularze systemu Windows został specjalnie zaprojektowany do wyświetlania informacji ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="9fe5d-106">Formant należy powiązać w <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> czasie wykonywania, wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="9fe5d-107">Chociaż można wyświetlać dane z różnych źródeł danych, najbardziej typowe źródła to zestawy danych i widoki danych.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="9fe5d-108">Aby programowo powiązać dane, formant DataGrid</span><span class="sxs-lookup"><span data-stu-id="9fe5d-108">To data-bind the DataGrid control programmatically</span></span>  
  
1. <span data-ttu-id="9fe5d-109">Napisz kod, aby wypełnić zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="9fe5d-110">Jeśli źródłem danych jest zestaw danych lub widok danych oparty na tabeli zestawu danych, dodaj kod do formularza, aby wypełnić zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="9fe5d-111">Dokładny kod, którego używasz, zależy od tego, gdzie zestaw danych jest pobieranie danych.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="9fe5d-112">Jeśli zestaw danych jest wypełniany bezpośrednio z bazy danych, zazwyczaj wywołana `Fill` jest metoda karty danych, jak w `DsCategories1`poniższym przykładzie, która wypełnia zestaw danych o nazwie:</span><span class="sxs-lookup"><span data-stu-id="9fe5d-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="9fe5d-113">Jeśli zestaw danych jest wypełniany z usługi sieci Web XML, zazwyczaj tworzy się wystąpienie usługi w kodzie, a następnie wywołanie jednej z jego metod, aby zwrócić zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="9fe5d-114">Następnie należy scalić zestaw danych z usługi sieci Web XML z lokalnym zestawem danych.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="9fe5d-115">Poniższy przykład pokazuje, jak można utworzyć wystąpienie `CategoriesService`usługi sieci `GetCategories` Web XML o nazwie , wywołać `DsCategories1`jego metodę i scalić wynikowy zestaw danych do lokalnego zestawu danych o nazwie:</span><span class="sxs-lookup"><span data-stu-id="9fe5d-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
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
  
2. <span data-ttu-id="9fe5d-116">Wywołanie <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody formantu, przekazując ją źródło danych i element członkowski danych.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="9fe5d-117">Jeśli nie trzeba jawnie przekazać element członkowski danych, przekazać pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9fe5d-118">Jeśli są wiązanie siatki po raz pierwszy, można <xref:System.Windows.Forms.DataGrid.DataSource%2A> <xref:System.Windows.Forms.DataGrid.DataMember%2A> ustawić formantu i właściwości.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="9fe5d-119">Jednak nie można zresetować te właściwości po ich ustawieniu.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="9fe5d-120">W związku z tym zaleca się, aby zawsze używać <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="9fe5d-121">W poniższym przykładzie pokazano, jak programowo można powiązać `DsCustomers1`z tabelą Klienci w zestawie danych o nazwie:</span><span class="sxs-lookup"><span data-stu-id="9fe5d-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="9fe5d-122">Jeśli tabela Klienci jest jedyną tabelą w zestawie danych, można alternatywnie powiązać siatkę w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="9fe5d-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. <span data-ttu-id="9fe5d-123">(Opcjonalnie) Dodaj odpowiednie style tabel i style kolumn do siatki.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="9fe5d-124">Jeśli nie ma żadnych stylów tabeli, zobaczysz tabelę, ale z minimalnym formatowaniem i widocznymi wszystkimi kolumnami.</span><span class="sxs-lookup"><span data-stu-id="9fe5d-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe5d-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fe5d-125">See also</span></span>

- [<span data-ttu-id="9fe5d-126">DataGrid, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="9fe5d-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="9fe5d-127">Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9fe5d-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="9fe5d-128">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="9fe5d-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="9fe5d-129">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9fe5d-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
