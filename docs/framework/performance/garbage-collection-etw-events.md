---
title: Zdarzenia ETW odzyskiwania pamięci
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 5ff214314b92796f4a4a89ddd33a976d8b1f21d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716069"
---
# <a name="garbage-collection-etw-events"></a>Zdarzenia ETW odzyskiwania pamięci

Te zdarzenia zbierają informacje dotyczące wyrzucania elementów bezużytecznych. Ułatwiają one diagnostykę i debugowanie, w tym określanie, ile razy zostało wykonane wyrzucanie elementów bezużytecznych, ilości pamięci, która została zwolniona podczas odzyskiwania pamięci i tak dalej.

Ta kategoria obejmuje następujące zdarzenia:

- [Zdarzenie GCStart_V1](#gcstart_v1-event)
- [Zdarzenie GCEnd_V1](#gcend_v1-event)
- [Zdarzenie GCHeapStats_V1](#gcheapstats_v1-event)
- [Zdarzenie GCCreateSegment_V1](#gccreatesegment_v1-event)
- [Zdarzenie GCFreeSegment_V1](#gcfreesegment_v1-event)
- [Zdarzenie GCRestartEEBegin_V1](#gcrestarteebegin_v1-event)
- [Zdarzenie GCRestartEEEnd_V1](#gcrestarteeend_v1-event)
- [Zdarzenie GCSuspendEE_V1](#gcsuspendee_v1-event)
- [Zdarzenie GCSuspendEEEnd_V1](#gcsuspendeeend_v1-event)
- [Zdarzenie GCAllocationTick_V2](#gcallocationtick_v2-event)
- [Zdarzenie GCFinalizersBegin_V1](#gcfinalizersbegin_v1-event)
- [Zdarzenie GCFinalizersEnd_V1](#gcfinalizersend_v1-event)
- [Zdarzenie GCCreateConcurrentThread_V1](#gccreateconcurrentthread_v1-event)
- [Zdarzenie GCTerminateConcurrentThread_V1](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a>Zdarzenie GCStart_V1  

W poniższej tabeli przedstawiono słowo kluczowe i poziom. Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md).

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`GCStart_V1`|1|Rozpoczęto odzyskiwanie pamięci.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|Count|win: UInt32|*N*-ta kolekcja elementów bezużytecznych.|
|Ścisł|win: UInt32|Generacja, która jest zbierana.|
|Przyczyna|win: UInt32|Dlaczego wyzwolono wyrzucanie elementów bezużytecznych:<br /><br /> 0x0 — alokacja sterty dla małego obiektu.<br /><br /> Wywołano 0x1.<br /><br /> 0x2 — mało pamięci.<br /><br /> 0x3 — puste.<br /><br /> 0x4 — alokacja sterty dla dużego obiektu.<br /><br /> 0x5 — brak miejsca (dla sterty małego obiektu).<br /><br /> 0x6 — brak miejsca (dla sterty dużego obiektu).<br /><br /> 0x7 — wywołano, ale nie wymuszono blokowania.|
|Typ|win: UInt32|0x0 — blokowanie odzyskiwania pamięci wystąpiło poza odzyskiwaniem pamięci w tle.<br /><br /> 0x1 — wyrzucanie elementów bezużytecznych w tle.<br /><br /> 0x2 — blokowanie wyrzucania elementów bezużytecznych wystąpiło podczas odzyskiwania pamięci w tle.|
|ClrInstanceID|Win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

## <a name="gcend_v1-event"></a>Zdarzenie GCEnd_V1

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`GCEnd_V1`|2|Wyrzucanie elementów bezużytecznych zostało zakończone.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|Count|win: UInt32|*N*-ta kolekcja elementów bezużytecznych.|
|Ścisł|win: UInt32|Generacja, która została zebrana.|
|ClrInstanceID|Win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

## <a name="gcheapstats_v1-event"></a>Zdarzenie GCHeapStats_V1

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Opis|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|4|Pokazuje statystyki sterty na końcu każdego wyrzucania elementów bezużytecznych.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|GenerationSize0|win: UInt64|Rozmiar (w bajtach) pamięci generacji 0.|
|TotalPromotedSize0|win: UInt64|Liczba bajtów, które są podwyższane z generacji 0 do generacji 1.|
|GenerationSize1|win: UInt64|Rozmiar (w bajtach) pamięci pierwszej generacji 1.|
|TotalPromotedSize1|win: UInt64|Liczba bajtów, które są podwyższane z generacji 1 do generacji 2.|
|GenerationSize2|win: UInt64|Rozmiar (w bajtach) pamięci podnoszącej 2 generacji.|
|TotalPromotedSize2|win: UInt64|Liczba bajtów, które przeżyły w generacji 2 po ostatniej kolekcji.|
|GenerationSize3|win: UInt64|Rozmiar sterty dużego obiektu w bajtach.|
|TotalPromotedSize3|win: UInt64|Liczba bajtów przeczytanych z sterty dużego obiektu po ostatniej kolekcji.|
|FinalizationPromotedSize|win: UInt64|Łączny rozmiar (w bajtach) obiektów, które są gotowe do finalizacji.|
|FinalizationPromotedCount|win: UInt64|Liczba obiektów, które są gotowe do finalizacji.|
|PinnedObjectCount|win: UInt32|Liczba przypiętych (nieruchomych) obiektów.|
|SinkBlockCount|win: UInt32|Liczba bloków synchronizacji w użyciu.|
|GCHandleCount|win: UInt32|Liczba dojść do wyrzucania elementów bezużytecznych w użyciu.|
|ClrInstanceID|Win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|
  
## <a name="gccreatesegment_v1-event"></a>Zdarzenie GCCreateSegment_V1

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|5|Utworzono nowy segment wyrzucania elementów bezużytecznych. Ponadto po włączeniu śledzenia dla procesu, który jest już uruchomiony, to zdarzenie jest zgłaszane dla każdego istniejącego segmentu.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|Adres|win: UInt64|Adres segmentu.|
|Rozmiar|win: UInt64|Rozmiar segmentu.|
|Typ|win: UInt32|0x0 — sterta małego obiektu.<br /><br /> 0x1 — sterta dużego obiektu.<br /><br /> 0x2 — sterta tylko do odczytu.|
|ClrInstanceID|Win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

Należy zauważyć, że rozmiar segmentów przydzielone przez moduł wyrzucania elementów bezużytecznych jest specyficzny dla implementacji i może ulec zmianie w dowolnym momencie, łącznie z okresowymi aktualizacjami. Aplikacja nigdy nie powinna mieć założeń lub zależeć od określonego rozmiaru segmentu ani nie powinna próbować skonfigurować ilości pamięci dostępnej dla alokacji segmentu.

## <a name="gcfreesegment_v1-event"></a>Zdarzenie GCFreeSegment_V1

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|6|Wydano segment wyrzucania elementów bezużytecznych.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|Adres|win: UInt64|Adres segmentu.|
|ClrInstanceID|Win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

## <a name="gcrestarteebegin_v1-event"></a>Zdarzenie GCRestartEEBegin_V1

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|7|Rozpoczęto wznawianie od zawieszenia środowiska uruchomieniowego języka wspólnego.|

Brak danych zdarzenia.

## <a name="gcrestarteeend_v1-event"></a>Zdarzenie GCRestartEEEnd_V1

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|3|Zakończono wznawianie z zawieszenia środowiska uruchomieniowego języka wspólnego.|

Brak danych zdarzenia.

## <a name="gcsuspendee_v1-event"></a>Zdarzenie GCSuspendEE_V1

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|9|Początek zawieszenia aparatu wykonywania na potrzeby wyrzucania elementów bezużytecznych.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|Przyczyna|Win: UInt16|0x0 — inne.<br /><br /> 0x1 — odzyskiwanie pamięci.<br /><br /> 0x2 — zamknięcie domeny aplikacji.<br /><br /> 0x3 — nachylenie kodu.<br /><br /> 0x4 — zamykanie.<br /><br /> 0x5 — debuger.<br /><br /> 0x6 — przygotowanie do wyrzucania elementów bezużytecznych.|
|Count|win: UInt32|Liczba GC w danym momencie. Zwykle po wykonaniu tej operacji zobaczysz kolejne zdarzenie uruchomienia GC, a jego liczba jest taka sama jak liczba + 1, ponieważ zwiększy indeks GC podczas wyrzucania elementów bezużytecznych.|
|ClrInstanceID|Win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

## <a name="gcsuspendeeend_v1-event"></a>Zdarzenie GCSuspendEEEnd_V1

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|8|Koniec zawieszenia aparatu wykonywania na potrzeby wyrzucania elementów bezużytecznych.|

Brak danych zdarzenia.

## <a name="gcallocationtick_v2-event"></a>Zdarzenie GCAllocationTick_V2

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|10|Za każdym razem przydzielono około 100 KB.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|AllocationAmount|win: UInt32|Rozmiar alokacji w bajtach. Ta wartość jest dokładna dla przydziałów, które są mniejsze niż długość ULONG (4 294 967 295 bajtów). Jeśli alokacja jest większa, to pole zawiera obciętą wartość. Użyj `AllocationAmount64` dla bardzo dużych alokacji.|
|AllocationKind|win: UInt32|0x0 — alokacja małego obiektu (alokacja jest w ramach sterty małego obiektu).<br /><br /> 0x1 — alokacja dużego obiektu (alokacja jest w sterty dużego obiektu).|
|ClrInstanceID|Win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|
|AllocationAmount64|win: UInt64|Rozmiar alokacji w bajtach. Ta wartość jest dokładna dla bardzo dużych alokacji.|
|IdentyfikatorTypu|win: wskaźnik|Adres metody. Jeśli istnieje kilka typów obiektów, które zostały przydzieloną w trakcie tego zdarzenia, jest to adres metody, która odnosi się do ostatniego przydzielony obiekt (obiekt, który spowodował przekroczenie 100 KB progu).|
|TypeName|win: UnicodeString|Nazwa przydzieloną typ. Jeśli istnieje kilka typów obiektów, które zostały przydzieloną w trakcie tego zdarzenia, jest to typ ostatniego przydzielono obiektu (obiektu, który spowodował przekroczenie 100 KB).|
|HeapIndex|win: UInt32|Sterta, do której został przydzielony obiekt. Ta wartość jest równa 0 (zero) podczas uruchamiania z odzyskiwaniem pamięci stacji roboczej.|

## <a name="gcfinalizersbegin_v1-event"></a>Zdarzenie GCFinalizersBegin_V1

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|14|Początek uruchamiania finalizatorów.|

Brak danych zdarzenia.

## <a name="gcfinalizersend_v1-event"></a>Zdarzenie GCFinalizersEnd_V1

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|13|Koniec uruchomionych finalizatorów.|

W poniższej tabeli przedstawiono dane zdarzenia:

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|Count|win: UInt32|Liczba uruchomionych finalizatorów.|
|ClrInstanceID|Win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

## <a name="gccreateconcurrentthread_v1-event"></a>Zdarzenie GCCreateConcurrentThread_V1

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informacyjny (4)|
|`ThreadingKeyword` (0x10000)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|11|Utworzono wątek współbieżnego wyrzucania elementów bezużytecznych.|

Brak danych zdarzenia.

## <a name="gcterminateconcurrentthread_v1-event"></a>Zdarzenie GCTerminateConcurrentThread_V1

W poniższej tabeli przedstawiono słowo kluczowe i poziom:

|Słowo kluczowe do podniesienia zdarzenia|Poziom|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informacyjny (4)|
|`ThreadingKeyword` (0x10000)|Informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu:

|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|12|Wątek współbieżnego wyrzucania elementów bezużytecznych został zakończony.|

Brak danych zdarzenia.

## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](clr-etw-events.md)
