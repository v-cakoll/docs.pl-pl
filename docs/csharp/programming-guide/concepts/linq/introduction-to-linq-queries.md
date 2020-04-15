---
title: Wprowadzenie do kwerend LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: 5a9d97ff14f087ddfc55986bf77f18492cbf8a04
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389577"
---
# <a name="introduction-to-linq-queries-c"></a>Wprowadzenie do kwerend LINQ (C#)
*Kwerenda* jest wyrażeniem pobieranym dane ze źródła danych. Zapytania są zwykle wyrażone w języku kwerend specjalistycznych. Z czasem opracowano różne języki dla różnych typów źródeł danych, na przykład SQL dla relacyjnych baz danych i XQuery dla XML. W związku z tym deweloperzy musieli nauczyć się nowego języka zapytań dla każdego typu źródła danych lub formatu danych, który muszą obsługiwać. LINQ upraszcza tę sytuację, oferując spójny model do pracy z danymi w różnych źródłach danych i formatach. W kwerendzie LINQ zawsze pracujesz z obiektami. Te same podstawowe wzorce kodowania są używane do wykonywania zapytań i przekształcania danych w dokumentach XML, bazach danych SQL, ADO.NET zestawach danych, kolekcjach platformy .NET i innych formatach, dla których dostawca LINQ jest dostępny.  
  
## <a name="three-parts-of-a-query-operation"></a>Trzy części operacji zapytania  
 Wszystkie operacje kwerendy LINQ składają się z trzech odrębnych akcji:  
  
1. Uzyskaj źródło danych.  
  
2. Utwórz kwerendę.  
  
