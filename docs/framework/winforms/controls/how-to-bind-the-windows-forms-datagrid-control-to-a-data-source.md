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
ms.openlocfilehash: 920a93894cc126f85bc6b618efbe6e9cedea4881
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666433"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source"></a><span data-ttu-id="8c1ec-102">Instrukcje: wiązanie kontrolki DataGrid formularzy systemu Windows ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="8c1ec-102">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>
> [!NOTE]
>  <span data-ttu-id="8c1ec-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="8c1ec-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="8c1ec-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="8c1ec-105">Formularze Windows <xref:System.Windows.Forms.DataGrid> kontroli jest specjalnie przeznaczona do wyświetlania informacji ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-105">The Windows Forms <xref:System.Windows.Forms.DataGrid> control is specifically designed to display information from a data source.</span></span> <span data-ttu-id="8c1ec-106">Powiązywanie formantu w czasie wykonywania, wywołując <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-106">You bind the control at run time by calling the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span> <span data-ttu-id="8c1ec-107">Choć można wyświetlać dane z różnych źródeł danych, najbardziej typowe źródła są zestawy danych i widokami danych.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-107">Although you can display data from a variety of data sources, the most typical sources are datasets and data views.</span></span>  
  
### <a name="to-data-bind-the-datagrid-control-programmatically"></a><span data-ttu-id="8c1ec-108">Do wiązania danych w formancie DataGrid programowe</span><span class="sxs-lookup"><span data-stu-id="8c1ec-108">To data-bind the DataGrid control programmatically</span></span>  
  
1. <span data-ttu-id="8c1ec-109">Pisz kod, aby wypełnić dataset.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-109">Write code to fill the dataset.</span></span>  
  
     <span data-ttu-id="8c1ec-110">W przypadku zestawu danych lub widoku danych, na podstawie tabeli zestawu danych źródła danych należy dodać kod do formularza, aby wypełnić dataset.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-110">If the data source is a dataset or a data view based on a dataset table, add code to the form to fill the dataset.</span></span>  
  
     <span data-ttu-id="8c1ec-111">Dokładne kod, który możesz użyć zależy od tego, gdzie zestaw danych jest wprowadzenie danych.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-111">The exact code you use depends on where the dataset is getting data.</span></span> <span data-ttu-id="8c1ec-112">Jeśli trwa wypełnianie zestawu danych bezpośrednio z bazy danych, zazwyczaj wywołujesz `Fill` metody w obrębie adaptera danych, jak w poniższym przykładzie, który wypełnia zestaw danych o nazwie `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="8c1ec-112">If the dataset is being populated directly from a database, you typically call the `Fill` method of a data adapter, as in the following example, which populates a dataset called `DsCategories1`:</span></span>  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     <span data-ttu-id="8c1ec-113">Jeśli zestaw danych jest wypełniany z usługi sieci Web XML, zwykle tworzysz wystąpienia usługi w kodzie, a następnie wywołać jedną z jego metod, aby zwrócić zestaw danych.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-113">If the dataset is being filled from an XML Web service, you typically create an instance of the service in your code and then call one of its methods to return a dataset.</span></span> <span data-ttu-id="8c1ec-114">Zestaw danych z usługi sieci Web XML jest następnie Scal do lokalnego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-114">You then merge the dataset from the XML Web service into your local dataset.</span></span> <span data-ttu-id="8c1ec-115">W poniższym przykładzie pokazano, jak utworzyć wystąpienie usługi XML sieci Web o nazwie `CategoriesService`, wywoływanie jej `GetCategories` metoda i scalanie Wynikowy zestaw danych do lokalnego zestawu danych o nazwie `DsCategories1`:</span><span class="sxs-lookup"><span data-stu-id="8c1ec-115">The following example shows how you can create an instance of an XML Web service called `CategoriesService`, call its `GetCategories` method, and merge the resulting dataset into a local dataset called `DsCategories1`:</span></span>  
  
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
  
2. <span data-ttu-id="8c1ec-116">Wywołaj <xref:System.Windows.Forms.DataGrid> kontrolki <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody przekazanie jej w źródle danych i element członkowski danych.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-116">Call the <xref:System.Windows.Forms.DataGrid> control's <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method, passing it the data source and a data member.</span></span> <span data-ttu-id="8c1ec-117">Jeśli jest konieczne jawne przekazywanie element członkowski danych, należy przekazać pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-117">If you do not need to explicitly pass a data member, pass an empty string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8c1ec-118">Siatki są wiązane po raz pierwszy, można ustawić formantu <xref:System.Windows.Forms.DataGrid.DataSource%2A> i <xref:System.Windows.Forms.DataGrid.DataMember%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-118">If you are binding the grid for the first time, you can set the control's <xref:System.Windows.Forms.DataGrid.DataSource%2A> and <xref:System.Windows.Forms.DataGrid.DataMember%2A> properties.</span></span> <span data-ttu-id="8c1ec-119">Jednak nie można zresetować te właściwości, gdy zostały ustawione.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-119">However, you cannot reset these properties once they have been set.</span></span> <span data-ttu-id="8c1ec-120">Dlatego zalecane jest, aby zawsze używać <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-120">Therefore, it is recommended that you always use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method.</span></span>  
  
     <span data-ttu-id="8c1ec-121">W poniższym przykładzie pokazano, jak można programowo powiązać tabelę Klienci w zestawie danych o nazwie `DsCustomers1`:</span><span class="sxs-lookup"><span data-stu-id="8c1ec-121">The following example shows how you can programmatically bind to the Customers table in a dataset called `DsCustomers1`:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     <span data-ttu-id="8c1ec-122">Jeśli klienci jest tylko tabela w zestawie danych, można też powiążesz siatki w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="8c1ec-122">If the Customers table is the only table in the dataset, you could alternatively bind the grid this way:</span></span>  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3. <span data-ttu-id="8c1ec-123">(Opcjonalnie) Dodaj style odpowiedniej tabeli i kolumn do siatki.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-123">(Optional) Add the appropriate table styles and column styles to the grid.</span></span> <span data-ttu-id="8c1ec-124">Jeśli nie ma żadnych style tabeli, tabeli, zostanie wyświetlony, ale z minimalnym formatowania i widoczne dla wszystkich kolumn.</span><span class="sxs-lookup"><span data-stu-id="8c1ec-124">If there are no table styles, you will see the table, but with minimal formatting and with all columns visible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c1ec-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c1ec-125">See also</span></span>

- [<span data-ttu-id="8c1ec-126">DataGrid, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="8c1ec-126">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="8c1ec-127">Instrukcje: Dodawanie tabel i kolumn do kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c1ec-127">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [<span data-ttu-id="8c1ec-128">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="8c1ec-128">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="8c1ec-129">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8c1ec-129">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
