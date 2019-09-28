---
title: Sterta dużego obiektu w systemach Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4663c42b784334f66318c61d531ab4cee2f8b02e
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71354060"
---
# <a name="the-large-object-heap-on-windows-systems"></a>Sterta dużego obiektu w systemach Windows

Moduł wyrzucania elementów bezużytecznych platformy .NET (GC) dzieli obiekty na małe i duże obiekty. Gdy obiekt jest duży, niektóre jego atrybuty stają się bardziej znaczące niż wtedy, gdy obiekt jest mały. Na przykład kompaktowanie go — czyli skopiowanie go w pamięci w innym miejscu na stercie — może być kosztowne. Z tego powodu moduł zbierający elementy bezużyteczne platformy .NET umieszcza duże obiekty na stercie dużego obiektu (LOH). W tym temacie zawarto szczegółowe omówienie sterty dużego obiektu. Będziemy omawiać, co kwalifikuje obiekt jako duży obiekt, jak zbierane są duże obiekty, oraz jakiego rodzaju wydajność nakłada duże obiekty.

> [!IMPORTANT]
> W tym temacie omówiono stertę dużego obiektu w .NET Framework i .NET Core działających tylko w systemach Windows. Nie obejmuje to LOH działających w ramach implementacji platformy .NET na innych platformach.

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a>Jak obiekt zostaje zakończony na stertie dużego obiektu i jak obsługuje je GC

Jeśli obiekt jest większy lub równy 85 000 bajtów, jest traktowany jako duży obiekt. Ta liczba została określona przez dostrajanie wydajności. Gdy żądanie alokacji obiektów jest przez 85 000 lub więcej bajtów, środowisko uruchomieniowe przydziela je na stercie dużego obiektu.

Aby zrozumieć, co to oznacza, warto zapoznać się z podstawą dla programu .NET GC.

Moduł wyrzucania elementów bezużytecznych platformy .NET jest modułem zbierającym. Ma trzy generacje: generacji 0, generacja 1 i generacja 2. Przyczyna 3 generacji polega na tym, że w dobrze dostrojonej aplikacji większość obiektów jest gen0. Na przykład w aplikacji serwera alokacje skojarzone z każdym żądaniem powinny być związane po zakończeniu żądania. Żądania alokacji w locie spowodują przekazanie go do Gen1 i umieszczenie w nim. Zasadniczo Gen1 działa jako bufor między terenami młodych obiektów i długotrwałymi obszarami obiektów.

Małe obiekty są zawsze przydzieleni w generacji 0 i, w zależności od ich okresu istnienia, mogą zostać podwyższone do generacji 1 lub generation2. Duże obiekty są zawsze przydzieleni w generacji 2.

Duże obiekty należą do generacji 2, ponieważ są zbierane tylko podczas kolekcji generacji 2. Po zebraniu generacji zbierane są również wszystkie jego młodsze generacji. Na przykład w przypadku, gdy jest wykonywana generacja 1 GC, zbierane są zarówno generacji 1, jak i 0. Po zakończeniu generacji 2, cała sterta jest zbierana. Z tego powodu generacja 2 GC jest również nazywana *pełną operacją GC*. Ten artykuł odnosi się do generacji 2 GC zamiast pełnego wykazu globalnego, ale warunki są zamienne.

Generacji zapewniają logiczny widok sterty GC. Fizyczne obiekty w zarządzanych segmentach sterty. *Segment sterty zarządzanej* jest fragmentem pamięci, która jest rezerwowana przez system operacyjny z systemu operacyjnego przez wywołanie [funkcji funkcja VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) w imieniu kodu zarządzanego. Po załadowaniu środowiska CLR program GC przydziela dwa początkowe segmenty sterty: jeden dla małych obiektów (sterta małego obiektu lub raport o kondycji) i jeden dla dużych obiektów (sterta dużego obiektu).

