---
title: 3552 — MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945941"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a>3552 — MaxPendingMessagesPerChannelExceeded
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|3552|  
|słowa kluczowe|Limit przydziału, WFServices|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 Wskazuje ograniczania "MaxPendingMessagesPerChannel" Osiągnięto limit.  
  
## <a name="message"></a>Komunikat  
 Ograniczenie "MaxPendingMessagesPerChannel" limit "%1" został trafiony. Aby zwiększyć ten limit, Dopasuj właściwość MaxPendingMessagesPerChannel BufferedReceiveServiceBehavior.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Limit|xs:String|Limit przepustowości MaxPendingMessagesPerChannel.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
