---
title: Tworzenie obiektu DataView (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
ms.openlocfilehash: afa760d890cf2857737372af5a9d3ba7c2749e6c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949418"
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>Tworzenie obiektu DataView (LINQ to DataSet)
Istnieją dwa sposoby tworzenia <xref:System.Data.DataView> w kontekście LINQ to DataSet. Można utworzyć na <xref:System.Data.DataView> podstawie zapytania <xref:System.Data.DataTable>LINQ to DataSet w lub można utworzyć je na podstawie typu lub z nieokreślonym typem <xref:System.Data.DataTable>. W obu przypadkach <xref:System.Data.DataView> tworzysz przy użyciu jednej <xref:System.Data.DataTableExtensions.AsDataView%2A> z metod rozszerzenia; <xref:System.Data.DataView> nie jest bezpośrednio konstrukcyjną w kontekście LINQ to DataSet.  
  
 <xref:System.Data.DataView> Po utworzeniu można powiązać go z kontrolką interfejsu użytkownika w aplikacji Windows Forms lub aplikacji ASP.NET albo zmienić ustawienia filtrowania i sortowania.  
  
 <xref:System.Data.DataView>tworzy indeks, co znacznie zwiększa wydajność operacji, które mogą używać indeksu, takich jak filtrowanie i sortowanie. Indeks dla <xref:System.Data.DataView> obiektu jest kompilowany zarówno <xref:System.Data.DataView> podczas tworzenia, jak i gdy dowolna z informacji o sortowaniu lub filtrowaniu jest modyfikowana. Utworzenie a, a następnie ustawienie informacji o sortowaniu lub filtrowaniu później spowoduje, że indeks zostanie skompilowany co najmniej dwa razy <xref:System.Data.DataView> : raz podczas tworzenia i ponownie, gdy właściwości sortowania lub filtrowania są modyfikowane. <xref:System.Data.DataView>  
  
 Aby uzyskać więcej informacji o filtrowaniu i <xref:System.Data.DataView>sortowaniu w programie, zobacz [filtrowanie z widokiem](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) danych i [sortowanie za pomocą widoku](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)danych.  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>Tworzenie elementu DataView z zapytania LINQ to DataSet  
 Obiekt można utworzyć na podstawie wyników zapytania LINQ to DataSet, gdzie wyniki są <xref:System.Data.DataRow> projekcją obiektów. <xref:System.Data.DataView> Nowo utworzona <xref:System.Data.DataView> dziedziczy informacje o filtrowaniu i sortowaniu z zapytania, z którego zostało utworzone.  
  
> [!NOTE]
> W większości przypadków wyrażenia używane do filtrowania i sortowania nie powinny mieć efektów ubocznych i muszą być deterministyczne. Ponadto wyrażenia nie powinny zawierać żadnych logiki, które są zależne od ustawionej liczby wykonań, ponieważ operacje sortowania i filtrowania mogą być wykonywane dowolną liczbę razy.  
  
 <xref:System.Data.DataView> Tworzenie z zapytania, które zwraca typy anonimowe lub zapytania, które wykonują operacje join, nie są obsługiwane.  
  
 W zapytaniu używanym do tworzenia <xref:System.Data.DataView>są obsługiwane tylko następujące operatory zapytań:  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
- <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 Należy pamiętać, że <xref:System.Data.DataView> gdy element jest tworzony na podstawie <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> zapytania LINQ to DataSet Metoda musi być ostateczną metodą wywołana w zapytaniu. Jest to pokazane w poniższym przykładzie, który tworzy <xref:System.Data.DataView> zamówienie online, które posortowano według sumy:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 Można również użyć parametrów <xref:System.Data.DataView.RowFilter%2A> i <xref:System.Data.DataView.Sort%2A> właściwości, <xref:System.Data.DataView> aby przefiltrować i posortować dane po utworzeniu z zapytania. Należy zauważyć, że spowoduje to wyczyszczenie informacji o sortowaniu i filtrowaniu dziedziczonych z zapytania. Poniższy przykład tworzy <xref:System.Data.DataView> kwerendę LINQ to DataSet, która filtruje według ostatnich nazw, które zaczynają się od ". Właściwość oparta <xref:System.Data.DataView.Sort%2A> na ciągach jest ustawiana na sortowanie w kolejności rosnącej, a następnie imię i nazwisko w kolejności malejącej:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>Tworzenie elementu DataView z tabeli DataTable  
 Oprócz tworzenia z kwerendy LINQ to DataSet, <xref:System.Data.DataView> obiekt można utworzyć <xref:System.Data.DataTable> przy użyciu <xref:System.Data.DataTableExtensions.AsDataView%2A> metody.  
  
 Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli SalesOrderDetail i ustawia ją jako źródło <xref:System.Windows.Forms.BindingSource> danych obiektu. Ten obiekt działa jako serwer proxy dla <xref:System.Windows.Forms.DataGridView> kontrolki.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 Filtrowanie i sortowanie można ustawić na <xref:System.Data.DataView> podstawie po utworzeniu utworzonego elementu <xref:System.Data.DataTable>z. Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli Contact i <xref:System.Data.DataView.Sort%2A> ustawia właściwość do sortowania według nazwisk w kolejności rosnącej, a następnie imię w kolejności malejącej:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 Istnieje jednak utrata wydajności, która jest dostarczana z ustawieniem <xref:System.Data.DataView.RowFilter%2A> właściwości <xref:System.Data.DataView.Sort%2A> lub po <xref:System.Data.DataView> utworzeniu z zapytania, ponieważ <xref:System.Data.DataView> tworzy indeks obsługujący operacje filtrowania i sortowania. Ustawienie właściwości <xref:System.Data.DataView.Sort%2A> lub powoduje odbudowanie indeksu dla danych, dodanie obciążenia do aplikacji i zmniejszenie wydajności. <xref:System.Data.DataView.RowFilter%2A> Jeśli to możliwe, lepiej jest określić informacje o filtrowaniu i sortowaniu podczas pierwszego tworzenia <xref:System.Data.DataView> i uniknąć modyfikacji.  
  
## <a name="see-also"></a>Zobacz także

- [Powiązanie danych i LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
- [Filtrowanie za pomocą widoku danych.](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)
- [Sortowanie za pomocą widoku danych.](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
