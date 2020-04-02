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
ms.openlocfilehash: 0e9b4510757fc0f98b2edfbe1c656cdb5f6bce72
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588633"
---
# <a name="order-preservation-in-plinq"></a>Zamawianie zachowywania w PLINQ
W PLINQ celem jest maksymalizacja wydajności przy zachowaniu poprawności. Kwerenda powinna działać tak szybko, jak to możliwe, ale nadal generować poprawne wyniki. W niektórych przypadkach poprawność wymaga zachowania kolejności sekwencji źródłowej; jednak zamawianie może być kosztowne pod względem obliczeniowym. W związku z tym domyślnie PLINQ nie zachowuje kolejność sekwencji źródłowej. Pod tym względem PLINQ [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)]przypomina , ale jest w przeciwieństwie do LINQ do obiektów, który zachowuje kolejność.  
  
 Aby zastąpić zachowanie domyślne, można włączyć zachowanie kolejności <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> przy użyciu operatora w sekwencji źródłowej. Następnie można wyłączyć zachowanie zamówienia w dalszej <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> części kwerendy przy użyciu metody. Przy obu metodach kwerenda jest przetwarzana na podstawie heurystyki, które określają, czy wykonać kwerendę jako równoległą lub sekwencyjną. Aby uzyskać więcej informacji, zobacz [Opis przyspieszenia w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
 W poniższym przykładzie pokazano nieuisorowane kwerendy równoległej, która filtruje dla wszystkich elementów, które pasują do warunku, bez próby uporządkowania wyników w jakikolwiek sposób.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 Ta kwerenda nie musi produkować pierwsze 1000 miast w sekwencji źródłowej, które spełniają warunek, ale raczej niektóre zestaw 1000 miast, które spełniają warunek. Operatory zapytań PLINQ partycji sekwencji źródłowej do wielu podsekwencji, które są przetwarzane jako równoczesnych zadań. Jeśli zachowanie zamówienia nie jest określony, wyniki z każdej partycji są przekazywane do następnego etapu kwerendy w dowolnej kolejności. Ponadto partycja może dać podzbiór jego wyników, zanim będzie nadal przetwarzać pozostałe elementy. Wynikowe zamówienie może być różne za każdym razem. Aplikacja nie może kontrolować tego, ponieważ zależy od tego, jak system operacyjny planuje wątki.  
  
 Poniższy przykład zastępuje zachowanie domyślne <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> przy użyciu operatora w sekwencji źródłowej. Gwarantuje to, <xref:System.Linq.ParallelEnumerable.Take%2A> że metoda zwraca pierwsze 1000 miast w sekwencji źródłowej, które spełniają warunek.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Jednak ta kwerenda prawdopodobnie nie działa tak szybko, jak wersja nieuiszczona, ponieważ musi śledzić oryginalną kolejność w partycjach i w czasie scalania upewnij się, że kolejność jest spójna. W związku z tym <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> zaleca się używać tylko wtedy, gdy jest to wymagane i tylko dla tych części kwerendy, które tego wymagają. Gdy zachowanie porządku nie jest <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> już wymagane, użyj go wyłączyć. Poniższy przykład osiąga to przez tworzenie dwóch zapytań.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 Należy zauważyć, że PLINQ zachowuje kolejność sekwencji produkowane przez operatorów nakładających zamówienia dla pozostałej części kwerendy. Innymi słowy, operatorzy, tacy jak <xref:System.Linq.ParallelEnumerable.OrderBy%2A> i <xref:System.Linq.ParallelEnumerable.ThenBy%2A> są traktowani tak, jakby po niej następowały wezwanie do <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
## <a name="query-operators-and-ordering"></a>Operatory zapytań i zamawianie  
 Następujące operatory zapytań wprowadzają zachowanie zlecania do <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> wszystkich kolejnych operacji w kwerendzie lub dopóki nie zostanie wywołana:  
  
- <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
- <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 Następujące operatory zapytań PLINQ mogą w niektórych przypadkach wymagać uporządkowanych sekwencji źródłowych w celu uzyskania prawidłowych wyników:  
  
- <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
- <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
- <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Niektóre operatory zapytań PLINQ zachowują się inaczej, w zależności od tego, czy ich sekwencja źródłowsza jest uporządkowana, czy nieuiszczona. W poniższej tabeli wymieniono te operatory.  
  
|Operator|Wynik po uporządkowaniu sekwencji źródłowej|Wynik, gdy sekwencja źródłowcza nie jest zauszczony|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Niedeterministyczne wyjście dla operacji niezesocjalnych lub niekomunikacyjnych|Niedeterministyczne wyjście dla operacji niezesocjalnych lub niekomunikacyjnych|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Niedeterministyczne wyjście dla operacji niezesocjalnych lub niekomunikacyjnych|Niedeterministyczne wyjście dla operacji niezesocjalnych lub niekomunikacyjnych|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Uporządkowane wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Uporządkowane wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Uporządkowane wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Zwracany określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Zwracany określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Nieuiarszone wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Zwracany określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Zwracany określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Wykonuje niedeterministycznie równolegle|Wykonuje niedeterministycznie równolegle|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Uporządkowane wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Uporządkowane wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Uporządkowane wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Uporządkowane wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Zwracany określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Zwracany określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Zmienia kolejność kolejności|Rozpoczyna nową sekcję uporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Zmienia kolejność kolejności|Rozpoczyna nową sekcję uporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Nie dotyczy (taka <xref:System.Linq.ParallelEnumerable.AsParallel%2A> sama wartość domyślna jak)|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Nie dotyczy (taka <xref:System.Linq.ParallelEnumerable.AsParallel%2A>sama wartość domyślna jak)|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Odwraca|Nic nie robi.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Uporządkowane wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>(indeksowane)|Uporządkowane wyniki|Nieurządzone wyniki.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Uporządkowane wyniki.|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>(indeksowane)|Uporządkowane wyniki.|Nieurządzone wyniki.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Zamówione porównanie|Nieuiarszone porównanie|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Pomija pierwsze *n* elementy|Pomija wszelkie *n* elementów|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Uporządkowane wyniki.|Rodzaju. Wykonuje SkipWhile w bieżącej dowolnej kolejności|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Niedeterministyczne wyjście dla operacji niezesocjalnych lub niekomunikacyjnych|Niedeterministyczne wyjście dla operacji niezesocjalnych lub niekomunikacyjnych|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Przyjmuje `n` pierwsze elementy|Przyjmuje `n` dowolne elementy|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Uporządkowane wyniki|Rodzaju. Wykonuje TakeWhile na bieżącej dowolnej kolejności|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Suplementy`OrderBy`|Suplementy`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Suplementy`OrderBy`|Suplementy`OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Uporządkowane wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Uporządkowane wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Uporządkowane wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Uporządkowane wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Uporządkowane wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>(indeksowane)|Uporządkowane wyniki|Nieuiarszone wyniki|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Uporządkowane wyniki|Nieuiarszone wyniki|  
  
 Nieuiarszone wyniki nie są aktywnie tasowane; po prostu nie mają żadnej specjalnej logiki zamawiania stosowane do nich. W niektórych przypadkach kwerenda nieuiszczona może zachować kolejność sekwencji źródłowej. W przypadku kwerend korzystających z indeksowanego operatora Select PLINQ gwarantuje, że elementy wyjściowe pojawią się w kolejności rosnących indeksów, ale nie daje żadnych gwarancji, które indeksy zostaną przypisane do których elementów.  
  
## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
