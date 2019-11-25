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
ms.openlocfilehash: 56ecdc41c5b5a3f7ee272768d5c2a3745da26633
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975516"
---
# <a name="clr-etw-keywords-and-levels"></a>Słowa kluczowe i poziomy ETW CLR
Zdarzenia śledzenia zdarzeń systemu Windows (ETW) mogą być filtrowane według kategorii i poziomu. Zdarzenia dotyczące [słów kluczowych funkcji ETW środowiska CLR](#clr-etw-keywords) umożliwiają filtrowanie zdarzeń według kategorii; są one używane w kombinacjach dla dostawców środowiska uruchomieniowego i uwalniania. [Poziomy zdarzeń](#etw-event-levels) są identyfikowane przez flagi.  
  
## <a name="clr-etw-keywords"></a>Słowa kluczowe ETW CLR  
 Słowa kluczowe są flagami, które można połączyć w celu wygenerowania wartości. W przypadku użycia wartości szesnastkowych słów kluczowych zamiast nazw słów kluczowych podczas wywoływania narzędzi wiersza polecenia.  
  
 Słowa kluczowe są opisane w następujących tabelach:  
  
- [Słowa kluczowe środowiska uruchomieniowego CLR ETW](#runtime)  
  
- [Słowa kluczowe uwalniania CLR](#rundown)  
  
- [Kombinacje słów kluczowych dla rozpoznawania symboli dla dostawcy środowiska uruchomieniowego](#runtime_combo)  
  
- [Kombinacje słów kluczowych dla rozpoznawania symboli dla dostawcy uwalniania](#rundown_combo)  
  
<a name="runtime"></a>   
### <a name="clr-etw-runtime-keywords"></a>Słowa kluczowe środowiska uruchomieniowego CLR ETW  
 W poniższej tabeli wymieniono słowa kluczowe środowiska uruchomieniowego CLR ETW, ich wartości i ich użycia.  
  
|Nazwa słowa kluczowego środowiska uruchomieniowego|Wartość|Cel|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|Włącza zbieranie [zdarzeń wyrzucania elementów bezużytecznych](garbage-collection-etw-events.md).|  
|`LoaderKeyword`|0x00000008|Włącza zbieranie [zdarzeń modułu ładującego](loader-etw-events.md).|  
|`JITKeyword`|0x00000010|Włącza zbieranie [zdarzeń just-in-Time (JIT)](jit-tracing-etw-events.md).|  
|`NGenKeyword`|0x00000020|Włącza zbieranie zdarzeń dla natywnych metod obrazu (metod przetwarzanych przez generator obrazu natywnego, Ngen. exe); używany z `StartEnumerationKeyword` i `EndEnumerationKeyword`. To słowo kluczowe ma duże obciążenie. Generuje zdarzenia dla każdej metody wewnątrz każdego załadowanego modułu NGen. Jeśli to możliwe, zamiast korzystać z tego słowa kluczowego, zalecamy używanie baz danych programu (plików PDB) generowanych przez narzędzia profilowania do pobierania informacji o metodach z modułów NGen. Zobacz również `OverrideAndSuppressNGenEventsKeyword` w dalszej części tej tabeli.|  
|`StartEnumerationKeyword`|0x00000040|Włącza Wyliczenie wszystkich metod w środowisku uruchomieniowym; używane w połączeniu z `NGenKeyword`.|  
|`EndEnumerationKeyword`|0x00000080|Włącza Wyliczenie wszystkich metod zniszczonych w czasie wykonywania; używane w połączeniu z `JITKeyword` i `NGenKeyword`.|  
|`SecurityKeyword`|0x00000400|Włącza zbieranie [zdarzeń zabezpieczeń](security-etw-events.md).|  
|`AppDomainResourceManagementKeyword`|0x00000800|Włącza zbieranie zdarzeń monitorowania zasobów na poziomie domeny aplikacji.|  
|`JITTracingKeyword`|0x00001000|Włącza zbieranie [zdarzeń śledzenia JIT](jit-tracing-etw-events.md).|  
|`InteropKeyword`|0x00002000|Włącza zbieranie [zdarzeń międzyoperacyjnych](interop-etw-events.md).|  
|`ContentionKeyword`|0x00004000|Włącza zbieranie [zdarzeń rywalizacji](contention-etw-events.md).|  
|`ExceptionKeyword`|0x00008000|Włącza zbieranie [zdarzeń wyjątków](exception-thrown-v1-etw-event.md).|  
|`ThreadingKeyword`|0x00010000|Włącza zbieranie [zdarzeń puli wątków](thread-pool-etw-events.md).|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(Dostępne w .NET Framework 4,5 i nowszych). Pomija nadmiarowe słowo kluczowe `NGenKeyword` i zapobiega generowaniu zdarzeń dla metod, które znajdują się w modułach NGen. Począwszy od .NET Framework 4,5, narzędzia profilowania powinny używać `OverrideAndSuppressNGenEventsKeyword` i `NGenKeyword` ze sobą, aby pominąć generowanie zdarzeń dla metod w modułach NGen. Dzięki temu narzędzie profilowania będzie używać bardziej wydajnej NGen plików PDB, aby uzyskać informacje o metodach w modułach NGen. Środowisko CLR w .NET Framework 4 i starszych wersjach nie obsługuje tworzenia plików PDB NGen. W tych wcześniejszych wersjach środowisko CLR nie rozpoznaje `OverrideAndSuppressNGenEventsKeyword` i przetworzy `NGenKeyword` do generowania zdarzeń dla metod w modułach NGen.|  
|`PerfTrackKeyWord`|0x2000000|Włącza zbieranie zdarzeń `ModuleLoad` i `ModuleRange`.|  
|`StackKeyword`|0x40000000|Włącza zbieranie [zdarzeń śledzenia stosu](stack-etw-event.md)CLR.|  
  
<a name="rundown"></a>   
### <a name="clr-etw-rundown-keywords"></a>Słowa kluczowe uwalniania CLR  
 Poniższa tabela zawiera listę słów kluczowych uwalniania CLR, ich wartości i ich użycia.  
  
|Nazwa słowa kluczowego uwalniania|Wartość|Cel|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Włącza zbieranie zdarzeń modułu ładującego, gdy są używane z `StartRundownKeyword` i `EndRundownKeyword`.|  
|`JitRundownKeyword`|0x00000010|Umożliwia zbieranie `DCStart` metod i zdarzeń `DCEnd` dla metod skompilowanych w trybie JIT, gdy są używane z `StartRundownKeyword` i `EndRundownKeyword`.|  
|`NGenRundownKeyword`|0x00000020|Umożliwia zbieranie `DCStart` metod i zdarzeń `DCEnd` dla metod obrazów natywnych NGen w przypadku używania z `StartRundownKeyword` i `EndRundownKeyword`. To słowo kluczowe ma duże obciążenie. Generuje zdarzenia dla każdej metody wewnątrz każdego załadowanego modułu NGen. Jeśli to możliwe, zamiast korzystać z tego słowa kluczowego, zalecamy używanie baz danych programu (plików PDB) generowanych przez narzędzia profilowania do pobierania informacji o metodach z modułów NGen. Zobacz również `OverrideAndSuppressNGenEventsRundownKeyword` w dalszej części tej tabeli.|  
|`StartRundownKeyword`|0x00000040|Włącza wyliczanie stanu systemu podczas początkowego uwalniania.|  
|`EndRundownKeyword`|0x00000100|Włącza wyliczanie stanu systemu podczas końcowego uwalniania.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Włącza zbieranie zdarzeń monitorowania zasobów na poziomie <xref:System.AppDomain>, gdy jest używany z `StartRundownKeyword` lub `EndRundownKeyword`.|  
|`ThreadingKeyword`|0x00010000|Włącza zbieranie zdarzeń puli wątków.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(Dostępne w .NET Framework 4,5 i nowszych). Pomija nadmiarowe słowo kluczowe `NGenRundownKeyword` i zapobiega generowaniu zdarzeń dla metod, które znajdują się w modułach NGen. Począwszy od .NET Framework 4,5, narzędzia profilowania powinny używać `OverrideAndSuppressNGenEventsRundownKeyword` i `NGenRundownKeyword` ze sobą, aby pominąć generowanie zdarzeń dla metod w modułach NGen. Dzięki temu narzędzie profilowania będzie używać bardziej wydajnej NGen plików PDB, aby uzyskać informacje o metodach w modułach NGen. Środowisko CLR w .NET Framework 4 i starszych wersjach nie obsługuje tworzenia plików PDB NGen. W tych wcześniejszych wersjach środowisko CLR nie rozpoznaje `OverrideAndSuppressNGenEventsRundownKeyword` i przetworzy `NGenRundownKeyword` do generowania zdarzeń dla metod w modułach NGen.|  
|`PerfTrackKeyWord`|0x2000000|Umożliwia zbieranie zdarzeń `ModuleDCStart`, `ModuleDCEnd`, `ModuleRangeDCStart`i `ModuleRangeDCEnd`.|   
  
<a name="runtime_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Kombinacje słów kluczowych dla rozpoznawania symboli dla dostawcy środowiska uruchomieniowego  
  
|Słowa kluczowe i flagi|Domena aplikacji, zestaw, zdarzenia ładowania/zwalniania modułu|Zdarzenia ładowania/zwalniania metod (z wyjątkiem zdarzeń dynamicznych)|Zdarzenia dynamicznej ładowania/niszczenia metod dynamicznych|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Ładowanie i zwalnianie zdarzeń.|Brak.|Brak.|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` nie dodaje niczego)|Brak.|Załaduj zdarzenia.|Ładowanie i zwalnianie zdarzeń.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|Brak.|Ładowanie i zwalnianie zdarzeń.|Ładowanie i zwalnianie zdarzeń.|  
|`NGenKeyword`|Brak.|Brak.|Nie dotyczy.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|Brak.|Załaduj zdarzenia.|Nie dotyczy.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|Brak.|Zwolnij zdarzenia.|Nie dotyczy.|  
  
<a name="rundown_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Kombinacje słów kluczowych dla rozpoznawania symboli dla dostawcy uwalniania  
  
|Słowa kluczowe i flagi|Domena aplikacji, zestaw, DCStart modułów/zdarzenia DCEnd|Zdarzenia DCStart/DCEnd (w tym zdarzenia metod dynamicznych)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|zdarzenia `DCStart`.|Brak.|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|zdarzenia `DCEnd`.|Brak.|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|Brak.|zdarzenia `DCStart`.|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|Brak.|zdarzenia `DCEnd`.|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|Brak.|zdarzenia `DCStart`.|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|Brak.|zdarzenia `DCEnd`.|  

## <a name="etw-event-levels"></a>Poziomy zdarzeń ETW  
 Zdarzenia ETW można również filtrować według poziomu. Jeśli poziom jest ustawiony na 0x5, zdarzenia wszystkich poziomów, w tym 0x5 i poniżej (czyli zdarzenia należące do kategorii włączonych za pomocą słów kluczowych) są wywoływane. Jeśli poziom jest ustawiony na 0x2, wywoływane są tylko zdarzenia należące do poziomu 0x2 i poniżej.  
  
 Poziomy mają następujące znaczenie:  
  
 0x5 — pełne  
  
 0x4 — informacje  
  
 0x3 — ostrzeżenie  
  
 0x2 — błąd  
  
 0x1 — krytyczny  
  
 0x0 — LogAlways  
  
## <a name="see-also"></a>Zobacz także

- [Dostawcy CLR ETW](clr-etw-providers.md)
- [Zdarzenia CLR ETW](clr-etw-events.md)
- [Zdarzenia ETW w środowisku CLR](etw-events-in-the-common-language-runtime.md)
