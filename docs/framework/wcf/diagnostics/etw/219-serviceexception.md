---
title: "219 — ServiceException"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dd38ab45bceeee577d9e33f699a03a81c09dfc99
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="219---serviceexception"></a>219 — ServiceException
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|219|  
|Słowa kluczowe|EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceModel|  
|Poziom|Błąd|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany, gdy usługa WCF napotka nieobsługiwany wyjątek. Dotyczy to również nieobsługiwanych wyjątków podczas aktywacji, podczas przetwarzania komunikatu i w kodzie użytkownika.  
  
## <a name="message"></a>Komunikat  
 Podczas przetwarzania komunikatu wystąpił nieobsługiwany wyjątek typu "%2". ToString pełny wyjątek: %1.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|Wyniku wywołania metody `ToString`() na wyjątku CLR.|  
|ExceptionTypeName|`xs:string`|Element FullName CLR typu wyjątku.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ". Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
