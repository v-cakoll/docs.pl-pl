---
title: Opcje scalania w PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, merge options
ms.assetid: e8f7be3b-88de-4f33-ab14-dc008e76c1ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7df080185db9631e47bb7a886f6e0db894974a6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="merge-options-in-plinq"></a>Opcje scalania w PLINQ
Gdy kwerendy jest wykonywany jako równoległe, partycje PLINQ sekwencji źródłowej tak, aby wiele wątków może działać na różnych części jednocześnie, zwykle w oddzielnych wątkach. Jeśli wyniki mają być używane w jednym wątku, na przykład w `foreach` (`For Each` w języku Visual Basic) w pętli, a następnie wyniki każdego wątku musi być scalone jedną sekwencję. Rodzaj operacji scalania, który wykonuje PLINQ zależy od operatory, które znajdują się w zapytaniu. Na przykład operatory, które nakładają zamówienie nowe wyniki musi bufor wszystkie elementy ze wszystkich wątków. Z perspektywy odbierającą wątku (która jest również użytkownik aplikacji) pełni buforowane zapytanie może działać zauważalne okres czasu, po upływie generuje jego pierwszego wyniku. Inne operatory domyślnie są częściowo buforowane; dają one ich wyniki w partiach. Jeden operator <xref:System.Linq.ParallelEnumerable.ForAll%2A> nie jest buforowana domyślnie. Go zwraca wszystkie elementy ze wszystkich wątków natychmiast.  
  
 Za pomocą <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> — metoda, jak pokazano w poniższym przykładzie, możesz podać wskazówkę do PLINQ, która wskazuje, jaki rodzaj scalania do wykonywania.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Aby uzyskać pełny przykład, zobacz [porady: Określanie opcji scalania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).  
  
 Jeśli kwerendy nie obsługuje żądanej opcji, następnie opcję zostanie zignorowane. W większości przypadków jest konieczne określanie opcji scalania w zapytaniu PLINQ. Jednak w niektórych przypadkach może się okazać polegająca na przetestowaniu i pomiar wykonujący zapytanie najlepiej w trybie innych niż domyślne. Typowe użycie tej opcji jest wymuszenie operatorem scalanie fragmentu do strumienia wyniki w celu zapewnienia poprawę reakcji interfejsu użytkownika.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 <xref:System.Linq.ParallelMergeOptions> Wyliczenie zawiera następujące opcje, które określają kształtów obsługiwane zapytania, jak jest zwróciło ostateczne dane wyjściowe zapytania, gdy wyniki są używane w jednym wątku:  
  
-   `Not Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.NotBuffered> Opcja powoduje, że każdy element przetworzonych mają być zwracane przez każdy wątek, jak produkcji. To zachowanie jest odpowiednikiem "przesyłania strumieniowego" dane wyjściowe. Jeśli <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operator jest obecne w zapytaniu, `NotBuffered` zachowuje kolejność elementów źródła. Mimo że `NotBuffered` uruchamia reaguje wyniki, jak są one dostępne, łączny czas do produkcji wszystkie wyniki mogą nadal być dłuższa niż przy użyciu jednej z opcji scalania.  
  
-   `Auto Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.AutoBuffered> Opcja powoduje, że kwerenda Zbieranie elementów do buforu i okresowo uzyskanie zawartości buforu jednocześnie odbierającą wątku. To jest odpowiednikiem reaguje danych źródłowych w "fragmentów" zamiast "przesyłania strumieniowego" zachowanie `NotBuffered`. `AutoBuffered` może trwać dłużej niż `NotBuffered` Aby udostępnić pierwszego elementu w wątku odbierającą. Rozmiar buforu i dokładne zachowanie otrzymania nie są konfigurowalne i może się różnić, w zależności od różnych czynników, które odnoszą się do zapytania.  
  
-   `FullyBuffered`  
  
     <xref:System.Linq.ParallelMergeOptions.FullyBuffered> Opcja powoduje, że dane wyjściowe całego zapytania do buforowane przed są zwróciło żadnego z elementów. Tej opcji może potrwać dłużej przed pierwszym elementem jest dostępna w wątku odbierającą, ale pełnych wyników może być jeszcze przedstawiony szybsza niż przy użyciu innych opcji.  
  
## <a name="query-operators-that-support-merge-options"></a>Operatory zapytań, które obsługują opcje scalania  
 W poniższej tabeli wymieniono operatory, które obsługują wszystkie tryby opcja scalania, ograniczeniom określony.  
  
|Operator|Ograniczenia|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Kwerend uporządkowane inne niż, które mają tablicy lub listy źródła tylko.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Kwerend uporządkowane inne niż, które mają tablicy lub listy źródła tylko.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Brak|  
  
 Wszystkie inne operatorów zapytań PLINQ może Ignoruj opcje scalania dostarczane przez użytkownika. Niektóre zapytania operatorów, na przykład <xref:System.Linq.ParallelEnumerable.Reverse%2A> i <xref:System.Linq.ParallelEnumerable.OrderBy%2A>, nie można przekazywać wszelkie elementy, dopóki wszystkie utworzone i kolejności. W związku z tym, kiedy <xref:System.Linq.ParallelMergeOptions> jest używany w zapytaniu, które również zawiera operator, takie jak <xref:System.Linq.ParallelEnumerable.Reverse%2A>, zachowanie scalania nie zostaną zastosowane w zapytaniu do czasu, po operatora przedstawiają wyniki.  
  
 Niektóre operatory możliwość obsługi opcji scalania zależy od typu sekwencji źródłowej i czy <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operator zostało użyte we wcześniejszej części zapytania. <xref:System.Linq.ParallelEnumerable.ForAll%2A> zawsze <xref:System.Linq.ParallelMergeOptions.NotBuffered> ; daje jej elementy natychmiast. <xref:System.Linq.ParallelEnumerable.OrderBy%2A> zawsze <xref:System.Linq.ParallelMergeOptions.FullyBuffered>; należy sortować całą listę, przed jego daje.  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Instrukcje: określanie opcji scalania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
