---
title: "217 — ClientOperationPrepared"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3e1b4e3aab6a6a7f94bfb3783c9e32f83557db19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="217---clientoperationprepared"></a>217 — ClientOperationPrepared
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|217|  
|Słowa kluczowe|Rozwiązywanie problemów, ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
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
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ". Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
