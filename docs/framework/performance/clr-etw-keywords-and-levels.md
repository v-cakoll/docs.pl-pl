---
title: Słowa kluczowe i poziomy ETW CLR
description: Sprawdź słowa kluczowe i poziomy śledzenia zdarzeń środowiska uruchomieniowego języka wspólnego (CLR) dla systemu Windows (ETW). Zdarzenia dotyczące słów kluczowych funkcji ETW środowiska CLR umożliwiają filtrowanie zdarzeń według kategorii.
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW keywords
- CLR ETW levels
- ETW, CLR keywords
- ETW, CLR levels
ms.assetid: fdf5856d-516b-4042-849d-911c4518a6cb
ms.openlocfilehash: dfbe047640a3a640cf37adeea6fa3656cfd9ec6d
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309680"
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
  
|Nazwa słowa kluczowego środowiska uruchomieniowego|Wartość|Przeznaczenie|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|Włącza zbieranie [zdarzeń wyrzucania elementów bezużytecznych](garbage-collection-etw-events.md).|  
|`LoaderKeyword`|0x00000008|Włącza zbieranie [zdarzeń modułu ładującego](loader-etw-events.md).|  
|`JITKeyword`|0x00000010|Włącza zbieranie [zdarzeń just-in-Time (JIT)](jit-tracing-etw-events.md).|  
|`NGenKeyword`|0x00000020|Włącza zbieranie zdarzeń dla natywnych metod obrazu (metod przetwarzanych przez generator obrazu natywnego, Ngen.exe); używany z `StartEnumerationKeyword` i `EndEnumerationKeyword` . To słowo kluczowe ma duże obciążenie. Generuje zdarzenia dla każdej metody wewnątrz każdego załadowanego modułu NGen. Jeśli to możliwe, zamiast korzystać z tego słowa kluczowego, zalecamy używanie baz danych programu (plików PDB) generowanych przez narzędzia profilowania do pobierania informacji o metodach z modułów NGen. Zobacz również `OverrideAndSuppressNGenEventsKeyword` w dalszej części tej tabeli.|  
|`StartEnumerationKeyword`|0x00000040|Włącza Wyliczenie wszystkich metod w środowisku uruchomieniowym; używane w połączeniu z `NGenKeyword` .|  
|`EndEnumerationKeyword`|0x00000080|Włącza Wyliczenie wszystkich metod zniszczonych w czasie wykonywania; używane w połączeniu z `JITKeyword` i `NGenKeyword` .|  
|`SecurityKeyword`|0x00000400|Włącza zbieranie [zdarzeń zabezpieczeń](security-etw-events.md).|  
|`AppDomainResourceManagementKeyword`|0x00000800|Włącza zbieranie zdarzeń monitorowania zasobów na poziomie domeny aplikacji.|  
|`JITTracingKeyword`|0x00001000|Włącza zbieranie [zdarzeń śledzenia JIT](jit-tracing-etw-events.md).|  
|`InteropKeyword`|0x00002000|Włącza zbieranie [zdarzeń międzyoperacyjnych](interop-etw-events.md).|  
|`ContentionKeyword`|0x00004000|Włącza zbieranie [zdarzeń rywalizacji](contention-etw-events.md).|  
|`ExceptionKeyword`|0x00008000|Włącza zbieranie [zdarzeń wyjątków](exception-thrown-v1-etw-event.md).|  
|`ThreadingKeyword`|0x00010000|Włącza zbieranie [zdarzeń puli wątków](thread-pool-etw-events.md).|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(Dostępne w .NET Framework 4,5 i nowszych). Pomija słowo kluczowe ze zbyt dużym obciążeniem `NGenKeyword` i zapobiega generowaniu zdarzeń dla metod, które znajdują się w modułach Ngen. Począwszy od .NET Framework 4,5, narzędzia profilowania powinny używać `OverrideAndSuppressNGenEventsKeyword` i `NGenKeyword` ze sobą, aby pominąć generowanie zdarzeń dla metod w modułach Ngen. Dzięki temu narzędzie profilowania będzie używać bardziej wydajnej NGen plików PDB, aby uzyskać informacje o metodach w modułach NGen. Środowisko CLR w .NET Framework 4 i starszych wersjach nie obsługuje tworzenia plików PDB NGen. W tych wcześniejszych wersjach środowisko CLR nie rozpoznaje `OverrideAndSuppressNGenEventsKeyword` i przetwarza `NGenKeyword` zdarzenia dla metod w modułach Ngen.|  
|`PerfTrackKeyWord`|0x2000000|Włącza zbieranie `ModuleLoad` `ModuleRange` zdarzeń i.|  
|`StackKeyword`|0x40000000|Włącza zbieranie [zdarzeń śledzenia stosu](stack-etw-event.md)CLR.|  
  
