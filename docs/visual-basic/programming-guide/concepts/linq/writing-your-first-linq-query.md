---
title: Pisanie pierwszego zapytania LINQ (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
caps.latest.revision: "56"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c16bb28189d5525654328da2dc80d868bbe61bf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="writing-your-first-linq-query-visual-basic"></a>Pisanie pierwszego zapytania LINQ (Visual Basic)
A *zapytania* jest wyrażenie, które pobiera dane ze źródła danych. Zapytania są wyrażane w języku dedykowanych zapytania. Wraz z upływem czasu w różnych językach opracowano dla różnych typów źródeł danych, na przykład SQL relacyjnych baz danych i XQuery dla formatu XML. Dzięki temu niezbędne dla deweloperów aplikacji dowiedzieć się nowy język kwerendy dla każdego typu źródła danych lub format danych, która jest obsługiwana.  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]upraszcza sytuację, oferując spójny model do pracy z danymi w różnych rodzajów źródeł danych i formaty. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, zawsze korzystasz z obiektów. Użyj tego samego kodowania wzorców podstawowych zapytań, przekształcania danych w dokumentach XML, baz danych SQL, danych ADO.NET i jednostek, kolekcji .NET Framework i wszelkie inne źródła lub format, dla którego [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawca jest niedostępny. W tym dokumencie opisano trzy etapy tworzenia i stosowania basic [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania.  
  
## <a name="three-stages-of-a-query-operation"></a>Trzy etapy operacji zapytania  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]Operacje kwerend obejmują trzy czynności:  
  
1.  Uzyskaj źródła danych lub źródła.  
  
2.  Utwórz zapytanie.  
  
3.  Wykonanie kwerendy.  
  
 W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], wykonanie zapytania różni się od utworzenia zapytania. Nie pobrać żadnych danych przez utworzenie kwerendy. Ten punkt jest omówiona bardziej szczegółowo w dalszej części tego tematu.  
  
 Poniższy przykład przedstawia trzy części operacji zapytania. W przykładzie użyto tablicy liczb całkowitych jako źródło danych wygodny dla celów demonstracyjnych. Jednak te same pojęcia dotyczą również innych źródeł danych.  
  
> [!NOTE]
>  Na [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), upewnij się, że **Option infer** ustawiono **na**.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Dane wyjściowe:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Źródło danych  
 Ponieważ źródło danych w poprzednim przykładzie jest tablicą, niejawnie obsługuje ogólnego <xref:System.Collections.Generic.IEnumerable%601> interfejsu. Jest to z faktu, że pozwala na użycie tablicy jako źródło danych dla [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Typy obsługujące <xref:System.Collections.Generic.IEnumerable%601> lub interfejsu pochodnego, takich jak ogólnego <xref:System.Linq.IQueryable%601> są nazywane *typy zapytań*.  
  
 W ustawieniu typu niejawnie kolejność tablicy nie musi podawać modyfikacji i szczególnego traktowania jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródła danych. To samo dotyczy dowolnego typu kolekcji, która obsługuje <xref:System.Collections.Generic.IEnumerable%601>, łącznie z ogólnego <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>i inne klasy w bibliotece klas programu .NET Framework.  
  
 Jeśli źródło danych nie obsługuje już <xref:System.Collections.Generic.IEnumerable%601>, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawcy jest wymagane w celu wdrożenia funkcji *standardowych operatorów zapytań* dla tego źródła danych. Na przykład [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsługuje ładowania dokumentu XML do kolejność pracy <xref:System.Xml.Linq.XElement> typ, jak pokazano w poniższym przykładzie. Aby uzyskać więcej informacji dotyczących standardowych operatorów zapytań, zobacz [standardowe operatory zapytań — omówienie (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 Z [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], należy najpierw utworzyć obiektów relacyjnych mapowanie w czasie projektowania, ręcznie lub za pomocą [składnika LINQ to SQL narzędzia w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) w programie Visual Studio. Pisanie zapytań względem obiektów oraz w czasie wykonywania [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] obsługuje komunikację z bazą danych. W poniższym przykładzie `customers` reprezentuje określonej tabeli w bazie danych i <xref:System.Data.Linq.Table%601> ogólny obsługuje <xref:System.Linq.IQueryable%601>.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Aby uzyskać więcej informacji o sposobie tworzenia określonych typów źródeł danych, zobacz dokumentację dla różnych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawców. (Aby uzyskać listę tych dostawców, zobacz [LINQ (zapytania język Language-Integrated)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).) Podstawowe reguły jest prosty: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródło danych jest dowolny obiekt, który obsługuje ogólnego <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub interfejsu, który dziedziczy z niego.  
  
> [!NOTE]
>  Typy, takich jak <xref:System.Collections.ArrayList> inny niż ogólny, który obsługuje <xref:System.Collections.IEnumerable> interfejs może również służyć jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródeł danych. Na przykład, który używa <xref:System.Collections.ArrayList>, zobacz [porady: zapytanie w ArrayList za pomocą LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>Zapytanie  
 W zapytaniu należy określić informacji, które mają zostać pobrane ze źródła danych lub źródła. Istnieje również możliwość określania, jak te informacje powinny być sortowane, pogrupowane lub strukturę przed zwróceniem jest. Aby włączyć tworzenie zapytań, Visual Basic ma włączyć nowej składni zapytania do języka.  
  
 Po wykonaniu, zapytanie w poniższym przykładzie zwraca wszystkie liczby parzyste z tablicy całkowitą `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Wyrażenia zapytania zawiera trzy klauzule: `From`, `Where`, i `Select`. Omówione w określonych funkcji i celów poszczególnych klauzuli wyrażenia zapytania [podstawowe operacje zapytań (Visual Basic)](basic-query-operations.md). Aby uzyskać więcej informacji, zobacz [zapytania](../../../../visual-basic/language-reference/queries/queries.md). Należy pamiętać, że w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], definicji zapytania często jest przechowywana w zmiennej i wykonać później. Zapytanie zmiennych, takich jak `evensQuery` w poprzednim przykładzie, musi być typem zapytań. Typ `evensQuery` jest `IEnumerable(Of Integer)`, przypisane przez kompilator przy użyciu wnioskowanie o typie lokalnym.  
  
 Należy pamiętać, że samej zmiennej zapytanie Brak działania i zwraca żadnych danych. Definicja zapytania jest przechowywana tylko. W poprzednim przykładzie jest `For Each` pętli wykonujący zapytanie.  
  
## <a name="query-execution"></a>Wykonywanie zapytania  
 Wykonywanie zapytania jest oddzielony od tworzenia zapytania. Tworzenie zapytań definiuje kwerendy, ale wykonanie jest wyzwalane przez inny mechanizm. Można było wykonać zapytanie, jak jest zdefiniowany (*natychmiastowego wykonania*), lub definicji mogą być przechowywane i można było wykonać zapytanie później (*odroczonego wykonania*).  
  
### <a name="deferred-execution"></a>Wykonanie odroczone  
 Typowe [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania opisany w poprzednim przykładzie, w którym `evensQuery` jest zdefiniowany. Tworzy zapytanie, ale nie wykonuje on natychmiast. Zamiast tego definicja zapytania jest przechowywana w zmiennej zapytania `evensQuery`. Wykonanie kwerendy później, zwykle za pomocą `For Each` pętli, która zwraca sekwencję wartości lub przez zastosowanie operatora zapytania standardowe, takie jak `Count` lub `Max`. Ten proces jest nazywany *odroczonego wykonania*.  
  
 [!code-vb[VbLINQFirstQuery#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 Sekwencji wartości dostępu pobrane dane przy użyciu zmiennej iteracji w `For Each` pętli (`number` w poprzednim przykładzie). Ponieważ zmienną zapytania `evensQuery`, posiada definicji zapytania, zamiast wyniki zapytania można wykonać zapytania tyle razy, ile przy użyciu zmiennej zapytania więcej niż jeden raz. Na przykład może być bazy danych w aplikacji, która jest aktualizowana stale w innej aplikacji. Po utworzeniu kwerendę, która pobiera dane z bazy danych, można użyć `For Each` pętli do wykonania zapytania, pobieranie najnowszych danych zawsze.  
  
 W poniższym przykładzie pokazano sposób odroczonego wykonania działania. Po `evensQuery2` został zdefiniowany i jest wykonywane z `For Each` pętli, jak w poprzednich przykładach, niektóre elementy w źródle danych `numbers` są zmieniane. Następnie drugiej `For Each` pętli działa `evensQuery2` ponownie. Wyniki są różne po raz drugi, ponieważ `For Each` pętla jest wykonywana zapytanie ponownie, używając nowej wartości w `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 Dane wyjściowe:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Natychmiastowe wykonanie  
 Odroczone podczas wykonywania zapytań definicja zapytania jest przechowywana w zmiennej zapytanie później. Podczas wykonywania bezpośredniego zapytanie jest wykonywane w czasie jego definicji. Wykonanie jest wyzwalane po zastosowaniu metody, która wymaga dostępu do poszczególnych elementów w wyniku zapytania. Często natychmiastowego wykonania wymusza przy użyciu jednej z standardowych operatorów zapytań zwracających jednej wartości. Przykłady `Count`, `Max`, `Average`, i `First`. Te standardowe operatory zapytań wykonać zapytanie, jak są one stosowane w celu obliczania i zwracają wynik singleton. Aby uzyskać więcej informacji o standardowych operatorów zapytań zwracających wartości jeden, zobacz [operacje agregacji](aggregation-operations.md), [operacje na elementach](element-operations.md), i [Operacje kwantyfikatora](quantifier-operations.md).  
  
 Następujące zapytanie zwraca liczbę liczby parzyste w tablicy liczb całkowitych. Definicja zapytania nie zostanie zapisana, i `numEvens` jest prostą `Integer`.  
  
 [!code-vb[VbLINQFirstQuery#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 Taki sam efekt można osiągnąć za pomocą `Aggregate` metody.  
  
 [!code-vb[VbLINQFirstQuery#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 Możesz też wymusić wykonanie kwerendy, wywołując `ToList` lub `ToArray` metoda zapytania (natychmiastowa) lub zmienną zapytania (odroczona), jak pokazano w poniższym kodzie.  
  
 [!code-vb[VbLINQFirstQuery#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 W poprzednich przykładach `evensQuery3` jest zapytaniem zmiennej, ale `evensList` jest listą i `evensArray` jest tablicą.  
  
 Przy użyciu `ToList` lub `ToArray` Aby wymusić natychmiastowe wykonanie jest szczególnie przydatne w scenariuszach, w których chcesz natychmiast wykonać zapytania i pamięci podręcznej wyniki w obiekcie jednej kolekcji. Aby uzyskać więcej informacji na temat tych metod, zobacz [konwertowanie typów danych](converting-data-types.md).  
  
 Może również spowodować kwerendzie wykonywanej przy użyciu `IEnumerable` metody, takie jak <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do korzystania z LINQ w Visual Basic](getting-started-with-linq.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Operatory standardowe zapytań — omówienie (Visual Basic)](standard-query-operators-overview.md)  
 [Wprowadzenie do LINQ w Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Zapytania](../../../../visual-basic/language-reference/queries/queries.md)
