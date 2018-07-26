---
title: 'Porady: analizowanie ciągów za pomocą funkcji String.Split (Przewodnik C#)'
description: Funkcji String.Split zwraca tablicę ciągów podzielona z zestawu ograniczników. To łatwe analizowanie ciągów.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: e2d788b27f54ac068922f0ebe558a2aea8a475ca
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960013"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="9b480-104">Porady: analizowanie ciągów za pomocą funkcji String.Split (Przewodnik C#)</span><span class="sxs-lookup"><span data-stu-id="9b480-104">How to: Parse Strings Using String.Split (C# Guide)</span></span>

<span data-ttu-id="9b480-105"><xref:System.String.Split%2A?displayProperty=nameWithType> Metoda tworzy tablicę podciągów, dzieląc oparte na co najmniej jeden ograniczników ciągu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="9b480-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="9b480-106">Często jest najłatwiejszym sposobem rozdzielenia ciągu na granicach słów.</span><span class="sxs-lookup"><span data-stu-id="9b480-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="9b480-107">Również służy do dzielenia ciągów na inne określone znaki lub ciągi znaków.</span><span class="sxs-lookup"><span data-stu-id="9b480-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="9b480-108">Poniższy kod dzieli popularnych na tablicę ciągów dla każdego wyrazu.</span><span class="sxs-lookup"><span data-stu-id="9b480-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="9b480-109">Każde wystąpienie znak separatora tworzy wartości zwróconej tablicy.</span><span class="sxs-lookup"><span data-stu-id="9b480-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="9b480-110">Następujące po sobie separatory dawać pusty ciąg jako wartość zwracana tablica.</span><span class="sxs-lookup"><span data-stu-id="9b480-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="9b480-111">Widać to w poniższym przykładzie, wykorzystuje miejsce jako separatora:</span><span class="sxs-lookup"><span data-stu-id="9b480-111">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="9b480-112">To zachowanie ułatwia w przypadku formatów takich jak pliki wartości (CSV) rozdzielonych przecinkami reprezentująca dane tabelaryczne.</span><span class="sxs-lookup"><span data-stu-id="9b480-112">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="9b480-113">Kolejne przecinkami reprezentują pustej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="9b480-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="9b480-114">Możesz przekazać opcjonalny <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametru, aby wykluczyć wszelkie puste ciągi w zwróconej tablicy.</span><span class="sxs-lookup"><span data-stu-id="9b480-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="9b480-115">W przypadku bardziej skomplikowanych przetwarzania zwrócona kolekcja, można użyć [LINQ](../programming-guide/concepts/linq/index.md) do manipulowania sekwencji wynik.</span><span class="sxs-lookup"><span data-stu-id="9b480-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>    

<span data-ttu-id="9b480-116"><xref:System.String.Split%2A?displayProperty=nameWithType> można użyć wielu znaków separatora.</span><span class="sxs-lookup"><span data-stu-id="9b480-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span> <span data-ttu-id="9b480-117">W poniższym przykładzie użyto miejsca do magazynowania, przecinki, kropki, dwukropki i kartach wszystkich przekazanych tablicę zawierającą je do oddzielania znaków, <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="9b480-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>  <span data-ttu-id="9b480-118">Pętla w dolnej części kodu wyświetla poszczególnych wyrazów w zwróconej tablicy.</span><span class="sxs-lookup"><span data-stu-id="9b480-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="9b480-119">Kolejne wystąpienia dowolnego separator dawać pusty ciąg w tablicy danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="9b480-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="9b480-120"><xref:System.String.Split%2A?displayProperty=nameWithType> może to potrwać tablicę ciągów (sekwencje znaków, które działają jako separatorów podczas analizowania ciągu docelowego, a nie pojedyncze znaki).</span><span class="sxs-lookup"><span data-stu-id="9b480-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="9b480-121">Możesz wypróbować te przykłady, patrząc na kod w naszym [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span><span class="sxs-lookup"><span data-stu-id="9b480-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="9b480-122">Można również pobrać przykłady [jako plik zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span><span class="sxs-lookup"><span data-stu-id="9b480-122">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="9b480-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b480-123">See Also</span></span>  
 [<span data-ttu-id="9b480-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9b480-124">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="9b480-125">Ciągi</span><span class="sxs-lookup"><span data-stu-id="9b480-125">Strings</span></span>](../programming-guide/strings/index.md)  
 [<span data-ttu-id="9b480-126">Wyrażeń regularnych programu .NET</span><span class="sxs-lookup"><span data-stu-id="9b480-126">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
