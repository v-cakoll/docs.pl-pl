---
title: Sterta dużych obiektów (LOH) w systemie Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: ab9beca58b3d6118bc0f5121b6f5dec71a9f9f36
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102271"
---
# <a name="the-large-object-heap-on-windows-systems"></a>Sterta dużych obiektów w systemach Windows

Moduł zbierający elementy bezużyteczne .NET (GC) dzieli obiekty na małe i duże obiekty. Gdy obiekt jest duży, niektóre z jego atrybutów stają się bardziej znaczące niż jeśli obiekt jest mały. Na przykład kompaktowanie&mdash;go, czyli kopiowanie go w&mdash;pamięci w innym miejscu na stercie może być kosztowne. Z tego powodu moduł zbierający elementy bezużyteczne umieszcza duże obiekty na stercie dużych obiektów (LOH). W tym artykule omówiono, co kwalifikuje obiekt jako duży obiekt, jak duże obiekty są zbierane i jakiego rodzaju wpływ na wydajność nakładają duże obiekty.

> [!IMPORTANT]
> W tym artykule omówiono sterty dużych obiektów w programie .NET Framework i .NET Core uruchomionym tylko w systemach Windows. Nie obejmuje loh działających na implementacje .NET na innych platformach.

## <a name="how-an-object-ends-up-on-the-loh"></a>Jak obiekt kończy się na LOH

Jeśli obiekt jest większy lub równy rozmiarowi 85 000 bajtów, jest uważany za duży obiekt. Liczba ta została określona przez dostrajanie wydajności. Gdy żądanie alokacji obiektu jest dla 85 000 lub więcej bajtów, środowisko wykonawcze przydziela je na stercie dużego obiektu.

Aby zrozumieć, co to oznacza, warto zbadać niektóre podstawy dotyczące modułu zbierającego elementy bezużyteczne.

Moduł zbierający elementy bezużyteczne jest modułem zbierającym generację. Ma trzy pokolenia: pokolenie 0, pokolenie 1 i pokolenie 2. Powodem posiadania 3 pokoleń jest to, że w dobrze dostrojone aplikacji, większość obiektów umiera w gen0. Na przykład w aplikacji serwera alokacje skojarzone z każdym żądaniem powinny umrzeć po zakończeniu żądania. Wnioski o przydział w locie sprawią, że będzie on akcjum1 i tam umrze. Zasadniczo gen1 działa jako bufor między młodymi obszarami obiektów a obszarami obiektów o długim okresie życia.

Małe obiekty są zawsze przydzielane w generacji 0 i, w zależności od ich żywotności, mogą być promowane do generacji 1 lub generacji2. Duże obiekty są zawsze przydzielane w generacji 2.

Duże obiekty należą do generacji 2, ponieważ są zbierane tylko podczas kolekcji generacji 2. Po zebraniu pokolenia zbierane są również wszystkie jego młodsze pokolenia. Na przykład, gdy dzieje się generacji 1 GC, zarówno generacji 1 i 0 są zbierane. A kiedy dzieje się generacji 2 GC, cała sterta jest zbierana. Z tego powodu, generacji 2 GC jest również nazywany *pełnym GC*. Ten artykuł odnosi się do generacji 2 GC zamiast pełnego GC, ale warunki są wymienne.

Pokolenia zapewniają logiczny widok sterty GC. Fizycznie obiekty znajdują się w segmentach zarządzanych sterty. *Segment zarządzanego sterty* jest fragmentem pamięci, który GC rezerwuje z systemu operacyjnego, wywołując [virtualalloc funkcji](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) w imieniu kodu zarządzanego. Po załadowaniu clr, GC przydziela dwa początkowe segmenty sterty: jeden dla małych obiektów (sterty małych obiektów lub SOH) i jeden dla dużych obiektów (sterty dużych obiektów).

Żądania alokacji są następnie spełnione przez umieszczenie zarządzanych obiektów w tych segmentach zarządzanych sterty. Jeśli obiekt jest mniejszy niż 85 000 bajtów, jest umieszczany na segmencie dla soh; w przeciwnym razie jest on umieszczany na segmencie LOH. Segmenty są zatwierdzane (w mniejszych fragmentów), jak coraz więcej obiektów są przydzielane do nich.
Dla SOH obiekty, które przetrwają GC są promowane do następnej generacji. Obiekty, które przetrwają kolekcję generacji 0 są teraz uważane za obiekty generacji 1 i tak dalej. Jednak obiekty, które przetrwają najstarszą generację, są nadal uważane za najstarsze pokolenie. Innymi słowy, ocalałych z generacji 2 są obiekty generacji 2; i ocalałych z LOH są obiekty LOH (które są zbierane z gen2).

