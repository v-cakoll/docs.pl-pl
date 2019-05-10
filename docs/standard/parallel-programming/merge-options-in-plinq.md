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
ms.openlocfilehash: 7255ef11bfdf74afa6ae2032b0c86c8c44dbfe7d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647726"
---
# <a name="merge-options-in-plinq"></a>Opcje scalania w PLINQ
Gdy zapytanie jest wykonywany jako równoległego, PLINQ partycje sekwencji źródłowej wiele wątków może pracować na różnych częściach współbieżnie, zazwyczaj w oddzielnych wątkach. Jeśli wyniki mają być używane w jednym wątku, na przykład w `foreach` (`For Each` w języku Visual Basic) w pętli, a następnie wyniki z każdego wątku muszą być scalone jednej sekwencji. Rodzaj scalania, który wykonuje PLINQ jest zależna od operatorów, które są obecne w zapytaniu. Na przykład operatory, które nakładają nowe zamówienie na wynikach musi buforu wszystkie elementy ze wszystkich wątków. Z punktu widzenia zużywającym wątku (jest to również w przypadku użytkowników aplikacji) pełni buforowane zapytanie może działać zauważalne okres czasu, tworzy jej pierwszego wyniku. Inne operatory domyślnie są częściowo buforowane; dają one ich wyniki w partiach. Jeden operator <xref:System.Linq.ParallelEnumerable.ForAll%2A> nie jest buforowana domyślnie. Natychmiast daje wszystkie elementy ze wszystkich wątków.  
  
 Za pomocą <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> metody, jak pokazano w poniższym przykładzie, można udostępnić wskazówki PLINQ, która wskazuje, jakiego rodzaju scalania do wykonywania.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Aby uzyskać kompletny przykład, zobacz [jak: Określanie opcji scalania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).  
  
 Jeśli określone zapytanie nie obsługuje żądanej opcji, następnie opcję zostanie zignorowane. W większości przypadków jest konieczne określanie opcji scalania dla zapytania PLINQ. Jednak w niektórych przypadkach może się okazać przez testom i pomiarom wykonujący zapytanie najlepiej w trybie innych niż domyślne. Wspólne użycie tej opcji jest wymuszenie operatorem scalanie fragmentu do przesyłania strumieniowego jego wyniki w celu zapewnienia zwiększyć szybkość reakcji interfejsu użytkownika.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 <xref:System.Linq.ParallelMergeOptions> Wyliczenie zawiera następujące opcje, które określają kształtów obsługiwane zapytania, jak uzyskane jest końcowych danych wyjściowych zapytania, gdy wyniki są używane w jednym wątku:  
  
- `Not Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.NotBuffered> Opcja powoduje, że każdy element przetwarzania będą zwracane z każdego wątku, tak szybko, jak są wytwarzane. To zachowanie jest odpowiednikiem "przesyłanie strumieniowe" dane wyjściowe. Jeśli <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operator jest obecne w zapytaniu `NotBuffered` zachowuje kolejność elementów źródła. Mimo że `NotBuffered` rozpoczyna się reaguje wyniki, jak są one dostępne, całkowity czas, aby wygenerować wszystkie wyniki mogą nadal być dłuższa niż przy użyciu jednej z innych opcji scalania.  
  
- `Auto Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.AutoBuffered> Opcja powoduje, że zapytanie, aby zebrać elementy do buforu i okresowo uzyskanie zawartość buforu w całości zużywającym wątku. Jest to analogiczne do otrzymania danych źródłowych w "fragmentów" zamiast "przesyłania strumieniowego" zachowanie `NotBuffered`. `AutoBuffered` może to trwać dłużej niż `NotBuffered` udostępnić pierwszego elementu w zużywającym wątku. Rozmiar buforu i dokładne zachowanie otrzymania nie są konfigurowalne i mogą się różnić, w zależności od różnych czynników, które odnoszą się do zapytania.  
  
- `FullyBuffered`  
  
     <xref:System.Linq.ParallelMergeOptions.FullyBuffered> Opcja powoduje, że całe zapytanie, aby być buforowane, przed dowolne elementy są uzyskane dane wyjściowe. Gdy używasz tej opcji, może to trwać dłużej przed pierwszym elementem jest dostępna w zużywającym wątku, ale pełnych wyników może być jeszcze przedstawiony szybciej niż przy użyciu innych opcji.  
  
## <a name="query-operators-that-support-merge-options"></a>Operatory zapytań, które obsługują opcje scalania  
 W poniższej tabeli wymieniono operatory, które obsługują wszystkie tryby opcja scalania, ograniczeniom określony.  
  
|Operator|Ograniczenia|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Uporządkowane inne niż zapytania, które mają tablicy lub listy tylko źródłowe.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Uporządkowane inne niż zapytania, które mają tablicy lub listy tylko źródłowe.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Brak|  
  
 Wszystkie inne operatory zapytań PLINQ może zignorować opcji scalania podanego przez użytkownika. Niektóre zapytania operatorów, na przykład <xref:System.Linq.ParallelEnumerable.Reverse%2A> i <xref:System.Linq.ParallelEnumerable.OrderBy%2A>, nie można przekazywać dowolne elementy, dopóki wszystkie utworzone i zmieniana. W związku z tym, kiedy <xref:System.Linq.ParallelMergeOptions> jest używany w zapytaniu, które również zawiera takie jak operator <xref:System.Linq.ParallelEnumerable.Reverse%2A>, zachowanie scalania nie będą stosowane w zapytaniu do czasu, po tego operatora tworzył wyniki.  
  
 Niektóre operatory możliwość obsługi opcji scalania zależy od typu sekwencji źródłowej i czy <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operator zostało użyte we wcześniejszej części zapytania. <xref:System.Linq.ParallelEnumerable.ForAll%2A> jest zawsze <xref:System.Linq.ParallelMergeOptions.NotBuffered> ; daje jego elementy natychmiast. <xref:System.Linq.ParallelEnumerable.OrderBy%2A> jest zawsze <xref:System.Linq.ParallelMergeOptions.FullyBuffered>; należy sortować całą listę, przed jego daje.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Instrukcje: Określanie opcji scalania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
