---
title: Obsługa wartości Null
description: Dowiedz się, w jaki sposób Dostawca danych .NET Framework dla SQL Server obsługuje wartość null, i przeczytaj informacje o wartościach null i SqlBoolean, z których ma być przypisana wartość null.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: a4d086d81f1c2c959780366cfeb59f2d265bc40c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286458"
---
# <a name="handling-null-values"></a>Obsługa wartości Null
Wartość null w relacyjnej bazie danych jest używana, gdy wartość w kolumnie jest nieznana lub brakująca. Wartość null nie jest ciągiem pustym (dla typów danych znakowych lub DateTime) ani wartością zerową (dla liczbowych typów danych). Specyfikacja ANSI SQL-92 stwierdza, że wartość null musi być taka sama dla wszystkich typów danych, tak aby wszystkie wartości null były obsługiwane spójnie. <xref:System.Data.SqlTypes>Przestrzeń nazw zapewnia semantykę o wartości null przez implementację <xref:System.Data.SqlTypes.INullable> interfejsu. Każdy z typów danych w programie <xref:System.Data.SqlTypes> ma własną `IsNull` Właściwość i `Null` wartość, która może być przypisana do wystąpienia tego typu danych.  
  
> [!NOTE]
> W .NET Framework w wersji 2,0 wprowadzono obsługę typów wartości dopuszczających wartość null, dzięki czemu programiści mogą rozwijać typ wartości reprezentujący wszystkie wartości typu podstawowego. Te typy wartości null CLR reprezentują wystąpienie <xref:System.Nullable> struktury. Ta funkcja jest szczególnie przydatna, gdy typy wartości są opakowane i rozpakowane, zapewniając zwiększoną zgodność z typami obiektów. Typy wartości null CLR nie są przeznaczone do przechowywania wartości null bazy danych, ponieważ wartość null w formacie ANSI nie zachowuje się tak samo jak `null` w przypadku odwołania (lub `Nothing` w Visual Basic). W przypadku pracy z bazami danych ANSI SQL o wartości null Użyj <xref:System.Data.SqlTypes> wartości null zamiast <xref:System.Nullable> . Aby uzyskać więcej informacji na temat pracy z typami CLR wartości null w Visual Basic zobacz [dopuszczanie typów wartości null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), a dla języka C# zobacz [dopuszczanie typów wartości](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Wartości null i logika trzech wartości  
 Zezwalanie na wartości null w definicjach kolumn wprowadza do aplikacji logiczną trzy wartości. Porównanie może wynikać z jednego z trzech warunków:  
  
- True  
  
- Fałsz  
  
- Nieznane  
  
 Ponieważ wartość null jest uznawana za nieznaną, dwie wartości null w porównaniu do siebie nie są traktowane jako równe. W wyrażeniach wykorzystujących operatory arytmetyczne, jeśli którykolwiek z operandów ma wartość null, wynik jest również równy null.  
  
