---
title: Wyrażenia w zapytaniach składnika LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 234b3059f9109c23b8ecae4da37e15f7f094fbd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203239"
---
# <a name="expressions-in-linq-to-entities-queries"></a>Wyrażenia w zapytaniach składnika LINQ to Entities
Wyrażenie jest fragment kodu, które może przyjąć jedną wartość, obiektu, metody lub przestrzeni nazw. Wyrażenia może zawierać wartości literału, wywołanie metody, operatora i argumentów lub prostą nazwą. Proste nazwy mogą być nazwa zmiennej, składowej typu, parametru metody, przestrzeń nazw lub typu. Wyrażenia można używać operatorów, które z kolei inne wyrażenia używane jako parametry lub metoda wywołuje metodę, której parametry są z kolei inne wywołania metody. W związku z tym w bardzo złożone wyrażenia może wynosić od prostego.  
  
 W [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytań, wyrażenia mogą zawierać czymkolwiek dozwolonym przez typów w ramach <xref:System.Linq.Expressions> przestrzeń nazw, w tym wyrażenia lambda. Wyrażenia, które mogą być używane w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania są podzbiorem wyrażeń, które mogą być używane do wykonywania zapytań [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  Wyrażenia, które są dostępne w ramach zapytania względem [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] są ograniczone do operacji obsługiwanych przez `ObjectQuery<T>` i źródle danych.  
  
 W poniższym przykładzie porównanie w `Where` klauzuli to wyrażenie:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  Tworzy określonego języka, takiego jak C# `unchecked`, nie mają znaczenia [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wyrażenia stałe](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [Wyrażenia porównania](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Porównania wartości Null](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [Wyrażenia inicjowania](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Relacje, właściwości nawigacji i kluczy obcych](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a>Zobacz także

- [Program Entity Framework na platformie ADO.NET](../../../../../../docs/framework/data/adonet/ef/index.md)
