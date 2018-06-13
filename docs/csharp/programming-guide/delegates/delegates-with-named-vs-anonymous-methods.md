---
title: Obiekty delegowane z nazwanego vs. Metody anonimowe (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 93e140859e44aab860577feede40df6eab4c8e00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330768"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a>Obiekty delegowane z nazwanego vs. Metody anonimowe (Przewodnik programowania w języku C#)
A [delegować](../../../csharp/language-reference/keywords/delegate.md) może być skojarzony z metodę o nazwie. Gdy przy użyciu nazwanego metody tworzenia wystąpienia delegata, metody jest przekazywany jako parametru, na przykład:  
  
 [!code-csharp[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]  
  
 Jest to, za pomocą metodę o nazwie. Obiekty delegowane skonstruowany przy metodę o nazwie umożliwiająca Hermetyzowanie albo [statycznych](../../../csharp/language-reference/keywords/static.md) metody lub metodą wystąpienia. Nazwane metody są jedynym sposobem tworzenia wystąpienia delegata we wcześniejszych wersjach języka C#. Jednak w sytuacji, gdy tworzenie nowej metody jest niechciane nakładów pracy, C# umożliwia tworzenia wystąpienia delegata i natychmiast Określ blok kodu, który przetworzy delegata, gdy jest wywoływana. Blok może zawierać wyrażenia lambda lub metody anonimowej. Aby uzyskać więcej informacji, zobacz [funkcje anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="remarks"></a>Uwagi  
 Metodę przekazać jako parametru delegowanego musi mieć taką samą sygnaturę jak deklaracji obiektu delegowanego.  
  
 Wystąpienie obiektu delegowanego Hermetyzowanie statycznych lub metody wystąpienia.  
  
 Mimo że można używać delegata [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametru, nie zaleca się on z delegaty multiemisji zdarzeń ponieważ nie wiadomo, delegata, która zostanie wywołana.  
  
## <a name="example-1"></a>Przykład 1  
 Oto prosty przykład deklarowania i przy użyciu delegata. Zwróć uwagę, że oba delegata, `Del`i skojarzone metody `MultiplyNumbers`, mają taką samą sygnaturę  
  
 [!code-csharp[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]  
  
## <a name="example-2"></a>Przykład 2  
 W poniższym przykładzie jednego delegata jest mapowany na obu statyczna i metod i zwraca określone informacje z każdego wystąpienia.  
  
 [!code-csharp[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Delegaci](../../../csharp/programming-guide/delegates/index.md)  
 [Metody anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)
