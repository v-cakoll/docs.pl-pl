---
title: 219 — ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: eb4289c0346c9e1d9481347d69db8c5f007e4325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781735"
---
# <a name="219---serviceexception"></a>219 — ServiceException
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|219|  
|słowa kluczowe|EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|Poziom|Błąd|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane, gdy usługa WCF napotkał nieobsługiwany wyjątek. Obejmuje to nieobsługiwane wyjątki podczas aktywacji, podczas przetwarzania komunikatu, a w kodzie użytkownika.  
  
## <a name="message"></a>Komunikat  
 Wystąpił nieobsługiwany wyjątek typu "%2" podczas przetwarzania komunikatu. ToString — pełny wyjątek: %1.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|Wynik wywołania metody `ToString`() na wyjątek CLR.|  
|ExceptionTypeName|`xs:string`|Pełna nazwa CLR typu wyjątku.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
