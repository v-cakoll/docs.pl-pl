---
title: 220 — MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 9f95edf42e0b1ec19d2019773def282fc279871b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948280"
---
# <a name="220---messagesenttotransport"></a>220 — MessageSentToTransport
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Id|220|  
|słowa kluczowe|EndToEndMonitoring, rozwiązywanie problemów, ServiceModel|  
|Poziom|Informacje|  
|Ukierunkowan|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane, gdy model usługi wysyła komunikat do transportu.  
  
> [!NOTE]
> To zdarzenie nie będzie emitowane w przypadku transportów jednokierunkowych.  
  
## <a name="message"></a>Message  
 Dyspozytor wysłał komunikat do transportu. Identyfikator korelacji = = '% 1 '.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Identyfikator korelacji|`xs:GUID`|Identyfikator działania służący do skorelowania `MessageSentToTransport` zdarzenia z usługi lub klienta do jego odpowiadającego `MessageReceivedFromTransport` na drugim końcu.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Nazwa witryny sieci Web ścieżka wirtualna&#124;usługi ścieżki wirtualnej&#124;Service Path ServiceName". Przykład: "Domyślna witryna sieci Web/&#124;CalculatorApplication&#124;/CalculatorService.svc CalculatorService".|  
|Wywołując|`xs:string`|Ciąg zwracany przez element AppDomain. CurrentDomain —. FriendlyName.|
