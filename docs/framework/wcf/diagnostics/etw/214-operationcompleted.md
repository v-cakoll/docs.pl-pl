---
title: "214 — OperationCompleted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 823207f4225252d94bd8fba450eb63edd00068ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="214---operationcompleted"></a>214 — OperationCompleted
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|214|  
|Słowa kluczowe|HealthMonitoring EndToEndMonitoring, rozwiązywania problemów, ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany gdy domyślny Model usługi `OperationInvoker` zostało zakończone wywołanie do metody bez tej metody generowania wyjątku.  
  
## <a name="message"></a>Komunikat  
 Obiekt OperationInvoker ukończył wywołanie metody '%1'. Wywołanie metody trwało "%2" ms.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa metody|`xs:string`|Nazwa metody, która została wywołana przez CLR `OperationInvoker`.|  
|Czas trwania|`xs:long`|Czas (w milisekundach), jaką trwało `OperationInvoker` można wywołać metody.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ". Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
