---
title: Wprowadzenie do kwerend LINQ (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- deferred execution [LINQ]
- LINQ, queries
- LINQ, deferred execution
- queries [LINQ], about LINQ queries
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
caps.latest.revision: "47"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae7a2d03859e95d939ff4c62fa33e07917a873a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-linq-queries-c"></a>Wprowadzenie do kwerend LINQ (C#)
A *zapytania* jest wyrażenie, które pobiera dane ze źródła danych. Zapytania są zwykle zapisywane w język kwerendy specjalne. Wraz z upływem czasu dla różnych typów źródeł danych, na przykład SQL relacyjnych baz danych i XQuery XML zostały opracowane w różnych językach. W związku z tym deweloperzy było nauczyć się nowy język kwerendy dla każdego typu źródła danych lub format danych, które muszą obsługiwać. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]upraszcza tej sytuacji, oferując spójny model do pracy z danymi w różnych rodzajów źródeł danych i formaty. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania, zawsze korzystasz z obiektów. Użyj tego samego podstawowe wzorców kodowania w celu wykonywania zapytań i przekształcania danych w dokumentach XML, baz danych, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] zestawów danych, kolekcji .NET i innym formacie, dla którego [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawca jest niedostępny.  
  
## <a name="three-parts-of-a-query-operation"></a>Trzy części operacji zapytania  
 Wszystkie [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania operacje składa się z trzy różne akcje:  
  
1.  Uzyskaj źródła danych.  
  
2.  Utwórz zapytanie.  
  
3.  Wykonanie kwerendy.  
  
 W poniższym przykładzie pokazano, jak te trzy części operacji zapytania są wyrażane w kodzie źródłowym. W przykładzie użyto tablicę całkowitych jako źródło danych dla wygody; Jednak te same pojęcia dotyczą innych źródeł danych również. W tym przykładzie jest określana w dalszej części tego tematu.  
  
 [!code-csharp[CsLINQGettingStarted#1](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_1.cs)]  
  
 Na poniższej ilustracji przedstawiono operację pełnej kwerendy. W [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wykonywania zapytania zawiera tylko unikatowe wiersze z samą kwerendę; innymi słowy nie pobrano wszystkie dane tak, tworząc zmienną zapytania.  
  
 ![Ukończenie operacji zapytania LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_query.png "LINQ_Query")  
  
## <a name="the-data-source"></a>Źródło danych  
 W poprzednim przykładzie, ponieważ źródło danych jest tablicą, niejawnie obsługuje ogólnego <xref:System.Collections.Generic.IEnumerable%601> interfejsu. Oznacza ten fakt może być badana z [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Zapytanie jest wykonywane w `foreach` instrukcji i `foreach` wymaga <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>. Typy obsługujące <xref:System.Collections.Generic.IEnumerable%601> lub interfejsu pochodnego, takich jak ogólnego <xref:System.Linq.IQueryable%601> są nazywane *typy zapytań*.  
  
 Kolejność typu nie musi podawać modyfikacji i szczególnego traktowania jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródła danych. Jeśli źródło danych nie jest już w pamięci jako typu kolejność [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] musi być on reprezentować jako takie w dostawcy. Na przykład [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ładowania dokumentu XML na kolejność <xref:System.Xml.Linq.XElement> typu:  
  
 [!code-csharp[CsLINQGettingStarted#2](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_2.cs)]  
  
 Z [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], należy najpierw utworzyć obiektów relacyjnych mapowanie w czasie projektowania ręcznie lub za pomocą [składnika LINQ to SQL narzędzia w programie Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) w programie Visual Studio. Pisanie zapytań względem obiektów oraz w czasie wykonywania [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] obsługuje komunikację z bazą danych. W poniższym przykładzie `Customers` reprezentuje określonej tabeli w bazie danych i typ wyniku kwerendy <xref:System.Linq.IQueryable%601>, pochodzi z <xref:System.Collections.Generic.IEnumerable%601>.  
  
```csharp  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
```  
  
 Aby uzyskać więcej informacji o sposobie tworzenia określonych typów źródeł danych, zobacz dokumentację dla różnych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dostawców. Jednak podstawowe reguły jest bardzo prosta: [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródło danych jest dowolny obiekt, który obsługuje ogólnego <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub interfejsu, który dziedziczy z niego.  
  
> [!NOTE]
>  Typy, takich jak <xref:System.Collections.ArrayList> inny niż ogólny, który obsługuje <xref:System.Collections.IEnumerable> interfejs może również służyć jako [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] źródła danych. Aby uzyskać więcej informacji, zobacz [porady: zapytanie w ArrayList za pomocą LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).  
  
##  <a name="query"></a>Zapytanie  
 Zapytanie określa informacjach zostać pobrane ze źródła danych lub źródła. Opcjonalnie zapytania również określa, jak te informacje sortowania, grupowane i w kształcie przed zwróceniem jest. Zapytanie jest przechowywana w zmiennej zapytania i zainicjować przy użyciu wyrażenia zapytania. Aby ułatwić pisać zapytania, C# wprowadziła nowej składni zapytań.  
  
 W poprzednim przykładzie zwraca wszystkie liczby parzyste z tablicy liczby całkowitej. Wyrażenia zapytania zawiera trzy klauzule: `from`, `where` i `select`. (Jeśli znasz SQL, można będzie zauważyć czy kolejność klauzule jest wycofywane z kolejnością SQL.) `from` Klauzuli Określa źródło danych, `where` klauzuli stosuje filtr oraz `select` klauzuli Określa typ zwrócony elementów. Te i inne klauzule zapytań omówiono szczegółowo w [wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md) sekcji. Na razie istotne jest to, że w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], samej zmiennej zapytanie Brak działania i zwraca żadnych danych. Po prostu przechowuje informacje, które są wymagane w celu uzyskania wyników podczas wykonywania zapytania w pewnym momencie nowsze. Aby uzyskać więcej informacji dotyczących sposobu zapytania są skonstruowane w tle, zobacz [standardowe operatory zapytań — omówienie (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
> [!NOTE]
>  Zapytania można wyrazić w taki sposób, przy użyciu składni metody. Aby uzyskać więcej informacji, zobacz [składnia zapytania a składnia metody w technologii LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="query-execution"></a>Wykonywanie zapytania  
  
### <a name="deferred-execution"></a>Wykonanie odroczone  
 Jak wspomniano wcześniej, samej zmiennej zapytania są przechowywane w poleceniach zapytań. Rzeczywiste wykonanie zapytania została odroczona dopóki iteracja zmienną zapytania w `foreach` instrukcji. To pojęcie jest określany jako *odroczonego wykonania* i przedstawiono w poniższym przykładzie:  
  
 [!code-csharp[csLinqGettingStarted#4](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_3.cs)]  
  
 `foreach` Instrukcja jest również którego pobierane są wyniki zapytania. Na przykład w poprzednie zapytanie zmiennej iteracji `num` zawiera wartości (po jednym naraz) zwrócone sekwencji.  
  
 Ponieważ samej zmiennej zapytanie nigdy nie przechowuje wyniki zapytania, można ją wykonać tak często, według uznania. Na przykład masz bazy danych, która jest aktualizowana stale w innej aplikacji. W aplikacji można utworzyć jedną kwerendę, która pobiera najnowsze dane, można wykonać w wielokrotnie w pewnego interwału do pobrania różne wyniki, co czasu.  
  
### <a name="forcing-immediate-execution"></a>Wymuszanie natychmiastowego wykonania  
 Zapytania, które funkcji agregacji w zakresie elementy źródłowe musi najpierw przejść przez te elementy. Przykłady takich kwerend `Count`, `Max`, `Average`, i `First`. Te zostanie wykonane bez jawnego `foreach` instrukcji samej kwerendzie musi korzystać `foreach` aby zwrócony wynik. Należy też zauważyć, tego rodzaju zapytania nie zwracać pojedynczą wartość, `IEnumerable` kolekcji. Następujące zapytanie zwraca liczbę liczby parzyste w tablicy źródłowej:  
  
 [!code-csharp[csLinqGettingStarted#5](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_4.cs)]  
  
 Aby wymusić natychmiastowe wykonanie żadnych zapytania i pamięci podręcznej wyniki, należy wywołać <xref:System.Linq.Enumerable.ToList%2A> lub <xref:System.Linq.Enumerable.ToArray%2A> metody.  
  
 [!code-csharp[csLinqGettingStarted#6](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_5.cs)]  
  
 Możesz też wymusić wykonanie przez umieszczenie `foreach` pętli natychmiast po wyrażeniu zapytania. Jednakże, wywołując `ToList` lub `ToArray` również pamięci podręcznej wszystkie dane w obiekcie jednej kolekcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do korzystania z LINQ w C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Wskazówki: Pisanie zapytań w języku C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [Wskazówki: Pisanie zapytań w języku C#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [Wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Instrukcja foreach w](../../../../csharp/language-reference/keywords/foreach-in.md)  
 [Słowa kluczowe zapytania (LINQ)](../../../../csharp/language-reference/keywords/query-keywords.md)
