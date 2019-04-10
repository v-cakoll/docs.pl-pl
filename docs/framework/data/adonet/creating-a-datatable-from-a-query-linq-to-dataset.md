---
title: Tworzenie elementu DataTable w wyniku zapytania (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: 0f750f2d23430691016fc2cf1e5e9d44d80da2a9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204084"
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>Tworzenie elementu DataTable w wyniku zapytania (LINQ to DataSet)
Wiązanie danych jest często używana <xref:System.Data.DataTable> obiektu. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda pobiera wyniki zapytania i kopiuje dane do <xref:System.Data.DataTable>, która następnie umożliwia powiązanie danych. Po wykonaniu operacji danych, nowa <xref:System.Data.DataTable> jest scalany z powrotem do źródła skrzynki <xref:System.Data.DataTable>.  
  
 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda przystępuje do następującej procedury, aby utworzyć <xref:System.Data.DataTable> w wyniku zapytania:  
  
1.  <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Klony metoda <xref:System.Data.DataTable> z tabeli źródłowej ( <xref:System.Data.DataTable> obiekt, który implementuje <xref:System.Linq.IQueryable%601> interfejsu). <xref:System.Collections.IEnumerable> Źródło ma zazwyczaj pochodzenia [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] wyrażenie lub metody zapytania.  
  
2.  Schemat sklonowany <xref:System.Data.DataTable> została stworzona od kolumny pierwszy wyliczane <xref:System.Data.DataRow> obiektu w tabeli źródłowej i nazwa tabeli sklonowany jest nazwą tabeli źródłowej z wyrazem "query" dołączone do niego.  
  
3.  Dla każdego wiersza w tabeli źródłowej zawartość wiersza jest kopiowany do nowego <xref:System.Data.DataRow> obiektu, który zostanie wstawiony na sklonowanym tabeli. <xref:System.Data.DataRow.RowState%2A> i <xref:System.Data.DataRow.RowError%2A> właściwości są zachowywane w operacji kopiowania. <xref:System.ArgumentException> Jest generowany, jeśli <xref:System.Data.DataRow> obiekty w źródle pochodzą z różnych tabel.  
  
4.  Sklonowany <xref:System.Data.DataTable> jest zwracany po wszystkich <xref:System.Data.DataRow> obiektów w tabeli wejściowej odpytywalny zostały skopiowane. Jeśli sekwencja źródłowa nie zawiera żadnych <xref:System.Data.DataRow> obiektów, metoda zwraca pustą <xref:System.Data.DataTable>.  
  
 Należy pamiętać, że wywołanie <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda spowoduje, że zapytanie powiązane z tabeli źródłowej do wykonania.  
  
 Gdy <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda napotka odwołanie o wartości null lub typ dopuszczający wartość null wartości wiersza w tabeli źródłowej, zastępuje ona wartości z <xref:System.DBNull.Value>. W ten sposób wartości null są obsługiwane poprawnie w zwróconym elemencie <xref:System.Data.DataTable>.  
  
 Uwaga: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda przyjmuje jako dane wejściowe zapytanie, które mogą zwracać wiersze z wieloma <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> obiektów. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda będzie kopiować ze źródła danych, ale nie właściwości <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> obiekty do zwracanego <xref:System.Data.DataTable>. Musisz jawnie ustawić właściwości zwracanego <xref:System.Data.DataTable>, takich jak <xref:System.Data.DataTable.Locale%2A> i <xref:System.Data.DataTable.TableName%2A>.  
  
 W poniższym przykładzie zapytania tabeli SalesOrderHeader zamówień po 8 sierpnia 2001 i używa <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metodę w celu utworzenia <xref:System.Data.DataTable> z tej kwerendy. <xref:System.Data.DataTable> Następnie jest powiązany z <xref:System.Windows.Forms.BindingSource>, który działa jako serwer proxy dla <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Tworzenie niestandardowych CopyToDataTable\<T > — Metoda  
 Istniejące <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody działać tylko w odniesieniu <xref:System.Collections.Generic.IEnumerable%601> źródła gdzie parametr ogólny `T` typu <xref:System.Data.DataRow>. Mimo że jest to przydatne, nie zezwala tabel, które ma zostać utworzony z sekwencji typami skalarnymi, zapytań, które zwracają typów anonimowych lub zapytania, które wykonują sprzężeń tabel. Przykładowy sposób implementacji niestandardowego dwóch `CopyToDataTable` metod, które ładują tabelę z sekwencji typów skalarnych lub anonimowe, zobacz [jak: Implementowanie CopyToDataTable\<T > gdzie ogólny typ T nie jest elementem DataRow](../../../../docs/framework/data/adonet/implement-copytodatatable-where-type-not-a-datarow.md)s.  
  
 Przykłady w tej sekcji należy użyć następujących typów niestandardowych:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Przykład  
 W tym przykładzie wykonuje sprzężenie `SalesOrderHeader` i `SalesOrderDetail` tabele można pobrać zamówień online z sierpień i tworzy tabelę na podstawie zapytania.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład zapytania kolekcji elementów cena jest większa niż 9,99 USD i tworzy tabelę na podstawie wyników zapytania.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wykonuje kwerendę kolekcję elementów cena jest większa niż 9,99 i projekty wyniki. Zwracanej sekwencji anonimowych typów są ładowane do istniejącej tabeli.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wykonuje kwerendę kolekcji elementów cena jest większa niż 9,99 USD i projekty wyniki. Zwracanej sekwencji anonimowych typów są ładowane do istniejącej tabeli. Schemat tabeli automatycznie jest rozwinięta, ponieważ `Book` i `Movies` typy są uzyskiwane z `Item` typu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie zapytania kolekcji elementów cena jest większa niż 9,99 USD i zwraca sekwencję <xref:System.Double>, który jest ładowany do nowej tabeli.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
- [Field i SetField, metody ogólne](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)
- [Przykłady LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
