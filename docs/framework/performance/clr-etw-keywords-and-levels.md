---
title: Słowa kluczowe i poziomy ETW CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW keywords
- CLR ETW levels
- ETW, CLR keywords
- ETW, CLR levels
ms.assetid: fdf5856d-516b-4042-849d-911c4518a6cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9a9061503ae4bf68903f35eb7624deed2f34c9b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616611"
---
# <a name="clr-etw-keywords-and-levels"></a>Słowa kluczowe i poziomy ETW CLR
<a name="top"></a> Śledzenie zdarzeń systemu Windows (ETW) zdarzenia mogą być filtrowane według kategorii i poziomu. Zdarzenie [słowa kluczowe CLR ETW](#keywords) Włącz filtrowanie zdarzeń według kategorii; są one używane w kombinacji dla dostawców środowiska uruchomieniowego i podsumowania. [Poziomów zdarzeń](#levels) są identyfikowane za pomocą flagi.  
  
<a name="keywords"></a>   
## <a name="clr-etw-keywords"></a>Słowa kluczowe CLR ETW  
 Słowa kluczowe są flagi, które mogą być połączone do generowania wartości. W praktyce użyjesz wartości szesnastkowych słów kluczowych zamiast nazw — słowo kluczowe podczas wywoływania narzędzia wiersza polecenia.  
  
 Słowa kluczowe są opisane w poniższych tabelach:  
  
- [Słowa kluczowe CLR ETW środowiska uruchomieniowego](#runtime)  
  
- [Słowa kluczowe podsumowań CLR ETW](#rundown)  
  
- [Kombinacje — słowo kluczowe dla rozpoznawania symboli dla dostawcy środowiska uruchomieniowego](#runtime_combo)  
  
- [Kombinacje — słowo kluczowe dla rozpoznawania symboli dla dostawcy podsumowań](#rundown_combo)  
  
<a name="runtime"></a>   
### <a name="clr-etw-runtime-keywords"></a>Słowa kluczowe CLR ETW środowiska uruchomieniowego  
 W poniższej tabeli wymieniono słowa kluczowe środowiska uruchomieniowego CLR ETW, ich wartości i ich zastosowania.  
  
|Nazwa — słowo kluczowe środowiska uruchomieniowego|Wartość|Cel|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|Umożliwia to kolekcji [zdarzenia odzyskiwania pamięci](../../../docs/framework/performance/garbage-collection-etw-events.md).|  
|`LoaderKeyword`|0x00000008|Umożliwia to kolekcji [zdarzenia modułu ładującego](../../../docs/framework/performance/loader-etw-events.md).|  
|`JITKeyword`|0x00000010|Umożliwia to kolekcji [zdarzenia just-in-time (JIT)](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`NGenKeyword`|0x00000020|Umożliwia to kolekcji zdarzeń dla obrazu natywnego metod (metod przetwarzane przez Generator obrazu natywnego Ngen.exe); używane z `StartEnumerationKeyword` i `EndEnumerationKeyword`. This — słowo kluczowe ma wysokie obciążenie. Generuje zdarzenia dla każdej metody w każdym załadowanym module NGen. Zawsze, gdy jest to możliwe, zamiast tego słowa kluczowego, zaleca się używać baz danych programu (PDB) generowanych przez narzędzia profilowania można pobrać informacji o metodach z modułów NGen. Zobacz też `OverrideAndSuppressNGenEventsKeyword` dalej w tej tabeli.|  
|`StartEnumerationKeyword`|0x00000040|Włącza wyliczanie wszystkie metody w środowisku wykonawczym; używany w połączeniu z `NGenKeyword`.|  
|`EndEnumerationKeyword`|0x00000080|Włącza wyliczanie wszystkich metod, które są niszczone w środowisku wykonawczym; używany w połączeniu z `JITKeyword` i `NGenKeyword`.|  
|`SecurityKeyword`|0x00000400|Umożliwia to kolekcji [zdarzeń związanych z zabezpieczeniami](../../../docs/framework/performance/security-etw-events.md).|  
|`AppDomainResourceManagementKeyword`|0x00000800|Umożliwia to kolekcji zdarzeń na poziomie domeny aplikacji do monitorowania zasobów.|  
|`JITTracingKeyword`|0x00001000|Umożliwia to kolekcji [zdarzenia śledzenia JIT](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`InteropKeyword`|0x00002000|Umożliwia to kolekcji [zdarzenia międzyoperacyjności](../../../docs/framework/performance/interop-etw-events.md).|  
|`ContentionKeyword`|0x00004000|Umożliwia to kolekcji [zdarzenia rywalizacji](../../../docs/framework/performance/contention-etw-events.md).|  
|`ExceptionKeyword`|0x00008000|Umożliwia to kolekcji [zdarzeń wyjątków](../../../docs/framework/performance/exception-thrown-v1-etw-event.md).|  
|`ThreadingKeyword`|0x00010000|Umożliwia to kolekcji [zdarzenia puli wątków](../../../docs/framework/performance/thread-pool-etw-events.md).|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(Dostępne w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i nowszych.) Pomija obciążenie o wysokiej `NGenKeyword` — słowo kluczowe i uniemożliwia generowanie zdarzeń dla metod, które znajdują się w modułach programu NGen. Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], skorzystaj z narzędzia profilowania `OverrideAndSuppressNGenEventsKeyword` i `NGenKeyword` ze sobą, aby pominąć generowanie zdarzeń dla metod w modułach programu NGen. Dzięki temu narzędzie profilowania, aby użyć bardziej wydajne plików PDB NGen, aby uzyskać informacje o metodach w modułach programu NGen. Środowisko CLR w .NET Framework 4 i starszych wersji nie obsługuje tworzenia baz danych programu NGen. We wcześniejszych wersjach środowiska CLR nie rozpoznaje `OverrideAndSuppressNGenEventsKeyword` i będzie przetwarzać `NGenKeyword` do generowania zdarzeń dla metod w modułach programu NGen.|  
|`PerfTrackKeyWord`|0x2000000|Umożliwia to kolekcji `ModuleLoad` i `ModuleRange` zdarzenia.|  
|`StackKeyword`|0x40000000|Umożliwia to kolekcji CLR [zdarzeń śledzenia stosu](../../../docs/framework/performance/stack-etw-event.md).|  
  
 [Powrót do początku](#top)  
  
<a name="rundown"></a>   
### <a name="clr-etw-rundown-keywords"></a>Słowa kluczowe podsumowań CLR ETW  
 W poniższej tabeli wymieniono podsumowań słowa kluczowe CLR ETW, ich wartości i ich zastosowania.  
  
|Nazwa podsumowań — słowo kluczowe|Wartość|Cel|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Umożliwia zbieranie zdarzeń modułu ładującego, gdy jest używane z `StartRundownKeyword` i `EndRundownKeyword`.|  
|`JitRundownKeyword`|0x00000010|Umożliwia to kolekcji metoda `DCStart` i `DCEnd` zdarzenia dla metod kompilowanego dokładnie na czas, gdy jest używane z `StartRundownKeyword` i `EndRundownKeyword`.|  
|`NGenRundownKeyword`|0x00000020|Umożliwia to kolekcji metoda `DCStart` i `DCEnd` zdarzenia dla metod obrazu natywnego NGen, gdy jest używane z `StartRundownKeyword` i `EndRundownKeyword`. This — słowo kluczowe ma wysokie obciążenie. Generuje zdarzenia dla każdej metody w każdym załadowanym module NGen. Zawsze, gdy jest to możliwe, zamiast tego słowa kluczowego, zaleca się używać baz danych programu (PDB) generowanych przez narzędzia profilowania można pobrać informacji o metodach z modułów NGen. Zobacz też `OverrideAndSuppressNGenEventsRundownKeyword` dalej w tej tabeli.|  
|`StartRundownKeyword`|0x00000040|Włącza wyliczanie stanu systemu podczas Początek podsumowania.|  
|`EndRundownKeyword`|0x00000100|Włącza wyliczanie stanu systemu podczas koniec podsumowania.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Umożliwia to kolekcji zdarzeń w celu monitorowania zasobów na poziomie <xref:System.AppDomain> poziomu, gdy jest używane z `StartRundownKeyword` lub `EndRundownKeyword`.|  
|`ThreadingKeyword`|0x00010000|Umożliwia to kolekcji zdarzeń puli wątków.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(Dostępne w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i nowszych.) Pomija obciążenie o wysokiej `NGenRundownKeyword` — słowo kluczowe i uniemożliwia generowanie zdarzeń dla metod, które znajdują się w modułach programu NGen. Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], skorzystaj z narzędzia profilowania `OverrideAndSuppressNGenEventsRundownKeyword` i `NGenRundownKeyword` ze sobą, aby pominąć generowanie zdarzeń dla metod w modułach programu NGen. Dzięki temu narzędzie profilowania, aby użyć bardziej wydajne plików PDB NGen, aby uzyskać informacje o metodach w modułach programu NGen. Środowisko CLR w .NET Framework 4 i starszych wersji nie obsługuje tworzenia baz danych programu NGen. We wcześniejszych wersjach środowiska CLR nie rozpoznaje `OverrideAndSuppressNGenEventsRundownKeyword` i będzie przetwarzać `NGenRundownKeyword` do generowania zdarzeń dla metod w modułach programu NGen.|  
|`PerfTrackKeyWord`|0x2000000|Umożliwia to kolekcji `ModuleDCStart`, `ModuleDCEnd`, `ModuleRangeDCStart`, i `ModuleRangeDCEnd` zdarzenia.|  
  
 [Powrót do początku](#top)  
  
<a name="runtime_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Kombinacje — słowo kluczowe dla rozpoznawania symboli dla dostawcy środowiska uruchomieniowego  
  
|Słowa kluczowe i flagi|Domeny aplikacji, zestaw, zdarzenia ładowanie/zwalnianie modułu|Metoda ładowanie/zwalnianie zdarzenia (z wyjątkiem zdarzeń dynamiczny)|Metoda dynamiczna obciążenia/zniszczenia zdarzenia|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Ładowanie i zwalnianie zdarzenia.|Brak.|Brak.|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` nic nie dodawać)|Brak.|Załaduj zdarzenia.|Ładowanie i zwalnianie zdarzenia.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|Brak.|Ładowanie i zwalnianie zdarzenia.|Ładowanie i zwalnianie zdarzenia.|  
|`NGenKeyword`|Brak.|Brak.|Nie dotyczy.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|Brak.|Załaduj zdarzenia.|Nie dotyczy.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|Brak.|Zwolnij zdarzenia.|Nie dotyczy.|  
  
 [Powrót do początku](#top)  
  
<a name="rundown_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Kombinacje — słowo kluczowe dla rozpoznawania symboli dla dostawcy podsumowań  
  
|Słowa kluczowe i flagi|Domeny aplikacji, zestaw, zdarzenia DCStart/DCEnd modułu|Metoda DCStart/DCEnd zdarzenia (w tym zdarzenia metodę dynamiczną)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|`DCStart` zdarzenia.|Brak.|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|`DCEnd` zdarzenia.|Brak.|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|Brak.|`DCStart` zdarzenia.|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|Brak.|`DCEnd` zdarzenia.|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|Brak.|`DCStart` zdarzenia.|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|Brak.|`DCEnd` zdarzenia.|  
  
 [Powrót do początku](#top)  
  
<a name="levels"></a>   
## <a name="etw-event-levels"></a>Poziomy zdarzenia ETW.  
 Zdarzenia ETW. można również filtrować według poziomu. Jeśli poziom równego 0x5, zdarzenia, wszystkie poziomy, w tym 0x5 a poniżej (które są zdarzenia, które należą do kategorii, włączana za pomocą słów kluczowych) są wywoływane. Jeśli poziom równego 0x2, są wywoływane tylko zdarzenia, które należą do poziomu 0x2 i poniżej.  
  
 Poziomy mają następujące znaczenie:  
  
 0x5 - verbose  
  
 0x4 - informacyjne  
  
 0x3 — ostrzeżenie  
  
 0x2 — błąd  
  
 0x1 — krytyczne  
  
 0x0 — LogAlways  
  
## <a name="see-also"></a>Zobacz także

- [Dostawcy CLR ETW](../../../docs/framework/performance/clr-etw-providers.md)
- [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
- [Zdarzenia ETW w środowisku CLR](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
