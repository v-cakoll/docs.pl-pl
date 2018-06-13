---
title: Wyniki zapytania grupy
description: Sposób grupowania wyników.
ms.date: 12/1/2016
ms.assetid: 2e4ec27f-06fb-4de7-8973-0189906d4520
ms.openlocfilehash: cb7808bfdd86dd23882d0722b87b1e013a84141e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289038"
---
# <a name="group-query-results"></a>Wyniki zapytania grupy

Grupowanie jest jednym z najbardziej zaawansowanych funkcji LINQ. Poniższe przykłady przedstawiają sposób grupowania danych na różne sposoby:  
  
-   W jednej właściwości.  
  
-   Przez pierwszą literę właściwości ciągu.  
  
-   Przez obliczoną zakresu numerycznego.  
  
-   Predykat Boolean lub innego wyrażenia.  
  
-   Przy użyciu klucza złożonego.  
  
 Ponadto ostatnie dwa zapytania projektu ich wyniki do nowego typu anonimowego, który zawiera tylko student imienia i nazwiska. Aby uzyskać więcej informacji, zobacz [klauzuli group](../language-reference/keywords/group-clause.md).  
  
## <a name="example"></a>Przykład  
 Wszystkie przykłady w tym temacie, użyj następujących źródeł danych i klas pomocnika.  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób grupowania elementów źródła przy użyciu jednej właściwości elementu jako klucz grupy. W tym przypadku jest klucz `string`, nazwisko studenta. Istnieje również możliwość użycia ciąg dla klucza. Operacji grupowania używa domyślna funkcja porównująca równości dla typu.  
  
 Wklej następującą metodę do `StudentClass` klasy. Zmień instrukcję wywoływania w `Main` metodę `sc.GroupBySingleProperty()`.  
  
 [!code-csharp[csProgGuideLINQ#17](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_2.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób grupowania elementów źródła przy użyciu inną niż właściwość obiektu dla klucza grupy. W tym przykładzie klucz jest pierwszą literę nazwisko studenta.  
  
 Wklej następującą metodę do `StudentClass` klasy. Zmień instrukcję wywoływania w `Main` metodę `sc.GroupBySubstring()`.  
  
 [!code-csharp[csProgGuideLINQ#18](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_3.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób grupowania elementów źródła przy użyciu zakresu numerycznego jako klucz grupy. Zapytanie następnie projekcję wyniki do typu anonimowego, zawierający tylko imię i nazwisko i zakres percentyl, do którego należy studenta. Typ anonimowy jest używany, ponieważ nie jest to niezbędne do korzystania z pełną `Student` obiektu do wyświetlenia wyników. `GetPercentile` Funkcja pomocnika, który oblicza percentyl opiera się na Średnia ocena studenta. Metoda zwraca liczbą całkowitą z przedziału od 0 do 10.  
  
 [!code-csharp[csProgGuideLINQ#50](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_4.cs)]  
  
 Wklej następującą metodę do `StudentClass` klasy. Zmień instrukcję wywoływania w `Main` metodę `sc.GroupByRange()`.  
  
 [!code-csharp[csProgGuideLINQ#19](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_5.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób grupowania elementów źródła przy użyciu wyrażenia logicznym. W tym przykładzie wyrażenie warunkowe sprawdza, czy wynik egzaminu średni studenta jest większa niż 75. Jak w poprzednich przykładach wyniki są przedstawione jako typu anonimowego, ponieważ element pełną źródła nie jest wymagana. Należy pamiętać, że właściwości typu anonimowego stają się właściwości z `Key` elementu członkowskiego i można uzyskać, sprawdzając nazwę podczas wykonywania zapytania.  
  
 Wklej następującą metodę do `StudentClass` klasy. Zmień instrukcję wywoływania w `Main` metodę `sc.GroupByBoolean()`.  
  
 [!code-csharp[csProgGuideLINQ#20](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_6.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie typu anonimowego w celu hermetyzacji klucz, który zawiera wiele wartości. W tym przykładzie pierwszą wartość klucza jest pierwszą literę nazwisko studenta. Druga wartość klucza jest wartość logiczna określająca, czy student oceniane ponad 85 na pierwszym stosowana. Można zamówić grupy przez dowolną właściwość klucza.  
  
 Wklej następującą metodę do `StudentClass` klasy. Zmień instrukcję wywoływania w `Main` metodę `sc.GroupByCompositeKey()`.  
  
 [!code-csharp[csProgGuideLINQ#21](../../../samples/snippets/csharp/concepts/linq/how-to-group-query-results_7.cs)]  
  
## <a name="see-also"></a>Zobacz także  
 <xref:System.Linq.Enumerable.GroupBy%2A>  
 <xref:System.Linq.IGrouping%602>  
 [Wyrażenia zapytań LINQ](index.md)  
 [group, klauzula](../language-reference/keywords/group-clause.md)  
 [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)  
 [Wykonanie podzapytania w operacji grupowania](perform-a-subquery-on-a-grouping-operation.md)  
 [Tworzenie grup zagnieżdżonych](create-a-nested-group.md)  
 [Grupowanie danych](../programming-guide/concepts/linq/grouping-data.md)
