---
title: "Porady: analizowanie ciągów za pomocą String.Split (Przewodnik C#)"
description: "String.Split zwraca tablicę ciągów podzielić z zestawu ograniczników. Jest łatwy sposób analizowanie ciągów."
ms.date: 01/03/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
author: BillWagner
ms.author: wiwagn
ms.custom: mvc
ms.openlocfilehash: 30b16ce5c263221fe917b3d6f289fea20d47b584
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="642ee-104">Porady: analizowanie ciągów za pomocą String.Split (Przewodnik C#)</span><span class="sxs-lookup"><span data-stu-id="642ee-104">How to: Parse Strings Using String.Split (C# Guide)</span></span>

<span data-ttu-id="642ee-105"><xref:System.String.Split%2A?displayProperty=nameWithType> Metoda tworzy tablicę podciągów dzieląc oparte na co najmniej jeden Ogranicznik ciągu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="642ee-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="642ee-106">Często jest najprostszym sposobem oddzielnych ciąg na granice programu word.</span><span class="sxs-lookup"><span data-stu-id="642ee-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="642ee-107">Służy również do dzielenie ciągów na inne określonych znaków lub ciągów.</span><span class="sxs-lookup"><span data-stu-id="642ee-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="642ee-108">Poniższy kod dzieli popularnych na tablicę ciągów dla każdego wyrazu.</span><span class="sxs-lookup"><span data-stu-id="642ee-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="642ee-109">Każde wystąpienie znak separatora daje wartość zwracana tablica.</span><span class="sxs-lookup"><span data-stu-id="642ee-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="642ee-110">Kolejne separatory utworzyć pusty ciąg jako wartość zwracana tablica.</span><span class="sxs-lookup"><span data-stu-id="642ee-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="642ee-111">W poniższym przykładzie, który używa miejsca jako separator można wyświetlić to:</span><span class="sxs-lookup"><span data-stu-id="642ee-111">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="642ee-112">To zachowanie ułatwia formatów takich jak pliki wartości (CSV) rozdzielonych przecinkami reprezentująca danych tabelarycznych.</span><span class="sxs-lookup"><span data-stu-id="642ee-112">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="642ee-113">Kolejne przecinkami reprezentuje pustą kolumnę.</span><span class="sxs-lookup"><span data-stu-id="642ee-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="642ee-114">Można przekazać opcjonalnie <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametr, aby wykluczyć wszystkie puste ciągi w zwróconej tablicy.</span><span class="sxs-lookup"><span data-stu-id="642ee-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="642ee-115">W przypadku bardziej skomplikowanych przetwarzania zwracana kolekcja, można użyć [LINQ](../programming-guide/concepts/linq/index.md) do manipulowania sekwencji wynik.</span><span class="sxs-lookup"><span data-stu-id="642ee-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>    

<span data-ttu-id="642ee-116"><xref:System.String.Split%2A?displayProperty=nameWithType> można użyć wielu znaków separatora.</span><span class="sxs-lookup"><span data-stu-id="642ee-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span> <span data-ttu-id="642ee-117">W poniższym przykładzie użyto spacji, przecinków okresów, dwukropki i karty, wszystkie przekazano tablicę zawierającą je do oddzielania znaków, <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="642ee-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>  <span data-ttu-id="642ee-118">Pętla w dolnej części kodu wyświetla poszczególnych wyrazów w zwróconej tablicy.</span><span class="sxs-lookup"><span data-stu-id="642ee-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="642ee-119">Kolejne wystąpienia dowolnego separatora utworzyć pusty ciąg na tablicę danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="642ee-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="642ee-120"><xref:System.String.Split%2A?displayProperty=nameWithType> możliwe jest tablicą ciągów (sekwencji znaków, które działają jako separatorów do analizowania parametrów docelowej, zamiast pojedynczy znaki).</span><span class="sxs-lookup"><span data-stu-id="642ee-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="642ee-121">Możesz spróbować te przykłady, sprawdzając kod w naszym [repozytorium GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)</span><span class="sxs-lookup"><span data-stu-id="642ee-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)</span></span>

## <a name="see-also"></a><span data-ttu-id="642ee-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="642ee-122">See Also</span></span>  
 [<span data-ttu-id="642ee-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="642ee-123">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="642ee-124">Ciągi</span><span class="sxs-lookup"><span data-stu-id="642ee-124">Strings</span></span>](../programming-guide/strings/index.md)  
 [<span data-ttu-id="642ee-125">Wyrażeń regularnych programu .NET</span><span class="sxs-lookup"><span data-stu-id="642ee-125">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
