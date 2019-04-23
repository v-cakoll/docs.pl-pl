---
title: Zdarzenia ETW odzyskiwania pamięci
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f9bf0e309ec8c77d4b1d6afbf111e7eeae629ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149737"
---
# <a name="garbage-collection-etw-events"></a>Zdarzenia ETW odzyskiwania pamięci
<a name="top"></a> Te zdarzenia zbierać informacje dotyczące wyrzucania elementów bezużytecznych. Pomagają w diagnostyce i debugowania, w tym określanie, ile razy wyrzucania elementów bezużytecznych zostało wykonane, ile pamięci została zwolniona podczas wyrzucania elementów bezużytecznych i tak dalej.  
  
 Ta kategoria obejmuje następujące zdarzenia:  
  
-   [Zdarzenie GCStart_V1](#gcstart_v1_event)  
  
-   [Zdarzenie GCEnd_V1](#gcend_v1_event)  
  
-   [GCHeapStats_V1 Event](#gcheapstats_v1_event)  
  
-   [Zdarzenie GCCreateSegment_V1](#gccreatesegment_v1_event)  
  
-   [Zdarzenie GCFreeSegment_V1](#gcfreesegment_v1_event)  
  
-   [Zdarzenie GCRestartEEBegin_V1](#gcrestarteebegin_v1_event)  
  
-   [Zdarzenie GCRestartEEEnd_V1](#gcrestarteeend_v1_event)  
  
-   [Zdarzenie GCSuspendEE_V1](#gcsuspendee_v1_event)  
  
-   [Zdarzenie GCSuspendEEEnd_V1](#gcsuspendeeend_v1_event)  
  
-   [Zdarzenie GCAllocationTick_V2](#gcallocationtick_v2_event)  
  
-   [Zdarzenie GCFinalizersBegin_V1](#gcfinalizersbegin_v1_event)  
  
-   [GCFinalizersEnd_V1 Event](#gcfinalizersend_v1_event)  
  
-   [GCCreateConcurrentThread_V1 Event](#gccreateconcurrentthread_v1_event)  
  
-   [Zdarzenie GCTerminateConcurrentThread_V1](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a>Zdarzenie GCStart_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|1|Wyrzucanie elementów bezużytecznych zostało uruchomione.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Licznik|win: UInt32.|*n*th wyrzucania elementów bezużytecznych.|  
|Głębokość|win: UInt32.|Generowanie, które są zbierane.|  
|Przyczyna|win: UInt32.|Dlaczego wyrzucania elementów bezużytecznych zostało wyzwolone:<br /><br /> 0x0 - Alokacja sterty dla małego obiektu.<br /><br /> 0x1 — wywołane.<br /><br /> 0x2 — małej ilości pamięci.<br /><br /> 0x3 — pusta.<br /><br /> 0x4 - Alokacja sterty dla dużego obiektu.<br /><br /> 0x5 — Brak miejsca (dla sterty małego obiektu).<br /><br /> 0x6 — Brak miejsca (dla sterty dużego obiektu).<br /><br /> 0x7 — wywołane, ale nie wymuszono jako blokowania.|  
|Typ|win: UInt32.|0x0 — blokowanie wyrzucania elementów bezużytecznych wystąpiło poza wyrzucania elementów bezużytecznych w tle.<br /><br /> 0x1 — wyrzucania elementów bezużytecznych w tle.<br /><br /> 0x2 — blokowanie wyrzucania elementów bezużytecznych wystąpił podczas wyrzucania elementów bezużytecznych w tle.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a>Zdarzenie GCEnd_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|2|Wyrzucanie elementów bezużytecznych zostało zakończone.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Licznik|win: UInt32.|*n*th wyrzucania elementów bezużytecznych.|  
|Głębokość|win: UInt32.|Generowanie, które zostały zebrane.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a>Zdarzenie GCHeapStats_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|4|Pokazuje statystykę sterty na końcu każdej operacji wyrzucania elementów bezużytecznych.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|GenerationSize0|win:UInt64|Rozmiar w bajtach pamięć generacji 0.|  
|TotalPromotedSize0|win:UInt64|Liczba bajtów, które są przenoszone z generacji 0 do 1. generacji.|  
|GenerationSize1|win:UInt64|Rozmiar w bajtach pamięci generacji 1.|  
|TotalPromotedSize1|win:UInt64|Liczba bajtów, które są przenoszone z generacji 1 do 2. generacji.|  
|GenerationSize2|win:UInt64|Rozmiar w bajtach pamięci generacji 2.|  
|TotalPromotedSize2|win:UInt64|Liczba bajtów, które przetrwały w generacji 2 od ostatniego zebrania.|  
|GenerationSize3|win:UInt64|Rozmiar w bajtach stosu dużych obiektów.|  
|TotalPromotedSize3|win:UInt64|Liczba bajtów, które przetrwały w stosie dużego obiektu, od ostatniego zebrania.|  
|FinalizationPromotedSize|win:UInt64|Całkowity rozmiar w bajtach, obiekty, które są gotowe do finalizacji.|  
|FinalizationPromotedCount|win:UInt64|Liczba obiektów, które są gotowe do finalizacji.|  
|PinnedObjectCount|win: UInt32.|Liczba przypiętych obiektów (nieprzenośne).|  
|SinkBlockCount|win: UInt32.|Liczba bloków synchronizacji w użyciu.|  
|GCHandleCount|win: UInt32.|Obsługuje liczbę operacji wyrzucania elementów bezużytecznych w użyciu.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a>Zdarzenie GCCreateSegment_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|5|Utworzono nowy segment kolekcji wyrzucania elementów. Ponadto gdy śledzenie jest włączone na temat procesu, który jest już uruchomiony, to zdarzenie jest wywoływane dla każdego istniejącego segmentu.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Adres|win:UInt64|Adres segmentu.|  
|Rozmiar|win:UInt64|Rozmiar segmentu.|  
|Typ|win: UInt32.|0x0 — sterty małego obiektu.<br /><br /> 0x1 — stertę dużego obiektu.<br /><br /> 0x2 — tylko do odczytu sterty.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 Należy pamiętać, że rozmiar segmentów przydzielonej przez moduł odśmiecania pamięci jest specyficzne dla implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowe aktualizacje. Twoja aplikacja nigdy nie należy wprowadzić założeń dotyczących lub zależeć od rozmiaru określonego segmentu nie ma podejmować skonfigurować ilość pamięci dostępnej dla alokacji segmentu.  
  
 [Powrót do początku](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a>GCFreeSegment_V1 Event  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|6|Segment kolekcji wyrzucania elementów został wydany.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Adres|win:UInt64|Adres segmentu.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a>Zdarzenie GCRestartEEBegin_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|7|Wznowienie z wspólnego języka środowiska uruchomieniowego zawieszenia została rozpoczęta.|  
  
 Brak danych zdarzenia.  
  
 [Powrót do początku](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a>Zdarzenie GCRestartEEEnd_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|3|Wznowienie z wspólnego języka środowiska uruchomieniowego zawieszenia została zakończona.|  
  
 Brak danych zdarzenia.  
  
 [Powrót do początku](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a>Zdarzenie GCSuspendEE_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|9|Początek zawieszenia aparatu wykonywania do wyrzucania elementów bezużytecznych.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Przyczyna|win: UInt16.|0x0 — inne.<br /><br /> 0x1 — wyrzucania elementów bezużytecznych.<br /><br /> 0x2 — zamykania domeny aplikacji.<br /><br /> 0x3 - pitching kodu.<br /><br /> 0x4 - shutdown.<br /><br /> 0x5 - debugera.<br /><br /> 0x6 — przygotowanie do wyrzucania elementów bezużytecznych.|  
|Licznik|win: UInt32.|Liczba operacji odzyskiwania pamięci w czasie. Zwykle po to zobaczysz kolejnych zdarzeń początek odzyskiwania pamięci, a licznik będzie wskazywać ta liczba + 1, jak możemy zwiększyć indeksu GC podczas wyrzucania elementów bezużytecznych.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a>Zdarzenie GCSuspendEEEnd_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom:  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu:  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|8|Koniec zawieszenia aparatu wykonywania do wyrzucania elementów bezużytecznych.|  
  
 Brak danych zdarzenia.  
  
 [Powrót do początku](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a>Zdarzenie GCAllocationTick_V2  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|10|Każdorazowo przydzielany około 100 KB.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AllocationAmount|win: UInt32.|Rozmiar alokacji w bajtach. Ta wartość jest prawidłowe dla alokacji, który jest mniejsza niż długość ULONG (4 294 967 295 w bajtach). Jeśli alokacja jest większa, to pole zawiera obciętą wartość. Użyj `AllocationAmount64` dla bardzo dużych alokacji.|  
|AllocationKind|win: UInt32.|0x0 - małych obiektów alokacji (alokacji jest sterty małego obiektu).<br /><br /> 0x1 — alokacji dużego obiektu (alokacji znajduje się w stosie dużego obiektu).|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
|AllocationAmount64|win:UInt64|Rozmiar alokacji w bajtach. Ta wartość jest dokładne w przypadku bardzo dużych alokacji.|  
|TypeId|win: wskaźnik|Adres MethodTable. W przypadku kilku typów obiektów, które zostały przydzielone podczas tego zdarzenia jest to adres MethodTable, który odpowiada ostatni obiekt przydzielony (obiekt, który spowodował zostać przekroczony próg 100 KB).|  
|TypeName|win:UnicodeString|Nazwa typu, która została przydzielona. W przypadku kilku typów obiektów, które zostały przydzielone podczas tego zdarzenia jest typ ostatni obiekt przydzielony (obiekt, który spowodował zostać przekroczony próg 100 KB).|  
|HeapIndex|win: UInt32.|Sterty, w którym został przydzielony obiekt. Ta wartość jest 0 (zero), podczas korzystania z użyciem wyrzucanie elementów bezużytecznych.|  
  
 [Powrót do początku](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a>Zdarzenie GCFinalizersBegin_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|14|Początek uruchamianie finalizatorów.|  
  
 Brak danych zdarzenia.  
  
 [Powrót do początku](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a>Zdarzenie GCFinalizersEnd_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|13|Koniec uruchamianie finalizatorów.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Licznik|win: UInt32.|Liczba finalizatorów, które zostały uruchomione.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a>Zdarzenie GCCreateConcurrentThread_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
|`ThreadingKeyword` (0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|11|Utworzono wątku kolekcji wyrzucania.|  
  
 Brak danych zdarzenia.  
  
 [Powrót do początku](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a>Zdarzenie GCTerminateConcurrentThread_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
|`ThreadingKeyword` (0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|12|Wątku równoczesne wyrzucania elementów bezużytecznych zostało zakończone.|  
  
 Brak danych zdarzenia.  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
