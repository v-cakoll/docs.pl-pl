---
title: Zdarzenia ETW międzyoperacyjności
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09b2848619256a255cc27f0268d46e5e6db8cbe4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083611"
---
# <a name="interop-etw-events"></a>Zdarzenia ETW międzyoperacyjności
<a name="top"></a> Zdarzenia międzyoperacyjności przechwytywania informacji na temat generowania szkieletu intermediate language (MSIL) firmy Microsoft i buforowania.  
  
 Ta kategoria obejmuje następujące zdarzenia:  
  
-   [Zdarzenie ILStubGenerated](#ilstubgenerated_event)  
  
-   [ILStubCacheHit Event](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a>Zdarzenie ILStubGenerated  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informational(4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|88|Klasy zastępczej MSIL został wygenerowany.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ModuleID|win: UInt16.|Identyfikator modułu.|  
|StubMethodID|win:UInt64|Identyfikator metody klasy zastępczej.|  
|StubFlags|win:UInt64|Flagi dla wycinka:<br /><br /> 0x1 — interop wstecznego.<br /><br /> 0x2 — Usługa międzyoperacyjna modelu COM.<br /><br /> 0x4 - wycinku wygenerowanym przez NGen.exe.<br /><br /> 0x8 - delegata.<br /><br /> 0x10 - arrgument zmiennej.<br /><br /> 0x20 — niezarządzane / / wywoływany.|  
|ManagedInteropMethodToken|win: UInt32.|Token dla zarządzanej metody międzyoperacyjnego.|  
|ManagedInteropMethodNameSpace|win:UnicodeString|Przestrzeń nazw zarządzanych metoda międzyoperacyjna.|  
|ManagedInteropMethodName|win:UnicodeString|Nazwa zarządzaną metodą międzyoperacyjnego.|  
|ManagedInteropMethodSignature|win:UnicodeString|Podpis zarządzaną metodą międzyoperacyjnego.|  
|NativeMethodSignature|win:UnicodeString|Podpis metody natywnej.|  
|StubMethodSignature|win:UnicodeString|Podpis metody klasy zastępczej.|  
|StubMethodILCode|win:UnicodeString|Kod MSIL metody klasy zastępczej.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a>ILStubCacheHit Event  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`InteropKeyword` (0x2000)|Informational(4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|89|Uzyskał dostęp do pamięci podręcznej MSIL.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ModuleID|win: UInt16.|Identyfikator modułu.|  
|StubMethodID|win:UInt64|Identyfikator metody klasy zastępczej.|  
|ManagedInteropMethodToken|win: UInt32.|Token dla zarządzanej metody międzyoperacyjnego.|  
|ManagedInteropMethodNameSpace|win:UnicodeString|Przestrzeń nazw zarządzanych metoda międzyoperacyjna.|  
|ManagedInteropMethodName|win:UnicodeString|Nazwa zarządzaną metodą międzyoperacyjnego.|  
|ManagedInteropMethodSignature|win:UnicodeString|Podpis zarządzaną metodą międzyoperacyjnego.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia ETW CLR](../../../docs/framework/performance/clr-etw-events.md)
