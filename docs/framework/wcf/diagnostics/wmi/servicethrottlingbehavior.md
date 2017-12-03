---
title: ServiceThrottlingBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59f85a148d6707876a4df512d5cfbd07ca0e54b7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="servicethrottlingbehavior"></a>ServiceThrottlingBehavior
ServiceThrottlingBehavior  
  
## <a name="syntax"></a>Składnia  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasy zachowania ServiceThrottlingBehavior nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasy zachowania ServiceThrottlingBehavior ma następujące właściwości:  
  
### <a name="maxconcurrentcalls"></a>maxConcurrentCalls  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba komunikatów aktywnie przetwarzanych w obrębie wszystkich obiektów dyspozytora w elemencie ServiceHost.  
  
### <a name="maxconcurrentinstances"></a>MaxConcurrentInstances  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba obiektów usługi, które mogą być wykonywane w tym samym czasie.  
  
### <a name="maxconcurrentsessions"></a>MaxConcurrentSessions  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalna liczba sesji, które host może zaakceptować jednocześnie.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
