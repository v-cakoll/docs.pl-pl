---
title: Pisanie pierwszej kwerendy LINQ
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: addf35afa2a4c88faf73ebc3d60fbcf9c4db1518
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636708"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>Pisanie pierwszego zapytania LINQ (Visual Basic)
*Zapytanie* jest wyrażeniem, które pobiera dane ze źródła danych. Zapytania są wyrażane w dedykowanym języku zapytań. W miarę upływu czasu różne języki zostały opracowane dla różnych typów źródeł danych, na przykład SQL dla relacyjnych baz danych i XQuery dla XML. Dzięki temu deweloper aplikacji może poznać nowy język zapytań dla każdego typu źródła danych lub obsługiwanego formatu danych.  
  
 Program Query Integrated Language (LINQ) upraszcza sytuację, oferując spójny model do pracy z danymi w różnych rodzajach źródeł danych i formatach. W zapytaniu LINQ zawsze pracujesz z obiektami. Te same podstawowe wzorce kodowania służą do wykonywania zapytań i przekształcania danych w dokumentach XML, baz danych SQL, ADO.NET zbiorach i jednostkach, kolekcjach .NET Framework i innych źródłach lub formatach, dla których jest dostępny dostawca LINQ. W tym dokumencie opisano trzy etapy tworzenia i używania podstawowych zapytań LINQ.  
  
## <a name="three-stages-of-a-query-operation"></a>Trzy etapy operacji zapytania  
 Operacje zapytań LINQ składają się z trzech akcji:  
  
1. Uzyskaj źródło danych lub źródła.  
  
2. Utwórz zapytanie.  
  
3. Wykonaj zapytanie.  
  
 W LINQ, wykonywanie zapytania jest różne od tworzenia zapytania. Nie są pobierane żadne dane tylko przez utworzenie zapytania. Ten punkt jest omówiona bardziej szczegółowo w dalszej części tego tematu.  
  
 Poniższy przykład ilustruje trzy części operacji zapytania. W przykładzie zastosowano tablicę liczb całkowitych jako wygodne źródło danych do celów demonstracyjnych. Jednak te same koncepcje dotyczą również innych źródeł danych.  
  
