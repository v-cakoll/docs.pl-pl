---
title: "Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a93e8cc1ab0b7488f920b556d2073d2813c3b7a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>Zdarzenia ETW monitorowania zasobów domen aplikacji (ARM)
<a name="top"></a>Zdarzenia te zawierają szczegółowe informacje diagnostyczne o stanie domeny aplikacji. Można użyć tych zdarzeń lub użyć zasobów domen aplikacji (ARM) funkcji monitorowania w celu uzyskania tych samych informacji.  
  
 Ta kategoria obejmuje następujące zdarzenia:  
  
-   [ThreadCreated zdarzeń](#threadcreated_event)  
  
-   [Zdarzenie AppDomainMemAllocated](#appdomainmemallocated_event)  
  
-   [Zdarzenie AppDomainMemSurvived](#appdomainmemsurvived_event)  
  
-   [Zdarzenie ThreadAppDomainEnter](#threadappdomainenter_event)  
  
-   [Zdarzenie ThreadTerminated](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a>ThreadCreated zdarzeń  
 To zdarzenie powstaje w obszarze dostawcy stert jako `ThreadDC` (w obszarze `AppDomainResourceManagementRundownKeyword` — słowo kluczowe). Jest to tylko zdarzenia, które jest wywoływane w obszarze stert dostawcy w tej kategorii.  
  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
|`ThreadingKeyword`(0x10000)|Informational(4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|85|Wątek został utworzony dla domeny aplikacji.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Identyfikator wątku|Windows: UInt64|Identyfikator wątku, który został utworzony.|  
|AppDomainID|Windows: UInt64|Identyfikator domeny aplikacji dla wątku, który jest raportowany działania.|  
|Flagi|Windows: UInt32.|Wątek flagi tworzenia.|  
|ManagedThreadIndex|Windows: UInt32.|Zarządzane indeks wątku, który został utworzony.|  
|Elementu OSThreadID|Windows: UInt32.|System operacyjny identyfikator wątku, który został utworzony.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a>Zdarzenie AppDomainMemAllocated  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|83|Co 4 MB pamięci (około) jest przydzielane w domenie aplikacji.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AppDomainID|Windows: UInt64|Identyfikator domeny aplikacji, dla którego zasobu jest raportowany użycia.|  
|Przydzielone|Windows: UInt64|Całkowita liczba bajtów przydzielonych w tej domenie aplikacji, ponieważ domena aplikacji została utworzona (liczba zwolnionych pamięci nie jest odejmowany).|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a>Zdarzenie AppDomainMemSurvived  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|84|Każdy wyrzucanie elementów bezużytecznych została zakończona.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|AppDomainID|Windows: UInt64|Identyfikator domeny, dla którego zasobu jest raportowany użycia.|  
|Udało się przetrwać|Windows: UInt64|Liczba bajtów, który udało przetrwać od ostatniego zebrania i które są znane przez tej domeny aplikacji. Ta liczba jest dokładne i kompletne po pełnej kolekcji, ale mogą być niekompletne po pobraniu tymczasowych.|  
|ProcessSurvived|Windows: UInt64|Całkowita liczba bajtów, które udało przetrwać od ostatniego zebrania. Po pełnej kolekcji ta liczba reprezentuje liczbę bajtów zablokowany na żywo w zarządzanych stosów. Po pobraniu tymczasowych ta liczba reprezentuje liczbę bajtów przechowywać na żywo w generacje tymczasowych.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a>Zdarzenie ThreadAppDomainEnter  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
|`ThreadingKeyword`(0x10000)|Informational(4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|87|Wątek przechodzi domeny aplikacji.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Identyfikator wątku|Windows: UInt64|Identyfikator wątku.|  
|AppDomainID|Windows: UInt64|Identyfikator domeny aplikacji.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a>Zdarzenie ThreadTerminated  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziom.  
  
|Słowo kluczowe wywołaniem zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword`(0x800)|Informational(4)|  
|`ThreadingKeyword`(0x10000)|Informational(4)|  
  
 W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|86|Zakończenie wątku.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia:  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|Identyfikator wątku|Windows: UInt64|Identyfikator wątku.|  
|AppDomainID|Windows: UInt64|Identyfikator domeny aplikacji.|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
