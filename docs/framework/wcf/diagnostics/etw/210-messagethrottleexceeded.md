---
title: 210 — MessageThrottleExceeded
ms.date: 03/30/2017
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
ms.openlocfilehash: 7ba5948b36642085ef44661b3d580e7f1c4102cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781889"
---
# <a name="210---messagethrottleexceeded"></a>210 — MessageThrottleExceeded
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|210|  
|słowa kluczowe|EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane, gdy dla jednej usługi trzy główne ograniczenia został przekroczony. Należy pamiętać, to zdarzenie tylko jest emitowane początkowo przekroczenia ograniczenie przepustowości. Na przykład, jeśli ograniczenie przepustowości współbieżnych wywołań to 10, 11 współbieżnych wyniki wywołania `MessageThrottleExceeded` zdarzeń. Wywołanie 12 nie powoduje inne zdarzenie. Ponadto aby uniknąć strumienia zdarzeń generujące dużo alertów, działania, który unosi się wokół granicy nie powoduje inne zdarzenie. W tym przykładzie wykonaj kilka wywołań następnie czy 9 równoczesnych wywołań. Jeśli później więcej wywołań w dwóch przychodzą, bieżąca wartość to ponownie 11. Nie powoduje w innym przypadku. Gdy bieżąca wartość znajduje się do 70 procent ograniczenie przepustowości zdarzenia są emitowane wskazującą, czy ma spowolnić działanie. Kolejnego działania, która przekracza limit wyników w innym `MessageThrottleExceeded` zdarzeń jest emitowane. W tym przykładzie, jeśli liczby współbieżnych wywołań znajduje się do 7, a następnie ponownie osiągnie 11 i innego `MessageThrottleExceeded` zdarzenia są emitowane.  
  
## <a name="message"></a>Komunikat  
 Osiągnięto limit przepustowości "%1" z "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa ograniczenia|`xs:string`|Nazwa ograniczenia, który został przekroczony. Albo `MaxConcurrentCalls`, `MaxConcurrentInstances`, lub `MaxConcurrentSessions`,|  
|Limit|`xs:long`|Aktualnie skonfigurowany limit przepustowości.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
