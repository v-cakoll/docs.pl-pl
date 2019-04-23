---
title: Pisanie pierwszego zapytania LINQ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: 6f6968713fdb1c0ec0ee9f9da3b199a649938de5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295877"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>Pisanie pierwszego zapytania LINQ (Visual Basic)
A *zapytania* jest wyrażeniem, które pobiera dane ze źródła danych. Zapytania są wyrażone w język kwerendy dedykowanych. Wraz z upływem czasu różnych języków zostały opracowane dla różnych typów źródeł danych, na przykład SQL dla relacyjnych baz danych i XQuery dla XML. Dzięki temu niezbędne dla deweloperów aplikacji dowiedzieć się nowego języka zapytań dla każdego typu źródła danych lub formatu danych, która jest obsługiwana.  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] upraszcza tę sytuację oferując spójny model do pracy z danymi w różnych rodzajach formatów i źródeł danych. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, zawsze pracujesz z obiektami. Używasz tych samych podstawowych schematów kodowania do wykonywania zapytań i przekształcania danych w dokumentach XML, baz danych SQL, zestawami danych ADO.NET i jednostek, kolekcjami .NET Framework i inne źródła lub format, dla którego [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawca jest niedostępny. W tym dokumencie opisano trzy etapy tworzenia i używania basic [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania.  
  
## <a name="three-stages-of-a-query-operation"></a>Trzy etapy operacji zapytania  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operacje zapytań obejmują trzy czynności:  
  
1. Uzyskaj lub źródeł danych.  
  
2. Utwórz zapytanie.  
  
3. Wykonaj zapytanie.  
  
 W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], wykonywanie kwerendy różni się od tworzenia kwerendy. Nie pobrać żadnych danych, po prostu tworząc zapytanie. Ten punkt jest omówiona bardziej szczegółowo w dalszej części tego tematu.  
  
 Poniższy przykład ilustruje te trzy części operacji zapytania. W przykładzie użyto tablicy liczb całkowitych jako źródła danych w dogodnym dla celów demonstracyjnych. Jednak te same pojęcia mają zastosowanie również do innych źródeł danych.  
  
> [!NOTE]
>  Na [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), upewnij się, że **Option infer** ustawiono **na**.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Dane wyjściowe:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Źródło danych  
 Ponieważ źródło danych w poprzednim przykładzie jest tablicą, niejawnie obsługuje ogólny <xref:System.Collections.Generic.IEnumerable%601> interfejsu. Jest to fakt, że pozwala na użycie tablicy jako źródło danych dla [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Typy obsługujące <xref:System.Collections.Generic.IEnumerable%601> lub interfejs pochodny, takie jak typowa <xref:System.Linq.IQueryable%601> są nazywane *typami odpytywalnymi*.  
  
 Jako typ odpytywalny niejawnie tablicy nie wymaga modyfikacji ani specjalnego traktowania, aby pełnić rolę [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródła danych. To samo dotyczy dowolnego typu kolekcji, która obsługuje <xref:System.Collections.Generic.IEnumerable%601>, łącznie z ogólnego <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>i innych klas w bibliotece klas programu .NET Framework.  
  
 Jeśli źródło danych nie obsługuje już <xref:System.Collections.Generic.IEnumerable%601>, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawcy jest potrzebne do zaimplementowania funkcji *standardowych operatorów zapytań* dla tego źródła danych. Na przykład [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsługuje pracę podczas ładowania dokumentu XML do odpytywalnego <xref:System.Xml.Linq.XElement> typ, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — Przegląd (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 Za pomocą [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], należy najpierw utworzyć obiektowo relacyjny mapowanie w czasie projektowania, ręcznie lub za pomocą [LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) w programie Visual Studio. Piszesz zapytania dotyczące obiektów, a także w czasie wykonywania [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] obsługuje komunikację z bazą danych. W poniższym przykładzie `customers` reprezentuje określoną tabelę w bazie danych i <xref:System.Data.Linq.Table%601> obsługuje ogólny <xref:System.Linq.IQueryable%601>.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Aby uzyskać więcej informacji na temat sposobu tworzenia określonych typów źródeł danych, zobacz dokumentację dla różnych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawców. (Aby uzyskać listę tych dostawców, zobacz [LINQ (Language-Integrated Query)](../../../../visual-basic/programming-guide/concepts/linq/index.md).) Podstawowa zasada jest proste: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródło danych jest dowolny obiekt obsługujący ogólny <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub interfejs, który dziedziczy z niego.  
  
> [!NOTE]
>  Typy takie jak <xref:System.Collections.ArrayList> który obsługuje niepodstawowy <xref:System.Collections.IEnumerable> interfejs może również służyć jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródeł danych. Aby uzyskać przykład, który używa <xref:System.Collections.ArrayList>, zobacz [jak: Zapytanie w ArrayList za pomocą LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>Zapytanie  
 Należy określić w zapytaniu, informacji, które mają zostać pobrane ze źródła danych lub źródła. Istnieje również możliwość wybrania, jak te informacje powinny być sortowane, pogrupowane lub ze strukturą przed zwróceniem. Aby włączyć tworzenie kwerendy, Visual Basic ma włączyć nową składnię zapytań do języka.  
  
 Gdy jest wykonywany w poniższym przykładzie zwraca wszystkie liczby parzyste z tablicę liczb całkowitych `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Wyrażenie zapytania zawiera trzy klauzule: `From`, `Where`, i `Select`. Określoną funkcję i cel każdej klauzuli wyrażenie zapytania, które zostało omówione w [podstawowe operacje zapytań (Visual Basic)](basic-query-operations.md). Aby uzyskać więcej informacji, zobacz [zapytania](../../../../visual-basic/language-reference/queries/index.md). Należy pamiętać, że w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], definicja kwerendy często są przechowywane w zmiennej i wykonane później. Zapytanie zmiennych, takich jak `evensQuery` w poprzednim przykładzie, musi być typem odpytywalnym. Typ `evensQuery` jest `IEnumerable(Of Integer)`, przypisanego przez kompilator przy użyciu wnioskowanie o typie lokalnym.  
  
 Należy pamiętać, że sama zmienna zapytania nie podejmuje żadnych działań i nie zwraca żadnych danych. Przechowuje tylko definicja zapytania. W poprzednim przykładzie, jest `For Each` pętli, która wykonuje zapytanie.  
  
## <a name="query-execution"></a>Wykonywanie zapytania  
 Wykonywanie kwerendy różni się od tworzenia kwerendy. Tworzenie kwerendy definiuje zapytanie, ale wykonanie jest wyzwalane przez innego mechanizmu. Zapytania mogą być wykonywane natychmiast po tym, jak to zdefiniowano (*natychmiastowe wykonanie*), lub definicji mogą być przechowywane i zapytania, które może być wykonane później (*wykonanie odroczone*).  
  
### <a name="deferred-execution"></a>Wykonanie odroczone  
 Typowa [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania podobne do pokazanego na poprzednim przykładzie, w którym `evensQuery` jest zdefiniowana. Tworzy zapytanie, ale nie jest wykonywane go natychmiast. Zamiast tego, definicja kwerendy jest przechowywana w zmiennej zapytania `evensQuery`. Wykonaj zapytanie później, zwykle za pomocą `For Each` pętli, która zwraca sekwencję wartości lub stosując operator standardowego zapytania, takie jak `Count` lub `Max`. Ten proces jest nazywany *wykonanie odroczone*.  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 Dla sekwencji wartości, uzyskujesz dostęp do tych danych przy użycie zmiennej iteracyjnej w `For Each` pętli (`number` w poprzednim przykładzie). Ponieważ zmienna zapytania `evensQuery`, przechowuje definicji zapytania, a nie wyniki zapytania może wykonywać kwerendę tak często, jak za pomocą zmiennej zapytania więcej niż jeden raz. Na przykład Niewykluczone, że bazy danych w aplikacji, który jest stale aktualizowana przez oddzielną aplikację. Po utworzeniu zapytania, które pobierają dane z tej bazy danych, można użyć `For Each` pętli do wykonania zapytania wielokrotnie, pobieranie najnowszych danych z każdym razem, gdy.  
  
 Poniższy przykład pokazuje, jak odroczonego wykonania działania. Po `evensQuery2` został zdefiniowany i jest wykonywany z `For Each` pętli, jak w poprzednich przykładach, niektóre elementy w źródle danych `numbers` są zmieniane. Następnie sekundy `For Each` pętli przebiegów `evensQuery2` ponownie. Wyniki różnią się po raz drugi, ponieważ `For Each` pętla jest wykonywana zapytanie ponownie, używając nowych wartości w `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 Dane wyjściowe:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Natychmiastowe wykonanie  
 W odroczonego wykonania zapytania definicja kwerendy jest przechowywana w zmiennej zapytania do późniejszego wykonania. Natychmiastowe wykonanie zapytanie jest wykonywane w czasie jego definicji. Wykonanie jest wyzwalane, gdy stosujesz metodę, która wymaga dostępu do indywidualnych elementów wyniku zapytania. Natychmiastowe wykonanie często jest wymuszone za pomocą jednego z standardowych operatorów zapytań, które zwracają wartości pojedynczej. Należą do nich `Count`, `Max`, `Average`, i `First`. Te standardowe operatory zapytań wykonaj zapytanie, jak są one stosowane w celu wykonywania obliczeń i zwracania pojedynczy rezultat. Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, które zwracają wartości pojedynczej zobacz [operacje agregacji](aggregation-operations.md), [operacje na elementach](element-operations.md), i [Operacje kwantyfikatora](quantifier-operations.md).  
  
 Następujące zapytanie zwraca liczbę liczb parzystych w tablicy liczb całkowitych. Definicja zapytania nie jest zapisywane, a `numEvens` to prosta `Integer`.  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 Ten sam efekt można osiągnąć za pomocą `Aggregate` metody.  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 Możesz też wymusić wykonanie zapytania, wywołując `ToList` lub `ToArray` metody zapytania (natychmiastowa) lub zmienna zapytania (odroczona), jak pokazano w poniższym kodzie.  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 W poprzednich przykładach `evensQuery3` jest zapytaniem zmiennej, ale `evensList` się listę i `evensArray` jest tablicą.  
  
 Za pomocą `ToList` lub `ToArray` Aby wymusić natychmiastowe wykonanie jest szczególnie przydatne w scenariuszach, w których chcesz przeprowadzić zapytanie natychmiastowo i wyniki w jednym obiekcie kolekcji w pamięci podręcznej. Aby uzyskać więcej informacji o tych metodach, zobacz [konwertowanie typów danych](converting-data-types.md).  
  
 Kwerenda do wykonania przy użyciu także może powodować `IEnumerable` metody takie jak <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> metody.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](getting-started-with-linq.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Omówienie operatorów standardowej kwerendy (Visual Basic)](standard-query-operators-overview.md)
- [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Zapytania](../../../../visual-basic/language-reference/queries/index.md)
