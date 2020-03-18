---
title: Niestandardowe partycjonery dla PLINQ i TPL
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, partitioners
ms.assetid: 96153688-9a01-47c4-8430-909cee9a2887
ms.openlocfilehash: 8caea6d8a97b8c0daf7c59718479ea2e12a52d78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141566"
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>Niestandardowe partycjonery dla PLINQ i TPL

Aby zrównoleglić operację w źródle danych, jednym z podstawowych kroków jest *partycjonowanie* źródła na wiele sekcji, do których można uzyskać dostęp jednocześnie przez wiele wątków. PLINQ i równoległej biblioteki zadań (TPL) zapewniają domyślne partycjonery, które działają w sposób niewidoczny podczas pisania kwerendy równoległej lub <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli. W przypadku bardziej zaawansowanych scenariuszy można podłączyć własny partycjoner.

## <a name="kinds-of-partitioning"></a>Rodzaje partycjonowania

Istnieje wiele sposobów partycjonowania źródła danych. W najbardziej efektywnych podejść wiele wątków współpracować do przetwarzania oryginalnej sekwencji źródłowej, a nie fizycznie oddzielanie źródła do wielu podsekwencji. Dla tablic i innych źródeł <xref:System.Collections.IList> indeksowanych, takich jak kolekcje, gdzie długość jest znana z góry, *partycjonowanie zakresu* jest najprostszym rodzajem partycjonowania. Każdy wątek odbiera unikatowe indeksy początkowe i końcowe, dzięki czemu może przetwarzać jego zakres źródła bez zastępowania lub zastępowania przez inny wątek. Jedynym obciążeniem związanym z partycjonowaniem zakresu jest początkowa praca tworzenia zakresów; po tym czasie nie jest wymagana dodatkowa synchronizacja. W związku z tym może zapewnić dobrą wydajność, tak długo, jak obciążenie jest dzielone równomiernie. Wadą partycjonowania zakresu jest to, że jeśli jeden wątek kończy się wcześnie, nie może pomóc innym wątkom zakończyć ich pracę.

Dla połączonych list lub innych kolekcji, których długość nie jest znana, można użyć *partycjonowania fragmentów*. W partycjonowanie fragmentu każdy wątek lub zadanie w pętli równoległej lub kwerendy zużywa pewną liczbę elementów źródłowych w jednym fragmencie, przetwarza je, a następnie wraca do pobierania dodatkowych elementów. Partycjonowanie zapewnia, że wszystkie elementy są dystrybuowane i że nie ma żadnych duplikatów. Fragment może mieć dowolny rozmiar. Na przykład partycjonowanie, który jest pokazany w [Jak: Implementować partycje dynamiczne](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md) tworzy fragmenty, które zawierają tylko jeden element. Tak długo, jak fragmenty nie są zbyt duże, tego rodzaju partycjonowania jest z natury równoważenia obciążenia, ponieważ przypisanie elementów do wątków nie jest wstępnie określone. Jednak partycjonowanie ponosi obciążenie synchronizacji za każdym razem, gdy wątek musi uzyskać inny fragment. Ilość synchronizacji poniesionej w tych przypadkach jest odwrotnie proporcjonalna do rozmiaru fragmentów.

Ogólnie rzecz biorąc partycjonowanie zakresu jest tylko szybsze, gdy czas wykonywania delegata jest mały do umiarkowanego, a źródło ma dużą liczbę elementów, a całkowita praca każdej partycji jest mniej więcej równoważna. Partycjonowanie fragmentów jest zatem zazwyczaj szybsze w większości przypadków. W źródłach z niewielką liczbą elementów lub dłuższyczas wykonywania dla delegata, a następnie wydajność fragmentu i zakresu partycjonowania jest o równej.

