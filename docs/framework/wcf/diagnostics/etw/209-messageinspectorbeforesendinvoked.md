---
title: 209 — MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 24184c24b9affdf3a56d7968c02cf5354d690749
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781886"
---
# <a name="209---messageinspectorbeforesendinvoked"></a>209 — MessageInspectorBeforeSendInvoked
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|209|  
|słowa kluczowe|Rozwiązywanie problemów, modelu ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane po modelu usługi zostało wywołane `BeforeSend` metody w Inspektorze wiadomości.  
  
## <a name="message"></a>Komunikat  
 Dyspozytor wywoływane "BeforeSendRequest" na MessageInspector typu "%1".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Imię i nazwisko CLR typu wywołanej `MessageInspector`.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
