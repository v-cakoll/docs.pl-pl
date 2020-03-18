---
title: LOH w systemie Windows - .NET
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: 5125b76dd26ffa4fb363ecf8449f65b490f57b93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74283620"
---
# <a name="the-large-object-heap-on-windows-systems"></a>Stos dużych obiektów w systemach Windows

Moduł zbierający elementy bezużyteczne .NET (GC) dzieli obiekty na małe i duże obiekty. Gdy obiekt jest duży, niektóre z jego atrybutów stają się bardziej znaczące niż jeśli obiekt jest mały. Na przykład zagęszczanie go - czyli kopiowanie go w pamięci w innym miejscu na stercie - może być kosztowne. Z tego powodu moduł odśmiecania pamięci .NET umieszcza duże obiekty na stercie dużych obiektów (LOH). W tym temacie przyjrzymy się głębiej sterty dużego obiektu. Omówimy, co kwalifikuje obiekt jako duży obiekt, jak te duże obiekty są zbierane i jakie implikacje wydajności dużych obiektów nałożyć.

> [!IMPORTANT]
> W tym temacie omówiono stertę dużych obiektów w programie .NET Framework i platformie .NET Core działającej tylko w systemach Windows. Nie obejmuje LOH uruchomiony na implementacje .NET na innych platformach.

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a>Jak obiekt kończy się na stercie dużego obiektu i jak GC obsługuje je

Jeśli obiekt jest większy lub równy rozmiarowi 85 000 bajtów, jest uważany za duży obiekt. Liczba ta została określona przez dostrajanie wydajności. Gdy żądanie alokacji obiektu jest dla 85 000 lub więcej bajtów, czas wykonywania przydziela go na stercie dużego obiektu.

Aby zrozumieć, co to oznacza, warto zbadać niektóre podstawy dotyczące .NET GC.

Moduł zbierający elementy bezużyteczne .NET jest modułem zbierającym pokoleń. Ma trzy pokolenia: pokolenie 0, pokolenie 1 i pokolenie 2. Powodem posiadania 3 pokoleń jest to, że w dobrze dostrojonej aplikacji większość obiektów ginie w gen0. Na przykład w aplikacji serwera alokacje skojarzone z każdym żądaniem powinny zostać umarznięte po zakończeniu żądania. Wnioski o przydział w locie trafią do gen1 i tam umrą. Zasadniczo gen1 działa jako bufor między młodymi obszarami obiektów a długowiecznymi obszarami obiektów.

Małe obiekty są zawsze przydzielane w generacji 0 i, w zależności od ich okresu istnienia, mogą być promowane do generacji 1 lub generacji2. Duże obiekty są zawsze przydzielane w generacji 2.

Duże obiekty należą do generacji 2, ponieważ są zbierane tylko podczas kolekcji generacji 2. Po zebraniu pokolenia zbierane są również wszystkie jego młodsze pokolenia. Na przykład, gdy generacji 1 GC się dzieje, zarówno generacji 1 i 0 są zbierane. A kiedy generacji 2 GC się dzieje, cała sterta jest zbierana. Z tego powodu, generacji 2 GC jest również nazywany *pełny GC*. Ten artykuł odnosi się do generacji 2 GC zamiast pełnego GC, ale terminy są wymienne.

Generacje zapewniają logiczny widok sterty GC. Fizycznie obiekty żyją w zarządzanych segmentach sterty. *Zarządzany segment sterty* to fragment pamięci, który GC rezerwuje z systemu operacyjnego, wywołując [funkcję VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) w imieniu kodu zarządzanego. Po załadowaniu clr GC przydziela dwa początkowe segmenty sterty: jeden dla małych obiektów (sterty małych obiektów lub SOH) i jeden dla dużych obiektów (sterty dużych obiektów).

Żądania alokacji są następnie spełnione przez umieszczenie zarządzanych obiektów w tych zarządzanych segmentach sterty. Jeśli obiekt jest mniejszy niż 85 000 bajtów, jest umieszczany w segmencie dla SOH; w przeciwnym razie jest umieszczany w segmencie LOH. Segmenty są zatwierdzane (w mniejszych fragmentach), ponieważ coraz więcej obiektów jest przydzielanych do nich.
Dla SOH obiekty, które przetrwają GC są promowane do następnej generacji. Obiekty, które przetrwają generacji 0 kolekcji są teraz uważane za generacji 1 obiektów i tak dalej. Jednak obiekty, które przetrwały najstarsze pokolenie, są nadal uważane za w najstarszym pokoleniu. Innymi słowy, osoby, które przeżyły z 2 generacji, są obiektami 2 generacji; i ocalałych z LOH są obiekty LOH (które są zbierane z gen2).

