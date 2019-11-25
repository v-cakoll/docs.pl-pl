---
title: Jak analizować ciągi przy użyciu ciągu. Split (C# przewodnik)
description: Ciąg. Split zwraca tablicę ciągów podzieloną z zestawu ograniczników. Jest to prosty sposób, aby przeanalizować ciągi.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b46429f3b55658e1f2a7d21eed714c1d02236c57
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973232"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="d7545-104">Jak analizować ciągi przy użyciu ciągu. Split (C# przewodnik)</span><span class="sxs-lookup"><span data-stu-id="d7545-104">How to parse strings using String.Split (C# Guide)</span></span>

<span data-ttu-id="d7545-105">Metoda <xref:System.String.Split%2A?displayProperty=nameWithType> tworzy tablicę podciągów, dzieląc ciąg wejściowy na podstawie co najmniej jednego ogranicznika.</span><span class="sxs-lookup"><span data-stu-id="d7545-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="d7545-106">Często najprostszym sposobem jest oddzielenie ciągu od granic wyrazów.</span><span class="sxs-lookup"><span data-stu-id="d7545-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="d7545-107">Jest on również używany do dzielenia ciągów dla innych określonych znaków lub ciągów.</span><span class="sxs-lookup"><span data-stu-id="d7545-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="d7545-108">Poniższy kod dzieli wspólną frazę na tablicę ciągów dla każdego wyrazu.</span><span class="sxs-lookup"><span data-stu-id="d7545-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="d7545-109">Każde wystąpienie znaku separatora generuje wartość w tablicy zwracanej.</span><span class="sxs-lookup"><span data-stu-id="d7545-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="d7545-110">Kolejne znaki separatora tworzą pusty ciąg jako wartość w zwróconej tablicy.</span><span class="sxs-lookup"><span data-stu-id="d7545-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="d7545-111">Można to zobaczyć w poniższym przykładzie, który używa spacji jako separatora:</span><span class="sxs-lookup"><span data-stu-id="d7545-111">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="d7545-112">Takie zachowanie ułatwia korzystanie z formatów, takich jak pliki z wartościami rozdzielanymi przecinkami (CSV) reprezentujące dane tabelaryczne.</span><span class="sxs-lookup"><span data-stu-id="d7545-112">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="d7545-113">Kolejne przecinki reprezentują pustą kolumnę.</span><span class="sxs-lookup"><span data-stu-id="d7545-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="d7545-114">Można przekazać opcjonalny parametr <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType>, aby wykluczyć wszelkie puste ciągi w zwróconej tablicy.</span><span class="sxs-lookup"><span data-stu-id="d7545-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="d7545-115">Aby bardziej skomplikowane przetwarzanie zwróconej kolekcji było możliwe, można użyć [LINQ](../programming-guide/concepts/linq/index.md) do manipulowania sekwencją wyników.</span><span class="sxs-lookup"><span data-stu-id="d7545-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="d7545-116"><xref:System.String.Split%2A?displayProperty=nameWithType> może używać wielu znaków separatora.</span><span class="sxs-lookup"><span data-stu-id="d7545-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="d7545-117">W poniższym przykładzie są wykorzystywane spacje, przecinki, kropki, dwukropki i karty, wszystkie przechodzą do tablicy zawierającej te oddzielane znaki, do <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="d7545-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>
<span data-ttu-id="d7545-118">Pętla u dołu kodu wyświetla każdy wyraz w zwracanej tablicy.</span><span class="sxs-lookup"><span data-stu-id="d7545-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="d7545-119">Kolejne wystąpienia dowolnego separatora tworzą pusty ciąg w tablicy wyjściowej:</span><span class="sxs-lookup"><span data-stu-id="d7545-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="d7545-120"><xref:System.String.Split%2A?displayProperty=nameWithType> może pobrać tablicę ciągów (sekwencje znaków, które działają jako separatory do analizowania ciągu docelowego, zamiast pojedynczych znaków).</span><span class="sxs-lookup"><span data-stu-id="d7545-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="d7545-121">Możesz wypróbować te przykłady, przeglądając kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="d7545-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="d7545-122">Możesz też pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="d7545-122">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7545-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7545-123">See also</span></span>

- [<span data-ttu-id="d7545-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d7545-124">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="d7545-125">Ciągi</span><span class="sxs-lookup"><span data-stu-id="d7545-125">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="d7545-126">Wyrażenia regularne .NET</span><span class="sxs-lookup"><span data-stu-id="d7545-126">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
