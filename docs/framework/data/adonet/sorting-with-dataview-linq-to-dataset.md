---
title: Sortowanie za pomocą widoku danych (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: 9f69b64088093bbdd46239a26f16aeea50b6dee7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44076879"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a>Sortowanie za pomocą widoku danych (LINQ to DataSet)
Możliwość sortowania danych w oparciu o określone kryteria, a następnie prezentować dane do klienta za pomocą kontrolki interfejsu użytkownika jest istotnym elementem powiązanie danych. <xref:System.Data.DataView> zapewnia kilka metod sortowania danych i zwraca wiersze danych uporządkowanych według określonych kryteriów porządkowania. Oprócz jego opartego na ciągach sortowanie możliwości <xref:System.Data.DataView> również pozwala na użycie [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] wyrażeń kryterium sortowania. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] wyrażenia pozwalają znacznie bardziej złożone i zaawansowane operacje sortowania niż sortowanie oparte na ciągach. W tym temacie opisano sortowanie, za pomocą obu metod <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a>Tworzenie widoku danych. w wyniku zapytania za pomocą sortowanie informacji  
 A <xref:System.Data.DataView> obiektu można tworzyć na podstawie [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania. Jeśli kwerenda zawiera <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, lub <xref:System.Linq.Enumerable.ThenByDescending%2A> wyrażenia w klauzulach te są używane jako podstawa sortowanie danych w klauzuli <xref:System.Data.DataView>. Na przykład, jeśli zapytanie zawiera `Order By…`i `Then By…` zdań, wynikowy <xref:System.Data.DataView> będzie porządkowania danych przez obie kolumny określone.  
  
 Oparte na wyrażeniach sortowania oferuje bardziej zaawansowanych i złożonych sortowania niż prostsze oparte na ciągach sortowania. Uwaga: ciąg znaków, jak i oparte na wyrażeniach sortowania są wzajemnie się wykluczają. Jeśli opartego na ciągach <xref:System.Data.DataView.Sort%2A> jest ustawiany po <xref:System.Data.DataView> jest tworzona w wyniku zapytania, oparte na wyrażeniach filtru, wywnioskowane z kwerendy jest wyczyszczone i nie może być resetowany.  
  
 Indeks <xref:System.Data.DataView> powstała zarówno gdy <xref:System.Data.DataView> jest tworzony i gdy którykolwiek z sortowania lub filtrowania informacji jest modyfikowany. Uzyskać najlepszą wydajność, podając kryteria sortowania w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytanie <xref:System.Data.DataView> został utworzony i nie modyfikowanie sortowania informacje, a później. Aby uzyskać więcej informacji, zobacz [wydajność widoku danych](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
> [!NOTE]
>  W większości przypadków wyrażenia używane do sortowania nie powinny mieć skutki uboczne i musi być deterministyczna. Ponadto wyrażenia nie może zawierać dowolną logikę, która jest zależna od określona liczba wykonań, ponieważ operacje sortowania może być wykonywane dowolną liczbę razy.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zapytania tabeli SalesOrderHeader i porządkuje zwrócone wiersze według dat zamówienia; Tworzy <xref:System.Data.DataView> z tej kwerendy; i wiąże <xref:System.Data.DataView> do <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zapytania tabeli SalesOrderHeader i porządkuje zwracany wiersz według sumy. Tworzy <xref:System.Data.DataView> z tej kwerendy; i wiąże <xref:System.Data.DataView> do <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zapytania w tabeli Szczegóły zamówienia sprzedaży i porządkuje zwrócone wiersze według ilości zamówienia, a następnie według Identyfikatora zamówienia sprzedaży; Tworzy <xref:System.Data.DataView> z tej kwerendy; i wiąże <xref:System.Data.DataView> do <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a>Przy użyciu właściwości sortowania oparte na ciągach  
 Oparte na ciągach sortowania funkcjonalność <xref:System.Data.DataView> nadal działa z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Po <xref:System.Data.DataView> została utworzona na podstawie [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania, można użyć <xref:System.Data.DataView.Sort%2A> właściwość można ustawić sortowanie według <xref:System.Data.DataView>.  
  
 Oparte na ciąg i oparte na wyrażeniach sortowania funkcje wzajemnie się wykluczają. Ustawienie <xref:System.Data.DataView.Sort%2A> właściwość spowoduje wyczyszczenie oparte na wyrażeniach sortowania dziedziczone z zapytania, <xref:System.Data.DataView> został utworzony na podstawie.  
  
 Aby uzyskać więcej informacji na temat oparte na ciągach <xref:System.Data.DataView.Sort%2A> filtrowania, zobacz [sortowanie i filtrowanie danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
### <a name="example"></a>Przykład  
 W przykładzie poniżej jest tworzony <xref:System.Data.DataView> z kontaktu tabeli i wiersze są sortowane według nazwiska w malejącej zamówienia, a następnie imię w kolejności rosnącej:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wysyła zapytanie do tabeli kontaktów nazwiska, które zaczyna się literą "S".  A <xref:System.Data.DataView> jest tworzone na podstawie tego zapytania i powiązany <xref:System.Windows.Forms.BindingSource> obiektu.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a>Czyszczenie sortowania  
 Kryteria sortowania na <xref:System.Data.DataView> może być obsadzona po ustawieniu, za pomocą <xref:System.Data.DataView.Sort%2A> właściwości. Istnieją dwa sposoby, aby wyczyścić sortowania informacje przedstawione w <xref:System.Data.DataView>:  
  
-   Ustaw <xref:System.Data.DataView.Sort%2A> właściwość `null`.  
  
-   Ustaw <xref:System.Data.DataView.Sort%2A> właściwości na pusty ciąg.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> w wyniku zapytania i czyści, sortowanie, ustawiając <xref:System.Data.DataView.Sort%2A> właściwości na pusty ciąg:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli Kontakt i zestawy <xref:System.Data.DataView.Sort%2A> właściwości, aby posortować według nazwiska w kolejności malejącej. Kryteria sortowania następnie wyczyścić, ustawiając <xref:System.Data.DataView.Sort%2A> właściwości `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych i LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [Filtrowanie za pomocą widoku danych.](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 [Sortowanie danych](https://msdn.microsoft.com/library/6d76e2d7-b418-49b5-ac78-2bcd61169c48)
