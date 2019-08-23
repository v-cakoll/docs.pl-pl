---
title: 215 — MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: aa1ad30526aa65501e5d9875d3877631ca00879b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964184"
---
# <a name="215---messagereceivedbytransport"></a>215 — MessageReceivedByTransport
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|id|215|  
|słowa kluczowe|Rozwiązywanie problemów, ServiceModel|  
|Poziom|Informacje|  
|Ukierunkowan|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie występuje, gdy transport oparty na protokole TCP odbierze komunikat. Należy pamiętać, że na poziomie transportu wiele komunikatów może być wymienianych między klientami i usługami w ramach jednej operacji. Może to być spowodowane zachowaniem infrastruktury, tym dobrym przykładem. W związku z tym liczba `MessageReceivedByTransport` wyemitowanych zdarzeń zależy od powiązania usługi i jego konfiguracji.  
  
> [!NOTE]
> To zdarzenie nie jest emitowane w przypadku transportów jednokierunkowych.  
  
## <a name="message"></a>Message  
 Transport odebrał komunikat z '% 1 '.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Adres nasłuchiwania|`xs:string`|Adres, który odebrał wiadomość.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Nazwa witryny sieci Web ścieżka wirtualna&#124;usługi ścieżki wirtualnej&#124;Service Path ServiceName". Przykład: "Domyślna witryna sieci Web/&#124;CalculatorApplication&#124;/CalculatorService.svc CalculatorService".|  
|Wywołując|`xs:string`|Ciąg zwracany przez element AppDomain. CurrentDomain —. FriendlyName.|
