---
title: Delegaty z nazwanymi lub. Metody anonimowe (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 6d7dcb3c7c6fa8f1d55237504c23cf468aa0e79d
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44274212"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a>Delegaty z nazwanymi lub. Metody anonimowe (Przewodnik programowania w języku C#)
A [delegować](../../../csharp/language-reference/keywords/delegate.md) mogą być skojarzone z metodę o nazwie. Podczas tworzenia wystąpienia delegata za pomocą metodę o nazwie metoda jest przekazywana jako parametr, na przykład:  
  
 [!code-csharp[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]  
  
 Jest to, za pomocą innej metody o nazwie. Delegaty skonstruowany przy użyciu metodę o nazwie umożliwiająca Hermetyzowanie albo [statyczne](../../../csharp/language-reference/keywords/static.md) metodę lub metodę wystąpienia. Metody o nazwie są jedynym sposobem tworzenia wystąpienia delegata we wcześniejszych wersjach języka C#. Jednak w sytuacji, w których utworzenie nowej metody jest niechciane obciążenie, C# umożliwia tworzenia wystąpienia delegata i natychmiast określić blok kodu, który przetworzy delegata, gdy jest wywoływana. Blok może zawierać wyrażenia lambda lub metodę anonimową. Aby uzyskać więcej informacji, zobacz [funkcjami anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="remarks"></a>Uwagi  
 Metoda, który jest przekazywany jako parametr delegata musi mieć taką samą sygnaturę jak deklaracja delegata.  
  
 Wystąpienie delegata może hermetyzacji statycznych lub metodę wystąpienia.  
  
 Chociaż można używać delegata [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametru, nie zaleca się korzystanie z delegaty multiemisji zdarzeń ponieważ nie wie, delegata, która zostanie wywołana.  
  
## <a name="example-1"></a>Przykład 1  
 Oto prosty przykład deklarowanie i używanie delegata. Należy zauważyć, że oba delegata, `Del`i skojarzoną metodę `MultiplyNumbers`, mają taki sam podpis  
  
 [!code-csharp[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]  
  
## <a name="example-2"></a>Przykład 2  
 W poniższym przykładzie jednego delegata jest mapowany na statycznych i metod i zwraca szczegółowe informacje z każdego wystąpienia.  
  
 [!code-csharp[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Delegaci](../../../csharp/programming-guide/delegates/index.md)  
- [Metody anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
- [Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)
