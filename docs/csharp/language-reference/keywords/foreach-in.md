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
# <a name="foreach-in-c-reference"></a><span data-ttu-id="28658-102">foreach, in (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="28658-102">foreach, in (C# Reference)</span></span>

<span data-ttu-id="28658-103">`foreach` Instrukcji powtarza grupę instrukcji embedded dla każdego elementu w tablicy lub kolekcji obiektu, który implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="28658-103">The `foreach` statement repeats a group of embedded statements for each element in an array or an object collection that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="28658-104">[Instrukcji foreach](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement) jest używany do iterowania po kolekcji, aby uzyskać informacje, ale nie można dodać lub usunąć elementy z kolekcji źródłowej, aby uniknąć nieprzewidywalne skutki uboczne.</span><span class="sxs-lookup"><span data-stu-id="28658-104">The [foreach statement](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement) is used to iterate through the collection to get the information that you want, but can not be used to add or remove items from the source collection to avoid unpredictable side effects.</span></span> <span data-ttu-id="28658-105">Jeśli musisz dodać lub usunąć elementy z kolekcji źródłowej, użyj [dla](for.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="28658-105">If you need to add or remove items from the source collection, use a [for](for.md) loop.</span></span>
  
 <span data-ttu-id="28658-106">Osadzone instrukcje nadal można wykonać dla każdego elementu w tablicy lub kolekcji.</span><span class="sxs-lookup"><span data-stu-id="28658-106">The embedded statements continue to execute for each element in the array or collection.</span></span> <span data-ttu-id="28658-107">Po ukończeniu iteracji dla wszystkich elementów w kolekcji, sterowania są przesyłane do następnej instrukcji następującej `foreach` bloku.</span><span class="sxs-lookup"><span data-stu-id="28658-107">After the iteration has been completed for all the elements in the collection, control is transferred to the next statement following the `foreach` block.</span></span>
  
 <span data-ttu-id="28658-108">W miejscach występowania dowolnego punktu w `foreach` bloku, za pomocą można wyjścia z pętli [podziału](break.md) — słowo kluczowe lub krok do następnej iteracji w pętli przy użyciu [kontynuować](continue.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="28658-108">At any point within the `foreach` block, you can break out of the loop by using the [break](break.md) keyword, or step to the next iteration in the loop by using the [continue](continue.md) keyword.</span></span>

 <span data-ttu-id="28658-109">A `foreach` pętli również można został zakończony przez [goto](goto.md), [zwracać](return.md), lub [throw](throw.md) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="28658-109">A `foreach` loop can also be exited by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

 <span data-ttu-id="28658-110">Aby uzyskać więcej informacji na temat `foreach` — słowo kluczowe i przykładowy kod, zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="28658-110">For more information about the `foreach` keyword and code samples, see the following topics:</span></span>  

 [<span data-ttu-id="28658-111">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="28658-111">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  

 [<span data-ttu-id="28658-112">Instrukcje: uzyskiwanie dostępu do klasy kolekcji za pomocą instrukcji foreach</span><span class="sxs-lookup"><span data-stu-id="28658-112">How to: Access a Collection Class with foreach</span></span>](../../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  

## <a name="example"></a><span data-ttu-id="28658-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="28658-113">Example</span></span>

<span data-ttu-id="28658-114">Poniższy kod przedstawia trzy przykłady:</span><span class="sxs-lookup"><span data-stu-id="28658-114">The following code shows three examples:</span></span>

> [!TIP]
> <span data-ttu-id="28658-115">Można modyfikować przykłady eksperymentować składnię i spróbuj różnych użycia, które bardziej przypominają Twojej przypadek użycia.</span><span class="sxs-lookup"><span data-stu-id="28658-115">You can modify the examples to experiment with the syntax and try different usages that are more similar to your use case.</span></span> <span data-ttu-id="28658-116">Naciśnij przycisk Uruchom, aby uruchomić kod, a następnie edytuj i naciśnij przycisk "Uruchom" ponownie.</span><span class="sxs-lookup"><span data-stu-id="28658-116">Press "Run" to run the code, then edit and press "Run" again.</span></span>

-   <span data-ttu-id="28658-117">Typowe `foreach` pętli, które wyświetla zawartość tablica wartości całkowitych</span><span class="sxs-lookup"><span data-stu-id="28658-117">a typical `foreach` loop that displays the contents of an array of integers</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L12-L26)]

-   <span data-ttu-id="28658-118">[dla](../../../csharp/language-reference/keywords/for.md) pętli, które jest równoznaczne</span><span class="sxs-lookup"><span data-stu-id="28658-118">a [for](../../../csharp/language-reference/keywords/for.md) loop that does the same thing</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L31-L46)]

-   <span data-ttu-id="28658-119">`foreach` pętli, które przechowuje licznik elementów w tablicy</span><span class="sxs-lookup"><span data-stu-id="28658-119">a `foreach` loop that maintains a count of the number of elements in the array</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L51-L69)]
 
## <a name="c-language-specification"></a><span data-ttu-id="28658-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="28658-120">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="28658-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28658-121">See Also</span></span>  

[<span data-ttu-id="28658-122">Instrukcja foreach (specyfikacja języka C#)</span><span class="sxs-lookup"><span data-stu-id="28658-122">The foreach statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)

[<span data-ttu-id="28658-123">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="28658-123">C# Reference</span></span>](../index.md)

[<span data-ttu-id="28658-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="28658-124">C# Programming Guide</span></span>](../../programming-guide/index.md)

[<span data-ttu-id="28658-125">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="28658-125">C# Keywords</span></span>](index.md)

[<span data-ttu-id="28658-126">Instrukcje iteracji</span><span class="sxs-lookup"><span data-stu-id="28658-126">Iteration Statements</span></span>](iteration-statements.md)

[<span data-ttu-id="28658-127">for</span><span class="sxs-lookup"><span data-stu-id="28658-127">for</span></span>](for.md)
