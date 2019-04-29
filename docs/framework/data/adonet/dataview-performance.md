---
title: Wydajność widoku danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: f0a85232b753eed891cded4b0fb1154269b30dc9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606947"
---
# <a name="dataview-performance"></a>Wydajność widoku danych
W tym temacie omówiono zalety wydajności przy użyciu <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView> klasy i buforowania <xref:System.Data.DataView> w aplikacji sieci Web.  
  
## <a name="find-and-findrows"></a>Znajdź i FindRows  
 <xref:System.Data.DataView> Tworzy indeks. Indeks zawiera klucze utworzona na podstawie co najmniej jedną kolumnę w tabeli lub widoku. Te klucze są przechowywane w strukturze, która umożliwia <xref:System.Data.DataView> można znaleźć wiersze skojarzonych wartości klucza, szybkie i skuteczne. Operacje korzystające z indeksu, takich jak filtrowanie i sortowanie, zobacz zwiększa istotnie poprawiającą wydajność. Indeks <xref:System.Data.DataView> powstała zarówno gdy <xref:System.Data.DataView> jest tworzony i gdy którykolwiek z sortowania lub filtrowania informacji jest modyfikowany. Tworzenie <xref:System.Data.DataView> , a następnie ustawienie sortowania lub filtrowania informacje później powoduje indeks ma zostać utworzony co najmniej dwa razy: po podczas <xref:System.Data.DataView> zostanie utworzony, i ponownie podczas sortowania lub filtrowania właściwości są modyfikowane. Aby uzyskać więcej informacji na temat filtrowania i sortowania z <xref:System.Data.DataView>, zobacz [Filtrowanie za pomocą widoku danych](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) i [sortowanie za pomocą widoku danych](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).  
  
 Jeśli mają być zwracane wyniki zapytania określonego na danych, w przeciwieństwie do realizacji dynamiczny widok podzbiór danych, można użyć <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>, zamiast ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwości. <xref:System.Data.DataView.RowFilter%2A> Właściwość najlepiej sprawdza się w aplikacji powiązanych z danymi gdzie powiązanej kontrolki Wyświetla wyfiltrowanych wyników. Ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwość odbudowania indeksu dla danych, obciążenie dodawanie do aplikacji i zmniejszenie wydajności. <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metody używać bieżącego indeksu bez konieczności indeks odbudowany. Jeśli wywołanie <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> tylko raz, użyj istniejącego <xref:System.Data.DataView>. Jeśli wywołanie <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> wielokrotnie, należy utworzyć nową <xref:System.Data.DataView> do odbudowania indeksu w kolumnie, aby wyszukać, a następnie wywołaj <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody. Aby uzyskać więcej informacji na temat <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metod, zobacz [znajdowanie wierszy](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
 W poniższym przykładzie użyto <xref:System.Data.DataView.Find%2A> metody do znalezienia kontaktu o nazwisku "Zhu".  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 W poniższym przykładzie użyto <xref:System.Data.DataView.FindRows%2A> metody do znalezienia wszystkich red pokolorowane produktów.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  
 Program ASP.NET ma mechanizm buforowania, która umożliwia przechowywanie obiektów, które wymagają zasobów rozbudowane serwera do tworzenia w pamięci. Buforowanie tych typów zasobów może znacznie poprawić wydajność aplikacji. Pamięć podręczna jest implementowana przez <xref:System.Web.Caching.Cache> klasy z wystąpienia pamięci podręcznej, które są prywatne dla każdej aplikacji. Ponieważ utworzenie nowego <xref:System.Data.DataView> obiekt może być dużej ilości zasobów, można skorzystać z tej funkcji w aplikacjach sieci Web buforowania, aby <xref:System.Data.DataView> nie trzeba odbudować, za każdym razem, gdy strona sieci Web zostanie odświeżona.  
  
 W poniższym przykładzie <xref:System.Data.DataView> są buforowane, dzięki czemu dane nie trzeba ponownie posortowane po odświeżeniu strony.  
  
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

- [Powiązanie danych i LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
