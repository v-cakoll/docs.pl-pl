---
title: 215 — MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: a8ba90b88ef8dbe3c8651bc565da61aae16a0a4a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781839"
---
# <a name="215---messagereceivedbytransport"></a>215 — MessageReceivedByTransport
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|215|  
|słowa kluczowe|Rozwiązywanie problemów, modelu ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie występuje, gdy transport oparte na protokole TCP odbiera komunikat. Należy pamiętać, że na poziomie transportu, wiele wiadomości mogą być wymieniane między klientów i usług dla pojedynczej operacji. Może to być spowodowane zachowanie infrastruktury, zabezpieczenia są dobrym przykładem. W związku z tym, liczba `MessageReceivedByTransport` zdarzenia, które są emitowane różnią się zależnie od powiązania z usługą i jego konfiguracji.  
  
> [!NOTE]
>  To zdarzenie nie jest emitowane dla transportów jednokierunkowe.  
  
## <a name="message"></a>Komunikat  
 Transport otrzymał komunikat z "%1".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Adresu nasłuchiwania|`xs:string`|Adres, który otrzymał komunikat.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