Partycjonery TPL obsługują również dynamiczną liczbę partycji. Oznacza to, że mogą tworzyć partycje w locie, <xref:System.Threading.Tasks.Parallel.ForEach%2A> na przykład, gdy pętla pojawia się nowe zadanie. Ta funkcja umożliwia partycjonowanie skalować wraz z samej pętli. Dynamiczne partycjonery są również z natury równoważenia obciążenia. Podczas tworzenia partycjonowania niestandardowego, należy obsługiwać partycjonowanie dynamiczne, aby można było zużywać z <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli.

### <a name="configuring-load-balancing-partitioners-for-plinq"></a>Konfigurowanie partycjonerów równoważenia obciążenia dla plinq

Niektóre przeciążenia <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metody umożliwiają utworzenie partycjonera <xref:System.Collections.IList> dla tablicy lub źródła i określić, czy należy próbować zrównoważyć obciążenie między wątkami. Gdy partycjonowanie jest skonfigurowany do równoważenia obciążenia, partycjonowanie fragment jest używany, a elementy są przekazywane do każdej partycji w małych fragmentów, ponieważ są one wymagane. Takie podejście pomaga upewnić się, że wszystkie partycje mają elementy do przetworzenia, dopóki nie zostanie ukończona cała pętla lub kwerenda. Dodatkowe przeciążenie może służyć do zapewnienia równoważenia <xref:System.Collections.IEnumerable> obciążenia partycjonowania dowolnego źródła.

Ogólnie rzecz biorąc równoważenia obciążenia wymaga partycji do żądania elementów stosunkowo często z partycjonowania. Natomiast partycjonowanie, który wykonuje partycjonowanie statyczne można przypisać elementy do każdego partycjonowania wszystkie naraz przy użyciu zakresu lub fragment partycjonowania. Wymaga to mniej obciążenia niż równoważenie obciążenia, ale może to potrwać dłużej, jeśli jeden wątek kończy się znacznie więcej pracy niż inne. Domyślnie po przekazaniu ilist lub tablicy, PLINQ zawsze używa partycjonowania zakresu bez równoważenia obciążenia. Aby włączyć równoważenie obciążenia dla funkcji `Partitioner.Create` PLINQ, należy użyć metody, jak pokazano w poniższym przykładzie.

