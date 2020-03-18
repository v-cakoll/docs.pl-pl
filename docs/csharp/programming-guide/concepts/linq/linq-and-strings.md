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
# <a name="linq-and-strings-c"></a>LINQ i ciągi (C#)

LINQ może służyć do wykonywania zapytań i przekształcania ciągów i kolekcji ciągów. Może to być szczególnie przydatne w przypadku danych częściowo strukturalnych w plikach tekstowych. Zapytania LINQ można łączyć z tradycyjnymi funkcjami ciągu i wyrażeniami regularnymi. Na przykład można użyć <xref:System.String.Split%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> lub metody, aby utworzyć tablicę ciągów, które następnie kwerendy lub modyfikowane przy użyciu LINQ. Można użyć <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metody w `where` klauzuli kwerendy LINQ. I można użyć LINQ do <xref:System.Text.RegularExpressions.MatchCollection> kwerendy lub zmodyfikować wyniki zwrócone przez wyrażenie regularne.

Można również użyć technik opisanych w tej sekcji, aby przekształcić dane tekstu częściowo strukturalnego do XML. Aby uzyskać więcej informacji, zobacz [Jak wygenerować kod XML z plików CSV](how-to-generate-xml-from-csv-files.md).

Przykłady w tej sekcji dzielą się na dwie kategorie:

## <a name="querying-a-block-of-text"></a>Wykonywanie zapytań dotyczących bloku tekstu

Można wysyłać zapytania, analizować i modyfikować bloki tekstowe, dzieląc je na <xref:System.String.Split%2A?displayProperty=nameWithType> tablicę <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> mniejszych ciągów z możliwością wykonywania zapytań przy użyciu metody lub metody. Tekst źródłowy można podzielić na słowa, zdania, akapity, strony lub inne kryteria, a następnie wykonać dodatkowe podziały, jeśli są one wymagane w zapytaniu.

- [Jak zliczać wystąpienia wyrazu w ciągu (LINQ) (C#)](how-to-count-occurrences-of-a-word-in-a-string-linq.md)  
  Pokazuje, jak używać LINQ do prostego wykonywania zapytań za pomocą tekstu.

- [Jak wysyłać zapytania do zdań zawierających określony zestaw słów (LINQ) (C#)](how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

  Pokazuje, jak dzielić pliki tekstowe na dowolne granice i jak wykonywać kwerendy względem każdej części.

- [Jak wysyłać zapytania o znaki w ciągu (LINQ) (C#)](how-to-query-for-characters-in-a-string-linq.md)

  Pokazuje, że ciąg jest typem podlegającym zapytań.

- [Jak połączyć zapytania LINQ z wyrażeniami regularnymi (C#)](how-to-combine-linq-queries-with-regular-expressions.md)

  Pokazuje, jak używać wyrażeń regularnych w kwerendach LINQ do dopasowywania wzorców złożonych w wynikach filtrowanych kwerend.

## <a name="querying-semi-structured-data-in-text-format"></a>Wykonywanie zapytań dotyczących danych częściowo strukturalnych w formacie tekstowym

Wiele różnych typów plików tekstowych składa się z serii linii, często z podobnym formatowaniem, takich jak pliki rozdzielane za pomocą kart lub przecinków lub linie o stałej długości. Po przeczytaniu takiego pliku tekstowego w pamięci, można użyć LINQ do kwerendy i /lub zmodyfikować wiersze. Zapytania LINQ również uprościć zadanie łączenia danych z wielu źródeł.

- [Jak znaleźć różnicę między dwiema listami (LINQ) (C#)](how-to-find-the-set-difference-between-two-lists-linq.md)

  Pokazuje, jak znaleźć wszystkie ciągi, które są obecne na jednej liście, ale nie inne.

- [Jak sortować lub filtrować dane tekstowe według dowolnego wyrazu lub pola (LINQ) (C#)](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)

  Pokazuje sposób sortowania wierszy tekstu na podstawie dowolnego wyrazu lub pola.

- [Jak ponownie uporządkować pola rozdzielonego pliku (LINQ) (C#)](how-to-reorder-the-fields-of-a-delimited-file-linq.md)

  Pokazuje, jak uporządkować pola w wierszu w pliku csv.

- [Jak łączyć i porównywać kolekcje ciągów (LINQ) (C#)](how-to-combine-and-compare-string-collections-linq.md)

  Pokazuje, jak łączyć listy ciągów na różne sposoby.

- [Jak wypełnić kolekcje obiektów z wielu źródeł (LINQ) (C#)](how-to-populate-object-collections-from-multiple-sources-linq.md)

  Pokazuje, jak tworzyć kolekcje obiektów przy użyciu wielu plików tekstowych jako źródeł danych.

- [Jak dołączyć zawartość z różnych plików (LINQ) (C#)](how-to-join-content-from-dissimilar-files-linq.md)
  
  Pokazuje, jak połączyć ciągi ciągów na dwóch listach w jeden ciąg za pomocą pasującego klucza.

- [Jak podzielić plik na wiele plików przy użyciu grup (LINQ) (C#)](how-to-split-a-file-into-many-files-by-using-groups-linq.md)
  
  Pokazuje, jak tworzyć nowe pliki przy użyciu pojedynczego pliku jako źródła danych.

- [Jak obliczyć wartości kolumn w pliku tekstowym CSV (LINQ) (C#)](how-to-compute-column-values-in-a-csv-text-file-linq.md)
  
  Pokazuje, jak wykonywać obliczenia matematyczne na danych tekstowych w plikach csv.

## <a name="see-also"></a>Zobacz też

- [Zapytanie zintegrowane z językiem (LINQ) (C#)](index.md)
- [Generowanie kodu XML z plików CSV](how-to-generate-xml-from-csv-files.md)
