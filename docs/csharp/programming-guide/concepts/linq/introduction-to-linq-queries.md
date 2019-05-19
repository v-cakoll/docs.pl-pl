---
title: Wprowadzenie do kwerend LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: 4276a1a7308e07b2dfb9cacb5670e97f6e2ca732
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879206"
---
# <a name="introduction-to-linq-queries-c"></a>Wprowadzenie do kwerend LINQ (C#)
A *zapytania* jest wyrażeniem, które pobiera dane ze źródła danych. Zapytania są zwykle wyrażane w specjalistycznym języku zapytań. Czas dla różnych rodzajów źródeł danych, na przykład SQL dla relacyjnych baz danych i XQuery dla XML zostały opracowane w różnych językach. Dlatego programiści musieli nauczyć się nowego języka zapytań dla każdego typu źródła danych lub formatu danych, które muszą obsługiwać. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] upraszcza tę sytuację oferując spójny model do pracy z danymi w różnych rodzajach formatów i źródeł danych. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, zawsze pracujesz z obiektami. Używasz tych samych podstawowych schematów kodowania do wykonywania zapytań i przekształcanie danych w dokumentów XML, baz danych SQL, zestawami danych ADO.NET, kolekcjach .NET i innych formatów, dla którego [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawca jest niedostępny.  
  
## <a name="three-parts-of-a-query-operation"></a>Trzy części operacji zapytania  
 Wszystkie [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania operacje składają się z trzech odrębnych czynności:  
  
1. Uzyskaj źródło danych.  
  
2. Utwórz zapytanie.  
  
3. Wykonaj zapytanie.  
  
 Poniższy przykład pokazuje, jak trzy części operacji zapytania są wyrażone w kodzie źródłowym. W przykładzie użyto tablicę liczb całkowitych jako źródła danych dla wygody; Jednak te same pojęcia dotyczą innych źródeł danych również. W tym przykładzie jest określana w pozostałej części tego tematu.  
  
 [!code-csharp[CsLINQGettingStarted#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#1)]  
  
 Poniższa ilustracja przedstawia pełną operację zapytania. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wykonywanie kwerendy różni się od samego zapytania; innymi słowy nie pobrano żadnych danych tylko przez utworzenie zmiennej zapytania.  
  
 ![Diagram pełną operację zapytania LINQ.](./media/introduction-to-linq-queries/linq-query-complete-operation.png)  
  
## <a name="the-data-source"></a>Źródło danych  
 W poprzednim przykładzie ponieważ źródło danych jest tablicą, niejawnie obsługuje ogólny <xref:System.Collections.Generic.IEnumerable%601> interfejsu. Fakt ten oznacza możliwość zapytania z [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Zapytanie jest wykonywane w `foreach` instrukcji i `foreach` wymaga <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>. Typy obsługujące <xref:System.Collections.Generic.IEnumerable%601> lub interfejs pochodny, takie jak typowa <xref:System.Linq.IQueryable%601> są nazywane *typami odpytywalnymi*.  
  
 Typ odpytywalny nie wymaga modyfikacji ani specjalnego traktowania, aby pełnić rolę [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródła danych. Jeśli źródło danych nie jest jeszcze w pamięci jako typ odpytywalny [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawcy musi reprezentowania je jako takie. Na przykład [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ładuje dokument XML do odpytywalnego <xref:System.Xml.Linq.XElement> typu:  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 Za pomocą [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], należy najpierw utworzyć obiektowo relacyjny mapowanie w czasie projektowania ręcznie lub za pomocą [LINQ to SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) w programie Visual Studio. Piszesz zapytania dotyczące obiektów, a także w czasie wykonywania [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] obsługuje komunikację z bazą danych. W poniższym przykładzie `Customers` reprezentuje określoną tabelę w bazie danych, a typ wyniku zapytania <xref:System.Linq.IQueryable%601>, pochodzi z <xref:System.Collections.Generic.IEnumerable%601>.  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Aby uzyskać więcej informacji na temat sposobu tworzenia określonych typów źródeł danych, zobacz dokumentację dla różnych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawców. Podstawowa zasada jest jednak bardzo prosta: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródło danych jest dowolny obiekt obsługujący ogólny <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub interfejs, który dziedziczy z niego.  
  
> [!NOTE]
>  Typy takie jak <xref:System.Collections.ArrayList> który obsługuje niepodstawowy <xref:System.Collections.IEnumerable> interfejs może również służyć jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródła danych. Aby uzyskać więcej informacji, zobacz [jak: Zapytanie w ArrayList za pomocą LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).  
  
## <a name="query"></a> Zapytanie  
 Zapytanie Określa, jakie informacje należy pobrać ze źródłem danych lub źródła. Opcjonalnie zapytanie określa również, jak te informacje powinny można sortowane, grupowane i kształtowane przed zwróceniem. Zapytanie jest przechowywane w zmiennej zapytania i inicjowane za pomocą wyrażenia zapytania. Aby ułatwić Zapisywanie zapytań, język C# wprowadził nową składnię zapytań.  
  
 W poprzednim przykładzie zwraca wszystkie liczby parzyste z tablicy liczb całkowitych. Wyrażenie zapytania zawiera trzy klauzule: `from`, `where` i `select`. (Jeśli jesteś zaznajomiony z językiem SQL, zauważą, że zamawianie klauzul jest wycofywane z zamówienia w języku SQL.) `from` Klauzula Określa źródło danych `where` zdanie odnosi się do filtru, a `select` klauzula Określa typ zwracanych elementów. Te i inne klauzule zapytania są szczegółowo omówione w [wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md) sekcji. Teraz istotną kwestią jest to, że w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], sama zmienna zapytania nie podejmuje żadnych działań i nie zwraca żadnych danych. Po prostu przechowuje informacje, które są wymagane w celu uzyskania wyników, gdy zapytanie jest wykonywane w pewnym momencie później. Aby uzyskać więcej informacji na temat sposobu tworzenia zapytań w tle, zobacz [standardowe operatory zapytań — Przegląd (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
> [!NOTE]
>  Zapytania można również wyrazić za pomocą składni metody. Aby uzyskać więcej informacji, zobacz [składnia zapytania a składnia metody w technologii LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Wykonywanie zapytania  
  
### <a name="deferred-execution"></a>Wykonanie odroczone  
 Jak wspomniano wcześniej, zmienna kwerendy przechowuje tylko polecenia kwerendy. Rzeczywiste wykonanie zapytania jest odroczone do czasu iteracji nad zmienną kwerendy w `foreach` instrukcji. Takie podejście jest określany jako *wykonanie odroczone* i została przedstawiona w poniższym przykładzie:  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 `foreach` Instrukcja jest również, gdzie pobierane są wyniki zapytania. Na przykład w poprzednim zapytaniu Zmienna iteracji `num` przechowuje każdą wartości (jedną na raz) w zwracanej sekwencji.  
  
 Ponieważ sama zmienna kwerendy nigdy nie przechowuje wyników kwerendy, można wykonywać ją tak często, jak chcesz. Na przykład masz bazę danych, która jest stale aktualizowana przez oddzielną aplikację. W aplikacji można utworzyć jedno zapytanie, które pobiera najnowsze dane, a użytkownik może je wykonać wielokrotnie z pewnym interwałem w celu pobierania różnych wyników za każdym razem, gdy.  
  
### <a name="forcing-immediate-execution"></a>Wymuszanie natychmiastowego wykonania  
 Zapytania, które wykonują funkcje agregacji w zakresie elementów źródła najpierw muszą przejść przez te elementy. Przykłady takich zapytań `Count`, `Max`, `Average`, i `First`. Działają one bez wyraźnej `foreach` instrukcji ponieważ samo zapytanie musi użyć `foreach` celu zwrócenia wyników. Należy zauważyć, tego rodzaju zapytania nie zwracać pojedynczą wartość, `IEnumerable` kolekcji. Następujące zapytanie zwraca liczbę liczb parzystych w tablicy źródłowej:  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 Aby wymusić natychmiastowe wykonanie dowolnego zapytania i buforowanie jego wyników, należy wywołać <xref:System.Linq.Enumerable.ToList%2A> lub <xref:System.Linq.Enumerable.ToArray%2A> metody.  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 Można również wymusić wykonanie przez umieszczenie `foreach` pętli natychmiast po wyrażeniu zapytania. Jednakże wywołując `ToList` lub `ToArray` , również buforujesz wszystkie dane w jednym obiekcie kolekcji.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do korzystania z LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Przewodnik: Pisanie zapytań wC#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [Wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [foreach, in](../../../../csharp/language-reference/keywords/foreach-in.md)
- [Słowa kluczowe zapytania (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md)
