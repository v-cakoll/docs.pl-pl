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
ms.openlocfilehash: 5b067fa277816e6105d37047c6c4996a4cbb9b5a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138221"
---
# <a name="order-preservation-in-plinq"></a>Zamawianie zachowywania w PLINQ
W PLINQ celem jest maksymalizacja wydajności przy zachowaniu poprawności. Zapytanie powinno działać tak szybko, jak to możliwe, ale nadal daje poprawne wyniki. W niektórych przypadkach poprawność wymaga zachowania kolejności sekwencji źródłowej; Określanie kolejności może być jednak kosztowne w praktyce. W związku z tym domyślnie PLINQ nie zachowuje kolejności sekwencji źródłowej. W tym względzie PLINQ przypomina [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)], ale w przeciwieństwie do LINQ to Objects, która zachowuje porządkowanie.  
  
 Aby przesłonić zachowanie domyślne, można włączyć opcję zachowywania kolejności przy użyciu operatora <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> w sekwencji źródłowej. Następnie można wyłączyć zachowanie w kolejności późniejszej w zapytaniu za pomocą metody <xref:System.Linq.ParallelEnumerable.AsUnordered%2A>. W obu metodach zapytanie jest przetwarzane w oparciu o algorytmy heurystyczne określające, czy wykonać zapytanie jako równoległe, czy sekwencyjne. Aby uzyskać więcej informacji, zobacz temat [Omówienie przyspieszenie w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
 Poniższy przykład przedstawia nieuporządkowane zapytanie równoległe, które filtruje dla wszystkich elementów, które pasują do warunku, bez konieczności przeszukiwania wyników w dowolny sposób.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 To zapytanie nie musi dawać pierwszych 1000 miast w sekwencji źródłowej spełniającej warunek, ale raczej z zestawu 1000 miasta, który spełnia warunek. Operatory zapytań PLINQ dzielą sekwencję źródłową na wiele podsekwencji, które są przetwarzane jako zadania współbieżne. Jeśli nie określono zachowywania zamówienia, wyniki każdej partycji są przekazywane do następnego etapu zapytania w dowolnej kolejności. Ponadto partycja może spowodować podzbiór wyników przed kontynuowaniem przetwarzania pozostałych elementów. Porządek ten może być różny za każdym razem. Aplikacja nie może kontrolować tego, ponieważ zależy od tego, jak system operacyjny planuje wątki.  
  
 Poniższy przykład zastępuje zachowanie domyślne przy użyciu operatora <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> w sekwencji źródłowej. Dzięki temu Metoda <xref:System.Linq.ParallelEnumerable.Take%2A> zwraca pierwsze miasta 1000 w sekwencji źródłowej spełniającej warunek.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Jednak to zapytanie prawdopodobnie nie działa tak szybko, jak w przypadku wersji nieuporządkowanej, ponieważ musi śledzić oryginalne porządkowanie w ramach partycji i czas scalania, upewniając się, że kolejność jest spójna. Dlatego zalecamy używanie <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> tylko wtedy, gdy jest to wymagane, i tylko dla tych części zapytania, które tego wymagają. Gdy zachowywanie kolejności nie jest już wymagane, użyj <xref:System.Linq.ParallelEnumerable.AsUnordered%2A>, aby je wyłączyć. W poniższym przykładzie są one osiągane przez złożenie dwóch zapytań.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 Należy zauważyć, że PLINQ zachowuje kolejność sekwencji wygenerowanej przez operatory nakładające się w kolejności dla reszty zapytania. Inaczej mówiąc, operatory, takie jak <xref:System.Linq.ParallelEnumerable.OrderBy%2A> i <xref:System.Linq.ParallelEnumerable.ThenBy%2A>, są traktowane tak, jakby były wykonane przez wywołanie <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
## <a name="query-operators-and-ordering"></a>Operatory zapytań i porządkowanie  
 Następujące operatory zapytań wprowadzają zachowywanie kolejności do wszystkich kolejnych operacji w zapytaniu lub do momentu wywołania <xref:System.Linq.ParallelEnumerable.AsUnordered%2A>:  
  
- <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 Następujące operatory zapytań PLINQ mogą w niektórych przypadkach wymagać uporządkowanych sekwencji źródłowych, aby generować poprawne wyniki:  
  
- <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
- <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Niektóre operatory zapytań PLINQ działają inaczej, w zależności od tego, czy ich sekwencja źródłowa jest uporządkowana, czy nieuporządkowana. Poniższa tabela zawiera listę tych operatorów.  
  
|Operator|Wynik po zamówieniu sekwencji źródłowej|Wynik w przypadku nieuporządkowania sekwencji źródłowej|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Niedeterministyczne dane wyjściowe dla operacji nieasocjacyjnych lub Noncommutative|Niedeterministyczne dane wyjściowe dla operacji nieasocjacyjnych lub Noncommutative|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Niedeterministyczne dane wyjściowe dla operacji nieasocjacyjnych lub Noncommutative|Niedeterministyczne dane wyjściowe dla operacji nieasocjacyjnych lub Noncommutative|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Uporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Uporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Uporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Nieuporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Wykonuje niedeterministycznie równolegle|Wykonuje niedeterministycznie równolegle|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Uporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Uporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Uporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Uporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Zmienia kolejność sekwencji|Uruchamia nową sekcję uporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Zmienia kolejność sekwencji|Uruchamia nową sekcję uporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Nie dotyczy (wartość domyślna jako <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Nie dotyczy (wartość domyślna jako <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Odwraca|Nic nie robi.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Uporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Select%2A> (indeksowane)|Uporządkowane wyniki|Nieuporządkowane wyniki.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Uporządkowane wyniki.|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A> (indeksowane)|Uporządkowane wyniki.|Nieuporządkowane wyniki.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Porównanie uporządkowane|Porównanie nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Pomija pierwsze *n* elementów|Pomija wszystkie *n* elementów|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Uporządkowane wyniki.|Niejednoznaczny. Wykonuje SkipWhile — w bieżącym arbitralnym zamówieniu|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Niedeterministyczne dane wyjściowe dla operacji nieasocjacyjnych lub Noncommutative|Niedeterministyczne dane wyjściowe dla operacji nieasocjacyjnych lub Noncommutative|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Przyjmuje najpierw elementy `n`|Przyjmuje dowolne `n` elementy|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Uporządkowane wyniki|Niejednoznaczny. Wykonuje TakeWhile — w bieżącym arbitralnym zamówieniu|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Suplementy `OrderBy`|Suplementy `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Suplementy `OrderBy`|Suplementy `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Uporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Uporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Uporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Uporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Uporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Where%2A> (indeksowane)|Uporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Uporządkowane wyniki|Nieuporządkowane wyniki|  
  
 Nieuporządkowane wyniki nie są aktywnie przełączone; po prostu nie mają zastosowania żadnej specjalnej logiki określania kolejności. W niektórych przypadkach nieuporządkowane zapytanie może zachować kolejność sekwencji źródłowej. W przypadku zapytań, które używają operatora indeksowanego SELECT, PLINQ gwarantuje, że elementy danych wyjściowych będą znajdować się w kolejności rosnących indeksów, ale nie gwarantuje, które indeksy zostaną przypisane do elementów.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
