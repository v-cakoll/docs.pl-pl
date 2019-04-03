---
title: LINQ i ciągi (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
ms.openlocfilehash: 7e0ebe64494182191dafa033ecbc38bad17180be
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818959"
---
# <a name="linq-and-strings-visual-basic"></a>LINQ i ciągi (Visual Basic)
LINQ mogą służyć do wykonywania zapytań i przekształcanie ciągów i zbiorów ciągów. Może być szczególnie przydatne w przypadku danych z częściową strukturą w plikach tekstowych. Zapytania LINQ można łączyć z funkcji tradycyjnego ciągów i wyrażeń regularnych. Na przykład, można użyć <xref:System.String.Split%2A> lub <xref:System.Text.RegularExpressions.Regex.Split%2A> metodę, aby utworzyć tablicę ciągów, które można zbadać lub zmodyfikować za pomocą LINQ. Możesz użyć <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method in Class metoda `where` klauzula zapytania LINQ. I LINQ umożliwia zapytania lub zmodyfikować <xref:System.Text.RegularExpressions.MatchCollection> wyniki zwrócone przez wyrażenie regularne.  
  
 Metod opisanych w tej sekcji służy również do przekształcania tekstu lub częściową strukturą danych do pliku XML. Aby uzyskać więcej informacji, zobacz [jak: Generowanie kodu XML z plików CSV](how-to-generate-xml-from-csv-files.md).  
  
 Przykłady w tej sekcji można podzielić na dwie kategorie:  
  
## <a name="querying-a-block-of-text"></a>Wykonywanie zapytań w bloku tekstu  
 Zapytanie, analizowania i zmodyfikować bloków tekstu, dzieląc je na odpytywalny tablicę ciągów mniejszych przy użyciu <xref:System.String.Split%2A> metody lub <xref:System.Text.RegularExpressions.Regex.Split%2A> metody. Można podzielić tekst źródłowy słów, zdań, akapitów, stron lub innych kryteriów, a następnie wykonać dodatkowe dzieli dane, jeśli są one wymagane w kwerendzie.  
  
 [Instrukcje: Liczba wystąpień wyrazu w ciągu (LINQ) (Visual Basic)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Pokazuje, jak używać programu LINQ do wykonywania prostych zapytań nad tekstem.  
  
 [Instrukcje: Zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (Visual Basic)](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 Pokazuje, jak podzielić pliki tekstowe na odgórnych ograniczeń i poznać sposoby wykonywania zapytań względem każdej części.  
  
 [Instrukcje: Zapytanie o znaki w ciągu (LINQ) (Visual Basic)](how-to-query-for-characters-in-a-string-linq.md)  
 Pokazuje, czy ciąg jest typem odpytywalnym.  
  
 [Instrukcje: Łączenie zapytań LINQ z wyrażeniami regularnymi (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)  
 Pokazuje, jak używać wyrażeń regularnych w zapytaniach LINQ dla złożonych dopasowania do wzorca w wynikach zapytania filtrowanego.  
  
## <a name="querying-semi-structured-data-in-text-format"></a>Podczas badania częściowo ustrukturyzowanych danych w formacie tekstowym  
 Wiele różnych typów plików tekstowych składają się z szeregu wiersze, często z podobnego formatowania, takie jak karty lub przecinkami pliki lub wiersze o stałej długości. Po przeczytaniu pliku tekstowego do pamięci można użyć LINQ do zapytań i/lub modyfikowania wierszy. Zapytania LINQ również uprościć zadanie połączenie danych z wielu źródeł.  
  
 [Instrukcje: Wyszukiwanie zestawu różnic między dwoma listami (LINQ) (Visual Basic)](how-to-find-the-set-difference-between-two-lists-linq.md)  
 Pokazuje, jak znaleźć wszystkie ciągi, które znajdują się w jednej liście, ale nie drugiej.  
  
 [Instrukcje: Sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Pokazuje sposób sortowania wierszy tekstu, w oparciu o dowolnego słowa lub pola.  
  
 [Instrukcje: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (Visual Basic)](how-to-reorder-the-fields-of-a-delimited-file.md)  
 Pokazuje, jak zmienianie kolejności pól w wierszu w pliku CSV.  
  
 [Instrukcje: Łączenie i porównywanie kolekcji ciągów (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)  
 Pokazuje, jak łączyć listy parametrów na różne sposoby.  
  
 [Instrukcje: Wypełnianie kolekcji Object z wielu źródeł (LINQ) (Visual Basic)](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Pokazuje, jak tworzyć kolekcje obiektów przy użyciu wielu plików tekstowych jako źródła danych.  
  
 [Instrukcje: Łączenie zawartości niepodobnych plików (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md)  
 Pokazuje, jak połączyć dwie listy ciągów w jeden ciąg przy użyciu zgodnego klucza.  
  
 [Instrukcje: Dzielenie pliku na kilka plików za pomocą grup (LINQ) (Visual Basic)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Pokazuje, jak utworzyć nowe pliki przy użyciu pojedynczego pliku jako źródło danych.  
  
 [Instrukcje: Obliczanie wartości kolumn w pliku tekstowym CSV (LINQ) (Visual Basic)](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 Pokazuje sposób wykonywania obliczeń matematycznych na danych tekstu w plikach CSV.  
  
## <a name="see-also"></a>Zobacz także

- [Zapytanie o języku zintegrowanym (LINQ) (Visual Basic)](index.md)
- [Instrukcje: Generowanie kodu XML z plików CSV](how-to-generate-xml-from-csv-files.md)
