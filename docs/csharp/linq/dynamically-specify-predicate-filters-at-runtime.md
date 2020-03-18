---
title: Dynamicznie określaj filtry predykatu w czasie wykonywania (LINQ w języku C#)
description: Dowiedz się, jak dynamicznie określać filtry predykatu w czasie wykonywania przy użyciu LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 314be8f98b9ff014f14bef11a1f3581eff8574b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659946"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a>Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym

W niektórych przypadkach nie wiesz, aż do czasu wykonywania, ile predykatów `where` trzeba zastosować do elementów źródłowych w klauzuli. Jednym ze sposobów dynamicznego określania wielu filtrów <xref:System.Linq.Enumerable.Contains%2A> predykatu jest użycie metody, jak pokazano w poniższym przykładzie. Przykład jest skonstruowany na dwa sposoby. Po pierwsze projekt jest uruchamiany przez filtrowanie wartości, które są dostarczane w programie. Następnie projekt jest uruchamiany ponownie przy użyciu danych wejściowych dostarczonych w czasie wykonywania.

## <a name="to-filter-by-using-the-contains-method"></a>Aby filtrować za pomocą metody Contains

1. Otwórz nową aplikację konsoli `PredicateFilters`i najmiej nazwę .

2. Skopiuj `StudentClass` klasę z [query kolekcji obiektów](query-a-collection-of-objects.md) `PredicateFilters` i wklej ją do obszaru nazw pod klasą `Program`. `StudentClass`zawiera listę `Student` obiektów.

3. Skomentuj `Main` metodę `StudentClass`w pliku .

4. Zamień klasę `Program` na następujący kod:

     [!code-csharp[csProgGuideLINQ#26](~/samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]

5. Dodaj następujący wiersz `Main` do metody `DynamicPredicates`w klasie `ids`, pod deklaracją .

     ```csharp
     QueryById(ids);
     ```

6. Uruchom projekt.

7. W oknie konsoli wyświetlane są następujące dane wyjściowe:

     Garcia: 114

     O'Donnell: 112

     Omelchenko: 111

8. Następnym krokiem jest ponowne uruchomienie projektu, tym razem przy użyciu `ids`danych wejściowych wprowadzonych w czasie wykonywania zamiast tablicy . Zmień `QueryByID(ids)` `QueryByID(args)` na `Main` w metodzie.

9. Uruchom projekt z argumentami `122 117 120 115`wiersza polecenia . Po uruchomieniu projektu te wartości `args`stają się elementami `Main` parametru metody.

10. W oknie konsoli wyświetlane są następujące dane wyjściowe:

     Adams: 120

     Feng: 117

     Garcia: 115

     Tucker: 122

## <a name="to-filter-by-using-a-switch-statement"></a>Aby filtrować przy użyciu instrukcji switch

1. Instrukcja służy `switch` do wybierania spośród wstępnie określonych kwerend alternatywnych. W poniższym `studentQuery` przykładzie używa `where` innej klauzuli w zależności od poziomu klasy lub roku, jest określony w czasie wykonywania.

2. Skopiuj następującą `DynamicPredicates`metodę i wklej ją do klasy .

     [!code-csharp[csProgGuideLINQ#27](~/samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]

3. W `Main` metodzie zastąp wywołanie `QueryByID` następujące wywołanie, które `args` wysyła pierwszy `QueryByYear(args[0])`element z tablicy jako jego argument: .

4. Uruchom projekt z argumentem wiersza polecenia o wartości całkowitej z wartością od 1 do 4.

## <a name="see-also"></a>Zobacz też

- [Language Integrated Query (LINQ)](index.md)
- [gdzie klauzula](../language-reference/keywords/where-clause.md)
