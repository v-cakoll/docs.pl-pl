---
title: Sterty dużego obiektu w systemie Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 68513d2535ea9e19a42f9e58b9d423e17008f9de
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="the-large-object-heap-on-windows-systems"></a>Sterty dużego obiektu w systemie Windows

Moduł zbierający elementy bezużyteczne .NET (GC) dzieli obiektów w małych i dużych obiektów. Gdy obiekt jest duży, niektóre z jego atrybutów stają się większe znaczenie niż Jeśli obiekt jest mała. Na przykład kompaktowania — które skopiować go w innym miejscu pamięci sterty — może być kosztowne. W związku z tym moduł zbierający elementy bezużyteczne .NET umieszcza dużych obiektów na stercie dużego obiektu (LOH). W tym temacie wyjaśniono sterty dużego obiektu szczegółowo. Omówiono co kwalifikuje obiektu jako obiektu dużych, jak te duże obiekty są zbierane i nałożyć rodzaj wydajności wpływ dużych obiektów.

> [!IMPORTANT]
> W tym temacie omówiono sterty dużego obiektu w .NET Framework i .NET Core uruchomiony tylko w systemie Windows. Nie obejmuje LOH systemem implementacje .NET na innych platformach.

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a>Jak obiekt kończy się na sterty dużego obiektu i jak GC je obsługuje

Jeśli obiekt jest większa niż lub równa 85,000 bajtów, uwzględniono dużego obiektu. Ten numer został ustaleniami dostrajania wydajności. Gdy żądanie alokacji obiektu jest 85,000 lub więcej bajtów, środowisko uruchomieniowe przydziela na sterty dużego obiektu.

Aby zrozumieć, co to znaczy, warto zbadać niektóre podstawowe założenia dotyczące odzyskiwania pamięci platformy .NET.

Moduł zbierający elementy bezużyteczne .NET jest pokoleniowej modułu zbierającego. Ma trzy generacje: pokolenia 0, generację 1 i generacji 2. Powodem generacje 3 jest fakt, że w dobrze Zaczekaj aplikacji, większość struktury obiektów w gen0. Na przykład w aplikacji serwera, alokacji skojarzone z każdym żądaniem powinien die po zakończeniu żądania. Żądań alokacji locie będzie przekształcić gen1 i die istnieje. Zasadniczo gen1 pełni rolę bufora między obszarów małych obiektów i długotrwałe obiektu.

Małych obiektów są zawsze przydzielana podczas generowania 0 i, w zależności od ich istnienia może funkcjonować jako generacji 1 czy generation2. Duże obiekty są zawsze przydzielana podczas generowania 2.

Duże obiekty należą do generacji 2, ponieważ są one pobierane tylko podczas zbierania generacji 2. Podczas zbierania generacji jego młodszych generation(s) są także pobierane. Na przykład w przypadku odzyskiwania pamięci generacji 1 są zbierane zarówno generacji 1 i 0. A w przypadku odzyskiwania pamięci generacji 2 są zbierane całego stosu. Z tego powodu GC generacji 2 jest również nazywany *pełne GC*. Ten artykuł dotyczy generacji 2 GC zamiast pełną operacją GC, ale warunki są wymienne.

Generacje Podaj widok logiczny stercie GC. Fizycznie obiektów na żywo w segmentach sterty zarządzanej. A *segmentu sterty zarządzanej* to fragment, pamięci, która GC rezerwuje z systemu operacyjnego przez wywołanie metody [funkcji VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) imieniu kodu zarządzanego. Podczas ładowania CLR GC przydziela dwa segmenty początkowej sterty: jeden dla małych obiektów (małe sterty obiektów, lub raportu o kondycji) i jeden dla dużych obiektów (sterty obiektów wielkich).

