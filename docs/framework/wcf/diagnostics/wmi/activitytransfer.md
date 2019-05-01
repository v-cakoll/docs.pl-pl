---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 936e870c1ec991e2e33acf8a08ccc93975989679
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964298"
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
  
- Typ danych: obiekt  
    Typ dostępu: tylko do odczytu  
  
- Identyfikator działania  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
- Typ danych: obiekt  
    Typ dostępu: tylko do odczytu  
  
- Identyfikator działania powiązane  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel.|
