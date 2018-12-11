---
title: słowo kluczowe stackalloc — C# odwołania
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 31fdbacb01d1f6052c86d40c0bffc903130f216c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245512"
---
# <a name="stackalloc-c-reference"></a>stackalloc (odwołanie w C#)

`stackalloc` Słowo kluczowe jest używane w kontekście niebezpieczny kod można przydzielić blok pamięci na stosie.

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a>Uwagi

Słowo kluczowe jest prawidłowy tylko w inicjatorach zmiennej lokalnej. Poniższy kod powoduje błędy kompilatora.

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

Począwszy od języka C# 7.3, można użyć składni inicjatora tablicy dla `stackalloc` tablic. Następujące deklaracje jest zadeklarowanie tablicy za pomocą trzech elementów, których wartości są liczbami całkowitymi `1`, `2`, i `3`:

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

Ponieważ typy wskaźników, `stackalloc` wymaga [niebezpieczne](unsafe.md) kontekstu. Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md).

`stackalloc` przypomina [_alloca](/cpp/c-runtime-library/reference/alloca) biblioteki wykonawczej C.

## <a name="examples"></a>Przykłady

Poniższy przykład oblicza i wyświetla pierwszych 20 cyfr w sekwencji Fibonacci. Każdy numer to suma poprzednich dwóch liczb. W kodzie, blok pamięci wystarczająco duży, aby zawierała 20 elementów typu `int` jest przydzielony na stosie nie sterty. Adres bloku jest przechowywany we wskaźniku `fib`. Ta pamięć nie podlega wyrzucania elementów bezużytecznych i w związku z tym nie trzeba przypiąć (przy użyciu [stałej](fixed-statement.md)). Okres istnienia blok pamięci jest ograniczona do okresu istnienia metody, który go definiuje. Nie można zwolnić pamięć, przed powrotem z metody.

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

Poniższy przykład inicjuje `stackalloc` tablica liczb całkowitych do maski bitowej o jeden bit ustawiona w każdym elemencie. W tym przykładzie pokazano, jak nowa składnia inicjatora dostępnych w języku C# 7.3:

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a>Zabezpieczenia

Niebezpieczny kod jest mniej bezpieczna niż bezpiecznych metod. Jednak użycie `stackalloc` automatycznie włącza funkcje wykrywania przepełnienia buforu, w środowisku uruchomieniowym języka (wspólnego CLR). W przypadku wykrycia przepełnienie buforu tak szybko, jak to możliwe, aby zminimalizować prawdopodobieństwo, że złośliwy kod jest wykonywany zakończenia procesu.

## <a name="c-language-specification"></a>specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
- [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)
- [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)