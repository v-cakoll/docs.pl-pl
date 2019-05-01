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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73c745fbbdb66777b50478623d969c125f92474b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973423"
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>Niestandardowe partycjonery dla PLINQ i TPL
Równoległe przetwarzanie operacji na źródle danych, jest jedną z czynności niezbędne do *partycji* źródło w wiele sekcji, które mogą być udostępniane jednocześnie z wielu wątków. Program PLINQ i Biblioteka zadań równoległych (TPL) zapewnia domyślne moduły partycjonowania, które działają w sposób niewidoczny dla użytkownika podczas wpisywania zapytanie równoległe lub <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli. Dla bardziej zaawansowanych scenariuszy można dodać własne partycjonera.  
  
## <a name="kinds-of-partitioning"></a>Rodzaje partycjonowania  
 Istnieje wiele sposobów partycjonowania źródła danych. Wiele wątków w najbardziej efektywny sposób podejścia, współpracować, aby proces oryginalnej sekwencji źródłowej, a nie fizycznie oddzielenie źródło w wiele podciągów. Tablice i inne indeksowany źródeł takich jak <xref:System.Collections.IList> kolekcji, której długość jest znana z wyprzedzeniem, *partycjonowania zakresu* to najprostszy rodzaj partycjonowania. Każdy wątek otrzymuje unikatowy rozpoczęcia i zakończenia indeksów, tak, aby przetworzyć jego zakres źródła bez zastępowania lub zastąpieniem przez inne wątków. Tylko kłopotów związanych z partycjonowania zakresu jest początkowa pracy tworzenia zakresów; nie dodatkowe synchronizacji jest wymagany po tym. W związku z tym jego zapewniają dobrą wydajność, tak długo, jak długo obciążenie jest dzielone równomiernie jedna. Partycjonowania zakresu niedogodność polega na tym, że jeśli jeden wątek zakończy się wcześniej, nie będzie pomocna wątków, Zakończ pracę.  
  
 W przypadku połączonej listy lub innych kolekcji, której długość jest nieznany, można użyć *fragmentów jest partycjonowanie*. W przypadku użycia partycjonowania fragmentów każdego wątku lub zadania w pętli równoległej lub zapytanie zużywa pewnej liczby elementów źródła w jednym fragmencie, przetwarza je i następnie wróci do pobierania dodatkowych elementów. Partycjonera gwarantuje, że wszystkie elementy są rozpowszechniane i czy nie ma duplikatów. Fragment może być dowolnego rozmiaru. Na przykład partycjonera, która została przedstawiona w [jak: Implementowanie partycji dynamicznych](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md) tworzy fragmentów, które zawierają tylko jeden element. Tak długo, jak fragmenty nie są zbyt duże, tego rodzaju Partycjonowanie jest natury równoważenia obciążenia ponieważ przypisanie elementów, które mają wątków nie jest wstępnie określić. Jednak partycjonera naliczone obciążenie synchronizacji każdorazowo, wątek musi uzyskać inny fragmentów. Ilość synchronizacji w takich przypadkach jest odwrotnie proporcjonalna do wielkości fragmentów.  
  
 Ogólnie rzecz biorąc partycjonowania zakresu tylko jest szybsze, czas wykonywania delegata jest mała, aby średni i źródło ma dużą liczbę elementów, gdy praca całkowita, każda partycja jest w przybliżeniu. Partycjonowanie fragmentów w związku z tym jest zwykle szybsze w większości przypadków. W źródłach z małą liczbą elementów lub dłuższym czasie wykonywania dla delegata następnie wydajność fragmentów i partycjonowania zakresu dotyczy równości.  
  
 Partycjonery TPL obsługuje również dynamiczne liczby partycji. Oznacza to, na przykład tworzyć partycje na bieżąco, gdy <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli spowoduje utworzenie nowego zadania. Ta funkcja umożliwia partycjonera skalowania wraz z samej pętli. Partycjonery dynamiczne są również natury równoważenia obciążenia. Podczas tworzenia niestandardowego partycjonera, musi obsługiwać dynamiczne partycjonowanie, być może być używany przez <xref:System.Threading.Tasks.Parallel.ForEach%2A> pętli.  
  
