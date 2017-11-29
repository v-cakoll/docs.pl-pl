---
title: 106 - CancelRequestRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f72a59aa-8093-4a8e-94df-40acaffb1ffb
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36de6eabb247cb59e8759032e5cd6d6996b52d45
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="106---cancelrequestrecord"></a>106 - CancelRequestRecord
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|106|  
|Słowa kluczowe|EndToEndMonitoring rozwiązywania problemów, HealthMonitoring, WFTracking|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows podczas działania w ramach wystąpienia przepływu pracy emituje cancelrequestedrecord.  
  
## <a name="message"></a>Komunikat  
 TrackRecord = CancelRequestedRecord, identyfikator wystąpienia = %1, RecordNumber = %2, EventTime = %3, nazwa = %4, identyfikator = %5, ActivityInstanceId = %6, ActivityTypeName = %7 ChildActivityName = %8, ChildActivityId = %9 ChildActivityInstanceId = % 10 ChildActivityTypeName = % 11, adnotacje = ProfileName 12, % = % 13  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Identyfikator wystąpienia|xs:GUID|Identyfikator wystąpienia przepływu pracy|  
|RecordNumber|xs:Long|Numer sekwencyjny emitowany rekordu|  
|eventTime|xs: DateTime|Godzina w formacie UTC podczas zdarzenia zostały wyemitowane|  
|Nazwa|xs:String|Nazwa działania, którego zażądano operacji anulowania|  
|Identyfikator działania|xs:String|Identyfikator działania, którego zażądano operacji anulowania|  
|ActivityInstanceId|xs:String|Identyfikator wystąpienia zażądano operacji anulowania działania|  
|ActivityTypeName|xs:String|Typ działania, którego zażądano operacji anulowania|  
|ChildActivityName|xs:String|Nazwa działania anulowane|  
|ChildActivityId|xs:String|Identyfikator działania anulowane|  
|ChildActivityInstanceId|xs:String|Identyfikator wystąpienia działania anulowane|  
|ChildActivityTypeName|xs:String|Typ działania anulowane|  
|Adnotacje|xs:String|Adnotacje, które zostały dodane do tego zdarzenia.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</elementu > \< /elementy >.  Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW. Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości adnotacji z \<elementy >...  \< /elementy >.|  
|ProfileName|xs:String|Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowany|  
|HostReference|xs:String|Dla usług sieci web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci web.  Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName "przykład:" Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService "|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
