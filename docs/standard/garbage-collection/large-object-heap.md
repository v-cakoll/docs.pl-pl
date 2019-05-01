---
title: Stos dużych obiektów w systemach Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9fef3bfb070e5e87dd0f7f78e76af6e6e051967
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63809631"
---
# <a name="the-large-object-heap-on-windows-systems"></a>Stos dużych obiektów w systemach Windows

Moduł zbierający elementy bezużyteczne .NET (GC) dzieli obiektów w małych i dużych obiektów. Gdy obiekt jest duży, niektóre jego atrybuty stają się większe znaczenie niż czy obiekt jest mała. Na przykład kompaktowania — które skopiować go w pamięci w stercie — może być kosztowne. W związku z tym moduł zbierający elementy bezużyteczne .NET powoduje duże obiekty sterty dużych obiektów (LOH). W tym temacie omówimy stertę dużego obiektu szczegółowo. Omówimy, co to jest uprawniony obiektu jako dużego obiektu, jak te dużych obiektów są zbierane i rodzaju skutki dużych obiektów wydajności nakładać.

> [!IMPORTANT]
> W tym temacie omówiono stertę dużego obiektu w .NET Framework i .NET Core uruchomiony tylko w systemach Windows. Nie uwzględniono w niej LOH systemem implementacje platformy .NET na innych platformach.

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a>Jak obiekt kończy się na stosie dużego obiektu i sposób obsługi ich GC

Jeśli obiekt jest większy niż lub równa rozmiarze 85 000 bajtów, jest uznawane za dużego obiektu. To była określana na podstawie dostrajanie wydajności. Gdy żądanie alokacji obiektów jest co najmniej rozmiarze 85 000 bajtów, środowisko uruchomieniowe przydziela na stosie dużego obiektu.

Aby zrozumieć, co to znaczy, warto sprawdzić niektóre podstawy dotyczące odzyskiwania pamięci platformy .NET.

Moduł zbierający elementy bezużyteczne .NET jest pokoleniowego modułu zbierającego. Posiada trzy generacje: generacji 0, generację 1 i generacji 2. Powodem generacje 3 jest to, że, w dobrze dostosowane aplikacji, większość struktury obiektów w gen0. Na przykład w aplikacji serwera, alokacje skojarzonej z każdym żądaniem powinien zdechną po wysłaniu żądania. Żądania alokacji śledząc będzie przekształcić gen1 i zdechną istnieje. Zasadniczo gen1 pełni rolę bufora między obszarów małych obiektów i długotrwałe obiektu.

Małych obiektów zawsze są przydzielane w generacji 0 i, w zależności od ich okres istnienia, może być promowane do generacji 1 lub generation2. Duże obiekty zawsze są przydzielane w generacji 2.

Duże obiekty należą do generacji 2, ponieważ są one pobierane tylko podczas kolekcji generacji 2. Po zebraniu generacji, jego młodszych generation(s) również są zbierane. Na przykład w sytuacji odzyskiwania pamięci generacji 1 są zbierane zarówno generacji 1 i 0. I sytuacji odzyskiwania pamięci generacji 2 całego sterty są zbierane. Z tego powodu GC generacji 2 jest również nazywany *pełne odzyskiwanie pamięci*. Ten artykuł odnosi się do odzyskiwania pamięci generacji 2, zamiast pełną operacją GC, ale warunki są wymienne.

Generacje zapewniają logiczne widok sterty GC. Fizycznie obiekty na żywo w zarządzanym stosie segmentach. A *segmentu w zarządzanej stercie* to fragment pamięci, która GC zastrzega sobie z systemu operacyjnego, wywołując [funkcji VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) imieniu kodu zarządzanego. Gdy środowisko CLR jest załadowany, GC przydziela dwa segmenty początkowej sterty: jeden dla małych obiektów (stos małych obiektów, lub raportu o kondycji) i jeden dla dużych obiektów (sterty obiektów wielkich).

