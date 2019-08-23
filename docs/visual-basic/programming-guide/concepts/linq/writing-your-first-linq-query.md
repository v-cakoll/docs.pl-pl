---
title: Pisanie pierwszego zapytania LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: 5c83d888f65ce5c216327e94c5d4d1267fb93c29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952002"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>Pisanie pierwszego zapytania LINQ (Visual Basic)
*Zapytanie* jest wyrażeniem, które pobiera dane ze źródła danych. Zapytania są wyrażane w dedykowanym języku zapytań. W miarę upływu czasu różne języki zostały opracowane dla różnych typów źródeł danych, na przykład SQL dla relacyjnych baz danych i XQuery dla XML. Dzięki temu deweloper aplikacji może poznać nowy język zapytań dla każdego typu źródła danych lub obsługiwanego formatu danych.  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]upraszcza sytuację, oferując spójny model do pracy z danymi w różnych rodzajach źródeł danych i formatach. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] W zapytaniu zawsze pracujesz z obiektami. Te same podstawowe wzorce kodowania służą do wykonywania zapytań i przekształcania danych w dokumentach XML, baz danych SQL, ADO.NET zbiorach i jednostkach, kolekcjach .NET Framework oraz innych źródłach lub [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] formatach, dla których jest dostępny dostawca. W tym dokumencie opisano trzy etapy tworzenia i używania zapytań podstawowych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] .  
  
## <a name="three-stages-of-a-query-operation"></a>Trzy etapy operacji zapytania  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]operacje zapytań składają się z trzech akcji:  
  
1. Uzyskaj źródło danych lub źródła.  
  
2. Utwórz zapytanie.  
  
3. Wykonaj zapytanie.  
  
 W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]programie wykonywanie zapytania jest różne od tworzenia zapytania. Nie są pobierane żadne dane tylko przez utworzenie zapytania. Ten punkt jest omówiona bardziej szczegółowo w dalszej części tego tematu.  
  
 Poniższy przykład ilustruje trzy części operacji zapytania. W przykładzie zastosowano tablicę liczb całkowitych jako wygodne źródło danych do celów demonstracyjnych. Jednak te same koncepcje dotyczą również innych źródeł danych.  
  
