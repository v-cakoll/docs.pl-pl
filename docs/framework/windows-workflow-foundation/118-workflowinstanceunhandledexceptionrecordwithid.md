---
title: 118 — WorkflowInstanceUnhandledExceptionRecordWithId
ms.date: 03/30/2017
ms.assetid: 2ce4b193-e141-4cc4-86a3-2e8c984c110d
ms.openlocfilehash: eb69fc4760cd89294e24680b5aab83fcd058feb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009880"
---
# <a name="118---workflowinstanceunhandledexceptionrecordwithid"></a>118 — WorkflowInstanceUnhandledExceptionRecordWithId
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|118|  
|słowa kluczowe|HealthMonitoring, WFTracking|  
|Poziom|Błąd|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows, gdy wystąpienie przepływu pracy emituje WorkflowInstanceUnhandledExceptionRecord.  
  
## <a name="message"></a>Komunikat  
 TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, identyfikator = %6, SourceInstanceId = %7, SourceTypeName = %8, wyjątek = %9, adnotacje = % 10, ProfileName = % 11, WorkflowDefinitionIdentity = % 12  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Identyfikator wystąpienia przepływu pracy|  
|RecordNumber|xs:long|Numer sekwencyjny emitowany rekordu|  
|eventTime|xs:dateTime|Godzina w formacie UTC zdarzenia został wyemitowany|  
|ActivityDefinitionId|xs:String|Nazwa działania głównego w przepływie pracy|  
|SourceName|xs:String|Nazwa źródłowego działania, za pomocą komunikacji niezawodnej skutkuje unhandledException|  
|SourceId|xs:String|Identyfikator działania działania źródłowego błędów|  
|SourceInstanceId|xs:String|Identyfikator wystąpienia działania działania źródłowego błędów|  
|SourceTypeName|xs:String|Nazwa źródłowego działania typu, który zwracające błędy powodujące unhandledException|  
|Wyjątek|xs:String|Szczegóły wyjątku dla nieobsłużonych wyjątków|  
|Stan|xs:String|Bieżący stan przepływu pracy.|  
|Adnotacje|xs:String|Adnotacje, które zostały dodane do tego zdarzenia. Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</item > \< /elementy >. Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar buforu ETW lub max ładunek zdarzenia ETW. Jeśli rozmiar zdarzenia przekracza limit ETW, a następnie zdarzenie zostanie obcięta przez usunięcie adnotacje i zastępując wartość symbolu adnotacji z \<elementy >...  \< /elementy >.|  
|ProfileName|xs:String|Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowane|  
|WorkflowDefinitionIdentity|xs:String|Identyfikator definicji przepływu pracy|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
