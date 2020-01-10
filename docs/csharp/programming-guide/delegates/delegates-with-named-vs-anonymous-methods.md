---
title: Delegaty z metodami nazwanymi i C# anonimowymi — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 1ec366999ca6457471b705fa83f06fcde4293f4e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712380"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a>Delegaty z metodami nazwanymi lub anonimowymi (Przewodnik programowania w języku C#)
[Delegat](../../language-reference/builtin-types/reference-types.md) może być skojarzony z nazwaną metodą. Podczas tworzenia wystąpienia delegata przy użyciu nazwanej metody Metoda jest przenoszona jako parametr, na przykład:  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 Ta metoda jest wywoływana przy użyciu nazwanej metody. Obiekty delegowane skonstruowane przy użyciu nazwanej metody mogą hermetyzować metodę [statyczną](../../language-reference/keywords/static.md) lub metodę wystąpienia. Nazwane metody są jedynym sposobem tworzenia wystąpienia delegata we wcześniejszych wersjach programu C#. Jednak w sytuacji, w której Tworzenie nowej metody jest niepożądane, C# umożliwia utworzenie wystąpienia delegata i natychmiastowe określenie bloku kodu, który obiekt delegowany będzie przetwarzany po wywołaniu. Blok może zawierać wyrażenie lambda lub metodę anonimową. Aby uzyskać więcej informacji, zobacz [funkcje anonimowe](../statements-expressions-operators/anonymous-functions.md).  
  
## <a name="remarks"></a>Uwagi  
 Metoda, która jest przekazywany jako parametr delegata, musi mieć taką samą sygnaturę jak Deklaracja delegata.  
  
 Wystąpienie delegata może hermetyzować wartość statyczną lub metodę wystąpienia.  
  
 Chociaż delegat może korzystać z parametru [out](../../language-reference/keywords/out-parameter-modifier.md) , nie zalecamy jej używania z delegatami zdarzeń multiemisji, ponieważ nie można wiedzieć, który delegat zostanie wywołany.  
  
## <a name="example-1"></a>Przykład 1  
 Poniżej przedstawiono prosty przykład deklarowania i używania delegata. Zwróć uwagę, że zarówno delegat, `Del`, jak i Metoda skojarzona, `MultiplyNumbers`, mają tę samą sygnaturę  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a>Przykład 2  
 W poniższym przykładzie jeden delegat jest mapowany na metody static i instance i zwraca określone informacje z każdego z nich.  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Delegaci](./index.md)
- [Jak łączyć delegatów (delegatów multiemisji)](./how-to-combine-delegates-multicast-delegates.md)
- [Zdarzenia](../events/index.md)
