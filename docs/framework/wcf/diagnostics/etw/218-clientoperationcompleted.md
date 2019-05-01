---
title: 218 — ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 83f39be84a8d62962b85652b0e39b537c92e612c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781772"
---
# <a name="218---clientoperationcompleted"></a>218 — ClientOperationCompleted
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|218|  
|słowa kluczowe|Rozwiązywanie problemów, modelu ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez klientów, po prostu, po zakończeniu operacji. W przypadku operacji jednokierunkowych jest po pomyślnym wysłaniu wiadomości. Dla operacji żądanie odpowiedź to po otrzymaniu odpowiedzi.  
  
## <a name="message"></a>Komunikat  
 Klient ukończyć wykonywania akcji "%1" skojarzonej z kontraktem "%2". Wiadomość została wysłana do "%3".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Akcja|xs:String|Nagłówek SOAP akcji w wiadomości wychodzących.|  
|Nazwa umowy|`xs:string`|Nazwa kontraktu. Przykład: ICalculator.|  
|Miejsce docelowe|`xs:string`|Adres punktu końcowego usługi, z którego wysłano wiadomość.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
