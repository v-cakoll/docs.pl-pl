---
title: 3508 - TrackingProfileNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34812b6ddefb69c053cfefa91d7227a7bf15f42e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|3508|  
|Słowa kluczowe|WFServices|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 Oznacza TrackingProfile nie został znaleziony w pliku konfiguracji lub obiekt ActivityDefinitionId jest niezgodny z profilu.  
  
## <a name="message"></a>Komunikat  
 TrackingProfile "%1" dla obiektu ActivityDefinitionId "%2" nie można odnaleźć. Nie można odnaleźć TrackingProfile w pliku konfiguracji, albo obiekt ActivityDefinitionId jest niezgodny.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|TrackingProfile|xs:String|Nazwa profilu śledzenia.|  
|Obiekt ActivityDefinitionId|xs:String|Identyfikator definicji działania.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
