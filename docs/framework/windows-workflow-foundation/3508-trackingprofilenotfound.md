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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fb5636057193fcfb59e5062f6f3833a62b4f3027
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
