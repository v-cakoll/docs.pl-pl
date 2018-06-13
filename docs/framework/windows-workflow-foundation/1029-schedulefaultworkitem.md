---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509733"
---
# <a name="1029---schedulefaultworkitem"></a>1029 - ScheduleFaultWorkItem
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1029|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że zaplanowano element roboczy FaultWorkItem.  
  
## <a name="message"></a>Komunikat  
 Zaplanowano element roboczy FaultWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'.  Wyjątek pochodzi z działania %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:String|Nazwa typu działania błędów.|  
|FaultActivityDisplayName|xs:String|Nazwa wyświetlana działania błędów.|  
|FaultActivityInstanceId|xs:String|Identyfikator wystąpienia działania błędów.|  
|ExceptionActivity|xs:String|Nazwa typu działania, która zgłosiła wyjątek.|  
|ExceptionActivityDisplayName|xs:String|Nazwa wyświetlana działania, która zgłosiła wyjątek.|  
|ExceptionActivityInstanceId|xs:String|Identyfikator wystąpienia działania, która zgłosiła wyjątek.|  
|Wyjątek|xs:String|Szczegóły wyjątku dla wyjątku|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
