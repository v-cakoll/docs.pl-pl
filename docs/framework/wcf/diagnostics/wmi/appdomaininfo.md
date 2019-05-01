---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 0b7f8aadbd9a9dfcdd33fc65be3a5a41ea95f5be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964258"
---
# <a name="appdomaininfo"></a>AppDomainInfo
Informacje o domenie aplikacji  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
  
 Typ dostępu: tylko do odczytu  
  
 Identyfikator elementu appdomain.  
  
### <a name="isdefault"></a>IsDefault  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wskazuje, czy element appdomain jest domyślnej domeny aplikacji.  
  
### <a name="logmalformedmessages"></a>LogMalformedMessages  
 Typ danych: wartość logiczna  
  
 Typ dostępu: Odczyt/zapis  
  
 Wartość, która określa, czy wadliwe komunikaty są rejestrowane.  
  
### <a name="logmessagesatservicelevel"></a>LogMessagesAtServiceLevel  
 Typ danych: wartość logiczna  
  
 Typ dostępu: Odczyt/zapis  
  
 Wartość, która określa, czy komunikaty są śledzone na poziomie usługi (przed zaszyfrowaniem i transformacjami związanymi z transportem).  
  
### <a name="logmessagesattransportlevel"></a>LogMessagesAtTransportLevel  
 Typ danych: wartość logiczna  
  
 Typ dostępu: Odczyt/zapis  
  
 Wartość, która określa, czy komunikaty są śledzone na poziomie transportu.  
  
### <a name="messageloggingtracelisteners"></a>MessageLoggingTraceListeners  
 Typ danych: Tablica zdarzeń TraceListener  
  
 Typ dostępu: tylko do odczytu  
  
 Kolekcja obiektów nasłuchujących śledzenia System.Wmi.MessageLogging źródła śledzenia.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Nazwa domeny aplikacji.  
  
### <a name="performancecounters"></a>Liczniki wydajności  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Zakres aktywnych liczników wydajności w domenie aplikacji.  
  
### <a name="processid"></a>Identyfikator procesu  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Identyfikator procesu.  
  
### <a name="serviceconfigpath"></a>ServiceConfigPath  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Ścieżka do konfiguracji usługi.  
  
### <a name="tracelevel"></a>TraceLevel  
 Typ danych: ciąg  
  
 Typ dostępu: Odczyt/zapis  
  
 Poziom śledzenia System.Wmi źródła śledzenia.  
  
### <a name="servicemodeltracelisteners"></a>ServiceModelTraceListeners  
 Typ danych: Tablica zdarzeń TraceListener  
  
 Typ dostępu: tylko do odczytu  
  
 Kolekcja obiektów nasłuchujących ze źródła śledzenia System.ServiceModel.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|
