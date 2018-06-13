---
title: 'Porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych'
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
ms.openlocfilehash: 62f61eb2d294baf007b0b3f749f3cf6b7f4857c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530305"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="a7a29-102">Porady: powiązywanie formantu DataGrid formularzy systemu Windows ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="a7a29-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
>  <span data-ttu-id="a7a29-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="a7a29-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="a7a29-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="a7a29-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="a7a29-105">Formularze systemu Windows <xref:System.Windows.Forms.DataGrid> kontrolki przeznaczone do wyświetlania informacji ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a7a29-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="a7a29-106">Powiązywanie formantu w czasie wykonywania, wywołując <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a7a29-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="a7a29-107">Choć można wyświetlać danych z różnych źródeł danych, najbardziej typowe źródła są widoków danych i zestawów danych.</span><span class="sxs-lookup"><span data-stu-id="a7a29-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="a7a29-108">Do wiązania danych formantu DataGrid programowo</span><span class="sxs-lookup"><span data-stu-id="a7a29-108">To data-bind the DataGrid control programmatically</span></span>  
  
1.  <span data-ttu-id="a7a29-109">Napisać kod, aby wypełnić dataset.</span><span class="sxs-lookup"><span data-stu-id="a7a29-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="a7a29-110">Jeśli źródło danych jest wartość dataset lub widok danych na podstawie tabeli zestawu danych, należy dodać kodu do formularza, aby wypełnić dataset.</span><span class="sxs-lookup"><span data-stu-id="a7a29-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="a7a29-111">Dokładnego kodu, używanego zależy od tego, gdzie zestawu danych jest pobieranie danych.</span><span class="sxs-lookup"><span data-stu-id="a7a29-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="a7a29-112">Jeśli jest on wypełnione zestawu danych bezpośrednio z bazy danych, należy zwykle wywołują `Fill` metody adapter danych, jak w poniższym przykładzie, który wypełnia zestawu danych o nazwie `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="a7a29-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="a7a29-113">Jeśli zestaw danych jest wypełniany z usługi XML sieci Web, należy zwykle utworzenia wystąpienia usługi w kodzie, a następnie wywołać jednej z jego metod do zwrócenia zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="a7a29-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="a7a29-114">Zestaw danych z usługi XML sieci Web jest następnie scalić w lokalnym zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="a7a29-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="a7a29-115">W poniższym przykładzie pokazano, jak można utworzyć wystąpienia usługi XML sieci Web o nazwie `CategoriesService`, wywołaj jego `GetCategories` — metoda i merge Wynikowy zestaw danych do lokalnego zestawu danych o nazwie `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="a7a29-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
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
  
2.  <span data-ttu-id="a7a29-116">Wywołanie <xref:System.Windows.Forms.DataGrid> formantu <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody przekazanie jej przez źródło danych i element członkowski danych.</span><span class="sxs-lookup"><span data-stu-id="a7a29-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="a7a29-117">Jeśli jawnego przesłania element członkowski danych nie jest wymagane, należy przekazać pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="a7a29-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a7a29-118">Siatki są wiązane po raz pierwszy, można ustawić formantu <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a7a29-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="a7a29-119">Jednak te właściwości nie można zresetować po ich ustawieniu.</span><span class="sxs-lookup"><span data-stu-id="a7a29-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="a7a29-120">Dlatego zalecane jest, aby zawsze używać <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a7a29-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="a7a29-121">W poniższym przykładzie pokazano, jak można programowo powiązać tabeli Klienci w zestawie danych o nazwie `DsCustomers1`:</span><span class="sxs-lookup"><span data-stu-id="a7a29-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="a7a29-122">Jeśli klienci jest tylko tabela w zestawie danych, można też powiąże siatki w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="a7a29-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  <span data-ttu-id="a7a29-123">(Opcjonalnie) Dodaj style właściwe tabeli i Style kolumn do tabeli.</span><span class="sxs-lookup"><span data-stu-id="a7a29-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="a7a29-124">Jeśli nie ma żadnych stylów tabeli, zobaczysz tabeli, ale z minimalnym formatowanie i widoczne wszystkie kolumny.</span><span class="sxs-lookup"><span data-stu-id="a7a29-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a29-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7a29-125">See Also</span></span>  
 [<span data-ttu-id="a7a29-126">DataGrid, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="a7a29-126">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [<span data-ttu-id="a7a29-127">Instrukcje: dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a29-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [<span data-ttu-id="a7a29-128">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a7a29-128">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [<span data-ttu-id="a7a29-129">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7a29-129">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)
