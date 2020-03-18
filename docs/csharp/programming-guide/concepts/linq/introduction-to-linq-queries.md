---
title: Wprowadzenie do kwerend LINQ (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
ms.openlocfilehash: 7fbdfa8656e3c4832226370dc6efe56964e14934
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168508"
---
# <a name="introduction-to-linq-queries-c"></a>Wprowadzenie do kwerend LINQ (C#)
*Kwerenda* jest wyrażeniem pobierającym dane ze źródła danych. Zapytania są zwykle wyrażane w specjalistycznym języku zapytań. Różne języki zostały opracowane w czasie dla różnych typów źródeł danych, na przykład SQL dla relacyjnych baz danych i XQuery dla XML. W związku z tym deweloperzy musieli nauczyć się nowego języka zapytań dla każdego typu źródła danych lub formatu danych, które muszą obsługiwać. LINQ upraszcza tę sytuację, oferując spójny model pracy z danymi w różnych rodzajach źródeł danych i formatów. W kwerendzie LINQ zawsze pracujesz z obiektami. Te same podstawowe wzorce kodowania są używane do wykonywania zapytań i przekształcania danych w dokumentach XML, bazach danych SQL, ADO.NET zestawach danych, kolekcjach .NET i dowolnym innym formacie, dla którego dostępny jest dostawca LINQ.  
  
## <a name="three-parts-of-a-query-operation"></a>Trzy części operacji zapytania  
 Wszystkie operacje kwerendy LINQ składają się z trzech różnych akcji:  
  
1. Uzyskaj źródło danych.  
  
2. Utwórz kwerendę.  
  
3. Wykonaj zapytanie.  
  
 W poniższym przykładzie pokazano, jak trzy części operacji kwerendy są wyrażone w kodzie źródłowym. W przykładzie użyto tablicy całkowitej jako źródła danych dla wygody; jednak te same pojęcia mają zastosowanie również do innych źródeł danych. Ten przykład jest określany w pozostałej części tego tematu.  
  
 [!code-csharp[CsLINQGettingStarted#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#1)]  
  
 Na poniższej ilustracji przedstawiono pełną operację kwerendy. W LINQ wykonanie kwerendy różni się od samej kwerendy. Innymi słowy, nie zostały pobrane żadne dane tylko przez utworzenie zmiennej kwerendy.  
  
 ![Diagram pełnej operacji kwerendy LINQ.](./media/introduction-to-linq-queries/linq-query-complete-operation.png)  
  
## <a name="the-data-source"></a>Źródło danych  
 W poprzednim przykładzie, ponieważ źródło danych jest tablicą, <xref:System.Collections.Generic.IEnumerable%601> niejawnie obsługuje interfejs ogólny. Fakt ten oznacza, że można go zapytać za pomocą LINQ. Kwerenda jest `foreach` wykonywana w `foreach` <xref:System.Collections.IEnumerable> instrukcji <xref:System.Collections.Generic.IEnumerable%601>i wymaga lub . Typy obsługujące <xref:System.Collections.Generic.IEnumerable%601> lub pochodny interfejs, <xref:System.Linq.IQueryable%601> taki jak ogólny, są nazywane *typami zapytań*.  
  
 Typ z możliwością zapytań nie wymaga modyfikacji ani specjalnego traktowania, aby służyć jako źródło danych LINQ. Jeśli dane źródłowe nie jest już w pamięci jako typ zapytań, dostawca LINQ musi reprezentować go jako takie. Na przykład [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ładuje dokument XML <xref:System.Xml.Linq.XElement> do typu podleganego zapytań:  
  
 [!code-csharp[CsLINQGettingStarted#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#2)]  
  
 Za [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]pomocą , najpierw utworzyć mapowanie obiekt-relacyjne w czasie projektowania ręcznie lub za pomocą [LINQ do SQL Tools w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) w programie Visual Studio. Piszesz zapytania względem obiektów, a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] w czasie wykonywania obsługuje komunikację z bazą danych. W poniższym `Customers` przykładzie reprezentuje określoną tabelę w bazie danych, a <xref:System.Linq.IQueryable%601>typ wyniku <xref:System.Collections.Generic.IEnumerable%601>kwerendy , pochodzi od .  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Aby uzyskać więcej informacji na temat tworzenia określonych typów źródeł danych, zobacz dokumentację dla różnych dostawców LINQ. Jednak podstawowa reguła jest bardzo prosta: źródło danych LINQ <xref:System.Collections.Generic.IEnumerable%601> jest dowolnym obiektem, który obsługuje interfejs ogólny lub interfejsem, który dziedziczy z niego.  
  
> [!NOTE]
> Typy, <xref:System.Collections.ArrayList> takie jak te, <xref:System.Collections.IEnumerable> które obsługują interfejs nierodzajowy może być również używany jako źródło danych LINQ. Aby uzyskać więcej informacji, zobacz [Jak wysyłać zapytania do list tabliczki z LINQ (C#)](./how-to-query-an-arraylist-with-linq.md).  
  
## <a name="query"></a>Kwerenda  
 Kwerenda określa, jakie informacje należy pobrać ze źródła danych lub źródeł. Opcjonalnie kwerenda określa również, jak te informacje powinny być sortowane, grupowane i kształtowane przed ich zwróceniem. Kwerenda jest przechowywana w zmiennej kwerendy i inicjowana z wyrażeniem kwerendy. Aby ułatwić pisanie zapytań, C# wprowadził nową składnię kwerendy.  
  
 Kwerenda w poprzednim przykładzie zwraca wszystkie liczby parzyste z tablicy całkowitej. Wyrażenie kwerendy zawiera trzy `from` `where` klauzule: , i `select`. (Jeśli znasz SQL, można zauważyć, że kolejność klauzul jest odwrócona od kolejności w SQL.) Klauzula `from` określa źródło danych, `where` klauzula stosuje filtr, `select` a klauzula określa typ zwróconych elementów. Te i inne klauzule zapytania są szczegółowo omówione w [sekcji Language Integrated Query (LINQ).](../../../linq/index.md) Na razie ważne jest to, że w LINQ sama zmienna kwerendy nie wykonuje żadnej akcji i nie zwraca żadnych danych. Po prostu przechowuje informacje, które są wymagane do uzyskania wyników, gdy kwerenda jest wykonywana w pewnym późniejszym momencie. Aby uzyskać więcej informacji na temat sposobu konstruowania zapytań w tle, zobacz [Omówienie standardowych operatorów zapytań (C#).](./standard-query-operators-overview.md)  
  
> [!NOTE]
> Zapytania mogą być również wyrażane przy użyciu składni metody. Aby uzyskać więcej informacji, zobacz [Składnia kwerend i Składnia metody w pliku LINQ](./query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Wykonywanie zapytania  
  
### <a name="deferred-execution"></a>Wykonanie odroczone  
 Jak wspomniano wcześniej, zmienna kwerendy sama przechowuje tylko polecenia kwerendy. Rzeczywiste wykonanie kwerendy jest odroczone, dopóki nie iterate `foreach` nad zmienną kwerendy w instrukcji. Pojęcie to jest określane jako *odroczonewykonanie* i przedstawiono w poniższym przykładzie:  
  
 [!code-csharp[csLinqGettingStarted#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#4)]  
  
 Instrukcja `foreach` jest również, gdzie wyniki kwerendy są pobierane. Na przykład w poprzedniej kwerendzie zmienna `num` iteracji przechowuje każdą wartość (po jednym naraz) w zwróconej sekwencji.  
  
 Ponieważ zmienna kwerendy nigdy nie przechowuje wyników kwerendy, można ją wykonać tak często, jak chcesz. Na przykład może mieć bazy danych, która jest stale aktualizowana przez oddzielną aplikację. W aplikacji można utworzyć jedną kwerendę, która pobiera najnowsze dane i można go wykonywać wielokrotnie w pewnym przedziale czasu, aby pobrać różne wyniki za każdym razem.  
  
### <a name="forcing-immediate-execution"></a>Wymuszanie natychmiastowego wykonania  
 Kwerendy, które wykonują funkcje agregacji w zakresie elementów źródłowych należy najpierw iterate nad tymi elementami. Przykładami takich zapytań `Max` `Average`są `Count` `First`, , i . Te są wykonywane `foreach` bez jawnej instrukcji, ponieważ sama kwerenda musi używać `foreach` w celu zwrócenia wyniku. Należy również zauważyć, że te typy kwerend `IEnumerable` zwracają pojedynczą wartość, a nie kolekcję. Następująca kwerenda zwraca liczbę liczb parzystych w tablicy źródłowej:  
  
 [!code-csharp[csLinqGettingStarted#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#5)]  
  
 Aby wymusić natychmiastowe wykonanie dowolnego zapytania i pamięci <xref:System.Linq.Enumerable.ToList%2A> <xref:System.Linq.Enumerable.ToArray%2A> podręcznej jego wyniki, można wywołać lub metody.  
  
 [!code-csharp[csLinqGettingStarted#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#6)]  
  
 Można również wymusić wykonanie, umieszczając pętlę `foreach` natychmiast po wyrażeniu zapytania. Jednak przez `ToList` wywołanie lub `ToArray` również buforować wszystkie dane w obiekcie pojedynczej kolekcji.  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do korzystania z LINQ w C#](index.md)
- [Instruktaż: Pisanie zapytań w C #](./walkthrough-writing-queries-linq.md)
- [Language Integrated Query (LINQ)](../../../linq/index.md)
- [foreach, in](../../../language-reference/keywords/foreach-in.md)
- [Słowa kluczowe zapytania (LINQ)](../../../language-reference/keywords/query-keywords.md)
