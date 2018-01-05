---
title: AppDomainInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed5053dd69628a9f5ff7318ce7fe772f42de6e24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="appdomaininfo"></a>AppDomainInfo
Informacje o domenie aplikacji  
  
## <a name="syntax"></a>Składnia  
  
```  
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa AppDomainInfo nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa AppDomainInfo ma następujące właściwości:  
  
### <a name="appdomainid"></a>AppDomainId  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Identyfikator domeny aplikacji.  
  
### <a name="isdefault"></a>Wartość  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wskazuje, czy domena aplikacji jest domyślną domeną.  
  
### <a name="logmalformedmessages"></a>LogMalformedMessages  
 Typ danych: wartość logiczna  
  
 Dostęp typu: odczytu/zapisu  
  
 Wartość określająca, czy wadliwe komunikaty są rejestrowane.  
  
### <a name="logmessagesatservicelevel"></a>LogMessagesAtServiceLevel  
 Typ danych: wartość logiczna  
  
 Dostęp typu: odczytu/zapisu  
  
 Wartość, która określa, czy komunikaty są śledzone na poziomie usługi (przed zaszyfrowaniem i transformacjami związanymi z transportem).  
  
### <a name="logmessagesattransportlevel"></a>LogMessagesAtTransportLevel  
 Typ danych: wartość logiczna  
  
 Dostęp typu: odczytu/zapisu  
  
 Wartość, która określa, czy komunikaty są śledzone na poziomie transportu.  
  
### <a name="messageloggingtracelisteners"></a>MessageLoggingTraceListeners  
 Typ danych: TraceListener tablicy  
  
 Dostęp typu: tylko do odczytu  
  
 Kolekcja obiektów nasłuchujących śledzenia System.Wmi.MessageLogging źródła śledzenia.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Nazwa elementu appdomain.  
  
### <a name="performancecounters"></a>liczniki wydajności  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Zakres aktywnych liczników wydajności w domenie aplikacji.  
  
### <a name="processid"></a>Identyfikator procesu  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Identyfikator procesu.  
  
### <a name="serviceconfigpath"></a>ServiceConfigPath  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Ścieżka do konfiguracji usługi.  
  
### <a name="tracelevel"></a>TraceLevel  
 Typ danych: ciąg  
  
 Dostęp typu: odczytu/zapisu  
  
 Poziom śledzenia źródła śledzenia System.Wmi.  
  
### <a name="servicemodeltracelisteners"></a>ServiceModelTraceListeners  
 Typ danych: TraceListener tablicy  
  
 Dostęp typu: tylko do odczytu  
  
 Kolekcja obiektów nasłuchujących ze źródła System.ServiceModel.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|