Kod użytkownika można przydzielić tylko w generacji 0 (małe obiekty) lub LOH (duże obiekty). Tylko GC może "przydzielić" obiekty w pokoleniu 1 (poprzez promowanie ocalałych z pokolenia 0) i generacji 2 (poprzez promowanie ocalałych z pokoleń 1 i 2).

Po wyzwoleniu wyrzucania elementów bezużytecznych GC śledzi obiekty na żywo i kompakty je. Ale ponieważ zagęszczanie jest drogie, GC *zamiata* LOH; tworzy bezpłatną listę martwych obiektów, które mogą być ponownie używane później, aby spełnić żądania alokacji dużych obiektów. Sąsiednie martwe obiekty są wykonane w jeden wolny obiekt.

.NET Core i .NET Framework (począwszy od .NET <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> Framework 4.5.1) zawierają właściwość, która pozwala użytkownikom określić, że LOH powinny być kompaktowane podczas następnego pełnego blokowania GC. A w przyszłości .NET może zdecydować się na automatyczne kompaktowanie LOH. Oznacza to, że jeśli przydzielisz duże obiekty i chcesz upewnić się, że nie poruszają się, nadal należy je przypiąć.

Rysunek 1 przedstawia scenariusz, w którym GC tworzy generacji `Obj1` 1 `Obj3` po pierwszej generacji 0 GC gdzie i `Obj2` `Obj5` są martwe, i tworzy generacji 2 po pierwszej generacji 1 GC, gdzie i są martwe. Należy pamiętać, że to i poniższe rysunki są tylko w celach ilustracyjnych; zawierają bardzo niewiele obiektów, aby lepiej pokazać, co dzieje się na stercie. W rzeczywistości wiele więcej obiektów są zazwyczaj zaangażowane w GC.

![Rysunek 1: Gen 0 GC i gc gen 1](media/loh/loh-figure-1.jpg)\
Rysunek 1: Generacja 0 i gc generacji 1.

Rysunek 2 pokazuje, że po generacji `Obj1` `Obj2` 2 GC, który widział, że i są martwe, GC tworzy `Obj1` `Obj2`ciągłe wolne miejsce z pamięci, `Obj4`które były zajęte przez i , który następnie został użyty do zaspokojenia żądania alokacji dla . Spacja po ostatnim `Obj3`obiekcie, do końca segmentu może być również używana do spełnienia żądań alokacji.

![Rysunek 2: Po gc gen 2](media/loh/loh-figure-2.jpg)\
Rysunek 2: Po 2 generacji GC

Jeśli nie ma wystarczającej ilości wolnego miejsca, aby pomieścić żądania alokacji dużych obiektów, GC najpierw próbuje uzyskać więcej segmentów z os. Jeśli to się nie powiedzie, wyzwala generacji 2 GC w nadziei na uwolnienie trochę miejsca.

Podczas generacji 1 lub generacji 2 GC moduł zbierający elementy bezużyteczne zwalnia segmenty, które nie mają obiektów na żywo na nich z powrotem do os, wywołując [VirtualFree funkcji](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree). Spacja po ostatnim obiekcie na żywo na końcu segmentu jest uchylana (z wyjątkiem segmentu efemeralnego, w którym działa gen0/gen1, gdzie moduł zbierający elementy bezużyteczne zachowuje pewne zatwierdzone, ponieważ aplikacja będzie przydzielać w nim od razu). Wolne miejsca pozostają zatwierdzone, mimo że są resetowane, co oznacza, że serwer operacyjny nie musi zapisywać danych w nich z powrotem na dysk.