### <a name="configuring-load-balancing-partitioners-for-plinq"></a>Konfigurowanie Partycjonery dla PLINQ równoważenia obciążenia  
 Niektóre przeciążenia <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> metody pozwalają tworzyć partycjonera tablicy lub <xref:System.Collections.IList> źródła i określ, czy ma podejmować równoważyć obciążenie między wątków. Gdy partycjonera jest skonfigurowany do równoważenia obciążenia, fragmentów jest Partycjonowanie jest używana, a elementy są przekazywane do każdej partycji w mniejszych fragmentach jako wymagane są. Takie podejście pomaga, upewnij się, że wszystkie partycje elementów do przetworzenia całej pętlą until lub wykonać kwerendy. Dodatkowe przeciążenia może służyć do zapewnia równoważenie obciążenia partycjonowanie dowolnego <xref:System.Collections.IEnumerable> źródła.  
  
 Ogólnie rzecz biorąc równoważenia obciążenia wymaga partycjach tak, aby poprosić elementy stosunkowo często partycjonera. Z kolei partycjonera, który wykonuje partycjonowania statycznego można przypisać elementów do każdego partycjonera wszystkie na raz przy użyciu zakresu lub fragmentów jest partycjonowanie. Wymaga to mniejsze obciążenie niż równoważenia obciążenia, ale może to trwać dłużej do wykonania, jeśli jeden wątek kończy znacznie więcej pracy niż pozostałe. Domyślnie przekazywana IList lub tablica, PLINQ zawsze używa zakresu partycjonowanie bez równoważenia obciążenia. Aby włączyć równoważenie obciążenia dla PLINQ, użyj `Partitioner.Create` metodzie, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
 [!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]  
  
 Najlepszym sposobem ustalenia, czy używać obciążenia równoważenia w dowolnym danym scenariuszu jest eksperymentowanie i zmierzyć czas potrzebny na zakończenie reprezentatywny obciążeń i konfiguracji komputerów operacji. Na przykład partycjonowania statycznego może zapewnić znaczne przyspieszenie na komputerze z wieloma procesorami ma tylko kilka rdzeni, ale może spowodować spowolnienie na komputerach, które mają względnie wiele rdzeni.  
  
 Poniższa tabela zawiera listę dostępnych przeciążeń <xref:System.Collections.Concurrent.Partitioner.Create%2A> metody. Partycjonery te nie są ograniczone do używać tylko wtedy, gdy program PLINQ lub <xref:System.Threading.Tasks.Task>. One można również za pomocą niestandardowych konstrukcji równoległych.  
  
|przeciążenie|Zastosowań Równoważenie obciążenia|  
|--------------|-------------------------|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|zawsze|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Gdy argument logiczny jest określony jako wartość true|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Gdy argument logiczny jest określony jako wartość true|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|nigdy nie|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|nigdy nie|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|nigdy nie|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|nigdy nie|  
  
### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Konfigurowanie zakresu statyczne Partycjonery dla Parallel.ForEach  
 W <xref:System.Threading.Tasks.Parallel.For%2A> pętli, treść pętli jest przekazane do metody jako pełnomocnik. Koszt wywoływania delegata jest prawie taki sam, jak wywołanie wirtualnej metody. W niektórych scenariuszach treść pętli równoległej może być wystarczająco mała, czy koszt wywołanie delegata w każdej iteracji pętli staje się istotne. W takich sytuacjach można użyć dowolnego <xref:System.Collections.Concurrent.Partitioner.Create%2A> przeciążenia, aby utworzyć <xref:System.Collections.Generic.IEnumerable%601> partycji zakresu przez elementy źródłowe. Następnie możesz przekazać ten zbiór zakresów <xref:System.Threading.Tasks.Parallel.ForEach%2A> metody, których treść składa się z regularnych `for` pętli. Zaletą tego podejścia jest to, że delegata wywołania koszt jest naliczany tylko raz na zakres, a nie raz dla każdego elementu. Poniższy przykład przedstawia podstawowy wzorzec.  
  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Każdy wątek w pętli otrzymuje własną <xref:System.Tuple%602> zawierającą początkowy i końcowy indeks wartości w określonym zakresie podrzędnych. Wewnętrzny `for` pętli używa `fromInclusive` i `toExclusive` wartości do pętli tablicy lub <xref:System.Collections.IList> bezpośrednio.  
  
 Jedną z <xref:System.Collections.Concurrent.Partitioner.Create%2A> przeciążenia pozwala określić rozmiar partycji i liczby partycji. Tego przeciążenia można używana w scenariuszach, gdzie jest więc niskie, że nawet jednego wirtualnego wywołania metody na element ma zauważalnego wpływu na wydajność pracy dla każdego elementu.  
  
