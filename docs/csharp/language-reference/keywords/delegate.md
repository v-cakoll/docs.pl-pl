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
ms.openlocfilehash: ba1cfdcc56b3d2301a07ffa4af793e7002da21bb
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948426"
---
# <a name="delegate-c-reference"></a>delegate (odwołanie w C#)

Deklaracja typu delegowanego jest podobny do sygnatury metody. Ma wartość zwracaną i dowolną liczbę parametrów dowolnego typu:

```csharp
public delegate void TestDelegate(string message);
public delegate int TestDelegate(MyType m, long num);
```

A `delegate` jest typem referencyjnym, który może służyć Hermetyzowanie nazwane ani metoda anonimowa. Obiekty delegowane są podobne do wskaźników funkcji w języku C++; jednak delegatów są bezpieczne i bezpieczne. W przypadku aplikacji o delegatów, zobacz [delegatów](../../../csharp/programming-guide/delegates/index.md) i [delegatów](../../../csharp/programming-guide/generics/generic-delegates.md).

## <a name="remarks"></a>Uwagi

Obiekty delegowane stanowią podstawę dla [zdarzenia](../../../csharp/programming-guide/events/index.md).

Delegat można wdrożyć przez skojarzenie za pomocą metody nazwane i anonimowe. Aby uzyskać więcej informacji, zobacz [metody o nazwie](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) i [metod anonimowych](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).

Obiekt delegowany musi być utworzone za pomocą wyrażenia metody lub lambda ma niezgodny typ zwracany i parametrów wejściowych. Aby uzyskać więcej informacji na stopień wariancję, jaki jest dozwolony w podpisie metody, zobacz [wariancji w Delegatach](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Do użytku z metod anonimowych delegat i kodu ma zostać skojarzony z nim są zadeklarowane jednocześnie. W tej sekcji omówiono obu kierunkach, tworzenie wystąpień obiektów delegowanych.

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsTypes#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#8)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
[Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
[Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)  
[Delegaci](../../../csharp/programming-guide/delegates/index.md)  
[Zdarzenia](../../../csharp/programming-guide/events/index.md)  
[Delegaci z metodami nazwanymi lub anonimowymi](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
[Metody anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
