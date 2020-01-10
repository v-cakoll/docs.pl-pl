---
title: Jak połączyć wiele ciągów (C# przewodnik)
description: Istnieje wiele sposobów łączenia ciągów w C#. Zapoznaj się z opcjami i przyczynami związanymi z różnymi opcjami.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 9a0640a7ce73fa8454442cd301157bf5c265f9de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713896"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="552fc-104">Jak połączyć wiele ciągów (C# przewodnik)</span><span class="sxs-lookup"><span data-stu-id="552fc-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="552fc-105">*Łączenie* jest procesem dołączania jednego ciągu do końca innego ciągu.</span><span class="sxs-lookup"><span data-stu-id="552fc-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="552fc-106">Parametry są łączone za pomocą operatora `+`.</span><span class="sxs-lookup"><span data-stu-id="552fc-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="552fc-107">W przypadku literałów ciągów i stałych ciągów łączenie odbywa się w czasie kompilacji; Brak łączenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="552fc-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="552fc-108">W przypadku zmiennych ciągów łączenie odbywa się tylko w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="552fc-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="552fc-109">Poniższy przykład używa łączenia do dzielenia długiego literału ciągu na mniejsze ciągi w celu zwiększenia czytelności w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="552fc-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="552fc-110">Te części są łączone w jeden ciąg w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="552fc-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="552fc-111">Nie ma kosztu wydajności w czasie wykonywania niezależnie od liczby używanych ciągów.</span><span class="sxs-lookup"><span data-stu-id="552fc-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

<span data-ttu-id="552fc-112">Aby połączyć zmienne ciągów, można użyć operatorów `+` lub `+=`, [interpolacji ciągów](../language-reference/tokens/interpolated.md) lub <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> lub metod <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="552fc-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="552fc-113">Operator `+` jest łatwy w użyciu i umożliwia korzystanie z intuicyjnego kodu.</span><span class="sxs-lookup"><span data-stu-id="552fc-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="552fc-114">Nawet jeśli używasz kilku operatorów `+` w jednej instrukcji, zawartość ciągu jest kopiowana tylko raz.</span><span class="sxs-lookup"><span data-stu-id="552fc-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="552fc-115">Poniższy kod przedstawia przykłady użycia operatorów `+` i `+=` do łączenia ciągów:</span><span class="sxs-lookup"><span data-stu-id="552fc-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="552fc-116">W niektórych wyrażeniach łatwiej jest łączyć ciągi przy użyciu interpolacji ciągów, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="552fc-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> <span data-ttu-id="552fc-117">W operacjach łączenia ciągów C# kompilator traktuje ciąg o wartości null tak samo jak pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="552fc-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="552fc-118">Inna metoda łączenia ciągów jest <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="552fc-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="552fc-119">Ta metoda dobrze sprawdza się w przypadku kompilowania ciągu z niewielkiej liczby ciągów komponentów.</span><span class="sxs-lookup"><span data-stu-id="552fc-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="552fc-120">W innych przypadkach można łączyć ciągi w pętli, gdzie nie wiadomo, ile łączonych parametrów źródłowych, a rzeczywista liczba ciągów źródłowych może być dość duża.</span><span class="sxs-lookup"><span data-stu-id="552fc-120">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="552fc-121">Klasa <xref:System.Text.StringBuilder> została zaprojektowana dla tych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="552fc-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="552fc-122">Poniższy kod używa metody <xref:System.Text.StringBuilder.Append%2A> klasy <xref:System.Text.StringBuilder> do łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="552fc-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="552fc-123">Więcej informacji na temat [przyczyn wyboru łączenia ciągów lub klasy `StringBuilder`](xref:System.Text.StringBuilder#StringAndSB).</span><span class="sxs-lookup"><span data-stu-id="552fc-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB).</span></span>

<span data-ttu-id="552fc-124">Kolejną opcją dołączenia ciągów do kolekcji jest użycie metody <xref:System.String.Concat%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="552fc-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="552fc-125">Użyj metody <xref:System.String.Join%2A?displayProperty=nameWithType>, jeśli ciągi źródłowe powinny być oddzielone ogranicznik.</span><span class="sxs-lookup"><span data-stu-id="552fc-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimeter.</span></span> <span data-ttu-id="552fc-126">Poniższy kod łączy tablicę wyrazów przy użyciu obu metod:</span><span class="sxs-lookup"><span data-stu-id="552fc-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="552fc-127">Na koniec można użyć [LINQ](../programming-guide/concepts/linq/index.md) i metody <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType>, aby dołączyć ciągi z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="552fc-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="552fc-128">Ta metoda łączy parametry źródłowe za pomocą wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="552fc-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="552fc-129">Wyrażenie lambda wykonuje pracy, aby dodać każdy ciąg do istniejącego akumulacji.</span><span class="sxs-lookup"><span data-stu-id="552fc-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="552fc-130">Poniższy przykład łączy tablicę wyrazów przez dodanie odstępu między każdym słowem w tablicy:</span><span class="sxs-lookup"><span data-stu-id="552fc-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="552fc-131">Możesz wypróbować te przykłady, przeglądając kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="552fc-131">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="552fc-132">Możesz też pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="552fc-132">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="552fc-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="552fc-133">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="552fc-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="552fc-134">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="552fc-135">Ciągi</span><span class="sxs-lookup"><span data-stu-id="552fc-135">Strings</span></span>](../programming-guide/strings/index.md)
