---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 480670f19407321eb0928d07752936b2ece1f7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
