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
ms.openlocfilehash: 13f7e935ab999ccc3cd3ea1e308e8d686bed4171
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="garbage-collection-etw-events"></a>Zdarzenia ETW odzyskiwania pamięci
<a name="top"></a> Te zdarzenia zbierać informacje dotyczące wyrzucania elementów bezużytecznych. Pomagają w diagnostyce i debugowanie, określając, ile razy wyrzucanie elementów bezużytecznych została wykonana, ile pamięci został zwolniony podczas wyrzucanie elementów bezużytecznych i tak dalej.  
  
 Ta kategoria obejmuje następujące zdarzenia:  
  
-   [Zdarzenie GCStart_V1](#gcstart_v1_event)  
  
-   [Zdarzenie GCEnd_V1](#gcend_v1_event)  
  
-   [Zdarzenie GCHeapStats_V1](#gcheapstats_v1_event)  
  
-   [Zdarzenie GCCreateSegment_V1](#gccreatesegment_v1_event)  
  
-   [Zdarzenie GCFreeSegment_V1](#gcfreesegment_v1_event)  
  
-   [Zdarzenie GCRestartEEBegin_V1](#gcrestarteebegin_v1_event)  
  
-   [Zdarzenie GCRestartEEEnd_V1](#gcrestarteeend_v1_event)  
  
-   [Zdarzenie GCSuspendEE_V1](#gcsuspendee_v1_event)  
  
-   [Zdarzenie GCSuspendEEEnd_V1](#gcsuspendeeend_v1_event)  
  
-   [Zdarzenie GCAllocationTick_V2](#gcallocationtick_v2_event)  
  
-   [Zdarzenie GCFinalizersBegin_V1](#gcfinalizersbegin_v1_event)  
  
-   [Zdarzenie GCFinalizersEnd_V1](#gcfinalizersend_v1_event)  
  
-   [Zdarzenie GCCreateConcurrentThread_V1](#gccreateconcurrentthread_v1_event)  
  
-   [Zdarzenie GCTerminateConcurrentThread_V1](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a>Zdarzenie GCStart_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|1|Wyrzucanie elementów bezużytecznych została uruchomiona.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Liczba|Windows: UInt32.|*n*th wyrzucanie elementów bezużytecznych.|  
|Głębokość|Windows: UInt32.|Generowanie zbieranych.|  
|Przyczyna|Windows: UInt32.|Dlaczego zostało wyzwolone odzyskiwanie pamięci:<br /><br /> 0x0 - Alokacja sterty dla małego obiektu.<br /><br /> 0x1 — powstaniu.<br /><br /> 0x2 — Brak pamięci.<br /><br /> 0x3 — pusty.<br /><br /> 0x4 - Alokacja sterty dla dużego obiektu.<br /><br /> 0x5 — Brak miejsca (dla sterty małego obiektu).<br /><br /> 0x6 — Brak miejsca (dla sterty dużego obiektu).<br /><br /> 0x7 - powstaniu, ale nie wymuszono jako blokowania.|  
|Typ|Windows: UInt32.|0x0 — blokowanie pamięci wystąpiło poza odzyskiwanie pamięci w tle.<br /><br /> 0x1 — odzyskiwanie pamięci w tle.<br /><br /> 0x2 — blokowanie wyrzucanie elementów bezużytecznych podczas odzyskiwanie pamięci w tle.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a>Zdarzenie GCEnd_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|2|Wyrzucanie elementów bezużytecznych została zakończona.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Liczba|Windows: UInt32.|*n*th wyrzucanie elementów bezużytecznych.|  
|Głębokość|Windows: UInt32.|Generowanie, który został zebrany.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a>Zdarzenie GCHeapStats_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|4|Wyświetla statystyki sterty na końcu każdej operacji wyrzucania elementów bezużytecznych.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|GenerationSize0|Windows: UInt64|Rozmiar w bajtach pamięć generacji 0.|  
|TotalPromotedSize0|Windows: UInt64|Liczba bajtów, które zostały awansowane z pokolenia 0 na pokolenie 1.|  
|GenerationSize1|Windows: UInt64|Rozmiar w bajtach pamięci generacji 1.|  
|TotalPromotedSize1|Windows: UInt64|Liczba bajtów, które zostały awansowane z pokolenia 1 na pokolenie 2.|  
|GenerationSize2|Windows: UInt64|Rozmiar w bajtach pamięci generacji 2.|  
|TotalPromotedSize2|Windows: UInt64|Liczba bajtów, które udało przetrwać podczas generowania 2 od ostatniego zebrania.|  
|GenerationSize3|Windows: UInt64|Rozmiar w bajtach sterty dużego obiektu.|  
|TotalPromotedSize3|Windows: UInt64|Liczba bajtów, które udało przetrwać w sterty dużego obiektu, od ostatniego zebrania.|  
|FinalizationPromotedSize|Windows: UInt64|Całkowity rozmiar w bajtach obiektów, które są gotowe do finalizacji.|  
|FinalizationPromotedCount|Windows: UInt64|Liczba obiektów, które są gotowe do finalizacji.|  
|PinnedObjectCount|Windows: UInt32.|Liczbę unieruchomionych obiektów (nieprzenośne).|  
|SinkBlockCount|Windows: UInt32.|Liczba bloków synchronizacji w użyciu.|  
|GCHandleCount|Windows: UInt32.|Obsługuje liczbę operacji wyrzucania elementów bezużytecznych w użyciu.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a>Zdarzenie GCCreateSegment_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|5|Utworzono nowy segment kolekcji pamięci. Ponadto gdy śledzenie jest włączone dla procesu, który jest już uruchomiona, to zdarzenie jest wywoływane dla każdego istniejącego segmentu.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Adres|Windows: UInt64|Adres segmentu.|  
|Rozmiar|Windows: UInt64|Rozmiar segmentu.|  
|Typ|Windows: UInt32.|0x0 - sterty małego obiektu.<br /><br /> 0x1 — sterty dużego obiektu.<br /><br /> 0x2 — sterty tylko do odczytu.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 Należy zauważyć, że rozmiar segmentów przydzielone przez moduł garbage collector konkretnej implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowych aktualizacji. Aplikacji nigdy nie może dokonać założeń dotyczących lub zależą od rozmiaru określonego segmentu nie powinny podejmować próby skonfiguruj ilość pamięci dostępnej dla segmentu alokacji.  
  
 [Powrót do początku](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a>Zdarzenie GCFreeSegment_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|6|Segment kolekcji odzyskiwanie zostało zwolnione.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Adres|Windows: UInt64|Adres segmentu.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a>Zdarzenie GCRestartEEBegin_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|7|Wznowienie z wspólnego języka środowiska uruchomieniowego zawieszenia zostało uruchomione.|  
  
 Brak danych zdarzenia.  
  
 [Powrót do początku](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a>Zdarzenie GCRestartEEEnd_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|3|Wznowienie z wspólnego języka środowiska uruchomieniowego zawieszenia została zakończona.|  
  
 Brak danych zdarzenia.  
  
 [Powrót do początku](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a>Zdarzenie GCSuspendEE_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|9|Początek zawieszenia aparat wykonywania dla wyrzucanie elementów bezużytecznych.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Przyczyna|Windows: UInt16|0x0 - innych.<br /><br /> 0x1 — wyrzucanie elementów bezużytecznych.<br /><br /> 0x2 — zamknięcia domeny aplikacji.<br /><br /> 0x3 - pitching kodu.<br /><br /> 0x4 - shutdown.<br /><br /> 0x5 - debugera.<br /><br /> 0x6 — przygotowanie do wyrzucanie elementów bezużytecznych.|  
|Liczba|Windows: UInt32.|Liczba GC, w tym czasie. Zwykle zobaczysz kolejnych zdarzeń GC Start po to, a licznika wyjątkowo licznik ten uwzględnia + 1, ponieważ indeks GC możemy zwiększyć podczas wyrzucania elementów bezużytecznych.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a>Zdarzenie GCSuspendEEEnd_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu:  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia:  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|8|Koniec zawieszenia aparat wykonywania dla wyrzucanie elementów bezużytecznych.|  
  
 Brak danych zdarzenia.  
  
 [Powrót do początku](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a>Zdarzenie GCAllocationTick_V2  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|10|Zawsze przydzielone około 100 KB.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AllocationAmount|Windows: UInt32.|Rozmiar alokacji w bajtach. Ta wartość jest dokładna dla alokacji, który jest mniejsza niż długość ULONG (4 294 967 295 w bajtach). Jeśli przydział jest większa, to pole zawiera obciętą wartość. Użyj `AllocationAmount64` dla bardzo dużych alokacji.|  
|AllocationKind|Windows: UInt32.|0x0 - małego obiektu alokacji (alokacji jest sterty małego obiektu).<br /><br /> 0x1 — alokacji dużego obiektu (alokacji jest sterty dużego obiektu).|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
|AllocationAmount64|Windows: UInt64|Rozmiar alokacji w bajtach. Ta wartość jest dokładne w przypadku bardzo dużych alokacji.|  
|TypeId|Windows: wskaźnik|Adres MethodTable. Jeśli istnieje kilka typów obiektów, które zostały przydzielone podczas tego zdarzenia, jest to adres MethodTable, odpowiadający ostatni obiekt przydzielony (obiekt, który spowodował może przekroczyć próg 100 KB).|  
|TypeName|Windows: UnicodeString|Nazwa typu, który został przydzielony. Jeśli istnieje kilka typów obiektów, które zostały przydzielone podczas tego zdarzenia, jest to typ ostatni obiekt przydzielony (obiekt, który spowodował może przekroczyć próg 100 KB).|  
|HeapIndex|Windows: UInt32.|Stosu, w którym obiekt został przydzielony. Ta wartość jest 0 (zero), gdy uruchomiona stacji roboczej wyrzucanie elementów bezużytecznych.|  
  
 [Powrót do początku](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a>Zdarzenie GCFinalizersBegin_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|14|Początek systemem finalizatory.|  
  
 Brak danych zdarzenia.  
  
 [Powrót do początku](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a>Zdarzenie GCFinalizersEnd_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|13|Koniec systemem finalizatory.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Liczba|Windows: UInt32.|Liczba finalizatory, które zostały uruchomione.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a>Zdarzenie GCCreateConcurrentThread_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
|`ThreadingKeyword` (0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|11|Współbieżne odzyskiwanie kolekcji wątek został utworzony.|  
  
 Brak danych zdarzenia.  
  
 [Powrót do początku](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a>Zdarzenie GCTerminateConcurrentThread_V1  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Komunikat informacyjny (4)|  
|`ThreadingKeyword` (0x10000)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|12|Współbieżne odzyskiwanie kolekcji wątek został przerwany.|  
  
 Brak danych zdarzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
