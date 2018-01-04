---
title: Niestandardowe partycjonery dla PLINQ i TPL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, partitioners
ms.assetid: 96153688-9a01-47c4-8430-909cee9a2887
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bc409a528dd095d3defb0026a48430b10a3ba6f3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>Niestandardowe partycjonery dla PLINQ i TPL
Do parallelize operacji na źródle danych, jest jednym z podstawowych kroków do *partycji* źródła do sekcje, które mogą być jednocześnie udostępniane przez wiele wątków. PLINQ i zadania biblioteki równoległych (TPL) zapewniają partycjonery domyślne, które działają w sposób przezroczysty podczas pisania zapytania równoległe lub <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli. Dla bardziej zaawansowanych scenariuszy można dodać własne partycjonera.  
  
## <a name="kinds-of-partitioning"></a>Rodzaje partycjonowania  
 Istnieje wiele sposobów do partycjonowania źródła danych. Najbardziej efektywne podejścia wiele wątków współpracują w celu procesu oryginalnej sekwencji źródłowej, a nie fizycznie rozdzielić wiele podciągów źródła. Tablice i innych indeksowania źródeł takich jak <xref:System.Collections.IList> kolekcji, której długość jest znany wcześniej, *zakresu partycjonowania* jest najprostsza rodzaj partycji. Każdy wątek otrzymuje unikatowy otwierające i zamykające indeksów, tak, aby jego zakres źródła może przetwarzać bez zastąpienia lub zastąpieniem przez innego wątku. Tylko obciążenie związane z zakresem Partycjonowanie jest początkowej pracy tworzenia zakresów; Synchronizacja nie dodatkowe jest wymagany po tym. W związku z tym go zapewniają dobrą wydajność, jak długo obciążenie jest dzielone równomiernie. Wadą partycjonowania zakres jest, że jeśli jeden wątek zakończy się wcześniej, nie będzie pomocna wątki, Zakończ pracę.  
  
 W przypadku list połączonych lub innych kolekcji, której długość jest nieznany, można użyć *partycjonowania fragmentu*. W fragmentu partycje, każdy wątek lub zadanie w równoległej pętli lub kwerendy zużywa pewną liczbę elementów źródła w jednym fragmencie, przetwarza je i następnie wróci do pobrania dodatkowych elementów. Obiekt partitioner zapewnia, że wszystkie elementy są dystrybuowane i czy nie ma duplikatów. Fragment może być dowolnym rozmiarze. Na przykład obiekt partitioner przedstawionej w [porady: Implementowanie partycji dynamicznych](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md) tworzy fragmentów, które zawierają tylko jeden element. Tak długo, jak fragmentów nie są zbyt duże, tego rodzaju partycjonowania wynika z założenia równoważenia obciążenia przypisania elementów wątków nie jest określona wstępnie. Jednak obiekt partitioner nakładu synchronizacji zawsze musi pobrać fragmentu innego wątku. Ilość synchronizacji opłatą w tych przypadkach jest odwrotnie proporcjonalny do rozmiaru fragmenty.  
  
 Ogólnie rzecz biorąc partycjonowanie zakresu tylko jest szybsze, gdy czas wykonania delegata jest mały, aby średnie i źródło zawiera dużą liczbę elementów i Praca całkowita każda partycja jest w przybliżeniu. W związku z tym jest zwykle szybsze w większości przypadków partycjonowania fragmentu. Na źródeł z mniejszą liczbą elementów lub wydłużenie czasu wykonywania dla obiekt delegowany następnie wydajność fragmentów i partycjonowania zakres jest o równości.  
  
 Partycjonery TPL obsługuje również dynamiczne liczby partycji. Oznacza to, mogą utworzyć partycji na bieżąco, na przykład, jeśli <xref:System.Threading.Tasks.Parallel.ForEach%2A> nowego zadania spowoduje utworzenie pętli. Ta funkcja umożliwia obiekt partitioner skalowanie wraz z pętli się. Partycjonery dynamiczne są również z założenia równoważenia obciążenia. Podczas tworzenia niestandardowego partycjonera musi obsługiwać partycjonowanie dynamiczne być dostępne z <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli.  
  
