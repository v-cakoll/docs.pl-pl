---
title: 113 - WorkflowInstanceTerminatedRecord
ms.date: 03/30/2017
ms.assetid: f53204ee-4ea2-45e1-8859-e86d07305efd
ms.openlocfilehash: e6ea25de7ceea33ca1e552c12545525bbc17f198
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514026"
---
# <a name="113---workflowinstanceterminatedrecord"></a>113 - WorkflowInstanceTerminatedRecord
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Id|113|  
|Słowa kluczowe|EndToEndMonitoring rozwiązywania problemów, HealthMonitoring, WFTracking|  
|Poziom|Błąd|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows, gdy WorkflowInstanceTerminatedRecord emituje wystąpienia przepływu pracy.  
  
## <a name="message"></a>Komunikat  
 TrackRecord = WorkflowInstanceTerminatedRecord, identyfikator wystąpienia = %1, RecordNumber = %2, EventTime = %3, obiekt ActivityDefinitionId = %4, przyczyna = %5, adnotacje = %6, ProfileName = %7  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Identyfikator wystąpienia|xs:GUID|Identyfikator wystąpienia przepływu pracy|  
|RecordNumber|xs:Long|Numer sekwencyjny emitowany rekordu|  
|eventTime|xs: DateTime|Godzina w formacie UTC podczas zdarzenia zostały wyemitowane|  
|Obiekt ActivityDefinitionId|xs:String|Nazwa działania głównego w przepływie pracy|  
|Przyczyna|xs:String|Przyczyna przepływ pracy został przerwany.|  
|Adnotacje|xs:String|Adnotacje, które zostały dodane do tego zdarzenia.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</elementu > \< /elementy >.  Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW. Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości adnotacji z \<elementy >...  \< /elementy >.|  
|ProfileName|xs:String|Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowany|  
|HostReference|xs:String|Dla usług sieci web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci web.  Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName" przykład: "Domyślna witryna sieci Web/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService"|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
