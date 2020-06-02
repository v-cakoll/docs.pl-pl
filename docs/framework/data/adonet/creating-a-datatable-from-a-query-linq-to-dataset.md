---
title: Tworzenie elementu DataTable na podstawie zapytania (LINQ to DataSet)
description: Dowiedz się, jak użyć metody CopyToDataTable, aby pobrać wyniki zapytania i skopiować dane do elementu DataTable, który można następnie użyć do wiązania danych.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b97afeb-03f8-41e2-8eb3-58aff65f7d18
ms.openlocfilehash: 0a7c8f005b90484ef2f9c7e48218bda40533696a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287015"
---
# <a name="creating-a-datatable-from-a-query-linq-to-dataset"></a>Tworzenie elementu DataTable na podstawie zapytania (LINQ to DataSet)
Powiązanie danych jest wspólnym zastosowaniem <xref:System.Data.DataTable> obiektu. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metoda pobiera wyniki zapytania i kopiuje dane do <xref:System.Data.DataTable> , które mogą być następnie używane do wiązania danych. Po wykonaniu operacji na danych nowy program <xref:System.Data.DataTable> zostanie scalony z powrotem ze źródłem <xref:System.Data.DataTable> .  
  
 <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metoda używa następującego procesu do tworzenia <xref:System.Data.DataTable> z zapytania:  
  
1. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metoda klonuje <xref:System.Data.DataTable> z tabeli źródłowej ( <xref:System.Data.DataTable> obiekt implementujący <xref:System.Linq.IQueryable%601> interfejs). <xref:System.Collections.IEnumerable>Źródło ogólnie pochodzi z kwerendy LINQ to DataSet lub wyrażenia metody.  
  
2. Schemat sklonowanego programu <xref:System.Data.DataTable> jest tworzony na podstawie kolumn pierwszego wyliczeniowego <xref:System.Data.DataRow> obiektu w tabeli źródłowej, a nazwa sklonowanej tabeli to nazwa tabeli źródłowej z dołączonym do niej słowem "Query".  
  
3. Dla każdego wiersza w tabeli źródłowej zawartość wiersza jest kopiowana do nowego <xref:System.Data.DataRow> obiektu, który jest następnie wstawiany do sklonowanej tabeli. <xref:System.Data.DataRow.RowState%2A>Właściwości i <xref:System.Data.DataRow.RowError%2A> są zachowywane przez operację kopiowania. <xref:System.ArgumentException>Jest zgłaszany, jeśli <xref:System.Data.DataRow> obiekty w źródle pochodzą z różnych tabel.  
  
4. Sklonowany <xref:System.Data.DataTable> jest zwracany po <xref:System.Data.DataRow> skopiowaniu wszystkich obiektów w tabeli wejściowej queryable. Jeśli sekwencja źródłowa nie zawiera żadnych <xref:System.Data.DataRow> obiektów, metoda zwraca wartość pustą <xref:System.Data.DataTable> .  
  
Wywołanie <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody powoduje wykonanie zapytania powiązanego z tabelą źródłową.  
  
 Gdy <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda napotka odwołanie do wartości null lub typ wartości null w wierszu w tabeli źródłowej, zastępuje wartość wartością <xref:System.DBNull.Value> . W ten sposób wartości null są obsługiwane poprawnie w zwracanym elemencie <xref:System.Data.DataTable> .  
  
 Uwaga: <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> Metoda akceptuje jako dane wejściowe zapytania, które może zwracać wiersze z wielu <xref:System.Data.DataTable> <xref:System.Data.DataSet> obiektów lub. <xref:System.Data.DataTableExtensions.CopyToDataTable%2A>Metoda skopiuje dane, ale nie właściwości ze źródła <xref:System.Data.DataTable> lub <xref:System.Data.DataSet> obiektów do zwracanego <xref:System.Data.DataTable> . Należy jawnie ustawić właściwości zwracanych <xref:System.Data.DataTable> , takich jak <xref:System.Data.DataTable.Locale%2A> i <xref:System.Data.DataTable.TableName%2A> .  
  
 Poniższy przykład wysyła zapytanie do tabeli SalesOrderHeader dla zamówień po 8 sierpnia 2001 i używa <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody do utworzenia <xref:System.Data.DataTable> z tego zapytania. <xref:System.Data.DataTable>Następnie jest powiązany z <xref:System.Windows.Forms.BindingSource> , który działa jako serwer proxy dla <xref:System.Windows.Forms.DataGridView> .  
  
 [!code-csharp[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#copytodatatable1)]
 [!code-vb[DP LINQ to DataSet Examples#CopyToDataTable1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#copytodatatable1)]  
  
## <a name="creating-a-custom-copytodatatablet-method"></a>Tworzenie niestandardowej metody CopyToDataTable \<T>  
 Istniejące <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> metody działają tylko względem <xref:System.Collections.Generic.IEnumerable%601> źródła, w którym parametr generyczny `T` jest typu <xref:System.Data.DataRow> . Chociaż jest to przydatne, nie zezwala na tworzenie tabel z sekwencji typów skalarnych, od zapytań, które zwracają typy anonimowe lub zapytania, które wykonują sprzężenia tabeli. Aby zapoznać się z przykładem sposobu implementacji dwóch `CopyToDataTable` metod niestandardowych, które ładują tabelę z sekwencji typów skalarnych lub anonimowych, zobacz [How to: Implementuj CopyToDataTable \<T> , gdzie typ ogólny T nie jest typem DataRow](implement-copytodatatable-where-type-not-a-datarow.md)s.  
  
 W przykładach w tej sekcji są używane następujące typy niestandardowe:  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#itemclass)]
 [!code-vb[DP Custom CopyToDataTable Examples#ItemClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#itemclass)]  
  
### <a name="example"></a>Przykład  
 Ten przykład wykonuje sprzężenie w `SalesOrderHeader` tabelach i `SalesOrderDetail` w celu uzyskania zamówień online od miesiąca sierpnia i tworzy tabelę na podstawie zapytania.  
  
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
 Poniższy przykład wysyła zapytanie do kolekcji dla elementów ceny większej niż $9,99 i projektuje wyniki. Zwracana sekwencja typów anonimowych jest ładowana do istniejącej tabeli. Schemat tabeli jest automatycznie rozwijany, ponieważ `Book` typy i pochodzą `Movies` od `Item` typu.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loaditemsexpandschema)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadItemsExpandSchema](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loaditemsexpandschema)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład wysyła zapytanie do kolekcji dla elementów ceny większej niż $9,99 i zwraca sekwencję <xref:System.Double> , która jest ładowana do nowej tabeli.  
  
 [!code-csharp[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#loadscalarsequence)]
 [!code-vb[DP Custom CopyToDataTable Examples#LoadScalarSequence](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#loadscalarsequence)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania](programming-guide-linq-to-dataset.md)
- [Pole ogólne i metody SetField](generic-field-and-setfield-methods-linq-to-dataset.md)
- [Przykłady LINQ to DataSet](linq-to-dataset-examples.md)
