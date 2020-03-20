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
# <a name="dataview-performance"></a>Wydajność widoku danych
W tym temacie omówiono korzyści <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> z wydajności <xref:System.Data.DataView> przy użyciu i metody <xref:System.Data.DataView> klasy i buforowania w aplikacji sieci Web.  
  
## <a name="find-and-findrows"></a>Znajdź i Znajdź Wrows  
 <xref:System.Data.DataView>konstruuje indeks. Indeks zawiera klucze utworzone z jednej lub więcej kolumn w tabeli lub widoku. Te klucze są przechowywane w <xref:System.Data.DataView> strukturze, która umożliwia szybkie i wydajne znajdowanie wiersza lub wierszy skojarzonych z wartościami klucza. Operacje korzystające z indeksu, takie jak filtrowanie i sortowanie, zobacz znaczny wzrost wydajności. Indeks dla <xref:System.Data.DataView> a jest tworzony <xref:System.Data.DataView> zarówno podczas tworzenia, jak i gdy którekolwiek z informacji sortowania lub filtrowania jest modyfikowany. <xref:System.Data.DataView> Tworzenie, a następnie ustawienie informacji sortowania lub filtrowania później powoduje, że indeks <xref:System.Data.DataView> ma być zbudowany co najmniej dwa razy: raz podczas tworzenia i ponownie, gdy którykolwiek z sortowania lub filtru właściwości są modyfikowane. Aby uzyskać więcej informacji na <xref:System.Data.DataView>temat filtrowania i sortowania za pomocą programu , zobacz [Filtrowanie za pomocą widoku data i](filtering-with-dataview-linq-to-dataset.md) [sortowanie za pomocą programu DataView](sorting-with-dataview-linq-to-dataset.md).  
  
 Jeśli chcesz zwrócić wyniki określonej kwerendy na danych, w przeciwieństwie do zapewnienia dynamicznego widoku podzbioru <xref:System.Data.DataView.FindRows%2A> danych, <xref:System.Data.DataView>można użyć <xref:System.Data.DataView.RowFilter%2A> <xref:System.Data.DataView.Find%2A> lub metody , zamiast ustawiania właściwości. Właściwość <xref:System.Data.DataView.RowFilter%2A> jest najlepiej używana w aplikacji związanej z danymi, w której formant powiązany wyświetla filtrowane wyniki. Ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwości odbudowuje indeks danych, dodając obciążenie do aplikacji i zmniejszając wydajność. I <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> metody używać bieżącego indeksu bez konieczności indeksu do przebudowy. Jeśli zamierzasz <xref:System.Data.DataView.Find%2A> zadzwonić <xref:System.Data.DataView.FindRows%2A> lub tylko raz, należy <xref:System.Data.DataView>użyć istniejącego . Jeśli <xref:System.Data.DataView.Find%2A> zamierzasz wywołać <xref:System.Data.DataView.FindRows%2A> lub wiele razy, <xref:System.Data.DataView> należy utworzyć nowy, aby odbudować indeks w kolumnie, w której chcesz szukać, a następnie wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody. Aby uzyskać więcej <xref:System.Data.DataView.Find%2A> <xref:System.Data.DataView.FindRows%2A> informacji na temat i metod, zobacz [Znajdowanie wierszy](./dataset-datatable-dataview/finding-rows.md).  
  
 Poniższy przykład używa <xref:System.Data.DataView.Find%2A> metody, aby znaleźć kontakt z nazwiskiem "Zhu".  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 W poniższym przykładzie użyto metody, <xref:System.Data.DataView.FindRows%2A> aby znaleźć wszystkie produkty w kolorze czerwonym.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  
 ASP.NET ma mechanizm buforowania, który umożliwia przechowywanie obiektów, które wymagają rozległych zasobów serwera do utworzenia w pamięci. Buforowanie tego typu zasobów może znacznie poprawić wydajność aplikacji. Buforowanie jest implementowane <xref:System.Web.Caching.Cache> przez klasę, z wystąpień pamięci podręcznej, które są prywatne dla każdej aplikacji. Ponieważ tworzenie nowego <xref:System.Data.DataView> obiektu może być intensywnie korzystające z zasobów, można użyć tej <xref:System.Data.DataView> funkcji buforowania w aplikacjach sieci Web, aby nie trzeba było go przebudowywać za każdym razem, gdy strona sieci Web jest odświeżana.  
  
 W poniższym przykładzie <xref:System.Data.DataView> jest buforowane, tak aby dane nie muszą być ponownie sortowane, gdy strona jest odświeżana.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Powiązanie danych i LINQ to DataSet](data-binding-and-linq-to-dataset.md)
