---
title: Tworzenie DataTable w wyniku zapytania (LINQ do DataSet)
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
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5be353d76f921edd730d46907096abe8a2a1188f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>Tworzenie DataTable w wyniku zapytania (LINQ do DataSet)
Powiązanie danych jest typowym zastosowaniem <xref:System.Data.DataTable> obiektu. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda pobiera wyników zapytania i kopiuje dane na <xref:System.Data.DataTable>, której następnie można użyć dla powiązania danych. Po wykonaniu operacji danych, nowa <xref:System.Data.DataTable> jest scalone źródło <xref:System.Data.DataTable>.  
  
 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metody przystępuje do następującej procedury, aby utworzyć <xref:System.Data.DataTable> w wyniku zapytania:  
  
1.  <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Klony metody <xref:System.Data.DataTable> z tabeli źródłowej ( <xref:System.Data.DataTable> obiekt, który implementuje <xref:System.Linq.IQueryable%601> interfejs). <xref:System.Collections.IEnumerable> Źródło ma zazwyczaj pochodzą ze [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] wyrażenie lub metoda zapytania.  
  
2.  Schemat sklonowany <xref:System.Data.DataTable> składa się z kolumny pierwszego wyliczyć <xref:System.Data.DataRow> obiektu w tabeli źródłowej i nazwa tabeli sklonowany jest nazwą tabeli źródłowej od słowa "query" dołączone do niego.  
  
3.  Dla każdego wiersza w tabeli źródłowej zawartości wiersza jest kopiowana do nowej <xref:System.Data.DataRow> obiektu, który jest następnie wstawione do tabeli sklonowany. <xref:System.Data.DataRow.RowState%2A> i <xref:System.Data.DataRow.RowError%2A> właściwości są zachowywane w operacji kopiowania. <xref:System.ArgumentException> Jest generowany, jeśli <xref:System.Data.DataRow> obiekty w źródle są z różnych tabel.  
  
4.  Sklonowany <xref:System.Data.DataTable> jest zwracany po wszystkich <xref:System.Data.DataRow> obiektów w tabeli wejściowej kolejność zostały skopiowane. Jeśli sekwencja źródło nie zawiera żadnych <xref:System.Data.DataRow> obiektów, metoda zwraca pustą <xref:System.Data.DataTable>.  
  
 Należy pamiętać, że wywołania <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda spowoduje powiązana z tabeli źródłowej, aby wykonać zapytanie.  
  
 Gdy <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody napotka odwołanie o wartości null lub typ dopuszczający wartość null wartości wiersza w tabeli źródłowej, zastępuje ona wartości z <xref:System.DBNull.Value>. Dzięki temu wartości null są obsługiwane poprawnie w zwróconym <xref:System.Data.DataTable>.  
  
 Uwaga: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda przyjmuje jako dane wejściowe kwerendę, która może zwracać wiersze z wieloma <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> obiektów. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metody spowoduje skopiowanie ze źródła danych, ale nie właściwości <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> obiektów zwrócona <xref:System.Data.DataTable>. Musisz jawnie ustawić właściwości w zwróconym <xref:System.Data.DataTable>, takich jak <xref:System.Data.DataTable.Locale%2A> i <xref:System.Data.DataTable.TableName%2A>.  
  
 W poniższym przykładzie zapytanie tabeli SalesOrderHeader zamówień po 8 sierpnia 2001 i używa <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metodę w celu utworzenia <xref:System.Data.DataTable> z tej kwerendy. <xref:System.Data.DataTable> Następnie jest powiązany z <xref:System.Windows.Forms.BindingSource>, który działa jako serwer proxy dla <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Tworzenie niestandardowych CopyToDataTable\<T > — Metoda  
 Istniejące <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody wykonywać operacje tylko na <xref:System.Collections.Generic.IEnumerable%601> źródła gdzie parametr generyczny `T` jest typu <xref:System.Data.DataRow>. Chociaż jest to przydatne, nie zezwala tabele, aby utworzyć sekwencję typy skalarne, z zapytań zwracających typy anonimowe lub z zapytań, które wykonują sprzężeń tabel. Przykład implementowania niestandardowych dwóch `CopyToDataTable` metod, które ładują tabelę z sekwencji typów skalarnych lub anonimowe, zobacz [jak: Implementowanie CopyToDataTable\<T > gdzie ogólny typ T nie jest element DataRow](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)s.  
  
 Przykłady w tej sekcji należy użyć następujących typów niestandardowych:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Przykład  
 W tym przykładzie wykonuje sprzężenie za pośrednictwem `SalesOrderHeader` i `SalesOrderDetail` tabele, aby uzyskać zamówień online z sierpień i tworzy tabelę na podstawie zapytania.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zapytanie kolekcji elementów ceny większe niż 9,99 $ i tworzy tabelę na podstawie wyników zapytania.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wysyła zapytanie do kolekcji elementów większe niż 9,99 ceny i projektów wyniki. Sekwencja zwracane typy anonimowe została załadowana do istniejącej tabeli.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wysyła zapytanie do kolekcji elementów większe niż 9,99 $ ceny i projektów wyniki. Sekwencja zwracane typy anonimowe została załadowana do istniejącej tabeli. Schemat tabeli jest automatycznie rozwinięta, ponieważ `Book` i `Movies` pochodne typy `Item` typu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zapytanie kolekcji elementów ceny większe niż 9,99 $ i zwraca sekwencji <xref:System.Double>, który jest ładowany do nowej tabeli.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)  
 [Pole ogólnego i metody SetField](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)  
 [LINQ do DataSet przykłady](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
