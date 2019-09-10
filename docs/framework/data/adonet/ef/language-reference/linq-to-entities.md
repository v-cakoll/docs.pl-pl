---
title: LINQ do Jednostek
ms.date: 03/30/2017
ms.assetid: 641f9b68-9046-47a1-abb0-1c8eaeda0e2d
ms.openlocfilehash: bc568cb9dff170062651c908471a36cd17eac980
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854369"
---
# <a name="linq-to-entities"></a>LINQ do Jednostek
LINQ to Entities zapewnia obsługę programu Query-Integrated Language (LINQ), która umożliwia deweloperom Pisanie zapytań względem modelu koncepcyjnego Entity Framework przy użyciu C#Visual Basic lub wizualizacji. Zapytania dotyczące Entity Framework są reprezentowane przez zapytania drzewa poleceń, które są wykonywane względem kontekstu obiektu. LINQ to Entities konwertuje zapytania dotyczące języka (LINQ) na zapytania drzewa poleceń, wykonuje zapytania względem Entity Framework i zwraca obiekty, które mogą być używane przez Entity Framework i LINQ. Poniżej przedstawiono proces tworzenia i wykonywania zapytania LINQ to Entities:  
  
1. Utwórz wystąpienie z <xref:System.Data.Objects.ObjectContext>. <xref:System.Data.Objects.ObjectQuery%601>  
  
2. Utwórz zapytanie LINQ to Entities w C# lub Visual Basic za pomocą <xref:System.Data.Objects.ObjectQuery%601> wystąpienia.  
  
3. Konwertuj standardowe operatory zapytań LINQ i wyrażenia na drzewa poleceń.  
  
4. Wykonaj zapytanie w obszarze Reprezentacja drzewa poleceń względem źródła danych. Wszystkie wyjątki zgłoszone w źródle danych podczas wykonywania są przesyłane bezpośrednio do klienta.  
  
5. Zwraca wyniki zapytania z powrotem do klienta.  
  
## <a name="constructing-an-objectquery-instance"></a>Konstruowanie wystąpienia ObjectQuery  
 Klasa <xref:System.Data.Objects.ObjectQuery%601> generyczna reprezentuje zapytanie, które zwraca kolekcję składającą się z zero lub więcej z wpisanych jednostek. Zapytanie obiektu jest zwykle konstruowane z istniejącego kontekstu obiektu, a nie do ręcznego konstruowania i zawsze należy do tego kontekstu obiektu. Ten kontekst zapewnia informacje o połączeniu i metadanych, które są wymagane do tworzenia i wykonywania zapytania. Klasa generyczna implementuje interfejs ogólny, którego metody konstruktora umożliwiają przyrostowe kompilowanie zapytań LINQ. <xref:System.Linq.IQueryable%601> <xref:System.Data.Objects.ObjectQuery%601> Można również zezwolić kompilatorowi na wnioskowanie typu jednostek za pomocą C# `var` słowa kluczowego (`Dim` w Visual Basic z włączonym wnioskem o typie lokalnym).  
  
## <a name="composing-the-queries"></a>Redagowanie zapytań  
 Wystąpienia klasy <xref:System.Linq.IQueryable%601> generycznej implementującej interfejs ogólny, służące jako źródło danych dla zapytań LINQ to Entities. <xref:System.Data.Objects.ObjectQuery%601> W zapytaniu należy określić dokładnie informacje, które mają zostać pobrane ze źródła danych. Zapytanie może również określać, jak te informacje powinny być sortowane, grupowane i ukształtowane przed zwróceniem. W LINQ, zapytanie jest przechowywane w zmiennej. Ta zmienna zapytania nie przyjmuje żadnej akcji i nie zwraca żadnych danych. przechowuje on tylko informacje o zapytaniu. Po utworzeniu zapytania należy wykonać to zapytanie w celu pobrania danych.  
  
 Zapytania LINQ to Entities mogą składać się z dwóch różnych składni: składni wyrażeń zapytania i składni zapytania opartego na metodzie. Składnia wyrażenia zapytania i Składnia zapytania oparta na metodzie są nowe C# w 3,0 i Visual Basic 9,0.  
  
 Aby uzyskać więcej informacji, zobacz [zapytania w LINQ to Entities](queries-in-linq-to-entities.md).  
  
