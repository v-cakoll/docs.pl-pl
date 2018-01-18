---
title: "Widok danych wydajności"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0858dec79f17906647a3244eb1686e91e53ac48d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="dataview-performance"></a><span data-ttu-id="8cb14-102">Widok danych wydajności</span><span class="sxs-lookup"><span data-stu-id="8cb14-102">DataView Performance</span></span>
<span data-ttu-id="8cb14-103">W tym temacie omówiono wydajności korzyści wynikające ze stosowania <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView> klasy i buforowania <xref:System.Data.DataView> w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8cb14-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="8cb14-104">Znajdź i FindRows</span><span class="sxs-lookup"><span data-stu-id="8cb14-104">Find and FindRows</span></span>  
 <span data-ttu-id="8cb14-105"><xref:System.Data.DataView>Tworzy indeks.</span><span class="sxs-lookup"><span data-stu-id="8cb14-105"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="8cb14-106">Indeks zawiera klucze zbudowane na podstawie co najmniej jedną kolumnę w tabeli lub widoku.</span><span class="sxs-lookup"><span data-stu-id="8cb14-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="8cb14-107">Klucze te są przechowywane w strukturze, która umożliwia <xref:System.Data.DataView> można znaleźć wiersze skojarzone z wartości klucza, szybkie i skuteczne.</span><span class="sxs-lookup"><span data-stu-id="8cb14-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="8cb14-108">Operacji korzystających z indeksu, na przykład filtrowanie i sortowanie, zobacz signifcant zwiększa wydajność.</span><span class="sxs-lookup"><span data-stu-id="8cb14-108">Operations that use the index, such as filtering and sorting, see signifcant performance increases.</span></span> <span data-ttu-id="8cb14-109">Indeks <xref:System.Data.DataView> składa się zarówno w przypadku <xref:System.Data.DataView> jest tworzony i podczas sortowania i filtrowania informacji jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="8cb14-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="8cb14-110">Tworzenie <xref:System.Data.DataView> , a następnie ustawienie sortowania i filtrowania informacje później powoduje indeksu, który ma zostać utworzony co najmniej dwa razy: po podczas <xref:System.Data.DataView> jest tworzony, i ponownie gdy dowolne z właściwości sortowania i filtrowania są modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="8cb14-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="8cb14-111">Aby uzyskać więcej informacji dotyczących filtrowania i sortowania z <xref:System.Data.DataView>, zobacz [filtrowanie z DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) i [sortowania z DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="8cb14-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="8cb14-112">Jeśli chcesz zwrócić wyników określonego zapytania na danych, w przeciwieństwie do zapewniające widoku dynamicznego podzbiór danych, można użyć <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>, zamiast ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cb14-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="8cb14-113"><xref:System.Data.DataView.RowFilter%2A> Właściwości najlepiej sprawdza się w aplikacji powiązanych z danymi gdzie powiązanej kontrolki wyświetla filtrowane wyniki.</span><span class="sxs-lookup"><span data-stu-id="8cb14-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="8cb14-114">Ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwości odtwarza indeksu dla danych narzut dodawanie do swojej aplikacji i zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="8cb14-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="8cb14-115"><xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metody używać bieżącego indeksu bez konieczności indeksu, który ma zostać również przebudowany.</span><span class="sxs-lookup"><span data-stu-id="8cb14-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="8cb14-116">Jeśli zamierzasz wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> tylko raz, następnie należy użyć istniejącego <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="8cb14-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="8cb14-117">Jeśli zamierzasz wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> wielokrotnie, należy utworzyć nowy <xref:System.Data.DataView> odbudować indeksu w kolumnie, aby wyszukać, a następnie wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8cb14-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="8cb14-118">Aby uzyskać więcej informacji na temat <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metod, zobacz [znajdowanie wierszy](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="8cb14-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="8cb14-119">W poniższym przykładzie użyto <xref:System.Data.DataView.Find%2A> metody do znalezienia kontaktu z nazwisko "Zhu".</span><span class="sxs-lookup"><span data-stu-id="8cb14-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="8cb14-120">W poniższym przykładzie użyto <xref:System.Data.DataView.FindRows%2A> metody do znalezienia wszystkich czerwony pokolorowane produktów.</span><span class="sxs-lookup"><span data-stu-id="8cb14-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="8cb14-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8cb14-121">ASP.NET</span></span>  
 <span data-ttu-id="8cb14-122">Program ASP.NET ma mechanizm buforowania, która umożliwia przechowywanie obiektów, które wymagają serwera szeroką gamę zasoby do utworzenia w pamięci.</span><span class="sxs-lookup"><span data-stu-id="8cb14-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="8cb14-123">Buforowanie tych typów zasobów może znacznie poprawić wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8cb14-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="8cb14-124">Buforowanie jest implementowany przez <xref:System.Web.Caching.Cache> klasy z wystąpienia pamięci podręcznej, które są prywatne dla każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8cb14-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="8cb14-125">Ponieważ tworzenia nowego <xref:System.Data.DataView> obiekt może być ilości zasobów, można użyć tej funkcji buforowania funkcji w aplikacji sieci Web, aby <xref:System.Data.DataView> nie musi zostać również przebudowany w każdym odświeżeniu strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8cb14-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="8cb14-126">W poniższym przykładzie <xref:System.Data.DataView> są buforowane, dzięki czemu nie ma danych do posortowania ponownie po odświeżeniu strony.</span><span class="sxs-lookup"><span data-stu-id="8cb14-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
```vb  
If (Cache("ordersView") = Nothing) Then  
  
Dim dataSet As New DataSet()  
  
   FillDataSet(dataSet)  
  
   Dim orders As DataTable = dataSet.Tables("SalesOrderHeader")  
  
   Dim query = _  
                    From order In orders.AsEnumerable() _  
                    Where order.Field(Of Boolean)("OnlineOrderFlag") = True _  
                    Order By order.Field(Of Decimal)("TotalDue") _  
                    Select order  
  
   Dim view As DataView = query.AsDataView()  
  
   Cache.Insert("ordersView", view)  
  
End If  
  
Dim ordersView = CType(Cache("ordersView"), DataView)  
  
GridView1.DataSource = ordersView  
GridView1.DataBind()  
```  
  
```csharp  
if (Cache["ordersView"] == null)  
{  
   // Fill the DataSet.                  
   DataSet dataSet = FillDataSet();  
  
   DataTable orders = dataSet.Tables["SalesOrderHeader"];  
  
   EnumerableRowCollection<DataRow> query =  
                        from order in orders.AsEnumerable()  
                        where order.Field<bool>("OnlineOrderFlag") == true  
                        orderby order.Field<decimal>("TotalDue")  
                        select order;  
  
   DataView view = query.AsDataView();  
   Cache.Insert("ordersView", view);  
}  
  
DataView ordersView = (DataView)Cache["ordersView"];  
  
GridView1.DataSource = ordersView;  
GridView1.DataBind();  
```  
  
## <a name="see-also"></a><span data-ttu-id="8cb14-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8cb14-127">See Also</span></span>  
 [<span data-ttu-id="8cb14-128">Powiązanie danych i LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="8cb14-128">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
