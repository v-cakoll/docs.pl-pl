---
title: Wprowadzenie do kwerend LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: 74a6f2e1e9296551f4faf73a905b49d3e2e3687e
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635720"
---
# <a name="introduction-to-linq-queries-c"></a>Wprowadzenie do kwerend LINQ (C#)
*Zapytanie* jest wyrażeniem, które pobiera dane ze źródła danych. Zapytania są zwykle wyrażane w wyspecjalizowanym języku zapytań. Różne języki zostały opracowane z upływem czasu dla różnych typów źródeł danych, na przykład SQL dla relacyjnych baz danych i XQuery dla XML. W związku z tym deweloperzy musieli poznać nowy język zapytań dla każdego typu źródła danych lub formatu danych, które muszą być obsługiwane przez program. LINQ upraszcza tę sytuację, oferując spójny model do pracy z danymi w różnych rodzajach źródeł danych i formatach. W zapytaniu LINQ zawsze pracujesz z obiektami. Te same podstawowe wzorce kodowania służą do wykonywania zapytań i przekształcania danych w dokumentach XML, baz danych SQL, ADO.NET, kolekcjach platformy .NET i innych formatach, dla których jest dostępny dostawca LINQ.  
  
## <a name="three-parts-of-a-query-operation"></a>Trzy części operacji zapytania  
 Wszystkie operacje zapytań LINQ składają się z trzech odrębnych akcji:  
  
1. Uzyskanie źródła danych.  
  
2. Utwórz zapytanie.  
  
