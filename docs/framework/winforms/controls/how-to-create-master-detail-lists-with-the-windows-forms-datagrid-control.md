---
title: 'Instrukcje: Tworzenie list wzorzec / szczegół za pomocą kontrolki DataGrid formularzy Windows Forms'
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
ms.openlocfilehash: 6ff13264709c4557d698435ac05b7759be58f1e8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712895"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a><span data-ttu-id="88856-102">Instrukcje: Tworzenie list wzorzec/szczegół za pomocą kontrolki DataGrid formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88856-102">How to: Create Master/Detail Lists with the Windows Forms DataGrid Control</span></span>
> [!NOTE]
>  <span data-ttu-id="88856-103"><xref:System.Windows.Forms.DataGridView> Kontroli zastępuje i dodaje funkcjonalność do <xref:System.Windows.Forms.DataGrid> kontrolować; jednak <xref:System.Windows.Forms.DataGrid> kontrolki została zachowana na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="88856-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="88856-104">Aby uzyskać więcej informacji, zobacz [różnice między Windows Forms formantami DataGridView i DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="88856-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="88856-105">Jeśli Twoje <xref:System.Data.DataSet> zawiera serię powiązane tabele, możesz użyć dwóch <xref:System.Windows.Forms.DataGrid> formantów do wyświetlania danych w formacie wzorzec/szczegół.</span><span class="sxs-lookup"><span data-stu-id="88856-105">If your <xref:System.Data.DataSet> contains a series of related tables, you can use two <xref:System.Windows.Forms.DataGrid> controls to display the data in a master/detail format.</span></span> <span data-ttu-id="88856-106">Jeden <xref:System.Windows.Forms.DataGrid> wyznaczony jako główny siatki, a drugi jest wyznaczony jako siatka szczegółów.</span><span class="sxs-lookup"><span data-stu-id="88856-106">One <xref:System.Windows.Forms.DataGrid> is designated to be the master grid, and the second is designated to be the details grid.</span></span> <span data-ttu-id="88856-107">Po wybraniu wpisu na liście głównej wszystkich wpisów powiązanych podrzędnej liście są wyświetlane szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="88856-107">When you select an entry in the master list, all of the related child entries are shown in the details list.</span></span> <span data-ttu-id="88856-108">Na przykład jeśli Twoja <xref:System.Data.DataSet> zawiera tabelę Klienci i powiązanej tabeli z zamówieniami, należy określić tabelę Klienci do głównej siatki i na tabeli Orders siatka szczegółów.</span><span class="sxs-lookup"><span data-stu-id="88856-108">For example, if your <xref:System.Data.DataSet> contains a Customers table and a related Orders table, you would specify the Customers table to be the master grid and the Orders table to be the details grid.</span></span> <span data-ttu-id="88856-109">Po wybraniu odbiorcy z siatki głównej wszystkich zamówień skojarzonych z klientem w tabeli zamówienia będzie wyświetlana w siatce szczegółów.</span><span class="sxs-lookup"><span data-stu-id="88856-109">When a customer is selected from the master grid, all of the orders associated with that customer in the Orders table would be displayed in the details grid.</span></span>  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a><span data-ttu-id="88856-110">Aby programowo ustawić relacji wzorzec/szczegół</span><span class="sxs-lookup"><span data-stu-id="88856-110">To set a master/detail relationship programmatically</span></span>  
  
1.  <span data-ttu-id="88856-111">Utworzyć dwa nowe <xref:System.Windows.Forms.DataGrid> kontroluje i ustawiać ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="88856-111">Create two new <xref:System.Windows.Forms.DataGrid> controls and set their properties.</span></span>  
  
2.  <span data-ttu-id="88856-112">Dodawanie tabel do zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="88856-112">Add tables to the dataset.</span></span>  
  
3.  <span data-ttu-id="88856-113">Zadeklaruj zmienną typu <xref:System.Data.DataRelation> do reprezentowania relacji, którą chcesz utworzyć.</span><span class="sxs-lookup"><span data-stu-id="88856-113">Declare a variable of type <xref:System.Data.DataRelation> to represent the relation you want to create.</span></span>  
  
4.  <span data-ttu-id="88856-114">Utwórz wystąpienie relacji, określając nazwę relacji i określenie tabeli, kolumny i element, który będzie łączyć dwóch tabel.</span><span class="sxs-lookup"><span data-stu-id="88856-114">Instantiate the relationship by specifying a name for the relationship and specifying the table, column, and item that will tie the two tables.</span></span>  
  
5.  <span data-ttu-id="88856-115">Dodawanie relacji z elementem <xref:System.Data.DataSet> obiektu <xref:System.Data.DataSet.Relations%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="88856-115">Add the relationship to the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Relations%2A> collection.</span></span>  
  
6.  <span data-ttu-id="88856-116">Użyj <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> metody <xref:System.Windows.Forms.DataGrid> każdego siatki, aby powiązać <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="88856-116">Use the <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> method of the <xref:System.Windows.Forms.DataGrid> to bind each of the grids to the <xref:System.Data.DataSet>.</span></span>  
  
     <span data-ttu-id="88856-117">Poniższy przykład pokazuje, jak ustawić relacji wzorzec/szczegół tabel Klienci i zamówienia w wcześniej wygenerowany <xref:System.Data.DataSet> (`ds`).</span><span class="sxs-lookup"><span data-stu-id="88856-117">The following example shows how to set a master/detail relationship between the Customers and Orders tables in a previously generated <xref:System.Data.DataSet> (`ds`).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88856-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88856-118">See also</span></span>
- [<span data-ttu-id="88856-119">DataGrid, kontrolka</span><span class="sxs-lookup"><span data-stu-id="88856-119">DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
- [<span data-ttu-id="88856-120">DataGrid, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="88856-120">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)
- [<span data-ttu-id="88856-121">Instrukcje: Powiązywanie formantu DataGrid formularzy Windows ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="88856-121">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
