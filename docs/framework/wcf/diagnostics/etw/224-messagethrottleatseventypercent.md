---
title: 224 — MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: f70dc235e037b4f490a25866940fe2bccceae2a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="224---messagethrottleatseventypercent"></a>224 — MessageThrottleAtSeventyPercent
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|224|  
|Słowa kluczowe|EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceModel|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 Gdy jeden z głównej usługi limity został przekroczony, `MessageThrottleExceeded` jest emitowany zdarzeń. Gdy spowalnia kolekcji działania i bieżącą wartość przepustnicy wynosi 70 procent bieżący limit następnie to zdarzenie jest emitowany. Należy pamiętać, że to zdarzenie tylko wysyłanego po jako działanie spowalnia. Jeśli bieżąca wartość wskaźnika myszy na znak 70 procent, (na przykład 70,69,70,71,70,69), tylko pierwsze wystąpienie 70 procent powoduje zdarzenia. Po to zdarzenie jest emitowany, przyszłych wystąpień przekroczenia ograniczania limit wyników w `MessageThrottleExceeded` zdarzeń.  
  
## <a name="message"></a>Komunikat  
 Limit przepustnicy "%1" z "%2" ma wartość 70 %%.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa ograniczenia|`xs:string`|Nazwa ograniczenia, który został przekroczony. Albo `MaxConcurrentCalls`, `MaxConcurrentInstances`, lub `MaxConcurrentSessions`,|  
|Limit|`xs:long`|Aktualnie skonfigurowany limit przepustnicy.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName". Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
