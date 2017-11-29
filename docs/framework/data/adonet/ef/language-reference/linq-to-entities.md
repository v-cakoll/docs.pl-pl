---
title: LINQ do Jednostek
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 641f9b68-9046-47a1-abb0-1c8eaeda0e2d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 685651f4291a11b857da82a63068e4bd2333275c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-entities"></a>LINQ do Jednostek
Składnik LINQ to Entities zapewnia obsługę język Language-Integrated zapytania (LINQ), który umożliwia deweloperom Pisanie zapytań dotyczących programu Entity Framework modelu koncepcyjnego za pomocą języka Visual Basic lub Visual C#. Zapytań dotyczących programu Entity Framework są reprezentowane przez kwerendy drzewa polecenia, których wykonanie względem kontekstu obiektów. Składnik LINQ to Entities konwertuje zapytań język Language-Integrated zapytania (LINQ) do polecenia drzewa zapytań, wykonuje zapytania względem programu Entity Framework i zwraca obiekty, które mogą być używane przez programu Entity Framework i LINQ. Poniżej przedstawiono procedurę tworzenia i wykonywania zapytania składnika LINQ to Entities:  
  
1.  Utworzyć <xref:System.Data.Objects.ObjectQuery%601> wystąpienia z <xref:System.Data.Objects.ObjectContext>.  
  
2.  Utworzenie zapytania składnika LINQ to Entities w języku C# lub Visual Basic przy użyciu <xref:System.Data.Objects.ObjectQuery%601> wystąpienia.  
  
3.  Konwertuj LINQ standardowych operatorów zapytań i wyrażenia na drzew poleceń.  
  
4.  Wykonanie kwerendy, w reprezentacji drzewa polecenia w źródle danych. Wszelkie wyjątki zgłaszane w źródle danych podczas wykonywania są przekazywane bezpośrednio do klienta.  
  
5.  Zwraca wyniki zapytania do klienta.  
  
## <a name="constructing-an-objectquery-instance"></a>Utworzenie wystąpienia obiektu ObjectQuery  
 <xref:System.Data.Objects.ObjectQuery%601> Klasa ogólna reprezentuje kwerendę, która zwraca kolekcję zero lub więcej typizowanych jednostek. Zapytanie obiektu zazwyczaj jest tworzony z kontekstu istniejący obiekt zamiast ręcznie tworzona i zawsze należy do tego kontekstu obiektów. Ten kontekst udostępnia połączenie i informacji o metadanych, który jest wymagany do tworzenia i wykonać zapytanie. <xref:System.Data.Objects.ObjectQuery%601> Implementuje klasy ogólnej <xref:System.Linq.IQueryable%601> interfejs ogólny, której metody konstruktora włączyć zapytań LINQ ma zostać utworzony przyrostowo. Można także pozwolić kompilatora wnioskować o typie jednostek przy użyciu języka C# `var` — słowo kluczowe (`Dim` w języku Visual Basic wnioskowanie o typie lokalnym włączona).  
  
## <a name="composing-the-queries"></a>Tworzenie zapytań  
 Wystąpienia <xref:System.Data.Objects.ObjectQuery%601> klasy generycznej, która implementuje ogólnego <xref:System.Linq.IQueryable%601> interfejsu, służyć jako źródło danych dla technologii LINQ do jednostek zapytań. W zapytaniu możesz określić dokładnie informacje, które mają zostać pobrane ze źródła danych. Zapytania można również określić, jak te informacje sortowania, grupowane i w kształcie przed zwróceniem jest. W składniku LINQ zapytanie jest przechowywana w zmiennej. Ta zmienna zapytania Brak działania i zwraca żadnych danych; tylko przechowuje informacje o kwerendzie. Po utworzeniu zapytania należy wykonać zapytania można pobrać żadnych danych.  
  
 LINQ do jednostek zapytania mogą być składane w dwóch składnie: wyrażenie składnia zapytania i metody zapytań. Składnia wyrażeń i składnia zapytania oparte na metodzie są nowością w programie 3.0 C# i Visual Basic 9.0.  
  
 Aby uzyskać więcej informacji, zobacz [zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md).  
  