Kod użytkownika można przydzielić tylko w generacji 0 (małe obiekty) lub LOH (duże obiekty). Tylko GC może "przydzielać" obiekty w pierwszej generacji (poprzez promowanie ocalałych z pokolenia 0) i generacji 2 (poprzez promowanie ocalałych z pokoleń 1 i 2).

Po wyzwoleniu wyrzucania elementów bezużytecznych GC śledzi obiekty aktywne i kompakuje je. Ale ponieważ zagęszczanie jest drogie, GC *zamiata* LOH; sprawia, że wolna lista z martwych obiektów, które mogą być ponownie ponownie zaspokojone później, aby spełnić żądania alokacji dużych obiektów. Sąsiadujące martwe obiekty są przekształcane w jeden wolny obiekt.

.NET Core i .NET Framework (począwszy od .NET Framework 4.5.1) zawierają <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> właściwość, która umożliwia użytkownikom określenie, że LOH powinny być kompaktowane podczas następnego pełnego blokowania GC. A w przyszłości .NET może zdecydować się na automatyczne kompaktowanie LOH. Oznacza to, że jeśli przydzielisz duże obiekty i chcesz się upewnić, że nie są one przesuniętye, nadal należy je przypiąć.

Rysunek 1 ilustruje scenariusz, w którym GC tworzy generację `Obj1` `Obj3` 1 po pierwszej generacji 0 GC, gdzie `Obj2` `Obj5` i są martwe, i tworzy generację 2 po pierwszej generacji 1 GC, gdzie i są martwe. Należy pamiętać, że to i następujące liczby są tylko w celach ilustracyjnych; zawierają one bardzo niewiele obiektów, aby lepiej pokazać, co dzieje się na stercie. W rzeczywistości wiele więcej obiektów są zazwyczaj zaangażowane w GC.

![Rysunek 1: Gen 0 GC i gen 1 GC](media/loh/loh-figure-1.jpg)\
Rysunek 1: Generacja 0 i generacja 1 GC.

Rysunek 2 pokazuje, że po generacji `Obj1` `Obj2` 2 GC, który widział, że i są martwe, GC `Obj1` `Obj2`tworzy przyległe wolne miejsce `Obj4`z pamięci, które były zajęte przez i , który następnie został użyty do spełnienia żądania alokacji dla . Spacja po ostatnim `Obj3`obiekcie , do końca segmentu może być również używana do spełniania żądań alokacji.

![Rysunek 2: Po gen 2 GC](media/loh/loh-figure-2.jpg)\
Rysunek 2: Po generacji 2 GC

Jeśli nie ma wystarczającej ilości wolnego miejsca, aby pomieścić żądania alokacji dużych obiektów, GC najpierw próbuje uzyskać więcej segmentów z systemu operacyjnego. Jeśli to się nie powiedzie, wyzwala generacji 2 GC w nadziei na uwolnienie trochę miejsca.

Podczas generacji 1 lub generacji 2 GC moduł zbierający elementy bezużyteczne zwalnia segmenty, które nie mają na nich obiektów na żywo z powrotem do systemu operacyjnego, wywołując [virtualfree funkcji](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree). Miejsce po ostatnim obiektu na żywo do końca segmentu jest umorzony (z wyjątkiem segmentu efemeryczny, gdzie gen0/gen1 żyć, gdzie moduł zbierający elementy bezużyteczne przechowuje niektóre zatwierdzone, ponieważ aplikacja będzie przydzielanie w nim od razu). Wolne miejsca pozostają zatwierdzone, mimo że są resetowane, co oznacza, że system operacyjny nie musi zapisywać w nich danych z powrotem na dysk.

