---
title: 217 — ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: 5979cd8ffe0e05b61af01d2aa98c4a2c63fd432c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="217---clientoperationprepared"></a>217 — ClientOperationPrepared
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|217|  
|Słowa kluczowe|Rozwiązywanie problemów, ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez klientów tuż przed operacją jest wysyłane do usługi.  
  
## <a name="message"></a>Komunikat  
 Klient wykonuje akcję "%1" skojarzoną z kontraktem "%2". Wiadomość zostanie wysłana do "%3".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Akcja|`xs:string`|Akcja SOAP nagłówka komunikatu wychodzącego.|  
|Nazwa umowy|`xs:string`|Nazwa kontraktu. Przykład: ICalculator.|  
|Miejsce docelowe|`xs:string`|Adres punktu końcowego usługi, który komunikat jest wysyłany do.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName". Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
