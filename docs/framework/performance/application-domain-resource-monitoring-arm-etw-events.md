---
title: Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e4002ae248022a9e4380c79174109494b5e4ca
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046767"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)
<a name="top"></a>Te zdarzenia zapewniają szczegółowe informacje diagnostyczne o stanie domeny aplikacji. Możesz użyć tych zdarzeń lub użyć funkcji monitorowania zasobów domeny aplikacji (ARM), aby uzyskać te same informacje.  
  
 Ta kategoria obejmuje następujące zdarzenia:  
  
- [Zdarzenie ThreadCreated —](#threadcreated_event)  
  
- [Zdarzenie AppDomainMemAllocated](#appdomainmemallocated_event)  
  
- [Zdarzenie AppDomainMemSurvived](#appdomainmemsurvived_event)  
  
- [Zdarzenie ThreadAppDomainEnter](#threadappdomainenter_event)  
  
- [Zdarzenie ThreadTerminated](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a>Zdarzenie ThreadCreated —  
 To zdarzenie jest również zgłaszane w ramach dostawcy uwalniania `ThreadDC` jako ( `AppDomainResourceManagementRundownKeyword` pod słowem kluczowym). Jest to jedyne zdarzenie zgłaszane w ramach dostawcy uwalniania w tej kategorii.  
  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).  
  
|Słowo kluczowe do podniesienia zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informacyjny (4)|  
|`ThreadingKeyword`0x10000|Informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|85|Utworzono wątek dla domeny aplikacji.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ThreadID|win: UInt64|Identyfikator utworzonego wątku.|  
|AppDomainID|win: UInt64|Identyfikator domeny aplikacji, dla której jest zgłaszane działanie wątku.|  
|Flagi|win: UInt32|Flagi tworzenia wątku.|  
|ManagedThreadIndex|win: UInt32|Zarządzany indeks wątku, który został utworzony.|  
|OSThreadID|win: UInt32|Identyfikator systemu operacyjnego wątku, który został utworzony.|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a>Zdarzenie AppDomainMemAllocated  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podniesienia zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|83|Co 4 MB pamięci (w przybliżeniu) jest przypisywany w domenie aplikacji.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AppDomainID|win: UInt64|Identyfikator domeny aplikacji, dla której zgłaszane jest użycie zasobów.|  
|Rozdziela|win: UInt64|Całkowita liczba bajtów przydzielono w tej domenie aplikacji od momentu utworzenia domeny aplikacji (ilość zwolnionej pamięci nie jest odejmowana).|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a>Zdarzenie AppDomainMemSurvived  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podniesienia zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|84|Wszystkie wyrzucanie elementów bezużytecznych zostało zakończone.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AppDomainID|win: UInt64|Identyfikator domeny, dla której zgłaszane jest użycie zasobów.|  
|Ocalałe|win: UInt64|Liczba bajtów przeprowadzonych po ostatniej kolekcji i, które są znane przez tę domenę aplikacji. Ta liczba jest dokładna i kompletna po pełnej kolekcji, ale może być niekompletna po kolekcji tymczasowej.|  
|ProcessSurvived|win: UInt64|Całkowita liczba bajtów przeczytanych z ostatniej kolekcji. Po pełnej kolekcji ta liczba reprezentuje liczbę bajtów przechowywanych na żywo w zarządzanych stertach. Po zakończeniu zbierania danych tymczasowych ta liczba reprezentuje liczbę bajtów przechowywanych na żywo w generacjach tymczasowych.|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a>Zdarzenie ThreadAppDomainEnter  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podniesienia zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informacyjny (4)|  
|`ThreadingKeyword`0x10000|Informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|87|Wątek przechodzi do domeny aplikacji.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ThreadID|win: UInt64|Identyfikator wątku.|  
|AppDomainID|win: UInt64|Identyfikator domeny aplikacji.|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a>Zdarzenie ThreadTerminated  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podniesienia zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informacyjny (4)|  
|`ThreadingKeyword`0x10000|Informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|86|Wątek kończy działanie.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia:  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ThreadID|win: UInt64|Identyfikator wątku.|  
|AppDomainID|win: UInt64|Identyfikator domeny aplikacji.|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](clr-etw-events.md)
