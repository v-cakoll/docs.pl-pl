---
title: Obsługa wartości Null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 0d200ad35d3ab56bf97114b51b4f7fcc898eecdf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032478"
---
# <a name="handling-null-values"></a>Obsługa wartości Null
Wartość null w relacyjnej bazie danych jest używany, gdy wartość w kolumnie jest nieznany lub Brak. Wartość null nie jest ciągiem pustym (dla typów danych znaku lub daty/godziny) ani wartość zero (w przypadku liczbowych typów danych). Specyfikacji ANSI SQL-92 z informacją o wartości null musi być taka sama dla wszystkich typów danych, tak, aby spójną wszystkie wartości null. <xref:System.Data.SqlTypes> Przestrzeń nazw zawiera semantyka wartości null, implementując <xref:System.Data.SqlTypes.INullable> interfejsu. Typy wszystkich danych w <xref:System.Data.SqlTypes> ma swój własny `IsNull` właściwości i `Null` wartość, którą można przypisać do wystąpienia tego typu danych.  
  
> [!NOTE]
>  .NET Framework w wersji 2.0 wprowadzono obsługę typy dopuszczające wartości null, które umożliwiają deweloperom rozszerzenie typu wartości do reprezentowania wszystkich wartości typu podstawowego. Te typy dopuszczające wartości null CLR reprezentują wystąpienia <xref:System.Nullable> struktury. Ta funkcja jest szczególnie przydatne, gdy wartość typów opakowany i rozpakowywany, udostępniając rozszerzoną zgodność z typów obiektów. Typy dopuszczające wartości zerowe CLR nie są przeznaczone dla magazynu bazy danych na wartości null, ponieważ null ANSI SQL zachowuje się tak samo, jak `null` odwołania (lub `Nothing` w języku Visual Basic). W przypadku pracy z wartościami null ANSI SQL bazy danych, użyj <xref:System.Data.SqlTypes> wartości null zamiast <xref:System.Nullable>. Aby uzyskać więcej informacji na temat pracy z CLR Zobacz typy dopuszczające wartości null w języku Visual Basic [typów wartości dopuszczających wartości zerowe](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)i uzyskać C#, zobacz [przy użyciu typów dopuszczających wartości zerowe](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Wartości null i zwracającej trzech logiki  
 Dopuszczających wartości null w definicjach kolumny wprowadza przechowywanymi w trzech logikę w aplikacji. Porównanie może służyć do oceny na jeden z trzech warunków:  
  
- Prawda  
  
- False  
  
- Nieznany  
  
 Ponieważ wartość null jest traktowana jako Nieznany, nie są uwzględniane równy dwie wartości null w porównaniu do siebie nawzajem. W wyrażeniach przy użyciu operatorów arytmetycznych, jeśli dowolny z argumentów ma wartość null, wynik ma wartość null w także.  
  