### <a name="configuring-load-balancing-partitioners-for-plinq"></a>Konfigurowanie Partycjonery dla PLINQ równoważenia obciążenia  
 Niektóre przeciążeń <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metody pozwalają tworzyć partycjonera dla tablicy lub <xref:System.Collections.IList> źródła i określ, czy mają podejmować próbę celu zrównoważenia obciążenia między wątki. Gdy obiekt partitioner jest skonfigurowany do równoważenia obciążenia, partycjonowanie fragmentu jest używana, a elementy są przekazywane do każdej partycji w małych fragmentów zgodnie z żądania. Takie podejście ułatwia, upewnij się, że wszystkie partycje mają elementy do przetworzenia do całego pętli lub wykonać kwerendy. Dodatkowe przeciążenia może służyć do zapewnienia, równoważenia obciążenia partycjonowania dowolnego <xref:System.Collections.IEnumerable> źródła.  
  
 Ogólnie rzecz biorąc równoważenia obciążenia wymaga partycje, które mają elementy stosunkowo występują częste żądania z obiekt partitioner. Z kolei partycjonerem, który jest partycjonowania statycznego można przypisać elementy do każdego partycjonera jednocześnie za pomocą zakresu lub fragmentu partycjonowania. Wymaga to mniejsze koszty niż Równoważenie obciążenia, ale może wymagać więcej czasu wykonania, jeśli jeden wątek kończy znacznie więcej pracy od innych. Domyślnie przekazywana IList lub tablicy, PLINQ zawsze używa zakresu partycjonowania bez równoważenia obciążenia. Aby włączyć funkcję równoważenia obciążenia dla PLINQ, należy użyć `Partitioner.Create` metody, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
 [!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]  
  
 Najlepszy sposób, aby ustalić, czy używać obciążenia równoważenia w dowolnym danego scenariusza jest eksperymentu do mierzenia czas potrzebny na zakończenie reprezentatywny obciążeń i konfiguracji komputerów operacji. Na przykład partycjonowania statycznego może zawierać znaczące przyspieszenie komputera wielordzeniowych, który ma tylko kilka rdzeni, ale może to spowodować spowolnienie na komputerach, które mają względnie wiele rdzeni.  
  
 W poniższej tabeli wymieniono dostępne przeciążenia <xref:System.Collections.Concurrent.Partitioner.Create%2A> metody. Partycjonery te nie są ograniczone do użycia tylko z PLINQ lub <xref:System.Threading.Tasks.Task>. Można można również używać razem niestandardowych konstrukcji równoległych.  
  
|Przeciążenia|Używa funkcji równoważenia obciążenia|  
|--------------|-------------------------|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Zawsze|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Gdy logiczną argumentu jest określona jako wartość true|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Gdy logiczną argumentu jest określona jako wartość true|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|Nigdy nie|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|Nigdy nie|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|Nigdy nie|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|Nigdy nie|  
  
### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Konfigurowanie statycznego zakresu Partycjonery dla Parallel.ForEach  
 W <xref:System.Threading.Tasks.Parallel.For%2A> pętli, treści pętli jest przekazane do metody jako pełnomocnik. Koszt wywoływania ten delegat jest o taki sam jak wywołanie metody wirtualnej. W niektórych scenariuszach może być duże, że koszt wywołanie delegata w każdej iteracji pętli staje się znaczące treści równoległej pętli. W takich sytuacjach należy użyć jednej z <xref:System.Collections.Concurrent.Partitioner.Create%2A> przeciążenia, aby utworzyć <xref:System.Collections.Generic.IEnumerable%601> zakres partycji za pośrednictwem elementy źródłowe. Następnie można przekazać tej kolekcji zakresów <xref:System.Threading.Tasks.Parallel.ForEach%2A> metody, których treść składa się z zwykły `for` pętli. Zaletą tej metody jest, że koszt wywołania delegata poniesienia tylko raz na zakres, a nie raz dla każdego elementu. W poniższym przykładzie pokazano podstawowy wzorzec.  
  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Każdy wątek w pętli odbiera własną <xref:System.Tuple%602> zawiera początkową i końcową indeksu w określonym zakresie podrzędnych. Wewnętrzny `for` pętli używa `fromInclusive` i `toExclusive` wartości do pętli tablicy lub <xref:System.Collections.IList> bezpośrednio.  
  
 Jeden z <xref:System.Collections.Concurrent.Partitioner.Create%2A> przeciążenia pozwala określić rozmiar partycji i liczby partycji. To przeciążenie może służyć w scenariuszach, w przypadku tak niskie, że wywołanie metody wirtualnej nawet jednego na element ma zauważalnego wpływu na wydajność pracy dla każdego elementu.  
  
## <a name="custom-partitioners"></a>Niestandardowe Partycjonery  
 W niektórych scenariuszach może być zastanowić lub nawet musi implementować własne partycjonera. Na przykład może mieć klasy niestandardowej kolekcji, która można podzielić efektywniej niż domyślne partycjonery mogą oparte na swoją wiedzę na temat wewnętrznej struktury klasy. Możesz też utworzyć zakres partycji o różnych rozmiarach oparte na swoją wiedzę na temat jak długo trwa proces elementów w różnych lokalizacjach w kolekcji źródłowej.  
  
 Aby utworzyć podstawowy partycjonera niestandardowych, klasa wyprowadzona z <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> i zastąpić metody wirtualne zgodnie z opisem w poniższej tabeli.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Ta metoda jest wywoływana raz przez wątku głównego i zwraca IList(IEnumerator(TSource)). Każdy wątek roboczy w pętli lub kwerendy można wywołać `GetEnumerator` na liście, aby pobrać <xref:System.Collections.Generic.IEnumerator%601> za pośrednictwem różnych partycji.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Zwraca `true` po zastosowaniu <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, w przeciwnym razie `false`.|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|Jeśli <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> jest `true`, opcjonalnie można wywołać tej metody zamiast <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Jeśli wyniki musi być sortowanie lub wymagają indeksowanego dostępu do elementów, następnie pochodzi od <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> i zastąp jego metody wirtualne zgodnie z opisem w poniższej tabeli.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Ta metoda jest wywoływana raz przez wątku głównego i zwraca `IList(IEnumerator(TSource))`. Każdy wątek roboczy w pętli lub kwerendy można wywołać `GetEnumerator` na liście, aby pobrać <xref:System.Collections.Generic.IEnumerator%601> za pośrednictwem różnych partycji.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Zwraca `true` po zastosowaniu <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>; w przeciwnym razie wartość false.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|Zwykle, to po prostu wywołuje <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|Jeśli <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> jest `true`, opcjonalnie można wywołać tej metody zamiast <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 W poniższej tabeli przedstawiono dodatkowe szczegółowe informacje na temat trzy rodzaje wdrożenie równoważenia obciążenia partycjonery <xref:System.Collections.Concurrent.OrderablePartitioner%601> klasy.  
  
|Metoda/właściwość|IList / tablicy bez równoważenia obciążenia|IList / tablicy z równoważeniem obciążenia|Interfejs IEnumerable|  
|----------------------|-------------------------------------------|----------------------------------------|-----------------|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Używa partycjonowania zakresu|Używa fragmentu partycjonowania zoptymalizowane pod kątem list dla partitionCount określony|Używa fragmentu partycjonowania tworząc statycznych liczby partycji.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|Obsługiwane nie zgłasza wyjątku|Używa fragmentu partycjonowania zoptymalizowane pod kątem list i partycji dynamicznych|Używa fragmentu partycjonowania przez tworzenie dynamiczne liczby partycji.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|Zwraca`true`|Zwraca`true`|Zwraca`true`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|Zwraca`true`|Zwraca`false`|Zwraca`false`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|Zwraca`true`|Zwraca`true`|Zwraca`true`|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Zwraca`false`|Zwraca`true`|Zwraca`true`|  
  
