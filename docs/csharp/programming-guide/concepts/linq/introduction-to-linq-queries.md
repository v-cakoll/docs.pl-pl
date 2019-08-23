---
title: Wprowadzenie do kwerend LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: 6188af0ffea699899212e4bcf20b7c19f68858b4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924334"
---
# <a name="introduction-to-linq-queries-c"></a>Wprowadzenie do kwerend LINQ (C#)
*Zapytanie* jest wyrażeniem, które pobiera dane ze źródła danych. Zapytania są zwykle wyrażane w wyspecjalizowanym języku zapytań. Różne języki zostały opracowane z upływem czasu dla różnych typów źródeł danych, na przykład SQL dla relacyjnych baz danych i XQuery dla XML. W związku z tym deweloperzy musieli poznać nowy język zapytań dla każdego typu źródła danych lub formatu danych, które muszą być obsługiwane przez program. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]upraszcza tę sytuację, oferując spójny model do pracy z danymi w różnych rodzajach źródeł danych i formatach. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] W zapytaniu zawsze pracujesz z obiektami. Te same podstawowe wzorce kodowania służą do wykonywania zapytań i przekształcania danych w dokumentach XML, baz danych SQL, ADO.NET, kolekcjach platformy .NET i innych formatach, dla [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] których dostawca jest dostępny.  
  
## <a name="three-parts-of-a-query-operation"></a>Trzy części operacji zapytania  
 Wszystkie [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] operacje zapytań składają się z trzech odrębnych akcji:  
  
1. Uzyskanie źródła danych.  
  
2. Utwórz zapytanie.  
  
