---
title: Wydajność widoku danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: 7c81619bf4ac6ed084ea63349345dbf3b7f139b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150691"
---
# <a name="dataview-performance"></a><span data-ttu-id="45d37-102">Wydajność widoku danych</span><span class="sxs-lookup"><span data-stu-id="45d37-102">DataView Performance</span></span>
<span data-ttu-id="45d37-103">W tym temacie omówiono korzyści <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> z wydajności <xref:System.Data.DataView> przy użyciu i metody <xref:System.Data.DataView> klasy i buforowania w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="45d37-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="45d37-104">Znajdź i Znajdź Wrows</span><span class="sxs-lookup"><span data-stu-id="45d37-104">Find and FindRows</span></span>  
 <span data-ttu-id="45d37-105"><xref:System.Data.DataView>konstruuje indeks.</span><span class="sxs-lookup"><span data-stu-id="45d37-105"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="45d37-106">Indeks zawiera klucze utworzone z jednej lub więcej kolumn w tabeli lub widoku.</span><span class="sxs-lookup"><span data-stu-id="45d37-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="45d37-107">Te klucze są przechowywane w <xref:System.Data.DataView> strukturze, która umożliwia szybkie i wydajne znajdowanie wiersza lub wierszy skojarzonych z wartościami klucza.</span><span class="sxs-lookup"><span data-stu-id="45d37-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="45d37-108">Operacje korzystające z indeksu, takie jak filtrowanie i sortowanie, zobacz znaczny wzrost wydajności.</span><span class="sxs-lookup"><span data-stu-id="45d37-108">Operations that use the index, such as filtering and sorting, see significant performance increases.</span></span> <span data-ttu-id="45d37-109">Indeks dla <xref:System.Data.DataView> a jest tworzony <xref:System.Data.DataView> zarówno podczas tworzenia, jak i gdy którekolwiek z informacji sortowania lub filtrowania jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="45d37-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="45d37-110"><xref:System.Data.DataView> Tworzenie, a następnie ustawienie informacji sortowania lub filtrowania później powoduje, że indeks <xref:System.Data.DataView> ma być zbudowany co najmniej dwa razy: raz podczas tworzenia i ponownie, gdy którykolwiek z sortowania lub filtru właściwości są modyfikowane.</span><span class="sxs-lookup"><span data-stu-id="45d37-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="45d37-111">Aby uzyskać więcej informacji na <xref:System.Data.DataView>temat filtrowania i sortowania za pomocą programu , zobacz [Filtrowanie za pomocą widoku data i](filtering-with-dataview-linq-to-dataset.md) [sortowanie za pomocą programu DataView](sorting-with-dataview-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="45d37-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="45d37-112">Jeśli chcesz zwrócić wyniki określonej kwerendy na danych, w przeciwieństwie do zapewnienia dynamicznego widoku podzbioru <xref:System.Data.DataView.FindRows%2A> danych, <xref:System.Data.DataView>można użyć <xref:System.Data.DataView.RowFilter%2A> <xref:System.Data.DataView.Find%2A> lub metody , zamiast ustawiania właściwości.</span><span class="sxs-lookup"><span data-stu-id="45d37-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="45d37-113">Właściwość <xref:System.Data.DataView.RowFilter%2A> jest najlepiej używana w aplikacji związanej z danymi, w której formant powiązany wyświetla filtrowane wyniki.</span><span class="sxs-lookup"><span data-stu-id="45d37-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="45d37-114">Ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwości odbudowuje indeks danych, dodając obciążenie do aplikacji i zmniejszając wydajność.</span><span class="sxs-lookup"><span data-stu-id="45d37-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="45d37-115">I <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> metody używać bieżącego indeksu bez konieczności indeksu do przebudowy.</span><span class="sxs-lookup"><span data-stu-id="45d37-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="45d37-116">Jeśli zamierzasz <xref:System.Data.DataView.Find%2A> zadzwonić <xref:System.Data.DataView.FindRows%2A> lub tylko raz, należy <xref:System.Data.DataView>użyć istniejącego .</span><span class="sxs-lookup"><span data-stu-id="45d37-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="45d37-117">Jeśli <xref:System.Data.DataView.Find%2A> zamierzasz wywołać <xref:System.Data.DataView.FindRows%2A> lub wiele razy, <xref:System.Data.DataView> należy utworzyć nowy, aby odbudować indeks w kolumnie, w której chcesz szukać, a następnie wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="45d37-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="45d37-118">Aby uzyskać więcej <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> informacji na temat i metod, zobacz [Znajdowanie wierszy](./dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="45d37-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](./dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="45d37-119">Poniższy przykład używa <xref:System.Data.DataView.Find%2A> metody, aby znaleźć kontakt z nazwiskiem "Zhu".</span><span class="sxs-lookup"><span data-stu-id="45d37-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="45d37-120">W poniższym przykładzie użyto metody, <xref:System.Data.DataView.FindRows%2A> aby znaleźć wszystkie produkty w kolorze czerwonym.</span><span class="sxs-lookup"><span data-stu-id="45d37-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="45d37-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="45d37-121">ASP.NET</span></span>  
 <span data-ttu-id="45d37-122">ASP.NET ma mechanizm buforowania, który umożliwia przechowywanie obiektów, które wymagają rozległych zasobów serwera do utworzenia w pamięci.</span><span class="sxs-lookup"><span data-stu-id="45d37-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="45d37-123">Buforowanie tego typu zasobów może znacznie poprawić wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45d37-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="45d37-124">Buforowanie jest implementowane <xref:System.Web.Caching.Cache> przez klasę, z wystąpień pamięci podręcznej, które są prywatne dla każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45d37-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="45d37-125">Ponieważ tworzenie nowego <xref:System.Data.DataView> obiektu może być intensywnie korzystające z zasobów, można użyć tej <xref:System.Data.DataView> funkcji buforowania w aplikacjach sieci Web, aby nie trzeba było go przebudowywać za każdym razem, gdy strona sieci Web jest odświeżana.</span><span class="sxs-lookup"><span data-stu-id="45d37-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="45d37-126">W poniższym przykładzie <xref:System.Data.DataView> jest buforowane, tak aby dane nie muszą być ponownie sortowane, gdy strona jest odświeżana.</span><span class="sxs-lookup"><span data-stu-id="45d37-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="45d37-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45d37-127">See also</span></span>

- [<span data-ttu-id="45d37-128">Powiązanie danych i LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="45d37-128">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
