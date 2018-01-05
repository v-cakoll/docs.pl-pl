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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 15727d327ca045a0206fc357e35c6fa7e1323747
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="dataview-performance"></a>Widok danych wydajności
W tym temacie omówiono wydajności korzyści wynikające ze stosowania <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView> klasy i buforowania <xref:System.Data.DataView> w aplikacji sieci Web.  
  
## <a name="find-and-findrows"></a>Znajdź i FindRows  
 <xref:System.Data.DataView>Tworzy indeks. Indeks zawiera klucze zbudowane na podstawie co najmniej jedną kolumnę w tabeli lub widoku. Klucze te są przechowywane w strukturze, która umożliwia <xref:System.Data.DataView> można znaleźć wiersze skojarzone z wartości klucza, szybkie i skuteczne. Operacji korzystających z indeksu, na przykład filtrowanie i sortowanie, zobacz signifcant zwiększa wydajność. Indeks <xref:System.Data.DataView> składa się zarówno w przypadku <xref:System.Data.DataView> jest tworzony i podczas sortowania i filtrowania informacji jest modyfikowany. Tworzenie <xref:System.Data.DataView> , a następnie ustawienie sortowania i filtrowania informacje później powoduje indeksu, który ma zostać utworzony co najmniej dwa razy: po podczas <xref:System.Data.DataView> jest tworzony, i ponownie gdy dowolne z właściwości sortowania i filtrowania są modyfikowane. Aby uzyskać więcej informacji dotyczących filtrowania i sortowania z <xref:System.Data.DataView>, zobacz [filtrowanie z DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) i [sortowania z DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).  
  
 Jeśli chcesz zwrócić wyników określonego zapytania na danych, w przeciwieństwie do zapewniające widoku dynamicznego podzbiór danych, można użyć <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody <xref:System.Data.DataView>, zamiast ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwości. <xref:System.Data.DataView.RowFilter%2A> Właściwości najlepiej sprawdza się w aplikacji powiązanych z danymi gdzie powiązanej kontrolki wyświetla filtrowane wyniki. Ustawienie <xref:System.Data.DataView.RowFilter%2A> właściwości odtwarza indeksu dla danych narzut dodawanie do swojej aplikacji i zmniejszenie wydajności. <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metody używać bieżącego indeksu bez konieczności indeksu, który ma zostać również przebudowany. Jeśli zamierzasz wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> tylko raz, następnie należy użyć istniejącego <xref:System.Data.DataView>. Jeśli zamierzasz wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> wielokrotnie, należy utworzyć nowy <xref:System.Data.DataView> odbudować indeksu w kolumnie, aby wyszukać, a następnie wywołać <xref:System.Data.DataView.Find%2A> lub <xref:System.Data.DataView.FindRows%2A> metody. Aby uzyskać więcej informacji na temat <xref:System.Data.DataView.Find%2A> i <xref:System.Data.DataView.FindRows%2A> metod, zobacz [znajdowanie wierszy](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md).  
  
 W poniższym przykładzie użyto <xref:System.Data.DataView.Find%2A> metody do znalezienia kontaktu z nazwisko "Zhu".  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 W poniższym przykładzie użyto <xref:System.Data.DataView.FindRows%2A> metody do znalezienia wszystkich czerwony pokolorowane produktów.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  
 Program ASP.NET ma mechanizm buforowania, która umożliwia przechowywanie obiektów, które wymagają serwera szeroką gamę zasoby do utworzenia w pamięci. Buforowanie tych typów zasobów może znacznie poprawić wydajność aplikacji. Buforowanie jest implementowany przez <xref:System.Web.Caching.Cache> klasy z wystąpienia pamięci podręcznej, które są prywatne dla każdej aplikacji. Ponieważ tworzenia nowego <xref:System.Data.DataView> obiekt może być ilości zasobów, można użyć tej funkcji buforowania funkcji w aplikacji sieci Web, aby <xref:System.Data.DataView> nie musi zostać również przebudowany w każdym odświeżeniu strony sieci Web.  
  
 W poniższym przykładzie <xref:System.Data.DataView> są buforowane, dzięki czemu nie ma danych do posortowania ponownie po odświeżeniu strony.  
  
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
 [Powiązanie danych i LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
