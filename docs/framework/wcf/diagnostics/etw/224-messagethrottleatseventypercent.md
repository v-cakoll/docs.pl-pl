---
title: "224 — MessageThrottleAtSeventyPercent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0dd985e3986548938f06e86c1f49d23c43307d17
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="224---messagethrottleatseventypercent"></a>224 — MessageThrottleAtSeventyPercent
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|224|  
|Słowa kluczowe|EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceModel|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 Gdy jeden z głównej usługi limity został przekroczony, `MessageThrottleExceeded` jest emitowany zdarzeń. Gdy spowalnia kolekcji działania i bieżącą wartość przepustnicy wynosi 70 procent bieżący limit następnie to zdarzenie jest emitowany. Należy pamiętać, że to zdarzenie tylko wysyłanego po jako działanie spowalnia. Jeśli bieżąca wartość wskaźnika myszy na znak 70 procent, (na przykład 70,69,70,71,70,69), tylko pierwsze wystąpienie 70 procent powoduje zdarzenia. Po to zdarzenie jest emitowany, przyszłych wystąpień przekroczenia ograniczania limit wyników w `MessageThrottleExceeded` zdarzeń.  
  
## <a name="message"></a>Komunikat  
 Limit przepustnicy "%1" z "%2" ma wartość 70 %%.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa ograniczenia|`xs:string`|Nazwa ograniczenia, który został przekroczony. Albo `MaxConcurrentCalls`, `MaxConcurrentInstances`, lub `MaxConcurrentSessions`,|  
|Limit|`xs:long`|Aktualnie skonfigurowany limit przepustnicy.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ". Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
