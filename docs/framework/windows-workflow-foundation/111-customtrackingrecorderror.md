---
title: 111 - CustomTrackingRecordError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d469fb12-e094-4d6c-9b4d-abd7ce0d17da
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adca15fccf773d1c6a8bc66b7dfa21be701c15cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="111---customtrackingrecorderror"></a>111 - CustomTrackingRecordError
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|111|  
|Słowa kluczowe|UserEvents EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|Poziom|Błąd|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows podczas działania w ramach wystąpienia przepływu pracy emituje CustomTrackingRecord z poziomu błędu.  
  
## <a name="message"></a>Komunikat  
 TrackRecord = CustomTrackingRecord, identyfikator wystąpienia = %1, RecordNumber = %2, EventTime = %3, nazwa = %4, ActivityName = %5, identyfikator = %6, ActivityInstanceId = %7 ActivityTypeName = %8, dane = %9 adnotacje = % 10 ProfileName = % 11  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Identyfikator wystąpienia|xs:GUID|Identyfikator wystąpienia przepływu pracy|  
|RecordNumber|xs:Long|Numer sekwencyjny emitowany rekordu|  
|eventTime|xs: DateTime|Godzina w formacie UTC podczas zdarzenia zostały wyemitowane|  
|Nazwa|xs:String|Nazwa CustomTrackingRecord|  
|activityName|xs:String|Nazwa działania, które są emitowane CustomTrackingRecord|  
|Identyfikator działania|xs:String|Identyfikator działania, które są emitowane CustomTrackingRecord|  
|ActivityInstanceId|xs:String|Identyfikator wystąpienia działania wysyłanego CustomTrackingRecord|  
|ActivityTypeName|xs:String|Nazwa działania, które są emitowane CustomTrackingRecord|  
|Dane|xs:String|Dane, które zostało śledzone z tym zdarzeniem.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "dataName" type="System.String" > wartości danych\</elementu > \< /elementy >.  Jeśli został śledzone żadne dane, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW. Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości danych z \<elementy >...  \< /elementy >.  Następujące typy są przechowywane jako wartości zwracane przez ToString(); String,char,bool,int,short,Long,uint,ushort,ulong,system.Single,float,Double,system.GUID,system.DateTimeOffset,system.DateTime.  Wszystkie inne typy są serializowane, przy użyciu System.Runtime.Serialization.NetDataContractSerializer.|  
|Adnotacje|xs:String|Adnotacje, które zostały dodane do tego zdarzenia.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</elementu > \< /elementy >.  Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW. Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości adnotacji z \<elementy >...  \< /elementy >.|  
|ProfileName|xs:String|Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowany|  
|HostReference|xs:String|Dla usług sieci web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci web.  Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName "przykład:" Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService "|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