## <a name="query-conversion"></a>Konwersja zapytania  
 Do wykonania zapytania składnika LINQ to Entities względem programu Entity Framework, zapytania LINQ muszą zostać skonwertowane do reprezentacji drzewa polecenia, które mogą być wykonywane względem programu Entity Framework.  
  
 LINQ do jednostek zapytań składają się z LINQ standardowych operatorów zapytań (takich jak <xref:System.Linq.Queryable.Select%2A>, <xref:System.Linq.Queryable.Where%2A>, i <xref:System.Linq.Queryable.GroupBy%2A>) i wyrażenia (x > 10, Contact.LastName i tak dalej). Operatory LINQ nie są zdefiniowane przez klasę, ale raczej są metody klasy. W składniku LINQ, wyrażenia może zawierać żadnych dozwolone przez typy w <xref:System.Linq.Expressions> przestrzeni nazw i przez rozszerzenie, wszystko, co może być reprezentowany w funkcji lambda. To jest nadzbiorem wyrażeń, które są dozwolone przez program Entity Framework, które zgodnie z definicją ograniczone do operacji dozwolony w bazie danych i obsługiwane przez <xref:System.Data.Objects.ObjectQuery%601>.  
  
 W ramach jednostki zarówno operatory i wyrażenia są reprezentowane przez jeden typ hierarchii, które następnie są umieszczane w drzewie poleceń. Drzewo poleceń jest używany przez program Entity Framework do wykonania zapytania. Jeśli nie można wyrazić zapytania LINQ jako drzewo polecenia, zostanie wygenerowany wyjątek podczas konwersji zapytania. Konwersja LINQ do jednostek zapytań obejmuje dwa konwersje podrzędne: konwersja standardowych operatorów zapytań i konwersji wyrażenia.  
  
 Istnieje wiele operatorów standardowej kwerendy LINQ, które nie mają prawidłowy tłumaczenia w składniku LINQ to Entities. Wystąpił wyjątek podczas translacji zapytania spowoduje próbuje użyć tych operatorów. Aby uzyskać listę obsługiwanych składnika LINQ to Entities operatorów, zobacz [obsługiwane i nieobsługiwane metody LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md).  
  
 Aby uzyskać więcej informacji dotyczących używania standardowych operatorów zapytań w składniku LINQ to Entities, zobacz [standardowych operatorów zapytań w składniku LINQ to Entities zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/standard-query-operators-in-linq-to-entities-queries.md).  
  
 Ogólnie rzecz biorąc wyrażenia w składniku LINQ to Entities są oceniane na serwerze, więc nie można się spodziewać zachowanie wyrażenia do wykonania semantykę środowiska CLR. Aby uzyskać więcej informacji, zobacz [wyrażenia w składniku LINQ to Entities zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md).  
  
 Aby uzyskać informacje o sposobie mapowania wywołania metody CLR kanonicznej funkcji w źródle danych, zobacz [metodę CLR mapowania funkcji kanonicznej](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
 Informacje o jak wywołać canonical, bazy danych i funkcji niestandardowych za pomocą [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytań, zobacz [podczas wywoływania funkcji w składniku LINQ to Entities zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md).  
  
## <a name="query-execution"></a>Wykonywanie zapytania  
 Po utworzeniu zapytania LINQ przez użytkownika jest konwertowany na reprezentację za pomocą zgodnego z programu Entity Framework (w formie drzewa polecenia), który jest następnie wykonywane względem źródła danych. Podczas wykonywania zapytania wszystkie wyrażenia zapytań (lub części zapytania) są oceniane na kliencie lub na serwerze. Dotyczy to również wyrażeń, które są używane w wyniku materialization lub projekcje jednostki. Aby uzyskać więcej informacji, zobacz [wykonywania zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md). Aby uzyskać informacje na temat sposobów usprawnienia wydajności raz kompilowania zapytania, a następnie jej wykonanie kilka razy o innych parametrach, zobacz [skompilowane zapytania (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).  
  
## <a name="materialization"></a>Materialization  
 Materialization jest proces zwracania wyników zapytania do klienta jako typów CLR. W składniku LINQ to Entities nigdy nie są zwracane rekordów danych wyników zapytania; zawsze jest zapasowy typ CLR, zdefiniowane przez użytkownika lub przez program Entity Framework lub generowane przez kompilator (typy anonimowe). Wszystkie materialization obiektu jest wykonywane przez program Entity Framework. Wyjątki, aby zostać wygenerowany podczas materialization obiektu spowoduje, że błędów spowodowanych brakiem mapowania programu Entity Framework i środowiska CLR.  
  
 Wyniki zapytania są zazwyczaj zwracane jako jedną z następujących czynności:  
  
-   Kolekcja zero lub więcej obiektów typów jednostek lub dla projekcji złożonych typów zdefiniowanych w modelu koncepcyjnym.  
  
-   Typy CLR, które są obsługiwane przez [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  
  
-   Kolekcje wbudowane.  
  
-   Typy anonimowe.  
  
 Aby uzyskać więcej informacji, zobacz [wyników zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-results.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
  
 [Wyrażenia w składniku LINQ to Entities zapytań](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)  
  
 [Wywoływanie funkcji w składniku LINQ to Entities zapytań](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
  
 [Skompilowane zapytania (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)  
  
 [Wykonywanie zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md)  
  
 [Wyniki zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/query-results.md)  
  
 [Standardowe operatory zapytań w składniku LINQ to Entities zapytań](../../../../../../docs/framework/data/adonet/ef/language-reference/standard-query-operators-in-linq-to-entities-queries.md)  
  
 [Metody mapowania kanonicznej funkcji CLR](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md)  
  
 [Metody obsługiwane i nieobsługiwane LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)  
  
 [Znane problemy i zagadnienia dotyczące w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Znane problemy i zagadnienia dotyczące w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)  
 [LINQ (zapytania o języku zintegrowanym)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [LINQ i ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
