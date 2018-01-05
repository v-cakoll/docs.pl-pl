---
title: "215 — MessageReceivedByTransport"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8bf2336d1b5c9dda1dac2b38305d944a822bd253
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="215---messagereceivedbytransport"></a>215 — MessageReceivedByTransport
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|215|  
|Słowa kluczowe|Rozwiązywanie problemów, ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie występuje, gdy transport opartych na protokole TCP odbiera komunikat. Należy pamiętać, że na poziomie transportu, wiele komunikatów mogą być wymieniane między klienci i usługi dla jednej operacji. Może to być spowodowane zachowanie infrastruktury, zabezpieczeń jest dobrym przykładem. W związku z tym numerem `MessageReceivedByTransport` zdarzenia, które są emitowane różnić w zależności od powiązanie z usługą i jego konfiguracja.  
  
> [!NOTE]
>  To zdarzenie nie jest emitowany dla transportów jednokierunkowe.  
  
## <a name="message"></a>Komunikat  
 Transportu odebrała wiadomość od "%1".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Adres nasłuchiwania|`xs:string`|Adres, który odebrał wiadomość.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ". Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
