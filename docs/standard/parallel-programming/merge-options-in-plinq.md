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
ms.openlocfilehash: 18f233ac4c5afa63ec31e83d5fff8f0a57f9146f
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204000"
---
# <a name="merge-options-in-plinq"></a>Opcje scalania w PLINQ
Gdy zapytanie jest wykonywane jako Parallel, PLINQ tworzy sekwencję źródłową, dzięki czemu wiele wątków może współdziałać z różnymi częściami, zwykle w oddzielnych wątkach. Jeśli wyniki mają być używane w jednym wątku, na przykład w pętli `foreach` (`For Each` w Visual Basic), wyniki z każdego wątku muszą zostać scalone z powrotem w jedną sekwencję. Rodzaj scalania, który PLINQ wykonuje, zależy od operatorów, które znajdują się w zapytaniu. Na przykład operatory, które nakładają nowe zamówienie na wyniki, muszą buforować wszystkie elementy ze wszystkich wątków. Z punktu widzenia wątku zużywanego (który również użytkownik aplikacji) w pełni buforowane zapytanie może być uruchamiane przez zauważalny okres czasu, zanim wygeneruje swój pierwszy wynik. Inne operatory domyślnie są częściowo buforowane; dają one wyniki w partiach. Jeden operator <xref:System.Linq.ParallelEnumerable.ForAll%2A> domyślnie nie jest buforowany. Powoduje natychmiastowe zwrócenie wszystkich elementów ze wszystkich wątków.  
  
 Za pomocą metody <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>, jak pokazano w poniższym przykładzie, można podać wskazówkę PLINQ, która wskazuje, jaki rodzaj scalania ma być wykonywany.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Aby zapoznać się z kompletnym przykładem, zobacz [How to: Określanie opcji scalania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).  
  
 Jeśli określone zapytanie nie może obsługiwać żądanych opcji, ta opcja zostanie po prostu zignorowana. W większości przypadków nie trzeba określać opcji scalania dla zapytania PLINQ. Jednak w niektórych przypadkach może się okazać, że testy i pomiary są wykonywane najlepiej w trybie innym niż domyślny. Typowym zastosowaniem tej opcji jest wymuszenie przesyłania strumieniowego przez operator scalania fragmentów w celu zapewnienia bardziej reagującego interfejsu użytkownika.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 Wyliczenie <xref:System.Linq.ParallelMergeOptions> obejmuje następujące opcje, które określają, dla obsługiwanych kształtów zapytań, w jaki sposób końcowe dane wyjściowe zapytania są dostarczane, gdy wyniki są używane w jednym wątku:  
  
- `Not Buffered`  
  
     Opcja <xref:System.Linq.ParallelMergeOptions.NotBuffered> powoduje, że każdy przetworzony element ma być zwracany z każdego wątku zaraz po jego wygenerowaniu. To zachowanie jest analogiczne do "przesyłania strumieniowego" danych wyjściowych. Jeśli w zapytaniu występuje operator <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>, `NotBuffered` zachowuje porządek elementów źródłowych. Mimo że `NotBuffered` zaczyna zwracać wyniki od razu po ich udostępnieniu, łączny czas generowania wszystkich wyników może być nadal dłuższy niż użycie jednej z innych opcji scalania.  
  
- `Auto Buffered`  
  
     Opcja <xref:System.Linq.ParallelMergeOptions.AutoBuffered> powoduje, że zapytanie zbiera elementy do bufora, a następnie okresowo przesyła zawartość bufora wszystkie jednocześnie do wątku zużywanego. Jest to analogiczne do wypełniania danych źródłowych w "fragmentach" zamiast używania zachowania "streaming" `NotBuffered`. `AutoBuffered` może trwać dłużej niż `NotBuffered`, aby udostępnić pierwszy element w wątku zużywanym. Rozmiar buforu i dokładne zachowanie nie są konfigurowane i mogą się różnić w zależności od różnych czynników odnoszących się do zapytania.  
  
- `FullyBuffered`  
  
     Opcja <xref:System.Linq.ParallelMergeOptions.FullyBuffered> powoduje, że dane wyjściowe całego zapytania mają być buforowane przed zwróceniem dowolnego elementu. W przypadku korzystania z tej opcji może upłynąć więcej czasu przed udostępnieniem pierwszego elementu w wątku zużywanym, ale kompletne wyniki mogą być nadal tworzone szybciej niż przy użyciu innych opcji.  
  
## <a name="query-operators-that-support-merge-options"></a>Operatory zapytań, które obsługują opcje scalania  
 W poniższej tabeli wymieniono operatory obsługujące wszystkie tryby opcji scalania, z uwzględnieniem określonych ograniczeń.  
  
|Operator|Ograniczenia|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Niezamówione zapytania, które mają tylko źródło tablicy lub listy.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Niezamówione zapytania, które mają tylko źródło tablicy lub listy.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Brak|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Brak|  
  
 Wszystkie inne operatory zapytań PLINQ mogą ignorować opcje scalania udostępniane przez użytkownika. Niektóre operatory zapytań, na przykład <xref:System.Linq.ParallelEnumerable.Reverse%2A> i <xref:System.Linq.ParallelEnumerable.OrderBy%2A>, nie mogą dać żadnych elementów do momentu wygenerowania i zmiany kolejności. W związku z tym, gdy <xref:System.Linq.ParallelMergeOptions> jest używany w zapytaniu, które również zawiera operator, taki jak <xref:System.Linq.ParallelEnumerable.Reverse%2A>, zachowanie scalania nie zostanie zastosowane w zapytaniu, dopóki ten operator nie wygenerował swoich wyników.  
  
 Niektóre operatory obsługujące opcje scalania są zależne od typu sekwencji źródłowej oraz tego, czy operator <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> był wcześniej używany w zapytaniu. <xref:System.Linq.ParallelEnumerable.ForAll%2A> jest zawsze <xref:System.Linq.ParallelMergeOptions.NotBuffered>; natychmiast zwraca swoje elementy. <xref:System.Linq.ParallelEnumerable.OrderBy%2A> jest zawsze <xref:System.Linq.ParallelMergeOptions.FullyBuffered>; Należy posortować całą listę przed jej zwróceniem.  
  
## <a name="see-also"></a>Zobacz także

- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Instrukcje: określanie opcji scalania w PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
