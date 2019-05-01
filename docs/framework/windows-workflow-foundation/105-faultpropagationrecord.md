---
title: 105 — FaultPropagationRecord
ms.date: 03/30/2017
ms.assetid: 168473b1-b1e5-4e9f-8a2a-35bbdb2ef531
ms.openlocfilehash: c48f42a91ad9a15b49aad8c1ab684f2348954174
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924205"
---
# <a name="105---faultpropagationrecord"></a>105 — FaultPropagationRecord
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Id|105|  
|słowa kluczowe|EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows, gdy działanie z wystąpieniem przepływu pracy emituje FaultPropagationRecord.  
  
## <a name="message"></a>Komunikat  
 TrackRecord = FaultPropagationRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, FaultSourceActivityName = %4, FaultSourceActivityId = %5, FaultSourceActivityInstanceId = %6, FaultSourceActivityTypeName = %7, FaultHandlerActivityName = %8,  FaultHandlerActivityId = %9, FaultHandlerActivityInstanceId = % 10, FaultHandlerActivityTypeName = % 11, błąd = 12, IsFaultSource % = % 13, adnotacje = % 14, ProfileName = % 15  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Identyfikator wystąpienia przepływu pracy|  
|RecordNumber|xs:long|Numer sekwencyjny emitowany rekordu|  
|eventTime|xs:dateTime|Godzina w formacie UTC zdarzenia został wyemitowany|  
|FaultSourceActivityName|xs:String|Nazwa działania, które są emitowane usterki|  
|FaultSourceActivityId|xs:String|Identyfikator działania, które są emitowane usterki|  
|FaultSourceActivityInstanceId|xs:String|Identyfikator wystąpienia działania, które są emitowane usterki|  
|FaultSourceActivityTypeName|xs:String|Typ działania, które są emitowane usterki|  
|FaultHandlerActivityName|xs:String|Nazwa wyświetlana działanie procedury obsługi błędów|  
|FaultHandlerActivityId|xs:String|Identyfikator działanie procedury obsługi błędów|  
|FaultHandlerActivityInstanceId|xs:String|Identyfikator wystąpienia działanie procedury obsługi błędów|  
|FaultHandlerActivityTypeName|xs:String|Typ działania obsługi błędów|  
|Błędów|xs:String|Szczegółowe informacje o błędzie|  
|IsFaultSource|xs:unsignedByte|Wskazuje, jeśli zdarzenie został wyemitowany ze źródła błędów|  
|Adnotacje|xs:String|Adnotacje, które zostały dodane do tego zdarzenia.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</item > \< /elementy >.  Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar buforu ETW lub max ładunek zdarzenia ETW. Jeśli rozmiar zdarzenia przekracza limit ETW, a następnie zdarzenie zostanie obcięta przez usunięcie adnotacje i zastępując wartość symbolu adnotacji z \<elementy >...  \< /elementy >.|  
|ProfileName|xs:String|Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowane|  
|HostReference|xs:String|Dla usług sieci web hostowanych w tym polu jednoznacznie identyfikuje usługę w hierarchii w sieci web.  Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName" przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
