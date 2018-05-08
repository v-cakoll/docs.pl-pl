---
title: Obsługa wartości Null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 9c0b6d250dcedc9b5996c50ccdb2f183707e54e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="handling-null-values"></a>Obsługa wartości Null
Wartość null w relacyjnej bazie danych jest używany, gdy wartość w kolumnie jest nieznany lub nieobecny. Wartość null nie jest ciągiem pustym (dla typów danych daty/godziny lub znakiem) ani wartość zero (dla liczbowych typów danych). Ze specyfikacją ANSI SQL-92 się informacja o wartości null musi być taka sama dla wszystkich typów danych tak, aby spójną wszystkie wartości null. <xref:System.Data.SqlTypes> Przestrzeń nazw zawiera wartości null semantyki zaimplementowanie <xref:System.Data.SqlTypes.INullable> interfejsu. Typy wszystkich danych w <xref:System.Data.SqlTypes> ma własną `IsNull` właściwości i `Null` wartość przypisana do wystąpienia tego typu danych.  
  
> [!NOTE]
>  .NET Framework w wersji 2.0 wprowadzono obsługę typy dopuszczające wartości null, które umożliwiają deweloperom rozszerzenie typu wartości reprezentujący wszystkie wartości typu bazowego. Te typy dopuszczające wartości zerowe CLR reprezentuje wystąpienie <xref:System.Nullable> struktury. Ta funkcja jest szczególnie przydatne, gdy wartość typów opakowany i rozpakowany zapewniające rozszerzoną zgodność z typów obiektów. Typy dopuszczające wartości zerowe CLR nie są przeznaczone do magazynu bazy danych zawiera wartości null, ponieważ null ANSI SQL nie działają tak samo jak `null` odwołania (lub `Nothing` w języku Visual Basic). Praca z wartościami null ANSI SQL bazy danych, użyj <xref:System.Data.SqlTypes> wartości null zamiast <xref:System.Nullable>. Aby uzyskać więcej informacji na temat pracy z CLR Zobacz typy dopuszczające wartości zerowe w języku Visual Basic [typy dopuszczające wartości zerowe wartości](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)i C# zobacz [przy użyciu typów dopuszczających wartości zerowe](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Wartości null i przechowywanymi na trzy logiczne  
 Stosowanie wartości null w definicjach kolumn wprowadza przechowywanymi w trzech logiki do aplikacji. Porównanie można ocenić do jednego z trzech warunków:  
  
-   True  
  
-   False  
  
-   Nieznany  
  
 Ponieważ wartość null jest traktowana jako Nieznany, dwie wartości null w porównaniu do siebie nie są traktowane jako równe. W wyrażeniach przy użyciu operatorów arytmetycznych, jeśli dowolny z argumentów jest wartość null, wynik ma wartość null w również.  
  
