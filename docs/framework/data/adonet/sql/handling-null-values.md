---
title: Obsługa wartości Null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 091fde9a6149f72577e0cf38c8ebf1536abdf6ea
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738203"
---
# <a name="handling-null-values"></a>Obsługa wartości Null
Wartość null w relacyjnej bazie danych jest używana, gdy wartość w kolumnie jest nieznana lub brakująca. Wartość null nie jest ciągiem pustym (dla typów danych znakowych lub DateTime) ani wartością zerową (dla liczbowych typów danych). Specyfikacja ANSI SQL-92 stwierdza, że wartość null musi być taka sama dla wszystkich typów danych, tak aby wszystkie wartości null były obsługiwane spójnie. Przestrzeń nazw <xref:System.Data.SqlTypes> zapewnia semantykę o wartości null przez implementację interfejsu <xref:System.Data.SqlTypes.INullable>. Każdy typ danych w <xref:System.Data.SqlTypes> ma własną Właściwość `IsNull` i `Null` wartość, która może być przypisana do wystąpienia tego typu danych.  
  
> [!NOTE]
> W .NET Framework w wersji 2,0 wprowadzono obsługę typów dopuszczających wartości null, dzięki czemu programiści mogą rozwijać typ wartości reprezentujący wszystkie wartości typu podstawowego. Te typy CLR dopuszczające wartość null reprezentują wystąpienie struktury <xref:System.Nullable>. Ta funkcja jest szczególnie przydatna, gdy typy wartości są opakowane i rozpakowane, zapewniając zwiększoną zgodność z typami obiektów. Typy CLR dopuszczające wartości null nie są przeznaczone do przechowywania wartości null bazy danych, ponieważ wartość null w formacie ANSI nie zachowuje się tak samo jak odwołanie `null` (lub `Nothing` w Visual Basic). W przypadku pracy z bazami danych ANSI języka SQL o wartości null należy używać <xref:System.Data.SqlTypes> wartości null, a nie <xref:System.Nullable>. Aby uzyskać więcej informacji na temat pracy z typami CLR dopuszczających wartości null w Visual Basic zobacz [typy wartości null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)i dla C# zobacz [typy wartości null](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Wartości null i logika trzech wartości  
 Zezwalanie na wartości null w definicjach kolumn wprowadza do aplikacji logiczną trzy wartości. Porównanie może wynikać z jednego z trzech warunków:  
  
- Oznacza  
  
- False  
  
- Nieznany  
  
 Ponieważ wartość null jest uznawana za nieznaną, dwie wartości null w porównaniu do siebie nie są traktowane jako równe. W wyrażeniach wykorzystujących operatory arytmetyczne, jeśli którykolwiek z operandów ma wartość null, wynik jest również równy null.  
  
