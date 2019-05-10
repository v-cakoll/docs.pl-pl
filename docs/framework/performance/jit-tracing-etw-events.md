---
title: Zdarzenia ETW śledzenia JIT
ms.date: 03/30/2017
helpviewer_keywords:
- JIT tracing events [.NET Framework]
- ETW, JIT tracing events (CLR)
ms.assetid: 926adde2-c123-452e-bf4f-4b977bf06ffb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 07d84506a7c07bde09b3b46ea608b1874842c3ac
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616384"
---
# <a name="jit-tracing-etw-events"></a>Zdarzenia ETW śledzenia JIT
<a name="top"></a> Te zdarzenia zbierać informacje dotyczące powodzenia lub niepowodzenia, just-in-time (JIT) wbudowanie i wywołania tail JIT.  
  
 Zdarzenia śledzenia JIT składają się z następujących dwóch kategorii:  
  
- [JIT wbudowanie zdarzenia](#jit_inlining_events)  
  
- [Zdarzenia wywołania Tail JIT](#jit_tail_call_events)  
  
<a name="jit_inlining_events"></a>   
## <a name="jit-inlining-events"></a>JIT wbudowanie zdarzenia  
  
### <a name="methodjitinliningfailed-event"></a>Zdarzenie MethodJitInliningFailed  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Pełne (5)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`MethodJitInliningFailed`|186|Wbudowanie JIT nie powiodło się.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Namespace metodę, która jest kompilowany.|  
|MethodBeingCompiledName|win:UnicodeString|Nazwa metody, która jest kompilowany.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Podpis metody, która jest kompilowany.|  
|InlinerNamespace|win:UnicodeString|Przestrzeń nazw metody kompilator JIT próbuje generowania kodu.|  
|InlinerName|win:UnicodeString|Nazwa metody, kompilator podejmuje próbę generowania kodu. Może to nie być taka sama jak `MethodBeingCompiledName` Jeśli kompilator próbuje wbudowany kod z gałęzią `MethodBeingCompiledName` zamiast generować wywołania `InlinerName`.|  
|InlinerNameSignature|win:UnicodeString|Podpis dla inliner.|  
|InlineeNamespace|win:UnicodeString|Przestrzeń nazw przed wstawianiem do treści.|  
|InlineeName|win:UnicodeString|Metoda próbuje kompilator wbudował (nie generuje wywołanie).|  
|InlineeNameSignature|win:UnicodeString|Podpis dla przed wstawianiem do treści.|  
|FailAlways|win: atrybut typu wartość logiczna|Wskazówkę oznacza wbudowanie kompilator JIT zawsze zakończy się niepowodzeniem przed wstawianiem do treści.|  
|FailReason|win:UnicodeString|INLINE_NEVER oznacza, że poprzednia próba wbudowanie określić tego wbudowanie będą nigdy nie powiedzie się innego powodu; tekst, w przeciwnym razie dowolnej postaci.|  
|ClrInstanceID|win:UnicodeString|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
### <a name="methodjitinliningsucceeded-event"></a>MethodJitInliningSucceeded Event  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Pełne (5)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`MethodJitInliningSucceeded`|185|Wbudowanie metody powiodło się.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Przestrzeń nazw metody, która jest kompilowany.|  
|MethodBeingCompiledName|win:UnicodeString|Nazwa jest metoda, która jest kompilowana.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Podpis metody, która jest kompilowany.|  
|InlinerNamespace|win:UnicodeString|Przestrzeń nazw metody kompilator JIT próbuje generowania kodu.|  
|InlinerName|win:UnicodeString|Nazwa metody, kompilator podejmuje próbę generowania kodu. Może to nie być taka sama jak `MethodBeingCompiledName` Jeśli kompilator próbuje wbudowany kod z gałęzią `MethodBeingCompiledName` zamiast generować wywołania `InlinerName`.|  
|InlinerNameSignature|win:UnicodeString|Podpis dla inliner.|  
|InlineeNamespace|win:UnicodeString|Przestrzeń nazw przed wstawianiem do treści.|  
|InlineeName|win:UnicodeString|Metoda próbuje kompilator wbudował (nie generuje wywołanie).|  
|InlineeNameSignature|win:UnicodeString|Podpis dla przed wstawianiem do treści.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="jit_tail_call_events"></a>   
## <a name="jit-tail-call-events"></a>Zdarzenia wywołania Tail JIT  
  
### <a name="methodjittailcallfailed-event"></a>Zdarzenie MethodJITTailCallFailed  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Pełne (5)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallFailed`|189|Wywołanie tail metody nie powiodło się.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Namespace metodę, która jest kompilowany.|  
|MethodBeingCompiledName|win:UnicodeString|Nazwa metody, która jest kompilowany.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Podpis metody, która jest kompilowany.|  
|CallerNamespace|win:UnicodeString|Przestrzeń nazw metody kompilator JIT próbuje generowania kodu.|  
|CallerName|win:UnicodeString|Nazwa metody, kompilator podejmuje próbę generowania kodu.|  
|CallerNameSignature|win:UnicodeString|Podpis dla obiektu wywołującego.|  
|CalleeNamespace|win:UnicodeString|Przestrzeń nazw obiekt wywoływany.|  
|CalleeName|win:UnicodeString|Metoda kompilator podejmuje próbę wywołania tail (nie generuje wywołanie).|  
|CalleeNameSignature|win:UnicodeString|Podpis dla / / wywoływany.|  
|TailPrefix|win: atrybut typu wartość logiczna|Prefiks dla wywołania tail|  
|FailReason|win:UnicodeString|Przyczyna wywołanie tail nie powiodło się.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
### <a name="methodjittailcallsucceeded-event"></a>Zdarzenie MethodJITTailCallSucceeded  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Pełne (5)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallSucceeded`|188|Wywołanie tail metody powiodło się.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|Namespace metodę, która jest kompilowany.|  
|MethodBeingCompiledName|win:UnicodeString|Nazwa metody, która jest kompilowany.|  
|MethodBeingCompiledNameSignature|win:UnicodeString|Podpis metody, która jest kompilowany.|  
|CallerNamespace|win:UnicodeString|Przestrzeń nazw metody kompilator JIT próbuje generowania kodu.|  
|CallerName|win:UnicodeString|Nazwa metody, kompilator podejmuje próbę generowania kodu.|  
|CallerNameSignature|win:UnicodeString|Podpis dla obiektu wywołującego.|  
|CalleeNamespace|win:UnicodeString|Przestrzeń nazw obiekt wywoływany.|  
|CalleeName|win:UnicodeString|Metoda kompilator podejmuje próbę wywołania tail (nie generuje wywołanie).|  
|CalleeNameSignature|win:UnicodeString|Podpis dla / / wywoływany.|  
|TailPrefix|win: atrybut typu wartość logiczna|Prefiks dla wywołania tail.|  
|TailCallType|win:UnicodeString|Typ wywołanie tail.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
