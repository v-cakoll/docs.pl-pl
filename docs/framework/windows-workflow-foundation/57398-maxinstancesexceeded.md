---
title: 57398 — MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: d644c25ec2dee06eea4a5fb66c30792bb650f252
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945967"
---
# <a name="57398---maxinstancesexceeded"></a>57398 — MaxInstancesExceeded
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|57398|  
|słowa kluczowe|WFServices|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 Wskazuje, że system osiągnięty limit ustawiony dla ograniczenia "MaxConcurrentInstances".  
  
## <a name="message"></a>Komunikat  
 System osiągnięty limit ustawiony dla ograniczenia "MaxConcurrentInstances". Limit dla tego ograniczania zostało ustawione na %1. Wartość ograniczenia przepustowości można zmienić, modyfikując atrybut "maxConcurrentInstances" w elemencie serviceThrottle lub modyfikując właściwość "MaxConcurrentInstances" Zachowanie elementu ServiceThrottlingBehavior.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa|xs:String|Nazwa elementu.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
