---
title: ActivityTransfer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c1caf0ae27efce858328e5db88434253be61d50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="activitytransfer"></a>ActivityTransfer
Zdarzenie transferu aktywności  
  
## <a name="syntax"></a>Składnia  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa ActivityTransfer nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa ActivityTransfer ma następujące właściwości:  
  
### <a name="activityid"></a>Identyfikator działania  
  
-   Typ danych: obiekt  
    Dostęp typu: tylko do odczytu  
  
-   Identyfikator działania  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
-   Typ danych: obiekt  
    Dostęp typu: tylko do odczytu  
  
-   Identyfikator działania pokrewne  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel.|
