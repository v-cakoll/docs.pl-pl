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
ms.openlocfilehash: 0b98fdcd425ae62aca0149df5136c28edc023bf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591643"
---
# <a name="order-preservation-in-plinq"></a>Zamawianie zachowywania w PLINQ
W PLINQ celem jest zmaksymalizować wydajność przy zachowaniu poprawności. Zapytanie powinien uruchamiana tak szybko jak to możliwe, ale nadal tworzyć poprawnych wyników. W niektórych przypadkach poprawności wymaga kolejność sekwencji źródłowej jest zachowywana; Jednak kolejność może być kosztowne w praktyce. W związku z tym domyślnie PLINQ nie zachowują kolejność sekwencji źródłowej. W tym zakresie podobny PLINQ [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)], ale różni się od LINQ do obiektów, które zachowania kolejności.  
  
 Aby zastąpić zachowanie domyślne, można włączyć zamawianie zachowywania przy użyciu <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operatora w sekwencji źródłowej. Można następnie wyłącz zamawianie zachowywania w dalszej części zapytania przy użyciu <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> metody. Za pomocą obu metod zapytania są przetwarzane w oparciu algorytmu heurystycznego, stwierdzić, czy można wykonać kwerendy w postaci równoległe lub jako kolejnych. Aby uzyskać więcej informacji, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
 W poniższym przykładzie przedstawiono kwerendę równoległych nieuporządkowaną filtrów dla wszystkich elementów spełniających warunek, bez próby kolejność wyników w dowolny sposób.  
  
 [!code-csharp[PLINQ#8](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#8)]
 [!code-vb[PLINQ#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#8)]  
  
 To zapytanie nie musi utworzyć pierwszych 1000 miast w sekwencji źródłowej, które spełniają warunek, ale raczej niektórych zestaw miast 1000, które spełniają warunek. Operatory zapytań PLINQ partycji sekwencji źródłowej do wielu podciągów, które są przetwarzane jako równoczesnych zadań. Jeśli nie określono porządku, wyniki z każdej partycji są przekazane do kolejnego etapu zapytania w dowolnej kolejności. Ponadto partycji może spowodować podzestawu wyników przed kontynuowaniem przetwarzania pozostałych elementów. Wynikowa kolejności mogą różnić się zawsze. Aplikacja nie może kontrolować to, ponieważ zależy od sposobu systemu operacyjnego planuje wątki.  
  
 Poniższy przykład zastępuje domyślne zachowanie przy użyciu <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operatora w sekwencji źródłowej. Gwarantuje to, że <xref:System.Linq.ParallelEnumerable.Take%2A> metoda zwraca pierwszych 1000 miast w sekwencji źródłowej, które spełniają warunek.  
  
 [!code-csharp[PLINQ#9](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#9)]
 [!code-vb[PLINQ#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#9)]  
  
 Jednak to zapytanie prawdopodobnie nie działa tak szybko, jak wersja nieuporządkowaną ponieważ go musi śledzić oryginalnej kolejności w całym partycji i w czasie scalania upewnij się, że kolejność jest spójna. Dlatego zaleca się używanie <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> tylko wtedy, gdy jest to wymagane i tylko dla części zapytania, które tego wymagają. Gdy porządku nie jest już wymagane, użyj <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> jej wyłączenia. Poniższy przykład osiąga to, tworzenie dwa zapytania.  
  
 [!code-csharp[PLINQ#6](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#6)]
 [!code-vb[PLINQ#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#6)]  
  
 Należy pamiętać, że PLINQ zachowa kolejność sekwencję produkowane przez nakładające kolejność operatorów w pozostałej części zapytania. Innymi słowy, operatory, takie jak <xref:System.Linq.ParallelEnumerable.OrderBy%2A> i <xref:System.Linq.ParallelEnumerable.ThenBy%2A> są traktowane tak, jakby były następuje wywołanie <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>.  
  
## <a name="query-operators-and-ordering"></a>Operatory zapytań i kolejność  
 Zamawianie zachowywania do wszystkich kolejnych operacji w zapytaniu lub do czasu wprowadzenie następujących operatorów zapytań <xref:System.Linq.ParallelEnumerable.AsUnordered%2A> nosi nazwę:  
  
-   <xref:System.Linq.ParallelEnumerable.OrderBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenBy%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>  
  
 W niektórych przypadkach następujących operatorów zapytań PLINQ mogą wymagać sekwencji uporządkowanej źródła do produkcji poprawnych wyników:  
  
-   <xref:System.Linq.ParallelEnumerable.Reverse%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.TakeWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.SkipWhile%2A>  
  
-   <xref:System.Linq.ParallelEnumerable.Zip%2A>  
  
 Niektóre operatorów zapytań PLINQ zachowywać się inaczej, w zależności od tego, czy uporządkowane lub nieuporządkowane ich sekwencji źródłowej. W poniższej tabeli wymieniono te podmioty.  
  
|Operator|Wynik po porządkowania sekwencji źródłowej|Wynik przypadku nieuporządkowanych sekwencji źródłowej|  
|--------------|------------------------------------------------|--------------------------------------------------|  
|<xref:System.Linq.ParallelEnumerable.Aggregate%2A>|Tego rodzaju dane wyjściowe nonassociative lub noncommutative operacji|Tego rodzaju dane wyjściowe nonassociative lub noncommutative operacji|  
|<xref:System.Linq.ParallelEnumerable.All%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Any%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Average%2A>|Tego rodzaju dane wyjściowe nonassociative lub noncommutative operacji|Tego rodzaju dane wyjściowe nonassociative lub noncommutative operacji|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.Count%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Distinct%2A>|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.ElementAt%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.ElementAtOrDefault%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.Except%2A>|Wyniki nieuporządkowaną|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.First%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.FirstOrDefault%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.ForAll%2A>|Niejednoznaczny wykonuje równolegle|Niejednoznaczny wykonuje równolegle|  
|<xref:System.Linq.ParallelEnumerable.GroupBy%2A>|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.GroupJoin%2A>|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.Intersect%2A>|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.Join%2A>|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.Last%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.LastOrDefault%2A>|Zwraca określony element|Dowolny element|  
|<xref:System.Linq.ParallelEnumerable.LongCount%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Min%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.OrderBy%2A>|Zmienia kolejność sekwencji|Uruchamia nowe uporządkowane sekcji|  
|<xref:System.Linq.ParallelEnumerable.OrderByDescending%2A>|Zmienia kolejność sekwencji|Uruchamia nowe uporządkowane sekcji|  
|<xref:System.Linq.ParallelEnumerable.Range%2A>|Nie dotyczy (domyślna takie same jak <xref:System.Linq.ParallelEnumerable.AsParallel%2A> )|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Repeat%2A>|Nie dotyczy (domyślna takie same jak <xref:System.Linq.ParallelEnumerable.AsParallel%2A>)|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Odwraca|Nic nie robi.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.Select%2A> (indeksowane)|Uporządkowanych wyników|Nieuporządkowaną wyniki.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Uporządkowanych wyników.|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A> (indeksowane)|Uporządkowanych wyników.|Nieuporządkowaną wyniki.|  
|<xref:System.Linq.ParallelEnumerable.SequenceEqual%2A>|Porównanie uporządkowane|Porównanie nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.Single%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.SingleOrDefault%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Pomija najpierw *n* elementów|Pomija wszelkie *n* elementów|  
|<xref:System.Linq.ParallelEnumerable.SkipWhile%2A>|Uporządkowanych wyników.|Tego rodzaju. Wykonuje SkipWhile dowolnego bieżącego zamówienia|  
|<xref:System.Linq.ParallelEnumerable.Sum%2A>|Tego rodzaju dane wyjściowe nonassociative lub noncommutative operacji|Tego rodzaju dane wyjściowe nonassociative lub noncommutative operacji|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Pobiera pierwszy `n` elementów|Przyjmuje żadnego `n` elementów|  
|<xref:System.Linq.ParallelEnumerable.TakeWhile%2A>|Uporządkowanych wyników|Tego rodzaju. Wykonuje TakeWhile dowolnego bieżącego zamówienia|  
|<xref:System.Linq.ParallelEnumerable.ThenBy%2A>|Dodatki `OrderBy`|Dodatki `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ThenByDescending%2A>|Dodatki `OrderBy`|Dodatki `OrderBy`|  
|<xref:System.Linq.ParallelEnumerable.ToArray%2A>|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.ToDictionary%2A>|Nie dotyczy|Nie dotyczy|  
|<xref:System.Linq.ParallelEnumerable.ToList%2A>|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.ToLookup%2A>|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.Union%2A>|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.Where%2A> (indeksowane)|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
|<xref:System.Linq.ParallelEnumerable.Zip%2A>|Uporządkowanych wyników|Wyniki nieuporządkowaną|  
  
 Wyniki nieuporządkowaną nie są aktywnie przemieszane; po prostu nie mają żadnych specjalnych logiki porządkowania zastosowanych do nich. W niektórych przypadkach nieuporządkowaną zapytania mogą zachować kolejność sekwencji źródłowej. Dla zapytań używających indeksowanego wybierz operator PLINQ gwarantuje, że elementy danych wyjściowych rozpocznie kolejności rosnącej indeksy, ale udziela żadnych gwarancji dotyczących indeksów, które zostaną przypisane do elementów.  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
