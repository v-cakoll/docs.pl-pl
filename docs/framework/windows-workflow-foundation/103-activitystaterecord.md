---
title: 103 — ActivityStateRecord
ms.date: 03/30/2017
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
ms.openlocfilehash: 38cec570cffebf6af6d35df481cbec8c7dca8cd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924387"
---
# <a name="103---activitystaterecord"></a>103 — ActivityStateRecord
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Id|103|  
|słowa kluczowe|EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows podczas działania w ramach wystąpienie przepływu pracy emituje ActivityStateRecord  
  
## <a name="message"></a>Komunikat  
 TrackRecord = ActivityStateRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, stan = %4, Nazwa = %5, identyfikator działania = %6, ActivityInstanceId = %7, ActivityTypeName = %8, argumenty = %9, zmienne = % 10, adnotacje = % 11, ProfileName = % 12  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Identyfikator wystąpienia przepływu pracy|  
|RecordNumber|xs:long|Numer sekwencyjny emitowany rekordu|  
|eventTime|xs:dateTime|Godzina w formacie UTC zdarzenia został wyemitowany|  
|Stan|xs:String|Stan działania|  
|Nazwa|xs:String|Nazwa wyświetlana działania, które są emitowane zdarzenia|  
|Identyfikator działania|xs:String|Identyfikator działania emitowanie działania|  
|ActivityInstanceId|xs:String|Identyfikator wystąpienia działania emitowanie działania|  
|ActivityTypeName|xs:String|Nazwa typu emitowanie działania|  
|Argumenty|xs:String|Argumenty, które były śledzone przy użyciu tego zdarzenia.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "argumentName" type="System.String" > argumentValue\</item > \< /elementy >.  Jeśli żadne argumenty były śledzone, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar buforu ETW lub max ładunek zdarzenia ETW. Jeśli rozmiar zdarzenia przekracza limit ETW, a następnie zdarzenie zostanie obcięta przez usunięcie adnotacje i zastępując wartość symbolu adnotacji z \<elementy >...  \< /elementy >.  Następujące typy są przechowywane jako ich wartość zwracana przez ToString(); String,char,bool,int,short,Long,uint,ushort,ulong,system.Single,float,Double,system.GUID,system.DateTimeOffset,system.DateTime.  Wszystkie inne typy są serializowane, za pomocą System.Runtime.Serialization.NetDataContractSerializer.|  
|Zmienne|xs:String|Zmienne, które były śledzone przy użyciu tego zdarzenia.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "nazwa_zmiennej" type="System.String" > variableValue\</item > \< /elementy >.  Jeśli zmienne nie były śledzone, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar buforu ETW lub max ładunek zdarzenia ETW. Jeśli rozmiar zdarzenia przekracza limit ETW, a następnie zdarzenie zostanie obcięta przez usunięcie adnotacje i zastąpienie wartości zmiennych z \<elementy >...  \< /elementy >.  Następujące typy są przechowywane jako ich wartość zwracana przez ToString(); String,char,bool,int,short,Long,uint,ushort,ulong,system.Single,float,Double,system.GUID,system.DateTimeOffset,system.DateTime.  Wszystkie inne typy są serializowane, za pomocą System.Runtime.Serialization.NetDataContractSerializer.|  
|Adnotacje|xs:String|Adnotacje, które zostały dodane do tego zdarzenia.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</item > \< /elementy >.  Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar buforu ETW lub max ładunek zdarzenia ETW. Jeśli rozmiar zdarzenia przekracza limit ETW, a następnie zdarzenie zostanie obcięta przez usunięcie adnotacje i zastępując wartość symbolu adnotacji z \<elementy >...  \< /elementy >.|  
|ProfileName|xs:String|Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowane|  
|HostReference|xs:String|Dla usług sieci web hostowanych w tym polu jednoznacznie identyfikuje usługę w hierarchii w sieci web.  Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName" przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