Następnie żądania alokacji są spełnione przez umieszczenie obiektów zarządzanych w tych segmentach sterty zarządzanej. Jeśli obiekt jest mniejszy niż 85 000 bajtów, jest umieszczany w segmencie dla raportu o kondycji. w przeciwnym razie jest umieszczany w segmencie LOH. Segmenty są zatwierdzane (w mniejszych fragmentach), gdy do nich są przydzielone więcej i więcej obiektów.
W przypadku raportu o kondycji obiekty, które przeżyły wykaz GC, są podwyższane do nowej generacji. Obiekty, które przeżyły kolekcję generacji 0, są teraz traktowane jak obiekty generacji 1 itd. Jednak obiekty, które przeżyły z najstarszej generacji, są nadal uznawane za najstarszej generacji. Innymi słowy, pozostałe z generacji 2 są obiektami generacji 2; i pozostałe z LOH są obiektami LOH (które są zbierane z Gen2).

Kod użytkownika można przydzielić tylko w generacji 0 (małe obiekty) lub LOH (duże obiekty). Tylko wykaz globalny może "przydzielić" obiekty w generacji 1 (przez podwyższenie poziomu od generacji 0) do generacji 2 (przez podwyższenie poziomu od pokoleń 1 i 2).

Po wyzwoleniu wyrzucania elementów bezużytecznych usługa GC śledzi dane za pomocą obiektów na żywo i kompaktuje je. Ale ponieważ kompaktowanie jest kosztowne, *czyszczenie* wykazuje LOH; powoduje to bezpłatną listę niemartwych obiektów, które mogą być ponownie używane później w celu spełnienia żądań alokacji dużego obiektu. Sąsiadujące obiekty martwe są wprowadzane do jednego bezpłatnego obiektu.

.NET Core i .NET Framework (począwszy od .NET Framework 4.5.1) zawierają <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> Właściwość umożliwiającą użytkownikom określenie, że LOH należy kompaktować podczas następnego pełnego blokowania GC. W przyszłości platforma .NET może zdecydować się na automatyczne kompaktowanie LOH. Oznacza to, że w przypadku przydzielenia dużych obiektów i upewnienia się, że nie są one przenoszone, należy je nadal przypiąć.

Rysunek 1 ilustruje scenariusz, w którym formularze GC generacji 1 po pierwszej generacji 0 GC, gdzie `Obj1` i `Obj3` są martwe, a następnie generacji tworzy 2 po `Obj2` pierwszej `Obj5` generacji 1. Należy zauważyć, że te i poniższe wartości są przeznaczone tylko do celów ilustracyjnych. zawierają one bardzo mało obiektów, aby lepiej zobaczyć, co się dzieje na stercie. W rzeczywistości wiele więcej obiektów jest zwykle używanych w wykazie globalnym.

![Rysunek 1. Generacji 0 GC i gen 1 GC](media/loh/loh-figure-1.jpg)\
Rysunek 1. Generacji 0 i 1. generacji GC.

Rysunek 2 pokazuje, że po 2. generacji GC, który `Obj1` wykaże, że i `Obj2` są martwe, system GC tworzy ciągłe wolne miejsce poza pamięcią `Obj1` `Obj2`, która została użyta w celu zaspokojenia żądania alokacji dla `Obj4`programu. Miejsce po ostatnim obiekcie, `Obj3`do końca segmentu może również służyć do zaspokojenia żądań alokacji.

![Rysunek 2. Po utworzeniu generacji 2 GC](media/loh/loh-figure-2.jpg)\
Rysunek 2. Po generacji 2 GC

Jeśli nie ma wystarczającej ilości wolnego miejsca, aby pomieścić żądania alokacji dużego obiektu, GC najpierw próbuje uzyskać więcej segmentów z systemu operacyjnego. Jeśli to się nie powiedzie, spowoduje to wyzwolenie generacji 2 GC w celu zwolnienia miejsca na dysku.

