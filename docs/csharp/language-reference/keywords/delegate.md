---
title: delegate (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
ms.openlocfilehash: 7a5f46d137e22da01b2ab6cd3eee57d66c411e8f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442736"
---
# <a name="delegate-c-reference"></a>delegate (odwołanie w C#)

Deklaracja typu delegata jest podobny do podpisu metody. Ma wartość zwracaną i dowolną liczbę parametrów, dowolnego typu:

```csharp
public delegate void TestDelegate(string message);
public delegate int TestDelegate(MyType m, long num);
```

Element `delegate` jest typem referencyjnym, który może służyć do hermetyzacji nazwane lub metodę anonimową. Delegaty są podobne do wskaźników funkcji języka C++; Jednak obiekty delegowane są bezpieczne i bezpieczny typowo. W przypadku aplikacji delegatów, zobacz [delegatów](../../../csharp/programming-guide/delegates/index.md) i [delegatów ogólnych](../../../csharp/programming-guide/generics/generic-delegates.md).

## <a name="remarks"></a>Uwagi

Obiekty delegowane są podstawą [zdarzenia](../../../csharp/programming-guide/events/index.md).

Pełnomocnik może być utworzone przez skojarzenie przy użyciu metody nazwane i anonimowe. Aby uzyskać więcej informacji, zobacz [metody o nazwie](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) i [anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).

Za pomocą metody lub wyrażenia lambda zgodne zwracany typ i parametry wejściowe, można utworzyć wystąpienia obiektu delegowanego. Aby uzyskać więcej informacji na temat stopień odchylenia, jaki jest dozwolony w podpisie metody, zobacz [wariancje w Delegatach](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Do użytku z metod anonimowych delegat i kodu, które ma zostać skojarzony z nim są zadeklarowane jednocześnie. Obie metody tworzenia wystąpienia obiektów delegowanych zostały omówione w tej sekcji.

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsTypes#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#8)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)  
- [Delegaci](../../../csharp/programming-guide/delegates/index.md)  
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
- [Delegaci z metodami nazwanymi lub anonimowymi](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
- [Metody anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
