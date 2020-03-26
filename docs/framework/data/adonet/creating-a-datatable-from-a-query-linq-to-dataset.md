---
title: Tworzenie datatable z kwerendy (LINQ do DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: 46e977088cd6eca7842565ae6b258f70ca5920a9
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111819"
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>Tworzenie datatable z kwerendy (LINQ do DataSet)
Powiązanie danych jest <xref:System.Data.DataTable> typowym zastosowaniem obiektu. Metoda <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> pobiera wyniki kwerendy i kopiuje <xref:System.Data.DataTable>dane do programu , który następnie może służyć do wiązania danych. Po wykonaniu operacji danych nowy <xref:System.Data.DataTable> jest scalany z <xref:System.Data.DataTable>powrotem do źródła .  
  
 Metoda <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> używa następującego procesu do <xref:System.Data.DataTable> utworzenia kwerendy:  
  
1. Metoda <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> klonuje <xref:System.Data.DataTable> z tabeli źródłowej <xref:System.Data.DataTable> (obiekt, <xref:System.Linq.IQueryable%601> który implementuje interfejs). Źródło <xref:System.Collections.IEnumerable> ma zazwyczaj pochodzi z LINQ do dataset wyrażenie lub kwerendy metody.  
  
2. Schemat sklonowanego <xref:System.Data.DataTable> jest zbudowany z kolumn pierwszego wyliczonego <xref:System.Data.DataRow> obiektu w tabeli źródłowej, a nazwa sklonowanej tabeli jest nazwą tabeli źródłowej ze słowem "zapytanie".  
  
3. Dla każdego wiersza w tabeli źródłowej zawartość wiersza <xref:System.Data.DataRow> jest kopiowana do nowego obiektu, który jest następnie wstawiany do sklonowanej tabeli. Właściwości <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRow.RowError%2A> i są zachowywane w całej operacji kopiowania. An <xref:System.ArgumentException> jest generowany, <xref:System.Data.DataRow> jeśli obiekty w źródle są z różnych tabel.  
  
4. Sklonowany <xref:System.Data.DataTable> jest zwracany po skopiowaniu wszystkich <xref:System.Data.DataRow> obiektów w tabeli, w których można wyeksliować. Jeśli sekwencja źródłowsza nie zawiera <xref:System.Data.DataRow> żadnych <xref:System.Data.DataTable>obiektów, metoda zwraca pusty .  
  
Wywołanie <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody powoduje, że kwerenda powiązana z tabelą źródłową do wykonania.  
  
 Gdy <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metoda napotka odwołanie zerowe lub typ wartości nullable w wierszu w <xref:System.DBNull.Value>tabeli źródłowej, zastępuje wartość . W ten sposób wartości null są <xref:System.Data.DataTable>obsługiwane poprawnie w zwróconym .  
  
 Uwaga: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda akceptuje jako dane wejściowe kwerendy, <xref:System.Data.DataTable> <xref:System.Data.DataSet> która może zwracać wiersze z wielu lub obiektów. Metoda <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> skopiuje dane, ale nie <xref:System.Data.DataTable> właściwości <xref:System.Data.DataSet> ze źródła <xref:System.Data.DataTable>lub obiektów do zwracanych . Należy jawnie ustawić właściwości na zwróconych <xref:System.Data.DataTable>, <xref:System.Data.DataTable.Locale%2A> takich <xref:System.Data.DataTable.TableName%2A>jak i .  
  
 Poniższy przykład kwerendy SalesOrderHeader tabeli dla zamówień po 8 sierpnia <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> 2001 r. i używa metody do utworzenia <xref:System.Data.DataTable> z tej kwerendy. Następnie <xref:System.Data.DataTable> jest związany <xref:System.Windows.Forms.BindingSource>z , który działa <xref:System.Windows.Forms.DataGridView>jako pełnomocnik dla .  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Tworzenie metody> niestandardowych\<copytodatatable T  
 Istniejące <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody działają tylko <xref:System.Collections.Generic.IEnumerable%601> na źródle, `T` w <xref:System.Data.DataRow>którym parametr ogólny jest typu . Chociaż jest to przydatne, nie zezwala na tworzenie tabel z sekwencji typów skalarnych, z kwerend zwracających typy anonimowe lub z kwerend, które wykonują sprzężenia tabeli. Na przykład jak zaimplementować dwie metody niestandardowe, `CopyToDataTable` które ładują tabelę z sekwencji typów skalarnych lub anonimowych, zobacz [Jak: Implementowanie CopyToDataTable\<T> Gdzie typ ogólny T nie jest datarow](implement-copytodatatable-where-type-not-a-datarow.md)s.  
  
 Przykłady w tej sekcji używają następujących typów niestandardowych:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Przykład  
 W tym przykładzie wykonuje `SalesOrderHeader` `SalesOrderDetail` sprzężenie za pośrednictwem tabel i, aby uzyskać zamówienia online z miesiąca sierpnia i tworzy tabelę z kwerendy.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#join)]
 [!code-vb[DP Custom CopyToDataTable Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#join)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kwerendy kolekcji dla towarów o cenie większej niż $9.99 i tworzy tabelę z wyników kwerendy.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintotable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintotable)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kwerendy kolekcji dla towarów o cenie większej niż 9,99 i projekty wyniki. Zwrócona sekwencja typów anonimowych jest ładowana do istniejącej tabeli.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsintoexistingtable)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsIntoExistingTable](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsintoexistingtable)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kwerendy kolekcji dla towarów o cenie większej niż $9.99 i projekty wyniki. Zwrócona sekwencja typów anonimowych jest ładowana do istniejącej tabeli. Schemat tabeli jest automatycznie rozwijany, `Book` ponieważ i `Movies` `Item` typy są pochodną typu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kwerendy kolekcji dla towarów o cenie większej niż $9.99 i zwraca sekwencję <xref:System.Double>, który jest ładowany do nowej tabeli.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik po programowaniu](programming-guide-linq-to-dataset.md)
- [Pole ogólne i metody SetField](generic-field-and-setfield-methods-linq-to-dataset.md)
- [Przykłady LINQ to DataSet](linq-to-dataset-examples.md)
