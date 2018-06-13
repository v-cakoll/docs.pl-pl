---
title: Zdarzenia ETW śledzenia JIT
ms.date: 03/30/2017
helpviewer_keywords:
- JIT tracing events [.NET Framework]
- ETW, JIT tracing events (CLR)
ms.assetid: 926adde2-c123-452e-bf4f-4b977bf06ffb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aeb0415395a59e59b4d5dc78c11d8b8f0902bad8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397562"
---
# <a name="jit-tracing-etw-events"></a>Zdarzenia ETW śledzenia JIT
<a name="top"></a> Te zdarzenia zbierać informacje dotyczące powodzenia lub niepowodzenia just-in-time (JIT) ze śródwierszowaniem i wywołania tail JIT.  
  
 Zdarzenia śledzenia JIT składają się z następujących dwóch kategorii:  
  
-   [JIT ze Śródwierszowaniem zdarzeń](#jit_inlining_events)  
  
-   [Zdarzenia wywołania Tail JIT](#jit_tail_call_events)  
  
<a name="jit_inlining_events"></a>   
## <a name="jit-inlining-events"></a>JIT ze Śródwierszowaniem zdarzeń  
  
### <a name="methodjitinliningfailed-event"></a>Zdarzenie MethodJitInliningFailed  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Pełne (5)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`MethodJitInliningFailed`|186|Ze śródwierszowaniem JIT nie powiodła się.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Windows: UnicodeString|Namespace — metoda, która jest kompilowany.|  
|MethodBeingCompiledName|Windows: UnicodeString|Nazwa metody, która jest kompilowany.|  
|MethodBeingCompiledNameSignature|Windows: UnicodeString|Podpis metody, która jest kompilowany.|  
|InlinerNamespace|Windows: UnicodeString|Przestrzeń nazw metody przy użyciu kompilatora JIT próbuje wygenerować kod.|  
|InlinerName|Windows: UnicodeString|Nazwa metody próbuje wygenerować kod dla kompilatora. To może nie być taka sama jak `MethodBeingCompiledName` Jeśli kompilator próbuje kodu wbudowanego w `MethodBeingCompiledName` zamiast generowania wywołania `InlinerName`.|  
|InlinerNameSignature|Windows: UnicodeString|Podpis dla inliner.|  
|InlineeNamespace|Windows: UnicodeString|Przestrzeń nazw przed wstawianiem do treści.|  
|InlineeName|Windows: UnicodeString|Metoda kompilator próbuje wbudowany (nie Generuj wywołania).|  
|InlineeNameSignature|Windows: UnicodeString|Podpis dla przed wstawianiem do treści.|  
|FailAlways|Windows: wartość logiczna|Wskazówkę kompilatora JIT to ze śródwierszowaniem zawsze kończy się niepowodzeniem przed wstawianiem do treści.|  
|FailReason|Windows: UnicodeString|INLINE_NEVER oznacza, że poprzednia próba ze śródwierszowaniem ustalić tego ze śródwierszowaniem zostanie nigdy nie powiodła się dla innego powodu; tekst, w przeciwnym razie dowolnych.|  
|ClrInstanceID|Windows: UnicodeString|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
### <a name="methodjitinliningsucceeded-event"></a>Zdarzenie MethodJitInliningSucceeded  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Pełne (5)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`MethodJitInliningSucceeded`|185|Metoda ze śródwierszowaniem zakończyło się pomyślnie.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Windows: UnicodeString|Przestrzeń nazw metody, która jest kompilowany.|  
|MethodBeingCompiledName|Windows: UnicodeString|Nazwa metody, która jest jest kompilowana.|  
|MethodBeingCompiledNameSignature|Windows: UnicodeString|Podpis metody jest kompilowany.|  
|InlinerNamespace|Windows: UnicodeString|Przestrzeń nazw metody przy użyciu kompilatora JIT próbuje wygenerować kod.|  
|InlinerName|Windows: UnicodeString|Nazwa metody próbuje wygenerować kod dla kompilatora. To może nie być taka sama jak `MethodBeingCompiledName` Jeśli kompilator próbuje kodu wbudowanego w `MethodBeingCompiledName` zamiast generowania wywołania `InlinerName`.|  
|InlinerNameSignature|Windows: UnicodeString|Podpis dla inliner.|  
|InlineeNamespace|Windows: UnicodeString|Przestrzeń nazw przed wstawianiem do treści.|  
|InlineeName|Windows: UnicodeString|Metoda kompilator próbuje wbudowany (nie Generuj wywołania).|  
|InlineeNameSignature|Windows: UnicodeString|Podpis dla przed wstawianiem do treści.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="jit_tail_call_events"></a>   
## <a name="jit-tail-call-events"></a>Zdarzenia wywołania Tail JIT  
  
### <a name="methodjittailcallfailed-event"></a>Zdarzenie MethodJITTailCallFailed  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Pełne (5)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallFailed`|189|Metoda wywołania tail nie powiodło się.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Windows: UnicodeString|Namespace — metoda, która jest kompilowany.|  
|MethodBeingCompiledName|Windows: UnicodeString|Nazwa metody, która jest kompilowany.|  
|MethodBeingCompiledNameSignature|Windows: UnicodeString|Podpis metody, która jest kompilowany.|  
|CallerNamespace|Windows: UnicodeString|Przestrzeń nazw metody przy użyciu kompilatora JIT próbuje wygenerować kod.|  
|CallerName|Windows: UnicodeString|Nazwa metody próbuje wygenerować kod dla kompilatora.|  
|CallerNameSignature|Windows: UnicodeString|Podpis dla obiekt wywołujący.|  
|CalleeNamespace|Windows: UnicodeString|Przestrzeń nazw wywoływany.|  
|CalleeName|Windows: UnicodeString|Metoda kompilator podejmuje próbę wywołania tail (nie Generuj wywołania).|  
|CalleeNameSignature|Windows: UnicodeString|Podpis dla wywoływany.|  
|TailPrefix|Windows: wartość logiczna|Prefiks dla wywołania tail|  
|FailReason|Windows: UnicodeString|Nie powiodło się z powodu wywołania tail.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
### <a name="methodjittailcallsucceeded-event"></a>Zdarzenie MethodJITTailCallSucceeded  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|Pełne (5)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallSucceeded`|188|Metoda wywołania tail zakończyło się pomyślnie.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|Windows: UnicodeString|Namespace — metoda, która jest kompilowany.|  
|MethodBeingCompiledName|Windows: UnicodeString|Nazwa metody, która jest kompilowany.|  
|MethodBeingCompiledNameSignature|Windows: UnicodeString|Podpis metody, która jest kompilowany.|  
|CallerNamespace|Windows: UnicodeString|Przestrzeń nazw metody przy użyciu kompilatora JIT próbuje wygenerować kod.|  
|CallerName|Windows: UnicodeString|Nazwa metody próbuje wygenerować kod dla kompilatora.|  
|CallerNameSignature|Windows: UnicodeString|Podpis dla obiekt wywołujący.|  
|CalleeNamespace|Windows: UnicodeString|Przestrzeń nazw wywoływany.|  
|CalleeName|Windows: UnicodeString|Metoda kompilator podejmuje próbę wywołania tail (nie Generuj wywołania).|  
|CalleeNameSignature|Windows: UnicodeString|Podpis dla wywoływany.|  
|TailPrefix|Windows: wartość logiczna|Prefiks dla wywołania tail.|  
|TailCallType|Windows: UnicodeString|Typ wywołania tail.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