> [!NOTE]
> Na [stronie kompilacja, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)upewnij się, że **opcja wnioskowanie** jest ustawiona na wartość **włączone**.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Dane wyjściowe:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Źródło danych  
 Ze względu na to, że źródło danych w poprzednim przykładzie jest tablicą, niejawnie obsługuje interfejs ogólny <xref:System.Collections.Generic.IEnumerable%601>. Jest to fakt, że umożliwia użycie tablicy jako źródła danych dla zapytania LINQ. Typy obsługujące <xref:System.Collections.Generic.IEnumerable%601> lub interfejs pochodny, takie jak generyczne <xref:System.Linq.IQueryable%601>, są nazywane *typami Queryable*.  
  
 Jako niejawnie queryable typ, tablica nie wymaga modyfikacji ani specjalnego traktowania, które ma stanowić źródło danych LINQ. Ta sama wartość dotyczy wszystkich typów kolekcji, które obsługują <xref:System.Collections.Generic.IEnumerable%601>, w tym <xref:System.Collections.Generic.List%601>ogólnych, <xref:System.Collections.Generic.Dictionary%602>i innych klas w bibliotece klas .NET Framework.  
  
 Jeśli dane źródłowe nie implementują jeszcze <xref:System.Collections.Generic.IEnumerable%601>, dostawca LINQ jest wymagany do zaimplementowania funkcji *standardowych operatorów zapytań* dla tego źródła danych. Na przykład [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsługuje Work ładowania dokumentu XML do typu <xref:System.Xml.Linq.XElement> queryable, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — Omówienie (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 Przy [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]należy najpierw utworzyć mapowanie relacyjne obiektu w czasie projektowania, ręcznie lub za pomocą [narzędzi LINQ to SQL w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) w programie Visual Studio. Zapytania są zapisywane względem obiektów, a w czasie wykonywania [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] obsługuje komunikację z bazą danych. W poniższym przykładzie `customers` reprezentuje określoną tabelę w bazie danych, a <xref:System.Data.Linq.Table%601> obsługuje generyczne <xref:System.Linq.IQueryable%601>.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Więcej informacji o sposobach tworzenia określonych typów źródeł danych znajduje się w dokumentacji dotyczącej różnych dostawców LINQ. (Aby uzyskać listę tych dostawców, zobacz [LINQ (zapytanie zintegrowane z językiem)](../../../../visual-basic/programming-guide/concepts/linq/index.md).) Podstawowa reguła jest prosta: Źródło danych LINQ to każdy obiekt, który obsługuje ogólny interfejs <xref:System.Collections.Generic.IEnumerable%601> lub interfejs, który dziedziczy z niego.  
  
> [!NOTE]
> Typy takie jak <xref:System.Collections.ArrayList> obsługujące nieogólny interfejs <xref:System.Collections.IEnumerable> mogą być również używane jako źródła danych LINQ. Aby zapoznać się z przykładem, który używa <xref:System.Collections.ArrayList>, zobacz [How to: Query a ArrayList with LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>Zapytanie  
 W zapytaniu należy określić, jakie informacje mają być pobierane ze źródła danych lub źródeł. Istnieje również możliwość określenia, w jaki sposób te informacje mają być sortowane, grupowane lub strukturalne przed zwróceniem. Aby włączyć Tworzenie zapytania, Visual Basic zawiera nową składnię zapytania w języku.  
  
 Gdy jest wykonywane, zapytanie w poniższym przykładzie zwraca wszystkie liczby parzyste z tablicy liczb całkowitych, `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Wyrażenie zapytania zawiera trzy klauzule: `From`, `Where`i `Select`. Określona funkcja i cel każdej klauzuli wyrażenia zapytania są omówione w [podstawowych operacjach zapytań (Visual Basic)](basic-query-operations.md). Aby uzyskać więcej informacji, zobacz [zapytania](../../../../visual-basic/language-reference/queries/index.md). Należy zauważyć, że w LINQ, definicja zapytania często jest przechowywana w zmiennej i wykonywany później. Zmienna zapytania, taka jak `evensQuery` w poprzednim przykładzie, musi być typem queryable. Typ `evensQuery` jest `IEnumerable(Of Integer)`, przypisany przez kompilator przy użyciu wnioskowania typu lokalnego.  
  
 Należy pamiętać, że zmienna zapytania nie przyjmuje żadnej akcji i nie zwraca żadnych danych. Przechowuje tylko definicję zapytania. W poprzednim przykładzie jest to `For Each` pętla, która wykonuje zapytanie.  
  
## <a name="query-execution"></a>Wykonywanie zapytania  
 Wykonanie zapytania jest niezależne od tworzenia zapytania. Tworzenie zapytania definiuje zapytanie, ale wykonywanie jest wyzwalane przez inny mechanizm. Zapytanie może być wykonywane zaraz po jego zdefiniowaniu (*natychmiastowe wykonanie*) lub definicji może być przechowywane, a zapytanie można wykonać później (*odroczone wykonanie*).  
  
### <a name="deferred-execution"></a>Wykonanie odroczone  
 Typowa kwerenda LINQ jest podobna do przedstawionej w poprzednim przykładzie, w którym zdefiniowano `evensQuery`. Tworzy zapytanie, ale nie wykonuje go od razu. Zamiast tego definicja zapytania jest przechowywana w zmiennej zapytania `evensQuery`. Zapytanie jest wykonywane później, zazwyczaj przy użyciu pętli `For Each`, która zwraca sekwencję wartości lub przez zastosowanie standardowego operatora zapytania, takiego jak `Count` lub `Max`. Ten proces jest nazywany *wykonaniem odroczonym*.  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 Dla sekwencji wartości uzyskuje się dostęp do pobranych danych przy użyciu zmiennej iteracji w pętli `For Each` (`number` w poprzednim przykładzie). Ponieważ zmienna zapytania, `evensQuery`, zawiera definicję zapytania zamiast wyników zapytania, można wykonać zapytanie tak często, jak chcesz, używając zmiennej zapytania więcej niż jeden raz. Na przykład może istnieć baza danych w aplikacji, która jest stale aktualizowana przez oddzielną aplikację. Po utworzeniu zapytania, które pobiera dane z tej bazy danych, można użyć pętli `For Each`, aby wielokrotnie wykonać zapytanie, pobierając najnowsze dane za każdym razem.  
  
 W poniższym przykładzie pokazano, jak działa odroczone wykonanie. Po zdefiniowaniu i wykonaniu `evensQuery2` z pętlą `For Each`, tak jak w poprzednich przykładach, niektóre elementy `numbers` źródła danych są zmieniane. Następnie `evensQuery2` zostanie ponownie uruchomiona Druga pętla `For Each`. Wyniki są różne w drugim czasie, ponieważ pętla `For Each` ponownie wykonuje zapytanie, używając nowych wartości w `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 Dane wyjściowe:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Natychmiastowe wykonanie  
 W odroczonym wykonywaniu zapytań definicja zapytania jest przechowywana w zmiennej zapytania na potrzeby późniejszego wykonania. W przypadku natychmiastowego wykonania zapytanie jest wykonywane w momencie jego definicji. Wykonywanie jest wyzwalane w przypadku zastosowania metody wymagającej dostępu do poszczególnych elementów wyniku zapytania. Natychmiastowe wykonanie często jest wymuszane przy użyciu jednego z standardowych operatorów zapytań, które zwracają pojedyncze wartości. Przykłady to `Count`, `Max`, `Average`i `First`. Te standardowe operatory zapytań wykonują zapytanie natychmiast po ich zastosowaniu, aby obliczyć i zwrócić pojedynczy wynik. Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, które zwracają pojedyncze wartości, zobacz [operacje agregacji](aggregation-operations.md), [operacje elementów](element-operations.md)i [Kwantyfikatory](quantifier-operations.md).  
  
 Następujące zapytanie zwraca liczbę liczb parzystych w tablicy liczb całkowitych. Definicja zapytania nie została zapisana, a `numEvens` jest prostą `Integer`.  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 Można osiągnąć ten sam wynik przy użyciu metody `Aggregate`.  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 Możesz również wymusić wykonanie zapytania, wywołując metodę `ToList` lub `ToArray` w zapytaniu (bezpośrednie) lub zmiennej zapytania (odroczono), jak pokazano w poniższym kodzie.  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 W poprzednich przykładach `evensQuery3` jest zmienną zapytania, ale `evensList` jest listą, a `evensArray` jest tablicą.  
  
 Użycie `ToList` lub `ToArray`, aby wymusić natychmiastowe wykonywanie, jest szczególnie przydatne w scenariuszach, w których chcesz natychmiast wykonać zapytanie i buforować wyniki w pojedynczym obiekcie kolekcji. Aby uzyskać więcej informacji na temat tych metod, zobacz [konwertowanie typów danych](converting-data-types.md).  
  
 Możesz również spowodować wykonanie zapytania przy użyciu metody `IEnumerable`, takiej jak Metoda <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie ze składnikami LINQ w Visual Basic](getting-started-with-linq.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](standard-query-operators-overview.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