## <a name="custom-partitioners"></a>Niestandardowe Partycjonery  
 W niektórych scenariuszach może być zwiększonej lub nawet wymagane do wdrożenia własnego partycjonera. Na przykład Niewykluczone, że klasę kolekcji niestandardowej, które można podzielić efektywniej niż domyślne partycjonery może oparte na swojej wiedzy na temat wewnętrznej struktury klasy. Możesz też utworzyć zakres partycji o różnych rozmiarach, w oparciu o swojej wiedzy na temat jak długo potrwa do elementów proces w różnych lokalizacjach w kolekcji źródłowej.  
  
 Aby utworzyć podstawowy niestandardowego partycjonera, należy wyprowadzić klasę z <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> i zastępują metody wirtualne zgodnie z opisem w poniższej tabeli.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Ta metoda jest wywoływana jeden raz w głównym wątku i zwraca IList(IEnumerator(TSource)). Każdy wątek procesu roboczego w pętli lub zapytanie może wywołać `GetEnumerator` na liście, aby pobrać <xref:System.Collections.Generic.IEnumerator%601> za pośrednictwem oddzielnej partycji.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Zwróć `true` w przypadku zaimplementowania <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, w przeciwnym razie `false`.|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|Jeśli <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> jest `true`, opcjonalnie można wywołać tej metody zamiast <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Jeśli wyniki muszą być sortowanie lub wymagają indeksowanych dostępu do elementów, następnie dziedziczyć <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> i zastąp jego metod wirtualnych, zgodnie z opisem w poniższej tabeli.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Ta metoda jest wywoływana jeden raz w głównym wątku i zwraca `IList(IEnumerator(TSource))`. Każdy wątek procesu roboczego w pętli lub zapytanie może wywołać `GetEnumerator` na liście, aby pobrać <xref:System.Collections.Generic.IEnumerator%601> za pośrednictwem oddzielnej partycji.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Zwróć `true` w przypadku zaimplementowania <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>; w przeciwnym razie wartość false.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|Zwykle to po prostu wywołuje funkcję <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|Jeśli <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> jest `true`, opcjonalnie można wywołać tej metody zamiast <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Poniższa tabela zawiera szczegółowe informacje o tym, jak trzy rodzaje implementują Równoważenie obciążenia partycjonery <xref:System.Collections.Concurrent.OrderablePartitioner%601> klasy.  
  
|Metoda/właściwość|IList / tablicy bez równoważenia obciążenia|IList / tablicy z modułem równoważenia obciążenia|Interfejs IEnumerable|  
|----------------------|-------------------------------------------|----------------------------------------|-----------------|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Korzysta z partycjonowania zakresu|Zastosowań fragmentów partycjonowanie zoptymalizowane pod kątem list dla liczba partycji określony|Zastosowań fragmentów partycjonowania, tworząc statycznej liczby partycji.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|Nieobsługiwane zgłasza wyjątek|Zastosowań fragmentów partycjonowania zoptymalizowane pod kątem list i partycji dynamicznych|Zastosowań fragmentów partycjonowania, tworząc dynamiczne liczby partycji.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|Zwraca `true`|Zwraca `true`|Zwraca `true`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|Zwraca `true`|Zwraca `false`|Zwraca `false`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|Zwraca `true`|Zwraca `true`|Zwraca `true`|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Zwraca `false`|Zwraca `true`|Zwraca `true`|  
  