## <a name="nulls-and-sqlboolean"></a>Wartości null i SqlBoolean  
 Porównanie między dowolnymi zwróci <xref:System.Data.SqlTypes> wynik <xref:System.Data.SqlTypes.SqlBoolean> . `IsNull`Funkcja dla każdej `SqlType` zwraca <xref:System.Data.SqlTypes.SqlBoolean> i może służyć do sprawdzania wartości null. Następujące tabele prawdy pokazują, jak i, lub, i nie operatory, w obecności wartości null. (T = true, F = false i U = Unknown lub null).  
  
 ![Tabela prawdy](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Zrozumienie opcji ANSI_NULLS  
 <xref:System.Data.SqlTypes>zapewnia taką samą semantykę, jak w przypadku ustawienia opcji ANSI_NULLS w SQL Server. Wszystkie operatory arytmetyczne (+,-, \* ,/,%), operatory bitowe (~, &, \| ) i większość funkcji zwracają wartość null, jeśli którykolwiek z operandów lub argumentów ma wartość null, z wyjątkiem właściwości `IsNull` .  
  
 Standard ANSI SQL-92 nie obsługuje elementu *ColumnName* = null w klauzuli WHERE. W SQL Server opcja ANSI_NULLS steruje domyślną wartością null w bazie danych i ocenie porównań z wartościami null. Jeśli ANSI_NULLS jest włączona (wartość domyślna), operator IS NULL musi być używany w wyrażeniach podczas testowania wartości null. Na przykład następujące porównanie zawsze jest nieznane, gdy ANSI_NULLS jest włączone:  
  
```sql
colname > NULL  
```  
  
 Porównanie do zmiennej zawierającej wartość null daje również nieznane:  
  
```sql
colname > @MyVariable  
```  
  
 Użyj predykatu IS NULL lub IS NOT NULL, aby przetestować wartość null. Może to zwiększyć złożoność do klauzuli WHERE. Na przykład kolumna TerritoryID w tabeli klient AdventureWorks pozwala na wartości null. Jeśli instrukcja SELECT ma przetestować pod kątem wartości null oprócz innych, musi zawierać predykat IS NULL:  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 Jeśli ustawiono ANSI_NULLS wyłączone w SQL Server, można utworzyć wyrażenia, które używają operatora równości do porównywania z wartością null. Nie można jednak uniemożliwiać różnych połączeń z ustawieniem opcji null dla tego połączenia. Używanie funkcji IS NULL do testowania wartości null zawsze działa, niezależnie od ustawień ANSI_NULLS dla połączenia.  
  
 Ustawienie ANSI_NULLS off nie jest obsługiwane w elemencie `DataSet` , który jest zawsze zgodny ze standardem ANSI SQL-92 w celu obsługi wartości null w <xref:System.Data.SqlTypes> .  
  
## <a name="assigning-null-values"></a>Przypisywanie wartości null  
 Wartości null są specjalne, a ich semantyka przechowywania i przypisywania różni się w różnych systemach typów i systemach magazynowania. `Dataset`Program jest przeznaczony do użycia z różnymi systemami typu i magazynowania.  
  
 W tej sekcji opisano semantykę wartości null do przypisywania wartości null do a <xref:System.Data.DataColumn> w <xref:System.Data.DataRow> różnych systemach typów.  
  
 `DBNull.Value`  
 To przypisanie jest prawidłowe dla `DataColumn` dowolnego typu. Jeśli typ implementuje `INullable` , `DBNull.Value` jest przekształcany na odpowiednią silnie wpisaną wartość null.  
  
 `SqlType.Null`  
 <xref:System.Data.SqlTypes>Implementuje wszystkie typy danych `INullable` . Jeśli silnie wpisana wartość null może zostać przekonwertowana na typ danych kolumny przy użyciu niejawnych operatorów rzutowania, przypisanie powinno nastąpić przez. W przeciwnym razie zostanie zgłoszony nieprawidłowy wyjątek rzutowania.  
  
 `null`  
 Jeśli wartość "null" jest wartością prawną dla danego `DataColumn` typu danych, jest ona przekształcana w odpowiednią `DbNull.Value` lub `Null` skojarzona z `INullable` typem ( `SqlType.Null` )  
  
 `derivedUdt.Null`  
 W przypadku kolumn UDT wartości null są zawsze przechowywane na podstawie typu skojarzonego z `DataColumn` . Rozważ przypadek, który jest skojarzony z elementem `DataColumn` , który nie implementuje, `INullable` gdy jego podklasa jest. W takim przypadku, jeśli zostanie przypisana silnie wpisana wartość null skojarzona z klasą pochodną, jest ona przechowywana jako bez typu `DbNull.Value` , ponieważ magazyn o wartości null jest zawsze spójny z typem danych DataColumn.  
  
> [!NOTE]
> `Nullable<T>`Struktura lub <xref:System.Nullable> nie jest obecnie obsługiwana w `DataSet` .  
  
### <a name="multiple-column-row-assignment"></a>Przypisanie wielu kolumn (wierszy)  
 `DataTable.Add`, `DataTable.LoadDataRow` lub inne interfejsy API, które akceptują <xref:System.Data.DataRow.ItemArray%2A> , które są zamapowane na wiersz, mapują wartość "null" do wartości domyślnej DataColumn. Jeśli obiekt w tablicy zawiera `DbNull.Value` lub jego silnie wpisaną, te same reguły, jak opisano powyżej, są stosowane.  
  
 Ponadto dla wystąpienia `DataRow.["columnName"]` przypisań o wartości null są stosowane następujące reguły:  
  
1. Domyślna wartość *Domyślna* to `DbNull.Value` dla wszystkich, z wyjątkiem kolumn o jednoznacznie określonym typie, w których jest to odpowiednia silnie wpisana wartość null.  
  
2. Wartości null nigdy nie są zapisywane podczas serializacji do plików XML (podobnie jak w przypadku elementu "xsi: nil").  
  
3. Wszystkie wartości inne niż null, w tym wartości domyślne, są zawsze zapisywane podczas serializacji do formatu XML. Jest to w przeciwieństwie do semantyki XSD/XML, gdzie wartość null (xsi: nil) jest jawna i wartość domyślna jest niejawna (jeśli nie jest obecny w kodzie XML, Analizator sprawdzania poprawności może pobrać go ze skojarzonego schematu XSD). Przeciwieństwo jest prawdziwe dla `DataTable` : wartość null jest niejawna, a wartość domyślna to explicit.  
  
4. Wszystkie brakujące wartości kolumn dla wierszy odczytanych z danych wejściowych XML mają przypisane wartość NULL. Do wierszy utworzonych przy użyciu <xref:System.Data.DataTable.NewRow%2A> lub podobnych metod są przypisywane wartości domyślnej kolumny DataColumn.  
  
5. <xref:System.Data.DataRow.IsNull%2A>Metoda zwraca `true` dla obu `DbNull.Value` i `INullable.Null` .  
  
## <a name="assigning-null-values"></a>Przypisywanie wartości null  
 Wartość domyślna dla dowolnego <xref:System.Data.SqlTypes> wystąpienia ma wartość null.  
  
 Wartości null w <xref:System.Data.SqlTypes> są specyficzne dla typu i nie mogą być reprezentowane przez pojedynczą wartość, na przykład `DbNull` . Użyj `IsNull` właściwości, aby sprawdzić wartości null.  
  
 Wartości null można przypisywać do typu <xref:System.Data.DataColumn> , tak jak pokazano w poniższym przykładzie kodu. Można bezpośrednio przypisywać wartości null do `SqlTypes` zmiennych bez wyzwalania wyjątku.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy <xref:System.Data.DataTable> z dwoma kolumnami zdefiniowanymi jako <xref:System.Data.SqlTypes.SqlInt32> i <xref:System.Data.SqlTypes.SqlString> . Kod dodaje jeden wiersz znanych wartości, jeden wiersz wartości null, a następnie iteruje przez <xref:System.Data.DataTable> , przypisując wartości do zmiennych i wyświetlając dane wyjściowe w oknie konsoli.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 W tym przykładzie są wyświetlane następujące wyniki:  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Porównywanie wartości null z typami SqlTypes i CLR  
 Porównując wartości null, ważne jest, aby zrozumieć różnicę między sposobem, `Equals` w jaki Metoda szacuje wartości null w <xref:System.Data.SqlTypes> porównaniu ze sposobem, w jaki działa z typami CLR. Wszystkie <xref:System.Data.SqlTypes> `Equals` metody używają semantyki bazy danych do oceny wartości null: Jeśli jedna lub obie wartości mają wartość null, porównanie daje wartość null. Z drugiej strony, użycie `Equals` metody CLR na dwóch <xref:System.Data.SqlTypes> zwróci wartość true, jeśli oba mają wartość null. Odzwierciedla to różnicę między użyciem metody wystąpienia, takiej jak `String.Equals` Metoda CLR, i przy użyciu metody static/Shared `SqlString.Equals` .  
  
 Poniższy przykład ilustruje różnicę w wynikach między `SqlString.Equals` metodą i `String.Equals` metodą, gdy każda z nich przekazuje parę wartości null, a następnie parę pustych ciągów.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 Kod generuje następujące dane wyjściowe:  
  
```output
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True
```  
  
## <a name="see-also"></a>Zobacz także

- [Typy danych programu SQL Server i ADO.NET](sql-server-data-types.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