3. Wykonaj zapytanie.  
  
 Poniższy przykład pokazuje, jak trzy części operacji kwerendy są wyrażone w kodzie źródłowym. W przykładzie używa tablicy liczby całkowitej jako źródła danych dla wygody; jednak te same pojęcia dotyczą również innych źródeł danych. Ten przykład jest odwoływany w pozostałej części tego tematu.  
  
 [!code-csharp[CsLINQGettingStarted#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#1)]  
  
 Na poniższej ilustracji przedstawiono pełną operację kwerendy. W LINQ wykonanie kwerendy różni się od samego zapytania. Innymi słowy nie zostały pobrane żadne dane tylko przez utworzenie zmiennej kwerendy.  
  
 ![Diagram pełnej operacji zapytania LINQ.](./media/introduction-to-linq-queries/linq-query-complete-operation.png)  
  
## <a name="the-data-source"></a>Źródło danych  
 W poprzednim przykładzie, ponieważ źródło danych jest tablicą, <xref:System.Collections.Generic.IEnumerable%601> niejawnie obsługuje interfejs ogólny. Fakt ten oznacza, że można go zbadać za pomocą LINQ. Kwerenda jest wykonywana `foreach` w `foreach` instrukcji <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601>i wymaga lub . Typy, <xref:System.Collections.Generic.IEnumerable%601> które obsługują lub interfejs <xref:System.Linq.IQueryable%601> pochodny, takich jak rodzajowy są *nazywane typy kwerendy*.  
  
 Typ, który można zbadać, nie wymaga modyfikacji ani specjalnego traktowania, aby służyć jako źródło danych LINQ. Jeśli dane źródłowe nie są jeszcze w pamięci jako typ, który można zbadać, dostawca LINQ musi reprezentować je jako takie. Na przykład [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ładuje dokument XML do <xref:System.Xml.Linq.XElement> typu, który można zbadać:  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 Za [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]pomocą programu , najpierw utworzysz mapowanie obiektowo-relacyjny w czasie projektowania ręcznie lub przy użyciu [LINQ do SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2). Piszesz zapytania względem obiektów, a w [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] czasie wykonywania obsługuje komunikację z bazą danych. W poniższym `Customers` przykładzie reprezentuje określoną tabelę w bazie danych, a typ wyniku kwerendy, <xref:System.Linq.IQueryable%601>pochodzi z <xref:System.Collections.Generic.IEnumerable%601>.  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Aby uzyskać więcej informacji na temat tworzenia określonych typów źródeł danych, zobacz dokumentację dla różnych dostawców LINQ. Jednak podstawowa reguła jest bardzo prosta: źródło danych LINQ <xref:System.Collections.Generic.IEnumerable%601> jest dowolny obiekt, który obsługuje interfejs ogólny lub interfejs, który dziedziczy z niego.  
  
> [!NOTE]
> Typy <xref:System.Collections.ArrayList> takie jak obsługujące <xref:System.Collections.IEnumerable> interfejs niegeneryczny może być również używany jako źródło danych LINQ. Aby uzyskać więcej informacji, zobacz [Jak zbadać listę tablic z LINQ (C#)](./how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a><a name="query"></a>Kwerenda  
 Kwerenda określa, jakie informacje mają być pobierane ze źródła danych lub źródeł. Opcjonalnie kwerenda określa również sposób sortowania, grupowania i kształtowania tych informacji przed ich zwracaniem. Kwerenda jest przechowywana w zmiennej kwerendy i inicjowana za pomocą wyrażenia kwerendy. Aby ułatwić pisanie zapytań, C# wprowadziła nową składnię kwerendy.  
  
 Kwerenda w poprzednim przykładzie zwraca wszystkie liczby parzyste z tablicy liczby całkowitej. Wyrażenie kwerendy zawiera trzy `from` `where` klauzule: , i `select`. (Jeśli znasz sql, można zauważyć, że kolejność klauzul jest odwrócony od kolejności w języku SQL.) Klauzula `from` określa źródło danych, `where` klauzula stosuje filtr, `select` a klauzula określa typ zwracanych elementów. Te i inne klauzule kwerendy są szczegółowo omówione w [języku zintegrowanej kwerendy (LINQ)](../../../linq/index.md) sekcji. Na razie ważnym punktem jest to, że w LINQ sama zmienna kwerendy nie wykonuje żadnych akcji i nie zwraca żadnych danych. Po prostu przechowuje informacje, które są wymagane do uzyskania wyników, gdy kwerenda jest wykonywana w późniejszym momencie. Aby uzyskać więcej informacji na temat sposobu konstruowania kwerend w tle, zobacz [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md).  
  
> [!NOTE]
> Zapytania mogą być również wyrażone przy użyciu składni metody. Aby uzyskać więcej informacji, zobacz [Składnia kwerendy i składnia metody w LINQ](./query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Wykonywanie zapytania  
  
### <a name="deferred-execution"></a>Wykonanie odroczone  
 Jak wspomniano wcześniej, sama zmienna kwerendy przechowuje tylko polecenia kwerendy. Rzeczywiste wykonanie kwerendy jest odroczone, dopóki nie iteruje `foreach` nad zmienną kwerendy w instrukcji. Pojęcie to jest określane jako *odroczone wykonanie* i jest wykazane w poniższym przykładzie:  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 Instrukcja `foreach` jest również, gdy wyniki kwerendy są pobierane. Na przykład w poprzedniej kwerendzie zmienna `num` iteracji przechowuje każdą wartość (po jednej naraz) w zwróconej sekwencji.  
  
 Ponieważ sama zmienna kwerendy nigdy nie przechowuje wyników kwerendy, można ją wykonać tak często, jak chcesz. Na przykład może mieć bazę danych, która jest stale aktualizowana przez oddzielną aplikację. W aplikacji można utworzyć jedną kwerendę, która pobiera najnowsze dane i można wykonać go wielokrotnie w pewnym przedziale czasu, aby pobrać różne wyniki za każdym razem.  
  
### <a name="forcing-immediate-execution"></a>Wymuszanie natychmiastowego wykonania  
 Kwerendy, które wykonują funkcje agregacji w zakresie elementów źródłowych musi najpierw iteracji nad tymi elementami. Przykładami takich zapytań `Count` `Max`są `Average`, `First`, i . Te wykonać bez `foreach` jawnej instrukcji, `foreach` ponieważ sama kwerenda musi używać w celu zwrócenia wyniku. Należy również zauważyć, że te typy zapytań zwracają pojedynczą wartość, a nie kolekcję. `IEnumerable` Następująca kwerenda zwraca liczbę liczb parzyste w tablicy źródłowej:  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 Aby wymusić natychmiastowe wykonanie dowolnej kwerendy i <xref:System.Linq.Enumerable.ToList%2A> <xref:System.Linq.Enumerable.ToArray%2A> buforować jej wyniki, można wywołać lub metody.  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 Można również wymusić wykonanie, umieszczając pętlę `foreach` natychmiast po wyrażeniu zapytania. Jednak wywołując `ToList` lub `ToArray` również buforować wszystkie dane w jednym obiekcie kolekcji.  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do korzystania z LINQ w C#](index.md)
- [Instruktaż: Pisanie zapytań w języku C #](./walkthrough-writing-queries-linq.md)
- [Language Integrated Query (LINQ)](../../../linq/index.md)
- [foreach, in](../../../language-reference/keywords/foreach-in.md)
- [Słowa kluczowe kwerendy (LINQ)](../../../language-reference/keywords/query-keywords.md)
