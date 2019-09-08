---
title: Wydajność widoku danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: 51ea09965c423f04c220260248c3501e061820cb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784138"
---
# <a name="dataview-performance"></a><span data-ttu-id="a2541-102">Wydajność widoku danych</span><span class="sxs-lookup"><span data-stu-id="a2541-102">DataView Performance</span></span>
<span data-ttu-id="a2541-103">W tym temacie omówiono <xref:System.Data.DataView.Find%2A> zalety korzystania z metod <xref:System.Data.DataView> i <xref:System.Data.DataView.FindRows%2A> klasy oraz buforowanie a <xref:System.Data.DataView> w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a2541-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="a2541-104">Znajdź i FindRows</span><span class="sxs-lookup"><span data-stu-id="a2541-104">Find and FindRows</span></span>  
 <span data-ttu-id="a2541-105"><xref:System.Data.DataView>tworzy indeks.</span><span class="sxs-lookup"><span data-stu-id="a2541-105"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="a2541-106">Indeks zawiera klucze skompilowane z co najmniej jednej kolumny w tabeli lub widoku.</span><span class="sxs-lookup"><span data-stu-id="a2541-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="a2541-107">Klucze te są przechowywane w strukturze, która umożliwia <xref:System.Data.DataView> szybkie i wydajne Znajdowanie wierszy lub wierszy skojarzonych z wartościami klucza.</span><span class="sxs-lookup"><span data-stu-id="a2541-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="a2541-108">Operacje, które używają indeksu, takie jak filtrowanie i sortowanie, zobacz znaczące zwiększenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="a2541-108">Operations that use the index, such as filtering and sorting, see significant performance increases.</span></span> <span data-ttu-id="a2541-109">Indeks dla <xref:System.Data.DataView> obiektu jest kompilowany zarówno <xref:System.Data.DataView> podczas tworzenia, jak i gdy dowolna z informacji o sortowaniu lub filtrowaniu jest modyfikowana.</span><span class="sxs-lookup"><span data-stu-id="a2541-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="a2541-110">Utworzenie a, a następnie ustawienie informacji o sortowaniu lub filtrowaniu później spowoduje, że indeks zostanie skompilowany co najmniej dwa razy <xref:System.Data.DataView> : raz podczas tworzenia i ponownie, gdy właściwości sortowania lub filtrowania są modyfikowane. <xref:System.Data.DataView></span><span class="sxs-lookup"><span data-stu-id="a2541-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="a2541-111">Aby uzyskać więcej informacji o filtrowaniu i <xref:System.Data.DataView>sortowaniu w programie, zobacz [filtrowanie z widokiem](filtering-with-dataview-linq-to-dataset.md) danych i [sortowanie za pomocą widoku](sorting-with-dataview-linq-to-dataset.md)danych.</span><span class="sxs-lookup"><span data-stu-id="a2541-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="a2541-112">Jeśli chcesz zwrócić wyniki konkretnego zapytania dotyczącego danych, w przeciwieństwie do udostępnienia dynamicznego widoku podzbioru danych, <xref:System.Data.DataView.Find%2A> możesz użyć metod <xref:System.Data.DataView>lub <xref:System.Data.DataView.FindRows%2A> zamiast ustawić <xref:System.Data.DataView.RowFilter%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="a2541-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="a2541-113"><xref:System.Data.DataView.RowFilter%2A> Właściwość najlepiej jest używana w aplikacji powiązanej z danymi, gdzie kontrolka powiązania Wyświetla przefiltrowane wyniki.</span><span class="sxs-lookup"><span data-stu-id="a2541-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="a2541-114"><xref:System.Data.DataView.RowFilter%2A> Ustawienie właściwości powoduje odbudowanie indeksu dla danych, dodanie obciążenia do aplikacji i zmniejszenie wydajności.</span><span class="sxs-lookup"><span data-stu-id="a2541-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="a2541-115">Metody <xref:System.Data.DataView.Find%2A> i<xref:System.Data.DataView.FindRows%2A> używają bieżącego indeksu bez konieczności ponownego kompilowania indeksu.</span><span class="sxs-lookup"><span data-stu-id="a2541-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="a2541-116">Jeśli zamierzasz wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> tylko raz, należy użyć istniejącej <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="a2541-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="a2541-117">Jeśli chcesz <xref:System.Data.DataView.Find%2A> wywoływać lub <xref:System.Data.DataView> <xref:System.Data.DataView.FindRows%2A> wiele razy, należy utworzyć nową, aby ponownie skompilować indeks w kolumnie, w której ma zostać wyszukane, a następnie wywołać <xref:System.Data.DataView.Find%2A> metody lub <xref:System.Data.DataView.FindRows%2A> .</span><span class="sxs-lookup"><span data-stu-id="a2541-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="a2541-118">Aby uzyskać więcej informacji o <xref:System.Data.DataView.Find%2A> metodach i <xref:System.Data.DataView.FindRows%2A> , zobacz [Znajdowanie wierszy](./dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="a2541-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](./dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="a2541-119">Poniższy przykład używa metody, <xref:System.Data.DataView.Find%2A> aby znaleźć kontakt z nazwiskiem "Zhu".</span><span class="sxs-lookup"><span data-stu-id="a2541-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="a2541-120">W poniższym przykładzie zastosowano <xref:System.Data.DataView.FindRows%2A> metodę, aby znaleźć wszystkie czerwone kolorowe produkty.</span><span class="sxs-lookup"><span data-stu-id="a2541-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="a2541-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a2541-121">ASP.NET</span></span>  
 <span data-ttu-id="a2541-122">ASP.NET ma mechanizm buforowania, który umożliwia przechowywanie obiektów wymagających rozległych zasobów serwera do tworzenia w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a2541-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="a2541-123">Buforowanie tych typów zasobów może znacząco poprawić wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2541-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="a2541-124">Buforowanie jest implementowane przez <xref:System.Web.Caching.Cache> klasę, z wystąpieniami pamięci podręcznej, które są prywatne dla każdej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2541-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="a2541-125">Ponieważ tworzenie nowego <xref:System.Data.DataView> obiektu może być czasochłonne, warto użyć tej funkcji buforowania w aplikacjach sieci Web, aby <xref:System.Data.DataView> nie trzeba było jej odbudować za każdym razem, gdy strona sieci Web zostanie odświeżona.</span><span class="sxs-lookup"><span data-stu-id="a2541-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="a2541-126">W poniższym przykładzie <xref:System.Data.DataView> znajduje się w pamięci podręcznej, dzięki czemu dane nie muszą być ponownie sortowane po odświeżeniu strony.</span><span class="sxs-lookup"><span data-stu-id="a2541-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2541-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2541-127">See also</span></span>

- [<span data-ttu-id="a2541-128">Powiązanie danych i LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="a2541-128">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
