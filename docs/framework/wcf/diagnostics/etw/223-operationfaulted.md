---
title: 223 — OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: cf4a455d80a1a0ac09e99bad967c1feba3653842
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="223---operationfaulted"></a>223 — OperationFaulted
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|223|  
|Słowa kluczowe|EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceModel|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany gdy domyślny Model usługi `OperationInvoker` napotkał wyjątek pochodny `FaultException` podczas wywoływania metody.  
  
## <a name="message"></a>Komunikat  
 Metoda "%1" spowodowała zgłoszenie wyjątku FaultException, gdy została wywołana przez obiekt OperationInvoker. Wywołanie metody trwało "%2" ms.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|MethodName|`xs:string`|Nazwa metody, która została wywołana przez CLR `OperationInvoker`.|  
|Czas trwania|`xs:long`|Czas (w milisekundach), jaką trwało `OperationInvoker` można wywołać metody.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName". Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
