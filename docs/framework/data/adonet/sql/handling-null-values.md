---
title: Obsługa wartości Null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: c45c6672983866df6c47ec84981cc7bd11637c0c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249080"
---
# <a name="handling-null-values"></a>Obsługa wartości Null
Wartość null w relacyjnej bazie danych jest używana, gdy wartość w kolumnie jest nieznana lub brakuje. Wartość null nie jest pustym ciągiem (dla typów danych znaku lub datetime) ani wartością zerową (dla typów danych liczbowych). Specyfikacja ANSI SQL-92 stwierdza, że wartość null musi być taka sama dla wszystkich typów danych, tak aby wszystkie wartości null były obsługiwane spójnie. Obszar <xref:System.Data.SqlTypes> nazw udostępnia semantyki null <xref:System.Data.SqlTypes.INullable> implementując interfejs. Każdy z typów <xref:System.Data.SqlTypes> danych w `IsNull` ma `Null` własną właściwość i wartość, która może być przypisana do wystąpienia tego typu danych.  
  
> [!NOTE]
> W programie .NET Framework w wersji 2.0 wprowadzono obsługę typów wartości z możliwością wartości null, które umożliwiają programistom rozszerzenie typu wartości w celu reprezentowania wszystkich wartości typu bazowego. Te typy wartości clr nullable <xref:System.Nullable> reprezentują wystąpienie struktury. Ta funkcja jest szczególnie przydatna, gdy typy wartości są zapakowane i unboxed, zapewniając lepszą zgodność z typami obiektów. Clr nullable typy wartości nie są przeznaczone do przechowywania wartości null bazy danych, `null` ponieważ ansi SQL null nie zachowuje się tak samo jak odwołanie (lub `Nothing` w języku Visual Basic). Do pracy z wartościami null SQL <xref:System.Data.SqlTypes> bazy danych <xref:System.Nullable>ANSI należy użyć wartości null, a nie . Aby uzyskać więcej informacji na temat pracy z typami nullable clr w języku Visual Basic, zobacz [Typy wartości nullable](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md), a w przypadku języka C# zobacz [Typy wartości nullable](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Wartości null i logika trójwartościowa  
 Zezwalając na wartości null w definicjach kolumn wprowadza logikę trójwartościową do aplikacji. Porównanie można ocenić do jednego z trzech warunków:  
  
- True  
  
- False  
  
- Nieznane  
  
 Ponieważ null jest uważany za nieznany, dwie wartości null w porównaniu do siebie nie są uważane za równe. W wyrażeniach przy użyciu operatorów arytmetycznych, jeśli którykolwiek z argumentów ma wartość null, wynik jest również zerowy.  
  
