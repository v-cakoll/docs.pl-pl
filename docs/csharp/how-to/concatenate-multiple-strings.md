---
title: Jak połączyć wiele ciągów (Przewodnik C#)
description: Istnieje wiele sposobów łączenia ciągów w języku C#. Zapoznaj się z opcjami i przyczynami związanymi z różnymi opcjami.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: ef3d79c5b40d08cb76e58eba1c8831c468fd1fc0
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663021"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="c1403-104">Jak połączyć wiele ciągów (Przewodnik C#)</span><span class="sxs-lookup"><span data-stu-id="c1403-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="c1403-105">*Łączenie* jest procesem dołączania jednego ciągu do końca innego ciągu.</span><span class="sxs-lookup"><span data-stu-id="c1403-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="c1403-106">Parametry są łączone za pomocą `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="c1403-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="c1403-107">W przypadku literałów ciągów i stałych ciągów łączenie odbywa się w czasie kompilacji; Brak łączenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c1403-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="c1403-108">W przypadku zmiennych ciągów łączenie odbywa się tylko w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c1403-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="c1403-109">Poniższy przykład używa łączenia do dzielenia długiego literału ciągu na mniejsze ciągi w celu zwiększenia czytelności w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="c1403-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="c1403-110">Te części są łączone w jeden ciąg w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c1403-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="c1403-111">Nie ma kosztu wydajności w czasie wykonywania niezależnie od liczby używanych ciągów.</span><span class="sxs-lookup"><span data-stu-id="c1403-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet1":::

<span data-ttu-id="c1403-112">Aby połączyć zmienne ciągów, można użyć `+` `+=` operatorów or, [interpolacji ciągów](../language-reference/tokens/interpolated.md) lub <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.String.Concat%2A?displayProperty=nameWithType> <xref:System.String.Join%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metod.</span><span class="sxs-lookup"><span data-stu-id="c1403-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="c1403-113">`+`Operator jest łatwy w użyciu i pozwala na intuicyjny kod.</span><span class="sxs-lookup"><span data-stu-id="c1403-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="c1403-114">Nawet jeśli używasz kilku `+` operatorów w jednej instrukcji, zawartość ciągu jest kopiowana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="c1403-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="c1403-115">Poniższy kod przedstawia przykłady użycia `+` `+=` operatorów i do łączenia ciągów:</span><span class="sxs-lookup"><span data-stu-id="c1403-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet2":::

<span data-ttu-id="c1403-116">W niektórych wyrażeniach łatwiej jest łączyć ciągi przy użyciu interpolacji ciągów, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="c1403-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet3":::

> [!NOTE]
> <span data-ttu-id="c1403-117">W operacjach łączenia ciągów kompilator języka C# traktuje ciąg o wartości null tak samo jak pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="c1403-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="c1403-118">Inną metodą łączenia ciągów jest <xref:System.String.Format%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c1403-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c1403-119">Ta metoda dobrze sprawdza się w przypadku kompilowania ciągu z niewielkiej liczby ciągów komponentów.</span><span class="sxs-lookup"><span data-stu-id="c1403-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="c1403-120">W innych przypadkach można łączyć ciągi w pętli, w której nie wiadomo, ile łączonych parametrów źródłowych, a rzeczywista liczba ciągów źródłowych może być duża.</span><span class="sxs-lookup"><span data-stu-id="c1403-120">In other cases, you may be combining strings in a loop where you don't know how many source strings you're combining, and the actual number of source strings may be large.</span></span> <span data-ttu-id="c1403-121"><xref:System.Text.StringBuilder>Klasa została zaprojektowana dla tych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="c1403-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="c1403-122">Poniższy kod używa <xref:System.Text.StringBuilder.Append%2A> metody <xref:System.Text.StringBuilder> klasy do łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="c1403-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet4":::

<span data-ttu-id="c1403-123">Więcej informacji na temat [przyczyn wyboru łączenia ciągów lub `StringBuilder` klasy](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types).</span><span class="sxs-lookup"><span data-stu-id="c1403-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types).</span></span>

<span data-ttu-id="c1403-124">Kolejną opcją dołączenia ciągów do kolekcji jest użycie <xref:System.String.Concat%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c1403-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c1403-125">Użyj <xref:System.String.Join%2A?displayProperty=nameWithType> metody, jeśli ciągi źródłowe powinny być oddzielone ogranicznikiem.</span><span class="sxs-lookup"><span data-stu-id="c1403-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimiter.</span></span> <span data-ttu-id="c1403-126">Poniższy kod łączy tablicę wyrazów przy użyciu obu metod:</span><span class="sxs-lookup"><span data-stu-id="c1403-126">The following code combines an array of words using both methods:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet5":::

<span data-ttu-id="c1403-127">Na koniec można użyć [LINQ](../programming-guide/concepts/linq/index.md) i <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metody do przyłączania ciągów do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c1403-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="c1403-128">Ta metoda łączy parametry źródłowe za pomocą wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="c1403-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="c1403-129">Wyrażenie lambda wykonuje pracy, aby dodać każdy ciąg do istniejącego akumulacji.</span><span class="sxs-lookup"><span data-stu-id="c1403-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="c1403-130">Poniższy przykład łączy tablicę wyrazów przez dodanie odstępu między każdym słowem w tablicy:</span><span class="sxs-lookup"><span data-stu-id="c1403-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet6":::

## <a name="see-also"></a><span data-ttu-id="c1403-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1403-131">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="c1403-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c1403-132">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="c1403-133">Ciągi</span><span class="sxs-lookup"><span data-stu-id="c1403-133">Strings</span></span>](../programming-guide/strings/index.md)
