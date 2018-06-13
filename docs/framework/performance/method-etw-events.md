---
title: Zdarzenia metod ETW
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, method events (CLR)
- method events [.NET Framework]
ms.assetid: 167a4459-bb6e-476c-9046-7920880f2bb5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 578aed02d5d44ae94763b6a254420a4976320f13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398108"
---
# <a name="method-etw-events"></a>Zdarzenia metod ETW
<a name="top"></a> Te zdarzenia zbierać informacje, które są specyficzne dla metody. Ładunek te zdarzenia jest wymagana do rozpoznawania symboli. Zdarzenia te zapewniają dodatkowo pomocne informacje takie jak liczba została wywołana metoda.  
  
 Wszystkie zdarzenia metod ma poziom "Informacyjny (4)". Wszystkie zdarzenia pełne metody mają poziom "Verbose (5)".  
  
 Wszystkie zdarzenia metod są wywoływane przez `JITKeyword` — słowo kluczowe (0x10) lub `NGenKeyword` — słowo kluczowe (0x20) w obszarze dostawcy środowiska uruchomieniowego lub `JitRundownKeyword` (0x10) lub `NGENRundownKeyword` (0x20) w obszarze stert dostawcy.  
  
 Zdarzenia metod CLR dalej są podzielone na następujące czynności:  
  