<a name="rundown"></a>
### <a name="clr-etw-rundown-keywords"></a>Słowa kluczowe uwalniania CLR  
 Poniższa tabela zawiera listę słów kluczowych uwalniania CLR, ich wartości i ich użycia.  
  
|Nazwa słowa kluczowego uwalniania|Wartość|Przeznaczenie|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Włącza zbieranie zdarzeń modułu ładującego, gdy są używane z `StartRundownKeyword` i `EndRundownKeyword` .|  
|`JitRundownKeyword`|0x00000010|Włącza kolekcję metod `DCStart` i `DCEnd` zdarzeń dla metod skompilowanych w trybie JIT, gdy są używane z `StartRundownKeyword` i `EndRundownKeyword` .|  
|`NGenRundownKeyword`|0x00000020|Włącza zbieranie metody `DCStart` i `DCEnd` zdarzeń dla metod obrazu natywnego NGen w przypadku używania z `StartRundownKeyword` i `EndRundownKeyword` . To słowo kluczowe ma duże obciążenie. Generuje zdarzenia dla każdej metody wewnątrz każdego załadowanego modułu NGen. Jeśli to możliwe, zamiast korzystać z tego słowa kluczowego, zalecamy używanie baz danych programu (plików PDB) generowanych przez narzędzia profilowania do pobierania informacji o metodach z modułów NGen. Zobacz również `OverrideAndSuppressNGenEventsRundownKeyword` w dalszej części tej tabeli.|  
|`StartRundownKeyword`|0x00000040|Włącza wyliczanie stanu systemu podczas początkowego uwalniania.|  
|`EndRundownKeyword`|0x00000100|Włącza wyliczanie stanu systemu podczas końcowego uwalniania.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Włącza zbieranie zdarzeń do monitorowania zasobów na <xref:System.AppDomain> poziomie, gdy jest używany z `StartRundownKeyword` lub `EndRundownKeyword` .|  
|`ThreadingKeyword`|0x00010000|Włącza zbieranie zdarzeń puli wątków.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(Dostępne w .NET Framework 4,5 i nowszych). Pomija słowo kluczowe ze zbyt dużym obciążeniem `NGenRundownKeyword` i zapobiega generowaniu zdarzeń dla metod, które znajdują się w modułach Ngen. Począwszy od .NET Framework 4,5, narzędzia profilowania powinny używać `OverrideAndSuppressNGenEventsRundownKeyword` i `NGenRundownKeyword` ze sobą, aby pominąć generowanie zdarzeń dla metod w modułach Ngen. Dzięki temu narzędzie profilowania będzie używać bardziej wydajnej NGen plików PDB, aby uzyskać informacje o metodach w modułach NGen. Środowisko CLR w .NET Framework 4 i starszych wersjach nie obsługuje tworzenia plików PDB NGen. W tych wcześniejszych wersjach środowisko CLR nie rozpoznaje `OverrideAndSuppressNGenEventsRundownKeyword` i przetwarza `NGenRundownKeyword` zdarzenia dla metod w modułach Ngen.|  
|`PerfTrackKeyWord`|0x2000000|Włącza zbieranie `ModuleDCStart` `ModuleDCEnd` zdarzeń,, `ModuleRangeDCStart` i `ModuleRangeDCEnd` .|
  
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
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|`DCStart`wydarzeniach.|Brak.|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|`DCEnd`wydarzeniach.|Brak.|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|Brak.|`DCStart`wydarzeniach.|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|Brak.|`DCEnd`wydarzeniach.|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|Brak.|`DCStart`wydarzeniach.|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|Brak.|`DCEnd`wydarzeniach.|  

## <a name="etw-event-levels"></a>Poziomy zdarzeń ETW  
 Zdarzenia ETW można również filtrować według poziomu. Jeśli poziom jest ustawiony na 0x5, zdarzenia wszystkich poziomów, w tym 0x5 i poniżej (czyli zdarzenia należące do kategorii włączonych za pomocą słów kluczowych) są wywoływane. Jeśli poziom jest ustawiony na 0x2, wywoływane są tylko zdarzenia należące do poziomu 0x2 i poniżej.  
  
 Poziomy mają następujące znaczenie:  
  
 0x5 — pełne  
  
 0x4 — informacje  
  
 0x3 — ostrzeżenie  
  
 0x2 — błąd  
  
 0x1 — krytyczny  
  
 0x0 — LogAlways  
  
## <a name="see-also"></a>Zobacz też

- [Dostawcy CLR ETW](clr-etw-providers.md)
- [Zdarzenia ETW CLR](clr-etw-events.md)
- [Zdarzenia ETW w środowisku CLR](etw-events-in-the-common-language-runtime.md)
