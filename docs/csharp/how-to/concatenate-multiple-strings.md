---
title: "Porady: łączenie wielu ciągów (Przewodnik C#)"
description: "Istnieje wiele sposobów łączenia ciągów w języku C#. Poznaj opcje i przyczynami różne opcje."
ms.date: 01/11/2018
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
ms.openlocfilehash: a4bc5e04edba48065746b96841b628ec5843c5e9
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="5fae6-104">Porady: łączenie wielu ciągów (Przewodnik C#)</span><span class="sxs-lookup"><span data-stu-id="5fae6-104">How to: Concatenate Multiple Strings (C# Guide)</span></span>

<span data-ttu-id="5fae6-105">*Łączenie* to proces dołączania jeden ciąg do końca ciągu innego.</span><span class="sxs-lookup"><span data-stu-id="5fae6-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="5fae6-106">Łączenie ciągów za pomocą operatora +.</span><span class="sxs-lookup"><span data-stu-id="5fae6-106">You concatenate strings by using the + operator.</span></span> <span data-ttu-id="5fae6-107">Literały ciągu i stałe typu string łączenia wystąpi w czasie kompilacji; występuje, nie łączenia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5fae6-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="5fae6-108">Dla zmiennych ciągu łączenia występuje tylko w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5fae6-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="5fae6-109">W poniższym przykładzie użyto łączenia, aby podzielić ciąg literału na mniejsze ciągów w celu zwiększenia czytelności w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="5fae6-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="5fae6-110">Te elementy zostaną połączone w jeden ciąg w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5fae6-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="5fae6-111">Nie ma żadnych kosztów wydajności w czasie wykonywania, niezależnie od liczby ciągów związane.</span><span class="sxs-lookup"><span data-stu-id="5fae6-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

<span data-ttu-id="5fae6-112">Aby połączyć zmiennych ciągu można użyć `+` lub `+=` operatorów, [ciągu interpolacji](../tutorials/string-interpolation.md) lub <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="5fae6-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../tutorials/string-interpolation.md) or the <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="5fae6-113">`+` Operator jest łatwy w użyciu i sprawia, że dla intuicyjne kodu.</span><span class="sxs-lookup"><span data-stu-id="5fae6-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="5fae6-114">Nawet jeśli używasz kilka + operatory w jednej instrukcji, ciąg zawartości jest kopiowany tylko raz.</span><span class="sxs-lookup"><span data-stu-id="5fae6-114">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="5fae6-115">Poniższy kod przedstawia dwa przykłady użycia `+` operatora łączenia ciągów:</span><span class="sxs-lookup"><span data-stu-id="5fae6-115">The following code shows two examples of using the `+` operator to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="5fae6-116">W niektórych wyrażeniach łatwiej ciągów za pomocą ciągu interpolacji, jak przedstawiono na poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="5fae6-116">In some expressions, it is easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  <span data-ttu-id="5fae6-117">W operacji łączenia ciągu kompilator języka C# traktuje pusty ciąg takie same jako ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="5fae6-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="5fae6-118">Inne metody do ciągów <xref:System.String.Concat%2A?displayProperty=nameWithType> i <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5fae6-118">Other methods to concatenate strings are <xref:System.String.Concat%2A?displayProperty=nameWithType> and <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5fae6-119">Te metody działa dobrze, podczas tworzenia ciągu z niewielkiej liczby składników ciągów.</span><span class="sxs-lookup"><span data-stu-id="5fae6-119">These methods work well when you are building a string from a small number of component strings.</span></span> <span data-ttu-id="5fae6-120">Te methdos są także doskonałym wyborem znać numer ciągów, które składają się z połączony ciąg.</span><span class="sxs-lookup"><span data-stu-id="5fae6-120">These methdos are also a great choice when you know the number of strings that make up your concatenated string.</span></span>

<span data-ttu-id="5fae6-121">W innych przypadkach może być łączenie ciągów w pętli, których nie wiadomo, ile parametry źródła są łączenie i rzeczywistą liczbę ciągów źródło może być dość duży.</span><span class="sxs-lookup"><span data-stu-id="5fae6-121">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="5fae6-122"><xref:System.Text.StringBuilder> Klasy zostało zaprojektowane na potrzeby tych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="5fae6-122">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="5fae6-123">Poniższy kod używa <xref:System.Text.StringBuilder.Append%2A> metody <xref:System.Text.StringBuilder> klasy do ciągów.</span><span class="sxs-lookup"><span data-stu-id="5fae6-123">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="5fae6-124">Możesz przeczytać dodatkowe informacje [powodów przemawiających ciągów lub `StringBuilder` — klasa](xref:System.Text.StringBuilder#StringAndSB)</span><span class="sxs-lookup"><span data-stu-id="5fae6-124">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB)</span></span>

<span data-ttu-id="5fae6-125">Inną opcją sprzęgać ciągów z kolekcji jest użycie [LINQ](../programming-guide/concepts/linq/index.md) i <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="5fae6-125">Another option to join strings from a collection is to use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5fae6-126">Ta metoda łączy ciągów źródło, za pomocą wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="5fae6-126">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="5fae6-127">Wyrażenia lambda wykonuje pracę można dodać każdego ciągu do gromadzenia istniejących.</span><span class="sxs-lookup"><span data-stu-id="5fae6-127">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="5fae6-128">Poniższy przykład łączy Tablica słów przez dodanie odstępów między wyrazami w tablicy:</span><span class="sxs-lookup"><span data-stu-id="5fae6-128">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]  


## <a name="see-also"></a><span data-ttu-id="5fae6-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5fae6-129">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="5fae6-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5fae6-130">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="5fae6-131">Ciągi</span><span class="sxs-lookup"><span data-stu-id="5fae6-131">Strings</span></span>](../programming-guide/strings/index.md)
