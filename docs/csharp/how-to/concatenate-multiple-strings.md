---
title: "Porady: łączenie wielu ciągów (Przewodnik C#)"
description: "Istnieje wiele sposobów łączenia ciągów w języku C#. Poznaj opcje i przyczynami różne opcje."
ms.date: 02/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 60b36e0ef6bb6c16979c9f0b0e1407e0b4631a2f
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="d2cf2-104">Porady: łączenie wielu ciągów (Przewodnik C#)</span><span class="sxs-lookup"><span data-stu-id="d2cf2-104">How to: Concatenate Multiple Strings (C# Guide)</span></span>

<span data-ttu-id="d2cf2-105">*Łączenie* to proces dołączania jeden ciąg do końca ciągu innego.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="d2cf2-106">Łączenie ciągów za pomocą `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="d2cf2-107">Literały ciągu i stałe typu string łączenia wystąpi w czasie kompilacji; występuje, nie łączenia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="d2cf2-108">Dla zmiennych ciągu łączenia występuje tylko w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="d2cf2-109">W poniższym przykładzie użyto łączenia, aby podzielić ciąg literału na mniejsze ciągów w celu zwiększenia czytelności w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="d2cf2-110">Te elementy są połączone w jeden ciąg w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="d2cf2-111">Nie ma żadnych kosztów wydajności w czasie wykonywania, niezależnie od liczby ciągów związane.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

<span data-ttu-id="d2cf2-112">Aby połączyć zmiennych ciągu można użyć `+` lub `+=` operatorów, [ciągu interpolacji](../tutorials/string-interpolation.md) lub <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../tutorials/string-interpolation.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="d2cf2-113">`+` Operator jest łatwy w użyciu i sprawia, że dla intuicyjne kodu.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="d2cf2-114">Nawet jeśli użyć kilku `+` operatory w jednej instrukcji, ciąg zawartości jest kopiowany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="d2cf2-115">Poniższy kod przedstawia przykłady użycia `+` i `+=` operatorom ciągów:</span><span class="sxs-lookup"><span data-stu-id="d2cf2-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="d2cf2-116">W niektórych wyrażeniach łatwiej ciągów za pomocą ciągu interpolacji, jak przedstawiono na poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="d2cf2-116">In some expressions, it is easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  <span data-ttu-id="d2cf2-117">W operacji łączenia ciągu kompilator języka C# traktuje pusty ciąg takie same jako ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="d2cf2-118">Innej metody do ciągów jest <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d2cf2-119">Ta metoda działa również w przypadku, gdy tworzysz ciąg z małą liczbą ciągów składnika.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="d2cf2-120">W innych przypadkach może być łączenie ciągów w pętli, których nie wiadomo, ile parametry źródła są łączenie i rzeczywistą liczbę ciągów źródło może być dość duży.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-120">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="d2cf2-121"><xref:System.Text.StringBuilder> Klasy zostało zaprojektowane na potrzeby tych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="d2cf2-122">Poniższy kod używa <xref:System.Text.StringBuilder.Append%2A> metody <xref:System.Text.StringBuilder> klasy do ciągów.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="d2cf2-123">Możesz przeczytać dodatkowe informacje [powodów przemawiających ciągów lub `StringBuilder` — klasa](xref:System.Text.StringBuilder#StringAndSB)</span><span class="sxs-lookup"><span data-stu-id="d2cf2-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB)</span></span>

<span data-ttu-id="d2cf2-124">Inną opcją sprzęgać ciągów z kolekcji jest użycie <xref:System.String.Concat%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d2cf2-125">Użyj <xref:System.String.Join%2A?displayProperty=nameWithType> metodę, jeśli parametry źródła powinny być oddzielone delimeter.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimeter.</span></span> <span data-ttu-id="d2cf2-126">Poniższy kod łączy tablicę wyrazy przy użyciu obu metod:</span><span class="sxs-lookup"><span data-stu-id="d2cf2-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="d2cf2-127">Ostatnio, można użyć [LINQ](../programming-guide/concepts/linq/index.md) i <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metody przyłączania ciągów z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="d2cf2-128">Ta metoda łączy ciągów źródło, za pomocą wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="d2cf2-129">Wyrażenia lambda wykonuje pracę można dodać każdego ciągu do gromadzenia istniejących.</span><span class="sxs-lookup"><span data-stu-id="d2cf2-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="d2cf2-130">Poniższy przykład łączy Tablica słów przez dodanie odstępów między wyrazami w tablicy:</span><span class="sxs-lookup"><span data-stu-id="d2cf2-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  


## <a name="see-also"></a><span data-ttu-id="d2cf2-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2cf2-131">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="d2cf2-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d2cf2-132">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="d2cf2-133">Ciągi</span><span class="sxs-lookup"><span data-stu-id="d2cf2-133">Strings</span></span>](../programming-guide/strings/index.md)
