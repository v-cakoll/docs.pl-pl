---
title: 3551 — BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 89643edde5856688c762b0cf0d188bd4e7ba8a24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755535"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a>3551 — BufferOutOfOrderMessageNoBookmark
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|3551|  
|słowa kluczowe|WFServices|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 Wskazuje, że nie powiodło się wznowienie zakładki. Buforowane odbieranie operacji zostanie podjęta ponownie kiedy wystąpienie usługi jest gotowy do przetwarzania tej operacji.  
  
## <a name="message"></a>Komunikat  
 Nie można wykonać operacji "%2" na wystąpienie usługi "%1" w tej chwili. Nastąpi wtedy podjąć kolejną próbę, gdy wystąpienie usługi jest gotowy do przetwarzania tej operacji.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:String|Nazwa operacji.|  
|ServiceInstanceId|xs:String|Identyfikator wystąpienia usługi.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
