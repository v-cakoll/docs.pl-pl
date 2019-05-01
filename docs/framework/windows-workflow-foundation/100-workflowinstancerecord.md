---
title: 100 — WorkflowInstanceRecord
ms.date: 03/30/2017
ms.assetid: ed4d1851-b378-489b-a22d-c1db09571fb4
ms.openlocfilehash: c7abb2c59c65e0b0f4c4f209e3c7c2d0cf4641d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008671"
---
# <a name="100---workflowinstancerecord"></a>100 — WorkflowInstanceRecord
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Id|100|  
|słowa kluczowe|EndToEndMonitoring, rozwiązywania problemów, HealthMonitoring, WFTracking|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows, gdy wystąpienie przepływu pracy emituje WorkflowInstanceRecord do stanów przepływu pracy: Pracę, wznowić i utrwalone, bezczynności (%), usunąć, zakończone, anulowane zwolniony, zawieszenia.  
  
## <a name="message"></a>Komunikat  
 TrackRecord = WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, stan = %5, adnotacje = %6, ProfileName = %7  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Identyfikator wystąpienia przepływu pracy|  
|RecordNumber|xs:long|Numer sekwencyjny emitowany rekordu|  
|eventTime|xs:dateTime|Godzina w formacie UTC zdarzenia został wyemitowany|  
|ActivityDefinitionId|xs:String|Nazwa działania głównego w przepływie pracy|  
|Stan|xs:String|Bieżący stan przepływu pracy.|  
|Adnotacje|xs:String|Adnotacje, które zostały dodane do tego zdarzenia.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</item > \< /elementy >.  Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar buforu ETW lub max ładunek zdarzenia ETW. Jeśli rozmiar zdarzenia przekracza limit ETW, a następnie zdarzenie zostanie obcięta przez usunięcie adnotacje i zastępując wartość symbolu adnotacji z \<elementy >...  \< /elementy >.|  
|ProfileName|xs:String|Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowane|  
|HostReference|xs:String|Dla usług sieci web hostowanych w tym polu jednoznacznie identyfikuje usługę w hierarchii w sieci web.  Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName" przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
