---
title: Jak uzyskać dostęp do elementu tablicy za pomocą wskaźnika - C# Programming Guide
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 4f5d82e0ccdffcb694e3030aabe58b8da687a5e1
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084800"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a>Jak uzyskać dostęp do elementu tablicy za pomocą wskaźnika (C# Programming Guide)

W niebezpiecznym kontekście uzyskujesz dostęp elementu w pamięci, używając dostępu do elementu wskaźnika, jak pokazano w poniższym przykładzie:

```csharp
char* charPointer = stackalloc char[123];
for (int i = 65; i < 123; i++)
{
    charPointer[i] = (char)i; //access array elements
}
```

Wyrażenie w nawiasach kwadratowych musi umożliwiać niejawną konwersję na `int`, `uint`, `long`, lub `ulong`. Operacja `p[e]` jest odpowiednikiem `*(p+e)`. Podobnie jak C i C++, dostępu do elementu wskaźnik nie sprawdza obecności liczbach błędy.

## <a name="example"></a>Przykład

W tym przykładzie 123 lokalizacji pamięci są przydzielane do tablicy znaków `charPointer`. Tablica jest używana do wyświetlania małe litery i wielkie litery w dwóch [dla](../../../csharp/language-reference/keywords/for.md) pętli.

Należy zauważyć, że wyrażenie `charPointer[i]` jest równoważne wyrażeniu `*(charPointer + i)`, i ten sam efekt można uzyskać przy użyciu jednej z dwóch wyrażeń.

[!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]

[!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]

**Wielkie litery:**
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**
**małe litery:**
**abcdefghijklmnopqrstuvwxyz**

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Wyrażenia wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Typy wskaźników](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
