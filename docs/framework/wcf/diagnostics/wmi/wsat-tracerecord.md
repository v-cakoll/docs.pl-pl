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
ms.openlocfilehash: b4e701c2f0d669a04be7f7235c8ab1edb8ce1612
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
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
