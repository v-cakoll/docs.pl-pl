---
title: LINQ i ciągi (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: b805bc7318b8c5fe70ab1c060d1058a6bbc4f177
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635538"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="24bf6-102">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="24bf6-102">LINQ and strings (C#)</span></span>

<span data-ttu-id="24bf6-103">LINQ może służyć do wykonywania zapytań i przekształcania ciągów i kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="24bf6-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="24bf6-104">Może to być szczególnie przydatne w przypadku danych częściowo strukturalnych w plikach tekstowych.</span><span class="sxs-lookup"><span data-stu-id="24bf6-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="24bf6-105">Zapytania LINQ można łączyć z tradycyjnymi funkcjami ciągu i wyrażeniami regularnymi.</span><span class="sxs-lookup"><span data-stu-id="24bf6-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="24bf6-106">Na przykład można użyć <xref:System.String.Split%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> lub metody, aby utworzyć tablicę ciągów, które następnie kwerendy lub modyfikowane przy użyciu LINQ.</span><span class="sxs-lookup"><span data-stu-id="24bf6-106">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="24bf6-107">Można użyć <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metody w `where` klauzuli kwerendy LINQ.</span><span class="sxs-lookup"><span data-stu-id="24bf6-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="24bf6-108">I można użyć LINQ do <xref:System.Text.RegularExpressions.MatchCollection> kwerendy lub zmodyfikować wyniki zwrócone przez wyrażenie regularne.</span><span class="sxs-lookup"><span data-stu-id="24bf6-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="24bf6-109">Można również użyć technik opisanych w tej sekcji, aby przekształcić dane tekstu częściowo strukturalnego do XML.</span><span class="sxs-lookup"><span data-stu-id="24bf6-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="24bf6-110">Aby uzyskać więcej informacji, zobacz [Jak wygenerować kod XML z plików CSV](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="24bf6-110">For more information, see [How to generate XML from CSV files](how-to-generate-xml-from-csv-files.md).</span></span>

<span data-ttu-id="24bf6-111">Przykłady w tej sekcji dzielą się na dwie kategorie:</span><span class="sxs-lookup"><span data-stu-id="24bf6-111">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="24bf6-112">Wykonywanie zapytań dotyczących bloku tekstu</span><span class="sxs-lookup"><span data-stu-id="24bf6-112">Querying a block of text</span></span>

<span data-ttu-id="24bf6-113">Można wysyłać zapytania, analizować i modyfikować bloki tekstowe, dzieląc je na <xref:System.String.Split%2A?displayProperty=nameWithType> tablicę <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> mniejszych ciągów z możliwością wykonywania zapytań przy użyciu metody lub metody.</span><span class="sxs-lookup"><span data-stu-id="24bf6-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="24bf6-114">Tekst źródłowy można podzielić na słowa, zdania, akapity, strony lub inne kryteria, a następnie wykonać dodatkowe podziały, jeśli są one wymagane w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="24bf6-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="24bf6-115">Jak zliczać wystąpienia wyrazu w ciągu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="24bf6-115">How to count occurrences of a word in a string (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="24bf6-116">Pokazuje, jak używać LINQ do prostego wykonywania zapytań za pomocą tekstu.</span><span class="sxs-lookup"><span data-stu-id="24bf6-116">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="24bf6-117">Jak wysyłać zapytania do zdań zawierających określony zestaw słów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="24bf6-117">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="24bf6-118">Pokazuje, jak dzielić pliki tekstowe na dowolne granice i jak wykonywać kwerendy względem każdej części.</span><span class="sxs-lookup"><span data-stu-id="24bf6-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="24bf6-119">Jak wysyłać zapytania o znaki w ciągu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="24bf6-119">How to query for characters in a string (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="24bf6-120">Pokazuje, że ciąg jest typem podlegającym zapytań.</span><span class="sxs-lookup"><span data-stu-id="24bf6-120">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="24bf6-121">Jak połączyć zapytania LINQ z wyrażeniami regularnymi (C#)</span><span class="sxs-lookup"><span data-stu-id="24bf6-121">How to combine LINQ queries with regular expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="24bf6-122">Pokazuje, jak używać wyrażeń regularnych w kwerendach LINQ do dopasowywania wzorców złożonych w wynikach filtrowanych kwerend.</span><span class="sxs-lookup"><span data-stu-id="24bf6-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="24bf6-123">Wykonywanie zapytań dotyczących danych częściowo strukturalnych w formacie tekstowym</span><span class="sxs-lookup"><span data-stu-id="24bf6-123">Querying semi-structured data in text format</span></span>

<span data-ttu-id="24bf6-124">Wiele różnych typów plików tekstowych składa się z serii linii, często z podobnym formatowaniem, takich jak pliki rozdzielane za pomocą kart lub przecinków lub linie o stałej długości.</span><span class="sxs-lookup"><span data-stu-id="24bf6-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="24bf6-125">Po przeczytaniu takiego pliku tekstowego w pamięci, można użyć LINQ do kwerendy i /lub zmodyfikować wiersze.</span><span class="sxs-lookup"><span data-stu-id="24bf6-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="24bf6-126">Zapytania LINQ również uprościć zadanie łączenia danych z wielu źródeł.</span><span class="sxs-lookup"><span data-stu-id="24bf6-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="24bf6-127">Jak znaleźć różnicę między dwiema listami (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="24bf6-127">How to find the set difference between two lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="24bf6-128">Pokazuje, jak znaleźć wszystkie ciągi, które są obecne na jednej liście, ale nie inne.</span><span class="sxs-lookup"><span data-stu-id="24bf6-128">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="24bf6-129">Jak sortować lub filtrować dane tekstowe według dowolnego wyrazu lub pola (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="24bf6-129">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="24bf6-130">Pokazuje sposób sortowania wierszy tekstu na podstawie dowolnego wyrazu lub pola.</span><span class="sxs-lookup"><span data-stu-id="24bf6-130">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="24bf6-131">Jak ponownie uporządkować pola rozdzielonego pliku (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="24bf6-131">How to reorder the fields of a delimited file (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="24bf6-132">Pokazuje, jak uporządkować pola w wierszu w pliku csv.</span><span class="sxs-lookup"><span data-stu-id="24bf6-132">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="24bf6-133">Jak łączyć i porównywać kolekcje ciągów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="24bf6-133">How to combine and compare string collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="24bf6-134">Pokazuje, jak łączyć listy ciągów na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="24bf6-134">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="24bf6-135">Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="24bf6-135">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="24bf6-136">Pokazuje, jak tworzyć kolekcje obiektów przy użyciu wielu plików tekstowych jako źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="24bf6-136">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="24bf6-137">Jak dołączyć zawartość z różnych plików (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="24bf6-137">How to join content from dissimilar files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="24bf6-138">Pokazuje, jak połączyć ciągi ciągów na dwóch listach w jeden ciąg za pomocą pasującego klucza.</span><span class="sxs-lookup"><span data-stu-id="24bf6-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="24bf6-139">Jak podzielić plik na wiele plików przy użyciu grup (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="24bf6-139">How to split a file into many files by using groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="24bf6-140">Pokazuje, jak tworzyć nowe pliki przy użyciu pojedynczego pliku jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="24bf6-140">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="24bf6-141">Jak obliczyć wartości kolumn w pliku tekstowym CSV (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="24bf6-141">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="24bf6-142">Pokazuje, jak wykonywać obliczenia matematyczne na danych tekstowych w plikach csv.</span><span class="sxs-lookup"><span data-stu-id="24bf6-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="24bf6-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24bf6-143">See also</span></span>

- [<span data-ttu-id="24bf6-144">Zapytanie zintegrowane z językiem (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="24bf6-144">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="24bf6-145">Generowanie kodu XML z plików CSV</span><span class="sxs-lookup"><span data-stu-id="24bf6-145">How to generate XML from CSV files</span></span>](how-to-generate-xml-from-csv-files.md)
