---
title: Wydajność widoku danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: 41b9e51e804d88227b8812124d25eae21838fc6d
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610453"
---
# <a name="dataview-performance"></a><span data-ttu-id="7c8b1-102">Wydajność widoku danych</span><span class="sxs-lookup"><span data-stu-id="7c8b1-102">DataView Performance</span></span>
<span data-ttu-id="7c8b1-103">W tym temacie omówiono zalety wydajności przy użyciu <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView> klasy i buforowania <xref:System.Data.DataView> w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="7c8b1-104">Znajdź i FindRows</span><span class="sxs-lookup"><span data-stu-id="7c8b1-104">Find and FindRows</span></span>  
 <span data-ttu-id="7c8b1-105"><xref:System.Data.DataView> Tworzy indeks.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-105"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="7c8b1-106">Indeks zawiera klucze utworzona na podstawie co najmniej jedną kolumnę w tabeli lub widoku.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="7c8b1-107">Te klucze są przechowywane w strukturze, która umożliwia <xref:System.Data.DataView> można znaleźć wiersze skojarzonych wartości klucza, szybkie i skuteczne.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="7c8b1-108">Operacje korzystające z indeksu, takich jak filtrowanie i sortowanie, zobacz zwiększa istotnie poprawiającą wydajność.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-108">Operations that use the index, such as filtering and sorting, see significant performance increases.</span></span> <span data-ttu-id="7c8b1-109">Indeks <xref:System.Data.DataView> powstała zarówno gdy <xref:System.Data.DataView> jest tworzony i gdy którykolwiek z sortowania lub filtrowania informacji jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="7c8b1-110">Tworzenie <xref:System.Data.DataView> , a następnie ustawienie sortowania lub filtrowania informacje później powoduje indeks ma zostać utworzony co najmniej dwa razy: po podczas <xref:System.Data.DataView> zostanie utworzony, i ponownie podczas sortowania lub filtrowania właściwości są modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="7c8b1-111">Aby uzyskać więcej informacji na temat filtrowania i sortowania z <xref:System.Data.DataView>, zobacz [Filtrowanie za pomocą widoku danych](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) i [sortowanie za pomocą widoku danych](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="7c8b1-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="7c8b1-112">Jeśli mają być zwracane wyniki zapytania określonego na danych, w przeciwieństwie do realizacji dynamiczny widok podzbiór danych, można użyć <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>, zamiast ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="7c8b1-113"><xref:System.Data.DataView.RowFilter%2A> Właściwość najlepiej sprawdza się w aplikacji powiązanych z danymi gdzie powiązanej kontrolki Wyświetla wyfiltrowanych wyników.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="7c8b1-114">Ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwość odbudowania indeksu dla danych, obciążenie dodawanie do aplikacji i zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="7c8b1-115"><xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metody używać bieżącego indeksu bez konieczności indeks odbudowany.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="7c8b1-116">Jeśli wywołanie <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> tylko raz, użyj istniejącego <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="7c8b1-117">Jeśli wywołanie <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> wielokrotnie, należy utworzyć nową <xref:System.Data.DataView> do odbudowania indeksu w kolumnie, aby wyszukać, a następnie wywołaj <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="7c8b1-118">Aby uzyskać więcej informacji na temat <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metod, zobacz [znajdowanie wierszy](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="7c8b1-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="7c8b1-119">W poniższym przykładzie użyto <xref:System.Data.DataView.Find%2A> metody do znalezienia kontaktu o nazwisku "Zhu".</span><span class="sxs-lookup"><span data-stu-id="7c8b1-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="7c8b1-120">W poniższym przykładzie użyto <xref:System.Data.DataView.FindRows%2A> metody do znalezienia wszystkich red pokolorowane produktów.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="7c8b1-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7c8b1-121">ASP.NET</span></span>  
 <span data-ttu-id="7c8b1-122">Program ASP.NET ma mechanizm buforowania, która umożliwia przechowywanie obiektów, które wymagają zasobów rozbudowane serwera do tworzenia w pamięci.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="7c8b1-123">Buforowanie tych typów zasobów może znacznie poprawić wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="7c8b1-124">Pamięć podręczna jest implementowana przez <xref:System.Web.Caching.Cache> klasy z wystąpienia pamięci podręcznej, które są prywatne dla każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="7c8b1-125">Ponieważ utworzenie nowego <xref:System.Data.DataView> obiekt może być dużej ilości zasobów, można skorzystać z tej funkcji w aplikacjach sieci Web buforowania, aby <xref:System.Data.DataView> nie trzeba odbudować, za każdym razem, gdy strona sieci Web zostanie odświeżona.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="7c8b1-126">W poniższym przykładzie <xref:System.Data.DataView> są buforowane, dzięki czemu dane nie trzeba ponownie posortowane po odświeżeniu strony.</span><span class="sxs-lookup"><span data-stu-id="7c8b1-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c8b1-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c8b1-127">See Also</span></span>  
 [<span data-ttu-id="7c8b1-128">Powiązanie danych i LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="7c8b1-128">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
