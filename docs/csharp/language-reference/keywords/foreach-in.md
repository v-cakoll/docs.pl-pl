---
title: foreach, in (odwołanie w C#)
ms.date: 10/11/2017
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: c0b1481988a2e3199fc6d06ca30cb5194ab2f44c
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="foreach-in-c-reference"></a>foreach, in (odwołanie w C#)

`foreach` Instrukcji powtarza grupę instrukcji embedded dla każdego elementu w tablicy lub kolekcji obiektu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu. [Instrukcji foreach](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement) jest używany do iterowania po kolekcji, aby uzyskać informacje, ale nie można dodać lub usunąć elementy z kolekcji źródłowej, aby uniknąć nieprzewidywalne skutki uboczne. Jeśli musisz dodać lub usunąć elementy z kolekcji źródłowej, użyj [dla](for.md) pętli.
  
 Osadzone instrukcje nadal można wykonać dla każdego elementu w tablicy lub kolekcji. Po ukończeniu iteracji dla wszystkich elementów w kolekcji, sterowania są przesyłane do następnej instrukcji następującej `foreach` bloku.
  
 W miejscach występowania dowolnego punktu w `foreach` bloku, za pomocą można wyjścia z pętli [podziału](break.md) — słowo kluczowe lub krok do następnej iteracji w pętli przy użyciu [kontynuować](continue.md) — słowo kluczowe.

 A `foreach` pętli również można został zakończony przez [goto](goto.md), [zwracać](return.md), lub [throw](throw.md) instrukcje.

 Aby uzyskać więcej informacji na temat `foreach` — słowo kluczowe i przykładowy kod, zobacz następujące tematy:  

 [Używanie instrukcji foreach z tablicami](../../programming-guide/arrays/using-foreach-with-arrays.md)  

 [Instrukcje: uzyskiwanie dostępu do klasy kolekcji za pomocą instrukcji foreach](../../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  

## <a name="example"></a>Przykład

Poniższy kod przedstawia trzy przykłady:

> [!TIP]
> Można modyfikować przykłady eksperymentować składnię i spróbuj różnych użycia, które bardziej przypominają Twojej przypadek użycia. Naciśnij przycisk Uruchom, aby uruchomić kod, a następnie edytuj i naciśnij przycisk "Uruchom" ponownie.

-   Typowe `foreach` pętli, które wyświetla zawartość tablica wartości całkowitych

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L12-L26)]

-   [dla](../../../csharp/language-reference/keywords/for.md) pętli, które jest równoznaczne

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L31-L46)]

-   `foreach` pętli, które przechowuje licznik elementów w tablicy

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L51-L69)]
 
## <a name="c-language-specification"></a>Specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też  

[Instrukcja foreach (specyfikacja języka C#)](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)

[Odwołanie w C#](../index.md)

[Przewodnik programowania w języku C#](../../programming-guide/index.md)

[Słowa kluczowe języka C#](index.md)

[Instrukcje iteracji](iteration-statements.md)

[for](for.md)
