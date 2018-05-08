---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 1136647ce668dbb69bdb8acf8ed62343831464b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
