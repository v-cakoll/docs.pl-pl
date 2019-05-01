---
title: 4211 — QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ede74eb642c5c2c79b90cf1458db424d9f83b087
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774247"
---
# <a name="4211---queuingsqlretry"></a>4211 — QueuingSqlRetry
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|4211|  
|słowa kluczowe|WFInstanceStore|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje kolejkowania ponawiania SQL.  
  
## <a name="message"></a>Komunikat  
 Kolejkowania ponownych prób z opóźnieniem %1 MS SQL.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Opóźnienie|xs:String|Opóźnienie między ponownymi próbami.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