## <a name="query-conversion"></a>Konwersja zapytań  
 Aby wykonać kwerendę LINQ to Entitiesową względem Entity Framework, zapytanie LINQ musi zostać przekonwertowane na reprezentację drzewa poleceń, które można wykonać w odniesieniu do Entity Framework.  
  
 Zapytania LINQ to Entities składają się z standardowych operatorów zapytań LINQ (takich jak <xref:System.Linq.Queryable.Select%2A>, <xref:System.Linq.Queryable.Where%2A>i <xref:System.Linq.Queryable.GroupBy%2A>) i wyrażeń (x > 10, Contact. LastName itd.). Operatory LINQ nie są zdefiniowane przez klasę, ale raczej są metodami klasy. W LINQ, wyrażenia mogą zawierać dowolne elementy dozwolone przez typy w <xref:System.Linq.Expressions> przestrzeni nazw i, przez rozszerzenie, wszystkie elementy, które mogą być reprezentowane w funkcji lambda. Jest to nadzbiór wyrażeń dozwolonych przez Entity Framework, które są przez definicję ograniczone do operacji dozwolonych w bazie danych i obsługiwanych przez <xref:System.Data.Objects.ObjectQuery%601>.  
  
 W Entity Framework operatory i wyrażenia są reprezentowane przez pojedynczą hierarchię typów, która następnie jest umieszczana w drzewie poleceń. Drzewo poleceń jest używane przez Entity Framework do wykonania zapytania. Jeśli zapytanie LINQ nie może być wyrażone jako drzewo poleceń, zostanie zgłoszony wyjątek, gdy zapytanie jest konwertowane. Konwersja zapytań LINQ to Entities obejmuje dwie podkonwersje: konwersję standardowych operatorów zapytań i konwersję wyrażeń.  
  
 Istnieje szereg standardowych operatorów zapytań LINQ, które nie mają prawidłowego tłumaczenia w LINQ to Entities. Próby użycia tych operatorów spowodują wyjątek w czasie translacji zapytań. Listę obsługiwanych operatorów LINQ to Entities można znaleźć w temacie [obsługiwane i nieobsługiwane metody LINQ (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md).  
  
 Aby uzyskać więcej informacji na temat używania standardowych operatorów zapytań w LINQ to Entities, zobacz [standardowe operatory zapytań w LINQ to Entities zapytaniach](standard-query-operators-in-linq-to-entities-queries.md).  
  
 Ogólnie rzecz biorąc, wyrażenia w LINQ to Entities są oceniane na serwerze, dlatego zachowanie wyrażenia nie powinno być oczekiwane przy użyciu semantyki CLR. Aby uzyskać więcej informacji, zobacz [wyrażenia w LINQ to Entities zapytaniach](expressions-in-linq-to-entities-queries.md).  
  
 Aby uzyskać informacje dotyczące sposobu, w jaki wywołania metod CLR są mapowane na funkcje kanoniczne w źródle danych, zobacz [Mapowanie funkcji CLR na kanoniczne](clr-method-to-canonical-function-mapping.md).  
  
 Aby uzyskać informacje o sposobie wywoływania funkcji kanonicznych, baz danych i niestandardowych w ramach zapytań LINQ to Entities, zobacz [wywoływanie funkcji w LINQ to Entities zapytaniach](calling-functions-in-linq-to-entities-queries.md).  
  
## <a name="query-execution"></a>Wykonywanie zapytania  
 Po utworzeniu zapytania LINQ przez użytkownika zostanie ono przekonwertowane na reprezentację zgodną z Entity Framework (w formie drzew poleceń), która jest następnie wykonywana względem źródła danych. W czasie wykonywania zapytania wszystkie wyrażenia zapytania (lub składniki zapytania) są oceniane na kliencie lub na serwerze. Obejmuje to wyrażenia, które są używane w wyniku materializację lub projekcji jednostek. Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań](query-execution.md). Aby uzyskać informacje na temat zwiększania wydajności przez skompilowanie zapytania raz, a następnie wykonywanie go kilka razy przy użyciu różnych parametrów, zobacz [skompilowane zapytania (LINQ to Entities)](compiled-queries-linq-to-entities.md).  
  
## <a name="materialization"></a>Materializację  
 Materializację to proces zwracania wyników zapytania z powrotem do klienta jako typy CLR. W LINQ to Entities rekordy danych wyników zapytania nigdy nie są zwracane; istnieje zawsze zapasowy typ CLR zdefiniowany przez użytkownika lub przez Entity Framework lub wygenerowany przez kompilator (typy anonimowe). Wszystkie materializację obiektów są wykonywane przez Entity Framework. Wszelkie błędy, które wynikają z braku możliwości mapowania między Entity Framework i CLR spowodują, że wyjątki będą zgłaszane podczas materializację obiektów.  
  
 Wyniki zapytania są zwykle zwracane jako jeden z następujących elementów:  
  
- Kolekcja obiektów jednostek typu "zero" lub "rzutowanie typów złożonych" zdefiniowanych w modelu koncepcyjnym.  
  
- Typy CLR obsługiwane przez Entity Framework.  
  
- Kolekcje wbudowane.  
  
- Typy anonimowe.  
  
 Aby uzyskać więcej informacji, zobacz [wyniki zapytania](query-results.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zapytania w składniku LINQ to Entities](queries-in-linq-to-entities.md)  
  
 [Wyrażenia w zapytaniach składnika LINQ to Entities](expressions-in-linq-to-entities-queries.md)  
  
 [Wywoływanie funkcji w zapytaniach składnika LINQ to Entities](calling-functions-in-linq-to-entities-queries.md)  
  
 [Zapytania skompilowane (LINQ to Entities)](compiled-queries-linq-to-entities.md)  
  
 [Wykonywanie zapytania](query-execution.md)  
  
 [Wyniki zapytania](query-results.md)  
  
 [Standardowe operatory zapytań w zapytaniach składnika LINQ to Entities](standard-query-operators-in-linq-to-entities-queries.md)  
  
 [Metody mapowania kanonicznej funkcji CLR](clr-method-to-canonical-function-mapping.md)  
  
 [Metody obsługiwane i nieobsługiwane LINQ (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md)  
  
 [Znane problemy i zagadnienia dotyczące w składniku LINQ to Entities](known-issues-and-considerations-in-linq-to-entities.md)  
  
## <a name="see-also"></a>Zobacz także

- [Znane problemy i zagadnienia dotyczące w składniku LINQ to Entities](known-issues-and-considerations-in-linq-to-entities.md)
- [Language-Integrated Query (LINQ) —C#](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Zapytanie zintegrowane z językiem (LINQ) — Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ i ADO.NET](../../linq-and-ado-net.md)
- [Program Entity Framework na platformie ADO.NET](../index.md)
