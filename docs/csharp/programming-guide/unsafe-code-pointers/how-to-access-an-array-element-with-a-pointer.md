---
title: 'Porady: uzyskiwanie dostępu do elementu tablicy za pomocą wskaźnika - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: b1538068f3ba37a7637e7dc3913e9511d4380daf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635187"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a>Porady: uzyskiwanie dostępu do elementu tablicy za pomocą wskaźnika (C# Programming Guide)

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

 [!code-csharp[csProgGuidePointers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#11)]

 [!code-csharp[csProgGuidePointers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#12)]

**Wielkie litery:**  
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**  
**Małe litery:**  
**abcdefghijklmnopqrstuvwxyz**  

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