### <a name="dynamic-partitions"></a>Partycje dynamiczne  
 Jeśli planujesz partycjonera do użycia w <xref:System.Threading.Tasks.Parallel.ForEach%2A> metody, musi być może zwrócić dynamiczne liczby partycji. Oznacza to, że obiekt partitioner można podać moduł wyliczający dla nowej partycji na żądanie w czasie wykonywania pętli. Zasadniczo przy każdym pętli dodaje nowe zadanie równoległe, żądań nową partycję do tego zadania. Jeśli potrzebujesz danych należy zamówić, następnie pochodzi od <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> tak, aby każdy element każda partycja jest przypisany unikatowy indeks.  
  
 Aby uzyskać więcej informacji i przykład, zobacz [porady: Implementowanie partycji dynamicznych](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
### <a name="contract-for-partitioners"></a>Kontrakt dla Partycjonery  
 Podczas implementowania niestandardowych partycjonera zgodna z tymi wytycznymi, aby zapewnić poprawne interakcji z PLINQ i <xref:System.Threading.Tasks.Parallel.ForEach%2A> w TPL:  
  
-   Jeśli <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> jest wywołana z nieprawidłowym argumentem zero lub mniej dla `partitionsCount`, throw <xref:System.ArgumentOutOfRangeException>. Chociaż PLINQ i TPL nigdy nie będzie przekazywać w `partitionCount` równa 0, jednak zaleca się ochronić możliwości.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>i <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> zawsze powinna zwrócić `partitionsCount` liczba partycji. Jeśli obiekt partitioner zabraknie danych i nie można utworzyć dowolną liczbę partycji zgodnie z wymaganiami, metoda powinna zwrócić pusty moduł wyliczający dla każdej z pozostałych partycji. W przeciwnym razie zgłosi zarówno PLINQ i TPL <xref:System.InvalidOperationException>.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>, <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, i <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> nigdy nie powinien zwrócić `null` (`Nothing` w języku Visual Basic). Jeśli nie, PLINQ / zgłosi TPL <xref:System.InvalidOperationException>.  
  
-   Metody zwracające partycji zawsze powinna zwrócić partycji, które można w pełni i unikatowo wyliczyć źródła danych. Nie powinno być nie występuje duplikacja w źródle danych lub pominięte elementy, chyba że jednoznacznie wymagane przez projekt obiekt partitioner. Jeśli ta reguła nie jest zakończony, kolejność danych wyjściowych może zaszyfrowane.  
  
-   Następujące pobierające logiczna zawsze dokładnie musi zwracać następujące wartości, tak, aby kolejności dane wyjściowe nie są zaszyfrowane:  
  
    -   `KeysOrderedInEachPartition`: Każda partycja zwraca elementy z rosnącym indeksów klucza.  
  
    -   `KeysOrderedAcrossPartitions`: Dla wszystkich partycji, które są zwracane klucza indeksy w partycji *i* są wyższe niż indeksy klucza partycji *i*-1.  
  
    -   `KeysNormalized`: Wszystkie indeksy klucza monotonicznie coraz bez przerwy, zaczynając od zera.  
  
-   Wszystkie indeksy muszą być unikatowe. Nie mogą być zduplikowane indeksy. Jeśli ta reguła nie jest zakończony, kolejność danych wyjściowych może zaszyfrowane.  
  
-   Wszystkie indeksy musi być nieujemna. Jeśli ta reguła nie jest zakończony, PLINQ/TPL może zgłaszać wyjątków.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)  
 [Instrukcje: implementowanie partycji dynamicznych](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)  
 [Instrukcje: implementowanie partycjonera dla partycjonowania statycznego](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