3. Wykonaj zapytanie.  
  
 Poniższy przykład pokazuje, jak trzy części operacji zapytania są wyrażone w kodzie źródłowym. W przykładzie jest wykorzystywana tablica liczb całkowitych jako źródło danych dla wygody; Jednak te same koncepcje odnoszą się również do innych źródeł danych. Ten przykład jest określany w pozostałej części tego tematu.  
  
 [!code-csharp[CsLINQGettingStarted#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#1)]  
  
 Na poniższej ilustracji przedstawiono wykonywanie operacji zapytania. W LINQ, wykonywanie zapytania jest różne od samego zapytania. Innymi słowy, nie pobrano żadnych danych tylko przez utworzenie zmiennej zapytania.  
  
 ![Diagram pełnej operacji zapytania LINQ.](./media/introduction-to-linq-queries/linq-query-complete-operation.png)  
  
## <a name="the-data-source"></a>Źródło danych  
 W poprzednim przykładzie, ponieważ źródło danych jest tablicą, niejawnie obsługuje interfejs ogólny <xref:System.Collections.Generic.IEnumerable%601>. Oznacza to, że można to zrobić za pomocą LINQ. Zapytanie jest wykonywane w instrukcji `foreach` i `foreach` wymaga <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>. Typy obsługujące <xref:System.Collections.Generic.IEnumerable%601> lub interfejs pochodny, takie jak generyczne <xref:System.Linq.IQueryable%601>, są nazywane *typami Queryable*.  
  
 Typ Queryable nie wymaga modyfikacji ani specjalnego traktowania, które ma stanowić źródło danych LINQ. Jeśli dane źródłowe nie są jeszcze w pamięci jako typ queryable, dostawca LINQ musi je przedstawić jako taki. Na przykład [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ładuje dokument XML do typu <xref:System.Xml.Linq.XElement> Queryable:  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 Przy [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]należy najpierw utworzyć mapowanie relacyjne obiektu w czasie projektowania ręcznie lub za pomocą [narzędzi LINQ to SQL w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) w programie Visual Studio. Zapytania są zapisywane względem obiektów, a w czasie wykonywania [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] obsługuje komunikację z bazą danych. W poniższym przykładzie `Customers` reprezentuje określoną tabelę w bazie danych, a typ wyniku zapytania, <xref:System.Linq.IQueryable%601>, pochodzi z <xref:System.Collections.Generic.IEnumerable%601>.  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Więcej informacji o sposobach tworzenia określonych typów źródeł danych znajduje się w dokumentacji dotyczącej różnych dostawców LINQ. Podstawowa reguła jest jednak bardzo prosta: źródłem danych LINQ jest dowolny obiekt obsługujący ogólny interfejs <xref:System.Collections.Generic.IEnumerable%601> lub interfejs, który dziedziczy z niego.  
  
> [!NOTE]
> Typy takie jak <xref:System.Collections.ArrayList> obsługujące nieogólny interfejs <xref:System.Collections.IEnumerable> mogą być również używane jako źródło danych LINQ. Aby uzyskać więcej informacji, zobacz [How to Query The ArrayList with LINQC#()](./how-to-query-an-arraylist-with-linq.md).  
  
## <a name="query"></a>Zapytanie  
 Zapytanie określa, jakie informacje mają być pobierane ze źródła danych lub źródeł. Opcjonalnie zapytanie określa również, jak te informacje powinny być sortowane, grupowane i ukształtowane przed zwróceniem. Zapytanie jest przechowywane w zmiennej zapytania i inicjowane z wyrażeniem zapytania. Aby ułatwić Pisanie zapytań, C# wprowadzono nową składnię zapytania.  
  
 Zapytanie w poprzednim przykładzie zwraca wszystkie liczby parzyste z tablicy liczb całkowitych. Wyrażenie zapytania zawiera trzy klauzule: `from`, `where` i `select`. (Jeśli znasz program SQL, zobaczysz, że kolejność klauzul została odwrócona z kolejności w języku SQL). Klauzula `from` określa źródło danych, klauzula `where` stosuje filtr, a klauzula `select` określa typ zwracanych elementów. Te i inne klauzule zapytań są szczegółowo omówione w sekcji [wyrażenia zapytania LINQ](../../../linq/index.md) . Na razie istotnym punktem jest to, że w LINQ, zmienna zapytania nie przyjmuje żadnych akcji i nie zwraca żadnych danych. Po prostu przechowuje informacje, które są wymagane do wygenerowania wyników, gdy zapytanie jest wykonywane w późniejszym momencie. Aby uzyskać więcej informacji o tym, jak zapytania są konstruowane w tle, zobacz [standardowe operatory zapytańC#— omówienie ()](./standard-query-operators-overview.md).  
  
> [!NOTE]
> Zapytania można również wyrazić przy użyciu składni metody. Aby uzyskać więcej informacji, zobacz [składnia zapytań i składnia metod w LINQ](./query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Wykonywanie zapytania  
  
### <a name="deferred-execution"></a>Wykonanie odroczone  
 Jak wspomniano wcześniej, zmienna zapytania zawiera tylko polecenia zapytania. Rzeczywiste wykonanie zapytania jest odroczone do czasu przetworzenia iteracji względem zmiennej zapytania w instrukcji `foreach`. Koncepcja ta jest nazywana *wykonywaniem odroczonym* i przedstawiono w poniższym przykładzie:  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 Instrukcja `foreach` jest również miejscem, w którym pobierane są wyniki zapytania. Na przykład w poprzedniej kwerendzie Zmienna iteracji `num` przechowuje każdą wartość (pojedynczo) w zwracanej sekwencji.  
  
 Ponieważ sama zmienna zapytania nigdy nie przechowuje wyników zapytania, można wykonać ją tak często, jak chcesz. Na przykład może istnieć baza danych, która jest stale aktualizowana przez oddzielną aplikację. W aplikacji można utworzyć jedno zapytanie, które pobiera najnowsze dane, i można wykonać je wielokrotnie w pewnym interwale, aby pobierać różne wyniki za każdym razem.  
  
### <a name="forcing-immediate-execution"></a>Wymuszanie natychmiastowego wykonania  
 Zapytania, które wykonują funkcje agregacji dla zakresu elementów źródłowych, muszą najpierw wykonać iterację tych elementów. Przykładami takich zapytań są `Count`, `Max`, `Average`i `First`. Te wykonywanie bez jawnej instrukcji `foreach`, ponieważ zapytanie musi używać `foreach`, aby można było zwrócić wynik. Należy zauważyć, że te typy zapytań zwracają pojedynczą wartość, a nie kolekcję `IEnumerable`. Następujące zapytanie zwraca liczbę liczb parzystych w tablicy źródłowej:  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 Aby wymusić natychmiastowe wykonywanie dowolnego zapytania i buforować jego wyniki, można wywołać metody <xref:System.Linq.Enumerable.ToList%2A> lub <xref:System.Linq.Enumerable.ToArray%2A>.  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 Możesz również wymusić wykonywanie, umieszczając pętlę `foreach` bezpośrednio po wyrażeniu zapytania. Jednak przez wywołanie `ToList` lub `ToArray` można również buforować wszystkie dane w jednym obiekcie kolekcji.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do korzystania z LINQ w C#](/dotnet/csharp/programming-guide/concepts/linq/)
- [Przewodnik: Pisanie zapytań wC#](./walkthrough-writing-queries-linq.md)
- [Wyrażenia zapytania LINQ](../../../linq/index.md)
- [foreach, in](../../../language-reference/keywords/foreach-in.md)
- [Słowa kluczowe zapytania (LINQ)](../../../language-reference/keywords/query-keywords.md)
