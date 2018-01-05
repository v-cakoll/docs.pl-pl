---
title: "206 — ErrorHandlerInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 43acd7ae7bbfc84e1d1ffb1bf4fa49a3dd3f191a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="206---errorhandlerinvoked"></a>206 — ErrorHandlerInvoked
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|206|  
|Słowa kluczowe|Rozwiązywanie problemów, ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany po `ErrorHandler` umożliwieniu do obsługi wyjątku, który wystąpił podczas operacji usługi.  
  
## <a name="message"></a>Komunikat  
 Dyspozytor wywołał obiekt ErrorHandler typu "%1" za pomocą wyjątku typu '%3'. Obsłużony błąd == "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Imię i nazwisko CLR typu wywołanej `ErrorHandler`.|  
|Obsługiwane|`xs:unsignedByte`|`true`Jeśli program obsługi błędów obsługi błędu, w przeciwnym razie `false`.|  
|ExceptionTypeName|`xs:string`|Element FullName CLR wyjątku, który został już obsługiwany.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ". Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
