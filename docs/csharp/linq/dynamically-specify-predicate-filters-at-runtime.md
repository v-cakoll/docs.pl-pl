---
title: Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym
description: Jak dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym.
ms.date: 12/1/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: fa3426a513758d8c30bf381ec480b9b8d12a5f81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33287943"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a>Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym

W niektórych przypadkach nie wiadomo, do czasu wykonywania ile predykaty ma być stosowany do elementów źródła w `where` klauzuli. Jednym ze sposobów dynamiczne określanie filtrów predykatów wielu jest użycie <xref:System.Linq.Enumerable.Contains%2A> metody, jak pokazano w poniższym przykładzie. Przykładzie jest tworzony na dwa sposoby. Po pierwsze projekt jest uruchamiany przez filtrowanie wartości, które znajdują się w programie. Projekt jest następnie uruchom ponownie przy użyciu danych wejściowych dostarczonych w czasie wykonywania.  
  
## <a name="to-filter-by-using-the-contains-method"></a>Aby filtrować przy użyciu metody zawiera  
  
1.  Otwórz nową aplikację konsoli i nadaj mu nazwę `PredicateFilters`.  
  
2.  Kopiuj `StudentClass` klasę z [kwerenda dotycząca kolekcji obiektów](query-a-collection-of-objects.md) i wklej go do obszaru nazw `PredicateFilters` poniżej klasy `Program`. `StudentClass` zawiera listę `Student` obiektów.  
  
3.  Komentarz `Main` metoda `StudentClass`.  
  
4.  Zastąp klasę `Program` następującym kodem.  
  
     [!code-csharp[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  Dodaj następujący wiersz do `Main` metody w klasie `DynamicPredicates`, w obszarze deklaracja `ids`.  
  
     ```csharp
     QueryById(ids);
     ```

6.  Uruchom projekt.  
  
7.  W oknie konsoli wyświetlane są następujące dane wyjściowe:  
  
     Kowalski: 114  
  
     O'Donnell: 112  
  
     Omelchenko: 111  
  
8.  Następnym krokiem jest ponowne uruchomienie projektu, teraz przy użyciu danych wejściowych wprowadzona w czasie wykonywania, zamiast tablicy `ids`. Zmień `QueryByID(ids)` do `QueryByID(args)` w `Main` metody.  
  
9. Uruchom projekt z argumenty wiersza polecenia `122 117 120 115`. Po uruchomieniu projektu, te wartości stają się elementami `args`, parametr `Main` metody.  
  
10. W oknie konsoli wyświetlane są następujące dane wyjściowe:  
  
     Zawadzki: 120  
  
     Feng: 117  
  
     Kowalski: 115  
  
     Tucker: 122  
  
## <a name="to-filter-by-using-a-switch-statement"></a>Aby filtrować za pomocą instrukcji switch  
  
1.  Można użyć `switch` instrukcji, aby wybrać spośród wstępnie określone alternatywne zapytania. W poniższym przykładzie `studentQuery` używa innej `where` klauzuli w zależności od tego, które klasy poziom lub rok, jest określona w czasie wykonywania.  
  
2.  Skopiuj następujące metody i wklej go do klasy `DynamicPredicates`.  
  
     [!code-csharp[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  W `Main` metody, Zastąp wywołanie `QueryByID` następujące wywołanie, który wysyła pierwszego elementu z `args` tablicy jako jej argument: `QueryByYear(args[0])`.  
  
4.  Uruchom projekt z argumentem wiersza polecenia liczbę całkowitą z przedziału od 1 do 4.  
  
 
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia zapytań LINQ](index.md)  
 [where, klauzula](../language-reference/keywords/where-clause.md)
