---
title: LINQ do Jednostek
ms.date: 03/30/2017
ms.assetid: 641f9b68-9046-47a1-abb0-1c8eaeda0e2d
ms.openlocfilehash: da9529da9b45fc8ac2fdf0b19d65634dd33450fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760717"
---
# <a name="linq-to-entities"></a>LINQ do Jednostek
Składnik LINQ to Entities zapewnia obsługę Language-Integrated Query (LINQ), która umożliwia programistom pisanie kwerend modelu koncepcyjnego Entity Framework przy użyciu języka Visual Basic lub Visual C#. Zapytania dotyczące programu Entity Framework są reprezentowane przez zapytania w drzewie poleceń, których wykonanie względem kontekst. Składnik LINQ to Entities konwertuje zapytań Language-Integrated zapytania (LINQ) z poleceniem Drzewo zapytań, wykonuje zapytania względem programu Entity Framework i zwraca obiekty używane przez Entity Framework i LINQ. Poniżej przedstawiono proces tworzenia i wykonywanie w zapytaniu składnika LINQ to Entities:  
  
1. Konstruowania <xref:System.Data.Objects.ObjectQuery%601> wystąpienia z <xref:System.Data.Objects.ObjectContext>.  
  
2. Za pomocą narzędzia Compose zapytaniu składnika LINQ to Entities w języku C# lub Visual Basic <xref:System.Data.Objects.ObjectQuery%601> wystąpienia.  
  
3. Konwertuj operatorów standardowej kwerendy LINQ i wyrażeń na drzew poleceń.  
  
4. Wykonanie kwerendy, w reprezentacji drzewa poleceń względem źródła danych. Wyjątki zgłaszane w źródle danych w czasie wykonywania są przekazywane bezpośrednio do klienta.  
  
5. Zwraca wyniki zapytania do klienta.  
  
## <a name="constructing-an-objectquery-instance"></a>Utworzenie wystąpienia obiektu ObjectQuery  
 <xref:System.Data.Objects.ObjectQuery%601> Klasa ogólna reprezentuje zapytanie, które zwraca kolekcję zero lub więcej z kontrolą typów jednostek. Zapytanie obiekt jest zwykle konstruowane na podstawie istniejącego kontekstu obiektu, zamiast ręcznie budowany i zawsze należy do tego obiektu kontekstu. Ten kontekst udostępnia połączenia i informacje o metadanych, który jest wymagany do tworzenia i wykonywanie zapytania. <xref:System.Data.Objects.ObjectQuery%601> Implementuje klasy ogólnej <xref:System.Linq.IQueryable%601> ogólny interfejs, w której metody konstruktora włączenia zapytań LINQ do zbudowania przyrostowo. Można także pozwolić kompilatorowi wydedukować typ. jednostek przy użyciu języka C# `var` — słowo kluczowe (`Dim` w Visual Basic, wnioskowanie o typie lokalnym włączona).  
  
## <a name="composing-the-queries"></a>Tworzenie zapytań  
 Wystąpienia elementu <xref:System.Data.Objects.ObjectQuery%601> klasy ogólnej, która implementuje ogólnego <xref:System.Linq.IQueryable%601> interfejsu, służyć jako źródło danych dla programu LINQ do zapytań jednostki. W zapytaniu określasz dokładnie informacje, które mają zostać pobrane ze źródła danych. Zapytania można również określić, jak te informacje powinny można sortowane, grupowane i kształtowane przed zwróceniem. W programie LINQ zapytania są przechowywane w zmiennej. Ta zmienna zapytania nie podejmuje żadnych działań i nie zwraca żadnych danych; tylko przechowuje informacje o kwerendzie. Po utworzeniu zapytania należy wykonać to zapytanie, aby pobrać wszystkie dane.  
  
 LINQ do zapytań jednostki może składać się w dwóch różnych składni: składnia wyrażenia oraz składni zapytania oparte na metodzie zapytania. Składnia wyrażenia zapytań i składni zapytania oparte na metodzie są nowością w programie C# 3.0 i Visual Basic 9.0.  
  
 Aby uzyskać więcej informacji, zobacz [zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md).  
  
