---
title: 105 - FaultPropagationRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 168473b1-b1e5-4e9f-8a2a-35bbdb2ef531
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8c427b9538e0215784bea3a69d41bd1b97623741
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="105---faultpropagationrecord"></a>105 - FaultPropagationRecord
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|105|  
|Słowa kluczowe|EndToEndMonitoring rozwiązywania problemów, HealthMonitoring, WFTracking|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows, gdy FaultPropagationRecord emituje działania z wystąpieniem przepływu pracy.  
  
## <a name="message"></a>Komunikat  
 TrackRecord = FaultPropagationRecord, identyfikator wystąpienia = %1, RecordNumber = %2, EventTime = %3, FaultSourceActivityName = %4, FaultSourceActivityId = %5, FaultSourceActivityInstanceId = %6, FaultSourceActivityTypeName = %7 FaultHandlerActivityName = %8  FaultHandlerActivityId = %9 FaultHandlerActivityInstanceId = % 10 FaultHandlerActivityTypeName = % 11 błąd = IsFaultSource 12, % = % 13, adnotacje = % 14, ProfileName = % 15  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Identyfikator wystąpienia|xs:GUID|Identyfikator wystąpienia przepływu pracy|  
|RecordNumber|xs:Long|Numer sekwencyjny emitowany rekordu|  
|eventTime|xs: DateTime|Godzina w formacie UTC podczas zdarzenia zostały wyemitowane|  
|FaultSourceActivityName|xs:String|Nazwa działania, które są emitowane usterki|  
|FaultSourceActivityId|xs:String|Identyfikator działania, które są emitowane usterki|  
|FaultSourceActivityInstanceId|xs:String|Identyfikator wystąpienia działania wysyłanego usterki|  
|FaultSourceActivityTypeName|xs:String|Typ działania, które są emitowane usterki|  
|FaultHandlerActivityName|xs:String|Nazwa wyświetlana działanie procedury obsługi błędów|  
|FaultHandlerActivityId|xs:String|Identyfikator działanie procedury obsługi błędów|  
|FaultHandlerActivityInstanceId|xs:String|Identyfikator wystąpienia działania obsługi błędów|  
|FaultHandlerActivityTypeName|xs:String|Typ działania obsługi błędów|  
|Błąd|xs:String|Szczegółowe informacje o błędzie|  
|IsFaultSource|xs:unsignedByte|Wskazuje, czy zdarzenie zostały wyemitowane ze źródła błędu|  
|Adnotacje|xs:String|Adnotacje, które zostały dodane do tego zdarzenia.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</elementu > \< /elementy >.  Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW. Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości adnotacji z \<elementy >...  \< /elementy >.|  
|ProfileName|xs:String|Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowany|  
|HostReference|xs:String|Dla usług sieci web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci web.  Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName "przykład:" Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService "|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