> [!NOTE]
> Na [stronie kompilacja, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)upewnij się, że **opcja wnioskowanie** jest ustawiona na wartość **włączone**.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Dane wyjściowe:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Źródło danych  
 Ze względu na to, że źródło danych w poprzednim przykładzie jest tablicą, niejawnie obsługuje interfejs ogólny <xref:System.Collections.Generic.IEnumerable%601> . Jest to fakt, że umożliwia użycie tablicy jako źródła danych dla [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Typy obsługujące <xref:System.Collections.Generic.IEnumerable%601> lub interfejs pochodny, takie jak generyczne <xref:System.Linq.IQueryable%601> , są nazywane *typami Queryable*.  
  
 Jako niejawnie queryable typ, tablica nie wymaga modyfikacji ani specjalnego traktowania, które ma stanowić [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródło danych. Ta sama wartość dotyczy dowolnego typu kolekcji, który obsługuje <xref:System.Collections.Generic.IEnumerable%601>, w tym generycznej <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.Generic.List%601>, i innych klas w bibliotece klas .NET Framework.  
  
 Jeśli dane źródłowe nie zostały jeszcze zaimplementowane <xref:System.Collections.Generic.IEnumerable%601> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] , dostawca jest wymagany do zaimplementowania funkcji *standardowych operatorów zapytań* dla tego źródła danych. Na przykład program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsługuje zadania ładowania dokumentu XML do typu queryable <xref:System.Xml.Linq.XElement> , jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — Omówienie (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 W programie należy najpierw utworzyć mapowanie relacyjne obiektu w czasie projektowania, ręcznie lub za pomocą [narzędzi LINQ to SQL w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) w programie Visual Studio. [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] Zapytania są zapisywane względem obiektów i w czasie [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] wykonywania obsługują komunikację z bazą danych. W poniższym przykładzie `customers` reprezentuje określoną tabelę w bazie danych i <xref:System.Data.Linq.Table%601> obsługuje ogólne <xref:System.Linq.IQueryable%601>.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Aby uzyskać więcej informacji o sposobach tworzenia określonych typów źródeł danych, zapoznaj się z dokumentacją dla [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] różnych dostawców. (Aby uzyskać listę tych dostawców, zobacz [LINQ (zapytanie zintegrowane z językiem)](../../../../visual-basic/programming-guide/concepts/linq/index.md).) Podstawowa reguła jest prosta: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródło danych to dowolny obiekt obsługujący interfejs ogólny <xref:System.Collections.Generic.IEnumerable%601> lub interfejs, który dziedziczy z niego.  
  
> [!NOTE]
> Typy takie jak <xref:System.Collections.ArrayList> obsługujące interfejs nieogólny <xref:System.Collections.IEnumerable> mogą również służyć jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródła danych. Aby zapoznać się z przykładem <xref:System.Collections.ArrayList>, który [używa programu, zobacz How to: Zbadaj ArrayList za pomocą LINQ (Visual Basic](how-to-query-an-arraylist-with-linq.md)).  
  
## <a name="the-query"></a>Zapytanie  
 W zapytaniu należy określić, jakie informacje mają być pobierane ze źródła danych lub źródeł. Istnieje również możliwość określenia, w jaki sposób te informacje mają być sortowane, grupowane lub strukturalne przed zwróceniem. Aby włączyć Tworzenie zapytania, Visual Basic zawiera nową składnię zapytania w języku.  
  
 Gdy jest wykonywane, zapytanie w poniższym przykładzie zwraca wszystkie liczby parzyste z tablicy `numbers`liczb całkowitych.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Wyrażenie zapytania zawiera trzy klauzule: `From`, `Where`, i `Select`. Określona funkcja i cel każdej klauzuli wyrażenia zapytania są omówione w [podstawowych operacjach zapytań (Visual Basic)](basic-query-operations.md). Aby uzyskać więcej informacji, zobacz [zapytania](../../../../visual-basic/language-reference/queries/index.md). Należy pamiętać, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]że w programie definicja zapytania często jest przechowywana w zmiennej i wykonywany później. Zmienna zapytania, taka jak `evensQuery` w poprzednim przykładzie, musi być typu queryable. Typ `evensQuery` jest`IEnumerable(Of Integer)`przypisany przez kompilator przy użyciu wnioskowania typu lokalnego.  
  
 Należy pamiętać, że zmienna zapytania nie przyjmuje żadnej akcji i nie zwraca żadnych danych. Przechowuje tylko definicję zapytania. W poprzednim przykładzie jest `For Each` to pętla, która wykonuje zapytanie.  
  
## <a name="query-execution"></a>Wykonywanie zapytania  
 Wykonanie zapytania jest niezależne od tworzenia zapytania. Tworzenie zapytania definiuje zapytanie, ale wykonywanie jest wyzwalane przez inny mechanizm. Zapytanie może być wykonywane zaraz po jego zdefiniowaniu (*natychmiastowe wykonanie*) lub definicji może być przechowywane, a zapytanie można wykonać później (*odroczone wykonanie*).  
  
### <a name="deferred-execution"></a>Wykonanie odroczone  
 Typowa [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kwerenda jest podobna do przedstawionej w poprzednim przykładzie, w którym `evensQuery` jest zdefiniowana. Tworzy zapytanie, ale nie wykonuje go od razu. Zamiast tego definicja zapytania jest przechowywana w zmiennej `evensQuery`zapytania. Zapytanie jest wykonywane później, zazwyczaj przy użyciu `For Each` pętli, która zwraca sekwencję wartości lub przez zastosowanie standardowego operatora zapytania, takiego jak `Count` lub `Max`. Ten proces jest nazywany wykonaniem *odroczonym*.  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 Dla sekwencji wartości uzyskuje się dostęp do pobranych danych przy użyciu zmiennej iteracji w `For Each` pętli (`number` w poprzednim przykładzie). Ponieważ zmienna zapytania, `evensQuery`zawiera definicję zapytania, a nie wyniki zapytania, można wykonać zapytanie tak często, jak chcesz, używając zmiennej zapytania więcej niż jeden raz. Na przykład może istnieć baza danych w aplikacji, która jest stale aktualizowana przez oddzielną aplikację. Po utworzeniu zapytania, które pobiera dane z tej bazy danych, można użyć `For Each` pętli, aby wielokrotnie wykonać zapytanie, pobierając najnowsze dane za każdym razem.  
  
 W poniższym przykładzie pokazano, jak działa odroczone wykonanie. Po `evensQuery2` zdefiniowaniu i wykonaniu `For Each` z pętlą, tak jak w poprzednich przykładach, niektóre elementy w źródle `numbers` danych są zmieniane. Następnie zostanie ponownie `For Each` uruchomiona `evensQuery2` Druga pętla. Wyniki są różne w drugim czasie, ponieważ `For Each` pętla wykonuje zapytanie ponownie, używając nowych wartości w. `numbers`  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 Dane wyjściowe:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Natychmiastowe wykonanie  
 W odroczonym wykonywaniu zapytań definicja zapytania jest przechowywana w zmiennej zapytania na potrzeby późniejszego wykonania. W przypadku natychmiastowego wykonania zapytanie jest wykonywane w momencie jego definicji. Wykonywanie jest wyzwalane w przypadku zastosowania metody wymagającej dostępu do poszczególnych elementów wyniku zapytania. Natychmiastowe wykonanie często jest wymuszane przy użyciu jednego z standardowych operatorów zapytań, które zwracają pojedyncze wartości. Przykłady to `Count`, `Max`, `Average`, i `First`. Te standardowe operatory zapytań wykonują zapytanie natychmiast po ich zastosowaniu, aby obliczyć i zwrócić pojedynczy wynik. Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, które zwracają pojedyncze wartości, zobacz [operacje agregacji](aggregation-operations.md), [operacje elementów](element-operations.md)i [Kwantyfikatory](quantifier-operations.md).  
  
 Następujące zapytanie zwraca liczbę liczb parzystych w tablicy liczb całkowitych. Definicja zapytania nie została zapisana i `numEvens` jest prosta. `Integer`  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 Można osiągnąć ten sam wynik przy użyciu `Aggregate` metody.  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 Możesz również wymusić wykonanie zapytania przez wywołanie `ToList` metody lub `ToArray` dla zapytania (bezpośrednie) lub zmiennej zapytania (odroczono), jak pokazano w poniższym kodzie.  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 W poprzednich przykładach `evensQuery3` jest zmienną zapytania, ale `evensList` jest listą i `evensArray` jest tablicą.  
  
 Użycie `ToList` lub`ToArray` , aby wymusić natychmiastowe wykonanie, jest szczególnie przydatne w scenariuszach, w których chcesz natychmiast wykonać zapytanie i buforować wyniki w pojedynczym obiekcie kolekcji. Aby uzyskać więcej informacji na temat tych metod, zobacz [konwertowanie typów danych](converting-data-types.md).  
  
 Możesz również spowodować wykonanie zapytania przy użyciu `IEnumerable` metody, takiej <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> jak metoda.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie ze składnikami LINQ w Visual Basic](getting-started-with-linq.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Standardowe operatory zapytań — Omówienie (Visual Basic)](standard-query-operators-overview.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
