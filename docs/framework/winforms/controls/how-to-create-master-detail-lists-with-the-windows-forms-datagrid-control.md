---
title: 'Instrukcje: Tworzenie list wzorzec-szczegół za pomocą kontrolki DataGrid Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
ms.openlocfilehash: f0fd95cf0cd66e9a5105c0b8ff77d8c536a5822d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914765"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="b9ccd-102">Instrukcje: tworzenie list wzorzec/szczegół za pomocą kontrolki DataGrid formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b9ccd-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
> <span data-ttu-id="b9ccd-103">Formant zastępuje i dodaje funkcję <xref:System.Windows.Forms.DataGrid> do <xref:System.Windows.Forms.DataGrid> kontrolki; jednak kontrolka jest zachowywana w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="b9ccd-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="b9ccd-104">Aby uzyskać więcej informacji, zobacz [różnice między kontrolkami DataGridView i DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b9ccd-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="b9ccd-105">Jeśli zawiera serię powiązanych tabel, można użyć dwóch <xref:System.Windows.Forms.DataGrid> kontrolek do wyświetlania danych w formacie wzorzec/szczegóły. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="b9ccd-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="b9ccd-106"><xref:System.Windows.Forms.DataGrid> Wyznaczono ją jako siatkę główną, a druga wyznaczono jako siatkę szczegółów.</span><span class="sxs-lookup"><span data-stu-id="b9ccd-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="b9ccd-107">Po wybraniu wpisu na liście głównej wszystkie powiązane wpisy podrzędne zostaną wyświetlone na liście szczegóły.</span><span class="sxs-lookup"><span data-stu-id="b9ccd-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="b9ccd-108">Na przykład, jeśli <xref:System.Data.DataSet> zawiera tabelę Customers i powiązanej tabeli Orders, należy określić tabelę Customers jako siatkę główną oraz tabelę Orders, która będzie siatką szczegółów.</span><span class="sxs-lookup"><span data-stu-id="b9ccd-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="b9ccd-109">Po wybraniu klienta z siatki głównej wszystkie zamówienia powiązane z tym klientem w tabeli Orders będą wyświetlane w siatce szczegółów.</span><span class="sxs-lookup"><span data-stu-id="b9ccd-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="b9ccd-110">Aby programowo ustawić relację wzorzec/szczegóły</span><span class="sxs-lookup"><span data-stu-id="b9ccd-110">To set a master/detail relationship programmatically</span></span>  
  
1. <span data-ttu-id="b9ccd-111">Utwórz dwie nowe <xref:System.Windows.Forms.DataGrid> kontrolki i ustaw ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="b9ccd-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2. <span data-ttu-id="b9ccd-112">Dodaj tabele do zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="b9ccd-112">Add tables to the dataset.</span></span>  
  
3. <span data-ttu-id="b9ccd-113">Zadeklaruj zmienną typu <xref:System.Data.DataRelation> reprezentującą relację, którą chcesz utworzyć.</span><span class="sxs-lookup"><span data-stu-id="b9ccd-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4. <span data-ttu-id="b9ccd-114">Utwórz wystąpienie relacji przez określenie nazwy relacji i określenie tabeli, kolumny i elementu, który będzie łączyć dwie tabele.</span><span class="sxs-lookup"><span data-stu-id="b9ccd-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5. <span data-ttu-id="b9ccd-115">Dodaj relację do <xref:System.Data.DataSet> <xref:System.Data.DataSet.Relations%2A> kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="b9ccd-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6. <span data-ttu-id="b9ccd-116">Użyj metody, <xref:System.Windows.Forms.DataGrid> aby powiązać wszystkie siatki z <xref:System.Data.DataSet>. <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A></span><span class="sxs-lookup"><span data-stu-id="b9ccd-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="b9ccd-117">Poniższy przykład pokazuje, jak ustawić relację wzorzec/szczegóły między tabelami Customers i Orders w wcześniej <xref:System.Data.DataSet> wygenerowanym`ds`().</span><span class="sxs-lookup"><span data-stu-id="b9ccd-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b9ccd-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9ccd-118">See also</span></span>

- [<span data-ttu-id="b9ccd-119">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="b9ccd-119">DataGrid Control</span></span>](datagrid-control-windows-forms.md)
- [<span data-ttu-id="b9ccd-120">DataGrid, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="b9ccd-120">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="b9ccd-121">Instrukcje: Powiązywanie kontrolki DataGrid Windows Forms ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="b9ccd-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
