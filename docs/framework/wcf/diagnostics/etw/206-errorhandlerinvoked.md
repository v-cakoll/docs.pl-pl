---
title: 206 — ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 40a92d77c57728249569a854eab8767ff371bca2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781930"
---
# <a name="206---errorhandlerinvoked"></a>206 — ErrorHandlerInvoked
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|206|  
|słowa kluczowe|Rozwiązywanie problemów, modelu ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane po `ErrorHandler` umożliwieniu może obsłużyć wyjątek, który wystąpił podczas operacji usługi.  
  
## <a name="message"></a>Komunikat  
 Dyspozytor wywoływane ErrorHandler typu "%1" z powodu wyjątku typu "%3". ErrorHandled == "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Imię i nazwisko CLR typu wywołanej `ErrorHandler`.|  
|Obsługiwane|`xs:unsignedByte`|`true` Jeśli program obsługi błędów obsługi błędu, w przeciwnym razie `false`.|  
|ExceptionTypeName|`xs:string`|Pełna nazwa CLR wyjątku, który został jest obsługiwany.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
