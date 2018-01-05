---
title: 112 - WorkflowInstanceSuspendedRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc825c7c-8c90-48f7-9336-9a978a8246c6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a53d670082a9e8c3c714c9c1ce519b5b9229d15a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="112---workflowinstancesuspendedrecord"></a>112 - WorkflowInstanceSuspendedRecord
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|112|  
|Słowa kluczowe|EndToEndMonitoring rozwiązywania problemów, HealthMonitoring, WFTracking|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows, gdy rekord WorkflowInstanceSuspended emituje wystąpienia przepływu pracy.  
  
## <a name="message"></a>Komunikat  
 TrackRecord = WorkflowInstanceSuspendedRecord, identyfikator wystąpienia = %1, RecordNumber = %2, EventTime = %3, obiekt ActivityDefinitionId = %4, przyczyna = %5, adnotacje = %6, ProfileName = %7  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Identyfikator wystąpienia|xs:GUID|Identyfikator wystąpienia przepływu pracy|  
|RecordNumber|xs:Long|Numer sekwencyjny emitowany rekordu|  
|eventTime|xs: DateTime|Godzina w formacie UTC podczas zdarzenia zostały wyemitowane|  
|Obiekt ActivityDefinitionId|xs:String|Nazwa działania głównego w przepływie pracy|  
|Przyczyna|xs:String|Przyczyna przepływ pracy został wstrzymany.|  
|Adnotacje|xs:String|Adnotacje, które zostały dodane do tego zdarzenia.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</elementu > \< /elementy >.  Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW. Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości adnotacji z \<elementy >...  \< /elementy >.|  
|ProfileName|xs:String|Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowany|  
|HostReference|xs:String|Dla usług sieci web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci web.  Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName "przykład:" Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService "|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
