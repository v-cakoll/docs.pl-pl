---
title: 39458 — TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774416"
---
# <a name="39458---trackingrecordtruncated"></a>39458 — TrackingRecordTruncated
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|39458|  
|słowa kluczowe|WFTracking|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że rekord śledzenia zostały obcięte. Dane adnotacje/zmienne/użytkownika zostały usunięte.  
  
## <a name="message"></a>Komunikat  
 Obcięte śledzenia rekord %1 zapisywane do sesji ETW za pomocą dostawcy %2. Usunięto użytkownika/zmienne/adnotacji danych  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs:String|Liczba rekordów śledzenia.|  
|ProviderId|xs:String|Identyfikator dostawcy funkcji ETW.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