### <a name="dynamic-partitions"></a>Partycji dynamicznych  
 Jeśli zamierzasz partycjonera, który ma być używany w <xref:System.Threading.Tasks.Parallel.ForEach%2A> metody musi być może zwrócić dynamiczne liczby partycji. Oznacza to, partycjonera można podać moduł wyliczający dla nowej partycji na żądanie w dowolnym momencie podczas wykonywania pętli. Po prostu zawsze wtedy, gdy pętli dodaje nowe zadanie równoległe, żąda ona nową partycję dla tego zadania. Jeśli potrzebujesz danych prędkości, następnie dziedziczyć <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> tak, aby każdy element w poszczególnych partycjach jest przypisany unikatowy indeks.  
  
 Aby uzyskać więcej informacji i przykład zobacz [jak: Implementowanie partycji dynamicznych](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
### <a name="contract-for-partitioners"></a>Kontrakt dla Partycjonery  
 Podczas implementowania niestandardowego partycjonera, należy przestrzegać następujących wytycznych, aby zapewnić poprawne interakcji z PLINQ i <xref:System.Threading.Tasks.Parallel.ForEach%2A> w TPL:  
  
- Jeśli <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> jest wywołana z nieprawidłowym argumentem zero lub szybciej w przypadku `partitionsCount`, throw <xref:System.ArgumentOutOfRangeException>. Mimo że PLINQ i TPL nigdy nie przejdzie w `partitionCount` równa 0, jednak zaleca się ochronić możliwości.  
  
- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> i <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> zawsze powinna zwrócić `partitionsCount` liczę partycji. Jeśli partycjonera zabraknie danych i nie można utworzyć dowolną liczbę partycji, zgodnie z żądaniem, metoda powinna zwrócić puste wyliczenie dla każdej z pozostałych partycji. W przeciwnym razie zgłosi PLINQ i TPL <xref:System.InvalidOperationException>.  
  
- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>, <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, i <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> nigdy nie powinna zwracać `null` (`Nothing` w języku Visual Basic). Jeśli tak, program PLINQ / zgłosi TPL <xref:System.InvalidOperationException>.  
  
- Metody, które zwracają partycji zawsze powinien zwrócić partycje, które można w pełni i jednoznacznie wyliczania źródła danych. Powinna istnieć nie ma duplikatów w źródle danych lub pominięte elementy, chyba że jednoznacznie wymagane przez projekt partycjonera. Jeśli ta reguła nie zostanie zastosowane, kolejność danych wyjściowych może być zaszyfrowane.  
  
- Następujące pobierające logiczna zawsze dokładnie musi zwracać następujące wartości, tak, aby kolejność danych wyjściowych nie jest on używany jako:  
  
    - `KeysOrderedInEachPartition`: Każda partycja zwraca elementy z rosnącym kluczowych wskaźników.  
  
    - `KeysOrderedAcrossPartitions`: Dla wszystkich partycji, które są zwracane kluczy indeksów w partycji *i* są większe niż indeksy klucza partycji *i*-1.  
  
    - `KeysNormalized`: Wszystkie indeksy klucza monotonicznie coraz więcej bez przerwy, począwszy od zera.  
  
- Wszystkie indeksy muszą być unikatowe. Nie mogą być zduplikowane indeksy. Jeśli ta reguła nie zostanie zastosowane, kolejność danych wyjściowych może być zaszyfrowane.  
  
- Wszystkie indeksy muszą być nieujemne. Jeśli ta reguła nie zostanie zastosowane, PLINQ/TPL może zgłaszać wyjątki.  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Instrukcje: Implementowanie partycji dynamicznych](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)
- [Instrukcje: Implementowanie Partycjonera dla partycjonowania statycznego](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
