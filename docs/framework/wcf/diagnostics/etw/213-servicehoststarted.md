---
title: "213 — ServiceHostStarted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a83cb1cfb87b562add1a791de5a651b563d63d4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="213---servicehoststarted"></a>213 — ServiceHostStarted
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|213|  
|Słowa kluczowe|EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceHost|  
|Poziom|LogAlways|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany po uruchomieniu hosta usługi hostowanej w sieci Web. Dzieje się tak zazwyczaj, gdy usługa jest aktywowany przez komunikat. Może się również zdarzyć, jeśli usługa jest skonfigurowana do automatycznego uruchomienia.  
  
## <a name="message"></a>Komunikat  
 Rozpoczęto ServiceHost: "%1".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa typu usługi|`xs:string`|Element FullName CLR typu implementacji usługi.|  
|HostReference|`xs:string`|Dla usług sieci Web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ". Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