## <a name="nulls-and-sqlboolean"></a>Wartości null i sqlboolean  
 Porównanie między <xref:System.Data.SqlTypes> dowolnym <xref:System.Data.SqlTypes.SqlBoolean>zwróci . Funkcja `IsNull` dla `SqlType` każdego <xref:System.Data.SqlTypes.SqlBoolean> zwraca i może służyć do sprawdzania wartości null. Poniższe tabele prawdy pokazują, jak operatory AND, OR i NOT działają w obecności wartości null. (T=true, F=false i U=unknown lub null.)  
  
 ![Tabela prawdy](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>Opis opcji ANSI_NULLS  
 <xref:System.Data.SqlTypes>zapewnia taką samą semantycę, jak wtedy, gdy opcja ANSI_NULLS jest ustawiona w programie SQL Server. Wszystkie operatory arytmetyczne (+, -, \*, /, %), operatory \|bitowe (~, &), a większość funkcji zwraca wartość null, jeśli którykolwiek z argumentów lub argumentów ma wartość null, z wyjątkiem właściwości `IsNull`.  
  
 Standard ANSI SQL-92 nie obsługuje *columnName* = NULL w klauzuli WHERE. W programie SQL Server opcja ANSI_NULLS kontroluje zarówno domyślną nieważność w bazie danych, jak i ocenę porównań z wartościami null. Jeśli ANSI_NULLS jest włączona (domyślnie), operator IS NULL musi być używany w wyrażeniach podczas testowania wartości null. Na przykład następujące porównanie zawsze daje nieznany, gdy ANSI_NULLS jest włączony:  
  
```sql
colname > NULL  
```  
  
 Porównanie ze zmienną zawierającą wartość null daje również nieznany:  
  
```sql
colname > @MyVariable  
```  
  
 Użyj predykatu IS NULL lub IS NOT NULL, aby przetestować wartość null. Może to zwiększyć złożoność klauzuli WHERE. Na przykład kolumna TerritoryID w tabeli Nabywca AdventureWorks zezwala na wartości null. Jeśli instrukcja SELECT ma testować wartości null oprócz innych, musi zawierać predykat IS NULL:  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 Jeśli ustawisz ANSI_NULLS wyłączony w programie SQL Server, można utworzyć wyrażenia, które używają operatora równości do porównania z wartością null. Nie można jednak zapobiec ustawianiu przez różne połączenia opcji null dla tego połączenia. Za pomocą is null do testowania wartości null zawsze działa, niezależnie od ustawień ANSI_NULLS dla połączenia.  
  
 Ustawienie ANSI_NULLS wyłączenia nie jest `DataSet`obsługiwane w programie , który zawsze jest zgodny ze standardem ANSI SQL-92 do obsługi wartości null w <xref:System.Data.SqlTypes>programie .  
  
## <a name="assigning-null-values"></a>Przypisywanie wartości null  
 Wartości null są specjalne, a ich semantyka przechowywania i przydziału różni się w różnych systemach typu i systemach magazynowania. A `Dataset` jest przeznaczony do stosowania z różnymi typami i systemami pamięci masowej.  
  
 W tej sekcji opisano semantykę null do <xref:System.Data.DataColumn> przypisywania wartości null do a w <xref:System.Data.DataRow> systemach różnych typów.  
  
 `DBNull.Value`  
 To przypisanie jest `DataColumn` prawidłowe dla dowolnego typu. Jeśli typ `INullable`implementuje `DBNull.Value` , jest wymuszany do odpowiedniej silnie wpisanej wartości Null.  
  
 `SqlType.Null`  
 Wszystkie <xref:System.Data.SqlTypes> typy `INullable`danych implementują . Jeśli silnie typią wartość null można przekonwertować na typ danych kolumny przy użyciu niejawnych operatorów rzutowania, przypisanie powinno przejść. W przeciwnym razie zostanie zgłoszony nieprawidłowy wyjątek rzutu.  
  
 `null`  
 Jeśli "null" jest wartością `DataColumn` prawną dla danego typu danych, `Null` jest on `INullable` a`SqlType.Null`przymuszony do odpowiedniego `DbNull.Value` lub skojarzonego z typem ( )  
  
 `derivedUdt.Null`  
 W przypadku kolumn UDT wartości null są zawsze przechowywane `DataColumn`na podstawie typu skojarzonego z programem . Należy wziąć pod uwagę przypadek UDT `DataColumn` skojarzone `INullable` z, który nie implementuje, podczas gdy jego podklasa nie. W takim przypadku, jeśli silnie typiona wartość null skojarzona z klasą pochodną `DbNull.Value`jest przypisana, jest przechowywana jako nietypowany , ponieważ magazyn null jest zawsze zgodny z typem danych DataColumn.  
  
> [!NOTE]
> Struktura `Nullable<T>` <xref:System.Nullable> lub struktura nie jest obecnie `DataSet`obsługiwana w pliku .  
  
### <a name="multiple-column-row-assignment"></a>Przypisanie wielu kolumn (wiersz)  
 `DataTable.Add`, `DataTable.LoadDataRow`lub inne interfejsy API, które akceptują, <xref:System.Data.DataRow.ItemArray%2A> który zostanie mapowany do wiersza, mapuje "null" na wartość domyślną DataColumn. Jeśli obiekt w tablicy zawiera `DbNull.Value` lub jego silnie typizowane odpowiednik, stosowane są te same reguły, jak opisano powyżej.  
  
 Ponadto następujące reguły mają zastosowanie `DataRow.["columnName"]` do wystąpienia przypisań null:  
  
1. Domyślna wartość `DbNull.Value` *domyślna* jest dla wszystkich z wyjątkiem silnie wpisane kolumny null, gdzie jest to odpowiedni silnie wpisane wartości null.  
  
2. Wartości null nigdy nie są zapisywane podczas serializacji do plików XML (jak w "xsi:nil").  
  
3. Wszystkie wartości inne niż null, w tym wartości domyślne, są zawsze zapisywane podczas serializacji do XML. Jest to w przeciwieństwie do semantyki XSD/XML, gdzie wartość null (xsi:nil) jest jawna, a wartość domyślna jest niejawna (jeśli nie jest obecna w języku XML, analizator sprawdzania poprawności może uzyskać ją ze skojarzonego schematu XSD). Odwrotnie jest w `DataTable`przypadku : wartość null jest niejawna, a wartość domyślna jest jawna.  
  
4. Wszystkie brakujące wartości kolumn dla wierszy odczytanych z danych wejściowych XML są przypisywane null. Wiersze utworzone <xref:System.Data.DataTable.NewRow%2A> przy użyciu lub podobne metody są przypisywane DataColumn wartość domyślną.  
  
5. Metoda <xref:System.Data.DataRow.IsNull%2A> zwraca `true` zarówno `DbNull.Value` `INullable.Null`i .  
  
## <a name="assigning-null-values"></a>Przypisywanie wartości null  
 Wartość domyślna <xref:System.Data.SqlTypes> dla dowolnego wystąpienia jest null.  
  
 Wartości null <xref:System.Data.SqlTypes> są specyficzne dla typu i nie mogą być `DbNull`reprezentowane przez pojedynczą wartość, taką jak . Użyj `IsNull` właściwości, aby sprawdzić wartości null.  
  
 Wartości null można przypisać <xref:System.Data.DataColumn> do, jak pokazano w poniższym przykładzie kodu. Wartości null można bezpośrednio `SqlTypes` przypisać do zmiennych bez wyzwalania wyjątku.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu <xref:System.Data.DataTable> tworzy z dwóch <xref:System.Data.SqlTypes.SqlInt32> <xref:System.Data.SqlTypes.SqlString>kolumn zdefiniowanych jako i . Kod dodaje jeden wiersz znanych wartości, jeden wiersz wartości null, <xref:System.Data.DataTable>a następnie iteruje za pośrednictwem , przypisując wartości do zmiennych i wyświetlając dane wyjściowe w oknie konsoli.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 W tym przykładzie są wyświetlane następujące wyniki:  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Porównywanie wartości null z typami SqlTypes i CLR  
 Podczas porównywania wartości null, ważne jest, aby `Equals` zrozumieć różnicę między <xref:System.Data.SqlTypes> sposób metoda ocenia wartości null w porównaniu ze sposobem, w jaki działa z typami CLR. <xref:System.Data.SqlTypes> `Equals` Wszystkie metody używają semantyki bazy danych do oceny wartości null: jeśli jedną lub obie wartości są null, porównanie daje wartość null. Z drugiej strony przy użyciu `Equals` CLR <xref:System.Data.SqlTypes> metody na dwa przyniesie true, jeśli oba są null. Odzwierciedla to różnicę między użyciem metody wystąpienia, `String.Equals` takiej jak clr, a `SqlString.Equals`wykorzystaniem metody statycznej/udostępnionej.  
  
 Poniższy przykład pokazuje różnicę w `SqlString.Equals` wynikach `String.Equals` między metodą i metodą, gdy każda jest przekazywana parę wartości null, a następnie parę pustych ciągów.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Typy danych programu SQL Server i ADO.NET](sql-server-data-types.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
