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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5ba5e4aa8e1338321838e40db7d976107315ef64
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
