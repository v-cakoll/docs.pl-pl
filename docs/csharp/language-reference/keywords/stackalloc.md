---
title: stackalloc (odwołanie w C#)
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 905873cf7f576ff35a9bc1c182ce7ebe17920288
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269171"
---
# <a name="stackalloc-c-reference"></a>stackalloc (odwołanie w C#)
`stackalloc` — Słowo kluczowe jest używane w kontekście niebezpieczny kod można przydzielić bloku pamięci na stosie.

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a>Uwagi

Słowo kluczowe jest prawidłowy tylko w lokalnej zmiennej inicjatory. Poniższy kod powoduje, że błędy kompilatora.

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

Począwszy od 7.3 C#, można użyć składni inicjatora tablicy dla `stackalloc` tablic. Następujące deklaracje zadeklarować tablicę z trzech elementów, których wartości są liczby całkowite `1`, `2`, i `3`:

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

Ponieważ są związane z typów wskaźnika, `stackalloc` wymaga [niebezpieczne](unsafe.md) kontekstu. Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md) 

`stackalloc` przypomina [_alloca](/cpp/c-runtime-library/reference/alloca) biblioteki wykonawcze języka C.

## <a name="examples"></a>Przykłady

Poniższy przykład oblicza i wyświetla najpierw 20 cyfr w sekwencji Fibonacci. Każdą liczbę to suma poprzednich dwóch liczb. W kodzie bloku pamięci wystarczający rozmiar ma 20 elementów typu `int` został przydzielony na stosie nie stosu. Adres bloku są przechowywane we wskaźniku `fib`. Ta pamięć nie podlega wyrzucanie elementów bezużytecznych i dlatego nie trzeba przypięty (przy użyciu [stałej](fixed-statement.md)). Okres istnienia blok pamięci jest ograniczona do istnienia metody, która definiuje ją. Nie można zwolnić pamięć, przed metoda zwraca.

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

W poniższym przykładzie inicjowane `stackalloc` tablica liczb całkowitych na maska bitowa o jeden bit, ustaw w każdym elemencie. Oznacza to, nowej składni inicjatora dostępne począwszy od 7.3 C#:

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a>Zabezpieczenia

Niebezpieczny kod jest mniej bezpieczna niż bezpiecznych metod. Jednak użycie `stackalloc` automatycznie włączone funkcje wykrywania przepełnienie buforu w środowisku uruchomieniowym języka (wspólnego CLR). W przypadku wykrycia przepełnienie buforu, proces jest zakończony tak szybko jak to możliwe, aby zminimalizować ryzyko, że złośliwy kod jest wykonywany.

## <a name="c-language-specification"></a>Specyfikacja języka C#
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [Niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
