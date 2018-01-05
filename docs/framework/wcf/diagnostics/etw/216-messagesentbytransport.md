---
title: "216 — MessageSentByTransport"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ad2b32b8d1386f6cc0754070cba2b1a556219b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="216---messagesentbytransport"></a>216 — MessageSentByTransport
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|216|  
|Słowa kluczowe|Rozwiązywanie problemów, ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie występuje, gdy transport opartych na protokole TCP wysyła komunikat. Należy pamiętać, że na poziomie transportu wiele komunikatów mogą być wymieniane między klienci i usługi dla jednej operacji. Może to być spowodowane zachowanie infrastruktury, zabezpieczeń są dobrym przykładem. W związku z tym numerem **MessageSentByTransport** zdarzenia, które są emitowane różnić w zależności od powiązanie z usługą i jego konfiguracja.  
  
## <a name="message"></a>Komunikat  
 Transportu wysłała wiadomość do "%1".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|DestinationAddress|`xs:string`|Adres, którego wysłano komunikat żądania.|  
|HostReference|xs:String|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ". Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
