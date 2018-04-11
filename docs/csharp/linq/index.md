---
title: Język zapytania zintegrowanym (LINQ)
description: Wprowadza języka zintegrowane zapytania (LINQ) w języku C#
keywords: .NET, .NET core, LINQ, C#
author: BillWagner
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 007cc736-f5cf-4919-b99b-0c00ab2814ce
ms.openlocfilehash: c4c26e2b7b0693ec940958a9b7d2d306001090e7
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="language-integrated-query-linq"></a>Język zapytania zintegrowanym (LINQ)

Zapytanie języku zintegrowanym (LINQ) jest nazwą zestawu technologii oparty na integracji możliwość wykonywania kwerend bezpośrednio w języku C#. Tradycyjnym zapytań dotyczących danych są wyrażane jako skompilować prostego parametry bez typu sprawdzania w czasie lub obsługę funkcji IntelliSense. Ponadto należy dowiedzieć się język kwerendy różne dla każdego typu źródła danych: SQL bazy danych, dokumentów XML, różnych usług sieci Web i tak dalej. Za pomocą LINQ zapytanie jest konstrukcję języka najwyższej jakości tak samo jak klasy, metody, zdarzenia.

Dla deweloperów, który zapisuje zapytania najbardziej widocznej części "języku zintegrowanym" LINQ jest wyrażenie zapytania. Wyrażenia zapytania są zapisywane w declarative *Składnia kwerendy*. Za pomocą składni zapytań, można wykonać filtrowania, kolejność i operacji grupowania na źródeł danych z co najmniej kodu. Te same wzory wyrażenia zapytania podstawowego służy do wykonywania zapytań i przekształcania danych bazy danych SQL, ADO .NET z zestawów danych, dokumentów XML i strumieni i kolekcji .NET.

Poniższy przykład przedstawia operację pełnej kwerendy. Ukończenia operacji obejmuje tworzenie źródła danych, definiujący wyrażenie zapytania i wykonywania zapytania w `foreach` instrukcji.

[!code-csharp[csProgGuideLINQ#11](../../../samples/snippets/csharp/concepts/linq/index_1.cs)]

## <a name="query-expression-overview"></a>Omówienie wyrażenia zapytania

-   Wyrażenia zapytań może służyć do badania i przekształcania danych z dowolnego źródła danych z obsługą LINQ. Na przykład pojedynczego zapytania można pobrać danych z bazy danych SQL i tworzy strumień XML jako dane wyjściowe.  
  
-   Wyrażenia zapytań są łatwe do głównego, ponieważ jest używany przez wiele znanych konstrukcji języka C#.  
  
-   Zmienne w wyrażeniu zapytania są wszystkie silnie typizowane, chociaż w wielu przypadkach trzeba jawnie Podaj typ ponieważ kompilator można go rozpoznać. Aby uzyskać więcej informacji, zobacz [relacje typu w składniku LINQ zapytania operacji](../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
-   Zapytanie nie jest wykonywane, dopóki iteracja zmienną zapytania, na przykład w `foreach` instrukcji. Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
-   W czasie kompilacji wyrażeń zapytania są konwertowane na wywołania metody standardowe — Operator zapytań zgodnie z regułami określonymi w specyfikacji języka C#. Wszelkie zapytania, które można wyrazić przy użyciu składni zapytania można wyrazić w taki sposób, przy użyciu składni metody. Jednak w większości przypadków składnia zapytania jest bardziej czytelny i zwięzłe. Aby uzyskać więcej informacji, zobacz [specyfikacji języka C#](../language-reference/language-specification/index.md) i [operatory standardowe zapytań — omówienie](../programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
-   Zgodnie z zasadą podczas pisania zapytań LINQ firma Microsoft zaleca użycie składni zapytania w miarę możliwości i metody zawsze, gdy jest to konieczne. Nie istnieje nie semantycznego lub różnicy wydajności między dwa sposoby. Wyrażenia zapytań są często bardziej czytelny niż równoważne wyrażenia napisany w składni metody.  
  
-   Zapytanie niektóre operacje, takie jak <xref:System.Linq.Enumerable.Count%2A> lub <xref:System.Linq.Enumerable.Max%2A>, nie generują braku klauzuli wyrażenia zapytania równoważne oraz w związku z tym muszą być wyrażone jako wywołania metody. Składnia metody można łączyć z składnia zapytania na różne sposoby. Aby uzyskać więcej informacji, zobacz [składnia zapytania i metody w technologii LINQ](../programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
-   Wyrażenia zapytania mogą być kompilowane na drzewa wyrażeń lub do delegatów, w zależności od typu dotyczy zapytanie. <xref:System.Collections.Generic.IEnumerable%601>zapytania są kompilowane do delegatów. <xref:System.Linq.IQueryable>i <xref:System.Linq.IQueryable%601> zapytania są kompilowane na drzewa wyrażeń. Aby uzyskać więcej informacji, zobacz [drzew wyrażeń](../expression-trees.md).  

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji na temat LINQ, Rozpocznij od staje się poznać niektóre podstawowe pojęcia związane z [podstawowe informacje o wyrażeniach zapytań](query-expression-basics.md), a następnie zapoznaj się z dokumentacją w technologii LINQ, w której jesteś zainteresowany:   
-   Dokumenty XML: [LINQ do XML](../programming-guide/concepts/linq/linq-to-xml.md)  
  
-   ADO.NET Entity Framework: [LINQ do jednostek](../../framework/data/adonet/ef/language-reference/linq-to-entities.md)  
  
-   Kolekcje .NET, plików, ciągi i tak dalej: [LINQ do obiektów](../programming-guide/concepts/linq/linq-to-objects.md)

Aby bardziej zrozumieć LINQ ogólnie rzecz biorąc, zobacz [LINQ w C#](linq-in-csharp.md).

Aby rozpocząć pracę z LINQ w C#, zobacz samouczek [pracy za pomocą LINQ](../tutorials/working-with-linq.md).