Alokacja żądań następnie są spełnione przez umieszczenie zarządzanych obiektów na te segmenty sterty zarządzanej. Jeśli obiekt jest mniejszy niż 85,000 bajtów, jest on umieszczany w segmencie dla raportu o kondycji; w przeciwnym razie jest umieszczany w segmencie LOH. Segmenty są zatwierdzone (w mniejsze fragmenty) jako więcej i więcej obiektów są przydzielone do nich.
Dla raportu o kondycji obiekty, które pozostają aktualne po wykaz Globalny są awansowane do nowej generacji. Obiekty, które pozostają aktualne po kolekcji pokolenia 0, teraz są traktowane jako obiekty generacji 1 i tak dalej. Obiekty, które pozostają aktualne po najstarsze generowania nadal są uwzględniane w najstarsze generacji. Innymi słowy przy życiu z generacji 2 są obiekty generacji 2; i przy życiu z LOH są obiekty LOH, (które są pobierane z gen2). 

Kod użytkownika można alokować podczas generowania 0 (małych obiektów) lub LOH (duże obiekty). Tylko GC "alokowania" obiektów podczas generowania 1 (przez podwyższania poziomu przy życiu z pokolenia 0) i 2 (przez podwyższania poziomu przy życiu z pokolenia 1 i 2).

Po wyzwoleniu wyrzucania elementów bezużytecznych GC śledzi za pośrednictwem obiektów na żywo i kompaktowanie je. Jednak ponieważ kompaktowanie jest kosztowna, GC *wachlarzy* LOH; ułatwia wolnego listy poza martwy obiektów, które mogą być ponownie używane później do spełnienia żądań alokacji dużego obiektu. Sąsiadujących ze sobą obiektów martwy są wprowadzane do jednego obiektu wolne.

Oprogramowanie .NET core i .NET Framework (począwszy od platformy .NET Framework 4.5.1) obejmują <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty="fullname"> właściwość, która umożliwia użytkownikom, aby określić, że LOH powinien kompaktowanie podczas następnego pełnego GC blokowania. I w przyszłości, .NET mogą zdecydować skompaktować LOH automatycznie. Oznacza to, że jeśli przydzielić duże obiekty i chce mieć pewność, że nie przenoś powinien nadal przypniesz je.

Rysunek 1 przedstawiono scenariusz, w którym GC formularzy generacji 1 po pierwszej generacji 0 GC gdzie `Obj1` i `Obj3` są martwy, a formularzy generacji 2 po pierwszej generacji 1 GC gdzie `Obj2` i `Obj5` jest martwy. Należy zauważyć, że to i poniższe rysunki tylko w celach ilustracyjnych; zawierają one bardzo mało obiekty lepiej widoczne, co się dzieje na stosie. W rzeczywistości wiele innych obiektów są zazwyczaj wynikiem wykazem Globalnym.

![Rysunek 1: Operacja gen 0 GC i operacji gen 1 GC](media/loh/loh-figure-1.jpg)   
Rysunek 1: Generacji 0 i GC generacji 1.

Rysunek 2 wskazuje, że po GC generacji 2 który był wyświetlany, który `Obj1` i `Obj2` są martwy GC stanowi ciągły wolnego miejsca, za mało pamięci, używany jest zajmowany przez `Obj1` i `Obj2`, który następnie został użyty do spełnienia żądań alokacji Aby uzyskać `Obj4`. Ilość miejsca po ostatni obiekt `Obj3`, do końca segmentu mogą służyć do spełnienia żądań alokacji.
 
![Rysunek 2: po operacji gen 2 GC](media/loh/loh-figure-2.jpg)  
Rysunek 2: po GC generacji 2

Jeśli nie ma wystarczająco dużo wolnego miejsca do dużego obiektu żądań alokacji, wykaz Globalny najpierw próbuje uzyskać więcej segmentów z systemu operacyjnego. W przypadku niepowodzenia wyzwala odzyskiwania pamięci generacji 2 w mamy nadzieję, że z zwolnić miejsce.

Podczas generacji 1 czy generacji 2 GC, moduł zbierający elementy bezużyteczne zwalnia segmentów, które ma żadnych obiektów na żywo na ich do systemu operacyjnego przez wywołanie metody [funkcja VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx). Ilość miejsca po ostatni obiekt na żywo na końcu segmentu jest anulowane (z wyjątkiem w segmencie tymczasowych, gdy gen0/gen1 na żywo, a gdy moduł garbage collector zachować niektóre zatwierdzone, ponieważ aplikacja będzie przydziału w nim od razu). I wolnego miejsca do pozostać zatwierdzone, że są one resetowane, co oznacza system operacyjny nie musi zapisywać dane w ich do dysku.

