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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138221"
---
# <a name="order-preservation-in-plinq"></a>Zamawianie zachowywania w PLINQ
W PLINQ celem jest maksymalizacja wydajności przy zachowaniu poprawności. Kwerenda powinna działać tak szybko, jak to możliwe, ale nadal daje poprawne wyniki. W niektórych przypadkach poprawność wymaga zachowania kolejności sekwencji źródłowej; jednak zamawianie może być obliczeniowo kosztowne. W związku z tym domyślnie PLINQ nie zachowuje kolejność sekwencji źródłowej. W związku z tym PLINQ przypomina [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)], ale jest w przeciwieństwie do LINQ do obiektów, który zachowuje kolejność.  
  
 Aby zastąpić zachowanie domyślne, można włączyć zachowanie kolejności <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> za pomocą operatora w sekwencji źródłowej. Następnie można wyłączyć zachowanie kolejności później w <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> kwerendzie przy użyciu metody. W przypadku obu metod kwerenda jest przetwarzana na podstawie heurystyki, które określają, czy wykonać kwerendę jako równoległą, czy sekwencyjną. Aby uzyskać więcej informacji, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
 W poniższym przykładzie przedstawiono nieuporządkowaną kwerendę równoległą, która filtruje wszystkie elementy, które odpowiadają warunkom, bez próby uporządkowania wyników w jakikolwiek sposób.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 Ta kwerenda nie musi produkować pierwsze 1000 miast w sekwencji źródłowej, które spełniają warunek, ale raczej niektóre zestaw 1000 miast, które spełniają warunek. Operatorzy kwerend PLINQ dzielisekwencję źródłową na wiele podsekwencji przetwarzanych jako równoczesne zadania. Jeśli zachowanie kolejności nie jest określony, wyniki z każdej partycji są przekazywane do następnego etapu kwerendy w dowolnej kolejności. Ponadto partycja może przynieść podzbiór jego wyników, zanim będzie nadal przetwarzać pozostałe elementy. Wynikowa kolejność może być inna za każdym razem. Aplikacja nie może kontrolować to, ponieważ zależy od tego, jak system operacyjny planuje wątki.  
  
 Poniższy przykład zastępuje domyślne zachowanie przy <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> użyciu operatora w sekwencji źródłowej. Gwarantuje to, <xref:System.Linq.ParallelEnumerable.Take%2A> że metoda zwraca pierwsze 1000 miast w sekwencji źródłowej, które spełniają warunek.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Jednak ta kwerenda prawdopodobnie nie działa tak szybko, jak wersja nieuporządkowana, ponieważ musi śledzić oryginalne porządki w partycjach i w czasie scalania upewnij się, że kolejność jest spójna. W związku z tym <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> zaleca się, aby używać tylko wtedy, gdy jest to wymagane i tylko dla tych części kwerendy, które tego wymagają. Gdy zachowanie zamówienia nie jest <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> już wymagane, należy go wyłączyć. Poniższy przykład osiąga to przez redagowanie dwóch zapytań.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 Należy zauważyć, że PLINQ zachowuje kolejność sekwencji produkowane przez operatorów nakładających kolejność dla reszty kwerendy. Innymi słowy, operatorzy tacy jak <xref:System.Linq.ParallelEnumerable.OrderBy%2A> i <xref:System.Linq.ParallelEnumerable.ThenBy%2A> są traktowani <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>tak, jakby następuje im wezwanie do .  
  
## <a name="query-operators-and-ordering"></a>Operatory zapytań i zamawianie  
 Następujące operatory kwerend wprowadzają zachowanie kolejności do wszystkich <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> kolejnych operacji w kwerendzie lub do momentu, gdy zostanie wywołany:  
  
- <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 Następujące operatory zapytań PLINQ mogą w niektórych przypadkach wymagać uporządkowanych sekwencji źródłowych w celu uzyskania poprawnych wyników:  
  
- <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
- <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Niektóre operatory zapytań PLINQ zachowują się inaczej, w zależności od tego, czy ich sekwencja źródłowa jest uporządkowana, czy nieuporządkowana. W poniższej tabeli wymieniono te operatory.  
  
|Operator|Wynik, gdy kolejność sekwencji źródłowej|Wynik, gdy sekwencja źródłowa jest nieuporządkowana|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Produkcja niedeterministyczna dla operacji nieasocjacyjnych lub niekomunikacyjnej|Produkcja niedeterministyczna dla operacji nieasocjacyjnych lub niekomunikacyjnej|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Produkcja niedeterministyczna dla operacji nieasocjacyjnych lub niekomunikacyjnej|Produkcja niedeterministyczna dla operacji nieasocjacyjnych lub niekomunikacyjnej|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Zamówione wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Zamówione wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Zamówione wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Nieuporządkowane wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Wykonuje nondeterministically równolegle|Wykonuje nondeterministically równolegle|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Zamówione wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Zamówione wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Zamówione wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Zamówione wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Zmienia kolejność sekwencji|Rozpoczyna nową uporządkowana sekcja|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Zmienia kolejność sekwencji|Rozpoczyna nową uporządkowana sekcja|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Nie dotyczy (takie <xref:System.Linq.ParallelEnumerable.AsParallel%2A> samo ustawienie domyślne jak )|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Nie dotyczy (takie <xref:System.Linq.ParallelEnumerable.AsParallel%2A>samo ustawienie domyślne jak )|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Odwraca|Nic nie robi.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Zamówione wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>(indeksowane)|Zamówione wyniki|Wyniki nieuporządkowane.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Uporządkowane wyniki.|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>(indeksowane)|Uporządkowane wyniki.|Wyniki nieuporządkowane.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Uporządkowane porównanie|Porównanie nieuporządkowane|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Pomija pierwsze *n* elementów|Pomija wszystkie *n* elementy|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Uporządkowane wyniki.|Rodzaju. Wykonuje SkipWhile na bieżącej kolejności dowolnych|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Produkcja niedeterministyczna dla operacji nieasocjacyjnych lub niekomunikacyjnej|Produkcja niedeterministyczna dla operacji nieasocjacyjnych lub niekomunikacyjnej|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Pobiera `n` pierwsze elementy|Bierze `n` dowolne elementy|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Zamówione wyniki|Rodzaju. Wykonuje TakeWhile na bieżącej kolejności dowolnych|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Suplementy`OrderBy`|Suplementy`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Suplementy`OrderBy`|Suplementy`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Zamówione wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Zamówione wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Zamówione wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Zamówione wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Zamówione wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>(indeksowane)|Zamówione wyniki|Nieuporządkowane wyniki|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Zamówione wyniki|Nieuporządkowane wyniki|  
  
 Nieuporządkowane wyniki nie są aktywnie tasowane; po prostu nie mają do nich zastosowania żadnej specjalnej logiki zamawiania. W niektórych przypadkach nieuporządkowane zapytanie może zachować kolejność sekwencji źródłowej. W przypadku kwerend korzystających z indeksowaneselect operatora, PLINQ gwarantuje, że elementy wyjściowe wyjdzie w kolejności zwiększenie indeksów, ale nie daje żadnych gwarancji, które indeksy zostaną przypisane do których elementów.  
  
## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
