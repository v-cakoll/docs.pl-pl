---
title: Obsługa wartości Null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 077cfd9b90df130e0a6090637d5dbd70a70930b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938184"
---
# <a name="handling-null-values"></a>Obsługa wartości Null
Wartość null w relacyjnej bazie danych jest używana, gdy wartość w kolumnie jest nieznana lub brakująca. Wartość null nie jest ciągiem pustym (dla typów danych znakowych lub DateTime) ani wartością zerową (dla liczbowych typów danych). Specyfikacja ANSI SQL-92 stwierdza, że wartość null musi być taka sama dla wszystkich typów danych, tak aby wszystkie wartości null były obsługiwane spójnie. Przestrzeń nazw zapewnia semantykę o wartości null przez <xref:System.Data.SqlTypes.INullable> implementację interfejsu. <xref:System.Data.SqlTypes> Każdy z typów danych w programie <xref:System.Data.SqlTypes> ma własną `IsNull` Właściwość i `Null` wartość, która może być przypisana do wystąpienia tego typu danych.  
  
> [!NOTE]
> W .NET Framework w wersji 2,0 wprowadzono obsługę typów dopuszczających wartości null, dzięki czemu programiści mogą rozwijać typ wartości reprezentujący wszystkie wartości typu podstawowego. Te typy CLR dopuszczające wartość null reprezentują wystąpienie <xref:System.Nullable> struktury. Ta funkcja jest szczególnie przydatna, gdy typy wartości są opakowane i rozpakowane, zapewniając zwiększoną zgodność z typami obiektów. Typy CLR nullable nie są przeznaczone do przechowywania wartości null bazy danych, ponieważ wartość null w formacie ANSI nie zachowuje się tak samo jak `null` w przypadku odwołania `Nothing` (lub w Visual Basic). W przypadku pracy z bazami danych ANSI SQL o <xref:System.Data.SqlTypes> wartości null Użyj wartości <xref:System.Nullable>null zamiast. Aby uzyskać więcej informacji na temat pracy z typami CLR dopuszczających wartości null w Visual Basic zobacz [typy wartości null](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)i C# zobacz [używanie typów dopuszczających wartość null](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Wartości null i logika trzech wartości  
 Zezwalanie na wartości null w definicjach kolumn wprowadza do aplikacji logiczną trzy wartości. Porównanie może wynikać z jednego z trzech warunków:  
  
- Prawda  
  
- False  
  
- Nieznany  
  
 Ponieważ wartość null jest uznawana za nieznaną, dwie wartości null w porównaniu do siebie nie są traktowane jako równe. W wyrażeniach wykorzystujących operatory arytmetyczne, jeśli którykolwiek z operandów ma wartość null, wynik jest również równy null.  
  
