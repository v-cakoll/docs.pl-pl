---
title: "Słowa kluczowe i poziomy ETW CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLR ETW keywords
- CLR ETW levels
- ETW, CLR keywords
- ETW, CLR levels
ms.assetid: fdf5856d-516b-4042-849d-911c4518a6cb
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7f5dcdd969619526c52a9ae44014030a9f0c6dc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="clr-etw-keywords-and-levels"></a>Słowa kluczowe i poziomy ETW CLR
<a name="top"></a>Zdarzenia śledzenia dla zdarzeń systemu Windows (ETW) można filtrować według kategorii i poziomu. Zdarzenia [słowa kluczowe CLR ETW](#keywords) włączenie filtrowania zdarzeń według kategorii; są używane w kombinacji dostawców środowiska uruchomieniowego i uwalniania. [Poziomów zdarzeń](#levels) są identyfikowane za pomocą flagi.  
  
<a name="keywords"></a>   
## <a name="clr-etw-keywords"></a>Słowa kluczowe CLR ETW  
 Słowa kluczowe są flag, które można łączyć do generowania wartości. W praktyce możesz użyć wartości szesnastkowe słów kluczowych zamiast nazw — słowo kluczowe podczas wywoływania narzędzia wiersza polecenia.  
  
 W poniższych tabelach opisano słowa kluczowe:  
  
-   [Słowa kluczowe środowiska uruchomieniowego CLR ETW](#runtime)  
  
-   [Stert słowa kluczowe CLR ETW](#rundown)  
  
-   [Kombinacje — słowo kluczowe do rozpoznawania symboli dla dostawcy środowiska wykonawczego](#runtime_combo)  
  
-   [Kombinacje — słowo kluczowe do rozpoznawania symboli dla dostawcy stert](#rundown_combo)  
  
<a name="runtime"></a>   
### <a name="clr-etw-runtime-keywords"></a>Słowa kluczowe środowiska uruchomieniowego CLR ETW  
 W poniższej tabeli wymieniono słowa kluczowe CLR ETW środowiska uruchomieniowego, ich wartości i ich użycia.  
  
|Nazwa środowiska uruchomieniowego — słowo kluczowe|Wartość|Cel|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|Umożliwia zbieranie [zdarzenia wyrzucania elementów bezużytecznych](../../../docs/framework/performance/garbage-collection-etw-events.md).|  
|`LoaderKeyword`|0x00000008|Umożliwia zbieranie [zdarzenia modułu ładującego](../../../docs/framework/performance/loader-etw-events.md).|  
|`JITKeyword`|0x00000010|Umożliwia zbieranie [zdarzenia just-in-time (JIT)](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`NGenKeyword`|0x00000020|Umożliwia zbieranie zdarzeń dla metody obrazu macierzystego (metody przetworzone przez Generator obrazu natywnego Ngen.exe); używane z `StartEnumerationKeyword` i `EndEnumerationKeyword`. To słowo kluczowe ma wysokie obciążenie. Generuje on zdarzenia dla każdej metody wewnątrz każdego załadowany moduł NGen. Jeśli to możliwe, zamiast używać słowa kluczowego, zalecane jest użycie baz danych programu (PDB) generowany przez narzędzia profilowania można pobrać informacji o metodach z modułów NGen. Zobacz też `OverrideAndSuppressNGenEventsKeyword` dalszej części tej tabeli.|  
|`StartEnumerationKeyword`|0x00000040|Włącza wyliczanie wszystkie metody w środowisku wykonawczym; używane w połączeniu z `NGenKeyword`.|  
|`EndEnumerationKeyword`|0x00000080|Włącza wyliczanie wszystkie metody zniszczone w środowisku wykonawczym; używane w połączeniu z `JITKeyword` i `NGenKeyword`.|  
|`SecurityKeyword`|0x00000400|Umożliwia zbieranie [zdarzenia zabezpieczeń](../../../docs/framework/performance/security-etw-events.md).|  
|`AppDomainResourceManagementKeyword`|0x00000800|Umożliwia zbieranie zdarzeń na poziomie domeny aplikacji do monitorowania zasobów.|  
|`JITTracingKeyword`|0x00001000|Umożliwia zbieranie [zdarzenia śledzenia JIT](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`InteropKeyword`|0x00002000|Umożliwia zbieranie [zdarzenia międzyoperacyjności](../../../docs/framework/performance/interop-etw-events.md).|  
|`ContentionKeyword`|0x00004000|Umożliwia zbieranie [zdarzenia rywalizacji](../../../docs/framework/performance/contention-etw-events.md).|  
|`ExceptionKeyword`|0x00008000|Umożliwia zbieranie [zdarzeń wyjątków](../../../docs/framework/performance/exception-thrown-v1-etw-event.md).|  
|`ThreadingKeyword`|0x00010000|Umożliwia zbieranie [zdarzenia puli wątków](../../../docs/framework/performance/thread-pool-etw-events.md).|  
|`OverrideAndSuppressNGenEventsKeyword`|0X00040000|(Dostępne w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszej.) Pomija koszty wysokiej `NGenKeyword` — słowo kluczowe i uniemożliwia generowanie zdarzeń dla metod, które znajdują się wewnątrz modułów NGen. Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], należy użyć narzędzia profilowania `OverrideAndSuppressNGenEventsKeyword` i `NGenKeyword` ze sobą, aby pominąć generowanie zdarzeń dla metod w modułach NGen. Dzięki temu narzędziu profilowania umożliwia bardziej efektywne PDB NGen uzyskanie informacji na temat metod w modułach NGen. CLR w .NET Framework 4 i wcześniejsze wersje nie obsługuje tworzenia plików PDB NGen. W tych starszych wersji środowiska CLR nie rozpoznaje `OverrideAndSuppressNGenEventsKeyword` i będzie przetwarzać `NGenKeyword` generowanie zdarzeń dla metod w modułach NGen.|  
|`PerfTrackKeyWord`|0x2000000|Umożliwia zbieranie `ModuleLoad` i `ModuleRange` zdarzenia.|  
|`StackKeyword`|0x40000000|Umożliwia zbieranie CLR [śledzenia zdarzeń stack](../../../docs/framework/performance/stack-etw-event.md).|  
  
 [Powrót do początku](#top)  
  
<a name="rundown"></a>   
### <a name="clr-etw-rundown-keywords"></a>Stert słowa kluczowe CLR ETW  
 W poniższej tabeli wymieniono stert słowa kluczowe CLR ETW, ich wartości i ich użycia.  
  
|Nazwa stert — słowo kluczowe|Wartość|Cel|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Umożliwia zbieranie zdarzeń modułu ładującego, gdy jest używany z `StartRundownKeyword` i `EndRundownKeyword`.|  
|`JitRundownKeyword`|0x00000010|Umożliwia zbieranie metody `DCStart` i `DCEnd` zdarzenia dla kompilacji JIT metod, gdy jest używany z `StartRundownKeyword` i `EndRundownKeyword`.|  
|`NGenRundownKeyword`|0x00000020|Umożliwia zbieranie metody `DCStart` i `DCEnd` zdarzenia dla metod obrazu macierzystego NGen, gdy jest używany z `StartRundownKeyword` i `EndRundownKeyword`. To słowo kluczowe ma wysokie obciążenie. Generuje on zdarzenia dla każdej metody wewnątrz każdego załadowany moduł NGen. Jeśli to możliwe, zamiast używać słowa kluczowego, zalecane jest użycie baz danych programu (PDB) generowany przez narzędzia profilowania można pobrać informacji o metodach z modułów NGen. Zobacz też `OverrideAndSuppressNGenEventsRundownKeyword` dalszej części tej tabeli.|  
|`StartRundownKeyword`|0x00000040|Włącza wyliczanie stanu systemu podczas uwalniania rozpoczęcia.|  
|`EndRundownKeyword`|0x00000100|Włącza wyliczanie stanu systemu podczas uwalniania zakończenia.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Umożliwia zbieranie zdarzeń monitorowania zasobów w <xref:System.AppDomain> poziom, gdy jest używany z `StartRundownKeyword` lub `EndRundownKeyword`.|  
|`ThreadingKeyword`|0x00010000|Umożliwia zbieranie zdarzeń puli wątków.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0X00040000|(Dostępne w [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszej.) Pomija koszty wysokiej `NGenRundownKeyword` — słowo kluczowe i uniemożliwia generowanie zdarzeń dla metod, które znajdują się wewnątrz modułów NGen. Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], należy użyć narzędzia profilowania `OverrideAndSuppressNGenEventsRundownKeyword` i `NGenRundownKeyword` ze sobą, aby pominąć generowanie zdarzeń dla metod w modułach NGen. Dzięki temu narzędziu profilowania umożliwia bardziej efektywne PDB NGen uzyskanie informacji na temat metod w modułach NGen. CLR w .NET Framework 4 i wcześniejsze wersje nie obsługuje tworzenia plików PDB NGen. W tych starszych wersji środowiska CLR nie rozpoznaje `OverrideAndSuppressNGenEventsRundownKeyword` i będzie przetwarzać `NGenRundownKeyword` generowanie zdarzeń dla metod w modułach NGen.|  
|`PerfTrackKeyWord`|0x2000000|Umożliwia zbieranie `ModuleDCStart`, `ModuleDCEnd`, `ModuleRangeDCStart`, i `ModuleRangeDCEnd` zdarzenia.|  
  
 [Powrót do początku](#top)  
  
<a name="runtime_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Kombinacje — słowo kluczowe do rozpoznawania symboli dla dostawcy środowiska wykonawczego  
  
|Słowa kluczowe i flagi|Domena aplikacji, zestawu, zdarzeń ładowania i zwalniania modułu|Zdarzeń ładowania i zwalniania — metoda (z wyjątkiem zdarzenia dynamicznego)|Zdarzenia obciążenia/zniszczenia metod dynamicznych|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Ładowanie i zwalnianie zdarzenia.|Brak.|Brak.|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` nie dodaje żadnych)|Brak.|Załaduj zdarzenia.|Ładowanie i zwalnianie zdarzenia.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|Brak.|Ładowanie i zwalnianie zdarzenia.|Ładowanie i zwalnianie zdarzenia.|  
|`NGenKeyword`|Brak.|Brak.|Nie dotyczy.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|Brak.|Załaduj zdarzenia.|Nie dotyczy.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|Brak.|Zwalnianie zdarzenia.|Nie dotyczy.|  
  
 [Powrót do początku](#top)  
  
<a name="rundown_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Kombinacje — słowo kluczowe do rozpoznawania symboli dla dostawcy stert  
  
|Słowa kluczowe i flagi|Domena aplikacji, zestawu, modułu DCStart/DCEnd zdarzeń|Metoda DCStart/DCEnd zdarzenia (w tym zdarzenia metod dynamicznych)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|`DCStart`zdarzenia.|Brak.|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|`DCEnd`zdarzenia.|Brak.|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|Brak.|`DCStart`zdarzenia.|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|Brak.|`DCEnd`zdarzenia.|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|Brak.|`DCStart`zdarzenia.|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|Brak.|`DCEnd`zdarzenia.|  
  
 [Powrót do początku](#top)  
  
<a name="levels"></a>   
## <a name="etw-event-levels"></a>Poziomy zdarzenia ETW.  
 Zdarzenia ETW można również filtrować według poziomu. Jeśli poziom jest ustawiony na 0x5, pojawienia się zdarzenia wszystkie poziomy, w tym 0x5 i poniżej (które są zdarzenia, które należą do kategorii włączona przy użyciu słowa kluczowe). Jeśli poziom jest ustawiony na 0x2, są wywoływane tylko zdarzenia, które należą do poziomu 0x2 i poniżej.  
  
 Poziomy mają następujące znaczenie:  
  
 0x5 - verbose  
  
 0x4 - informacyjny  
  
 0x3 — ostrzeżenie  
  
 0x2 — błąd  
  
 0x1 — krytyczne  
  
 0x0 - LogAlways  
  
## <a name="see-also"></a>Zobacz też  
 [Dostawcy CLR ETW](../../../docs/framework/performance/clr-etw-providers.md)  
 [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)  
 [Zdarzenia ETW w środowisko uruchomieniowe języka wspólnego](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
