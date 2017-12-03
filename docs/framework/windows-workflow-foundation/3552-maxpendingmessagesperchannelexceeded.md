---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5455472a5b9ebdba7aea7d0384ce9cd4a9a2849d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a>3552 - MaxPendingMessagesPerChannelExceeded
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|3552|  
|Słowa kluczowe|Limit przydziału, WFServices|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 Wskazuje "MaxPendingMessagesPerChannel" Osiągnięto limit przepustnicy.  
  
## <a name="message"></a>Komunikat  
 Osiągnięto przepustnicy "MaxPendingMessagesPerChannel" limit równy "%1". Aby zwiększyć ten limit, zmień właściwość MaxPendingMessagesPerChannel obiektu bufferedreceiveservicebehavior.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Limit|xs:String|Limit przepustnicy MaxPendingMessagesPerChannel.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
