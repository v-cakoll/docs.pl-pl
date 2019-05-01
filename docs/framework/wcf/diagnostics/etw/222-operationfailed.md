---
title: 222 — OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: c49aad0f93ce47b66306d75741267530dc6d3fe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781644"
---
# <a name="222---operationfailed"></a>222 — OperationFailed
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|222|  
|słowa kluczowe|EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przy domyślny Model usług `OperationInvoker` napotkał wyjątek podczas wywoływania jego metody. Uwaga tego wyjątki, które wynikają z `FaultException` spowodować, że to zdarzenie nie jest emitowany.  
  
## <a name="message"></a>Komunikat  
 Metoda "%1" spowodowała nieobsługiwany wyjątek podczas wywoływania przez OperationInvoker. Czas trwania wywołania metody wynosiła ms "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa metody|`xs:string`|Nazwa aparatu CLR metody, która została wywołana przez `OperationInvoker`.|  
|Czas trwania|`xs:long`|Czas w milisekundach, jaki zajęło `OperationInvoker` było wywołanie metody.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
