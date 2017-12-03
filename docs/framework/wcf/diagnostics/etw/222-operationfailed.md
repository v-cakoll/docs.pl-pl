---
title: "222 — OperationFailed"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d56766dd32acf1ef71f7c06a5c3c94cc7510070
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="222---operationfailed"></a>222 — OperationFailed
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|222|  
|Słowa kluczowe|EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceModel|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany gdy domyślny Model usługi `OperationInvoker` napotkał wyjątek podczas wywoływania metody. Uwaga tego wyjątki pochodzące z `FaultException` spowodować to zdarzenie nie być emitowane.  
  
## <a name="message"></a>Komunikat  
 Metoda "%1" spowodowała zgłoszenie nieobsługiwanego wyjątku, gdy została wywołana przez obiekt OperationInvoker. Wywołanie metody trwało "%2" ms.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa metody|`xs:string`|Nazwa metody, która została wywołana przez CLR `OperationInvoker`.|  
|Czas trwania|`xs:long`|Czas (w milisekundach), jaką trwało `OperationInvoker` można wywołać metody.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ". Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