## <a name="nulls-and-sqlboolean"></a>Wartości null i SqlBoolean  
 Porównanie między dowolnymi <xref:System.Data.SqlTypes> zwróci <xref:System.Data.SqlTypes.SqlBoolean>. Funkcja `IsNull` dla każdej `SqlType` zwraca <xref:System.Data.SqlTypes.SqlBoolean> i może służyć do sprawdzania wartości null. Następujące tabele prawdy pokazują, jak i, lub, i nie operatory, w obecności wartości null. (T = true, F = false i U = Unknown lub null).  
  
 ![Tabela prawdy](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Zrozumienie opcji ANSI_NULLS  
 <xref:System.Data.SqlTypes> zapewnia taką samą semantykę, jak w przypadku ustawienia opcji ANSI_NULLS w SQL Server. Wszystkie operatory arytmetyczne (+,-, \*,/,%), operatory bitowe (~, &, \|) i większość funkcji zwracają wartość null, jeśli którykolwiek z operandów lub argumentów ma wartość null, z wyjątkiem `IsNull`właściwości.  
  
 Standard ANSI SQL-92 nie obsługuje elementu *ColumnName* = null w klauzuli WHERE. W SQL Server opcja ANSI_NULLS steruje domyślną wartością null w bazie danych i oceną porównania z wartościami null. Jeśli ANSI_NULLS jest włączona (wartość domyślna), operator IS NULL musi być używany w wyrażeniach podczas testowania wartości null. Na przykład następujące porównanie zawsze jest nieznane, gdy ANSI_NULLS jest włączone:  
  
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
  
 W przypadku ustawienia opcji ANSI_NULLS off w SQL Server można utworzyć wyrażenia, które używają operatora równości do porównywania z wartością null. Nie można jednak uniemożliwiać różnych połączeń z ustawieniem opcji null dla tego połączenia. Używanie funkcji IS NULL do testowania wartości null zawsze działa, niezależnie od ustawień ANSI_NULLS dla połączenia.  
  
 Ustawienie ANSI_NULLS off nie jest obsługiwane w `DataSet`, które jest zawsze zgodne ze standardem ANSI SQL-92 na potrzeby obsługi wartości null w <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Przypisywanie wartości null  
 Wartości null są specjalne, a ich semantyka przechowywania i przypisywania różni się w różnych systemach typów i systemach magazynowania. `Dataset` jest przeznaczony do użycia z różnymi systemami typów i magazynowania.  
  
 W tej sekcji opisano semantykę wartości null do przypisywania wartości null do <xref:System.Data.DataColumn> w <xref:System.Data.DataRow>ch w różnych systemach typu.  
  
 `DBNull.Value`  
 To przypisanie jest prawidłowe dla `DataColumn` dowolnego typu. Jeśli typ implementuje `INullable`, `DBNull.Value` jest przekształcony w odpowiednią wartość null o jednoznacznie określonym typie.  
  
 `SqlType.Null`  
 Wszystkie <xref:System.Data.SqlTypes> typy danych implementują `INullable`. Jeśli silnie wpisana wartość null może zostać przekonwertowana na typ danych kolumny przy użyciu niejawnych operatorów rzutowania, przypisanie powinno nastąpić przez. W przeciwnym razie zostanie zgłoszony nieprawidłowy wyjątek rzutowania.  
  
 `null`  
 Jeśli wartość "null" jest wartością prawną dla danego typu danych `DataColumn`, zostanie ona przekształcona w odpowiednie `DbNull.Value` lub `Null` skojarzona z typem `INullable` (`SqlType.Null`)  
  
 `derivedUdt.Null`  
 W przypadku kolumn UDT wartości null są zawsze przechowywane na podstawie typu skojarzonego z `DataColumn`. Rozważmy przypadek typu UDT skojarzony z `DataColumn`, który nie implementuje `INullable`, gdy jego podklasa wykonuje. W takim przypadku, jeśli zostanie przypisana silnie wpisana wartość null skojarzona z klasą pochodną, jest ona przechowywana jako `DbNull.Value`bez typu, ponieważ magazyn o wartości null jest zawsze spójny z typem danych DataColumn.  
  
> [!NOTE]
> Struktura `Nullable<T>` lub <xref:System.Nullable> nie jest obecnie obsługiwana w `DataSet`.  
  
### <a name="multiple-column-row-assignment"></a>Przypisanie wielu kolumn (wierszy)  
 `DataTable.Add`, `DataTable.LoadDataRow`lub inne interfejsy API, które akceptują <xref:System.Data.DataRow.ItemArray%2A>, które są mapowane na wiersz, mapują wartości null na wartość domyślną DataColumn. Jeśli obiekt w tablicy zawiera `DbNull.Value` lub jego silnie wpisaną, te same reguły, jak opisano powyżej, są stosowane.  
  
 Ponadto dla wystąpienia `DataRow.["columnName"]` przypisań null mają zastosowanie następujące reguły:  
  
1. Domyślna wartość *Domyślna* to `DbNull.Value` dla wszystkich z wyjątkiem kolumn o jednoznacznie określonym typie, w których jest to odpowiednia silna wartość null.  
  
2. Wartości null nigdy nie są zapisywane podczas serializacji do plików XML (podobnie jak w przypadku elementu "xsi: nil").  
  
3. Wszystkie wartości inne niż null, w tym wartości domyślne, są zawsze zapisywane podczas serializacji do formatu XML. Jest to w przeciwieństwie do semantyki XSD/XML, gdzie wartość null (xsi: nil) jest jawna i wartość domyślna jest niejawna (jeśli nie jest obecny w kodzie XML, Analizator sprawdzania poprawności może pobrać go ze skojarzonego schematu XSD). Przeciwieństwem jest wartość true dla `DataTable`: wartość null jest niejawna, a wartość domyślna to explicit.  
  
4. Wszystkie brakujące wartości kolumn dla wierszy odczytanych z danych wejściowych XML mają przypisane wartość NULL. Wiersze utworzone przy użyciu <xref:System.Data.DataTable.NewRow%2A> lub podobnych metod są przypisane do wartości domyślnej kolumny DataColumn.  
  
5. Metoda <xref:System.Data.DataRow.IsNull%2A> zwraca `true` zarówno dla `DbNull.Value`, jak i `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Przypisywanie wartości null  
 Wartość domyślna dla dowolnego wystąpienia <xref:System.Data.SqlTypes> ma wartość null.  
  
 Wartości null w <xref:System.Data.SqlTypes> są specyficzne dla typu i nie mogą być reprezentowane przez pojedynczą wartość, na przykład `DbNull`. Użyj właściwości `IsNull`, aby sprawdzić wartości null.  
  
 Wartości null można przypisywać do <xref:System.Data.DataColumn>, jak pokazano w poniższym przykładzie kodu. Można bezpośrednio przypisywać wartości null do zmiennych `SqlTypes` bez wyzwalania wyjątku.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy <xref:System.Data.DataTable> z dwiema kolumnami zdefiniowanymi jako <xref:System.Data.SqlTypes.SqlInt32> i <xref:System.Data.SqlTypes.SqlString>. Kod dodaje jeden wiersz znanych wartości, jeden wiersz wartości null, a następnie iteruje przez <xref:System.Data.DataTable>, przypisując wartości do zmiennych i wyświetlając dane wyjściowe w oknie konsoli.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 W tym przykładzie są wyświetlane następujące wyniki:  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Porównywanie wartości null z typami SqlTypes i CLR  
 Porównując wartości null, ważne jest, aby zrozumieć różnicę między sposobem, w jaki Metoda `Equals` oblicza wartości null w <xref:System.Data.SqlTypes> w porównaniu z sposobem działania z typami CLR. Wszystkie <xref:System.Data.SqlTypes>metody`Equals` używają semantyki bazy danych do oceny wartości null: Jeśli jedna lub obie wartości mają wartość null, porównanie daje wartość null. Z drugiej strony, użycie metody CLR `Equals` w dwóch <xref:System.Data.SqlTypes> zwróci wartość true, jeśli oba mają wartość null. Odzwierciedla to różnicę między użyciem metody wystąpienia, takiej jak Metoda `String.Equals` CLR i użycie metody static/Shared, `SqlString.Equals`.  
  
 Poniższy przykład ilustruje różnicę w wynikach między metodą `SqlString.Equals` a metodą `String.Equals`, gdy każda z nich przekazała parę wartości null, a następnie parę pustych ciągów.  
  
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
