---
title: Tworzenie obiektu widoku danych (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
ms.openlocfilehash: 3f53c9889e1fdae6c582e8d4a17f640e425e6594
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734438"
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>Tworzenie obiektu widoku danych (LINQ to DataSet)
Istnieją dwa sposoby tworzenia <xref:System.Data.DataView> w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kontekstu. Możesz utworzyć <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytanie dotyczące <xref:System.Data.DataTable>, lub możesz je utworzyć z kontrolą typów lub bez <xref:System.Data.DataTable>. W obu przypadkach należy utworzyć <xref:System.Data.DataView> przy użyciu jednej z <xref:System.Data.DataTableExtensions.AsDataView%2A> metody rozszerzenia; <xref:System.Data.DataView> nie jest bezpośrednio konstrukcyjną w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kontekstu.  
  
 Po <xref:System.Data.DataView> został utworzony, można powiązać kontrolki interfejsu użytkownika w aplikacji ASP.NET lub aplikacji programu Windows forms, lub zmienić filtrowania i sortowania ustawienia.  
  
 <xref:System.Data.DataView> Tworzy indeks, co znacznie zwiększa wydajność operacji, które mogą używać indeksu, takich jak filtrowanie i sortowanie. Indeks <xref:System.Data.DataView> powstała zarówno gdy <xref:System.Data.DataView> jest tworzony i gdy którykolwiek z sortowania lub filtrowania informacji jest modyfikowany. Tworzenie <xref:System.Data.DataView> , a następnie ustawienie sortowania lub filtrowania informacje później powoduje indeks ma zostać utworzony co najmniej dwa razy: po podczas <xref:System.Data.DataView> zostanie utworzony, i ponownie podczas sortowania lub filtrowania właściwości są modyfikowane.  
  
 Aby uzyskać więcej informacji na temat filtrowania i sortowania z <xref:System.Data.DataView>, zobacz [Filtrowanie za pomocą widoku danych](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) i [sortowanie za pomocą widoku danych](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>Tworzenie widoku danych z LINQ do kwerendy zestawu danych  
 A <xref:System.Data.DataView> obiektu można tworzyć na podstawie wyników [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania, których wyniki są rzutowaniem <xref:System.Data.DataRow> obiektów. Nowo utworzony <xref:System.Data.DataView> dziedziczy filtrowanie i sortowanie informacji z zapytania jest tworzona na podstawie.  
  
> [!NOTE]
>  W większości przypadków wyrażenia używane do filtrowania i sortowania nie powinny mieć skutki uboczne i musi być deterministyczna. Ponadto wyrażenia nie może zawierać dowolne logiki, które są zależne od określona liczba wykonań, ponieważ sortowanie i filtrowanie działań może być wykonywane dowolną liczbę razy.  
  
 Tworzenie <xref:System.Data.DataView> z zapytania, które zwraca typy anonimowe lub zapytania, które wykonują operacje sprzężenia nie jest obsługiwane.  
  
 Tylko następujące operatory zapytania są obsługiwane w zapytaniu użyty do utworzenia <xref:System.Data.DataView>:  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 Należy pamiętać, że w przypadku <xref:System.Data.DataView> jest tworzona na podstawie [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> metoda musi być ostatnią metodę o nazwie w zapytaniu. Jest to pokazane w poniższym przykładzie, który tworzy <xref:System.Data.DataView> online zamówień, posortowane według całkowitej termin:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 Można również użyć opartego na ciągach <xref:System.Data.DataView.RowFilter%2A> i <xref:System.Data.DataView.Sort%2A> właściwości w celu filtrowania i sortowania <xref:System.Data.DataView> po utworzeniu w wyniku zapytania. Należy pamiętać, że spowoduje to wyczyszczenie sortowanie i filtrowanie informacji dziedziczone z zapytania. Poniższy przykład tworzy <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytanie filtrujące według nazwiska, rozpoczynających się od użytkownika ". Opartego na ciągach <xref:System.Data.DataView.Sort%2A> właściwość jest ustawiona na sortowanie według nazwiska w rosnącej kolejności, a następnie nazwy pierwszy w kolejności malejącej:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>Tworzenie elementu DataView z obiektu DataTable  
 Oprócz tworzona z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania, <xref:System.Data.DataView> obiektu można tworzyć na podstawie <xref:System.Data.DataTable> przy użyciu <xref:System.Data.DataTableExtensions.AsDataView%2A> metody.  
  
 Poniższy przykład tworzy <xref:System.Data.DataView> z szczegóły zamówienia sprzedaży tabeli i ustawia go jako źródło danych <xref:System.Windows.Forms.BindingSource> obiektu. Ten obiekt działa jako serwer proxy dla <xref:System.Windows.Forms.DataGridView> kontroli.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 Filtrowanie i sortowanie można ustawić na <xref:System.Data.DataView> po utworzeniu z <xref:System.Data.DataTable>. Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli Kontakt i zestawy <xref:System.Data.DataView.Sort%2A> właściwości, aby sortować rekordy według nazwiska w rosnącej kolejności, a następnie nazwy pierwszy w kolejności malejącej:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 Istnieje jednak straty wydajności, dostarczanego razem z ustawieniem <xref:System.Data.DataView.RowFilter%2A> lub <xref:System.Data.DataView.Sort%2A> właściwości po <xref:System.Data.DataView> została utworzona na podstawie zapytania, ponieważ <xref:System.Data.DataView> tworzy indeks do obsługi operacji filtrowania i sortowania. Ustawienie <xref:System.Data.DataView.RowFilter%2A> lub <xref:System.Data.DataView.Sort%2A> właściwość odbudowania indeksu dla danych, obciążenie dodawanie do aplikacji i zmniejszenie wydajności. Jeśli to możliwe, zaleca się określenie filtrowanie i sortowanie informacji podczas pierwszego tworzenia <xref:System.Data.DataView> i należy unikać modyfikowania go później.  
  
## <a name="see-also"></a>Zobacz także
- [Powiązanie danych i LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
- [Filtrowanie za pomocą widoku danych.](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)
- [Sortowanie za pomocą widoku danych.](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
