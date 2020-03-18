---
title: Pełnomocnicy z nazwanymi i anonimowymi metodami — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 1ec366999ca6457471b705fa83f06fcde4293f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712380"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a>Delegaty z metodami nazwanymi lub anonimowymi (Przewodnik programowania w języku C#)
[Pełnomocnik](../../language-reference/builtin-types/reference-types.md) a może być skojarzony z nazwanego metody. Podczas tworzenia wystąpienia delegata przy użyciu metody nazwane, metoda jest przekazywana jako parametr, na przykład:  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 Jest to wywoływane przy użyciu metody o nazwie. Delegaci skonstruowane z nazwanego metody może hermetyzować metodę [statyczną](../../language-reference/keywords/static.md) lub metody wystąpienia. Nazwane metody są jedynym sposobem wystąpienia delegata we wcześniejszych wersjach języka C#. Jednak w sytuacji, gdy tworzenie nowej metody jest niepożądane obciążenie, C# umożliwia utworzenie wystąpienia delegata i natychmiast określić blok kodu, który pełnomocnik będzie przetwarzać, gdy jest wywoływana. Blok może zawierać wyrażenie lambda lub metodę anonimową. Aby uzyskać więcej informacji, zobacz [Funkcje anonimowe](../statements-expressions-operators/anonymous-functions.md).  
  
## <a name="remarks"></a>Uwagi  
 Metoda, która jest przekazana jako parametr delegata musi mieć ten sam podpis jako deklaracja delegata.  
  
 Wystąpienie delegata może hermetyzować metodę statyczną lub instancję.  
  
 Mimo że pełnomocnik może użyć [out](../../language-reference/keywords/out-parameter-modifier.md) parametru, nie zaleca się jego użycia z delegatów zdarzeń multiemisji, ponieważ nie wiadomo, który delegat zostanie wywołany.  
  
## <a name="example-1"></a>Przykład 1  
 Poniżej przedstawiono prosty przykład deklarowania i używania pełnomocnika. Należy zauważyć, że `Del`zarówno pełnomocnik, i `MultiplyNumbers`skojarzona metoda , mają ten sam podpis  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a>Przykład 2  
 W poniższym przykładzie jeden delegat jest mapowany na metody statyczne i wystąpienia i zwraca określone informacje z każdego z nich.  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Delegaty](./index.md)
- [Jak połączyć delegatów (delegatów multiemisji)](./how-to-combine-delegates-multicast-delegates.md)
- [Zdarzenia](../events/index.md)
