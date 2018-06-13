---
title: 215 — MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: a8ba90b88ef8dbe3c8651bc565da61aae16a0a4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460906"
---
# <a name="215---messagereceivedbytransport"></a>215 — MessageReceivedByTransport
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|215|  
|Słowa kluczowe|Rozwiązywanie problemów, ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
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
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName". Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