-   [Zdarzenia CLR — metoda](#clr_method_events)  
  
-   [Zdarzenia znacznika metod CLR](#clr_method_marker_events)  
  
-   [Zdarzenia pełne CLR — metoda](#clr_method_verbose_events)  
  
-   [Zdarzenie MethodJittingStarted](#methodjittingstarted_event)  
  
<a name="clr_method_events"></a>   
## <a name="clr-method-events"></a>Zdarzenia CLR — metoda  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITKeyword` dostawcy środowiska uruchomieniowego (0x10)|Komunikat informacyjny (4)|  
|`NGenKeyword` dostawcy środowiska uruchomieniowego (0x20)|Komunikat informacyjny (4)|  
|`JitRundownKeyword` Dostawca stert (0x10)|Komunikat informacyjny (4)|  
|`NGENRundownKeyword` Dostawca stert (0x20)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`MethodLoad_V1`|136|Wywoływane, gdy metoda jest just-in-time załadowane (ładowanej przez JIT) lub załadowanie obrazu NGEN. Metody dynamiczne i rodzajowy nie należy używać tej wersji pod kątem obciążeń metody. JIT pomocników nigdy nie używaj tej wersji.|  
|`MethodUnLoad_V1`|137|Wywoływane, gdy moduł jest zwolniony, lub domeny aplikacji zostanie zniszczony. Metody dynamiczne nigdy nie używaj tej wersji dla zwalnia metody.|  
|`MethodDCStart_V1`|137|Wylicza metody podczas uwalniania rozpoczęcia.|  
|`MethodDCEnd_V1`|138|Wylicza metody podczas uwalniania zakończenia.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodID|Windows: UInt64|Unikatowy identyfikator metody. Dla metody pomocnicze JIT ta jest ustawiona na adres początkowy metody.|  
|ModuleID|Windows: UInt64|Identyfikator modułu, do którego ta metoda należy (0 oznacza pomocników JIT).|  
|MethodStartAddress|Windows: UInt64|Początkowy adres metody.|  
|MethodSize|Windows: UInt32.|Rozmiar metody.|  
|MethodToken|Windows: UInt32.|0 dynamicznych metod i pomocników JIT.|  
|MethodFlags|Windows: UInt32.|0x1: metody dynamicznej.<br /><br /> 0x2: Metoda ogólna.<br /><br /> 0x4: metody JIT skompilowanego kodu (w przeciwnym razie NGEN obrazu macierzystego kodu).<br /><br /> 0x8: metoda pomocnika.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="clr_method_marker_events"></a>   
## <a name="clr-method-marker-events"></a>Zdarzenia znacznika metod CLR  
 Te zdarzenia są generowane tylko w przypadku zamknięcia dostawcy. One wskazują na końcu metody wyliczania podczas uruchamiania ani na końcu uwalniania. (To znaczy są wywoływane podczas `NGENRundownKeyword`, `JitRundownKeyword`, `LoaderRundownKeyword`, lub `AppDomainResourceManagementRundownKeyword` — słowo kluczowe jest włączona.)  
  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementRundownKeyword` Dostawca stert (0x800)|Komunikat informacyjny (4)|  
|`JitRundownKeyword` Dostawca stert (0x10)|Komunikat informacyjny (4)|  
|`NGENRundownKeyword` Dostawca stert (0x20)|Komunikat informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|----------------|  
|`DCStartInit_V1`|147|Wysyłane przed rozpoczęciem wyliczania podczas uwalniania rozpoczęcia.|  
|`DCStartComplete_V1`|145|Wysyłane na końcu wyliczenie podczas uwalniania rozpoczęcia.|  
|`DCEndInit_V1`|148|Wysyłane przed rozpoczęciem wyliczania podczas uwalniania zakończenia.|  
|`DCEndComplete_V1`|146|Wysyłane na końcu wyliczenie podczas uwalniania zakończenia.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="clr_method_verbose_events"></a>   
## <a name="clr-method-verbose-events"></a>Zdarzenia pełne CLR — metoda  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITKeyword` dostawcy środowiska uruchomieniowego (0x10)|Pełne (5)|  
|`NGenKeyword` dostawcy środowiska uruchomieniowego (0x20)|Pełne (5)|  
|`JitRundownKeyword` Dostawca stert (0x10)|Pełne (5)|  
|`NGENRundownKeyword` Dostawca stert (0x20)|Pełne (5)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`MethodLoadVerbose_V1`|143|Wywoływane, gdy metoda jest ładowany JIT lub załadowanie obrazu NGEN. Metody dynamiczne i rodzajowy zawsze używać tej wersji w przypadku obciążeń — metoda. Pomocnicy JIT zawsze używać tej wersji.|  
|`MethodUnLoadVerbose_V1`|144|Wywoływane, gdy zostanie zniszczony metody dynamicznej, moduł jest zwolniony lub domeny aplikacji zostanie zniszczony. Metody dynamiczne zawsze używaj metoda zwalnia tej wersji.|  
|`MethodDCStartVerbose_V1`|141|Wylicza metody podczas uwalniania rozpoczęcia.|  
|`MethodDCEndVerbose_V1`|142|Wylicza metody podczas uwalniania zakończenia.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodID|Windows: UInt64|Unikatowy identyfikator metody. Dla metody pomocnicze JIT należy ustawić adres początkowy metody.|  
|ModuleID|Windows: UInt64|Identyfikator modułu, do którego ta metoda należy (0 oznacza pomocników JIT).|  
|MethodStartAddress|Windows: UInt64|Adres początkowy.|  
|MethodSize|Windows: UInt32.|Długość metody.|  
|MethodToken|Windows: UInt32.|0 dynamicznych metod i pomocników JIT.|  
|MethodFlags|Windows: UInt32.|0x1: metody dynamicznej.<br /><br /> 0x2: Metoda ogólna.<br /><br /> 0x4: Metoda kompilacji JIT (w przeciwnym razie został wygenerowany przez NGen.exe)<br /><br /> 0x8: metoda pomocnika.|  
|MethodNameSpace|Windows: UnicodeString|Nazwa pełnej przestrzeni nazw skojarzonego z metodą.|  
|MethodName|Windows: UnicodeString|Pełne nazwy klas skojarzonego z metodą.|  
|MethodSignature|Windows: UnicodeString|Podpis metody (rozdzielana przecinkami lista nazw typu).|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="methodjittingstarted_event"></a>   
## <a name="methodjittingstarted-event"></a>Zdarzenie MethodJittingStarted  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`JITKeyword` dostawcy środowiska uruchomieniowego (0x10)|Pełne (5)|  
|`NGenKeyword` dostawcy środowiska uruchomieniowego (0x20)|Pełne (5)|  
|`JitRundownKeyword` Dostawca stert (0x10)|Pełne (5)|  
|`NGENRundownKeyword` Dostawca stert (0x20)|Pełne (5)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Opis|  
|-----------|--------------|-----------------|  
|`MethodJittingStarted`|145|Wywoływane, gdy metody są kompilowane JIT.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|MethodID|Windows: UInt64|Unikatowy identyfikator metody.|  
|ModuleID|Windows: UInt64|Identyfikator modułu, do którego należy ta metoda.|  
|MethodToken|Windows: UInt32.|0 dynamicznych metod i pomocników JIT.|  
|MethodILSize|Windows: UInt32.|Rozmiar Microsoft język pośredni (MSIL) metodę, która jest w trakcie kompilacji JIT.|  
|MethodNameSpace|Windows: UnicodeString|Pełne nazwy klas skojarzonego z metodą.|  
|MethodName|Windows: UnicodeString|Nazwa metody.|  
|MethodSignature|Windows: UnicodeString|Podpis metody (rozdzielana przecinkami lista nazw typu).|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