Ponieważ LOH jest zbierany tylko podczas generacji 2 GC, segment LOH może zostać uwolniony tylko podczas takiego GC. Rysunek 3 przedstawia scenariusz, w którym moduł odśmiecania pamięci zwalnia jeden segment (segment 2) z powrotem do os i anutuje więcej miejsca na pozostałych segmentach. Jeśli musi użyć nieprzydzielonych miejsca na końcu segmentu, aby spełnić żądania alokacji dużych obiektów, ponownie zatwierdza pamięć. (Aby uzyskać wyjaśnienie zatwierdzenia/dezcommit, zobacz dokumentację [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).

![Rysunek 3: LOH po gc gen 2](media/loh/loh-figure-3.jpg)\
Rysunek 3: LOH po 2 generacji GC

## <a name="when-is-a-large-object-collected"></a>Kiedy zbiera się duży obiekt?

Ogólnie rzecz biorąc GC występuje, gdy jeden z następujących 3 warunki dzieje:

- Alokacja przekracza próg generacji 0 lub dużego obiektu.

  Próg jest właściwością generacji. Próg dla generacji jest ustawiany, gdy moduł zbierający elementy bezużyteczne przydziela do niego obiekty. Po przekroczeniu progu gc jest wyzwalany na tej generacji. Podczas przydzielania małych lub dużych obiektów, należy użyć generacji 0 i progi LOH, odpowiednio. Gdy moduł zbierający elementy bezużyteczne przydziela do generacji 1 i 2, zużywa ich progi. Progi te są dynamicznie dostrojone podczas pracy programu.

  Jest to typowy przypadek; większość kontrolerów gcs się odbywa z powodu alokacji na zarządzanym stercie.

- Metoda <xref:System.GC.Collect%2A?displayProperty=nameWithType> jest wywoływana.

  Jeśli metoda <xref:System.GC.Collect?displayProperty=nameWithType> bezparametrów jest wywoływana lub <xref:System.GC.MaxGeneration?displayProperty=nameWithType> inne przeciążenie jest przekazywane jako argument, LOH jest zbierane wraz z resztą zarządzanego sterty.

- System znajduje się w małej ilości pamięci.

  Dzieje się tak, gdy moduł zbierający elementy bezużyteczne odbiera powiadomienie o wysokiej pamięci z os. Jeśli moduł zbierający elementy bezużyteczne uważa, że wykonywanie generacji 2 GC będzie produktywne, wyzwala jeden.

## <a name="loh-performance-implications"></a>Implikacje wydajności LOH

Alokacje na stercie dużych obiektów wpływ na wydajność w następujący sposób.

- Koszt alokacji.

  CLR sprawia, że gwarancja, że pamięć dla każdego nowego obiektu, który rozdaje jest wyczyszczone. Oznacza to, że koszt alokacji dużego obiektu jest całkowicie zdominowany przez wyczyszczenie pamięci (chyba że wyzwala GC). Jeśli trwa 2 cykle, aby wyczyścić jeden bajt, trwa 170.000 cykli, aby wyczyścić najmniejszy duży obiekt. Wyczyszczenie pamięci obiektu o rozmiarze 16 MB na komputerze 2 GHz zajmuje około 16 ms. To dość duży koszt.

- Koszt odbioru.

  Ponieważ LOH i generacji 2 są zbierane razem, jeśli jeden próg zostanie przekroczony, generacji 2 kolekcji jest wyzwalany. Jeśli kolekcja 2 generacji jest wyzwalana z powodu LOH, generacja 2 nie musi być znacznie mniejsza po GC. Jeśli nie ma zbyt wiele danych na generacji 2, ma to minimalny wpływ. Ale jeśli generacja 2 jest duża, może to spowodować problemy z wydajnością, jeśli zostanie wyzwolonych wiele kontrolerów GCs generacji 2. Jeśli wiele dużych obiektów są przydzielane na bardzo tymczasowe i masz duży SOH, można spędzać zbyt dużo czasu robi GCs. Ponadto koszt alokacji może naprawdę się sumować, jeśli nadal przydzielania i puszczania naprawdę dużych obiektów.

- Elementy tablicy z typami odwołań.

  Bardzo duże obiekty na LOH są zazwyczaj tablice (jest bardzo rzadko mają obiekt wystąpienia, który jest naprawdę duży). Jeśli elementy tablicy są bogate w odwołania, ponosi koszt, który nie jest obecny, jeśli elementy nie są bogate w odwołania. Jeśli element nie zawiera żadnych odwołań, moduł zbierający elementy bezużyteczne nie musi w ogóle przechodzić przez tablicę. Na przykład jeśli używasz tablicy do przechowywania węzłów w drzewie binarnym, jednym ze sposobów zaimplementowania jest odwoływanie się do węzła prawego i lewego węzła przez rzeczywiste węzły:

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

  Zamiast odwoływać się do danych lewego węzła `left.d`jako `binary_tr[left_index].d`, można odnosić się do niego jako . A moduł zbierający elementy bezużyteczne nie musi patrzeć na żadne odwołania dla lewego i prawego węzła.

Z trzech czynników, pierwsze dwa są zwykle bardziej znaczące niż trzeci. Z tego powodu zaleca się przydzielenie puli dużych obiektów, które są ponownie używane zamiast przydzielania tymczasowych.

## <a name="collecting-performance-data-for-the-loh"></a>Zbieranie danych o wydajności dla LOH

Przed zebraniem danych dotyczących wydajności dla określonego obszaru należy już wykonać następujące czynności:

1. Znaleziono dowody, że powinieneś przyjrzeć się tej dziedzinie.

2. Wyczerpane inne obszary, które znasz, nie znajdując niczego, co mogłoby wyjaśnić problem z wydajnością, który widziałeś.

Zobacz blog [Opis ztym problemem, zanim spróbujesz znaleźć rozwiązanie, aby](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) uzyskać więcej informacji na temat podstaw pamięci i procesora CPU.

Do zbierania danych na temat wydajności LOH można używać następujących narzędzi:

- [Liczniki wydajności pamięci CLR .NET](#net-clr-memory-performance-counters)

- [zdarzenia ETW](#etw-events)

- [Debuger](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>Liczniki wydajności pamięci CLR .NET

Te liczniki wydajności są zwykle dobrym pierwszym krokiem w badaniu problemów z wydajnością (chociaż zaleca się użycie [zdarzeń ETW).](#etw-events) Monitor wydajności można skonfigurować, dodając liczniki, które mają, jak pokazano na rysunku 4. Te, które są istotne dla LOH są:

- **Kolekcje Gen 2**

   Wyświetla liczbę powtórzeń generacji 2 kontrolerów domeny od czasu rozpoczęcia procesu. Licznik jest zwiększany na końcu kolekcji generacji 2 (nazywanerównież pełne wyrzucanie elementów bezużytecznych). Ten licznik wyświetla ostatnio zaobserwowaną wartość.

- **Rozmiar sterty dużych obiektów**

   Wyświetla bieżący rozmiar, w bajtach, w tym wolne miejsce, LOH. Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, a nie na każdej alokacji.

Typowym sposobem patrzenia na liczniki wydajności jest monitor wydajności (perfmon.exe). Użyj "Dodaj liczniki", aby dodać interesujący licznik dla procesów, na których Ci zależy. Dane licznika wydajności można zapisać w pliku dziennika, jak pokazano na rysunku 4:

![Zrzut ekranu przedstawiający dodawanie liczników wydajności.](media/large-object-heap/add-performance-counter.png)
Rysunek 4: LOH po 2 generacji GC

Liczniki wydajności można również programowo przeszukiwać. Wiele osób zbiera je w ten sposób w ramach rutynowego procesu testowania. Kiedy wykrywają liczniki z wartościami, które są nietypowe, używają innych środków, aby uzyskać bardziej szczegółowe dane, aby pomóc w dochodzeniu.

> [!NOTE]
> Zaleca się używanie zdarzeń ETW zamiast liczników wydajności, ponieważ ETW dostarcza znacznie bogatszych informacji.

### <a name="etw-events"></a>zdarzenia ETW

Moduł zbierający elementy bezużyteczne udostępnia bogaty zestaw zdarzeń ETW, które pomogą Ci zrozumieć, co robi sterta i dlaczego. Następujące wpisy na blogu pokazują, jak zbierać i rozumieć zdarzenia GC za pomocą ETW:

- [Gc ETW Wydarzenia - 1](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [Gc ETW Wydarzenia - 2](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [Gc ETW Wydarzenia - 3](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [Gc ETW Wydarzenia - 4](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

Aby zidentyfikować nadmierne generacje 2 gcs spowodowane tymczasowymi alokacjami LOH, przyjrzyj się kolumnie Przyczyna wyzwalacza dla kontrolerów GCs. Aby uzyskać prosty test, który przydziela tylko tymczasowe duże obiekty, można zbierać informacje o zdarzeniach ETW za pomocą następującego wiersza polecenia [PerfView:](https://www.microsoft.com/download/details.aspx?id=28567)

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

Wynik jest coś takiego:

![Zrzut ekranu przedstawiający zdarzenia ETW w perfview.](media/large-object-heap/event-tracing-windows-perfview.png)
Rysunek 5: Zdarzenia ETW wyświetlane za pomocą PerfView

Jak widać, wszystkie GP generacji 2 i wszystkie są wyzwalane przez AllocLarge, co oznacza, że przydzielanie dużego obiektu wyzwoliło ten GC. Wiemy, że te przydziały są tymczasowe, ponieważ kolumna **LOH Survival Rate %** mówi 1%.

Można zbierać dodatkowe zdarzenia ETW, które informują, kto przydzielił te duże obiekty. Następujący wiersz polecenia:

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

zbiera AllocationTick zdarzenie, które jest uruchamiane w przybliżeniu co 100k wartości alokacji. Innymi słowy zdarzenie jest uruchamiany za każdym razem, gdy duży obiekt jest przydzielany. Następnie można spojrzeć na jeden z widoków GC Heap Alloc, które pokazują stosy wywołań, które adzielone dużych obiektów:

![Zrzut ekranu przedstawiający widok sterty modułu zbierającego elementy bezużyteczne.](media/large-object-heap/garbage-collector-heap.png)
Rysunek 6: Widok alloc sterty GC

Jak widać, jest to bardzo prosty test, który po `Main` prostu przydziela duże obiekty z jego metody.

### <a name="a-debugger"></a>Debuger

Jeśli wszystko, co masz jest zrzut pamięci i trzeba spojrzeć na jakie obiekty są faktycznie na LOH, można użyć [rozszerzenia debugera SoS](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) dostarczone przez .NET.

> [!NOTE]
> Polecenia debugowania wymienione w tej sekcji mają zastosowanie do [debugerów systemu Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).

Poniżej przedstawiono przykładowe dane wyjściowe z analizy LOH:

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

Rozmiar sterty LOH wynosi (16 754 224 + 16 699 288 + 16 284 504) = 49 738 016 bajtów. Między adresami 023e1000 i 033db630, 8 008 736 bajtów <xref:System.Object?displayProperty=nameWithType> jest zajmowanych przez tablicę obiektów, 6 663 696 bajtów zajmują tablica <xref:System.Byte?displayProperty=nameWithType> obiektów, a 2 081 792 bajtów zajmują wolne miejsce.

Czasami debuger pokazuje, że całkowity rozmiar LOH jest mniejsza niż 85.000 bajtów. Dzieje się tak, ponieważ czas wykonywania sam używa LOH do przydzielenia niektórych obiektów, które są mniejsze niż duży obiekt.

Ponieważ LOH nie jest zagęszczony, czasami LOH jest uważany za źródło fragmentacji. Fragmentacja oznacza:

- Fragmentacja zarządzanej sterty, która jest wskazywana przez ilość wolnego miejsca między obiektami zarządzanymi. W `!dumpheap –type Free` usg, polecenie wyświetla ilość wolnego miejsca między obiektami zarządzanymi.

- Fragmentacja przestrzeni adresowej pamięci wirtualnej (VM), czyli `MEM_FREE`pamięci oznaczonej jako . Można go uzyskać za pomocą różnych poleceń debugera w windbg.

   W poniższym przykładzie przedstawiono fragmentację w przestrzeni maszyny Wirtualnej:

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

Jest bardziej powszechne, aby zobaczyć fragmentacji maszyny wirtualnej spowodowane przez tymczasowe dużych obiektów, które wymagają modułzbierający elementy bezużyteczne do często nabywania nowych zarządzanych segmentów sterty z systemu operacyjnego i zwolnić puste z powrotem do systemu operacyjnego.

Aby sprawdzić, czy LOH jest przyczyną fragmentacji maszyn wirtualnych, można ustawić punkt przerwania na [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) i [VirtualFree,](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) aby zobaczyć, kto do nich wywołać. Na przykład, aby zobaczyć, kto próbował przydzielić fragmenty pamięci wirtualnej większe niż 8MBB z os, można ustawić punkt przerwania w ten sposób:

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

To polecenie jest podzielone na debuger i pokazuje stos wywołań tylko wtedy, gdy [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) jest wywoływana o rozmiarze alokacji większym niż 8 MB (0x800000).

W clr 2.0 dodano funkcję o nazwie *VM Hoarding,* która może być przydatna w scenariuszach, w których segmenty (w tym na stertach dużych i małych obiektów) są często nabywane i zwalniane. Aby określić vm hoarding, należy `STARTUP_HOARD_GC_VM` określić flagę uruchamiania wywoływaną za pośrednictwem hostingu interfejsu API. Zamiast zwalniać puste segmenty z powrotem do os, CLR anutuje pamięć w tych segmentach i umieszcza je na liście gotowości. (Należy zauważyć, że CLR nie robi tego dla segmentów, które są zbyt duże.) CLR później używa tych segmentów do spełnienia nowych żądań segmentu. Następnym razem, gdy aplikacja potrzebuje nowego segmentu, CLR używa jednego z tej listy gotowości, jeśli może znaleźć taki, który jest wystarczająco duży.

Gromadzenie maszyn wirtualnych jest również przydatne w przypadku aplikacji, które chcą trzymać się segmentów, które już nabyły, takich jak niektóre aplikacje serwera, które są dominującymi aplikacjami działającymi w systemie, aby uniknąć wyjątków z pamięci.

Zdecydowanie zaleca się, aby dokładnie przetestować aplikację podczas korzystania z tej funkcji, aby upewnić się, że aplikacja ma dość stabilne użycie pamięci.