3. Wykonaj zapytanie.  
  
 Poniższy przykład pokazuje, jak trzy części operacji zapytania są wyrażone w kodzie źródłowym. W przykładzie jest wykorzystywana tablica liczb całkowitych jako źródło danych dla wygody; Jednak te same koncepcje odnoszą się również do innych źródeł danych. Ten przykład jest określany w pozostałej części tego tematu.  
  
 [!code-csharp[CsLINQGettingStarted#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#1)]  
  
 Na poniższej ilustracji przedstawiono wykonywanie operacji zapytania. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] trakcie wykonywania zapytania różni się od samego zapytania; innymi słowy nie pobrano żadnych danych tylko przez utworzenie zmiennej zapytania.  
  
 ![Diagram pełnej operacji zapytania LINQ.](./media/introduction-to-linq-queries/linq-query-complete-operation.png)  
  
## <a name="the-data-source"></a>Źródło danych  
 W poprzednim przykładzie, ponieważ źródło danych jest tablicą, niejawnie obsługuje interfejs ogólny <xref:System.Collections.Generic.IEnumerable%601> . Oznacza to, że można je zbadać przy użyciu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Zapytanie `foreach` jest wykonywane w instrukcji i `foreach` wymaga <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>. Typy obsługujące <xref:System.Collections.Generic.IEnumerable%601> lub interfejs pochodny, takie jak generyczne <xref:System.Linq.IQueryable%601> , są nazywane *typami Queryable*.  
  
 Typ Queryable nie wymaga modyfikacji ani specjalnego traktowania, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] które ma stanowić źródło danych. Jeśli dane źródłowe nie są jeszcze w pamięci jako typ queryable, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawca musi je przedstawić jako taki. Na przykład [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wczytuje dokument XML do typu queryable <xref:System.Xml.Linq.XElement> :  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 W programie należy najpierw utworzyć mapowanie relacyjne obiektu w czasie projektowania ręcznie lub za pomocą [narzędzi LINQ to SQL w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) w programie Visual Studio. [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] Zapytania są zapisywane względem obiektów i w czasie [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] wykonywania obsługują komunikację z bazą danych. W poniższym przykładzie `Customers` reprezentuje określoną tabelę w bazie danych, a typ <xref:System.Linq.IQueryable%601>wyniku zapytania,, pochodzi od <xref:System.Collections.Generic.IEnumerable%601>.  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Aby uzyskać więcej informacji o sposobach tworzenia określonych typów źródeł danych, zapoznaj się z dokumentacją dla [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] różnych dostawców. Podstawowa reguła jest jednak bardzo prosta: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródłem danych jest dowolny obiekt obsługujący interfejs ogólny <xref:System.Collections.Generic.IEnumerable%601> lub interfejs, który dziedziczy z niego.  
  
> [!NOTE]
> Typy takie jak <xref:System.Collections.ArrayList> obsługujące interfejs nieogólny <xref:System.Collections.IEnumerable> mogą [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] również służyć jako źródło danych. Aby uzyskać więcej informacji, zobacz [jak: Zbadaj ArrayList za pomocą LINQC#(](./how-to-query-an-arraylist-with-linq.md)).  
  
## <a name="query"></a>Zapytanie  
 Zapytanie określa, jakie informacje mają być pobierane ze źródła danych lub źródeł. Opcjonalnie zapytanie określa również, jak te informacje powinny być sortowane, grupowane i ukształtowane przed zwróceniem. Zapytanie jest przechowywane w zmiennej zapytania i inicjowane z wyrażeniem zapytania. Aby ułatwić Pisanie zapytań, C# wprowadzono nową składnię zapytania.  
  
 Zapytanie w poprzednim przykładzie zwraca wszystkie liczby parzyste z tablicy liczb całkowitych. Wyrażenie zapytania zawiera trzy klauzule: `from`, `where` i `select`. (Jeśli znasz program SQL, zobaczysz, że kolejność klauzul została odwrócona z kolejności w języku SQL). Klauzula określa źródło danych `where` , klauzula stosuje filtr, a `select` klauzula określa typ zwracanych elementów. `from` Te i inne klauzule zapytań są szczegółowo omówione w sekcji [wyrażenia zapytania LINQ](../../linq-query-expressions/index.md) . Na razie istotnym punktem jest to, że [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]w programie zmienna zapytania nie przyjmuje żadnej akcji i nie zwraca żadnych danych. Po prostu przechowuje informacje, które są wymagane do wygenerowania wyników, gdy zapytanie jest wykonywane w późniejszym momencie. Aby uzyskać więcej informacji o tym, jak zapytania są konstruowane w tle, zobacz [standardowe operatory zapytańC#— omówienie ()](./standard-query-operators-overview.md).  
  
> [!NOTE]
> Zapytania można również wyrazić przy użyciu składni metody. Aby uzyskać więcej informacji, zobacz [składnia zapytań i składnia metod w LINQ](./query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Wykonywanie zapytania  
  
### <a name="deferred-execution"></a>Wykonanie odroczone  
 Jak wspomniano wcześniej, zmienna zapytania zawiera tylko polecenia zapytania. Rzeczywiste wykonanie zapytania jest odroczone do czasu przetworzenia iteracji względem zmiennej zapytania w `foreach` instrukcji. Koncepcja ta jest nazywana *wykonywaniem odroczonym* i przedstawiono w poniższym przykładzie:  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 `foreach` Instrukcja jest również miejscem, w którym są pobierane wyniki zapytania. Na przykład w poprzedniej kwerendzie zmienna `num` iteracji przechowuje każdą wartość (pojedynczo) w zwracanej sekwencji.  
  
 Ponieważ sama zmienna zapytania nigdy nie przechowuje wyników zapytania, można wykonać ją tak często, jak chcesz. Na przykład może istnieć baza danych, która jest stale aktualizowana przez oddzielną aplikację. W aplikacji można utworzyć jedno zapytanie, które pobiera najnowsze dane, i można wykonać je wielokrotnie w pewnym interwale, aby pobierać różne wyniki za każdym razem.  
  
### <a name="forcing-immediate-execution"></a>Wymuszanie natychmiastowego wykonania  
 Zapytania, które wykonują funkcje agregacji dla zakresu elementów źródłowych, muszą najpierw wykonać iterację tych elementów. Przykładami takich zapytań są `Count` `Average`, `Max`,, i `First`. Te wykonywanie bez jawnej `foreach` instrukcji, ponieważ zapytanie musi być używane `foreach` w celu zwrócenia wyniku. Należy zauważyć, że te typy zapytań zwracają pojedynczą wartość, a nie `IEnumerable` kolekcję. Następujące zapytanie zwraca liczbę liczb parzystych w tablicy źródłowej:  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 Aby wymusić natychmiastowe wykonywanie dowolnych zapytań i buforować wyniki, można <xref:System.Linq.Enumerable.ToList%2A> wywołać <xref:System.Linq.Enumerable.ToArray%2A> metody lub.  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 Możesz również wymusić wykonywanie przez umieszczenie `foreach` pętli bezpośrednio po wyrażeniu zapytania. Jednak przez wywołanie `ToList` lub `ToArray` można również buforować wszystkie dane w jednym obiekcie kolekcji.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do korzystania z LINQ w C#](./getting-started-with-linq.md)
- [Przewodnik: Pisanie zapytań wC#](./walkthrough-writing-queries-linq.md)
- [Wyrażenia zapytania LINQ](../../linq-query-expressions/index.md)
- [foreach, in](../../../language-reference/keywords/foreach-in.md)
- [Słowa kluczowe zapytania (LINQ)](../../../language-reference/keywords/query-keywords.md)
