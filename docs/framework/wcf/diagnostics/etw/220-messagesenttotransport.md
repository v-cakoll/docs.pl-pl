---
title: 220 — MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 92ec664aead15470fbed576bf157d64d984ddebf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781748"
---
# <a name="220---messagesenttotransport"></a>220 — MessageSentToTransport
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Id|220|  
|słowa kluczowe|EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane, gdy Model usług, wysyła wiadomość do transportu.  
  
> [!NOTE]
>  To zdarzenie nie będzie emitowany dla transportów jednokierunkowe.  
  
## <a name="message"></a>Komunikat  
 Dyspozytor wysłano komunikat do transportu. Identyfikator korelacji == "%1".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Identyfikator korelacji|`xs:GUID`|Działanie identyfikator używany do skorelowania `MessageSentToTransport` zdarzenie z usługi lub klienta, aby odpowiadającymi mu dostawcami `MessageReceivedFromTransport` po drugiej stronie.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
