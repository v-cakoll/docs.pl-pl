---
title: 214 — OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: da1021b674b555b683f8f745f5a2a0073c9567e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968002"
---
# <a name="214---operationcompleted"></a>214 — OperationCompleted
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|214|  
|słowa kluczowe|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przy domyślny Model usług `OperationInvoker` zakończone wywołanie do metody bez tej metody, zostanie zgłoszony wyjątek.  
  
## <a name="message"></a>Komunikat  
 OperationInvoker wykonać wywołanie metody "%1". Czas trwania wywołania metody wynosiła ms "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa metody|`xs:string`|Nazwa aparatu CLR metody, która została wywołana przez `OperationInvoker`.|  
|Czas trwania|`xs:long`|Czas w milisekundach, jaki zajęło `OperationInvoker` było wywołanie metody.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
