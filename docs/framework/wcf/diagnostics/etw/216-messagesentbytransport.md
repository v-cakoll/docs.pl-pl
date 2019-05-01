---
title: 216 — MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: fa21568e4c8c38eefe359c417d47ec0a9d30a7c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781813"
---
# <a name="216---messagesentbytransport"></a>216 — MessageSentByTransport
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|216|  
|słowa kluczowe|Rozwiązywanie problemów, modelu ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie występuje, gdy transport oparte na protokole TCP jest wysyłana wiadomość. Należy pamiętać, że na poziomie transportu wiele wiadomości mogą być wymieniane między klientów i usług dla pojedynczej operacji. Może to być spowodowane zachowanie infrastruktury, zabezpieczeń, które są dobrym przykładem. W związku z tym, liczba **MessageSentByTransport** zdarzenia, które są emitowane różnią się zależnie od powiązania z usługą i jego konfiguracji.  
  
## <a name="message"></a>Komunikat  
 Transport wiadomości do "%1".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|DestinationAddress|`xs:string`|Adres, na który wysłano komunikat żądania.|  
|HostReference|xs:String|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
