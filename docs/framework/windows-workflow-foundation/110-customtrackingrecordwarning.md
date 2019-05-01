---
title: 110 — CustomTrackingRecordWarning
ms.date: 03/30/2017
ms.assetid: 3bc093de-be47-4ed0-983f-05b4246446fc
ms.openlocfilehash: 230e889c677ee83b2e71b128413b7107ec11dc2e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924140"
---
# <a name="110---customtrackingrecordwarning"></a>110 — CustomTrackingRecordWarning
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Id|110|  
|słowa kluczowe|UserEvents EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows podczas działania w ramach wystąpienie przepływu pracy emituje CustomTrackingRecord z ostrzeżeniem poziomu  
  
## <a name="message"></a>Komunikat  
 TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, nazwa = %4, ActivityName = %5, identyfikator działania = %6, ActivityInstanceId = %7, ActivityTypeName = %8, dane = %9, adnotacje = % 10, ProfileName = % 11  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Identyfikator wystąpienia przepływu pracy|  
|RecordNumber|xs:long|Numer sekwencyjny emitowany rekordu|  
|eventTime|xs:dateTime|Godzina w formacie UTC zdarzenia został wyemitowany|  
|Nazwa|xs:String|Nazwa CustomTrackingRecord|  
|ActivityName|xs:String|Nazwa działania, które są emitowane CustomTrackingRecord|  
|Identyfikator działania|xs:String|Identyfikator działania, które są emitowane CustomTrackingRecord|  
|ActivityInstanceId|xs:String|Identyfikator wystąpienia działania, które są emitowane CustomTrackingRecord|  
|ActivityTypeName|xs:String|Nazwa działania, które są emitowane CustomTrackingRecord|  
|Dane|xs:String|Dane, która była śledzona z tym zdarzeniem.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "dataName" type="System.String" > dataValue\</item > \< /elementy >.  Jeśli żadne dane nie była śledzona, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar buforu ETW lub max ładunek zdarzenia ETW. Jeśli rozmiar zdarzenia przekracza limit ETW, a następnie zdarzenie zostanie obcięta przez usunięcie adnotacje i zastąpienie wartości danych z \<elementy >...  \< /elementy >.  Następujące typy są przechowywane jako ich wartość zwracana przez ToString(); String,char,bool,int,short,Long,uint,ushort,ulong,system.Single,float,Double,system.GUID,system.DateTimeOffset,system.DateTime.  Wszystkie inne typy są serializowane, za pomocą System.Runtime.Serialization.NetDataContractSerializer.|  
|Adnotacje|xs:String|Adnotacje, które zostały dodane do tego zdarzenia.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</item > \< /elementy >.  Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar buforu ETW lub max ładunek zdarzenia ETW. Jeśli rozmiar zdarzenia przekracza limit ETW, a następnie zdarzenie zostanie obcięta przez usunięcie adnotacje i zastępując wartość symbolu adnotacji z \<elementy >...  \< /elementy >.|  
|ProfileName|xs:String|Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowane|  
|HostReference|xs:String|Dla usług sieci web hostowanych w tym polu jednoznacznie identyfikuje usługę w hierarchii w sieci web.  Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName" przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