## <a name="nulls-and-sqlboolean"></a>Wartości null i SqlBoolean  
 Porównanie między dowolnymi <xref:System.Data.SqlTypes> zwróci <xref:System.Data.SqlTypes.SqlBoolean>wynik. Funkcja dla każdej `SqlType` zwraca<xref:System.Data.SqlTypes.SqlBoolean> i może służyć do sprawdzania wartości null. `IsNull` Następujące tabele prawdy pokazują, jak i, lub, i nie operatory, w obecności wartości null. (T = true, F = false i U = Unknown lub null).  
  
 ![Tabela prawdy](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Zrozumienie opcji ANSI_NULLS  
 <xref:System.Data.SqlTypes>zapewnia tę samą semantykę, co, gdy opcja ANSI_NULLS jest ustawiona na w SQL Server. Wszystkie operatory arytmetyczne (+,-, *,/,%), operatory bitowe (~, & &#124;,) i większość funkcji zwracają wartość null, jeśli którykolwiek z operandów lub argumentów ma wartość null, z wyjątkiem `IsNull`właściwości.  
  
 Standard ANSI SQL-92 nie obsługuje elementu *ColumnName* = null w klauzuli WHERE. W SQL Server opcja ANSI_NULLS steruje domyślną wartością null w bazie danych i oceną porównania z wartościami null. Jeśli ANSI_NULLS jest włączona (wartość domyślna), operator IS NULL musi być używany w wyrażeniach podczas testowania wartości null. Na przykład następujące porównanie zawsze jest nieznane, gdy ANSI_NULLS jest włączone:  
  
```  
colname > NULL  
```  
  
 Porównanie do zmiennej zawierającej wartość null daje również nieznane:  
  
```  
colname > @MyVariable  
```  
  
 Użyj predykatu IS NULL lub IS NOT NULL, aby przetestować wartość null. Może to zwiększyć złożoność do klauzuli WHERE. Na przykład kolumna TerritoryID w tabeli klient AdventureWorks pozwala na wartości null. Jeśli instrukcja SELECT ma przetestować pod kątem wartości null oprócz innych, musi zawierać predykat IS NULL:  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 W przypadku ustawienia opcji ANSI_NULLS off w SQL Server można utworzyć wyrażenia, które używają operatora równości do porównywania z wartością null. Nie można jednak uniemożliwiać różnych połączeń z ustawieniem opcji null dla tego połączenia. Używanie funkcji IS NULL do testowania wartości null zawsze działa, niezależnie od ustawień ANSI_NULLS dla połączenia.  
  
 Ustawienie ANSI_NULLS off nie jest obsługiwane w `DataSet`elemencie, który jest zawsze zgodny ze standardem ANSI SQL-92 w celu obsługi wartości null w. <xref:System.Data.SqlTypes>  
  
## <a name="assigning-null-values"></a>Przypisywanie wartości null  
 Wartości null są specjalne, a ich semantyka przechowywania i przypisywania różni się w różnych systemach typów i systemach magazynowania. Program `Dataset` jest przeznaczony do użycia z różnymi systemami typu i magazynowania.  
  
 W tej sekcji opisano semantykę wartości null do przypisywania wartości <xref:System.Data.DataColumn> null do <xref:System.Data.DataRow> a w różnych systemach typów.  
  
 `DBNull.Value`  
 To przypisanie jest prawidłowe dla `DataColumn` dowolnego typu. Jeśli typ implementuje `INullable`, `DBNull.Value` jest przekształcany na odpowiednią silnie wpisaną wartość null.  
  
 `SqlType.Null`  
 <xref:System.Data.SqlTypes> Implementuje`INullable`wszystkie typy danych. Jeśli silnie wpisana wartość null może zostać przekonwertowana na typ danych kolumny przy użyciu niejawnych operatorów rzutowania, przypisanie powinno nastąpić przez. W przeciwnym razie zostanie zgłoszony nieprawidłowy wyjątek rzutowania.  
  
 `null`  
 Jeśli wartość "null" jest `DataColumn` wartością prawną dla danego typu danych, jest ona przekształcana w odpowiednią `DbNull.Value` lub `Null` skojarzona z `INullable` typem (`SqlType.Null`)  
  
 `derivedUdt.Null`  
 W przypadku kolumn UDT wartości null są zawsze przechowywane na podstawie typu skojarzonego z `DataColumn`. Rozważ przypadek, który jest skojarzony z elementem `DataColumn` , który nie implementuje `INullable` , gdy jego podklasa jest. W takim przypadku, jeśli zostanie przypisana silnie wpisana wartość null skojarzona z klasą pochodną, jest ona przechowywana jako bez `DbNull.Value`typu, ponieważ magazyn o wartości null jest zawsze spójny z typem danych DataColumn.  
  
> [!NOTE]
> Struktura `Nullable<T>` lub <xref:System.Nullable> niejest`DataSet`obecnie obsługiwana w.  
  
### <a name="multiple-column-row-assignment"></a>Przypisanie wielu kolumn (wierszy)  
 `DataTable.Add`, `DataTable.LoadDataRow`lub inne interfejsy API, które <xref:System.Data.DataRow.ItemArray%2A> akceptują, które są zamapowane na wiersz, mapują wartość "null" do wartości domyślnej DataColumn. Jeśli obiekt w tablicy zawiera `DbNull.Value` lub jego silnie wpisaną, te same reguły, jak opisano powyżej, są stosowane.  
  
 Ponadto dla wystąpienia przypisań o `DataRow.["columnName"]` wartości null są stosowane następujące reguły:  
  
1. Domyślna wartość *Domyślna* to `DbNull.Value` dla wszystkich, z wyjątkiem kolumn o jednoznacznie określonym typie, w których jest to odpowiednia silnie wpisana wartość null.  
  
2. Wartości null nigdy nie są zapisywane podczas serializacji do plików XML (podobnie jak w przypadku elementu "xsi: nil").  
  
3. Wszystkie wartości inne niż null, w tym wartości domyślne, są zawsze zapisywane podczas serializacji do formatu XML. Jest to w przeciwieństwie do semantyki XSD/XML, gdzie wartość null (xsi: nil) jest jawna i wartość domyślna jest niejawna (jeśli nie jest obecny w kodzie XML, Analizator sprawdzania poprawności może pobrać go ze skojarzonego schematu XSD). Przeciwieństwo jest prawdziwe dla `DataTable`: wartość null jest niejawna, a wartość domyślna to explicit.  
  
4. Wszystkie brakujące wartości kolumn dla wierszy odczytanych z danych wejściowych XML mają przypisane wartość NULL. Do wierszy utworzonych <xref:System.Data.DataTable.NewRow%2A> przy użyciu lub podobnych metod są przypisywane wartości domyślnej kolumny DataColumn.  
  
5. Metoda zwraca `true` dla obu`DbNull.Value` i .`INullable.Null` <xref:System.Data.DataRow.IsNull%2A>  
  
## <a name="assigning-null-values"></a>Przypisywanie wartości null  
 Wartość domyślna dla dowolnego <xref:System.Data.SqlTypes> wystąpienia ma wartość null.  
  
 Wartości null w <xref:System.Data.SqlTypes> są specyficzne dla typu i nie mogą być reprezentowane przez pojedynczą wartość, na `DbNull`przykład. Użyj właściwości `IsNull` , aby sprawdzić wartości null.  
  
 Wartości null można przypisywać do typu <xref:System.Data.DataColumn> , tak jak pokazano w poniższym przykładzie kodu. Można bezpośrednio przypisywać wartości null do `SqlTypes` zmiennych bez wyzwalania wyjątku.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy <xref:System.Data.DataTable> z dwoma kolumnami zdefiniowanymi jako <xref:System.Data.SqlTypes.SqlInt32> i. <xref:System.Data.SqlTypes.SqlString> Kod dodaje jeden wiersz znanych wartości, jeden wiersz wartości null, a następnie iteruje przez <xref:System.Data.DataTable>, przypisując wartości do zmiennych i wyświetlając dane wyjściowe w oknie konsoli.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 W tym przykładzie są wyświetlane następujące wyniki:  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Porównywanie wartości null z typami SqlTypes i CLR  
 Porównując wartości null, ważne jest, aby zrozumieć różnicę między sposobem `Equals` , w jaki Metoda szacuje wartości null w <xref:System.Data.SqlTypes> porównaniu ze sposobem, w jaki działa z typami CLR. <xref:System.Data.SqlTypes> Wszystkiemetodyużywająsemantykibazydanychdoocenywartościnull:Jeślijednalubobiewartościmająwartośćnull,`Equals` porównanie daje wartość null. Z drugiej strony, użycie metody CLR `Equals` na dwóch <xref:System.Data.SqlTypes> zwróci wartość true, jeśli oba mają wartość null. Odzwierciedla to różnicę między użyciem metody wystąpienia, takiej jak metoda CLR `String.Equals` , i przy użyciu `SqlString.Equals`metody static/Shared.  
  
 Poniższy przykład ilustruje różnicę w wynikach między `SqlString.Equals` metodą `String.Equals` i metodą, gdy każda z nich przekazuje parę wartości null, a następnie parę pustych ciągów.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 Kod generuje następujące dane wyjściowe:  
  
```  
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

- [Typy danych programu SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
