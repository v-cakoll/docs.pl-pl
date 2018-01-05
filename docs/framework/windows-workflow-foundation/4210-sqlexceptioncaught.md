---
title: 4210 - SqlExceptionCaught
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fbcb566574e38e3c4688c16bd29a33ff7048bfa4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="4210---sqlexceptioncaught"></a>4210 - SqlExceptionCaught
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|4210|  
|Słowa kluczowe|WFInstanceStore|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że Przechwycono wyjątek SQL.  
  
## <a name="message"></a>Komunikat  
 Przechwycono wyjątek SQL o numerze %1 wiadomość %2.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Numer_błędu|xs:String|Numer błędu SQL.|  
|ExceptionMessage|xs:String|Komunikat wyjątku SQL.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