Ponieważ LOH są zbierane podczas generowania 2 GC, LOH segment można zwolnić tylko podczas operacji GC. Rysunek 3 przedstawia scenariusz, w której moduł zbierający elementy bezużyteczne zwalnia jednego segmentu (segment 2) do systemu operacyjnego i decommits więcej miejsca na pozostałe segmenty. Jeśli musi używać anulowane miejsca na końcu segmentu do spełnienia żądań alokacji dużego obiektu, jego zatwierdza pamięć ponownie. (Opis commit/zrzeka się w dokumentacji dla [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx).
 
![Rysunek 3: LOH po operacji gen 2 GC](media/loh/loh-figure-3.jpg)  
Rysunek 3: LOH po GC generacji 2

## <a name="when-is-a-large-object-collected"></a>Gdy są zbierane dużego obiektu

Ogólnie rzecz biorąc GC występuje, gdy jedna z następujących warunków 3 następujących sytuacji:

- Alokacja przekracza generacji 0 lub próg dużego obiektu.

   Właściwość generacji jest wartość progową. Próg generacji jest ustawiona, gdy moduł garbage collector przydziela obiektów do niej. Po przekroczeniu progu wykaz Globalny jest wyzwalane w tej generacji. Podczas alokowania małych i dużych obiektów można używać generacji 0 i progi LOH odpowiednio. Gdy moduł garbage collector przydziela do generacji 1 i 2, zużywa ich progów. Tych progów są dopasowane dynamicznie, jak program będzie uruchamiany.

   To jest typową sytuacją; Większość GC się tak zdarzyć z powodu alokacje na stercie zarządzanej.

- <xref:System.GC.Collect%2A?displayProperty=nameWithType> Metoda jest wywoływana.

   Jeśli bez parametrów <xref:System.GC.Collect?displayProperty=nameWithType> metoda jest wywoływana lub innego przeciążenia jest przekazywany <xref:System.GC.MaxGeneration?displayProperty=nameWithType> jako argument LOH są zbierane wraz z resztą sterty zarządzanej.

- System jest w sytuacji braku pamięci.

   Dzieje się tak, gdy moduł garbage collector otrzyma powiadomienie pamięci wysokiej z systemu operacyjnego. Jeśli moduł zbierający elementy bezużyteczne sądzi, że podczas odzyskiwania pamięci generacji 2 nie będą produktywności, wyzwala jeden.

## <a name="loh-performance-implications"></a>Wpływ na wydajność LOH

Alokacje na stercie dużego obiektu wpływ na wydajność w następujący sposób.

- Alokacja kosztów.

   Środowisko CLR sprawia, że gwarancji czyszczeniu pamięci dla każdego nowego obiektu udostępnia. Oznacza to, że koszt alokacji dużego obiektu całkowicie jest zdominowany przez pamięci wyczyszczenie (chyba że wyzwala wykaz Globalny). Jeśli trwa cykli 2, aby wyczyścić jednego bajtu przyjmuje 170,000 cykle, aby wyczyścić najmniejszą dużego obiektu. Wyczyszczenie memmory obiektu 16MB na komputerze, 2GHz trwa około 16 ms. To jest raczej dużych kosztów.

- Kolekcja kosztów.

   Ponieważ LOH i generacji 2 są zbierane ze sobą, po przekroczeniu progu jednej firmy, zostanie wywołany kolekcji generacji 2. Jeśli generowania wyzwolenia kolekcji 2 z powodu LOH generacji 2 nie koniecznie znacznie mniejszy po GC. Jeśli w generacji 2 nie jest dużą ilość danych, to ma minimalny wpływ. Ale jeśli generacji 2 jest duży, może spowodować problemy z wydajnością, jeśli wiele GC generacji 2 są wyzwalane. Jeśli wiele duże obiekty są przydzielane na bardzo tymczasowego i konieczne jest duża raportu o kondycji, może spędzać zbyt dużo czasu wykonywania wykazów globalnych. Ponadto koszt alokacji można naprawdę sumują Jeśli zachowasz przydziału, dzięki czemu Przejdź naprawdę dużych obiektów.

- Elementy tablicy z typy referencyjne.

   Bardzo dużych obiektów na LOH są zazwyczaj tablic (jest bardzo rzadko mają naprawdę dużego obiektu wystąpienia). W przypadku elementów tablicy odwołania bogate generuje koszt, który nie jest obecny, jeśli elementy nie są bogate odwołania. Jeśli element nie zawiera żadnych odwołań, moduł zbierający elementy bezużyteczne nie musi przechodzić przez tablicy na wszystkich. Na przykład użycie tablicy do przechowywania węzłów w drzewie binarne jednym ze sposobów ją wdrożyć jest do odwoływania się do prawej i lewej węzła węzła za rzeczywiste węzłów:

   ```csharp
   class Node
   {
      Data d;
      Node left;
      Node right;
   };

   Node[] binary_tr = new Node [num_nodes];
   ```

   Jeśli `num_nodes` jest duży, moduł zbierający elementy bezużyteczne musi przechodzić przez co najmniej dwa odwołania dla każdego elementu. Informacje o innym podejściu ma indeks prawej i lewej węzłów magazynu:

   ```csharp
   class Node
   {
      Data d;
      uint left_index;
      uint right_index;
   } ;
   ```

   Zamiast odwołujących się po lewej stronie węzła dane jako `left.d`, możesz odwoływać się do niego jako `binary_tr[left_index].d`. I nie trzeba przyjrzeć się wszystkie odwołania dla węzła lewy i prawy moduł garbage collector.

Poza trzech czynników dwa pierwsze są zazwyczaj większe znaczenie niż trzeci. W związku z tym zaleca się przydzielenie puli dużych obiektów, które można ponownie użyć zamiast przydzielania czasowe. 

## <a name="collecting-performance-data-for-the-loh"></a>Zbieranie danych o wydajności dla LOH

Aby zebrać dane wydajności dla określonego obszaru, użytkownik powinien już zostały wykonane następujące:

1. Znaleziono dowód, że użytkownik powinien patrzeć na ten obszar.

1. Wyczerpane innych obszarów, które znasz niczego nie objaśniające problem z wydajnością, który został wyświetlony.

Znajduje się we wpisie [zrozumieć przed podjęciem próby rozwiązania](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) uzyskać więcej informacji o podstawowe informacje dotyczące procesora CPU i pamięci.

Następujące narzędzia służy do zbierania danych dotyczących wydajności LOH:

- [Liczniki wydajności pamięci .NET CLR](#net-clr-memory-performance-counters)

- [Zdarzenia ETW.](#etw-events)

- [Debuger](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a>Liczniki wydajności pamięci .NET CLR

Te liczniki wydajności są zwykle dobry, pierwszym krokiem w badaniu problemów z wydajnością (mimo że firma Microsoft zaleca użycie [zdarzenia ETW](#etw)). Możesz skonfigurować Monitor wydajności, dodając liczniki, które mają, jak pokazano na rysunku 4. Te, które są odpowiednie dla LOH są:

- **\# Kolekcje Gen 2**

   Wyświetla liczbę powtórzeń generacji 2 GC miały miejsce od rozpoczęcia procesu. Licznik jest zwiększany po zakończeniu kolekcji generacji 2 (nazywanej także pełną wyrzucania elementów bezużytecznych). Ten licznik wskazuje ostatnią odczytaną wartość.

- **Rozmiar sterty obiektów wielkich**

   Wyświetla bieżący rozmiar w bajtach, włącznie z wolnego miejsca, LOH. Ten licznik jest aktualizowany po zakończeniu operacji wyrzucania elementów bezużytecznych w każdej alokacji.

Jest to często stosowana metoda przyjrzeć się liczniki wydajności z Monitora wydajności (perfmon.exe). Użyj "Dodaj liczniki" można dodać licznika interesujące dla procesów, które są dla Ciebie ważne. Dane liczników wydajności można zapisać do pliku dziennika, jak pokazano na rysunku 4.

![Rysunek 4: Dodawanie liczników wydajności.](media/loh/perfcounter.png)    
Rysunek 4: LOH po GC generacji 2

Liczniki wydajności można również można zbadać programowo. Wiele osób zebrać je jako część procesu testowania rutynowych dzięki temu. Po ich dodatkowe liczniki z wartościami, które są niezwykłe, korzystają z innych metod Aby uzyskać bardziej szczegółowe dane ułatwiające dochodzenia.

> [!NOTE]
> Firma Microsoft zaleca, czy można użyć zdarzenia ETW zamiast wydajności liczników, ponieważ ETW zapewnia bardziej rozbudowane dużej ilości informacji.

### <a name="etw"></a>ETW

Moduł zbierający elementy bezużyteczne zawiera bogaty zestaw zdarzeń ETW, aby lepiej zrozumieć czynności sterty i dlaczego. Następujących wpisach w blogu pokazują, jak zbierać i zrozumieć zdarzenia GC za pomocą funkcji ETW:

- [Zdarzenia GC ETW - 1 ](http://blogs.msdn.com/b/maoni/archive/2014/12/22/gc-etw-events.aspx)

- [Zdarzenia GC ETW - 2](http://blogs.msdn.com/b/maoni/archive/2014/12/25/gc-etw-events-2.aspx)

- [Zdarzenia GC ETW - 3](http://blogs.msdn.com/b/maoni/archive/2014/12/25/gc-etw-events-3.aspx) 

- [Zdarzenia GC ETW - 4](http://blogs.msdn.com/b/maoni/archive/2014/12/30/gc-etw-events-4.aspx)

Aby zidentyfikować generowania nadmiernej GC 2 spowodowany tymczasowego alokacji LOH, poszukaj w kolumnie Przyczyna wyzwalacza wykazów globalnych. Prosty test tylko przydziela duże obiekty tymczasowe, można zbierać informacje dotyczące zdarzeń ETW z następującymi [narzędzia PerfView](https://www.microsoft.com/download/details.aspx?id=28567) wiersza polecenia:

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

Wynik jest podobny do następującego:
 
![Rysunek 5: Sprawdzenie zdarzenia ETW przy użyciu narzędzia PerfView](media/loh/perfview.png)  
Rysunek 5: Zdarzenia ETW pokazano przy użyciu narzędzia PerfView

Jak widać, wszystkich wykazów globalnych są generacji 2 GC, a ich są wszystkie wyzwalane przez AllocLarge, co oznacza, że przydzielanie dużego obiektu wyzwalane to GC. Wiemy, że te przydziały są tymczasowe ponieważ **% szybkość przetrwania LOH** kolumny mówi 1%.

Można zbierać dodatkowe zdarzenia ETW określające, kto przydzielone te dużych obiektów. Następujący wiersz polecenia:

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

zbiera zdarzenia AllocationTick uruchamiane mniej więcej co 100k warto alokacji. Innymi słowy zdarzenie jest wywoływane zawsze, gdy jest przydzielany dużego obiektu. Następnie zapoznanie się z jednego z widoków alokacji sterty GC, których opisano callstacks, która przydzielona dużych obiektów:
 
![Rysunek 6: Widok alokacji sterty GC](media/loh/perfview2.png)  
Rysunek 6: Widok alokacji sterty GC
 
Jak widać, jest bardzo proste test, który właśnie przydziela duże obiekty z jego `Main` metody.

### <a name="a-debugger"></a>Debuger

Jeśli masz zrzut pamięci jest i należy przyjrzeć się, jakie obiekty są faktycznie na LOH, można użyć [rozszerzenia debugera SoS](http://msdn2.microsoft.com/ms404370.aspx) dostarczonych przez .NET. 

> [!NOTE]
> Debugowania polecenia wymienione w tej sekcji mają zastosowanie do [debugery Windows](http://www.microsoft.com/whdc/devtools/debugging/default.mspx).

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

Rozmiar sterty LOH jest (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bajtów. Między 023e1000 adresy i 033db630 bajtów 8,008,736 są zajęte przez tablicę <xref:System.Object?displayProperty=fullName> obiekty bajtów 6,663,696 są zajęte przez tablicę <xref:System.Byte?displayProperty=nameWithType> obiektów i 2,081,792 bajtów są zajęte przez ilość wolnego miejsca.

Czasami debuger pokazuje, czy całkowity rozmiar LOH jest mniejsza niż 85,000 bajtów. Dzieje się tak, ponieważ wykonawcze używa LOH przydzielić niektóre obiekty, które są mniejsze niż dużego obiektu.

Ponieważ nie jest kompaktowanie LOH, czasami LOH jest thoought na źródło fragmentacji. Fragmentacja oznacza:

- Fragmentacja sterty zarządzanej, który jest wskazywany przez ilość wolnego miejsca między zarządzanych obiektów. W SoS `!dumpheap –type Free` polecenie wyświetla ilość wolnego miejsca między zarządzanych obiektów.

- Fragmentacja przestrzeni adresów pamięci wirtualnej (VM), który jest pamięć oznaczony jako `MEM_FREE`. Możesz pobrać go przy użyciu różnych poleceń debugera w windbg.

   W poniższym przykładzie przedstawiono fragmentacji przestrzeni maszyny Wirtualnej:

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

Jest więcej częściej można zobaczyć fragmentacji maszyny Wirtualnej spowodowane tymczasowego duże obiekty, które wymagają modułu zbierającego elementy bezużyteczne często uzyskać nowy zarządzanych segmentów sterty z systemu operacyjnego i wersji pustych z powrotem do systemu operacyjnego.

Aby sprawdzić, czy LOH powoduje fragmentację maszyny Wirtualnej, należy ustawić punkt przerwania na [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) i [VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) aby zobaczyć, kto połączeń telefonicznych z nimi. Na przykład aby zobaczyć, kto próbował Przydziel większy niż 8MBB fragmentów pamięci wirtualnej z systemu operacyjnego, można ustawić punkt przerwania następująco:

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

To polecenie przechodzi do debugera i pokazuje tylko wtedy, gdy stos wywołań [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) jest wywoływana z rozmiarem alokacji większa niż 8 MB (0x800000).

CLR 2.0 dodano funkcję *Hoarding maszyny Wirtualnej* które może być przydatne w przypadku scenarious gdzie segmenty (w tym na duże i małe obiektu stosów) są często nabyte i wydane. Aby określić Hoarding maszyny Wirtualnej, należy określić flagę uruchamiania o nazwie `STARTUP_HOARD_GC_VM` za pomocą obsługi interfejsu API. Zamiast zwalnianie pusty segmentów do systemu operacyjnego, środowisko CLR decommits pamięci na te segmenty i umieszcza je na liście wstrzymania. (Należy pamiętać, że środowisko CLR nie tym segmentów, które są za duże). Środowisko CLR później używa tych segmentów do spełnienia żądania nowego segmentu. Przy następnym, że Twoja aplikacja powinna nowy segment, CLR korzysta z tej listy gotowości Jeśli znajdziesz taki, który jest wystarczająco duży.

Hoarding maszyny Wirtualnej jest również przydatne w przypadku aplikacji, które mają być przechowywane na segmenty, które już nabyte, takie jak niektóre aplikacje serwera, które są dominującą aplikacje uruchomione w systemie, aby uniknąć poza wyjątkami pamięci.

Zdecydowanie zaleca się starannie przetestować aplikację podczas upewnij się, że aplikacja ma użycie pamięci stabilny za pomocą tej funkcji.
BP kernel32! virtualalloc "j (dwo (@esp+ 8) > 800000)"kb";" g ""
```

This command breaks into the debugger and shows the callstack only if [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) is called with an allocation size greater than 8MB (0x800000).

CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarious where segments (including on the large and small object heaps) are frequently acquired and released. To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API. Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list. (Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests. The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.

VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.

We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.
