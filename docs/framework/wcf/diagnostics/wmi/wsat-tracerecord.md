---
title: WSAT_TraceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d24f74d4086a5499d3bfd4ef6183d377528acc21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wsattracerecord"></a>WSAT_TraceRecord
WSAT_TraceRecord  
  
## <a name="syntax"></a>Składnia  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa WSAT_TraceRecord nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa WSAT_TraceRecord ma następujące właściwości:  
  
### <a name="activityid"></a>Identyfikator działania  
 Typ danych: obiekt  
Dostęp typu: tylko do odczytu  
  
 Identyfikator działania rekordu śledzenia.  
  
### <a name="eventid"></a>Identyfikator zdarzenia  
 Typ danych: sint32  
Dostęp typu: tylko do odczytu  
  
 Identyfikator zdarzenia Rekord śledzenia.  
  
### <a name="tracerecord"></a>TraceRecord  
 Typ danych: ciąg  
Dostęp typu: tylko do odczytu  
  
 Rekord śledzenia  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|