## <a name="nulls-and-sqlboolean"></a>Wartości null i SqlBoolean  
 Porównanie między żadnego <xref:System.Data.SqlTypes> zwróci <xref:System.Data.SqlTypes.SqlBoolean>. `IsNull` Funkcja dla każdego `SqlType` zwraca <xref:System.Data.SqlTypes.SqlBoolean> i może służyć do sprawdzenia wartości null. Prawdy następujące tabele Pokaż jak AND, OR i nie operatory funkcji obecności wartości null. (T = true, F = false, U = nieznany lub wartość null.)  
  
 ![Tabela prawdy](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansinulls-option"></a>Opis opcji ANSI_NULLS  
 <xref:System.Data.SqlTypes> udostępnia tej samej semantyki jako, gdy opcja ANSI_NULLS jest ustawiona na w programie SQL Server. Wszystkie operatory arytmetyczne (+, -, *, /, %), operatory bitowe (~ &, &#124;), a większość funkcji zwracać wartość null, jeśli dowolny z argumentów lub argumentów jest pusta, z wyjątkiem właściwości `IsNull`.  
  
 Nie obsługuje standardu ANSI SQL-92 *columnName* = NULL w klauzuli WHERE. W programie SQL Server opcji ANSI_NULLS steruje dopuszczania wartości null zarówno domyślnej bazy danych i oceny porównania z wartości null. Jeśli ANSI_NULLS jest włączona (ustawienie domyślne), operatora IS NULL należy używać w wyrażeniach podczas testowania wartości null. Na przykład poniższe porównanie zawsze daje nieznany, gdy ANSI_NULLS znajduje się na:  
  
```  
colname > NULL  
```  
  
 Porównanie ze zmienną również zawierających wartości null daje nieznany:  
  
```  
colname > @MyVariable  
```  
  
 Próba na wartość null, należy użyć predykatu IS NULL i IS NOT NULL. To zwiększenia złożoności klauzuli WHERE. Na przykład TerritoryID kolumny w tabeli Nabywca AdventureWorks dozwolone wartości null. W przypadku instrukcji SELECT do sprawdzenia wartości null, oprócz innych osób, musi on zawierać predykat IS NULL:  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 Jeśli ustawisz ANSI_NULLS off w programie SQL Server, można utworzyć wyrażenia używające operatora równości do porównania wartości null. Nie można jednak zapobiec różnych połączeń z ustawień wartości null dla tego połączenia. Aby przetestować wartości null zawsze działa niezależnie od ustawienia ANSI_NULLS połączenia za pomocą IS NULL.  
  
 Ustawienie ANSI_NULLS wyłączanie nie jest obsługiwany w `DataSet`, który jest zawsze zgodny standardu ANSI SQL-92 dla Obsługa wartości zerowych w <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Przypisanie wartości Null  
 Wartości null są specjalne, a ich semantyki magazynu i przypisywania różnią się i systemami magazynu innego typu. A `Dataset` jest przeznaczony do użycia z innego typu i systemów pamięci masowej.  
  
 W tej sekcji opisano null semantyki przypisywania wartości null do <xref:System.Data.DataColumn> w <xref:System.Data.DataRow> we wszystkich systemach innego typu.  
  
 `DBNull.Value`  
 To przypisanie jest nieprawidłowa dla `DataColumn` dowolnego typu. Jeśli typ implementuje `INullable`, `DBNull.Value` jest przekształcić na odpowiednie silnie typizowaną wartość Null.  
  
 `SqlType.Null`  
 Wszystkie <xref:System.Data.SqlTypes> typy danych implementuje `INullable`. Przypisanie silnie typizowaną wartość null, mogą być konwertowane na typ danych kolumny przy użyciu operatorów niejawne rzutowanie, należy przejść przez. W przeciwnym razie Nieprawidłowe rzutowanie jest zwracany wyjątek.  
  
 `null`  
 Jeśli wartość "null" jest dozwoloną wartością dla danego `DataColumn` typ danych, jest on przekształcić na odpowiedni `DbNull.Value` lub `Null` skojarzone z `INullable` typu (`SqlType.Null`)  
  
 `derivedUdt.Null`  
 Dla kolumny UDT wartości null są zawsze zapisywane na podstawie typu skojarzonego z `DataColumn`. Rozważmy przypadek UDT skojarzone z `DataColumn` nie zawiera implementacji `INullable` podczas jego klasa podrzędnych. W tym przypadku jeśli przypisany jest skojarzony z klasy pochodnej silnie typizowaną wartość null, jest przechowywany jako bez typu `DbNull.Value`, ponieważ Magazyn wartość null jest zawsze zgodny z typem danych DataColumn.  
  
> [!NOTE]
>  `Nullable<T>` Lub <xref:System.Nullable> struktury nie jest obecnie obsługiwany w `DataSet`.  
  
### <a name="multiple-column-row-assignment"></a>Wiele przypisania kolumnie (wiersz)  
 `DataTable.Add`, `DataTable.LoadDataRow`, lub innych interfejsów API, które akceptują <xref:System.Data.DataRow.ItemArray%2A> który pobiera zamapowana na wiersz, Mapa "null", wartość domyślna elementu DataColumn. Jeśli obiekt w tablicy zawiera `DbNull.Value` lub jego odpowiednik jednoznacznie regułom opisanych powyżej są stosowane.  
  
 Ponadto, obowiązują następujące reguły dla wystąpienia `DataRow.["columnName"]` null przypisania:  
  
1.  Wartość domyślna *domyślne* wartość jest `DbNull.Value` wszystkie z wyjątkiem jednoznacznie kolumny wartości null, gdzie jest silnie typizowanej wartości null.  
  
2.  Wartości null nie są zapisywane podczas serializacji, aby pliki XML (jak "xsi: nil").  
  
3.  Wszystkich wartości innych niż null, w tym ustawienia domyślne, są zawsze zapisywane podczas serializowania do pliku XML. To w odróżnieniu od semantyki XSD/XML, gdzie wartość null (xsi: nil) jest jawne, a wartość domyślna to niejawne (Jeśli nie znajduje się w pliku XML, parserze można pobrać go ze schematu XSD skojarzone). Dotyczy to także przeciwieństwem `DataTable`: wartość null jest niejawnie i wartością domyślną jest jawne.  
  
4.  Wszystkie brakujące wartości kolumny dla wierszy odczytywać dane wejściowe XML są przypisane wartości NULL. Wiersze utworzone za pomocą <xref:System.Data.DataTable.NewRow%2A> lub podobnych metod są przypisane DataColumn wartości domyślnej.  
  
5.  <xref:System.Data.DataRow.IsNull%2A> Metoda zwraca `true` dla obu `DbNull.Value` i `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Przypisanie wartości Null  
 Wartością domyślną dla każdego <xref:System.Data.SqlTypes> wystąpienie ma wartość null.  
  
 Wartość null w <xref:System.Data.SqlTypes> są specyficzne dla danego typu i nie może być reprezentowany przez pojedynczą wartość, takich jak `DbNull`. Użyj `IsNull` właściwość do sprawdzenia wartości null.  
  
 Można przypisać wartości null do <xref:System.Data.DataColumn> jak pokazano w poniższym przykładzie kodu. Można bezpośrednio przypisać wartości null do `SqlTypes` zmienne bez wyzwalania Wystąpił wyjątek.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy <xref:System.Data.DataTable> z dwiema kolumnami zdefiniowany jako <xref:System.Data.SqlTypes.SqlInt32> i <xref:System.Data.SqlTypes.SqlString>. Ten kod dodaje jeden wiersz znane wartości, jeden wiersz null wartości, a następnie wykonuje iterację <xref:System.Data.DataTable>, przypisywanie wartości do zmiennych i wyświetlanie danych wyjściowych w oknie konsoli.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 W tym przykładzie wyświetlono następujące wyniki:  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Porównanie wartości Null z właściwości SqlTypes i typów CLR  
 Porównując wartości null, ważne jest, aby zrozumieć różnicę między sposób `Equals` metody oblicza wartości null w <xref:System.Data.SqlTypes> porównaniu sposób działa z typami CLR. Wszystkie <xref:System.Data.SqlTypes> `Equals` metody korzystają bezpośrednio z semantyki bazy danych do obliczenia wartości null: w przypadku jednego lub obu wartości null, porównanie daje wartość null. Z drugiej strony, przy użyciu środowiska CLR `Equals` metody na dwóch <xref:System.Data.SqlTypes> umożliwia uzyskanie wartość true, jeśli oba mają wartość null. Ta właściwość odzwierciedla różnicę między za pomocą metody wystąpienia takich jak środowisko CLR `String.Equals` — metoda i przy użyciu metody statycznej/udostępnione `SqlString.Equals`.  
  
 W poniższym przykładzie pokazano różnica w wynikach między `SqlString.Equals` — metoda i `String.Equals` metody w przypadku każdego przekazania pary wartości null, a następnie dwa puste ciągi.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 Kod tworzy następujące dane wyjściowe:  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych programu SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