Ponieważ LOH jest zbierany tylko podczas generacji 2 GC, segment LOH może zostać uwolniony tylko podczas takiego GC. Rysunek 3 ilustruje scenariusz, w którym moduł zbierający elementy bezużyteczne zwalnia jeden segment (segment 2) z powrotem do systemu operacyjnego i ulikuje więcej miejsca na pozostałych segmentach. Jeśli musi użyć miejsca umorzone na końcu segmentu, aby spełnić żądania alokacji dużych obiektów, zatwierdza pamięć ponownie. (Aby uzyskać wyjaśnienie commit/decommit, zobacz dokumentację [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).

![Rysunek 3: LOH po gen 2 GC](media/loh/loh-figure-3.jpg)\
Rysunek 3: LOH po generacji 2 GC

## <a name="when-is-a-large-object-collected"></a>Kiedy zbierany jest duży obiekt?

Ogólnie rzecz biorąc, GC występuje w jednym z następujących trzech warunków:

- Alokacja przekracza próg generacji 0 lub dużego obiektu.

  Próg jest właściwością pokolenia. Próg dla generacji jest ustawiany, gdy moduł zbierający elementy bezużyteczne przydziela obiekty do niego. Po przekroczeniu progu gc jest wyzwalany na tej generacji. Podczas przydzielania małych lub dużych obiektów, zużywają generacji 0 i progi LOH, odpowiednio. Gdy moduł zbierający elementy bezużyteczne przydziela do generacji 1 i 2, zużywa ich progi. Progi te są dynamicznie dostrojone podczas uruchamiania programu.

  Jest to typowy przypadek; większość gc się z powodu alokacji na zarządzanym stosie.

- Metoda <xref:System.GC.Collect%2A?displayProperty=nameWithType> jest wywoływana.

  Jeśli metoda <xref:System.GC.Collect?displayProperty=nameWithType> bez parametrów jest wywoływana <xref:System.GC.MaxGeneration?displayProperty=nameWithType> lub inne przeciążenie jest przekazywana jako argument, LOH są zbierane wraz z resztą zarządzanego stosu.

- System znajduje się w sytuacji małej pamięci.

  Dzieje się tak, gdy moduł zbierający elementy bezużyteczne odbiera powiadomienie o wysokiej pamięci z systemu operacyjnego. Jeśli moduł zbierający elementy bezużyteczne uważa, że robi generacji 2 GC będzie produktywne, wyzwala jeden.

## <a name="loh-performance-implications"></a>Wpływ loh na wydajność

Alokacje na stercie dużych obiektów wpływają na wydajność w następujący sposób.

- Koszt alokacji.

  CLR sprawia, że gwarancja, że pamięć dla każdego nowego obiektu, który daje jest wyczyszczone. Oznacza to, że koszt alokacji dużego obiektu jest całkowicie zdominowany przez wyczyszczenie pamięci (chyba że wyzwala GC). Jeśli trwa 2 cykle, aby wyczyścić jeden bajt, trwa 170.000 cykli, aby wyczyścić najmniejszy duży obiekt. Wyczyszczenie pamięci obiektu o rozmiarze 16 MB na komputerze 2GHz zajmuje około 16 m. To dość duży koszt.

- Koszt odbioru.

  Ponieważ LOH i generacji 2 są zbierane razem, jeśli jeden próg zostanie przekroczony, kolekcja generacji 2 jest wyzwalany. Jeśli kolekcja generacji 2 jest wyzwalana z powodu LOH, generacja 2 nie musi być znacznie mniejsza po GC. Jeśli nie ma zbyt wiele danych na temat generacji 2, ma to minimalny wpływ. Ale jeśli generacja 2 jest duża, może powodować problemy z wydajnością, jeśli zostanie uruchomionych wiele gc generacji 2. Jeśli wiele dużych obiektów są przydzielane na bardzo tymczasowe i masz duży SOH, można spędzać zbyt dużo czasu robi GCs. Ponadto koszt alokacji może naprawdę się sumować, jeśli nadal przydzielasz i puszczasz naprawdę duże obiekty.

- Elementy tablicy z typami odwołań.

  Bardzo duże obiekty na LOH są zwykle tablice (bardzo rzadko mają obiekt wystąpienia, który jest naprawdę duży). Jeśli elementy tablicy są bogate w odwołania, ponosi koszt, który nie jest obecny, jeśli elementy nie są bogate w odwołania. Jeśli element nie zawiera żadnych odwołań, moduł zbierający elementy bezużyteczne nie trzeba przejść przez tablicę w ogóle. Na przykład jeśli używasz tablicy do przechowywania węzłów w drzewie binarnym, jednym ze sposobów jego zaimplementowania jest odwoływanie się do prawego i lewego węzła węzła przez rzeczywiste węzły:

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  Jeśli `num_nodes` jest duży, moduł zbierający elementy bezużyteczne musi przejść przez co najmniej dwa odwołania na element. Alternatywnym podejściem jest przechowywanie indeksu węzłów po prawej i lewej stronie:

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  Zamiast odwoływać się do danych lewego węzła `left.d`jako `binary_tr[left_index].d`, odnosisz się do niego jako . A moduł zbierający elementy bezużyteczne nie trzeba patrzeć na żadnych odwołań do lewego i prawego węzła.

Z trzech czynników, pierwsze dwa są zwykle bardziej znaczące niż trzeci. Z tego powodu zaleca się przydzielić pulę dużych obiektów, które można ponownie użyć zamiast przydzielania tymczasowych.

## <a name="collect-performance-data-for-the-loh"></a>Zbieranie danych dotyczących wydajności dla LOH

Przed zebraniem danych o wydajności dla określonego obszaru należy już wykonać następujące czynności:

1. Znaleziono dowody, że należy spojrzeć na ten obszar.

2. Wyczerpane inne obszary, które znasz, nie znajdując niczego, co mogłoby wyjaśnić problem z wydajnością, który widziałeś.

Zobacz blog [Zrozumieć problem, zanim spróbujesz znaleźć rozwiązanie, aby uzyskać](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) więcej informacji na temat podstaw pamięci i procesora.

Do zbierania danych na temat wydajności LOH można użyć następujących narzędzi:

- [Liczniki wydajności pamięci CLR platformy .NET](#net-clr-memory-performance-counters)

- [zdarzenia ETW](#etw-events)

- [Debuger](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>Liczniki wydajności pamięci CLR platformy .NET

Te liczniki wydajności są zwykle dobrym pierwszym krokiem w badaniu problemów z wydajnością (chociaż zaleca się używanie [zdarzeń ETW).](#etw-events) Monitor wydajności można skonfigurować, dodając żądane liczniki, jak pokazano na rysunku 4. Te, które są istotne dla LOH są:

- **Kolekcje Gen 2**

   Wyświetla liczbę razy generacji 2 GC wystąpiły od momentu rozpoczęcia procesu. Licznik jest zwiększany na końcu kolekcji generacji 2 (nazywane również pełną wyrzucaniem elementów bezużytecznych). Ten licznik wyświetla ostatnią zaobserwowaną wartość.

- **Rozmiar sterty dużego obiektu**

   Wyświetla bieżący rozmiar w bajtach, w tym wolne miejsce, LOH. Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, a nie w każdej alokacji.

Typowym sposobem patrzenia na liczniki wydajności jest monitor wydajności (perfmon.exe). Użyj "Dodaj liczniki", aby dodać interesujący licznik dla procesów, na których Ci zależy. Dane licznika wydajności można zapisać w pliku dziennika, jak pokazano na rysunku 4:

![Zrzut ekranu przedstawiający dodawanie liczników wydajności.](media/large-object-heap/add-performance-counter.png)
Rysunek 4: LOH po generacji 2 GC

Liczniki wydajności można również wyszukiwać programowo. Wiele osób zbiera je w ten sposób w ramach rutynowego procesu testowania. Gdy wykryć liczniki z wartościami, które są nietypowe, używają innych środków, aby uzyskać bardziej szczegółowe dane, aby pomóc w dochodzeniu.

> [!NOTE]
> Zaleca się używanie zdarzeń ETW zamiast liczników wydajności, ponieważ ETW dostarcza znacznie bogatszych informacji.

### <a name="etw-events"></a>zdarzenia ETW

Moduł zbierający elementy bezużyteczne udostępnia bogaty zestaw zdarzeń ETW, które pomogą Ci zrozumieć, co robi sterty i dlaczego. Następujące wpisy w blogu pokazują, jak zbierać i rozumieć zdarzenia GC z ETW:

- [Wydarzenia ETW GC - 1](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [Wydarzenia ETW GC - 2](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [Wydarzenia ETW GC - 3](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [Wydarzenia ETW GC - 4](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

Aby zidentyfikować nadmierne generacji 2 GC spowodowane przez tymczasowe alokacje LOH, należy spojrzeć na trigger reason kolumny dla gc. W przypadku prostego testu, który przydziela tylko tymczasowe duże obiekty, można zbierać informacje o zdarzeniach ETW za pomocą następującego wiersza polecenia [PerfView:](https://www.microsoft.com/download/details.aspx?id=28567)

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

Rezultatem jest coś takiego:

![Zrzut ekranu przedstawiający zdarzenia ETW w perfView.](media/large-object-heap/event-tracing-windows-perfview.png)
Rysunek 5: Zdarzenia ETW wyświetlane przy użyciu PerfView

Jak widać, wszystkie gc są generacji 2 GCs, i wszystkie są one wyzwalane przez AllocLarge, co oznacza, że przydzielanie duży obiekt wyzwolił ten GC. Wiemy, że te przydziały są tymczasowe, ponieważ kolumna **LOH Survival Rate %** mówi 1%.

Można zbierać dodatkowe zdarzenia ETW, które informują, kto przydzielił te duże obiekty. Następujący wiersz polecenia:

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

zbiera allocationTick zdarzenie, które jest uruchamiane około co 100k warto alokacji. Innymi słowy zdarzenie jest uruchamiany za każdym razem, gdy duży obiekt jest przydzielany. Następnie można spojrzeć na jeden z GC Heap Alloc widoki, które pokazują, że callstacks, które przydzielone duże obiekty:

![Zrzut ekranu przedstawiający widok sterty modułu zbierającego elementy bezużyteczne.](media/large-object-heap/garbage-collector-heap.png)
Rysunek 6: Widok GC Heap Alloc

Jak widać, jest to bardzo prosty test, który po `Main` prostu przydziela duże obiekty z jego metody.

### <a name="a-debugger"></a>Debuger

Jeśli wszystko, co masz, to zrzut pamięci i musisz sprawdzić, jakie obiekty znajdują się w rzeczywistości na LOH, możesz użyć [rozszerzenia debugera SoS dostarczonego](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) przez .NET.

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

Rozmiar sterty LOH wynosi (16 754 224 + 16 699 288 + 16 284 504) = 49 738 016 bajtów. Między adresami 023e1000 i 033db630, 8,008,736 bajty <xref:System.Object?displayProperty=nameWithType> są zajęte przez tablicę obiektów, 6,663,696 bajty są zajęte przez tablicę <xref:System.Byte?displayProperty=nameWithType> obiektów, a 2,081,792 bajty są zajęte przez wolne miejsce.

Czasami debuger pokazuje, że całkowity rozmiar LOH jest mniejszy niż 85 000 bajtów. Dzieje się tak, ponieważ środowisko wykonawcze używa LOH do przydzielenia niektórych obiektów, które są mniejsze niż duży obiekt.

Ponieważ LOH nie jest zagęszczona, czasami LOH jest uważany za źródło fragmentacji. Rozdrobnienie oznacza:

- Fragmentacja zarządzanego stosu, co jest wskazywane przez ilość wolnego miejsca między obiektami zarządzanymi. W sosie `!dumpheap –type Free` polecenie wyświetla ilość wolnego miejsca między obiektami zarządzanymi.

- Fragmentacja przestrzeni adresowej pamięci wirtualnej, która jest pamięcią oznaczoną jako `MEM_FREE`. Można go uzyskać za pomocą różnych poleceń debugera w windbg.

   W poniższym przykładzie pokazano fragmentację w przestrzeni maszyny Wirtualnej:

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

Jest bardziej powszechne, aby zobaczyć fragmentacji maszyny Wirtualnej spowodowane przez tymczasowe dużych obiektów, które wymagają modułu zbierającego elementy bezużyteczne często uzyskać nowe segmenty zarządzanych sterty z systemu operacyjnego i zwolnić puste z powrotem do systemu operacyjnego.

Aby sprawdzić, czy LOH powoduje fragmentację maszyny Wirtualnej, można ustawić punkt przerwania na [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) i [VirtualFree,](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) aby zobaczyć, kto je wywoła. Na przykład, aby zobaczyć, kto próbował przydzielić fragmenty pamięci wirtualnej większe niż 8MBB z systemu operacyjnego, można ustawić punkt przerwania w ten sposób:

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

To polecenie dzieli się na debuger i pokazuje stos wywołań tylko wtedy, [gdy VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) jest wywoływany o rozmiarze alokacji większym niż 8 MB (0x800000).

Program CLR 2.0 dodał funkcję o nazwie *VM Hoarding,* która może być przydatna w scenariuszach, w których segmenty (w tym na stertach dużych i małych obiektów) są często nabywane i zwalniane. Aby określić gromadzenie maszyn wirtualnych, należy `STARTUP_HOARD_GC_VM` określić flagę uruchamiania wywoływaną za pośrednictwem interfejsu API hostingu. Zamiast zwalniać puste segmenty z powrotem do systemu operacyjnego, CLR zwalnia pamięć w tych segmentach i umieszcza je na liście wstrzymania. (Należy zauważyć, że program CLR nie robi tego dla segmentów, które są zbyt duże). Clr później używa tych segmentów do zaspokojenia nowych żądań segmentu. Następnym razem, gdy aplikacja potrzebuje nowego segmentu, program CLR używa go z tej listy wstrzymania, jeśli można znaleźć taki, który jest wystarczająco duży.

Gromadzenie maszyn wirtualnych jest również przydatne w przypadku aplikacji, które chcą trzymać się segmentów, które zostały już nabyte, takich jak niektóre aplikacje serwera, które są dominującymi aplikacjami działającymi w systemie, aby uniknąć wyjątków braku pamięci.

Zdecydowanie zaleca się, aby dokładnie przetestować aplikację podczas korzystania z tej funkcji, aby upewnić się, że aplikacja ma dość stabilne użycie pamięci.
