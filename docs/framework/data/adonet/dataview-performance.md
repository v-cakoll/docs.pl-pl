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
# <a name="dataview-performance"></a>Wydajność widoku danych
W tym temacie omówiono <xref:System.Data.DataView.Find%2A> zalety korzystania z metod <xref:System.Data.DataView> i <xref:System.Data.DataView.FindRows%2A> klasy oraz buforowanie a <xref:System.Data.DataView> w aplikacji sieci Web.  
  
## <a name="find-and-findrows"></a>Znajdź i FindRows  
 <xref:System.Data.DataView>tworzy indeks. Indeks zawiera klucze skompilowane z co najmniej jednej kolumny w tabeli lub widoku. Klucze te są przechowywane w strukturze, która umożliwia <xref:System.Data.DataView> szybkie i wydajne Znajdowanie wierszy lub wierszy skojarzonych z wartościami klucza. Operacje, które używają indeksu, takie jak filtrowanie i sortowanie, zobacz znaczące zwiększenie wydajności. Indeks dla <xref:System.Data.DataView> obiektu jest kompilowany zarówno <xref:System.Data.DataView> podczas tworzenia, jak i gdy dowolna z informacji o sortowaniu lub filtrowaniu jest modyfikowana. Utworzenie a, a następnie ustawienie informacji o sortowaniu lub filtrowaniu później spowoduje, że indeks zostanie skompilowany co najmniej dwa razy <xref:System.Data.DataView> : raz podczas tworzenia i ponownie, gdy właściwości sortowania lub filtrowania są modyfikowane. <xref:System.Data.DataView> Aby uzyskać więcej informacji o filtrowaniu i <xref:System.Data.DataView>sortowaniu w programie, zobacz [filtrowanie z widokiem](filtering-with-dataview-linq-to-dataset.md) danych i [sortowanie za pomocą widoku](sorting-with-dataview-linq-to-dataset.md)danych.  
  
 Jeśli chcesz zwrócić wyniki konkretnego zapytania dotyczącego danych, w przeciwieństwie do udostępnienia dynamicznego widoku podzbioru danych, <xref:System.Data.DataView.Find%2A> możesz użyć metod <xref:System.Data.DataView>lub <xref:System.Data.DataView.FindRows%2A> zamiast ustawić <xref:System.Data.DataView.RowFilter%2A> właściwość. <xref:System.Data.DataView.RowFilter%2A> Właściwość najlepiej jest używana w aplikacji powiązanej z danymi, gdzie kontrolka powiązania Wyświetla przefiltrowane wyniki. <xref:System.Data.DataView.RowFilter%2A> Ustawienie właściwości powoduje odbudowanie indeksu dla danych, dodanie obciążenia do aplikacji i zmniejszenie wydajności. Metody <xref:System.Data.DataView.Find%2A> i<xref:System.Data.DataView.FindRows%2A> używają bieżącego indeksu bez konieczności ponownego kompilowania indeksu. Jeśli zamierzasz wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> tylko raz, należy użyć istniejącej <xref:System.Data.DataView>. Jeśli chcesz <xref:System.Data.DataView.Find%2A> wywoływać lub <xref:System.Data.DataView> <xref:System.Data.DataView.FindRows%2A> wiele razy, należy utworzyć nową, aby ponownie skompilować indeks w kolumnie, w której ma zostać wyszukane, a następnie wywołać <xref:System.Data.DataView.Find%2A> metody lub <xref:System.Data.DataView.FindRows%2A> . Aby uzyskać więcej informacji o <xref:System.Data.DataView.Find%2A> metodach i <xref:System.Data.DataView.FindRows%2A> , zobacz [Znajdowanie wierszy](./dataset-datatable-dataview/finding-rows.md).  
  
 Poniższy przykład używa metody, <xref:System.Data.DataView.Find%2A> aby znaleźć kontakt z nazwiskiem "Zhu".  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 W poniższym przykładzie zastosowano <xref:System.Data.DataView.FindRows%2A> metodę, aby znaleźć wszystkie czerwone kolorowe produkty.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  
 ASP.NET ma mechanizm buforowania, który umożliwia przechowywanie obiektów wymagających rozległych zasobów serwera do tworzenia w pamięci. Buforowanie tych typów zasobów może znacząco poprawić wydajność aplikacji. Buforowanie jest implementowane przez <xref:System.Web.Caching.Cache> klasę, z wystąpieniami pamięci podręcznej, które są prywatne dla każdej aplikacji. Ponieważ tworzenie nowego <xref:System.Data.DataView> obiektu może być czasochłonne, warto użyć tej funkcji buforowania w aplikacjach sieci Web, aby <xref:System.Data.DataView> nie trzeba było jej odbudować za każdym razem, gdy strona sieci Web zostanie odświeżona.  
  
 W poniższym przykładzie <xref:System.Data.DataView> znajduje się w pamięci podręcznej, dzięki czemu dane nie muszą być ponownie sortowane po odświeżeniu strony.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych i LINQ to DataSet](data-binding-and-linq-to-dataset.md)
