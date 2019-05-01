---
title: 221 — MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 98dbf2728242fa73b3e54b7cf32f9e227e5251b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781722"
---
# <a name="221---messagereceivedfromtransport"></a>221 — MessageReceivedFromTransport
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|221|  
|słowa kluczowe|EndToEndMonitoring, rozwiązywania problemów, modelu ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane, gdy Model usług otrzymuje komunikat z transportu.  
  
## <a name="message"></a>Komunikat  
 Dyspozytor otrzymał komunikat z transportu. Identyfikator korelacji == "%1".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Identyfikator korelacji|`xs:GUID`|Działanie identyfikator używany do skorelowania `MessageSentToTransport` zdarzenie z usługi lub klienta, aby odpowiadającymi mu dostawcami `MessageReceivedFromTransport` po drugiej stronie.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
