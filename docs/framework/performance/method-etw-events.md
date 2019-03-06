---
title: Zdarzenia metod ETW
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, method events (CLR)
- method events [.NET Framework]
ms.assetid: 167a4459-bb6e-476c-9046-7920880f2bb5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c7969c0a3f5f828f1a1c0d4f33b82881130c6e15
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370166"
---
# <a name="method-etw-events"></a>Zdarzenia metod ETW

<a name="top"></a> Te zdarzenia zbierać informacje, które są specyficzne dla metody. Ładunku zdarzenia jest wymagany dla rozpoznawania symboli. Ponadto te zdarzenia zawierają przydatne informacje takie jak liczba, że metoda została wywołana.

Wszystkie zdarzenia metod ma poziom "Informacyjne (4)". Wszystkie zdarzenia pełne metoda ma poziom "Pełny (5)".

Wszystkie zdarzenia metody są wywoływane przez `JITKeyword` — słowo kluczowe (0x10) lub `NGenKeyword` — słowo kluczowe (0x20), w obszarze dostawcy środowiska uruchomieniowego lub `JitRundownKeyword` (0x10) lub `NGENRundownKeyword` (0x20) w obszarze dostawcy podsumowań.

Zdarzenia metod środowiska CLR jest podzielona na następujące:

