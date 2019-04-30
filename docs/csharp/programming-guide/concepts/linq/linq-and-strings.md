---
title: LINQ i ciągi (C#)
ms.date: 07/20/2015
ms.assetid: dbe2d657-b3f3-487e-b645-21fb2d71cd7b
ms.openlocfilehash: c7a1b86cc611d5f38ceab814b4594f5ad953fbc4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667408"
---
# <a name="linq-and-strings-c"></a><span data-ttu-id="52a46-102">LINQ i ciągi (C#)</span><span class="sxs-lookup"><span data-stu-id="52a46-102">LINQ and strings (C#)</span></span>

<span data-ttu-id="52a46-103">LINQ mogą służyć do wykonywania zapytań i przekształcanie ciągów i zbiorów ciągów.</span><span class="sxs-lookup"><span data-stu-id="52a46-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="52a46-104">Może być szczególnie przydatne w przypadku danych z częściową strukturą w plikach tekstowych.</span><span class="sxs-lookup"><span data-stu-id="52a46-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="52a46-105">Zapytania LINQ można łączyć z funkcji tradycyjnego ciągów i wyrażeń regularnych.</span><span class="sxs-lookup"><span data-stu-id="52a46-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="52a46-106">Na przykład, można użyć <xref:System.String.Split%2A?displayProperty=nameWithType> lub <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> metodę, aby utworzyć tablicę ciągów, które można zbadać lub zmodyfikować za pomocą LINQ.</span><span class="sxs-lookup"><span data-stu-id="52a46-106">For example, you can use the <xref:System.String.Split%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="52a46-107">Możesz użyć <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in Class metoda `where` klauzula zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="52a46-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="52a46-108">I LINQ umożliwia zapytania lub zmodyfikować <xref:System.Text.RegularExpressions.MatchCollection> wyniki zwrócone przez wyrażenie regularne.</span><span class="sxs-lookup"><span data-stu-id="52a46-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>

<span data-ttu-id="52a46-109">Metod opisanych w tej sekcji służy również do przekształcania tekstu lub częściową strukturą danych do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="52a46-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="52a46-110">Aby uzyskać więcej informacji, zobacz [jak: Generowanie kodu XML z plików CSV](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="52a46-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>

<span data-ttu-id="52a46-111">Przykłady w tej sekcji można podzielić na dwie kategorie:</span><span class="sxs-lookup"><span data-stu-id="52a46-111">The examples in this section fall into two categories:</span></span>

## <a name="querying-a-block-of-text"></a><span data-ttu-id="52a46-112">Wykonywanie zapytań w bloku tekstu</span><span class="sxs-lookup"><span data-stu-id="52a46-112">Querying a block of text</span></span>

<span data-ttu-id="52a46-113">Zapytanie, analizowania i zmodyfikować bloków tekstu, dzieląc je na odpytywalny tablicę ciągów mniejszych przy użyciu <xref:System.String.Split%2A?displayProperty=nameWithType> metody lub <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="52a46-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A?displayProperty=nameWithType> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="52a46-114">Można podzielić tekst źródłowy słów, zdań, akapitów, stron lub innych kryteriów, a następnie wykonać dodatkowe dzieli dane, jeśli są one wymagane w kwerendzie.</span><span class="sxs-lookup"><span data-stu-id="52a46-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>

- [<span data-ttu-id="52a46-115">Instrukcje: Liczenie wystąpień wyrazu w ciągu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="52a46-115">How to: Count Occurrences of a Word in a String (LINQ) (C#)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  <span data-ttu-id="52a46-116">Pokazuje, jak używać programu LINQ do wykonywania prostych zapytań nad tekstem.</span><span class="sxs-lookup"><span data-stu-id="52a46-116">Shows how to use LINQ for simple querying over text.</span></span>

- [<span data-ttu-id="52a46-117">Instrukcje: Zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="52a46-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  <span data-ttu-id="52a46-118">Pokazuje, jak podzielić pliki tekstowe na odgórnych ograniczeń i poznać sposoby wykonywania zapytań względem każdej części.</span><span class="sxs-lookup"><span data-stu-id="52a46-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>

- [<span data-ttu-id="52a46-119">Instrukcje: Zapytanie o znaki w ciągu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="52a46-119">How to: Query for Characters in a String (LINQ) (C#)</span></span>](how-to-query-for-characters-in-a-string-linq.md)

  <span data-ttu-id="52a46-120">Pokazuje, czy ciąg jest typem odpytywalnym.</span><span class="sxs-lookup"><span data-stu-id="52a46-120">Demonstrates that a string is a queryable type.</span></span>

- [<span data-ttu-id="52a46-121">Instrukcje: Łączenie zapytań LINQ z wyrażeniami regularnymi (C#)</span><span class="sxs-lookup"><span data-stu-id="52a46-121">How to: Combine LINQ Queries with Regular Expressions (C#)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)

  <span data-ttu-id="52a46-122">Pokazuje, jak używać wyrażeń regularnych w zapytaniach LINQ dla złożonych dopasowania do wzorca w wynikach zapytania filtrowanego.</span><span class="sxs-lookup"><span data-stu-id="52a46-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>

## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="52a46-123">Podczas badania częściowo ustrukturyzowanych danych w formacie tekstowym</span><span class="sxs-lookup"><span data-stu-id="52a46-123">Querying semi-structured data in text format</span></span>

<span data-ttu-id="52a46-124">Wiele różnych typów plików tekstowych składają się z szeregu wiersze, często z podobnego formatowania, takie jak karty lub przecinkami pliki lub wiersze o stałej długości.</span><span class="sxs-lookup"><span data-stu-id="52a46-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="52a46-125">Po przeczytaniu pliku tekstowego do pamięci można użyć LINQ do zapytań i/lub modyfikowania wierszy.</span><span class="sxs-lookup"><span data-stu-id="52a46-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="52a46-126">Zapytania LINQ również uprościć zadanie połączenie danych z wielu źródeł.</span><span class="sxs-lookup"><span data-stu-id="52a46-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>

- [<span data-ttu-id="52a46-127">Instrukcje: Wyszukiwanie zestawu różnic między dwoma listami (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="52a46-127">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)

  <span data-ttu-id="52a46-128">Pokazuje, jak znaleźć wszystkie ciągi, które znajdują się w jednej liście, ale nie drugiej.</span><span class="sxs-lookup"><span data-stu-id="52a46-128">Shows how to find all the strings that are present in one list but not the other.</span></span>

- [<span data-ttu-id="52a46-129">Instrukcje: Sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="52a46-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  <span data-ttu-id="52a46-130">Pokazuje sposób sortowania wierszy tekstu, w oparciu o dowolnego słowa lub pola.</span><span class="sxs-lookup"><span data-stu-id="52a46-130">Shows how to sort text lines based on any word or field.</span></span>

- [<span data-ttu-id="52a46-131">Instrukcje: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="52a46-131">How to: Reorder the Fields of a Delimited File (LINQ) (C#)</span></span>](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  <span data-ttu-id="52a46-132">Pokazuje, jak zmienianie kolejności pól w wierszu w pliku CSV.</span><span class="sxs-lookup"><span data-stu-id="52a46-132">Shows how to reorder fields in a line in a .csv file.</span></span>

- [<span data-ttu-id="52a46-133">Instrukcje: Łączenie i porównywanie kolekcji ciągów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="52a46-133">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](how-to-combine-and-compare-string-collections-linq.md)

  <span data-ttu-id="52a46-134">Pokazuje, jak łączyć listy parametrów na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="52a46-134">Shows how to combine string lists in various ways.</span></span>

- [<span data-ttu-id="52a46-135">Instrukcje: Wypełnianie kolekcji Object z wielu źródeł (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="52a46-135">How to: Populate Object Collections from Multiple Sources (LINQ) (C#)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)

  <span data-ttu-id="52a46-136">Pokazuje, jak tworzyć kolekcje obiektów przy użyciu wielu plików tekstowych jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="52a46-136">Shows how to create object collections by using multiple text files as data sources.</span></span>

- [<span data-ttu-id="52a46-137">Instrukcje: Łączenie zawartości niepodobnych plików (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="52a46-137">How to: Join Content from Dissimilar Files (LINQ) (C#)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)
  
  <span data-ttu-id="52a46-138">Pokazuje, jak połączyć dwie listy ciągów w jeden ciąg przy użyciu zgodnego klucza.</span><span class="sxs-lookup"><span data-stu-id="52a46-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>

- [<span data-ttu-id="52a46-139">Instrukcje: Dzielenie pliku na kilka plików za pomocą grup (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="52a46-139">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  <span data-ttu-id="52a46-140">Pokazuje, jak utworzyć nowe pliki przy użyciu pojedynczego pliku jako źródło danych.</span><span class="sxs-lookup"><span data-stu-id="52a46-140">Shows how to create new files by using a single file as a data source.</span></span>

- [<span data-ttu-id="52a46-141">Instrukcje: Obliczanie wartości kolumn w pliku tekstowym CSV (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="52a46-141">How to: Compute Column Values in a CSV Text File (LINQ) (C#)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  <span data-ttu-id="52a46-142">Pokazuje sposób wykonywania obliczeń matematycznych na danych tekstu w plikach CSV.</span><span class="sxs-lookup"><span data-stu-id="52a46-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>

## <a name="see-also"></a><span data-ttu-id="52a46-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52a46-143">See also</span></span>

- [<span data-ttu-id="52a46-144">Zapytanie o języku zintegrowanym (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="52a46-144">Language-Integrated Query (LINQ) (C#)</span></span>](index.md)
- [<span data-ttu-id="52a46-145">Instrukcje: Generowanie kodu XML z plików CSV</span><span class="sxs-lookup"><span data-stu-id="52a46-145">How to: Generate XML from CSV Files</span></span>](how-to-generate-xml-from-csv-files.md)
