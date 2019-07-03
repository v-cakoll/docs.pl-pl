---
title: Wyrażenia w zapytaniach składnika LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 0b77fc4c2a7c7df6efc9f4d8ce4001c39250ab94
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539900"
---
# <a name="expressions-in-linq-to-entities-queries"></a>Wyrażenia w zapytaniach składnika LINQ to Entities
Wyrażenie jest fragment kodu, które może przyjąć jedną wartość, obiektu, metody lub przestrzeni nazw. Wyrażenia może zawierać wartości literału, wywołanie metody, operatora i argumentów lub prostą nazwą. Proste nazwy mogą być nazwa zmiennej, składowej typu, parametru metody, przestrzeń nazw lub typu. Wyrażenia można używać operatorów, które z kolei inne wyrażenia używane jako parametry lub metoda wywołuje metodę, której parametry są z kolei inne wywołania metody. W związku z tym w bardzo złożone wyrażenia może wynosić od prostego.  
  
 W zapytaniach składnika LINQ to Entities, wyrażeń może zawierać czymkolwiek dozwolonym przez typów w ramach <xref:System.Linq.Expressions> przestrzeń nazw, w tym wyrażenia lambda. Wyrażenia, które może służyć w składniku LINQ do zapytań jednostki są podzbiorem wyrażeń, które mogą być używane do wykonywania zapytań [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  Wyrażenia, które są dostępne w ramach zapytania względem [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] są ograniczone do operacji obsługiwanych przez `ObjectQuery<T>` i źródle danych.  
  
 W poniższym przykładzie porównanie w `Where` klauzuli to wyrażenie:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  Tworzy określonego języka, takich jak C# `unchecked`, nie mają znaczenia w składniku LINQ to Entities.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wyrażenia stałe](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [Porównywanie wyrażeń](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Porównania wartości Null](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [Wyrażenia inicjowania](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Relacje, właściwości nawigacji i kluczy obcych](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a>Zobacz także

- [Program Entity Framework na platformie ADO.NET](../../../../../../docs/framework/data/adonet/ef/index.md)
