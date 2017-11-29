---
title: Operacje kwantyfikatora (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9bc48c69179b1f8876efaa465295e94a9a0e0fb6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="quantifier-operations-visual-basic"></a>Operacje kwantyfikatora (Visual Basic)
Operacje kwantyfikatora zwracać <xref:System.Boolean> wartość, która wskazuje, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.  
  
 Na poniższej ilustracji przedstawiono dwie operacje kwantyfikatora różnych na dwóch różnych źródeł sekwencji. Pierwszą operacją zapyta, jeśli co najmniej jeden z elementów jest znak "A", a wynik jest `true`. Druga operacja zapyta, czy wszystkie elementy są znaków "A", a wynik jest `true`.  
  
 ![Operacje kwantyfikatora LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")  
  
 Metody — operator standardowe zapytań, które wykonują operacje kwantyfikatora są wymienione w poniższej sekcji.  
  
## <a name="methods"></a>Metody  
  
|Nazwa metody|Opis|Składnia wyrażeń języka Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Wszystkie|Określa, czy wszystkie elementy w sekwencji spełniają warunek.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|wszystkie|Określa, czy wszystkie elementy w sekwencji spełniają warunek.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|Zawiera|Określa, czy sekwencja zawiera określony element.|Nie dotyczy.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Przykłady składni wyrażeń zapytania  
 Użyj tych przykładów `Aggregate` klauzuli w języku Visual Basic w ramach warunek filtrowania w zapytaniu składnika LINQ.  
  
 W poniższym przykładzie użyto `Aggregate` klauzuli i <xref:System.Linq.Enumerable.All%2A> — metoda rozszerzenia do zwrócenia z kolekcji osoby, których zwierząt domowych są wszystkie starsze niż określony okres ważności.  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 W następnym przykładzie użyto `Aggregate` klauzuli i <xref:System.Linq.Enumerable.Any%2A> — metoda rozszerzenia do zwrócenia z kolekcji tych osób, które mają co najmniej jeden domowe, która jest starsza niż określony okres ważności.  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq>  
 [Operatory standardowe zapytań — omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [AGGREGATE — klauzula](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Porady: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
