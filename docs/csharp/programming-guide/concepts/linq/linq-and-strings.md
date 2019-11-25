---
title: LINQ i ciągi (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: fb1714c54331ead80cd28435cf3ed1c4c54a704e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140895"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="d2031-102">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="d2031-102">LINQ and strings (C#)</span></span>

<span data-ttu-id="d2031-103">LINQ może służyć do wykonywania zapytań i przekształcania ciągów i kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="d2031-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="d2031-104">Może być szczególnie przydatne w przypadku danych z częściową strukturą w plikach tekstowych.</span><span class="sxs-lookup"><span data-stu-id="d2031-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="d2031-105">Zapytania LINQ można łączyć z tradycyjnymi funkcjami ciągów i wyrażeniami regularnymi.</span><span class="sxs-lookup"><span data-stu-id="d2031-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="d2031-106">Na przykład można użyć metody <xref:System.String.Split%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>, aby utworzyć tablicę ciągów, które można następnie wykonać zapytania lub zmodyfikować przy użyciu LINQ.</span><span class="sxs-lookup"><span data-stu-id="d2031-106">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="d2031-107">Metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> można użyć w klauzuli `where` zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="d2031-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="d2031-108">I można użyć LINQ do zapytania lub zmodyfikować wyniki <xref:System.Text.RegularExpressions.MatchCollection> zwrócone przez wyrażenie regularne.</span><span class="sxs-lookup"><span data-stu-id="d2031-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="d2031-109">Można również użyć technik opisanych w tej sekcji, aby przekształcić dane z częściową strukturą do formatu XML.</span><span class="sxs-lookup"><span data-stu-id="d2031-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="d2031-110">Aby uzyskać więcej informacji, zobacz [How to: Generate XML from pliki CSV](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="d2031-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>

<span data-ttu-id="d2031-111">Przykłady w tej sekcji należą do dwóch kategorii:</span><span class="sxs-lookup"><span data-stu-id="d2031-111">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="d2031-112">Wykonywanie zapytania dotyczącego bloku tekstu</span><span class="sxs-lookup"><span data-stu-id="d2031-112">Querying a block of text</span></span>

<span data-ttu-id="d2031-113">Można wykonywać zapytania, analizować i modyfikować bloki tekstu, dzieląc je na tablicę Queryable mniejszych ciągów przy użyciu metody <xref:System.String.Split%2A?displayProperty=nameWithType> lub metody <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d2031-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d2031-114">Możesz podzielić tekst źródłowy na słowa, zdania, akapity, strony lub inne kryteria, a następnie wykonać dodatkowe podziały, jeśli są one wymagane w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="d2031-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="d2031-115">Jak zliczyć wystąpienia wyrazu w ciągu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d2031-115">How to count occurrences of a word in a string (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="d2031-116">Pokazuje, jak używać LINQ do prostego wykonywania zapytań względem tekstu.</span><span class="sxs-lookup"><span data-stu-id="d2031-116">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="d2031-117">Instrukcje: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d2031-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="d2031-118">Pokazuje sposób dzielenia plików tekstowych na dowolne granice oraz wykonywania zapytań dotyczących poszczególnych części.</span><span class="sxs-lookup"><span data-stu-id="d2031-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="d2031-119">Instrukcje: zapytanie o znaki w ciągu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d2031-119">How to: Query for Characters in a String (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="d2031-120">Pokazuje, że ciąg jest typem queryable.</span><span class="sxs-lookup"><span data-stu-id="d2031-120">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="d2031-121">Jak połączyć zapytania LINQ z wyrażeniami regularnymiC#()</span><span class="sxs-lookup"><span data-stu-id="d2031-121">How to combine LINQ queries with regular expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="d2031-122">Pokazuje, jak używać wyrażeń regularnych w zapytaniach LINQ dla złożonego dopasowania do wzorca na filtrowanych wynikach zapytań.</span><span class="sxs-lookup"><span data-stu-id="d2031-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="d2031-123">Wykonywanie zapytania dotyczącego danych z częściową strukturą w formacie tekstowym</span><span class="sxs-lookup"><span data-stu-id="d2031-123">Querying semi-structured data in text format</span></span>

<span data-ttu-id="d2031-124">Wiele różnych typów plików tekstowych składa się z szeregu wierszy, często z podobnym formatowaniem, takim jak pliki rozdzielane znakami tabulacji lub rozdzielonymi długościami.</span><span class="sxs-lookup"><span data-stu-id="d2031-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="d2031-125">Po przeczytaniu takiego pliku tekstowego do pamięci można użyć LINQ do wykonywania zapytań i/lub modyfikowania wierszy.</span><span class="sxs-lookup"><span data-stu-id="d2031-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="d2031-126">Zapytania LINQ upraszczają także zadanie łączenia danych z wielu źródeł.</span><span class="sxs-lookup"><span data-stu-id="d2031-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="d2031-127">Instrukcje: Wyszukiwanie zestawu różnic między dwoma listami (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d2031-127">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="d2031-128">Pokazuje, jak znaleźć wszystkie ciągi, które znajdują się na jednej liście, ale nie w drugim.</span><span class="sxs-lookup"><span data-stu-id="d2031-128">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="d2031-129">Instrukcje: sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d2031-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="d2031-130">Pokazuje, jak sortować wiersze tekstu na podstawie dowolnego wyrazu lub pola.</span><span class="sxs-lookup"><span data-stu-id="d2031-130">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="d2031-131">Instrukcje: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d2031-131">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="d2031-132">Pokazuje, jak zmienić kolejność pól w wierszu w pliku CSV.</span><span class="sxs-lookup"><span data-stu-id="d2031-132">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="d2031-133">Instrukcje: łączenie i porównywanie kolekcji ciągów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d2031-133">How to: combine and compare string collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="d2031-134">Pokazuje, jak łączyć listy ciągów na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="d2031-134">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="d2031-135">Instrukcje: wypełnianie kolekcji obiektów z wielu źródeł (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="d2031-135">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="d2031-136">Pokazuje, jak tworzyć kolekcje obiektów przy użyciu wielu plików tekstowych jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="d2031-136">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="d2031-137">Instrukcje: dołączanie zawartości z niepodobnych plików (LINQC#) ()</span><span class="sxs-lookup"><span data-stu-id="d2031-137">How to: Join Content from Dissimilar Files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="d2031-138">Pokazuje, w jaki sposób połączyć ciągi w dwóch listach w jeden ciąg za pomocą pasującego klucza.</span><span class="sxs-lookup"><span data-stu-id="d2031-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="d2031-139">Instrukcje: dzielenie pliku na wiele plików przy użyciu grup (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d2031-139">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="d2031-140">Pokazuje, jak tworzyć nowe pliki przy użyciu pojedynczego pliku jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="d2031-140">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="d2031-141">Jak obliczyć wartości kolumn w pliku tekstowym CSV (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d2031-141">How to compute column values in a CSV text file (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="d2031-142">Pokazuje, jak wykonywać obliczenia matematyczne na danych tekstowych w plikach CSV.</span><span class="sxs-lookup"><span data-stu-id="d2031-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2031-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2031-143">See also</span></span>

- [<span data-ttu-id="d2031-144">Zapytanie zintegrowane z językiem (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="d2031-144">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="d2031-145">Instrukcje: generowanie kodu XML z plików CSV</span><span class="sxs-lookup"><span data-stu-id="d2031-145">How to: Generate XML from CSV Files</span></span>](how-to-generate-xml-from-csv-files.md)
