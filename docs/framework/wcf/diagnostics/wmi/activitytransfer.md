---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 936e870c1ec991e2e33acf8a08ccc93975989679
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50034433"
---
# <a name="activitytransfer"></a>ActivityTransfer
Zdarzenia transferu aktywności  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
    Dostęp do typu: tylko do odczytu  
  
-   Identyfikator działania  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
-   Typ danych: obiekt  
    Dostęp do typu: tylko do odczytu  
  
-   Identyfikator działania powiązane  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel.|
