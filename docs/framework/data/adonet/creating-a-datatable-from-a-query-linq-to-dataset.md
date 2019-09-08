---
title: Tworzenie elementu DataTable na podstawie zapytania (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: 4b95ec5a3e83fa5553a154ed64704312726153cf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785628"
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>Tworzenie elementu DataTable na podstawie zapytania (LINQ to DataSet)
Powiązanie danych jest wspólnym zastosowaniem <xref:System.Data.DataTable> obiektu. Metoda pobiera wyniki zapytania i kopiuje dane <xref:System.Data.DataTable>do, które mogą być następnie używane do wiązania danych. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Po wykonaniu operacji na danych nowy <xref:System.Data.DataTable> program zostanie scalony z powrotem ze źródłem. <xref:System.Data.DataTable>  
  
 Metoda używa następującego procesu do <xref:System.Data.DataTable> tworzenia z zapytania: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>  
  
1. Metoda klonuje <xref:System.Data.DataTable> z tabeli źródłowej ( <xref:System.Data.DataTable> obiekt implementujący <xref:System.Linq.IQueryable%601> interfejs). <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> <xref:System.Collections.IEnumerable> Źródło ogólnie pochodzi z kwerendy LINQ to DataSet lub wyrażenia metody.  
  
2. Schemat sklonowanego <xref:System.Data.DataTable> programu jest tworzony na podstawie kolumn pierwszego <xref:System.Data.DataRow> wyliczeniowego obiektu w tabeli źródłowej, a nazwa sklonowanej tabeli to nazwa tabeli źródłowej z dołączonym do niej słowem "Query".  
  
3. Dla każdego wiersza w tabeli źródłowej zawartość wiersza jest kopiowana do nowego <xref:System.Data.DataRow> obiektu, który jest następnie wstawiany do sklonowanej tabeli. Właściwości <xref:System.Data.DataRow.RowState%2A> i<xref:System.Data.DataRow.RowError%2A> są zachowywane przez operację kopiowania. Jest zgłaszany, jeśli obiekty w źródle pochodzą z różnych tabel. <xref:System.Data.DataRow> <xref:System.ArgumentException>  
  
4. Sklonowany <xref:System.Data.DataTable> jest zwracany po skopiowaniu <xref:System.Data.DataRow> wszystkich obiektów w tabeli wejściowej queryable. Jeśli sekwencja źródłowa nie zawiera żadnych <xref:System.Data.DataRow> obiektów, metoda zwraca wartość pustą. <xref:System.Data.DataTable>  
  
 Należy zauważyć, że <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> wywołanie metody spowoduje wykonanie zapytania powiązanego z tabelą źródłową.  
  
 Gdy metoda napotka odwołanie do wartości null lub typ wartości null w wierszu w tabeli źródłowej, zastępuje <xref:System.DBNull.Value>wartość wartością. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> W ten sposób wartości null są obsługiwane poprawnie w zwracanym <xref:System.Data.DataTable>elemencie.  
  
 Uwaga: Metoda akceptuje jako dane wejściowe zapytania, które może zwracać wiersze z wielu <xref:System.Data.DataTable> obiektów <xref:System.Data.DataSet>lub. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda skopiuje dane, ale nie właściwości ze źródła <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> obiektów do zwracanego <xref:System.Data.DataTable>. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Należy jawnie ustawić właściwości zwracanych <xref:System.Data.DataTable>, takich jak <xref:System.Data.DataTable.Locale%2A> i <xref:System.Data.DataTable.TableName%2A>.  
  
 Poniższy przykład wysyła zapytanie do tabeli SalesOrderHeader dla zamówień po 8 sierpnia 2001 i używa <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody do <xref:System.Data.DataTable> utworzenia z tego zapytania. Następnie jest powiązany <xref:System.Windows.Forms.BindingSource>z, który <xref:System.Windows.Forms.DataGridView>działa jako serwer proxy dla. <xref:System.Data.DataTable>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Tworzenie niestandardowej metody CopyToDataTable\<T >  
 Istniejące <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody działają tylko <xref:System.Collections.Generic.IEnumerable%601> względem źródła, w którym parametr `T` generyczny jest typu <xref:System.Data.DataRow>. Chociaż jest to przydatne, nie zezwala na tworzenie tabel z sekwencji typów skalarnych, od zapytań, które zwracają typy anonimowe lub zapytania, które wykonują sprzężenia tabeli. Aby zapoznać się z przykładem implementacji dwóch metod `CopyToDataTable` niestandardowych, które ładują tabelę z sekwencji typów skalarnych lub anonimowych, [zobacz How to: Zaimplementuj\<CopyToDataTable T >, gdzie typ ogólny t nie jest typem](implement-copytodatatable-where-type-not-a-datarow.md)DataRow s.  
  
 W przykładach w tej sekcji są używane następujące typy niestandardowe:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Przykład  
 Ten przykład wykonuje sprzężenie `SalesOrderHeader` w tabelach i `SalesOrderDetail` w celu uzyskania zamówień online od miesiąca sierpnia i tworzy tabelę na podstawie zapytania.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wysyła zapytanie do kolekcji dla elementów ceny większej niż $9,99 i tworzy tabelę na podstawie wyników zapytania.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wysyła zapytanie do kolekcji dla elementów ceny większej niż 9,99 i projektuje wyniki. Zwracana sekwencja typów anonimowych jest ładowana do istniejącej tabeli.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wysyła zapytanie do kolekcji dla elementów ceny większej niż $9,99 i projektuje wyniki. Zwracana sekwencja typów anonimowych jest ładowana do istniejącej tabeli. Schemat tabeli jest automatycznie rozwijany, ponieważ `Book` `Item` typy `Movies` i pochodzą od typu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wysyła zapytanie do kolekcji dla elementów ceny większej niż $9,99 i zwraca sekwencję <xref:System.Double>, która jest ładowana do nowej tabeli.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania](programming-guide-linq-to-dataset.md)
- [Pole ogólne i metody SetField](generic-field-and-setfield-methods-linq-to-dataset.md)
- [Przykłady LINQ to DataSet](linq-to-dataset-examples.md)
