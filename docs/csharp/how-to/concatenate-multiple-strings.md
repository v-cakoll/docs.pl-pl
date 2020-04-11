---
title: Jak połączyć wiele ciągów (Przewodnik języka C#)
description: Istnieje wiele sposobów łączenia ciągów w języku C#. Poznaj opcje i powody różnych wyborów.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 87ec5104f36d0c6cce12037e70dacf2752ef5e62
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121052"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="0258a-104">Jak połączyć wiele ciągów (Przewodnik języka C#)</span><span class="sxs-lookup"><span data-stu-id="0258a-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="0258a-105">*Łączenie* jest procesem dołączania jednego ciągu na końcu innego ciągu.</span><span class="sxs-lookup"><span data-stu-id="0258a-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="0258a-106">Można połączyć ciągi przy `+` użyciu operatora.</span><span class="sxs-lookup"><span data-stu-id="0258a-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="0258a-107">W przypadku literałów ciągów i stałych ciągów łączenie odbywa się w czasie kompilacji; nie występuje łączenie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0258a-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="0258a-108">W przypadku zmiennych ciągów łączenie odbywa się tylko w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0258a-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="0258a-109">W poniższym przykładzie użyto łączenia do dzielenia długiego ciągu literał na mniejsze ciągi w celu poprawy czytelności w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="0258a-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="0258a-110">Te części są łączone w jeden ciąg w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0258a-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="0258a-111">Nie ma żadnych kosztów wydajności w czasie wykonywania, niezależnie od liczby zaangażowanych ciągów.</span><span class="sxs-lookup"><span data-stu-id="0258a-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

<span data-ttu-id="0258a-112">Aby połączyć zmienne ciągu, można `+` `+=` użyć lub operatorów, <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.String.Concat%2A?displayProperty=nameWithType> [interpolacji ciągów](../language-reference/tokens/interpolated.md) lub , lub <xref:System.String.Join%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="0258a-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="0258a-113">Operator `+` jest łatwy w obsłudze i sprawia, że intuicyjny kod.</span><span class="sxs-lookup"><span data-stu-id="0258a-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="0258a-114">Nawet jeśli używasz kilku `+` operatorów w jednej instrukcji, zawartość ciągu jest kopiowana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="0258a-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="0258a-115">Poniższy kod przedstawia przykłady `+` `+=` używania operatorów i do łączenia ciągów:</span><span class="sxs-lookup"><span data-stu-id="0258a-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="0258a-116">W niektórych wyrażeniach łatwiej jest łączyć ciągi za pomocą interpolacji ciągów, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="0258a-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> <span data-ttu-id="0258a-117">W operacjach łączenia ciągów kompilator języka C# traktuje ciąg zerowy tak samo jak pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="0258a-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="0258a-118">Inną metodą łączenia ciągów jest <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0258a-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0258a-119">Ta metoda działa dobrze podczas tworzenia ciągu z niewielkiej liczby ciągów składników.</span><span class="sxs-lookup"><span data-stu-id="0258a-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="0258a-120">W innych przypadkach może być łączenie ciągów w pętli, gdzie nie wiesz, ile ciągów źródłowych łączysz, a rzeczywista liczba ciągów źródłowych może być dość duża.</span><span class="sxs-lookup"><span data-stu-id="0258a-120">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="0258a-121">Klasa <xref:System.Text.StringBuilder> została zaprojektowana dla tych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="0258a-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="0258a-122">Poniższy kod używa <xref:System.Text.StringBuilder.Append%2A> metody <xref:System.Text.StringBuilder> klasy do łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="0258a-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="0258a-123">Możesz przeczytać więcej o [powodach, dla których `StringBuilder` warto wybrać łączenie ciągów lub klasę](xref:System.Text.StringBuilder#StringAndSB).</span><span class="sxs-lookup"><span data-stu-id="0258a-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB).</span></span>

<span data-ttu-id="0258a-124">Inną opcją łączenia ciągów z <xref:System.String.Concat%2A?displayProperty=nameWithType> kolekcji jest użycie metody.</span><span class="sxs-lookup"><span data-stu-id="0258a-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0258a-125">Użyj <xref:System.String.Join%2A?displayProperty=nameWithType> metody, jeśli ciągi źródłowe powinny być oddzielone delimeter.</span><span class="sxs-lookup"><span data-stu-id="0258a-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimeter.</span></span> <span data-ttu-id="0258a-126">Poniższy kod łączy tablicę słów przy użyciu obu metod:</span><span class="sxs-lookup"><span data-stu-id="0258a-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="0258a-127">W końcu można użyć [LINQ](../programming-guide/concepts/linq/index.md) i <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metody do łączenia ciągów z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0258a-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="0258a-128">Ta metoda łączy ciągi źródłowe przy użyciu wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="0258a-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="0258a-129">Wyrażenie lambda wykonuje pracę, aby dodać każdy ciąg do istniejącej akumulacji.</span><span class="sxs-lookup"><span data-stu-id="0258a-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="0258a-130">Poniższy przykład łączy tablicę słów, dodając spację między każdym wyrazem w tablicy:</span><span class="sxs-lookup"><span data-stu-id="0258a-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="0258a-131">Możesz wypróbować te przykłady, patrząc na [przykładowy kod](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="0258a-131">You can try these samples by looking at the [sample code](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="0258a-132">Możesz też pobrać próbki [jako plik zip](../../../samples/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="0258a-132">Or, you can download the samples [as a zip file](../../../samples/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="0258a-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0258a-133">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="0258a-134">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="0258a-134">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="0258a-135">Ciągi</span><span class="sxs-lookup"><span data-stu-id="0258a-135">Strings</span></span>](../programming-guide/strings/index.md)