## <a name="query-conversion"></a>Konwersja zapytania  
 Aby wykonać zapytaniu składnika LINQ to Entities względem programu Entity Framework, zapytanie LINQ muszą zostać skonwertowane do reprezentacji drzewa polecenia, które mogą być wykonywane względem programu Entity Framework.  
  
 LINQ do zapytań jednostek składają się z LINQ standardowych operatorów zapytań (takie jak <xref:System.Linq.Queryable.Select%2A>, <xref:System.Linq.Queryable.Where%2A>, i <xref:System.Linq.Queryable.GroupBy%2A>) i wyrażenia (x > 10 Contact.LastName i tak dalej). Operatory LINQ nie są zdefiniowane przez klasę, ale raczej są metody w klasie. W programie LINQ, wyrażenia mogą zawierać czymkolwiek dozwolonym przez typów w ramach <xref:System.Linq.Expressions> przestrzeni nazw i przez rozszerzenie, wszystkie elementy, które mogą być reprezentowane w funkcji lambda. Jest to nadzbiór wyrażeń, które są dozwolone przez program Entity Framework i które są zgodnie z definicją ograniczone do operacji dozwolony w bazie danych i obsługiwane przez <xref:System.Data.Objects.ObjectQuery%601>.  
  
 Platformy Entity Framework zarówno operatory i wyrażenia są reprezentowane przez jeden typ hierarchii, które następnie są umieszczane w drzewie poleceń. Drzewo poleceń jest używany przez program Entity Framework do wykonania zapytania. Jeśli zapytanie LINQ nie może być wyrażona jako drzewo poleceń, pojawi się wyjątek podczas konwersji zapytania. Konwersja LINQ do zapytań jednostki obejmuje dwa konwersje podrzędne: konwersji standardowych operatorów zapytań i konwersji wyrażenia.  
  
 Istnieje szereg LINQ standardowych operatorów zapytań, które nie mają prawidłowe tłumaczenia w składniku LINQ to Entities. Próbuje użyć tych operatorów, wynikiem będzie wyjątek podczas translacji zapytania. Aby uzyskać listę obsługiwanych LINQ do jednostek operatorów, zobacz [obsługiwane i nieobsługiwane LINQ metody (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md).  
  
 Aby uzyskać więcej informacji dotyczących używania standardowych operatorów zapytań w składniku LINQ to Entities, zobacz [standardowych operatorów zapytań w technologii LINQ do zapytań jednostki](../../../../../../docs/framework/data/adonet/ef/language-reference/standard-query-operators-in-linq-to-entities-queries.md).  
  
 Ogólnie rzecz biorąc wyrażenia w składniku LINQ to Entities są oceniane na serwerze, nie można się spodziewać zachowanie wyrażenia z semantyki CLR. Aby uzyskać więcej informacji, zobacz [wyrażenia w zapytaniach jednostek składnika LINQ to](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md).  
  
 Aby dowiedzieć się, jak sposób wywołania metody CLR są mapowane na funkcje canonical w źródle danych, zobacz [metody mapowania kanonicznej funkcji CLR](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
 Aby uzyskać informacji na temat jak wywoływać canonical, bazy danych i funkcji niestandardowych z poziomu [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytań, zobacz [podczas wywoływania funkcji w zapytaniach jednostek składnika LINQ to](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md).  
  
## <a name="query-execution"></a>Wykonywanie zapytania  
 Po utworzeniu zapytania LINQ przez użytkownika wartość jest konwertowana na reprezentację w postaci, która jest zgodna z platformy Entity Framework (w postaci drzew poleceń), który następnie jest wykonywane względem źródła danych. W czasie wykonywania zapytań wszystkie wyrażenia zapytań (lub zapytania) są obliczane na kliencie lub na serwerze. Wyrażenia, które są używane w tym w wyniku materializacja lub projekcji jednostki. Aby uzyskać więcej informacji, zobacz [wykonywania zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md). Aby uzyskać informacji na temat zwiększyć wydajność przez kompilowanie zapytania raz, a następnie wykonywanie go kilka razy z różnymi parametrami, zobacz [zapytania skompilowane (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).  
  
## <a name="materialization"></a>Materializacja  
 Materializacja polega na zwracaniu wyników zapytania do klienta jako typy CLR. W składniku LINQ to Entities nigdy nie zwracane są rekordy danych wyników zapytań; zawsze jest zapasowy typ CLR, zdefiniowane przez użytkownika lub przez program Entity Framework lub generowanych przez kompilator (typy anonimowe). Wszystkie materializacja obiektu odbywa się przez program Entity Framework. Wszelkie błędy, które wynikają z brakiem połączenia do mapowania miedzy Entity Framework i środowiska CLR spowoduje, że wyjątki zostanie wygenerowany podczas materializacja obiektu.  
  
 Wyniki zapytania są zwykle zwracane jako jeden z następujących czynności:  
  
- Kolekcja zero lub więcej obiektów typów jednostek lub projekcji złożonych typów zdefiniowanych w modelu koncepcyjnym.  
  
- Typy CLR, które są obsługiwane przez [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  
  
- Kolekcje wbudowane.  
  
- Typy anonimowe.  
  
 Aby uzyskać więcej informacji, zobacz [wyników zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-results.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
  
 [Wyrażenia w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)  
  
 [Wywoływanie funkcji w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
  
 [Zapytania skompilowane (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)  
  
 [Wykonywanie zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md)  
  
 [Wyniki zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-results.md)  
  
 [Standardowe operatory zapytań w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/standard-query-operators-in-linq-to-entities-queries.md)  
  
 [Metody mapowania kanonicznej funkcji CLR](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md)  
  
 [Metody obsługiwane i nieobsługiwane LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)  
  
 [Znane problemy i zagadnienia dotyczące w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)  
  
## <a name="see-also"></a>Zobacz także

- [Znane problemy i zagadnienia dotyczące w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
- [Zapytanie o języku zintegrowanym (LINQ) —C#](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Zapytanie o języku zintegrowanym (LINQ) - Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [LINQ i ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)
- [Program Entity Framework na platformie ADO.NET](../../../../../../docs/framework/data/adonet/ef/index.md)
