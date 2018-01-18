---
title: Tworzenie obiektu DataView (LINQ do DataSet)
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
ms.assetid: 76057508-e12d-4779-a707-06a4c2568acf
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 895f692bc07e8e48904e0829e322788f2aa45337
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="creating-a-dataview-object-linq-to-dataset"></a>Tworzenie obiektu DataView (LINQ do DataSet)
Istnieją dwa sposoby tworzenia <xref:System.Data.DataView> w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kontekstu. Można utworzyć <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytanie dotyczące <xref:System.Data.DataTable>, lub można utworzyć go z typu lub wyrażeniami bez typu <xref:System.Data.DataTable>. W obu przypadkach należy utworzyć <xref:System.Data.DataView> przy użyciu jednej z <xref:System.Data.DataTableExtensions.AsDataView%2A> metody rozszerzenia; <xref:System.Data.DataView> nie jest bezpośrednio umożliwia konstrukcji w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kontekstu.  
  
 Po <xref:System.Data.DataView> został utworzony, można powiązać go z formantu interfejsu użytkownika w aplikacji formularzy systemu Windows lub aplikacji ASP.NET lub zmienić filtrowanie i sortowanie ustawienia.  
  
 <xref:System.Data.DataView>Tworzy indeks, co znacznie zwiększa wydajność operacji korzystających z indeksu, na przykład filtrowanie i sortowanie. Indeks <xref:System.Data.DataView> składa się zarówno w przypadku <xref:System.Data.DataView> jest tworzony i podczas sortowania i filtrowania informacji jest modyfikowany. Tworzenie <xref:System.Data.DataView> , a następnie ustawienie sortowania i filtrowania informacje później powoduje indeksu, który ma zostać utworzony co najmniej dwa razy: po podczas <xref:System.Data.DataView> jest tworzony, i ponownie gdy dowolne z właściwości sortowania i filtrowania są modyfikowane.  
  
 Aby uzyskać więcej informacji dotyczących filtrowania i sortowania z <xref:System.Data.DataView>, zobacz [filtrowanie z DataView](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md) i [sortowania z DataView](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md).  
  
## <a name="creating-dataview-from-a-linq-to-dataset-query"></a>Tworzenie widoku danych ze składnika LINQ do zestawu danych zapytania  
 A <xref:System.Data.DataView> można utworzyć obiektu wyników [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania, gdy wyniki są projekcji z <xref:System.Data.DataRow> obiektów. Nowo utworzony <xref:System.Data.DataView> dziedziczy filtrowanie i sortowanie jest tworzona na podstawie zapytania.  
  
> [!NOTE]
>  W większości przypadków wyrażenia używane do filtrowania i sortowania nie powinny mieć efekty uboczne i musi być deterministyczny. Ponadto wyrażenia nie może zawierać żadnego logiki, które są zależne od zestawu Liczba wykonań, jakie sortowania i filtrowania operacje mogą być wykonywane dowolną liczbę razy.  
  
 Tworzenie <xref:System.Data.DataView> z zapytanie zwracające typy anonimowe lub kwerend, które wykonują operacje sprzężenia nie jest obsługiwany.  
  
 Tylko następujące operatory zapytania są obsługiwane w zapytaniu użyty do utworzenia <xref:System.Data.DataView>:  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Cast%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.OrderByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenBy%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.ThenByDescending%2A>  
  
-   <xref:System.Data.EnumerableRowCollectionExtensions.Where%2A>  
  
 Należy pamiętać, że w przypadku <xref:System.Data.DataView> jest tworzona na podstawie [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania <xref:System.Data.EnumerableRowCollectionExtensions.Select%2A> metoda musi być ostatnia metoda wywoływana w zapytaniu. Przedstawiono to w poniższym przykładzie, który tworzy <xref:System.Data.DataView> online zamówień posortowane według całkowitej termin:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquery1)]
 [!code-vb[DP DataView Samples#CreateLDVFromQuery1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquery1)]  
  
 Można również użyć ciągu podstawie <xref:System.Data.DataView.RowFilter%2A> i <xref:System.Data.DataView.Sort%2A> właściwości, aby filtrować i sortować <xref:System.Data.DataView> po został utworzony w wyniku zapytania. Należy pamiętać, że spowoduje to wyczyszczenie sortowania i filtrowania dziedziczone z zapytania. Poniższy przykład tworzy <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytanie filtrujące według nazwisk rozpoczynających się od elementu ". Ciąg znaków na podstawie <xref:System.Data.DataView.Sort%2A> właściwość jest ustawiona na sortowanie nazwisk w rosnącej kolejności, a następnie imion w kolejności malejącej:  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="creating-a-dataview-from-a-datatable"></a>Tworzenie widoku danych z obiektu DataTable  
 Oprócz tworzenia z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania, <xref:System.Data.DataView> można utworzyć obiektu z <xref:System.Data.DataTable> przy użyciu <xref:System.Data.DataTableExtensions.AsDataView%2A> metody.  
  
 Poniższy przykład tworzy <xref:System.Data.DataView> z szczegóły zamówienia sprzedaży tabeli i ustawia go jako źródło danych <xref:System.Windows.Forms.BindingSource> obiektu. Ten obiekt działa jako serwer proxy dla <xref:System.Windows.Forms.DataGridView> formantu.  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromtable)]
 [!code-vb[DP DataView Samples#CreateLDVFromTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromtable)]  
  
 Filtrowanie i sortowanie można ustawić na <xref:System.Data.DataView> po utworzeniu z <xref:System.Data.DataTable>. Poniższy przykład tworzy <xref:System.Data.DataView> z tabeli Kontakt i zestawy <xref:System.Data.DataView.Sort%2A> właściwości do sortowania nazwisk w rosnącej kolejności, a następnie imion w kolejności malejącej:  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
 Istnieje jednak utrata wydajności dołączoną ustawienie <xref:System.Data.DataView.RowFilter%2A> lub <xref:System.Data.DataView.Sort%2A> właściwości po <xref:System.Data.DataView> został utworzony w wyniku zapytania, ponieważ <xref:System.Data.DataView> tworzy indeksu w celu obsługi operacji filtrowania i sortowania. Ustawienie <xref:System.Data.DataView.RowFilter%2A> lub <xref:System.Data.DataView.Sort%2A> właściwości odtwarza indeksu dla danych narzut dodawanie do swojej aplikacji i zmniejszenie wydajności. Jeśli to możliwe, zaleca się określenie filtrowanie i sortowanie podczas tworzenia <xref:System.Data.DataView> i unikać modyfikacji go później.  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych i LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)  
 [Filtrowanie za pomocą widoku danych.](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 [Sortowanie za pomocą widoku danych.](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)
