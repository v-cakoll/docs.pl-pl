---
title: 117 — WorkflowInstanceTerminatedRecordWithId
ms.date: 03/30/2017
ms.assetid: e68539d0-5338-468a-9f75-7e5b09d39a3c
ms.openlocfilehash: d1d6930a08eeb513dbb017b6c9b409916e5b1a2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009893"
---
# <a name="117---workflowinstanceterminatedrecordwithid"></a>117 — WorkflowInstanceTerminatedRecordWithId
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|117|  
|słowa kluczowe|HealthMonitoring, WFTracking|  
|Poziom|Błąd|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows, gdy wystąpienie przepływu pracy emituje WorkflowInstanceTerminatedRecord.  
  
## <a name="message"></a>Komunikat  
 TrackRecord = WorkflowInstanceTerminatedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, przyczyna = %5, adnotacje = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|Identyfikator wystąpienia przepływu pracy|  
|RecordNumber|xs:long|Numer sekwencyjny emitowany rekordu|  
|eventTime|xs:dateTime|Godzina w formacie UTC zdarzenia został wyemitowany|  
|ActivityDefinitionId|xs:String|Nazwa działania głównego w przepływie pracy|  
|Stan|xs:String|Bieżący stan przepływu pracy.|  
|Adnotacje|xs:String|Adnotacje, które zostały dodane do tego zdarzenia. Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</item > \< /elementy >. Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar buforu ETW lub max ładunek zdarzenia ETW. Jeśli rozmiar zdarzenia przekracza limit ETW, a następnie zdarzenie zostanie obcięta przez usunięcie adnotacje i zastępując wartość symbolu adnotacji z \<elementy >...  \< /elementy >.|  
|ProfileName|xs:String|Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowane|  
|WorkflowDefinitionIdentity|xs:String|Identyfikator definicji przepływu pracy|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
