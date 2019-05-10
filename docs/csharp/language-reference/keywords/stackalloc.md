---
title: słowo kluczowe stackalloc — C# odwołania
ms.custom: seodec18
ms.date: 04/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 654e225ef98b13aeb4f689e17b1ff378e6002d28
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063913"
---
# <a name="stackalloc-c-reference"></a>stackalloc (odwołanie w C#)

`stackalloc` — Słowo kluczowe jest używany do alokowania blok pamięci na stosie.

```csharp
Span<int> block = stackalloc int[100];
```

Przypisywanie przydzielonego bloku <xref:System.Span%601?displayName=nameWithType> zamiast `int*` umożliwia twórz stos z alokacji w bezpiecznym bloku. `unsafe` Kontekst nie jest wymagane.

## <a name="remarks"></a>Uwagi

Słowo kluczowe jest prawidłowy tylko w inicjatorach zmiennej lokalnej. Poniższy kod powoduje błędy kompilatora.

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
Span<int> span;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
span = stackalloc int[100];
```

Począwszy od języka C# 7.3, można użyć składni inicjatora tablicy dla `stackalloc` tablic. Następujące deklaracje jest zadeklarowanie tablicy za pomocą trzech elementów, których wartości są liczbami całkowitymi `1`, `2`, i `3`. Drugi inicjowania przypisuje pamięci, aby <xref:System.ReadOnlySpan%601>, wskazujący, że pamięć nie może być modyfikowany.

```csharp
// Valid starting with C# 7.3
Span<int> first = stackalloc int[3] { 1, 2, 3 };
ReadOnlySpan<int> second = stackalloc int[] { 1, 2, 3 };
Span<int> third = stackalloc[] { 1, 2, 3 };
```

W przypadku typów wskaźnika `stackalloc` wymaga [niebezpieczne](unsafe.md) kontekstu. Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md).

`stackalloc` przypomina [_alloca](/cpp/c-runtime-library/reference/alloca) biblioteki wykonawczej C.

## <a name="examples"></a>Przykłady

Poniższy przykład oblicza i wyświetla pierwszych 20 cyfr w sekwencji Fibonacci. Każdy numer to suma poprzednich dwóch liczb. W kodzie, blok pamięci wystarczająco duży, aby zawierała 20 elementów typu `int` jest przydzielony na stosie nie sterty. Adres bloku są przechowywane w `Span` `fib`. Ta pamięć nie podlega wyrzucania elementów bezużytecznych i w związku z tym nie trzeba przypiąć (przy użyciu [stałej](fixed-statement.md)). Okres istnienia blok pamięci jest ograniczona do okresu istnienia metody, który go definiuje. Nie można zwolnić pamięć, przed powrotem z metody.

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

Poniższy przykład inicjuje `stackalloc` tablica liczb całkowitych do maski bitowej o jeden bit ustawiona w każdym elemencie. W tym przykładzie pokazano, jak nowa składnia inicjatora dostępnych w języku C# 7.3:

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a>Zabezpieczenia

Należy używać <xref:System.Span%601> lub <xref:System.ReadOnlySpan%601> Jeśli to możliwe, ponieważ niebezpieczny kod jest mniej bezpieczna niż bezpiecznych metod. Nawet wtedy, gdy jest używane z wskaźników, użycie `stackalloc` automatycznie włącza funkcje wykrywania przepełnienia buforu, w środowisku uruchomieniowym języka (wspólnego CLR). W przypadku wykrycia przepełnienie buforu tak szybko, jak to możliwe, aby zminimalizować prawdopodobieństwo, że złośliwy kod jest wykonywany zakończenia procesu.

## <a name="c-language-specification"></a>specyfikacja języka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Słowa kluczowe operatora](operator-keywords.md)
- [Niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md)
