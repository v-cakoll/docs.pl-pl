---
title: "LINQ i ciągi (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b615f3dc76d72e7f73146498e0143f88c52278a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="linq-and-strings-visual-basic"></a><span data-ttu-id="c8cd6-102">LINQ i ciągi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cd6-102">LINQ and Strings (Visual Basic)</span></span>
<span data-ttu-id="c8cd6-103">LINQ może służyć do wykonywania zapytań i przekształcanie ciągów i kolekcji ciągów.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-103">LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="c8cd6-104">Może być szczególnie przydatne w przypadku częściowo ustrukturyzowanych danych w plikach tekstowych.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-104">It can be especially useful with semi-structured data in text files.</span></span> <span data-ttu-id="c8cd6-105">Zapytania LINQ można łączyć z funkcje tradycyjnych ciągów i wyrażenia regularne.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-105">LINQ queries can be combined with traditional string functions and regular expressions.</span></span> <span data-ttu-id="c8cd6-106">Na przykład można użyć <xref:System.String.Split%2A> lub <xref:System.Text.RegularExpressions.Regex.Split%2A> metodę w celu utworzenia tablicy ciągów, które można zbadać lub zmodyfikować za pomocą LINQ.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-106">For example, you can use the <xref:System.String.Split%2A> or <xref:System.Text.RegularExpressions.Regex.Split%2A> method to create an array of strings that you can then query or modify by using LINQ.</span></span> <span data-ttu-id="c8cd6-107">Można użyć <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metoda `where` klauzuli zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-107">You can use the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method in the `where` clause of a LINQ query.</span></span> <span data-ttu-id="c8cd6-108">I użyj rozszerzenia LINQ, aby zapytań, lub zmodyfikuj <xref:System.Text.RegularExpressions.MatchCollection> wyników zwróconych w wyniku wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-108">And you can use LINQ to query or modify the <xref:System.Text.RegularExpressions.MatchCollection> results returned by a regular expression.</span></span>  
  
 <span data-ttu-id="c8cd6-109">Metod opisanych w tej sekcji służy również do przekształcania tekstu częściowo ustrukturyzowanych danych do formatu XML.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-109">You can also use the techniques described in this section to transform semi-structured text data to XML.</span></span> <span data-ttu-id="c8cd6-110">Aby uzyskać więcej informacji, zobacz [porady: generowanie XML z plików CSV](how-to-generate-xml-from-csv-files.md).</span><span class="sxs-lookup"><span data-stu-id="c8cd6-110">For more information, see [How to: Generate XML from CSV Files](how-to-generate-xml-from-csv-files.md).</span></span>  
  
 <span data-ttu-id="c8cd6-111">Przykłady w tej sekcji można podzielić na dwie kategorie:</span><span class="sxs-lookup"><span data-stu-id="c8cd6-111">The examples in this section fall into two categories:</span></span>  
  
