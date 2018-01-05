---
title: 4211 - QueuingSqlRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ffd44cf9d2333b22e3be809d05f2fa8c33d4cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="4211---queuingsqlretry"></a>4211 - QueuingSqlRetry
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|4211|  
|Słowa kluczowe|WFInstanceStore|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje kolejkowania SQL ponów próbę.  
  
## <a name="message"></a>Komunikat  
 Kolejkowanie ponawiania SQL z opóźnieniem %1 MS.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Opóźnienie|xs:String|Opóźnienie między kolejnymi próbami.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
