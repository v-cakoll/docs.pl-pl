---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514485"
---
# <a name="39458---trackingrecordtruncated"></a>39458 - TrackingRecordTruncated
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|39458|  
|Słowa kluczowe|WFTracking|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że został obcięty rekord śledzenia. Zmienne/adnotacje/dane użytkownika zostały usunięte.  
  
## <a name="message"></a>Komunikat  
 Obcięty rekord śledzenia %1 został zapisany w sesji usługi ETW za pomocą dostawcy %2. Zmienne/adnotacje/dane użytkownika zostały usunięte  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs:String|Liczba rekordów śledzenia.|  
|Identyfikator dostawcy|xs:String|Identyfikator dostawcy ETW.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
