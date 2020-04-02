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
ms.openlocfilehash: 623466e0e960ea991ae92e5de432171b70bad1d2
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588616"
---
# <a name="merge-options-in-plinq"></a>Opcje scalania w PLINQ
Gdy kwerenda jest wykonywana jako równoległa, PLINQ partycje sekwencji źródłowej, tak aby wiele wątków może pracować na różnych częściach jednocześnie, zazwyczaj na oddzielnych wątków. Jeśli wyniki mają być używane w jednym wątku, `foreach` `For Each` na przykład w (w języku Visual Basic) pętli, a następnie wyniki z każdego wątku muszą być scalone z powrotem w jednej sekwencji. Rodzaj scalania, który wykonuje PLINQ zależy od operatorów, które są obecne w kwerendzie. Na przykład operatory, które nakładają nowe zamówienie na wyniki musi buforować wszystkie elementy ze wszystkich wątków. Z punktu widzenia wątku zużywającego (który jest również użytkownika aplikacji) w pełni buforowane zapytanie może działać przez zauważalny okres czasu, zanim wygeneruje swój pierwszy wynik. Inne operatory, domyślnie, są częściowo buforowane; dają one swoje wyniki w partiach. Jeden operator, <xref:System.Linq.ParallelEnumerable.ForAll%2A> nie jest buforowany domyślnie. Natychmiast daje wszystkie elementy ze wszystkich wątków.  
  
 Za pomocą <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> metody, jak pokazano w poniższym przykładzie, można podać wskazówkę do PLINQ, który wskazuje, jakiego rodzaju scalania do wykonania.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Aby uzyskać pełny przykład, zobacz [Jak: Określanie opcji scalania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).  
  
 Jeśli określone zapytanie nie może obsługiwać żądanej opcji, opcja zostanie po prostu zignorowana. W większości przypadków nie trzeba określać opcji scalania dla zapytania PLINQ. Jednak w niektórych przypadkach może się okazać, testując i miarę, że kwerenda wykonuje najlepiej w trybie nie-domyślnym. Typowym zastosowaniem tej opcji jest wymuszenie operatora scalania fragmentów do przesyłania strumieniowego jego wyników w celu zapewnienia bardziej responsywnego interfejsu użytkownika.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions (Nieskładki równoległe)  
 Wyliczenie <xref:System.Linq.ParallelMergeOptions> zawiera następujące opcje, które określają, dla obsługiwanych kształtów kwerendy, jak końcowe dane wyjściowe kwerendy jest uzyskiwał, gdy wyniki są używane w jednym wątku:  
  
- `Not Buffered`  
  
     Opcja <xref:System.Linq.ParallelMergeOptions.NotBuffered> powoduje, że każdy przetworzony element ma być zwracany z każdego wątku, jak tylko jest produkowany. To zachowanie jest analogiczne do "przesyłania strumieniowego" danych wyjściowych. Jeśli <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operator jest obecny w `NotBuffered` kwerendzie, zachowuje kolejność elementów źródłowych. Mimo `NotBuffered` że zaczyna przynosić wyniki, gdy tylko są one dostępne, całkowity czas na uzyskanie wszystkich wyników może być dłuższy niż przy użyciu jednej z innych opcji scalania.  
  
- `Auto Buffered`  
  
     Opcja <xref:System.Linq.ParallelMergeOptions.AutoBuffered> powoduje, że kwerenda do zbierania elementów do buforu, a następnie okresowo dają zawartość buforu na raz do wątku zużywającego. Jest to analogiczne do uzyskania danych źródłowych w "fragmentach" zamiast `NotBuffered`używania zachowania "przesyłania strumieniowego" . `AutoBuffered`może potrwać `NotBuffered` dłużej niż udostępnienie pierwszego elementu na wątku zużywającym. Rozmiar buforu i dokładne zachowanie wydajności nie są konfigurowalne i mogą się różnić, w zależności od różnych czynników, które odnoszą się do kwerendy.  
  
- `FullyBuffered`  
  
     Opcja <xref:System.Linq.ParallelMergeOptions.FullyBuffered> powoduje, że dane wyjściowe całej kwerendy mają być buforowane przed którykolwiek z elementów są yielded. Korzystając z tej opcji, może upłynąć dłużej, zanim pierwszy element jest dostępny w wątku zużywającym, ale pełne wyniki mogą być nadal produkowane szybciej niż przy użyciu innych opcji.  
  
## <a name="query-operators-that-support-merge-options"></a>Operatory kwerend obsługujące opcje korespondencji seryjnej  
 W poniższej tabeli wymieniono operatory obsługujące wszystkie tryby opcji scalania, z zastrzeżeniem określonych ograniczeń.  
  
|Operator|Ograniczenia|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Niezamówione kwerendy, które mają tylko źródło tablicy lub listy.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Niezamówione kwerendy, które mają tylko źródło tablicy lub listy.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Brak|  
  
 Wszystkie inne operatory zapytań PLINQ mogą ignorować opcje scalania dostarczone przez użytkownika. Niektóre operatory zapytań, <xref:System.Linq.ParallelEnumerable.OrderBy%2A>na przykład i , nie może przynieść żadnych elementów, <xref:System.Linq.ParallelEnumerable.Reverse%2A> dopóki wszystkie zostały wyprodukowane i zsprzedane. W związku <xref:System.Linq.ParallelMergeOptions> z tym gdy jest używany w <xref:System.Linq.ParallelEnumerable.Reverse%2A>kwerendzie, która zawiera również operator, takich jak , zachowanie scalania nie zostaną zastosowane w kwerendzie, dopóki operator nie przyniosły jego wyniki.  
  
 Możliwość niektórych operatorów do obsługi opcji scalania zależy od <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> typu sekwencji źródłowej i czy operator był używany wcześniej w kwerendzie. <xref:System.Linq.ParallelEnumerable.ForAll%2A>jest <xref:System.Linq.ParallelMergeOptions.NotBuffered> zawsze ; natychmiast daje swoje elementy. <xref:System.Linq.ParallelEnumerable.OrderBy%2A>jest <xref:System.Linq.ParallelMergeOptions.FullyBuffered>zawsze ; musi posortować całą listę, zanim się podda.  
  
## <a name="see-also"></a>Zobacz też

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
- [Instrukcje: określanie opcji scalania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
