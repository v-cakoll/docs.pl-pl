---
title: Wyrażenia w zapytaniach składnika LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: 383339241194c56d0c3178f538f2ac08b2f1b437
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950390"
---
# <a name="expressions-in-linq-to-entities-queries"></a>Wyrażenia w zapytaniach składnika LINQ to Entities
Wyrażenie to fragment kodu, który może zostać oceniony jako pojedyncza wartość, obiekt, metoda lub przestrzeń nazw. Wyrażenia mogą zawierać wartość literału, wywołanie metody, operator i jego operandy albo prostą nazwę. Proste nazwy mogą być nazwą zmiennej, składową, parametrem metody, przestrzenią nazw lub typem. Wyrażenia mogą używać operatorów, które z kolei używają innych wyrażeń jako parametrów lub wywołania metody, których parametry są z kolei inne wywołania metody. W związku z tym wyrażenia mogą być różne od prostych do bardzo złożonych.  
  
 W zapytaniach LINQ to Entities wyrażenia mogą zawierać dowolne elementy dozwolone przez typy w <xref:System.Linq.Expressions> przestrzeni nazw, w tym wyrażenia lambda. Wyrażenia, które mogą być używane w zapytaniach LINQ to Entities są nadzbiorem wyrażeń, których można użyć do wykonywania [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]zapytań względem.  Wyrażenia, które są częścią zapytań, [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] są ograniczone do operacji obsługiwanych przez `ObjectQuery<T>` i bazowe źródło danych.  
  
 W poniższym przykładzie porównanie w `Where` klauzuli jest wyrażeniem:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> Określone konstrukcje języka, takie jak C# `unchecked`, nie mają znaczenia w LINQ to Entities.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wyrażenia stałe](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [Porównywanie wyrażeń](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Porównania wartości Null](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [Wyrażenia inicjowania](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Relacje, właściwości nawigacji i klucze obce](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a>Zobacz także

- [Program Entity Framework na platformie ADO.NET](../../../../../../docs/framework/data/adonet/ef/index.md)
