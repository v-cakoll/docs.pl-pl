---
title: Wyrażenia w zapytaniach składnika LINQ to Entities
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: e625ac3968542c65e737093c0ac292de4c2ffa37
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854460"
---
# <a name="expressions-in-linq-to-entities-queries"></a>Wyrażenia w zapytaniach składnika LINQ to Entities
Wyrażenie to fragment kodu, który może zostać oceniony jako pojedyncza wartość, obiekt, metoda lub przestrzeń nazw. Wyrażenia mogą zawierać wartość literału, wywołanie metody, operator i jego operandy albo prostą nazwę. Proste nazwy mogą być nazwą zmiennej, składową, parametrem metody, przestrzenią nazw lub typem. Wyrażenia mogą używać operatorów, które z kolei używają innych wyrażeń jako parametrów lub wywołania metody, których parametry są z kolei inne wywołania metody. W związku z tym wyrażenia mogą być różne od prostych do bardzo złożonych.  
  
 W zapytaniach LINQ to Entities wyrażenia mogą zawierać dowolne elementy dozwolone przez typy w <xref:System.Linq.Expressions> przestrzeni nazw, w tym wyrażenia lambda. Wyrażenia, które mogą być używane w zapytaniach LINQ to Entities są nadzbiorem wyrażeń, których można użyć do wykonywania zapytań dotyczących Entity Framework. wyrażenia, które są częścią zapytań względem Entity Framework są ograniczone do operacji `ObjectQuery<T>` obsługiwanych przez i bazowe źródło danych.  
  
 W poniższym przykładzie porównanie w `Where` klauzuli jest wyrażeniem:  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> Określone konstrukcje języka, takie jak C# `unchecked`, nie mają znaczenia w LINQ to Entities.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wyrażenia stałe](constant-expressions.md)  
  
 [Porównywanie wyrażeń](comparison-expressions.md)  
  
 [Porównania wartości Null](null-comparisons.md)  
  
 [Wyrażenia inicjowania](initialization-expressions.md)  
  
 [Relacje, właściwości nawigacji i klucze obce](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a>Zobacz także

- [Program Entity Framework na platformie ADO.NET](../index.md)
