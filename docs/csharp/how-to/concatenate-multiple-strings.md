---
title: 'Porady: łączenie wielu ciągów (Przewodnik C#)'
description: Istnieje wiele sposobów łączenia ciągów w języku C#. Poznaj opcje i powodów różne opcje.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 355e56acf36b6212ee4563f34722b10b56a0fb47
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43256101"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="263c1-104">Porady: łączenie wielu ciągów (Przewodnik C#)</span><span class="sxs-lookup"><span data-stu-id="263c1-104">How to: Concatenate Multiple Strings (C# Guide)</span></span>

<span data-ttu-id="263c1-105">*Łączenie* to proces dołączania jednego ciągu do końca ciągu w innym.</span><span class="sxs-lookup"><span data-stu-id="263c1-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="263c1-106">Łączenie ciągów za pomocą `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="263c1-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="263c1-107">Literały ciągu i stałych ciągów łączenie wystąpi w czasie kompilacji; występuje, nie łączenia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="263c1-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="263c1-108">W przypadku zmiennych ciągu łączenia jest wykonywane tylko w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="263c1-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="263c1-109">W poniższym przykładzie użyto łączenia, aby podzielić ciąg literału mniejszych ciągów w celu poprawienia czytelności w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="263c1-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="263c1-110">Te elementy są łączone w pojedynczy ciąg w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="263c1-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="263c1-111">Nie ma żadnych kosztów wydajności w czasie wykonywania, bez względu na liczbę ciągów zaangażowane.</span><span class="sxs-lookup"><span data-stu-id="263c1-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

<span data-ttu-id="263c1-112">Aby połączyć zmiennych ciągu, można użyć `+` lub `+=` operatorów, [Interpolacja ciągów](../language-reference/tokens/interpolated.md) lub <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="263c1-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="263c1-113">`+` Operator jest łatwa w użyciu i sprawia, że kod intuicyjne.</span><span class="sxs-lookup"><span data-stu-id="263c1-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="263c1-114">Nawet w przypadku używania kilku `+` operatorów w jednej instrukcji, ciąg zawartości jest kopiowany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="263c1-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="263c1-115">Poniższy kod pokazuje przykłady stosowania `+` i `+=` operatory łączenia ciągów:</span><span class="sxs-lookup"><span data-stu-id="263c1-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="263c1-116">W niektórych wyrażeniach łatwiej jest łączenie ciągów przy użyciu interpolacji ciągu, co ilustruje poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="263c1-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> <span data-ttu-id="263c1-117">W ramach operacji łączenia ciągu kompilator języka C# traktuje pusty ciąg takie same jako pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="263c1-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="263c1-118">Druga metoda łączenia ciągów jest <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="263c1-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="263c1-119">Ta metoda działa dobrze w przypadku, gdy tworzysz ciąg z małą liczbą składników ciągów.</span><span class="sxs-lookup"><span data-stu-id="263c1-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="263c1-120">W innych przypadkach może być łączenie ciągów w pętli, w którym nie wiesz, ile ciągi źródłowe są połączenie, a rzeczywista liczba ciągi źródłowe może być dość duży.</span><span class="sxs-lookup"><span data-stu-id="263c1-120">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="263c1-121"><xref:System.Text.StringBuilder> Klasa została zaprojektowana dla tych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="263c1-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="263c1-122">Poniższy kod używa <xref:System.Text.StringBuilder.Append%2A> metody <xref:System.Text.StringBuilder> klasy do łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="263c1-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="263c1-123">Przeczytaj więcej o [powodów przemawiających ciągów lub `StringBuilder` klasy](xref:System.Text.StringBuilder#StringAndSB)</span><span class="sxs-lookup"><span data-stu-id="263c1-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB)</span></span>

<span data-ttu-id="263c1-124">Inną opcję, aby dołączyć ciągi z kolekcji jest użycie <xref:System.String.Concat%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="263c1-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="263c1-125">Użyj <xref:System.String.Join%2A?displayProperty=nameWithType> metodę, jeżeli ciągi źródłowe powinien być oddzielony przecinkiem ogranicznik.</span><span class="sxs-lookup"><span data-stu-id="263c1-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimeter.</span></span> <span data-ttu-id="263c1-126">Poniższy kod łączy tablicę wyrazów za pomocą obu tych metod:</span><span class="sxs-lookup"><span data-stu-id="263c1-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="263c1-127">Ostatnio, możesz użyć [LINQ](../programming-guide/concepts/linq/index.md) i <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metodę, aby dołączyć ciągi z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="263c1-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="263c1-128">Ta metoda łączy ciągi źródłowe użycie wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="263c1-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="263c1-129">Wyrażenie lambda wykonuje pracę można dodać każdego ciągu do gromadzenia istniejących.</span><span class="sxs-lookup"><span data-stu-id="263c1-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="263c1-130">Poniższy przykład obejmuje szereg słów przez dodanie miejsca między każdego wyrazu w tablicy:</span><span class="sxs-lookup"><span data-stu-id="263c1-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="263c1-131">Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="263c1-131">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="263c1-132">Można również pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="263c1-132">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="263c1-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="263c1-133">See Also</span></span>

- <xref:System.String>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="263c1-134">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="263c1-134">C# Programming Guide</span></span>](../programming-guide/index.md)  
- [<span data-ttu-id="263c1-135">Ciągi</span><span class="sxs-lookup"><span data-stu-id="263c1-135">Strings</span></span>](../programming-guide/strings/index.md)
