---
title: 223 — OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: cf4a455d80a1a0ac09e99bad967c1feba3653842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596540"
---
# <a name="223---operationfaulted"></a>223 — OperationFaulted
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|223|  
|słowa kluczowe|EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przy domyślny Model usług `OperationInvoker` napotkała wyjątek pochodząca od `FaultException` podczas wywoływania metody.  
  
## <a name="message"></a>Komunikat  
 Metoda "%1" zwróciła wyjątek FaultException —, po wywołaniu przez OperationInvoker. Czas trwania wywołania metody wynosiła ms "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|MethodName|`xs:string`|Nazwa aparatu CLR metody, która została wywołana przez `OperationInvoker`.|  
|Czas trwania|`xs:long`|Czas w milisekundach, jaki zajęło `OperationInvoker` było wywołanie metody.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
