---
title: 205 — OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: e95b6923d21307b2ef68d4a5369b3cee86540239
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458352"
---
# <a name="205---operationinvoked"></a>205 — OperationInvoked
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|205|  
|Słowa kluczowe|Rozwiązywanie problemów, ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany tuż przed domyślny Model usługi `OperationInvoker` rozpoczyna wywołanie do metody.  
  
## <a name="message"></a>Komunikat  
 Obiekt OperationInvoker wywołał metodę "%1". Informacje o obiekcie wywołującym: "%2".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa metody|`xs:string`|Nazwa metody, która została wywołana przez CLR `OperationInvoker`.|  
|Informacje o wywołującym|`xs:string`|IP adres i port numer klienta w formacie "IPAddress:PortNumber". Te dwie wartości są pobierane z właściwości komunikatu "System.ServiceModel.Channels.RemoteEndpointMessageProperty" w ramach operacji. Należy pamiętać, że dla powiązania z systemem innym niż TCP tej wartości `null`.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName". Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
