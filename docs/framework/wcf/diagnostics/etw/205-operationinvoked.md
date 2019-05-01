---
title: 205 — OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: e95b6923d21307b2ef68d4a5369b3cee86540239
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781982"
---
# <a name="205---operationinvoked"></a>205 — OperationInvoked
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|205|  
|słowa kluczowe|Rozwiązywanie problemów, modelu ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane bezpośrednio przed domyślny Model usług `OperationInvoker` rozpoczyna się wywołanie do metody.  
  
## <a name="message"></a>Komunikat  
 OperationInvoker wywołał metodę "%1". Informacje o wywołującym: "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa metody|`xs:string`|Nazwa aparatu CLR metody, która została wywołana przez `OperationInvoker`.|  
|Informacje o wywołującym|`xs:string`|Adres IP i port numer klienta w formacie "IPAddress:PortNumber". Te dwie wartości są pobierane z właściwości komunikatu "System.ServiceModel.Channels.RemoteEndpointMessageProperty" w kontekście operacji. Należy pamiętać, że na inny niż TCP powiązania tej wartości `null`.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
