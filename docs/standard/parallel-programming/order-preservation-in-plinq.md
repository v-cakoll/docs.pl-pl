---
title: Zamawianie zachowywania w PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, order preservation
ms.assetid: 10d202bc-19e1-4b5c-bbf1-9a977322a9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1587b2c4d19833c615c5a10a2fe0d6b28e854aca
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061523"
---
# <a name="order-preservation-in-plinq"></a>Zamawianie zachowywania w PLINQ
W programie PLINQ celem jest aby zmaksymalizować wydajność przy zachowaniu poprawności. Zapytanie powinno działają równie szybko, ale nadal generować prawidłowe wyniki. W niektórych przypadkach poprawność wymaga kolejność sekwencji źródłowej zostanie zachowana; jednak porządkowania może być dużego nakładu mocy obliczeniowych. Dlatego domyślnie PLINQ nie pozwala zachować kolejność sekwencji źródłowej. W tym zakresie przypomina PLINQ [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)], ale w przeciwieństwie do programu LINQ do obiektów, które zachowują kolejność.  
  
 Aby zastąpić domyślne zachowanie, można włączyć zachowywanie kolejności przy użyciu <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operatora w sekwencji źródłowej. Możesz następnie wyłączyć zachowywanie kolejności w dalszej części zapytania przy użyciu <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> metody. Za pomocą obu metod zapytania są przetwarzane w zależności od Algorytm heurystyczny, który ustalić, czy można wykonać kwerendy w postaci równoległego lub jako kolejnych. Aby uzyskać więcej informacji, zobacz [ogólne informacje o przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
 Poniższy przykład pokazuje nieuporządkowaną zapytanie równoległe, który filtruje dla wszystkich elementów, które odpowiadają warunku, bez próby kolejność wyników w dowolny sposób.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 To zapytanie nie zawsze generuje 1000 pierwszych miast w sekwencji źródłowej, które spełniają warunek, ale raczej niektóre zestaw miast 1000, które spełniają warunek. Operatory zapytań PLINQ partycji sekwencję źródłową na wiele podciągów, które są przetwarzane jako współbieżnych zadań. Jeśli nie określono porządku, wyniki z każdej partycji są przekazane do kolejnego etapu zapytania w dowolnej kolejności. Ponadto partycji może przynieść podzbiór wyników, przed kontynuowaniem przetworzyć wszystkie pozostałe elementy. Wynikowy zamówienia może różnić się zawsze. Aplikacji nie można kontrolować to, ponieważ zależy ona jak system operacyjny planuje wątków.  
  
 Poniższy przykład zastępuje domyślne zachowanie za pomocą <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operatora w sekwencji źródłowej. Gwarantuje to, że <xref:System.Linq.ParallelEnumerable.Take%2A> metoda zwraca wartość 1000 pierwszych miast w sekwencji źródłowej, które spełniają warunek.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Jednak ta kwerenda prawdopodobnie nie działa tak szybko, jak Nieuporządkowana wersja, ponieważ jego musi śledzić oryginalna kolejność w partycji i w czasie scalania upewnij się, że kolejność spójne. Dlatego zaleca się używanie <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> tylko wtedy, gdy jest to wymagane i tylko dla tych części zapytania, które tego wymagają. Gdy porządku nie jest już wymagane, użyj <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> jej wyłączenia. Poniższy przykład osiąga to za pośrednictwem dwóch zapytań.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 Należy pamiętać, że PLINQ zachowuje kolejności sekwencji generowany przez nakładające kolejność operatorów w pozostałej części zapytania. Innymi słowy, operatory, takie jak <xref:System.Linq.ParallelEnumerable.OrderBy%2A> i <xref:System.Linq.ParallelEnumerable.ThenBy%2A> są traktowane tak, jakby były następuje po wywołaniu <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
## <a name="query-operators-and-ordering"></a>Operatory zapytań i kolejność  
 Następujące operatory zapytań wprowadzić porządku na wszystkie kolejne operacje w zapytaniu lub do chwili <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> nosi nazwę:  
  
-   <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 W niektórych przypadkach następujących operatorów zapytań PLINQ może wymagać uporządkowane źródłowych sekwencji, aby wygenerować prawidłowych wyników:  
  
-   <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Niektóre operatory zapytań PLINQ zachowywać się różnie w zależności od tego, czy ich sekwencja źródłowa jest uporządkowany lub nieuporządkowane. Poniższa tabela zawiera listę tych operatorów.  
  
|Operator|Wynik, jeśli sekwencja źródłowa jest uporządkowany|Wynik, jeśli sekwencja źródłowa jest nieuporządkowane|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Tego rodzaju danych wyjściowych dla operacji nonassociative lub noncommutative|Tego rodzaju danych wyjściowych dla operacji nonassociative lub noncommutative|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Tego rodzaju danych wyjściowych dla operacji nonassociative lub noncommutative|Tego rodzaju danych wyjściowych dla operacji nonassociative lub noncommutative|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Wyniki uporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Wyniki uporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Wyniki uporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Wyniki nieuporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Wykonywane w sposób niedeterministyczny równolegle|Wykonywane w sposób niedeterministyczny równolegle|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Wyniki uporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Wyniki uporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Wyniki uporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Wyniki uporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Zmienia kolejność sekwencji|Rozpoczyna się nowej sekcji uporządkowane|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Zmienia kolejność sekwencji|Rozpoczyna się nowej sekcji uporządkowane|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Nie dotyczy (domyślnie takie same jak <xref:System.Linq.ParallelEnumerable.AsParallel%2A> )|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Nie dotyczy (domyślnie takie same jak <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Odwraca|Nic nie robi.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Wyniki uporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.Select%2A> (indeksowanych)|Wyniki uporządkowane|Nieuporządkowana wyników.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Uporządkowanych wyników.|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A> (indeksowanych)|Uporządkowanych wyników.|Nieuporządkowana wyników.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Uporządkowane porównania|Porównanie nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Pomija najpierw *n* elementów|Pomija dowolne *n* elementów|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Uporządkowanych wyników.|Jednoznaczne wyniki. Wykonuje skipwhile — bieżącego dowolnego zamówienia|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Tego rodzaju danych wyjściowych dla operacji nonassociative lub noncommutative|Tego rodzaju danych wyjściowych dla operacji nonassociative lub noncommutative|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Pobiera pierwszy `n` elementów|Przyjmuje żadnego `n` elementów|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Wyniki uporządkowane|Jednoznaczne wyniki. Wykonuje takewhile — bieżącego dowolnego zamówienia|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Dodatki `OrderBy`|Dodatki `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Dodatki `OrderBy`|Dodatki `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Wyniki uporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Wyniki uporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Wyniki uporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Wyniki uporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Wyniki uporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.Where%2A> (indeksowanych)|Wyniki uporządkowane|Wyniki nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Wyniki uporządkowane|Wyniki nieuporządkowane|  
  
 Nieuporządkowana wyniki nie są aktywnie przekazanych; po prostu nie mają jakąkolwiek logikę specjalną szeregowania, zastosowanych do nich. W niektórych przypadkach nieuporządkowaną zapytania może zachować kolejność sekwencji źródłowej. Dla zapytań, korzystających z indeksowanej wybierz operator PLINQ gwarantuje, że elementy danych wyjściowych pojawią zgodnie z kolejnością rosnącą indeksów, ale sprawia, że żadnej gwarancji dotyczącej indeksów, które zostaną przypisane do elementów.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
