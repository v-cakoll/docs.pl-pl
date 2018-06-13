---
title: Wyrażenia w składniku LINQ to Entities zapytań
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: f9230e9b5ac0c906652c03111b82df5147267143
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760768"
---
# <a name="expressions-in-linq-to-entities-queries"></a>Wyrażenia w składniku LINQ to Entities zapytań
Wyrażenie jest fragment kodu, które może przyjąć pojedynczą wartość, obiekt, metodę lub przestrzeń nazw. Wyrażenia może zawierać wartość literału, wywołanie metody, operator i argumentów lub prostą nazwą. Proste nazwy mogą być nazwę zmiennej, członka typu, parametru metody, przestrzeni nazw lub typu. Wyrażenia można używać operatorów, które z kolei inne wyrażenia używane jako parametry lub wywołania metody, której parametry są z kolei inne wywołania metody. W związku z tym wyrażenia mogą należeć do zakresu od prostego do bardzo złożonych.  
  
 W [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytań, wyrażenia mogą zawierać dowolne elementy dozwolone przez typy w <xref:System.Linq.Expressions> przestrzeni nazw, w tym wyrażenia lambda. Wyrażeń, które mogą być używane w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania są podzbiorem wyrażeń, które mogą być używane w zapytaniu [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  Wyrażeń, które są częścią zapytania względem [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] są ograniczone do operacji obsługiwanych przez `ObjectQuery<T>` i źródła danych.  
  
 W poniższym przykładzie porównania w `Where` klauzula jest wyrażenie:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  Tworzy określonego języka, takich jak C# `unchecked`, mają znaczenia w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wyrażenia stałe](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [Porównywanie wyrażeń](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Porównania wartości Null](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [Wyrażenia inicjowania](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Właściwości nawigacji](http://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## <a name="see-also"></a>Zobacz też  
 [Program Entity Framework na platformie ADO.NET](../../../../../../docs/framework/data/adonet/ef/index.md)
