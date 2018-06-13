---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: d644c25ec2dee06eea4a5fb66c30792bb650f252
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512554"
---
# <a name="57398---maxinstancesexceeded"></a>57398 - MaxInstancesExceeded
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|57398|  
|Słowa kluczowe|WFServices|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 Wskazuje, że system osiągnął limit ustawiony dla przepustnicy "MaxConcurrentInstances".  
  
## <a name="message"></a>Komunikat  
 System osiągnął limit ustawiony dla przepustnicy "MaxConcurrentInstances". Limit dla tej przepustnicy została ustawiona na %1. Wartość przepustnicy można zmienić, modyfikując atrybut "maxConcurrentInstances" elementu serviceThrottle lub modyfikując właściwość "MaxConcurrentInstances" zachowania ServiceThrottlingBehavior.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa|xs:String|Nazwa elementu.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