[!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
[!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]

Najlepszym sposobem określenia, czy używać równoważenia obciążenia w danym scenariuszu jest eksperymentowanie i mierzenie czasu, jaki trwa operacja w ramach reprezentatywnych obciążeń i konfiguracji komputera. Na przykład partycjonowanie statyczne może zapewnić znaczne przyspieszenie na komputerze wielordzeniowym, który ma tylko kilka rdzeni, ale może spowodować spowolnienie na komputerach, które mają stosunkowo wiele rdzeni.

W poniższej tabeli wymieniono <xref:System.Collections.Concurrent.Partitioner.Create%2A> dostępne przeciążenia metody. Te partycjonery nie są ograniczone do <xref:System.Threading.Tasks.Task>użytku tylko z PLINQ lub . Mogą być również używane z dowolną konstrukcją równoległą niestandardową.

|Przeciążenie|Używa równoważenia obciążenia|
|--------------|-------------------------|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Zawsze|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Gdy argument Logiczny jest określony jako true|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Gdy argument Logiczny jest określony jako true|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|Nigdy|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|Nigdy|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|Nigdy|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|Nigdy|

### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Konfigurowanie partycjonerów zakresu statycznego dla Parallel.ForEach

W <xref:System.Threading.Tasks.Parallel.For%2A> pętli treść pętli jest dostarczana do metody jako delegat. Koszt wywołania tego delegata jest mniej więcej taki sam jak wywołanie metody wirtualnej. W niektórych scenariuszach treść pętli równoległej może być na tyle mała, że koszt wywołania delegata w każdej iteracji pętli staje się znaczący. W takich sytuacjach można użyć <xref:System.Collections.Concurrent.Partitioner.Create%2A> jednego z przeciążeń, aby utworzyć <xref:System.Collections.Generic.IEnumerable%601> partycje zakresu nad elementami źródłowymi. Następnie można przekazać tę kolekcję <xref:System.Threading.Tasks.Parallel.ForEach%2A> zakresów do metody, `for` której treść składa się z regularnej pętli. Zaletą tego podejścia jest to, że koszt wywołania delegata jest ponoszony tylko raz na zakres, a nie raz na element. W poniższym przykładzie przedstawiono podstawowy wzorzec.

[!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
[!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]

Każdy wątek w pętli <xref:System.Tuple%602> odbiera własne, który zawiera początkowe i końcowe wartości indeksu w określonym podzakresie. Pętla `for` wewnętrzna `fromInclusive` `toExclusive` używa i wartości do <xref:System.Collections.IList> pętli przez tablicy lub bezpośrednio.

Jedno z <xref:System.Collections.Concurrent.Partitioner.Create%2A> przeciążeń pozwala określić rozmiar partycji i liczbę partycji. To przeciążenie może służyć w scenariuszach, w których praca na element jest tak niska, że nawet jedno wywołanie metody wirtualnej na element ma zauważalny wpływ na wydajność.

## <a name="custom-partitioners"></a>Niestandardowe partycjonery

W niektórych scenariuszach może być warto lub nawet wymagane do zaimplementowania własnego partycjonowania. Na przykład może mieć niestandardowe klasy kolekcji, które można podzielić bardziej efektywnie niż domyślne partycjonowania może, na podstawie wiedzy o wewnętrznej struktury klasy. Lub można utworzyć partycje zakres o różnych rozmiarach na podstawie wiedzy o tym, jak długo potrwa do przetwarzania elementów w różnych lokalizacjach w kolekcji źródłowej.

Aby utworzyć podstawowy niestandardowy partycjonator, należy wyprowadzić klasę z <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> i zastąpić metody wirtualne, zgodnie z opisem w poniższej tabeli.

|||
|-|-|
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Ta metoda jest wywoływana raz przez wątek główny i zwraca IList(IEnumerator(TSource)). Każdy wątek roboczy w pętli `GetEnumerator` lub kwerendy <xref:System.Collections.Generic.IEnumerator%601> można wywołać na liście, aby pobrać ponad partycji odrębne.|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Powrót, `true` jeśli <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>zaimplementujesz , w przeciwnym razie, `false`.|
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|Jeśli <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> `true`jest , ta metoda może <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>być opcjonalnie wywołana zamiast .|

Jeśli wyniki muszą być sortowalne lub wymagają dostępu indeksowane <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> do elementów, a następnie pochodzą od i zastąpić jego metody wirtualne, jak opisano w poniższej tabeli.

|||
|-|-|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Ta metoda jest wywoływana raz przez `IList(IEnumerator(TSource))`wątek główny i zwraca . Każdy wątek roboczy w pętli `GetEnumerator` lub kwerendy <xref:System.Collections.Generic.IEnumerator%601> można wywołać na liście, aby pobrać ponad partycji odrębne.|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Powrót, `true` jeśli <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>zaimplementujesz ; w przeciwnym razie, false.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|Zazwyczaj to tylko <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>wywołuje .|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|Jeśli <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> `true`jest , ta metoda może <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>być opcjonalnie wywołana zamiast .|

W poniższej tabeli przedstawiono dodatkowe szczegóły dotyczące sposobu implementowania <xref:System.Collections.Concurrent.OrderablePartitioner%601> klasy trzech rodzajów partycjonerów równoważenia obciążenia.

|Metoda/właściwość|IList / Tablica bez równoważenia obciążenia|IList / Tablica z równoważeniem obciążenia|Ienumerable|
|----------------------|-------------------------------------------|----------------------------------------|-----------------|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Używa partycjonowania zakresu|Używa partycjonowania fragmentów zoptymalizowanych pod kątem list dla określonej liczby partycji|Używa partycjonowania fragmentu, tworząc statyczną liczbę partycji.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|Zgłasza wyjątek nieobsługiwany|Używa partycjonowania fragmentów zoptymalizowanych pod kątem list i partycji dynamicznych|Używa partycjonowania fragmentów, tworząc dynamiczną liczbę partycji.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|Zwraca`true`|Zwraca`true`|Zwraca`true`|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|Zwraca`true`|Zwraca`false`|Zwraca`false`|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|Zwraca`true`|Zwraca`true`|Zwraca`true`|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Zwraca`false`|Zwraca`true`|Zwraca`true`|

### <a name="dynamic-partitions"></a>Partycje dynamiczne

Jeśli zamierzasz partycjonowania, które <xref:System.Threading.Tasks.Parallel.ForEach%2A> mają być używane w metodzie, musi być w stanie zwrócić dynamiczną liczbę partycji. Oznacza to, że partycjonowanie może dostarczyć wyliczacz dla nowej partycji na żądanie w dowolnym momencie podczas wykonywania pętli. Zasadniczo za każdym razem, gdy pętla dodaje nowe zadanie równoległe, żąda nowej partycji dla tego zadania. Jeśli wymagane dane mają być uporządkowane, a <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> następnie pochodzą z tak, że każdy element w każdej partycji jest przypisany unikatowy indeks.

Aby uzyskać więcej informacji i przykład, zobacz [Jak: Implementowanie partycji dynamicznych](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).

### <a name="contract-for-partitioners"></a>Kontrakt dla partycjonerów

Podczas implementacji niestandardowego partycjonera postępuj zgodnie z poniższymi <xref:System.Threading.Tasks.Parallel.ForEach%2A> wskazówkami, aby zapewnić prawidłową interakcję z PLINQ i w tpl:

- Jeśli <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> jest wywoływana z argumentem `partitionsCount`zero <xref:System.ArgumentOutOfRangeException>lub mniej dla , throw . Chociaż PLINQ i TPL nigdy `partitionCount` nie przejdą w równej 0, zalecamy jednak ochronę przed możliwością.

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>i <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> zawsze `partitionsCount` zwracaliczbę partycji. Jeśli partycjonowanie zabraknie danych i nie można utworzyć tyle partycji, zgodnie z żądaniem, a następnie metoda powinna zwrócić puste wyliczacza dla każdej z pozostałych partycji. W przeciwnym razie zarówno PLINQ, <xref:System.InvalidOperationException>jak i TPL wyrzucą .

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> , i `null` `Nothing` nigdy nie powinien zwracać (w języku Visual Basic). Jeśli to zrobią, PLINQ/TPL wyrzuci . <xref:System.InvalidOperationException>

- Metody, które zwracają partycje zawsze należy zwrócić partycje, które można w pełni i jednoznacznie wyliczyć źródło danych. Nie powinno być żadnych powielania w źródle danych lub pominięte elementy, chyba że jest to wyraźnie wymagane przez projekt partycjonowania. Jeśli ta reguła nie jest przestrzegana, kolejność wyjścia może być kodowane.

- Następujące programy święcenia muszą zawsze dokładnie zwracać następujące wartości, aby kolejność danych wyjściowych nie była kodowane:

  - `KeysOrderedInEachPartition`: Każda partycja zwraca elementy z rosnącymi indeksami kluczy.

  - `KeysOrderedAcrossPartitions`: Dla wszystkich partycji, które są zwracane, kluczowe indeksy w partycji *i* są wyższe niż kluczowe indeksy w partycji *i*-1.

  - `KeysNormalized`: Wszystkie kluczowe indeksy rosną monotonicznie bez luk, zaczynając od zera.

- Wszystkie indeksy muszą być unikatowe. Nie mogą być zduplikowane indeksy. Jeśli ta reguła nie jest przestrzegana, kolejność wyjścia może być kodowane.

- Wszystkie indeksy muszą być nieujemna. Jeśli ta reguła nie jest przestrzegana, plinq/TPL może zgłaszać wyjątki.

## <a name="see-also"></a>Zobacz też

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Porady: implementowanie partycji dynamicznych](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)
- [Porady: implementowanie partycjonera dla partycjonowania statycznego](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
