---
title: "107 — BookmarkResumptionRecord"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa2d37ed-2bfa-439b-89e8-a9354027f155
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8d3effb662ec2994351e1de7975b8ce2737c5ef0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="107----bookmarkresumptionrecord"></a>107 — BookmarkResumptionRecord
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|107|  
|Słowa kluczowe|EndToEndMonitoring rozwiązywania problemów, HealthMonitoring, WFTracking|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows, gdy BookmarkResumptionRecord emituje wystąpienia przepływu pracy.  
  
## <a name="message"></a>Komunikat  
 TrackRecord = BookmarkResumptionRecord, identyfikator wystąpienia = %1, RecordNumber = %2, EventTime = %3, nazwa = %4, SubInstanceID = %5, OwnerActivityName = %6, OwnerActivityId = %7 OwnerActivityInstanceId = %8, OwnerActivityTypeName = %9 adnotacje = % 10 ProfileName = % 11  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Identyfikator wystąpienia|xs:GUID|Identyfikator wystąpienia przepływu pracy|  
|RecordNumber|xs:Long|Numer sekwencyjny emitowany rekordu|  
|eventTime|xs: DateTime|Godzina w formacie UTC podczas zdarzenia zostały wyemitowane|  
|Nazwa|xs:String|Nazwa zakładki, która zostało wznowione|  
|SubInstanceID|xs:GUID|Identyfikator zakresu zakładek|  
|Właściwość OwnerActivityName|xs:String|Nazwa działania zakładki|  
|OwnerActivityId|xs:String|Identyfikator działania zakładki|  
|OwnerActivityInstanceId|xs:String|Identyfikator wystąpienia działania zakładki|  
|OwnerActivityTypeName|xs:String|Typ działania zakładki|  
|Adnotacje|xs:String|Adnotacje, które zostały dodane do tego zdarzenia.  Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</elementu > \< /elementy >.  Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >. Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW. Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości adnotacji z \<elementy >...  \< /elementy >.|  
|ProfileName|xs:String|Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowany|  
|HostReference|xs:String|Dla usług sieci web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci web.  Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName "przykład:" Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService "|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