Alokacja żądań następnie są spełnione, umieszczając zarządzane obiekty w tych segmentach sterty zarządzanej. Jeśli obiekt jest mniejszy niż rozmiarze 85 000 bajtów, zostanie ono przełączone na segmencie dla raportu o kondycji; w przeciwnym razie jest umieszczany w segmencie LOH. Segmenty są zatwierdzane (na mniejsze fragmenty) jako więcej i więcej obiektów są przydzielane do nich.
Dla raportu o kondycji obiekty, które przeżyły wykaz Globalny są promowane do następnej generacji. Obiekty, które przeżyły bezużytecznych generacji 0, teraz są traktowane jako obiekty w generacji 1 i tak dalej. Obiekty, które przeżyły najstarsze generowania nadal są uwzględniane w najstarsze generacji. Innymi słowy przy życiu z generacji 2 są obiekty generacji 2; i pozostałości z LOH są obiektami LOH, (które są zbierane za pomocą gen2).

Kod użytkownika może alokować w generacji 0 (małych obiektów) lub LOH (duże obiekty). Tylko GC "przydzielać" obiektów w generacji 1 (przez wspieranie pozostałości z generacji 0) i 2. generacji (przez wspieranie pozostałości z generacji 1 i 2).

Po wyzwoleniu wyrzucania elementów bezużytecznych, GC ślady za pośrednictwem obiektów na żywo i kompaktowanie je. Ale ponieważ kompaktowanie jest kosztowne, GC *wrzucając* LOH; to sprawia, że listę bezpłatnych poza obiekty martwe, których można używać w dalszej części do spełnienia żądania alokacji dużego obiektu. Obiekty martwe sąsiadujących są wprowadzane w jeden obiekt bezpłatne.

.NET core i .NET Framework (począwszy od programu .NET Framework 4.5.1) obejmują <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> właściwość, która umożliwia użytkownikom, aby określić, że LOH powinien można skompaktować podczas następnego pełną operacją GC blokowania. I w przyszłości .NET może podjąć decyzję o compact LOH automatycznie. Oznacza to, jeśli przydzielić dużych obiektów i upewnić się, że nie przenoś powinny nadal przypinanych je.

Rysunek 1 przedstawia scenariusz, w którym GC formularzy generacji 1 po pierwszej generacji 0 GC gdzie `Obj1` i `Obj3` są martwe i formularzy generacji 2 po pierwszej generacji 1 GC gdzie `Obj2` i `Obj5` jest nieużywany. Należy zauważyć, że to i poniższych ilustracjach tylko w celach ilustracyjnych; zawierają one bardzo mało obiekty, aby lepiej zrozumieć, co się dzieje na stosie. W rzeczywistości wiele innych obiektów zazwyczaj wiążą się z wykazem Globalnym.

![Rysunek 1: Gen 0 GC i gen 1 GC](media/loh/loh-figure-1.jpg)\
Rysunek 1: Generacji 0 i odzyskiwania pamięci generacji 1.

Rysunek 2 pokazuje, że po GC generacji 2 której pokazano, że `Obj1` i `Obj2` są serialem telewizyjnym GC formularzy ciągłych ilość wolnego miejsca na Brak pamięci używanej zajmowany przez `Obj1` i `Obj2`, który następnie został użyty do spełnienia żądania alokacji Aby uzyskać `Obj4`. Odstęp po ostatni obiekt `Obj3`do końca segmentu można również spełnić żądania alokacji.

![Rysunek 2: Po gen 2 GC](media/loh/loh-figure-2.jpg)\
Rysunek 2: Po GC generacji 2

Jeśli nie ma wystarczającej ilości wolnego miejsca, aby obsłużyć żądania alokacji dużego obiektu, GC najpierw próbuje pobrać więcej segmentów z systemu operacyjnego. W przypadku niepowodzenia wyzwala wykaz Globalny generacji 2 w nadzieję, że jest zwolnić miejsce.