## <a name="querying-a-block-of-text"></a><span data-ttu-id="c8cd6-112">Wykonywanie zapytania bloku tekstu</span><span class="sxs-lookup"><span data-stu-id="c8cd6-112">Querying a Block of Text</span></span>  
 <span data-ttu-id="c8cd6-113">Zapytanie, analizowanie i zmodyfikować bloków tekstu, podziel je na kolejność tablicę ciągów mniejszy przy użyciu <xref:System.String.Split%2A> metody lub <xref:System.Text.RegularExpressions.Regex.Split%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-113">You can query, analyze, and modify text blocks by splitting them into a queryable array of smaller strings by using the <xref:System.String.Split%2A> method or the <xref:System.Text.RegularExpressions.Regex.Split%2A> method.</span></span> <span data-ttu-id="c8cd6-114">Można podzielić tekst źródłowy słów, zdań, akapitów, stron lub innych kryteriów, a następnie wykonaj dodatkowych podziałów, jeśli są one wymagane w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-114">You can split the source text into words, sentences, paragraphs, pages, or any other criteria, and then perform additional splits if they are required in your query.</span></span>  
  
 [<span data-ttu-id="c8cd6-115">Porady: liczenie wystąpień słowa w ciągu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cd6-115">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 <span data-ttu-id="c8cd6-116">Przedstawia sposób użycia LINQ prostych zapytań nad tekstem.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-116">Shows how to use LINQ for simple querying over text.</span></span>  
  
 [<span data-ttu-id="c8cd6-117">Porady: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cd6-117">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 <span data-ttu-id="c8cd6-118">Pokazuje podział plików tekstowych w granicach dowolnego oraz sposobu wykonania zapytania względem każdej części.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-118">Shows how to split text files on arbitrary boundaries and how to perform queries against each part.</span></span>  
  
 [<span data-ttu-id="c8cd6-119">Porady: zapytanie o znaki w ciągu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cd6-119">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>](how-to-query-for-characters-in-a-string-linq.md)  
 <span data-ttu-id="c8cd6-120">Pokazuje, że kolejność typem jest ciąg.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-120">Demonstrates that a string is a queryable type.</span></span>  
  
 [<span data-ttu-id="c8cd6-121">Porady: łączenie kwerend LINQ z wyrażeniami regularnymi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cd6-121">How to: Combine LINQ Queries with Regular Expressions (Visual Basic)</span></span>](how-to-combine-linq-queries-with-regular-expressions.md)  
 <span data-ttu-id="c8cd6-122">Przedstawia sposób użycia wyrażeń regularnych w zapytaniach LINQ dla złożonych dopasowania wzorca w filtrowane wyniki.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-122">Shows how to use regular expressions in LINQ queries for complex pattern matching on filtered query results.</span></span>  
  
## <a name="querying-semi-structured-data-in-text-format"></a><span data-ttu-id="c8cd6-123">Wykonywanie zapytania na częściowo ustrukturyzowanych danych w formacie tekstowym</span><span class="sxs-lookup"><span data-stu-id="c8cd6-123">Querying Semi-Structured Data in Text Format</span></span>  
 <span data-ttu-id="c8cd6-124">Wiele różnych typów plików tekstowych składają się z szeregu wierszy, często z podobnego formatowania, takie jak karty lub przecinkami plików lub wierszy o stałej długości.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-124">Many different types of text files consist of a series of lines, often with similar formatting, such as tab- or comma-delimited files or fixed-length lines.</span></span> <span data-ttu-id="c8cd6-125">Po przeczytaniu plik tekstowy do pamięci umożliwia LINQ zapytania i/lub modyfikowania wierszy.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-125">After you read such a text file into memory, you can use LINQ to query and/or modify the lines.</span></span> <span data-ttu-id="c8cd6-126">Zapytania LINQ także upraszcza zadanie połączenie danych z wielu źródeł.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-126">LINQ queries also simplify the task of combining data from multiple sources.</span></span>  
  
 [<span data-ttu-id="c8cd6-127">Porady: znajdowanie różnicy pomiędzy dwoma listami (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cd6-127">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)  
 <span data-ttu-id="c8cd6-128">Pokazuje, jak można znaleźć wszystkie ciągi, które znajdują się w jednej liście, ale nie przez drugą.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-128">Shows how to find all the strings that are present in one list but not the other.</span></span>  
  
 [<span data-ttu-id="c8cd6-129">Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cd6-129">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 <span data-ttu-id="c8cd6-130">Pokazuje, jak można sortować według dowolnego słowa lub pola wierszy tekstu.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-130">Shows how to sort text lines based on any word or field.</span></span>  
  
 [<span data-ttu-id="c8cd6-131">Porady: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cd6-131">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>](how-to-reorder-the-fields-of-a-delimited-file.md)  
 <span data-ttu-id="c8cd6-132">Pokazuje, jak można zmienić kolejności pól w wierszu pliku CSV.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-132">Shows how to reorder fields in a line in a .csv file.</span></span>  
  
 [<span data-ttu-id="c8cd6-133">Porady: łączenie i porównywanie kolekcji ciągów (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cd6-133">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)  
 <span data-ttu-id="c8cd6-134">Pokazuje, jak połączyć list ciągów na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-134">Shows how to combine string lists in various ways.</span></span>  
  
 [<span data-ttu-id="c8cd6-135">Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cd6-135">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 <span data-ttu-id="c8cd6-136">Pokazuje, jak utworzyć kolekcje obiektów za pomocą wielu plików tekstowych jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-136">Shows how to create object collections by using multiple text files as data sources.</span></span>  
  
 [<span data-ttu-id="c8cd6-137">Porady: łączenie zawartości niepodobnych plików (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cd6-137">How to: Join Content from Dissimilar Files (LINQ) (Visual Basic)</span></span>](how-to-join-content-from-dissimilar-files-linq.md)  
 <span data-ttu-id="c8cd6-138">Pokazuje, jak połączyć ciągów w obu list w jednym ciągu przy użyciu odpowiedniego klucza.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-138">Shows how to combine strings in two lists into a single string by using a matching key.</span></span>  
  
 [<span data-ttu-id="c8cd6-139">Porady: dzielenie pliku na wiele plików za pomocą grup (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cd6-139">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 <span data-ttu-id="c8cd6-140">Przedstawia sposób tworzenia nowych plików za pomocą pojedynczego pliku jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-140">Shows how to create new files by using a single file as a data source.</span></span>  
  
 [<span data-ttu-id="c8cd6-141">Porady: obliczanie wartości kolumn w pliku tekstowym CSV (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cd6-141">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 <span data-ttu-id="c8cd6-142">Pokazuje, jak wykonać obliczenia matematyczne na dane tekstu w plikach CSV.</span><span class="sxs-lookup"><span data-stu-id="c8cd6-142">Shows how to perform mathematical computations on text data in .csv files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8cd6-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8cd6-143">See Also</span></span>  
 [<span data-ttu-id="c8cd6-144">Zapytanie o języku zintegrowanym (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8cd6-144">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)  
 [<span data-ttu-id="c8cd6-145">Porady: generowanie kodu XML z plików CSV</span><span class="sxs-lookup"><span data-stu-id="c8cd6-145">How to: Generate XML from CSV Files</span></span>](how-to-generate-xml-from-csv-files.md)