## <a name="nulls-and-sqlboolean"></a>Wartości null i SqlBoolean  
 Porównanie między dowolnymi <xref:System.Data.SqlTypes> zwróci <xref:System.Data.SqlTypes.SqlBoolean>. `IsNull` Funkcji dla każdego `SqlType` zwraca <xref:System.Data.SqlTypes.SqlBoolean> i może służyć do sprawdzania wartości null. Uspójniaj następujące tabele show jak AND, OR i nie operatory funkcji obecności wartość null. (T = true, F = false i U = nieznany lub ma wartość null.)  
  
 ![Tabela prawdy](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansinulls-option"></a>Opis opcji ANSI_NULLS  
 <xref:System.Data.SqlTypes> tą samą semantyką jako miejsce, gdy ustawiono opcję Ustawienia w programie SQL Server. Wszystkie operatory arytmetyczne (+, -, *, /, %), operatory bitowe (~ &, &#124;), a większość funkcji zwracać wartość null, jeśli którykolwiek z argumentów lub argumentów jest wartość null, z wyjątkiem właściwości `IsNull`.  
  
 Nie obsługuje standardu ANSI SQL-92 *columnName* = NULL w klauzuli WHERE. W programie SQL Server opcji ANSI_NULLS steruje dopuszczania wartości null zarówno domyślnej bazy danych i oceny porównania wartości null. Jeśli ANSI_NULLS jest włączona (ustawienie domyślne), operatora IS NULL należy używać w wyrażeniach podczas testowania w przypadku wartości null. Na przykład poniższe porównanie zawsze daje nieznany, gdy ustawienia znajduje się na:  
  
```  
colname > NULL  
```  
  
 Porównanie ze zmienną, która zawiera wartość null, również daje nieznany:  
  
```  
colname > @MyVariable  
```  
  
 Aby sprawdzić wartość null, należy użyć predykatu IS NULL i IS NOT NULL. To zwiększenia złożoności klauzuli WHERE. Na przykład w kolumnie tabeli klientów AdventureWorks TerritoryID dopuszcza wartości null. W przypadku instrukcji SELECT do testowania wartości null, oprócz innych użytkowników, musi on zawierać predykat IS NULL:  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 Jeśli ustawisz ANSI_NULLS w programie SQL Server, można utworzyć wyrażeniach, które używają operatora równości do porównania wartości null. Nie można jednak zapobiec różnych połączeń z ustawień o wartości null dla tego połączenia. Za pomocą IS NULL do testowania wartości null zawsze działa niezależnie od ustawień ANSI_NULLS dla połączenia.  
  
 Ustawienie ANSI_NULLS wyłączanie nie jest obsługiwana w `DataSet`, która zawsze odnosi się do standardu ANSI SQL-92 obsługę wartości null w <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Przypisywanie wartości Null  
 Wartości null są specjalne, a ich przechowywania i przypisania semantyki różnią się w różnych typów systemów i systemów magazynowych. Element `Dataset` jest przeznaczona do użycia z innego typu i systemów pamięci masowej.  
  
 W tej sekcji opisano semantyka wartości null do przypisywania wartości null do <xref:System.Data.DataColumn> w <xref:System.Data.DataRow> we wszystkich systemach innego typu.  
  
 `DBNull.Value`  
 To przypisanie jest prawidłowa dla `DataColumn` dowolnego typu. Jeśli typ implementuje `INullable`, `DBNull.Value` to przekształcone na odpowiednie silnie typizowaną wartość Null.  
  
 `SqlType.Null`  
 Wszystkie <xref:System.Data.SqlTypes> typy danych implementują `INullable`. Przypisanie silnie typizowaną wartość null, mogą być konwertowane na typ danych kolumny przy użyciu operatorów rzutowania niejawnego, należy przejść przez. W przeciwnym razie jest zgłaszany wyjątek Nieprawidłowe rzutowanie.  
  
 `null`  
 Jeśli wartość "null" jest dozwoloną wartością dla danego `DataColumn` typ danych, jest ona przekształcone na odpowiednie `DbNull.Value` lub `Null` skojarzone z `INullable` typu (`SqlType.Null`)  
  
 `derivedUdt.Null`  
 W kolumnach UDT wartości null są zawsze zapisywane na podstawie typu skojarzone z `DataColumn`. Rozważmy przypadek UDT skojarzone z `DataColumn` nie implementują `INullable` podczas jego klasa podrzędnych. W tym przypadku jeśli silnie typizowaną wartość null, skojarzone z klasy pochodnej jest przypisane, jest przechowywany jako nietypizowane `DbNull.Value`, ponieważ jest zawsze zgodny z typem danych DataColumn magazynu o wartości null.  
  
> [!NOTE]
>  `Nullable<T>` Lub <xref:System.Nullable> struktura nie jest obsługiwana w `DataSet`.  
  
### <a name="multiple-column-row-assignment"></a>Kilka przypisanie kolumny (wiersz)  
 `DataTable.Add`, `DataTable.LoadDataRow`, lub innych interfejsów API, które akceptują <xref:System.Data.DataRow.ItemArray%2A> , pobiera zamapowana na wiersz, mapy "null" DataColumn wartość domyślną. Jeśli obiekt w tablicy zawiera `DbNull.Value` lub jego odpowiednik silnie typizowaną te same zasady zgodnie z opisem powyżej są stosowane.  
  
 Ponadto obowiązują następujące reguły dla wystąpienia `DataRow.["columnName"]` null przypisania:  
  
1. Wartość domyślna *domyślne* wartość `DbNull.Value` wszystkie z wyjątkiem silnie typizowanych kolumn o wartości null gdzie jest odpowiedni silnie typizowane wartości null.  
  
2. Wartości null są nigdy zapisywane podczas serializacji, aby pliki XML (jak "xsi: nil").  
  
3. Wszystkich wartości innych niż null, w tym wartości domyślne, są zawsze zapisywane podczas serializacji XML. To różni się od semantyki XSD/XML, gdzie wartość null (xsi: nil) jest jawne, a wartość domyślna to niejawne (Jeśli nie jest obecny w pliku XML, sprawdzanie poprawności analizator pobrać go ze skojarzonego schematu XSD). Dotyczy to przeciwieństwo `DataTable`: wartość null jest niejawny, i wartość domyślna to jawne.  
  
4. Wszystkie brakujące wartości kolumn dla wierszy odczytywać dane wejściowe XML są przypisane wartości NULL. Wiersze utworzone za pomocą <xref:System.Data.DataTable.NewRow%2A> lub podobne metody są przypisywane DataColumn wartości domyślnej.  
  
5. <xref:System.Data.DataRow.IsNull%2A> Metoda zwraca `true` dla obu `DbNull.Value` i `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Przypisywanie wartości Null  
 Wartością domyślną dla każdego <xref:System.Data.SqlTypes> wystąpienie ma wartość null.  
  
 Null w <xref:System.Data.SqlTypes> są specyficzne dla danego typu i nie może być przedstawiona przez pojedynczej wartości, takich jak `DbNull`. Użyj `IsNull` właściwości pod kątem wartości null.  
  
 Można przypisać wartości null do <xref:System.Data.DataColumn> jak pokazano w poniższym przykładzie kodu. Można bezpośrednio przypisać wartości null do `SqlTypes` zmienne bez powodowania wyjątek.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy <xref:System.Data.DataTable> zawierającą dwie kolumny zdefiniowane jako <xref:System.Data.SqlTypes.SqlInt32> i <xref:System.Data.SqlTypes.SqlString>. Ten kod dodaje jeden wiersz znane wartości, wartości jeden wiersz o wartości null, a następnie wykonuje iterację <xref:System.Data.DataTable>przypisywania wartości do zmiennych oraz wyświetlanie danych wyjściowych w oknie konsoli.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 W tym przykładzie są wyświetlane następujące wyniki:  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Porównanie wartości Null za pomocą SqlTypes i typów CLR  
 Podczas porównywania wartości null, ważne jest, aby zrozumieć różnicę między sposób `Equals` metoda oblicza wartości null w <xref:System.Data.SqlTypes> porównaniu sposób działa z typami CLR. Wszystkie <xref:System.Data.SqlTypes> `Equals` metody korzystają bezpośrednio z semantyki bazy danych do oceny wartości null: Jeśli jeden lub oba wartości ma wartość null, porównanie daje wartość null. Z drugiej strony, przy użyciu środowiska CLR `Equals` metody na dwóch <xref:System.Data.SqlTypes> da wartość true, jeśli oba mają wartość null. Ten sposób odzwierciedlono różnica między metodą wystąpienia, takie jak środowisko CLR `String.Equals` metody i przy użyciu metody statyczne/udostępnione `SqlString.Equals`.  
  
 Poniższy przykład ilustruje różnicę w wynikach między `SqlString.Equals` metody i `String.Equals` metody, gdy każda jest przekazywany pary wartości null, a następnie para pustych ciągów.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 Kod generuje następujące wyniki:  
  
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
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
