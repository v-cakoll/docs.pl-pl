---
title: Zdarzenia ETW śledzenia JIT
ms.date: 03/30/2017
helpviewer_keywords:
- JIT tracing events [.NET Framework]
- ETW, JIT tracing events (CLR)
ms.assetid: 926adde2-c123-452e-bf4f-4b977bf06ffb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 145a53363c9d7aca622ee0b1ccb2700e5984397d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046426"
---
# <a name="jit-tracing-etw-events"></a>Zdarzenia ETW śledzenia JIT
<a name="top"></a>Te zdarzenia zbierają informacje dotyczące sukcesu lub niepowodzenia wywołań wywołania "just-in-Time (JIT) i" JIT ".  
  
 Zdarzenia śledzenia JIT składają się z następujących dwóch kategorii:  
  
- [Zdarzenia związane z derysowaniem JIT](#jit_inlining_events)  
  
- [Zdarzenia wywołania tail w trybie JIT](#jit_tail_call_events)  
  
<a name="jit_inlining_events"></a>   
## <a name="jit-inlining-events"></a>Zdarzenia związane z derysowaniem JIT  
  
### <a name="methodjitinliningfailed-event"></a>Zdarzenie MethodJitInliningFailed  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).  
  
|Słowo kluczowe do podniesienia zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`0x10|Verbose (5)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`MethodJitInliningFailed`|186|Nie można wykreślać w trybie JIT.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win: UnicodeString|Przestrzeń nazw metody, która jest kompilowana.|  
|MethodBeingCompiledName|win: UnicodeString|Nazwa metody, która jest kompilowana.|  
|MethodBeingCompiledNameSignature|win: UnicodeString|Sygnatura metody, która jest kompilowana.|  
|InlinerNamespace|win: UnicodeString|Przestrzeń nazw metody kompilator JIT próbuje wygenerować kod dla.|  
|Nieliniowa|win: UnicodeString|Nazwa metody, dla której kompilator próbuje wygenerować kod. Taka sytuacja może nie być taka sama `MethodBeingCompiledName` jak w przypadku, gdy kompilator próbuje wykonać `MethodBeingCompiledName` kod wbudowany zamiast generowania wywołania do `InlinerName`.|  
|InlinerNameSignature|win: UnicodeString|Podpis dla elementu inline.|  
|InlineeNamespace|win: UnicodeString|Przestrzeń nazw międzywierszowego elementu.|  
|InlineeName|win: UnicodeString|Metoda, którą kompilator próbuje wykonać w wierszu (nie generuje wywołania do).|  
|InlineeNameSignature|win: UnicodeString|Podpis dla elementu inline.|  
|FailAlways|win: wartość logiczna|Wskazówka do kompilatora JIT, który będzie zawsze kończyć się niepowodzeniem dla delinii.|  
|FailReason|win: UnicodeString|INLINE_NEVER oznacza, że poprzednia próba podzielenia zostanie określona, że wykreślenie nigdy nie powiedzie się z innego powodu. w przeciwnym razie tekst w dowolnej postaci.|  
|ClrInstanceID|win: UnicodeString|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
### <a name="methodjitinliningsucceeded-event"></a>Zdarzenie MethodJitInliningSucceeded  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podniesienia zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`0x10|Verbose (5)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`MethodJitInliningSucceeded`|185|Metoda tworzenia konspektu zakończyła się pomyślnie.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win: UnicodeString|Przestrzeń nazw metody, która jest kompilowana.|  
|MethodBeingCompiledName|win: UnicodeString|Nazwa skompilowanej metody.|  
|MethodBeingCompiledNameSignature|win: UnicodeString|Sygnatura metody, która jest kompilowana.|  
|InlinerNamespace|win: UnicodeString|Przestrzeń nazw metody kompilator JIT próbuje wygenerować kod dla.|  
|Nieliniowa|win: UnicodeString|Nazwa metody, dla której kompilator próbuje wygenerować kod. Taka sytuacja może nie być taka sama `MethodBeingCompiledName` jak w przypadku, gdy kompilator próbuje wykonać `MethodBeingCompiledName` kod wbudowany zamiast generowania wywołania do `InlinerName`.|  
|InlinerNameSignature|win: UnicodeString|Podpis dla elementu inline.|  
|InlineeNamespace|win: UnicodeString|Przestrzeń nazw międzywierszowego elementu.|  
|InlineeName|win: UnicodeString|Metoda, którą kompilator próbuje wykonać w wierszu (nie generuje wywołania do).|  
|InlineeNameSignature|win: UnicodeString|Podpis dla elementu inline.|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="jit_tail_call_events"></a>   
## <a name="jit-tail-call-events"></a>Zdarzenia wywołania tail w trybie JIT  
  
### <a name="methodjittailcallfailed-event"></a>Zdarzenie MethodJITTailCallFailed  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podniesienia zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`0x10|Verbose (5)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallFailed`|189|Wywołanie metody końcowego nie powiodło się.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win: UnicodeString|Przestrzeń nazw metody, która jest kompilowana.|  
|MethodBeingCompiledName|win: UnicodeString|Nazwa metody, która jest kompilowana.|  
|MethodBeingCompiledNameSignature|win: UnicodeString|Sygnatura metody, która jest kompilowana.|  
|CallerNamespace|win: UnicodeString|Przestrzeń nazw metody kompilator JIT próbuje wygenerować kod dla.|  
|Element wywołujący|win: UnicodeString|Nazwa metody, dla której kompilator próbuje wygenerować kod.|  
|CallerNameSignature|win: UnicodeString|Podpis dla obiektu wywołującego.|  
|CalleeNamespace|win: UnicodeString|Przestrzeń nazw wywoływanego elementu.|  
|Obiekt wywoływany|win: UnicodeString|Metoda, którą kompilator próbuje wywołać (nie generuje wywołania do).|  
|CalleeNameSignature|win: UnicodeString|Podpis dla elementu wywoływanego.|  
|TailPrefix|win: wartość logiczna|Prefiks wywołania tail.|  
|FailReason|win: UnicodeString|Przyczyna wywołania tail nie powiodła się.|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
### <a name="methodjittailcallsucceeded-event"></a>Zdarzenie MethodJITTailCallSucceeded  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podniesienia zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITTracingKeyword`0x10|Verbose (5)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallSucceeded`|188|Wywołanie metody tail zakończyło się pomyślnie.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win: UnicodeString|Przestrzeń nazw metody, która jest kompilowana.|  
|MethodBeingCompiledName|win: UnicodeString|Nazwa metody, która jest kompilowana.|  
|MethodBeingCompiledNameSignature|win: UnicodeString|Sygnatura metody, która jest kompilowana.|  
|CallerNamespace|win: UnicodeString|Przestrzeń nazw metody kompilator JIT próbuje wygenerować kod dla.|  
|Element wywołujący|win: UnicodeString|Nazwa metody, dla której kompilator próbuje wygenerować kod.|  
|CallerNameSignature|win: UnicodeString|Podpis dla obiektu wywołującego.|  
|CalleeNamespace|win: UnicodeString|Przestrzeń nazw wywoływanego elementu.|  
|Obiekt wywoływany|win: UnicodeString|Metoda, którą kompilator próbuje wywołać (nie generuje wywołania do).|  
|CalleeNameSignature|win: UnicodeString|Podpis dla elementu wywoływanego.|  
|TailPrefix|win: wartość logiczna|Prefiks wywołania tail.|  
|TailCallType|win: UnicodeString|Typ wywołania tail.|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](clr-etw-events.md)