Podczas generacji 1 lub generacja 2 GC, moduł zbierający elementy bezużyteczne zwalnia, które mają żadne obiekty na żywo na nich do systemu operacyjnego, wywołując [funkcji VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree). Odstęp po ostatni obiekt na żywo na końcu segmentu jest anulowane (z wyjątkiem w segmencie efemerycznym, gdzie gen0/gen1 na żywo, a gdy moduł odśmiecania pamięci przechowuje niektóre zatwierdzone, ponieważ aplikacja będzie przydzielanie w nim natychmiast). I wolnego miejsca do magazynowania pozostaną zatwierdzone, chociaż są one resetowane, co oznacza system operacyjny nie musi zapisywać dane w ich do dysku.

Ponieważ LOH są zbierane podczas operacje odzyskiwania pamięci generacji 2, LOH segment może być zwolniony tylko podczas odzyskiwania pamięci. Rysunek 3 przedstawia scenariusz, w której moduł zbierający elementy bezużyteczne zwalnia jednego segmentu (segment 2) do systemu operacyjnego i anuluje więcej miejsca na pozostałe segmenty. Jeśli musi używać miejsca anulowane na końcu segmentu do spełnienia żądania alokacji dużego obiektu, jej zatwierdzenia pamięć ponownie. (Objaśnienia dotyczące zatwierdzania/anulowania, zobacz dokumentację dla [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).

![Rysunek 3: LOH po gen 2 GC](media/loh/loh-figure-3.jpg)\
Rysunek 3: LOH po GC generacji 2

## <a name="when-is-a-large-object-collected"></a>Gdy dużego obiektu są zbierane?

Ogólnie rzecz biorąc GC występuje, gdy jedna z następujących warunków 3 sytuacji:

- Alokacja przekracza generacji 0 lub próg dużego obiektu.

  Próg jest właściwością generacji. Próg generacji jest ustawiona, gdy moduł odśmiecania pamięci przydziela obiekty do niego. Po przekroczeniu progu wykaz Globalny jest wyzwalana dla tej generacji. Podczas alokowania obiektów małych lub dużych wykorzystasz generacji 0 i progów LOH, odpowiednio. Gdy moduł odśmiecania pamięci przydziela w generacji 1 i 2, wykorzystuje ich progów. Tych progów dynamicznie specjalnie po uruchomieniu programu.

  Jest to typowy przypadek; Większość wykazów globalnych się tak zdarzyć z powodu alokacji na stosie zarządzanym.

- <xref:System.GC.Collect%2A?displayProperty=nameWithType> Metoda jest wywoływana.

  Jeśli bez parametrów <xref:System.GC.Collect?displayProperty=nameWithType> metoda jest wywoływana lub innego przeciążenia metody jest przekazywana <xref:System.GC.MaxGeneration?displayProperty=nameWithType> jako argument, LOH są zbierane wraz z pozostałej części zarządzanego stosu.

- System jest w sytuacji braku pamięci.

  Dzieje się tak, gdy moduł zbierający elementy bezużyteczne otrzyma powiadomienie dużą ilość pamięci z systemu operacyjnego. Jeśli moduł zbierający elementy bezużyteczne sądzą, że podczas odzyskiwania pamięci generacji 2 będą produktywność, wyzwala jeden.

## <a name="loh-performance-implications"></a>Wpływ na wydajność LOH

Alokacje sterty dużych obiektów wpłynąć na wydajność w następujący sposób.

- Alokacja kosztów.

  Środowisko CLR sprawia, że gwarancji, że pamięci dla każdego nowego obiektu, zapewnia jest wyczyszczone. Oznacza to, że koszt alokacji dużego obiektu jest całkowicie zdominowany przez wyczyszczenie (chyba że wyzwala wykaz Globalny) pamięci. Jeśli zajmuje 2 cykle, aby wyczyścić jednobajtowego, zajmuje 170,000 cykle, aby wyczyścić najmniejszy dużego obiektu. Czyszczenie pamięci obiektu 16MB na maszynie 2GHz zajmuje około 16ms. Jest dosyć duża kosztów.

- Kolekcja kosztów.

  Ponieważ LOH i generacji 2 są zbierane ze sobą, po przekroczeniu progu pojedynczo firmy, zostanie wywołany kolekcji generacji 2. Jeśli generacja wyzwolenia kolekcji 2 z powodu LOH generacji 2 nie zawsze będzie znacznie mniejszy po GC. Jeśli w generacji 2 jest dużo danych, ma minimalny wpływ. Ale jeśli generacji 2 jest duży, może to spowodować problemy z wydajnością w przypadku wielu generacji 2 wykazów globalnych są wyzwalane. Jeśli wiele duże obiekty są przydzielane na bardzo tymczasowego i masz duży raportu o kondycji, może być wydatków zbyt dużo czasu, wykonując wykazów globalnych. Ponadto koszt alokacji jest naprawdę coraz więcej jeśli zachowasz przydzielanie i odpuszczenie bardzo dużych obiektów.

- Elementy tablicy w przypadku typów referencyjnych.

  Bardzo duże obiekty na LOH są zazwyczaj tablicami (jest to bardzo rzadko, aby wystąpienie obiektu, który jest bardzo duża). Jeśli elementy tablicy są bogate odniesienia powoduje koszt, który nie jest obecny, jeśli elementy nie są bogate odwołania. Jeśli element nie zawiera żadnych odwołań, moduł odśmiecania pamięci nie musi przechodzić przez tablicy na wszystkich. Na przykład jeśli używasz tablicy do przechowywania węzłów w drzewie binarnym, jednym ze sposobów jego wdrożenia jest do odwoływania się do lewej i prawej węzła węzła przez węzły rzeczywiste:

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  Jeśli `num_nodes` jest duży, moduł zbierający elementy bezużyteczne musi przechodzić przez co najmniej dwa odwołania dla każdego elementu. Alternatywnym podejściem jest do przechowywania indeksu po prawej stronie i węzłów po lewej stronie:

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  Zamiast odwołujące się po lewej stronie węzła danych jako `left.d`, odwołasz się do niego jako `binary_tr[left_index].d`. I moduł odśmiecania pamięci nie ma konieczności Przyjrzyj się wszystkie odwołania dla węzła po lewej i prawej stronie.

Poza trzy czynniki pierwsze dwa są zwykle bardziej znaczące, niż trzeci. W związku z tym zaleca się przydzielanie puli dużych obiektów, które możesz ponownie użyć zamiast przydzielać czasowe.

## <a name="collecting-performance-data-for-the-loh"></a>Zbieranie danych o wydajności dla LOH

Przed można zbierać dane wydajności dotyczące określonego obszaru, użytkownik powinien już zostały wykonane następujące:

1. Znaleziono dowody, że patrzy powinny być tego obszaru.

2. Wyczerpane innych obszarów, które znasz bez znajdowanie niczego objaśniające problem z wydajnością, które zostały użyte.

Zobacz w blogu [zrozumienie problemu, przed podjęciem próby znalezienia rozwiązania](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) więcej informacji na temat podstawowe informacje dotyczące pamięci i procesora CPU.

Aby zbierać dane dotyczące wydajności LOH, można użyć następujących narzędzi:

- [Liczniki wydajności pamięci środowiska .NET CLR](#net-clr-memory-performance-counters)

- [Zdarzenia ETW.](#etw-events)

- [Debuger](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>Liczniki wydajności pamięci CLR platformy .NET

Te liczniki wydajności są zwykle dobry, pierwszym krokiem w badanie problemów z wydajnością (mimo że zaleca się, że używasz [zdarzenia ETW](#etw-events)). Możesz skonfigurować monitorowanie wydajności, dodając liczniki, które chcesz, jak pokazano na rysunku 4. Te, które są istotne dla LOH są:

- **Zbieranie pokolenia 2**

   Przedstawia liczbę przypadków, gdy operacje odzyskiwania pamięci generacji 2 miały miejsce od momentu uruchomienia procesu. Licznik jest zwiększany na końcu kolekcji generacji 2 (nazywany także pełne wyrzucanie elementów bezużytecznych). Ten licznik wskazuje ostatnią odczytaną wartość.

- **Duży rozmiar sterty obiektów**

   Wyświetla bieżący rozmiar w bajtach, włącznie z wolnego miejsca LOH. Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, nie na każdej alokacji.

Typowym sposobem Obejrzyj liczników wydajności to za pomocą Monitora wydajności (perfmon.exe). Użyj "Dodawanie liczników", aby dodać licznik interesujące dla procesów, które Cię interesują. Dane licznika wydajności można zapisać do pliku dziennika, jak pokazano na rysunku 4:

![Screenshow, który pokazuje dodawania liczników wydajności.](media/large-object-heap/add-performance-counter.png)
Rysunek 4: LOH po GC generacji 2

Liczniki wydajności można również można wykonywać zapytania programowo. Wiele osób ich zbierania dzięki temu w ramach rutynowego procesu testowania. Gdy są dodatkowe liczniki wartościami, które są niezwykłe, używają innych oznacza, że aby uzyskać bardziej szczegółowe dane ułatwiające wykonywanie analiz.

> [!NOTE]
> Firma Microsoft zaleca, że przy użyciu zdarzenia ETW zamiast wydajności liczników, ponieważ ETW zapewnia znacznie bogatsze informacje.

### <a name="etw-events"></a>zdarzenia ETW

Moduł zbierający elementy bezużyteczne zawiera bogaty zestaw zdarzeń ETW, które pomagają zrozumieć, co robi sterty i dlaczego. Następujące wpisy na blogu pokazują, jak zbierać i zrozumieć zdarzenia GC za pomocą funkcji ETW:

- [Zdarzenia ETW odzyskiwania pamięci - 1](https://blogs.msdn.microsoft.com/maoni/2014/12/22/gc-etw-events-1/)

- [Zdarzenia ETW odzyskiwania pamięci - 2](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-2/)

- [Zdarzenia ETW odzyskiwania pamięci - 3](https://blogs.msdn.microsoft.com/maoni/2014/12/25/gc-etw-events-3/)

- [Zdarzenia ETW odzyskiwania pamięci - 4](https://blogs.msdn.microsoft.com/maoni/2014/12/30/gc-etw-events-4/)

Aby zidentyfikować nadmierne generacji 2 wykazów globalnych spowodowane przez tymczasowe alokacje LOH, poszukaj w kolumnie Przyczyna wyzwolenia wykazów globalnych. Prosty test, który przydziela tylko tymczasowe dużych obiektów, można zbierać informacje dotyczące zdarzeń ETW za pomocą następujących [narzędzia PerfView](https://www.microsoft.com/download/details.aspx?id=28567) wiersza polecenia:

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

Wynik jest podobny do poniższego:

![Zrzut ekranu pokazujący zdarzenia ETW w PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)
Rysunek 5: Zdarzenia ETW są wyświetlane, za pomocą narzędzia PerfView

Jak widać, wszystkie wykazów globalnych są operacje odzyskiwania pamięci generacji 2, a ich wszystkich wygenerowaniu przez AllocLarge, oznacza to, czy alokowanie dużego obiektu wyzwolenie tej GC. Wiemy, że te przydziały są tymczasowe ponieważ **% LOH przeżywalność** kolumny mówi 1%.

Możesz zbierać dodatkowe zdarzenia ETW, określające, kto jest przydzielony te dużych obiektów. Następujące polecenie w wierszu:

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

zbiera zdarzenia AllocationTick uruchamiane mniej więcej co 100 tysięcy warte alokacji. Innymi słowy zdarzenie jest generowane każdorazowo, gdy jest przydzielany dużego obiektu. Można następnie przyjrzymy się jeden z widoków alokacji sterty GC, pokazujące stosy wywołań, który przydzielony dużych obiektów:

![Zrzut ekranu przedstawiający widok sterty modułu odśmiecania pamięci.](media/large-object-heap/garbage-collector-heap.png)
Rysunek 6: Widok alokacji sterty GC

Jak widać, jest to bardzo prosty test, który po prostu przydziela dużych obiektów z jego `Main` metody.

### <a name="a-debugger"></a>Debuger

Jeśli masz wystarczy zrzutu pamięci i należy przyjrzeć się, jakie obiekty są faktycznie na LOH, możesz użyć [rozszerzenie debugowania SoS](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) dostarczone przez platformy .NET.

> [!NOTE]
> Debugowanie polecenia wymienione w tej sekcji mają zastosowanie do [debugery Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).

Poniżej przedstawiono przykładowe dane wyjściowe analizowanie LOH:

```
0:003> .loadby sos mscorwks
0:003> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013e35ec
sdgeneration 1 starts at 0x013e1b6c
generation 2 starts at 0x013e1000
ephemeral segment allocation context: none
segment   begin allocated     size
0018f2d0 790d5588 790f4b38 0x0001f5b0(128432)
013e0000 013e1000 013e35f8 0x000025f8(9720)
Large object heap starts at 0x023e1000
segment   begin allocated     size
023e0000 023e1000 033db630 0x00ffa630(16754224)
033e0000 033e1000 043cdf98 0x00fecf98(16699288)
043e0000 043e1000 05368b58 0x00f87b58(16284504)
Total Size 0x2f90cc8(49876168)
------------------------------
GC Heap Size 0x2f90cc8(49876168)
0:003> !dumpheap -stat 023e1000 033db630
total 133 objects
Statistics:
MT   Count   TotalSize Class Name
001521d0       66     2081792     Free
7912273c       63     6663696 System.Byte[]
7912254c       4     8008736 System.Object[]
Total 133 objects
```

Rozmiar sterty LOH jest (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bajtów. Między adresami 023e1000 i 033db630 8,008,736 bajtów są zajęte przez tablicę <xref:System.Object?displayProperty=nameWithType> obiektów, 6,663,696 bajtów są zajęte przez tablicę <xref:System.Byte?displayProperty=nameWithType> obiektów i 2,081,792 bajtów, które są zajęte przez ilość wolnego miejsca.

Czasami debuger pokazuje, że całkowity rozmiar LOH jest mniejsza niż rozmiarze 85 000 bajtów. Dzieje się tak, ponieważ środowisko wykonawcze używa LOH przydzielić niektóre obiekty, które są mniejsze niż dużego obiektu.

Ponieważ LOH nie skompaktowany, czasami LOH jest uznawane za źródło fragmentacji. Oznacza, że fragmentacji:

- Fragmentacja zarządzanej sterty, która jest wskazywany przez ilość wolnego miejsca między obiektami zarządzanej. W SoS `!dumpheap –type Free` polecenia wyświetlana jest ilość wolnego miejsca między obiektami zarządzanej.

- Fragmentacja przestrzeni adresów pamięci wirtualnej (VM), czyli pamięć oznaczone jako `MEM_FREE`. Możesz pobrać go przy użyciu różnych poleceń debugera w windbg.

   Poniższy przykład przedstawia fragmentacji przestrzeni maszyny Wirtualnej:

   ```
   0:000> !address
   00000000 : 00000000 - 00010000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   00010000 : 00010000 - 00002000
   Type     00020000 MEM_PRIVATE
   Protect 00000004 PAGE_READWRITE
   State   00001000 MEM_COMMIT
   Usage   RegionUsageEnvironmentBlock
   00012000 : 00012000 - 0000e000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   … [omitted]
   -------------------- Usage SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Pct(Busy)   Usage
   701000 (   7172) : 00.34%   20.69%   : RegionUsageIsVAD
   7de15000 ( 2062420) : 98.35%   00.00%   : RegionUsageFree
   1452000 (   20808) : 00.99%   60.02%   : RegionUsageImage
   300000 (   3072) : 00.15%   08.86%   : RegionUsageStack
   3000 (     12) : 00.00%   00.03%   : RegionUsageTeb
   381000 (   3588) : 00.17%   10.35%   : RegionUsageHeap
   0 (       0) : 00.00%   00.00%   : RegionUsagePageHeap
   1000 (       4) : 00.00%   00.01%   : RegionUsagePeb
   1000 (       4) : 00.00%   00.01%   : RegionUsageProcessParametrs
   2000 (       8) : 00.00%   00.02%   : RegionUsageEnvironmentBlock
   Tot: 7fff0000 (2097088 KB) Busy: 021db000 (34668 KB)

   -------------------- Type SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   7de15000 ( 2062420) : 98.35%   : <free>
   1452000 (   20808) : 00.99%   : MEM_IMAGE
   69f000 (   6780) : 00.32%   : MEM_MAPPED
   6ea000 (   7080) : 00.34%   : MEM_PRIVATE

   -------------------- State SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   1a58000 (   26976) : 01.29%   : MEM_COMMIT
   7de15000 ( 2062420) : 98.35%   : MEM_FREE
   783000 (   7692) : 00.37%   : MEM_RESERVE

   Largest free region: Base 01432000 - Size 707ee000 (1843128 KB)
   ```

Jest to bardziej powszechne, aby zobaczyć fragmentacji maszyny Wirtualnej spowodowane przez tymczasowe dużych obiektów, które wymagają modułu odśmiecania pamięci, można często uzyskać nowe zarządzane segmentów sterty z systemu operacyjnego i zwolnienie pustych z powrotem do systemu operacyjnego.

Aby sprawdzić, czy LOH powoduje fragmentację maszyny Wirtualnej, możesz ustawić punkt przerwania na [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) i [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) aby zobaczyć, kto ich wywoływania. Na przykład aby zobaczyć, kto próbował Alokacja pamięci wirtualnej fragmentów w większe niż 8MBB z systemu operacyjnego, można ustawić punkt przerwania w następujący sposób:

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

To polecenie przechodzi do debugera i przedstawia stos wywołań tylko wtedy, gdy [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) jest wywoływana z rozmiarem alokacji większe niż 8 MB (0x800000).

Środowisko CLR 2.0 dodano funkcję o nazwie *Hoarding maszyny Wirtualnej* , może być przydatne w scenariuszach gdzie segmenty (łącznie z dużymi i małymi obiekt sterty) są często nabyte i wydania. Aby określić Hoarding maszyny Wirtualnej, należy określić flagę uruchamiania o nazwie `STARTUP_HOARD_GC_VM` za pośrednictwem interfejsu API. Zamiast zwalnianie pustych segmentów do systemu operacyjnego, środowisko CLR anuluje pamięci w tych segmentach i umieszcza je na liście wstrzymania. (Zwróć uwagę, że CLR nie robi to segmentów, które są zbyt duże). Środowisko CLR używa później te segmenty do obsługi nowych żądań segmentu. Następnym razem, że Twoja aplikacja wymaga nowego segmentu, środowisko CLR używa z tej listy gotowości Jeśli znajdziesz taki, który jest wystarczająco duży.

Hoarding maszyny Wirtualnej jest również przydatne w przypadku aplikacji, które mają być przechowywane segmentów, którzy już uzyskali, takich jak niektórych aplikacji serwera, które są dominujący aplikacje uruchomione w systemie, aby uniknąć poza wyjątki pamięci.

Zdecydowanie zaleca się starannie przetestować aplikację podczas korzystania z tej funkcji w celu zapewnienia, że Twoja aplikacja ma użycie pamięci stabilny.
