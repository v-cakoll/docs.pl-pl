---
title: LINQ i ciągi (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
ms.openlocfilehash: a76465b33a30d149cd6313e2628ee742e248ab3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linq-and-strings-visual-basic"></a>LINQ i ciągi (Visual Basic)
LINQ może służyć do wykonywania zapytań i przekształcanie ciągów i kolekcji ciągów. Może być szczególnie przydatne w przypadku częściowo ustrukturyzowanych danych w plikach tekstowych. Zapytania LINQ można łączyć z funkcje tradycyjnych ciągów i wyrażenia regularne. Na przykład można użyć <xref:System.String.Split%2A> lub <xref:System.Text.RegularExpressions.Regex.Split%2A> metodę w celu utworzenia tablicy ciągów, które można zbadać lub zmodyfikować za pomocą LINQ. Można użyć <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metoda `where` klauzuli zapytania LINQ. I użyj rozszerzenia LINQ, aby zapytań, lub zmodyfikuj <xref:System.Text.RegularExpressions.MatchCollection> wyników zwróconych w wyniku wyrażenia regularnego.  
  
 Metod opisanych w tej sekcji służy również do przekształcania tekstu częściowo ustrukturyzowanych danych do formatu XML. Aby uzyskać więcej informacji, zobacz [porady: generowanie XML z plików CSV](how-to-generate-xml-from-csv-files.md).  
  
 Przykłady w tej sekcji można podzielić na dwie kategorie:  
  
## <a name="querying-a-block-of-text"></a>Wykonywanie zapytania bloku tekstu  
 Zapytanie, analizowanie i zmodyfikować bloków tekstu, podziel je na kolejność tablicę ciągów mniejszy przy użyciu <xref:System.String.Split%2A> metody lub <xref:System.Text.RegularExpressions.Regex.Split%2A> metody. Można podzielić tekst źródłowy słów, zdań, akapitów, stron lub innych kryteriów, a następnie wykonaj dodatkowych podziałów, jeśli są one wymagane w zapytaniu.  
  
 [Porady: liczenie wystąpień słowa w ciągu (LINQ) (Visual Basic)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Przedstawia sposób użycia LINQ prostych zapytań nad tekstem.  
  
 [Porady: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (Visual Basic)](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 Pokazuje podział plików tekstowych w granicach dowolnego oraz sposobu wykonania zapytania względem każdej części.  
  
 [Porady: zapytanie o znaki w ciągu (LINQ) (Visual Basic)](how-to-query-for-characters-in-a-string-linq.md)  
 Pokazuje, że kolejność typem jest ciąg.  
  
 [Porady: łączenie kwerend LINQ z wyrażeniami regularnymi (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)  
 Przedstawia sposób użycia wyrażeń regularnych w zapytaniach LINQ dla złożonych dopasowania wzorca w filtrowane wyniki.  
  
## <a name="querying-semi-structured-data-in-text-format"></a>Wykonywanie zapytania na częściowo ustrukturyzowanych danych w formacie tekstowym  
 Wiele różnych typów plików tekstowych składają się z szeregu wierszy, często z podobnego formatowania, takie jak karty lub przecinkami plików lub wierszy o stałej długości. Po przeczytaniu plik tekstowy do pamięci umożliwia LINQ zapytania i/lub modyfikowania wierszy. Zapytania LINQ także upraszcza zadanie połączenie danych z wielu źródeł.  
  
 [Porady: znajdowanie różnicy pomiędzy dwoma listami (LINQ) (Visual Basic)](how-to-find-the-set-difference-between-two-lists-linq.md)  
 Pokazuje, jak można znaleźć wszystkie ciągi, które znajdują się w jednej liście, ale nie przez drugą.  
  
 [Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Pokazuje, jak można sortować według dowolnego słowa lub pola wierszy tekstu.  
  
 [Porady: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (Visual Basic)](how-to-reorder-the-fields-of-a-delimited-file.md)  
 Pokazuje, jak można zmienić kolejności pól w wierszu pliku CSV.  
  
 [Porady: łączenie i porównywanie kolekcji ciągów (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)  
 Pokazuje, jak połączyć list ciągów na różne sposoby.  
  
 [Porady: wypełnianie kolekcji Object z wielu źródeł (LINQ) (Visual Basic)](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Pokazuje, jak utworzyć kolekcje obiektów za pomocą wielu plików tekstowych jako źródła danych.  
  
 [Porady: łączenie zawartości niepodobnych plików (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md)  
 Pokazuje, jak połączyć ciągów w obu list w jednym ciągu przy użyciu odpowiedniego klucza.  
  
 [Porady: dzielenie pliku na wiele plików za pomocą grup (LINQ) (Visual Basic)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Przedstawia sposób tworzenia nowych plików za pomocą pojedynczego pliku jako źródła danych.  
  
 [Porady: obliczanie wartości kolumn w pliku tekstowym CSV (LINQ) (Visual Basic)](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 Pokazuje, jak wykonać obliczenia matematyczne na dane tekstu w plikach CSV.  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytanie o języku zintegrowanym (LINQ) (Visual Basic)](index.md)  
 [Instrukcje: generowanie kodu XML z plików CSV](how-to-generate-xml-from-csv-files.md)
