---
title: Słowa kluczowe i poziomy ETW CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW keywords
- CLR ETW levels
- ETW, CLR keywords
- ETW, CLR levels
ms.assetid: fdf5856d-516b-4042-849d-911c4518a6cb
ms.openlocfilehash: 2106ed0d85cd116be4d7c46396ad6e1597c4341d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400065"
---
# <a name="clr-etw-keywords-and-levels"></a>Słowa kluczowe i poziomy ETW CLR
Śledzenie zdarzeń dla zdarzeń systemu Windows (ETW) można filtrować według kategorii i poziomu. Słowa kluczowe programu [CLR ETW](#clr-etw-keywords) zdarzenia umożliwiają filtrowanie zdarzeń według kategorii; są one używane w kombinacjach dla dostawców środowiska wykonawczego i rundown. [Poziomy zdarzeń](#etw-event-levels) są identyfikowane przez flagi.  
  
## <a name="clr-etw-keywords"></a>Clr ETW Słowa kluczowe  
 Słowa kluczowe są flagi, które mogą być łączone do generowania wartości. W praktyce używasz wartości szesnastkowe słów kluczowych zamiast nazw słów kluczowych podczas wywoływania narzędzi wiersza polecenia.  
  
 Słowa kluczowe są opisane w następujących tabelach:  
  
- [Clr ETW słowa kluczowe środowiska uruchomieniowego](#runtime)  
  
- [Clr ETW rundown słowa kluczowe](#rundown)  
  
- [Kombinacje słów kluczowych dla rozpoznawania symboli dla dostawcy środowiska wykonawczego](#runtime_combo)  
  
- [Kombinacje słów kluczowych dla rozpoznawania symboli dla dostawcy wybiegiem](#rundown_combo)  
  
<a name="runtime"></a>
### <a name="clr-etw-runtime-keywords"></a>Clr ETW Runtime Słowa kluczowe  
 W poniższej tabeli wymieniono słowa kluczowe środowiska wykonawczego CLR ETW, ich wartości i używane.  
  
|Nazwa słowa kluczowego środowiska uruchomieniowego|Wartość|Przeznaczenie|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|Włącza zbieranie [zdarzeń wyrzucania elementów bezużytecznych.](garbage-collection-etw-events.md)|  
|`LoaderKeyword`|0x00000008|Umożliwia zbieranie [zdarzeń modułu ładującego](loader-etw-events.md).|  
|`JITKeyword`|0x00000010|Umożliwia zbieranie [zdarzeń just-in-time (JIT).](jit-tracing-etw-events.md)|  
|`NGenKeyword`|0x00000020|Umożliwia zbieranie zdarzeń dla metod obrazu macierzystego (metody przetwarzane przez generator obrazu natywnego, Ngen.exe); używane `StartEnumerationKeyword` z `EndEnumerationKeyword`i . To słowo kluczowe ma wysokie obciążenie. Generuje zdarzenia dla każdej metody wewnątrz każdego załadowanego modułu NGen. Jeśli to możliwe, zamiast używać tego słowa kluczowego, zaleca się użycie baz danych programu (PDB) generowanych przez narzędzia profilowania w celu pobrania informacji o metodach z modułów NGen. Zobacz `OverrideAndSuppressNGenEventsKeyword` też w dalszej części tej tabeli.|  
|`StartEnumerationKeyword`|0x00000040|Umożliwia wyliczenie wszystkich metod w czasie wykonywania; w połączeniu `NGenKeyword`z .|  
|`EndEnumerationKeyword`|0x00000080|Umożliwia wyliczenie wszystkich metod zniszczonych w czasie wykonywania; w połączeniu `JITKeyword` z `NGenKeyword`i .|  
|`SecurityKeyword`|0x00000400|Umożliwia zbieranie [zdarzeń zabezpieczeń](security-etw-events.md).|  
|`AppDomainResourceManagementKeyword`|0x00000800|Umożliwia zbieranie zdarzeń monitorowania zasobów na poziomie domeny aplikacji.|  
|`JITTracingKeyword`|0x00001000|Umożliwia zbieranie [zdarzeń śledzenia JIT](jit-tracing-etw-events.md).|  
|`InteropKeyword`|0x00002000|Umożliwia zbieranie [zdarzeń międzyoperacyjnych](interop-etw-events.md).|  
|`ContentionKeyword`|0x00004000|Włącza zbieranie [zdarzeń rywalizacji](contention-etw-events.md).|  
|`ExceptionKeyword`|0x00008000|Włącza zbieranie [zdarzeń wyjątków](exception-thrown-v1-etw-event.md).|  
|`ThreadingKeyword`|0x00010000|Umożliwia zbieranie [zdarzeń puli wątków](thread-pool-etw-events.md).|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(Dostępne w .NET Framework 4.5 i nowszych). Pomija słowo kluczowe `NGenKeyword` wysokiego napowietrzania i zapobiega generowaniu zdarzeń dla metod, które znajdują się wewnątrz modułów NGen. Począwszy od .NET Framework 4.5, `OverrideAndSuppressNGenEventsKeyword` narzędzia `NGenKeyword` profilowania należy używać i razem pomijać generowanie zdarzeń dla metod w modułach NGen. Dzięki temu narzędzie do profilowania do korzystania z bardziej wydajnych NGen PDBs, aby uzyskać informacje o metodach w modułach NGen. Clr w .NET Framework 4 i wcześniejszych wersjach nie obsługuje tworzenia kontrolerów PDB NGen. W tych wcześniejszych wersjach CLR `OverrideAndSuppressNGenEventsKeyword` nie `NGenKeyword` rozpozna i będzie przetwarzać do generowania zdarzeń dla metod w modułach NGen.|  
|`PerfTrackKeyWord`|0x2000000|Umożliwia zbieranie `ModuleLoad` i `ModuleRange` zdarzenia.|  
|`StackKeyword`|0x40000000|Włącza zbieranie zdarzeń [śledzenia stosu](stack-etw-event.md)CLR.|  
  
<a name="rundown"></a>
### <a name="clr-etw-rundown-keywords"></a>Clr ETW Rundown Słowa kluczowe  
 W poniższej tabeli wymieniono słowa kluczowe, ich wartości i używane słowa kluczowe CLR ETW.  
  
|Nazwa słowa kluczowego sysk w przebiegłej sy|Wartość|Przeznaczenie|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Włącza zbieranie zdarzeń modułu ładującego, gdy jest używany z `StartRundownKeyword` i . `EndRundownKeyword`|  
|`JitRundownKeyword`|0x00000010|Włącza zbieranie metod `DCStart` `DCEnd` i zdarzeń dla metod skompilowanych przez JIT, gdy jest używany z `StartRundownKeyword` i `EndRundownKeyword`.|  
|`NGenRundownKeyword`|0x00000020|Włącza zbieranie metod `DCStart` `DCEnd` i zdarzeń dla metod obrazu `StartRundownKeyword` natywnego NGen, gdy są używane z i `EndRundownKeyword`. To słowo kluczowe ma wysokie obciążenie. Generuje zdarzenia dla każdej metody wewnątrz każdego załadowanego modułu NGen. Jeśli to możliwe, zamiast używać tego słowa kluczowego, zaleca się użycie baz danych programu (PDB) generowanych przez narzędzia profilowania w celu pobrania informacji o metodach z modułów NGen. Zobacz `OverrideAndSuppressNGenEventsRundownKeyword` też w dalszej części tej tabeli.|  
|`StartRundownKeyword`|0x00000040|Włącza wyliczenie stanu systemu podczas uruchomienia.|  
|`EndRundownKeyword`|0x00000100|Włącza wyliczenie stanu systemu podczas zakończenia spływu.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Włącza zbieranie zdarzeń do monitorowania <xref:System.AppDomain> zasobów na `StartRundownKeyword` poziomie `EndRundownKeyword`używanym z programem .|  
|`ThreadingKeyword`|0x00010000|Umożliwia zbieranie zdarzeń puli wątków.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(Dostępne w .NET Framework 4.5 i nowszych). Pomija słowo kluczowe `NGenRundownKeyword` wysokiego napowietrzania i zapobiega generowaniu zdarzeń dla metod, które znajdują się wewnątrz modułów NGen. Począwszy od .NET Framework 4.5, `OverrideAndSuppressNGenEventsRundownKeyword` narzędzia `NGenRundownKeyword` profilowania należy używać i razem pomijać generowanie zdarzeń dla metod w modułach NGen. Dzięki temu narzędzie do profilowania do korzystania z bardziej wydajnych NGen PDBs, aby uzyskać informacje o metodach w modułach NGen. Clr w .NET Framework 4 i wcześniejszych wersjach nie obsługuje tworzenia kontrolerów PDB NGen. W tych wcześniejszych wersjach CLR `OverrideAndSuppressNGenEventsRundownKeyword` nie `NGenRundownKeyword` rozpozna i będzie przetwarzać do generowania zdarzeń dla metod w modułach NGen.|  
|`PerfTrackKeyWord`|0x2000000|Włącza kolekcję `ModuleDCStart`, `ModuleDCEnd` `ModuleRangeDCStart`, `ModuleRangeDCEnd` i zdarzeń.|
  
<a name="runtime_combo"></a>
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Kombinacje słów kluczowych dla rozpoznawania symboli dla dostawcy środowiska wykonawczego  
  
|Słowa kluczowe i flagi|Domena aplikacji, zestaw, zdarzenia ładowania/zwalniania modułu|Zdarzenia ładowania/zwalniania metody (z wyjątkiem zdarzeń dynamicznych)|Zdarzenia ładowania/niszczenia metody dynamicznej|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Załaduj i rozładuj zdarzenia.|Brak.|Brak.|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` nic nie dodaje)|Brak.|Załaduj zdarzenia.|Załaduj i rozładuj zdarzenia.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|Brak.|Załaduj i rozładuj zdarzenia.|Załaduj i rozładuj zdarzenia.|  
|`NGenKeyword`|Brak.|Brak.|Nie dotyczy.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|Brak.|Załaduj zdarzenia.|Nie dotyczy.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|Brak.|Zwalnianie zdarzeń.|Nie dotyczy.|  
  
<a name="rundown_combo"></a>
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Kombinacje słów kluczowych dla rozpoznawania symboli dla dostawcy wybiegu  
  
|Słowa kluczowe i flagi|Domena aplikacji, zestaw, zdarzenia dcstart/DCEnd modułu|Zdarzenia metody DCStart/DCEnd (w tym zdarzenia metody dynamicznej)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|`DCStart`Zdarzenia.|Brak.|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|`DCEnd`Zdarzenia.|Brak.|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|Brak.|`DCStart`Zdarzenia.|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|Brak.|`DCEnd`Zdarzenia.|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|Brak.|`DCStart`Zdarzenia.|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|Brak.|`DCEnd`Zdarzenia.|  

## <a name="etw-event-levels"></a>Poziomy zdarzeń ETW  
 Zdarzenia ETW mogą być również filtrowane według poziomu. Jeśli poziom jest ustawiony na 0x5, zdarzenia na wszystkich poziomach, w tym 0x5 i poniżej (które są zdarzeniami, które należą do kategorii włączonych za pomocą słów kluczowych) są wywoływane. Jeśli poziom jest ustawiony na 0x2, tylko zdarzenia, które należą do poziomu 0x2 i poniżej są wywoływane.  
  
 Poziomy mają następujące znaczenie:  
  
 0x5 - Pełne  
  
 0x4 - Informacyjny  
  
 0x3 - Ostrzeżenie  
  
 0x2 - Błąd  
  
 0x1 - Krytyczny  
  
 0x0 - LogWki  
  
## <a name="see-also"></a>Zobacz też

- [Dostawcy CLR ETW](clr-etw-providers.md)
- [Zdarzenia ETW CLR](clr-etw-events.md)
- [Zdarzenia ETW w środowisku CLR](etw-events-in-the-common-language-runtime.md)
