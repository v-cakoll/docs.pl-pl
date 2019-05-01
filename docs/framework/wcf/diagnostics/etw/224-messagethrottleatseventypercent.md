---
title: 224 — MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: f70dc235e037b4f490a25866940fe2bccceae2a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916308"
---
# <a name="224---messagethrottleatseventypercent"></a>224 — MessageThrottleAtSeventyPercent
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|224|  
|słowa kluczowe|EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 Gdy jeden ograniczenia głównych usług został przekroczony, `MessageThrottleExceeded` zdarzenia są emitowane. Gdy spowalnia wzrost aktywności i bieżącą wartość ograniczenie wynosi 70 procent bieżący limit następnie to zdarzenie jest emitowane. Należy pamiętać o tym, czy to zdarzenie jest emitowane tylko po jako działanie spowalnia. Jeśli bieżąca wartość wskaźnika pozycji 70 procent, (na przykład 70,69,70,71,70,69), tylko pierwsze wystąpienie 70 procent wyników w zdarzeniu. Po to zdarzenie jest emitowane, przyszłych wystąpień przekroczenia ograniczania ograniczyć wynik na liście `MessageThrottleExceeded` zdarzeń.  
  
## <a name="message"></a>Komunikat  
 Ograniczenie przepustowości "%1" z "%2" wynosi 70 %%.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa ograniczenia|`xs:string`|Nazwa ograniczenia, który został przekroczony. Albo `MaxConcurrentCalls`, `MaxConcurrentInstances`, lub `MaxConcurrentSessions`,|  
|Limit|`xs:long`|Aktualnie skonfigurowany limit przepustowości.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
