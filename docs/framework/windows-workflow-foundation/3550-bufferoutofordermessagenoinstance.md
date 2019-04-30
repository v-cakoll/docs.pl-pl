---
title: 3550 — BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 1af943e23aa643c6614b946175c0b1854a7ceb62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755587"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a>3550 — BufferOutOfOrderMessageNoInstance
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|3550|  
|słowa kluczowe|WFServices|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 Wskazuje, że buforowane odbieranie nie powiodło się. Operacja zostanie podjęta ponownie, gdy wystąpienie usługi jest gotowy do przetwarzania tej operacji.  
  
## <a name="message"></a>Komunikat  
 W tej chwili nie można wykonać operacji "%1". Nastąpi wtedy podjąć kolejną próbę, gdy wystąpienie usługi jest gotowy do przetwarzania tej operacji.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:String|Nazwa operacji.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
