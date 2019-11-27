---
title: LINQ i ciągi
ms.date: 07/20/2015
ms.assetid: 75ddb201-d97a-4f98-8cdf-4ad51714529a
ms.openlocfilehash: 73ce4bf5586f1f9ff4995ea6f425b90744b7e333
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353285"
---
# <a name="linq-and-strings-visual-basic"></a>LINQ i ciągi (Visual Basic)
LINQ może służyć do wykonywania zapytań i przekształcania ciągów i kolekcji ciągów. Może być szczególnie przydatne w przypadku danych z częściową strukturą w plikach tekstowych. Zapytania LINQ można łączyć z tradycyjnymi funkcjami ciągów i wyrażeniami regularnymi. Na przykład można użyć metody <xref:System.String.Split%2A> lub <xref:System.Text.RegularExpressions.Regex.Split%2A>, aby utworzyć tablicę ciągów, które można następnie wykonać zapytania lub zmodyfikować przy użyciu LINQ. Metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> można użyć w klauzuli `where` zapytania LINQ. I można użyć LINQ do zapytania lub zmodyfikować wyniki <xref:System.Text.RegularExpressions.MatchCollection> zwrócone przez wyrażenie regularne.  
  
 Można również użyć technik opisanych w tej sekcji, aby przekształcić dane z częściową strukturą do formatu XML. Aby uzyskać więcej informacji, zobacz [How to: Generate XML from pliki CSV](how-to-generate-xml-from-csv-files.md).  
  
 Przykłady w tej sekcji należą do dwóch kategorii:  
  
## <a name="querying-a-block-of-text"></a>Wykonywanie zapytania dotyczącego bloku tekstu  
 Można wykonywać zapytania, analizować i modyfikować bloki tekstu, dzieląc je na tablicę Queryable mniejszych ciągów przy użyciu metody <xref:System.String.Split%2A> lub metody <xref:System.Text.RegularExpressions.Regex.Split%2A>. Możesz podzielić tekst źródłowy na słowa, zdania, akapity, strony lub inne kryteria, a następnie wykonać dodatkowe podziały, jeśli są one wymagane w zapytaniu.  
  
 [Instrukcje: Liczenie wystąpień wyrazu w ciągu (LINQ) (Visual Basic)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
 Pokazuje, jak używać LINQ do prostego wykonywania zapytań względem tekstu.  
  
 [Instrukcje: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (Visual Basic)](how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)

 Pokazuje sposób dzielenia plików tekstowych na dowolne granice oraz wykonywania zapytań dotyczących poszczególnych części.  
  
 [Instrukcje: zapytanie o znaki w ciągu (LINQ) (Visual Basic)](how-to-query-for-characters-in-a-string-linq.md)  
 Pokazuje, że ciąg jest typem queryable.  
  
 [Jak połączyć zapytania LINQ z wyrażeniami regularnymi (Visual Basic)](how-to-combine-linq-queries-with-regular-expressions.md)  
 Pokazuje, jak używać wyrażeń regularnych w zapytaniach LINQ dla złożonego dopasowania do wzorca na filtrowanych wynikach zapytań.  
  
## <a name="querying-semi-structured-data-in-text-format"></a>Wykonywanie zapytania dotyczącego danych z częściową strukturą w formacie tekstowym  
 Wiele różnych typów plików tekstowych składa się z szeregu wierszy, często z podobnym formatowaniem, takim jak pliki rozdzielane znakami tabulacji lub rozdzielonymi długościami. Po przeczytaniu takiego pliku tekstowego do pamięci można użyć LINQ do wykonywania zapytań i/lub modyfikowania wierszy. Zapytania LINQ upraszczają także zadanie łączenia danych z wielu źródeł.  
  
 [Instrukcje: Wyszukiwanie zestawu różnic między dwoma listami (LINQ) (Visual Basic)](how-to-find-the-set-difference-between-two-lists-linq.md)  
 Pokazuje, jak znaleźć wszystkie ciągi, które znajdują się na jednej liście, ale nie w drugim.  
  
 [Instrukcje: sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (Visual Basic)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)  
 Pokazuje, jak sortować wiersze tekstu na podstawie dowolnego wyrazu lub pola.  
  
 [Instrukcje: Zmienianie kolejności pól w rozdzielonym pliku (LINQ) (Visual Basic)](how-to-reorder-the-fields-of-a-delimited-file.md)  
 Pokazuje, jak zmienić kolejność pól w wierszu w pliku CSV.  
  
 [Instrukcje: łączenie i porównywanie kolekcji ciągów (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)  
 Pokazuje, jak łączyć listy ciągów na różne sposoby.  
  
 [Instrukcje: wypełnianie kolekcji obiektów z wielu źródeł (LINQ) (Visual Basic)](how-to-populate-object-collections-from-multiple-sources-linq.md)  
 Pokazuje, jak tworzyć kolekcje obiektów przy użyciu wielu plików tekstowych jako źródła danych.  
  
 [Instrukcje: dołączanie zawartości z niepodobnych plików (LINQ) (Visual Basic)](how-to-join-content-from-dissimilar-files-linq.md)  
 Pokazuje, w jaki sposób połączyć ciągi w dwóch listach w jeden ciąg za pomocą pasującego klucza.  
  
 [Instrukcje: dzielenie pliku na wiele plików przy użyciu grup (LINQ) (Visual Basic)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)  
 Pokazuje, jak tworzyć nowe pliki przy użyciu pojedynczego pliku jako źródła danych.  
  
 [Instrukcje: Obliczanie wartości kolumn w pliku tekstowym CSV (LINQ) (Visual Basic)](how-to-compute-column-values-in-a-csv-text-file-linq.md)  
 Pokazuje, jak wykonywać obliczenia matematyczne na danych tekstowych w plikach CSV.  
  
## <a name="see-also"></a>Zobacz także

- [Zapytanie zintegrowane z językiem (LINQ) (Visual Basic)](index.md)
- [Instrukcje: generowanie kodu XML z plików CSV](how-to-generate-xml-from-csv-files.md)
