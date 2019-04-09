---
title: Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bb2b0dd95877fc6492f6d23a19c14688cd78f7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133825"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)
<a name="top"></a> Zdarzenia te zawierają szczegółowe informacje diagnostyczne o stanie domeny aplikacji. Można użyć tych zdarzeń, lub użyć zasobów domen aplikacji (ARM) funkcji monitorowania można uzyskać te same informacje.  
  
 Ta kategoria obejmuje następujące zdarzenia:  
  
-   [Threadcreated — zdarzenie](#threadcreated_event)  
  
-   [Zdarzenie AppDomainMemAllocated](#appdomainmemallocated_event)  
  
-   [Zdarzenie AppDomainMemSurvived](#appdomainmemsurvived_event)  
  
-   [Zdarzenie ThreadAppDomainEnter](#threadappdomainenter_event)  
  
-   [Zdarzenie ThreadTerminated](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a>Threadcreated — zdarzenie  
 To zdarzenie jest także inicjowane w obszarze dostawcy podsumowań jako `ThreadDC` (w obszarze `AppDomainResourceManagementRundownKeyword` — słowo kluczowe). Jest to jedyne zdarzenie, które jest wywoływane w obszarze dostawcy podsumowań w tej kategorii.  
  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
|`ThreadingKeyword` (0x10000)|Informational(4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|85|Wątek został utworzony dla domeny aplikacji.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|Identyfikator wątku, który został utworzony.|  
|AppDomainID|win:UInt64|Identyfikator wątku, który jest zgłaszany działania domeny aplikacji.|  
|Flagi|win: UInt32.|Wątek flagi tworzenia.|  
|ManagedThreadIndex|win: UInt32.|Zarządzane indeks wątku, który został utworzony.|  
|Elementu OSThreadID|win: UInt32.|Identyfikator wątku, który został utworzony w system operacyjny.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a>Zdarzenie AppDomainMemAllocated  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|83|Co 4 MB pamięci (w przybliżeniu) jest przydzielany w domenie aplikacji.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|Identyfikator domeny aplikacji do zasobu, który jest zgłaszany użycia.|  
|przydzielona|win:UInt64|Całkowita liczba bajtów przydzielonych w tej domenie aplikacji, od momentu utworzenia domeny aplikacji (ilość zwolnionej pamięci nie jest odejmowany).|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a>Zdarzenie AppDomainMemSurvived  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|84|Każdy wyrzucania elementów bezużytecznych zostało zakończone.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|Identyfikator domeny dla zasobu, który jest zgłaszany użycia.|  
|Przetrwały|win:UInt64|Liczba bajtów, które przetrwały od ostatniego zebrania i które są znane przez tej domeny aplikacji. Ta liczba jest dokładne i kompletne po pełnej kolekcji, ale mogą być niekompletne po pobraniu tymczasowych.|  
|ProcessSurvived|win:UInt64|Całkowita liczba bajtów, które przetrwały od ostatniego zebrania. Po pełnego ta liczba przedstawia liczbę bajtów przechowywanych na żywo w zarządzanej sterty. Po pobraniu tymczasowych ten numer reprezentuje liczbę bajtów przechowywanych na żywo w generacje efemeryczne.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a>Zdarzenie ThreadAppDomainEnter  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
|`ThreadingKeyword` (0x10000)|Informational(4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|87|Wątek wchodzi domeny aplikacji.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|Identyfikator wątku.|  
|AppDomainID|win:UInt64|Identyfikator domeny aplikacji.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a>Zdarzenie ThreadTerminated  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informational(4)|  
|`ThreadingKeyword` (0x10000)|Informational(4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|86|Wątek kończy działanie.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia:  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|Identyfikator wątku.|  
|AppDomainID|win:UInt64|Identyfikator domeny aplikacji.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia ETW CLR](../../../docs/framework/performance/clr-etw-events.md)
