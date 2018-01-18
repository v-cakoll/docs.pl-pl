---
title: Sortowania z DataView (LINQ do DataSet)
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
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e8eda365fa1970f4fa836440151cc1ba0d3ae9dd
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="sorting-with-dataview-linq-to-dataset"></a>Sortowania z DataView (LINQ do DataSet)
Sortowanie danych na podstawie określonych kryteriów, a następnie prezentować danych do klienta za pomocą formantu interfejsu użytkownika jest ważnym aspektem wiązania z danymi. <xref:System.Data.DataView>udostępnia kilka sposobów, aby posortować dane i zwracanie wszystkich wierszy danych uporządkowanych według określonych kryteriów porządkowania. Oprócz jego podstawie ciąg sortowania możliwości, <xref:System.Data.DataView> także pozwala na użycie [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] wyrażenia kryterium sortowania. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]wyrażenia umożliwia bardziej złożone i zaawansowane operacje sortowania niż sortowanie oparte na ciągach. W tym temacie opisano oba podejścia do sortowania za pomocą <xref:System.Data.DataView>.  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a>Tworzenie widoku danych z zapytania z sortowaniem informacji  
 A <xref:System.Data.DataView> można utworzyć obiektu z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania. Jeśli kwerenda zawiera <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, lub <xref:System.Linq.Enumerable.ThenByDescending%2A> wyrażeń w klauzuli te są używane jako podstawa sortowania danych w klauzuli <xref:System.Data.DataView>. Na przykład, jeśli zapytanie zawiera `Order By…`i `Then By…` klauzule powstałe w ten sposób <xref:System.Data.DataView> czy określanie kolejności według obu kolumn określonych danych.  
  
 Oparte na wyrażeniach sortowania oferuje bardziej zaawansowaną i złożone sortowania niż prostsze oparte na ciąg sortowania. Należy pamiętać, że na podstawie ciągu i oparte na wyrażeniach sortowania wzajemnie się wykluczają. Jeśli ciąg podstawie <xref:System.Data.DataView.Sort%2A> jest ustawiany po <xref:System.Data.DataView> jest tworzony w wyniku zapytania oparte na wyrażeniach filtru wywnioskować na podstawie zapytania jest wyczyszczone i nie można przywrócić.  
  
 Indeks <xref:System.Data.DataView> składa się zarówno w przypadku <xref:System.Data.DataView> jest tworzony i podczas sortowania i filtrowania informacji jest modyfikowany. Możesz uzyskać najlepszą wydajność, podając kryteria sortowania w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytanie <xref:System.Data.DataView> jest tworzona na podstawie i nie modyfikowanie sortowania informacje, a później. Aby uzyskać więcej informacji, zobacz [wydajności DataView](../../../../docs/framework/data/adonet/dataview-performance.md).  
  
> [!NOTE]
>  W większości przypadków wyrażenia używane do sortowania nie powinny mieć efekty uboczne i musi być deterministyczny. Ponadto wyrażenia nie może zawierać dowolną logikę, która jest zależna od zestawu Liczba wykonań, ponieważ sortowania operacje mogą być wykonywane dowolną liczbę razy.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zapytanie tabeli SalesOrderHeader i porządkuje zwrócone wiersze według dat zamówienia; Tworzy <xref:System.Data.DataView> z tej kwerendy; i wiąże <xref:System.Data.DataView> do <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zapytanie tabeli SalesOrderHeader i porządkuje wiersza zwrócone przez suma. Tworzy <xref:System.Data.DataView> z tej kwerendy; i wiąże <xref:System.Data.DataView> do <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zapytanie tabeli Szczegóły zamówienia sprzedaży i porządkuje zwrócone wiersze według ilości zlecenia, a następnie według Identyfikatora zamówienia; Tworzy <xref:System.Data.DataView> z tej kwerendy; i wiąże <xref:System.Data.DataView> do <xref:System.Windows.Forms.BindingSource>.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a>Za pomocą właściwości sortowania oparte na ciągach  
 Ciąg sortowania funkcje związane z <xref:System.Data.DataView> nadal działa z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]. Po <xref:System.Data.DataView> została utworzona na podstawie [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kwerendy, można użyć <xref:System.Data.DataView.Sort%2A> właściwość umożliwiająca ustawienie sortowania na <xref:System.Data.DataView>.  
  
 Na podstawie ciągu i oparte na wyrażeniach sortowania funkcje wzajemnie się wykluczają. Ustawienie <xref:System.Data.DataView.Sort%2A> właściwość spowoduje wyczyszczenie oparte na wyrażeniach sortowania dziedziczone z poziomu zapytania który <xref:System.Data.DataView> został utworzony na podstawie.  
  
 Aby uzyskać więcej informacji na temat na podstawie ciągu <xref:System.Data.DataView.Sort%2A> filtrowania, zobacz [sortowanie i filtrowanie danych](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).  
  
### <a name="example"></a>Przykład  
 W przykładzie poniżej tworzy <xref:System.Data.DataView> z kontaktu tabela i wiersze są sortowane według nazwiska malejąco kolejności, a następnie imię w kolejności rosnącej:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wysyła zapytanie do tabeli kontaktów nazwiska rozpoczynające się od litery "S".  A <xref:System.Data.DataView> jest tworzone na podstawie zapytania i powiązany <xref:System.Windows.Forms.BindingSource> obiektu.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a>Wyczyszczenie sortowania  
 Kryteria sortowania na <xref:System.Data.DataView> można wyczyścić po ustawieniu, przy użyciu <xref:System.Data.DataView.Sort%2A> właściwości. Istnieją dwa sposoby, aby wyczyścić informacje sortowania w <xref:System.Data.DataView>:  
  
-   Ustaw <xref:System.Data.DataView.Sort%2A> właściwości `null`.  
  
-   Ustaw <xref:System.Data.DataView.Sort%2A> właściwości na pusty ciąg.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> z zapytania i czyści sortowanie przez ustawienie <xref:System.Data.DataView.Sort%2A> właściwości na pusty ciąg:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli Kontakt i zestawy <xref:System.Data.DataView.Sort%2A> właściwości, aby posortować według nazwisko w kolejności malejącej. Następnie wyczyścić kryteria sortowania, ustawiając <xref:System.Data.DataView.Sort%2A> właściwości `null`:  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych i LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [Filtrowanie za pomocą widoku danych.](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 [Sortowanie danych](http://msdn.microsoft.com/library/6d76e2d7-b418-49b5-ac78-2bcd61169c48)