Podczas generacji 1 lub 2. generacji wyrzucania elementów bezużytecznych zwalnia segmenty, które nie mają żadnych obiektów na żywo z powrotem do systemu operacyjnego przez wywołanie [funkcji VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree). Miejsce po ostatnim aktywnym obiekcie na końcu segmentu zostaje cofnięte (z wyjątkiem segmentów tymczasowych, gdzie gen0/Gen1 na żywo, gdzie moduł zbierający elementy bezużyteczne wykonuje pewne zatwierdzenie, ponieważ aplikacja będzie od razu przydzielana). A wolne miejsca pozostają zatwierdzone, chociaż są one resetowane, co oznacza, że system operacyjny nie musi zapisywać danych z powrotem na dysku.

Ponieważ LOH jest zbierany tylko podczas operacje odzyskiwania pamięci generacji 2, segment LOH można zwolnić tylko podczas tej operacji GC. Rysunek 3 ilustruje scenariusz, w którym Moduł wyrzucania elementów bezużytecznych zwalnia jeden segment (segment 2) z powrotem do systemu operacyjnego i cofa więcej miejsca na pozostałych segmentach. Jeśli konieczne jest użycie nieprzydzielonego miejsca na końcu segmentu w celu zaspokojenia żądań alokacji dużych obiektów, ponownie zostanie zatwierdzona pamięć. (Aby uzyskać wyjaśnienie zatwierdzeń/anulowania zatwierdzenia, zapoznaj się z dokumentacją dotyczącą usługi [Funkcja VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).

![Rysunek 3. LOH po generacji 2 GC](media/loh/loh-figure-3.jpg)\
Rysunek 3. LOH po generacji 2 GC

## <a name="when-is-a-large-object-collected"></a>Kiedy jest zbierany duży obiekt?

Ogólnie rzecz biorąc, wykaz globalny występuje, gdy wystąpi jedno z następujących trzech warunków:

- Alokacja przekracza wartość progową generacji 0 lub dużego obiektu.

  Wartość progowa jest właściwością generacji. Próg dla generacji jest ustawiany, gdy moduł wyrzucania elementów bezużytecznych przydzieli do niego obiekty. Po przekroczeniu progu jest wyzwalana dla tej generacji. W przypadku przydzielania małych lub dużych obiektów należy odpowiednio wykorzystać wartości progowe generacji 0 i LOH. Gdy moduł wyrzucania elementów bezużytecznych alokuje do generacji 1 i 2, wykorzystuje ich progi. Te progi są dynamicznie dostrajane podczas uruchamiania programu.

  Jest to typowy przypadek; Większość operacje odzyskiwania pamięci występuje ze względu na alokacje na stosie zarządzanym.

- <xref:System.GC.Collect%2A?displayProperty=nameWithType> Metoda jest wywoływana.

  Jeśli wywoływana jest <xref:System.GC.Collect?displayProperty=nameWithType> Metoda bez parametrów lub inne Przeciążenie jest przenoszona <xref:System.GC.MaxGeneration?displayProperty=nameWithType> jako argument, LOH jest zbierane wraz z resztą zarządzanej sterty.

- W systemie występuje niewielka ilość pamięci.

  Dzieje się tak, gdy moduł zbierający elementy bezużyteczne otrzymuje powiadomienie o wysokim poziomie pamięci od systemu operacyjnego. Jeśli moduł zbierający elementy bezużyteczne uzna, że wykonanie generacji 2 GC będzie produktywne, wyzwala.

## <a name="loh-performance-implications"></a>Konsekwencje dotyczące wydajności LOH

Alokacje na wydajność sterty dużego obiektu są w następujący sposób.

- Koszt alokacji.

  Środowisko CLR gwarantuje, że pamięć dla każdego nowego obiektu, który wydaje, zostaje wyczyszczona. Oznacza to, że koszt alokacji dużego obiektu jest całkowicie zdominowany przez czyszczenie pamięci (chyba że wyzwala on GC). Jeśli trwa 2 cykle czyszczenia jednego bajtu, trwa 170 000 cykli, aby wyczyścić najmniejszy duży obiekt. Wyczyszczenie pamięci z 16 MB obiektu na maszynie 2GHz trwa około 16ms. To raczej duży koszt.

- Koszt zbierania danych.

  Ponieważ LOH i generacja 2 są zbierane razem, gdy zostanie przekroczony próg jednego z nich, zostanie wyzwolona kolekcja generacji 2. Jeśli kolekcja generacji 2 jest wyzwalana ze względu na LOH, generacja 2 nie będzie konieczna znacznie mniejsza po GC. Jeśli nie ma dużo danych w generacji 2, ma to minimalny wpływ na. Ale jeśli generacja 2 jest duża, może to spowodować problemy z wydajnością w przypadku wyzwolenia wielu operacje odzyskiwania pamięci generacji 2. Jeśli wiele dużych obiektów jest przydzielanych na bardzo tymczasowym czasie i masz duży raport o kondycji, można wyznaczyć zbyt dużo czasu na wykonanie operacje odzyskiwania pamięci. Ponadto koszt alokacji można naprawdę dodać, jeśli będziesz nadal przydzielać i przełączać się do bardzo dużych obiektów.

- Elementy tablicy z typami referencyjnymi.

  Bardzo duże obiekty na LOH są zwykle tablicami (bardzo rzadko jest to obiekt wystąpienia, który jest naprawdę duży). Jeśli elementy tablicy są rozbudowane odwołania, wiąże się to z kosztem nieobecnym, jeśli elementy nie są rozbudowane. Jeśli element nie zawiera żadnych odwołań, Moduł wyrzucania elementów bezużytecznych nie musi przechodzić przez tablicę. Na przykład, jeśli używasz tablicy do przechowywania węzłów w drzewie binarnym, jednym ze sposobów implementacji jest odwołanie do węzła prawego i lewego węzła przez rzeczywiste węzły:

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  Jeśli `num_nodes` jest duży, moduł zbierający elementy bezużyteczne musi przejść przez co najmniej dwa odwołania na element. Alternatywnym podejściem jest przechowywanie indeksu prawego i lewego węzła:

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  Zamiast odwoływać się do danych lewego węzła jako `left.d`, odwołuje się do niego `binary_tr[left_index].d`jako. A Moduł wyrzucania elementów bezużytecznych nie musi odwoływać się do żadnych odwołań dla lewego i prawego węzła.

Od trzech czynników pierwsze dwa są zwykle ważniejsze od trzeciej. W związku z tym zalecamy przydzielenie puli dużych obiektów, których ponowne użycie nie jest możliwe do przydzielenia tymczasowych.

## <a name="collecting-performance-data-for-the-loh"></a>Zbieranie danych wydajności dla LOH

Przed zebraniem danych wydajności dla określonego obszaru należy wykonać następujące czynności:

1. Znaleziono dowody, które należy przejrzeć w tym obszarze.

2. Wyczerpuje się inne obszary, które znasz, bez znalezienia wszystkiego, co może wyjaśnić problem z wydajnością.

Zapoznaj się [z blogiem, aby](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) uzyskać więcej informacji na temat podstawy pamięci i procesora CPU.

Za pomocą poniższych narzędzi można zbierać dane dotyczące wydajności LOH:

- [Liczniki wydajności pamięci CLR platformy .NET](#net-clr-memory-performance-counters)

- [Zdarzenia ETW](#etw-events)

- [Debuger](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>Liczniki wydajności pamięci CLR platformy .NET

Te liczniki wydajności są zwykle dobrym pierwszym krokiem w badaniu problemów z wydajnością (Chociaż zalecamy korzystanie z [zdarzeń ETW](#etw-events)). Monitor wydajności można skonfigurować przez dodanie żądanych liczników, jak pokazano na rysunku 4. Te, które są istotne dla LOH są:

- **Kolekcje generacji 2**

   Przedstawia liczbę przypadków, w których wystąpiło operacje odzyskiwania pamięci generacji 2 od momentu rozpoczęcia procesu. Licznik jest zwiększany na końcu kolekcji generacji 2 (nazywanej również pełnym wyrzucaniem elementów bezużytecznych). Ten licznik wyświetla ostatnią obserwowana wartość.

- **Rozmiar sterty dla dużego obiektu**

   Wyświetla bieżący rozmiar (w bajtach), w tym wolne miejsce LOH. Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, a nie przy każdej alokacji.

Typowym sposobem na przyjrzeć się licznikom wydajności jest Monitor wydajności (Perfmon. exe). Użyj "Dodaj liczniki", aby dodać interesujący licznik dla procesów, które Cię interesują. Dane licznika wydajności można zapisać w pliku dziennika, jak pokazano na rysunku 4:

![Screenshow, który pokazuje Dodawanie liczników wydajności.](media/large-object-heap/add-performance-counter.png)
Rysunek 4. LOH po generacji 2 GC

Liczniki wydajności mogą być również wykonywane programowo. Wiele osób zbiera je w ten sposób w ramach procesu rutynowego testowania. Gdy znajdują się w nich liczniki z wartościami, które są niezwykłe, wykorzystują inne metody, aby uzyskać bardziej szczegółowe dane, które pomagają w badaniu.

> [!NOTE]
> Zalecamy korzystanie z zdarzeń ETW zamiast liczników wydajności, ponieważ funkcja ETW udostępnia znacznie bogatsze informacje.

### <a name="etw-events"></a>zdarzenia ETW

Moduł wyrzucania elementów bezużytecznych udostępnia rozbudowany zestaw zdarzeń ETW, które ułatwiają zrozumienie działania sterty i przyczyn. Następujące wpisy w blogu pokazują, jak zbierać i zrozumieć zdarzenia GC z funkcją ETW:

- [Zdarzenia ETW odzyskiwania pamięci — 1](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [Zdarzenia ETW odzyskiwania pamięci — 2](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [Zdarzenia ETW odzyskiwania pamięci — 3](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [Zdarzenia ETW odzyskiwania pamięci — 4](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

Aby zidentyfikować nadmierną operacje odzyskiwania pamięci generacji 2 spowodowaną przez tymczasowe alokacje LOH, zapoznaj się z kolumną przyczyna wyzwalacza dla operacje odzyskiwania pamięci. Dla prostego testu, który przydziela tylko tymczasowe duże obiekty, można zbierać informacje dotyczące zdarzeń ETW za pomocą następującego wiersza polecenia [Narzędzia PerfView](https://www.microsoft.com/download/details.aspx?id=28567) :

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

Wynik jest podobny do tego:

![Zrzut ekranu przedstawiający zdarzenia ETW w narzędzia PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)
Rysunek 5. Zdarzenia ETW wyświetlane przy użyciu narzędzia PerfView

Jak widać, wszystkie operacje odzyskiwania pamięci są generacji 2 operacje odzyskiwania pamięci i są wyzwalane przez AllocLarge, co oznacza, że przydzielanie dużego obiektu wyzwolił ten wykaz GC. Wiemy, że te przydziały są tymczasowe ze względu na to, że procent **przeżycia LOH%** Column brzmi 1%.

Można zbierać dodatkowe zdarzenia ETW, które informują użytkownika, kto przydzielił te duże obiekty. Następujący wiersz polecenia:

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

zbiera zdarzenie AllocationTick, które jest uruchamiane około każdej 100 000 przydziałów. Innymi słowy, zdarzenie jest wywoływane przy każdym przydzieleniu dużego obiektu. Następnie można przyjrzeć się jednemu z widoków alokacji sterty GC pokazujących stosy wywołań przydzieloną duże obiekty:

![Zrzut ekranu pokazujący widok sterty odzyskiwania pamięci.](media/large-object-heap/garbage-collector-heap.png)
Rysunek 6. Widok alokacji sterty GC

Jak widać, jest to bardzo prosty test, który po prostu przypisuje duże obiekty z jego `Main` metody.

### <a name="a-debugger"></a>Debuger

Jeśli wszystko jest zrzutem pamięci i chcesz sprawdzić, jakie obiekty faktycznie znajdują się w LOH, możesz użyć [rozszerzenia debugera sos](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) dostarczonego przez platformę .NET.

> [!NOTE]
> Polecenia debugowania wymienione w tej sekcji dotyczą [debugerów systemu Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).

Poniżej przedstawiono przykładowe dane wyjściowe analizy LOH:

```console
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

Rozmiar sterty LOH to (16 754 224 + 16 699 288 + 16 284 504) = 49 738 016 bajtów. Między adresami 023e1000 i 033db630, 8 008 736 bajty są zajęte przez tablicę <xref:System.Object?displayProperty=nameWithType> obiektów, 6 663 696 bajty są zajęte przez <xref:System.Byte?displayProperty=nameWithType> tablicę obiektów, a 2 081 792 bajty są zajęte przez wolne miejsce.

Czasami debuger pokazuje, że łączny rozmiar LOH jest mniejszy niż 85 000 bajtów. Dzieje się tak, ponieważ środowisko uruchomieniowe używa LOH do alokowania niektórych obiektów, które są mniejsze niż w przypadku dużego obiektu.

Ponieważ LOH nie jest kompaktowana, czasami LOH jest uważana za źródło fragmentacji. Fragmentacja oznacza:

- Fragmentacja zarządzanego sterty, która jest wskazywana przez ilość wolnego miejsca między obiektami zarządzanymi. W sos `!dumpheap –type Free` polecenie wyświetla ilość wolnego miejsca między obiektami zarządzanymi.

- Fragmentacja przestrzeni adresowej pamięci wirtualnej (VM), czyli pamięci oznaczonej jako `MEM_FREE`. Można to zrobić za pomocą różnych poleceń debugera w programie WinDbg.

   Poniższy przykład przedstawia fragmentację w obszarze maszyny wirtualnej:

   ```console
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

Jest to bardziej powszechne, aby zobaczyć fragmentację maszyny wirtualnej spowodowaną przez tymczasowe duże obiekty, które wymagają modułu wyrzucania elementów bezużytecznych, aby często uzyskać nowe zarządzane segmenty sterty z systemu operacyjnego i zwalniać puste z powrotem do systemu operacyjnego.

Aby sprawdzić, czy LOH powoduje fragmentację maszyny wirtualnej, można ustawić punkt przerwania dla [Funkcja VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) i [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) , aby zobaczyć, kto je wywołuje. Na przykład aby zobaczyć, kto próbował przydzielić fragmenty pamięci wirtualnej większe niż 8MBB z systemu operacyjnego, można ustawić punkt przerwania w następujący sposób:

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

To polecenie dzieli się na debuger i pokazuje stosu wywołań tylko wtedy, gdy [Funkcja VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) jest wywoływana z rozmiarem alokacji większym niż 8 MB (0x800000).

Środowisko CLR 2,0 dodaliśmy funkcję o nazwie *VM Hoarding* , która może być przydatna w scenariuszach, w których segmenty (w tym duże i małe sterty obiektów) są często uzyskiwane i zwalniane. Aby określić Hoarding maszyny wirtualnej, należy określić flagę uruchamiania `STARTUP_HOARD_GC_VM` wywoływaną za pośrednictwem interfejsu API hostingu. Zamiast zwalniać puste segmenty z powrotem do systemu operacyjnego, środowisko CLR zwalnia pamięć w tych segmentach i umieszcza je na liście gotowości. (Należy pamiętać, że środowisko CLR nie wykonuje tego w przypadku segmentów, które są zbyt duże). Środowisko CLR później używa tych segmentów, aby spełnić nowe żądania segmentów. Następnym razem, gdy aplikacja będzie potrzebowała nowego segmentu, środowisko CLR używa jednego z tej listy w stanie wstrzymania, jeśli będzie można je znaleźć wystarczająco duże.

Hoarding maszyny wirtualnej jest również przydatne w przypadku aplikacji, które mają być przechowywane do segmentów, które już uzyskały, takich jak niektóre aplikacje serwerowe, które są aplikacjami dominującymi uruchomionymi w systemie, aby uniknąć wyjątków z pamięci.

Zdecydowanie zalecamy dokładne przetestowanie aplikacji podczas korzystania z tej funkcji, aby upewnić się, że aplikacja ma dość stabilne użycie pamięci.
