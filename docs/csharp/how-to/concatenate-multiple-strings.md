---
title: Jak połączyć wiele ciągów (Przewodnik C#)
description: Istnieje wiele sposobów łączenia ciągów w języku C#. Poznaj opcje i przyczyny różnych wyborów.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 9a0640a7ce73fa8454442cd301157bf5c265f9de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713896"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="5724d-104">Jak połączyć wiele ciągów (Przewodnik C#)</span><span class="sxs-lookup"><span data-stu-id="5724d-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="5724d-105">*Łączenie* jest procesem dołączania jednego ciągu na końcu innego ciągu.</span><span class="sxs-lookup"><span data-stu-id="5724d-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="5724d-106">Ciągi łączysz za pomocą `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="5724d-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="5724d-107">W przypadku literału ciągów i stałych ciągów łączenie odbywa się w czasie kompilacji; nie występuje konkanację w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5724d-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="5724d-108">W przypadku zmiennych ciągów łączenie występuje tylko w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5724d-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="5724d-109">W poniższym przykładzie użyto konkatenacji, aby podzielić literał długiego ciągu na mniejsze ciągi w celu zwiększenia czytelności w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="5724d-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="5724d-110">Te części są łączone w jeden ciąg w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5724d-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="5724d-111">Nie ma żadnych kosztów wydajności w czasie wykonywania, niezależnie od liczby ciągów zaangażowanych.</span><span class="sxs-lookup"><span data-stu-id="5724d-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

<span data-ttu-id="5724d-112">Aby połączyć zmienne ciągów, można użyć `+` `+=` lub operatorów, [interpolacji ciągów](../language-reference/tokens/interpolated.md) <xref:System.String.Format%2A?displayProperty=nameWithType>lub <xref:System.String.Concat%2A?displayProperty=nameWithType>, lub <xref:System.String.Join%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metod.</span><span class="sxs-lookup"><span data-stu-id="5724d-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="5724d-113">Operator `+` jest łatwy w obsłudze i zapewnia intuicyjny kod.</span><span class="sxs-lookup"><span data-stu-id="5724d-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="5724d-114">Nawet jeśli używasz `+` kilku operatorów w jednej instrukcji, zawartość ciągu jest kopiowany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="5724d-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="5724d-115">Poniższy kod przedstawia przykłady używania `+` `+=` i operatorów do łączenia ciągów:</span><span class="sxs-lookup"><span data-stu-id="5724d-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="5724d-116">W niektórych wyrażeniach łatwiej jest połączyć ciągi za pomocą interpolacji ciągów, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="5724d-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> <span data-ttu-id="5724d-117">W operacjach łączenia ciągów kompilator C# traktuje ciąg zerowy taki sam jak pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="5724d-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="5724d-118">Inną metodą łączenia ciągów jest <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5724d-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5724d-119">Ta metoda działa dobrze podczas tworzenia ciągu z niewielkiej liczby ciągów składników.</span><span class="sxs-lookup"><span data-stu-id="5724d-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="5724d-120">W innych przypadkach może być łączenie ciągów w pętli, gdzie nie wiesz, ile ciągów źródłowych są łączące, a rzeczywista liczba ciągów źródłowych może być dość duża.</span><span class="sxs-lookup"><span data-stu-id="5724d-120">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="5724d-121">Klasa <xref:System.Text.StringBuilder> została zaprojektowana dla tych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="5724d-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="5724d-122">Poniższy kod używa <xref:System.Text.StringBuilder.Append%2A> metody <xref:System.Text.StringBuilder> klasy do łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="5724d-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="5724d-123">Możesz przeczytać więcej o [powodach, dla których `StringBuilder` należy wybrać łączenie ciągów lub klasę](xref:System.Text.StringBuilder#StringAndSB).</span><span class="sxs-lookup"><span data-stu-id="5724d-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB).</span></span>

<span data-ttu-id="5724d-124">Inną opcją łączenia ciągów z <xref:System.String.Concat%2A?displayProperty=nameWithType> kolekcji jest użycie metody.</span><span class="sxs-lookup"><span data-stu-id="5724d-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5724d-125">Użyj <xref:System.String.Join%2A?displayProperty=nameWithType> metody, jeśli ciągi źródłowe powinny być oddzielone delimeter.</span><span class="sxs-lookup"><span data-stu-id="5724d-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimeter.</span></span> <span data-ttu-id="5724d-126">Poniższy kod łączy tablicę wyrazów przy użyciu obu metod:</span><span class="sxs-lookup"><span data-stu-id="5724d-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="5724d-127">W końcu można użyć [LINQ](../programming-guide/concepts/linq/index.md) i <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metody do łączenia ciągów z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5724d-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="5724d-128">Ta metoda łączy ciągi źródłowe przy użyciu wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="5724d-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="5724d-129">Wyrażenie lambda wykonuje pracę, aby dodać każdy ciąg do istniejącej akumulacji.</span><span class="sxs-lookup"><span data-stu-id="5724d-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="5724d-130">Poniższy przykład łączy tablicę wyrazów, dodając odstęp między każdym wyrazem w tablicy:</span><span class="sxs-lookup"><span data-stu-id="5724d-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="5724d-131">Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="5724d-131">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="5724d-132">Możesz też pobrać próbki [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="5724d-132">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="5724d-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5724d-133">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="5724d-134">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="5724d-134">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="5724d-135">Ciągi</span><span class="sxs-lookup"><span data-stu-id="5724d-135">Strings</span></span>](../programming-guide/strings/index.md)
