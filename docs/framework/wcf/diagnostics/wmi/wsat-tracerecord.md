---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 907e764cf032e595c7aba455fd4808a640f68016
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194777"
---
# <a name="wsattracerecord"></a>WSAT_TraceRecord
WSAT_TraceRecord  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
Dostęp do typu: tylko do odczytu  
  
 Identyfikator działania rekord śledzenia.  
  
### <a name="eventid"></a>Identyfikator zdarzenia  
 Typ danych: sint32  
Dostęp do typu: tylko do odczytu  
  
 Identyfikator zdarzenia Rekord śledzenia.  
  
### <a name="tracerecord"></a>TraceRecord  
 Typ danych: ciąg  
Dostęp do typu: tylko do odczytu  
  
 Rekord śledzenia  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|