- [Zdarzenia metod CLR](#clr_method_events)

- [CLR — metoda znacznik zdarzenia](#clr_method_marker_events)

- [Zdarzenia pełne CLR — metoda](#clr_method_verbose_events)

- [Zdarzenie MethodJittingStarted](#methodjittingstarted_event)

<a name="clr_method_events"></a>

## <a name="clr-method-events"></a>Zdarzenia metod CLR

W poniższej tabeli przedstawiono — słowo kluczowe i poziomu. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)

|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|
|-----------------------------------|-----------|
|`JITKeyword` Dostawca środowiska uruchomieniowego (0x10)|Komunikat informacyjny (4)|
|`NGenKeyword` Dostawca środowiska uruchomieniowego (0x20)|Komunikat informacyjny (4)|
|`JitRundownKeyword` Dostawca podsumowań (0x10)|Komunikat informacyjny (4)|
|`NGENRundownKeyword` Dostawca podsumowań (0x20)|Komunikat informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu.

|Zdarzenie|Identyfikator zdarzenia|Opis|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|136|Wywoływane, gdy metoda jest just-in-time załadowane (załadowany JIT) lub załadowaniu obrazów NGEN. Metody dynamiczne i ogólny nie należy używać tej wersji metoda obciążeń roboczych. Pomocnicy JIT nigdy nie używaj tej wersji.|
|`MethodUnLoad_V1`|137|Wywoływane, gdy moduł jest zwolniony, lub zostanie zniszczony domeny aplikacji. Metody dynamiczne nigdy nie używaj tej wersji dla zwalnia metody.|
|`MethodDCStart_V1`|137|Wylicza metody podczas Początek podsumowania.|
|`MethodDCEnd_V1`|138|Wylicza metody podczas koniec podsumowania.|

W poniższej tabeli przedstawiono dane zdarzenia.

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|MethodID|win:UInt64|Unikatowy identyfikator metody. Dla metody pomocnika JIT to jest równa adres początkowy metody.|
|ModuleID|win:UInt64|Identyfikator modułu, do którego ta metoda należy (od 0 do pomocników JIT).|
|MethodStartAddress|win:UInt64|Początkowy adres metody.|
|MethodSize|win: UInt32.|Rozmiar metody.|
|MethodToken|win: UInt32.|0 w przypadku dynamicznych metod i pomocników JIT.|
|MethodFlags|win: UInt32.|0x1: Metoda dynamiczna.<br /><br /> 0x2: Metody rodzajowej.<br /><br /> 0x4: Metoda kod kompilowany dokładnie na czas (w przeciwnym razie NGEN obrazu natywnego kodu).<br /><br /> 0x8: Metoda pomocnika.|
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

[Powrót do początku](#top)

<a name="clr_method_marker_events"></a>

## <a name="clr-method-marker-events"></a>CLR — metoda znacznik zdarzenia

Te zdarzenia są wywoływane tylko w obszarze dostawcy podsumowań. One oznaczającego koniec metody wyliczania podczas rozpoczęcia lub zakończenia podsumowania. (Oznacza to, że są one inicjowane po `NGENRundownKeyword`, `JitRundownKeyword`, `LoaderRundownKeyword`, lub `AppDomainResourceManagementRundownKeyword` — słowo kluczowe jest włączony.)

W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.

|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|
|-----------------------------------|-----------|
|`AppDomainResourceManagementRundownKeyword` Dostawca podsumowań (0x800)|Komunikat informacyjny (4)|
|`JitRundownKeyword` Dostawca podsumowań (0x10)|Komunikat informacyjny (4)|
|`NGENRundownKeyword` Dostawca podsumowań (0x20)|Komunikat informacyjny (4)|

W poniższej tabeli przedstawiono informacje o zdarzeniu.

|Zdarzenie|Identyfikator zdarzenia|Opis|
|-----------|--------------|----------------|
|`DCStartInit_V1`|147|Wysłane przed rozpoczęciem wyliczania podczas Początek podsumowania.|
|`DCStartComplete_V1`|145|Wysyłane na koniec wyliczenia podczas Początek podsumowania.|
|`DCEndInit_V1`|148|Wysłane przed rozpoczęciem wyliczania podczas koniec podsumowania.|
|`DCEndComplete_V1`|146|Wysyłane na koniec wyliczenia podczas koniec podsumowania.|

W poniższej tabeli przedstawiono dane zdarzenia.

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

[Powrót do początku](#top)

<a name="clr_method_verbose_events"></a>

## <a name="clr-method-verbose-events"></a>Zdarzenia pełne CLR — metoda

W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.

|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|
|-----------------------------------|-----------|
|`JITKeyword` Dostawca środowiska uruchomieniowego (0x10)|Pełne (5)|
|`NGenKeyword` Dostawca środowiska uruchomieniowego (0x20)|Pełne (5)|
|`JitRundownKeyword` Dostawca podsumowań (0x10)|Pełne (5)|
|`NGENRundownKeyword` Dostawca podsumowań (0x20)|Pełne (5)|

W poniższej tabeli przedstawiono informacje o zdarzeniu.

|Zdarzenie|Identyfikator zdarzenia|Opis|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|143|Wywoływane, gdy metoda jest załadowana w trybie JIT lub załadowaniu obrazów NGEN. Metody dynamiczne i ogólny zawsze używaj tej wersji metoda obciążeń. Pomocnicy JIT zawsze używać tej wersji.|
|`MethodUnLoadVerbose_V1`|144|Wywoływane, gdy metoda dynamiczna jest niszczony, moduł jest zwalniana lub domeny aplikacji jest niszczona. Metody dynamiczne zawsze używaj tej wersji metoda zwalnia.|
|`MethodDCStartVerbose_V1`|141|Wylicza metody podczas Początek podsumowania.|
|`MethodDCEndVerbose_V1`|142|Wylicza metody podczas koniec podsumowania.|

W poniższej tabeli przedstawiono dane zdarzenia.

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|MethodID|win:UInt64|Unikatowy identyfikator metody. Ustaw adres początkowy metody dla metod pomocniczych JIT.|
|ModuleID|win:UInt64|Identyfikator modułu, do którego ta metoda należy (od 0 do pomocników JIT).|
|MethodStartAddress|win:UInt64|Adres początkowy.|
|MethodSize|win: UInt32.|Metoda długość.|
|MethodToken|win: UInt32.|0 w przypadku dynamicznych metod i pomocników JIT.|
|MethodFlags|win: UInt32.|0x1: Metoda dynamiczna.<br /><br /> 0x2: Metody rodzajowej.<br /><br /> 0x4: Metoda kompilowanego dokładnie na czas (w przeciwnym razie wygenerowane przez NGen.exe)<br /><br /> 0x8: Metoda pomocnika.|
|MethodNameSpace|win:UnicodeString|Nazwa przestrzeni nazw pełnej powiązany z metodą.|
|MethodName|win:UnicodeString|Pełna nazwa klasy powiązany z metodą.|
|MethodSignature|win:UnicodeString|Podpis metody (rozdzielana przecinkami lista nazw typu).|
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

[Powrót do początku](#top)

<a name="methodjittingstarted_event"></a>

## <a name="methodjittingstarted-event"></a>Zdarzenie MethodJittingStarted

W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.

|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|
|-----------------------------------|-----------|
|`JITKeyword` Dostawca środowiska uruchomieniowego (0x10)|Pełne (5)|
|`NGenKeyword` Dostawca środowiska uruchomieniowego (0x20)|Pełne (5)|
|`JitRundownKeyword` Dostawca podsumowań (0x10)|Pełne (5)|
|`NGENRundownKeyword` Dostawca podsumowań (0x20)|Pełne (5)|

W poniższej tabeli przedstawiono informacje o zdarzeniu.

|Zdarzenie|Identyfikator zdarzenia|Opis|
|-----------|--------------|-----------------|
|`MethodJittingStarted`|145|Wywoływane, gdy metoda jest kompilowany dokładnie na czas.|

W poniższej tabeli przedstawiono dane zdarzenia.

|Nazwa pola|Typ danych|Opis|
|----------------|---------------|-----------------|
|MethodID|win:UInt64|Unikatowy identyfikator metody.|
|ModuleID|win:UInt64|Identyfikator modułu, do której należy ta metoda.|
|MethodToken|win: UInt32.|0 w przypadku dynamicznych metod i pomocników JIT.|
|MethodILSize|win: UInt32.|Rozmiar języka Microsoft intermediate language (MSIL) metody, która jest kompilowany dokładnie na czas.|
|MethodNameSpace|win:UnicodeString|Pełna nazwa klasy powiązany z metodą.|
|MethodName|win:UnicodeString|Nazwa metody.|
|MethodSignature|win:UnicodeString|Podpis metody (rozdzielana przecinkami lista nazw typu).|
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|

## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
