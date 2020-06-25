---
title: Analizowanie ciągów za pomocą ciągu. Split (Przewodnik C#)
description: Metoda Split zwraca tablicę ciągów podzieloną z zestawu ograniczników. Jest to prosty sposób, aby przeanalizować ciągi.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 7c5d8fa462775c6f3a9981693129997dda6c2286
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324144"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a><span data-ttu-id="340aa-104">Jak analizować ciągi przy użyciu ciągu. Split w C\#</span><span class="sxs-lookup"><span data-stu-id="340aa-104">How to parse strings using String.Split in C\#</span></span>

<span data-ttu-id="340aa-105"><xref:System.String.Split%2A?displayProperty=nameWithType>Metoda tworzy tablicę podciągów, dzieląc ciąg wejściowy na podstawie co najmniej jednego ogranicznika.</span><span class="sxs-lookup"><span data-stu-id="340aa-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="340aa-106">Ta metoda jest często najprostszym sposobem odseparowania ciągu na granicach wyrazów.</span><span class="sxs-lookup"><span data-stu-id="340aa-106">This method is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="340aa-107">Jest on również używany do dzielenia ciągów dla innych określonych znaków lub ciągów.</span><span class="sxs-lookup"><span data-stu-id="340aa-107">It's also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="340aa-108">Poniższy kod dzieli wspólną frazę na tablicę ciągów dla każdego wyrazu.</span><span class="sxs-lookup"><span data-stu-id="340aa-108">The following code splits a common phrase into an array of strings for each word.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

<span data-ttu-id="340aa-109">Każde wystąpienie znaku separatora generuje wartość w tablicy zwracanej.</span><span class="sxs-lookup"><span data-stu-id="340aa-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="340aa-110">Kolejne znaki separatora tworzą pusty ciąg jako wartość w zwróconej tablicy.</span><span class="sxs-lookup"><span data-stu-id="340aa-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span> <span data-ttu-id="340aa-111">Można zobaczyć, jak w poniższym przykładzie jest tworzony pusty ciąg, który używa znaku spacji jako separatora.</span><span class="sxs-lookup"><span data-stu-id="340aa-111">You can see how an empty string is created in the following example, which uses the space character as a separator.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

<span data-ttu-id="340aa-112">To zachowanie ułatwia formatowanie, takie jak pliki z wartościami rozdzielanymi przecinkami (CSV) reprezentujące dane tabelaryczne.</span><span class="sxs-lookup"><span data-stu-id="340aa-112">This behavior makes it easier for formats like comma-separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="340aa-113">Kolejne przecinki reprezentują pustą kolumnę.</span><span class="sxs-lookup"><span data-stu-id="340aa-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="340aa-114">Można przekazać opcjonalny parametr, <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> Aby wykluczyć wszelkie puste ciągi w zwróconej tablicy.</span><span class="sxs-lookup"><span data-stu-id="340aa-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="340aa-115">Aby bardziej skomplikowane przetwarzanie zwróconej kolekcji było możliwe, można użyć [LINQ](../programming-guide/concepts/linq/index.md) do manipulowania sekwencją wyników.</span><span class="sxs-lookup"><span data-stu-id="340aa-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="340aa-116"><xref:System.String.Split%2A?displayProperty=nameWithType>może używać wielu znaków separatora.</span><span class="sxs-lookup"><span data-stu-id="340aa-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="340aa-117">Poniższy przykład używa spacji, przecinków, kropek, dwukropków i tabulatorów jako separatora znaków, które są przenoszone do <xref:System.String.Split%2A> tablicy.</span><span class="sxs-lookup"><span data-stu-id="340aa-117">The following example uses spaces, commas, periods, colons, and tabs as separating characters, which are passed to <xref:System.String.Split%2A> in an array .</span></span>
<span data-ttu-id="340aa-118">Pętla u dołu kodu wyświetla każdy wyraz w zwracanej tablicy.</span><span class="sxs-lookup"><span data-stu-id="340aa-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

<span data-ttu-id="340aa-119">Kolejne wystąpienia dowolnego separatora tworzą pusty ciąg w tablicy wyjściowej:</span><span class="sxs-lookup"><span data-stu-id="340aa-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<span data-ttu-id="340aa-120"><xref:System.String.Split%2A?displayProperty=nameWithType>może przyjmować tablicę ciągów (sekwencje znaków, które działają jako separatory do analizowania ciągu docelowego, zamiast pojedynczych znaków).</span><span class="sxs-lookup"><span data-stu-id="340aa-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a><span data-ttu-id="340aa-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="340aa-121">See also</span></span>

- [<span data-ttu-id="340aa-122">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="340aa-122">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="340aa-123">Ciągi</span><span class="sxs-lookup"><span data-stu-id="340aa-123">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="340aa-124">Wyrażenia regularne .NET</span><span class="sxs-lookup"><span data-stu-id="340aa-124">.NET regular expressions</span></span>](../../standard/base-types/regular-expressions.md)
