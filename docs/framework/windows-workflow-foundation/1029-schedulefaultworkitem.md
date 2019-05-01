---
title: 1029 — ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924361"
---
# <a name="1029---schedulefaultworkitem"></a>1029 — ScheduleFaultWorkItem
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1029|  
|słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że FaultWorkItem została zaplanowana.  
  
## <a name="message"></a>Komunikat  
 FaultWorkItem została zaplanowana dla działania "%1", DisplayName: "%2", InstanceId: "%3".  Wyjątek został rozpropagowany działania "%4", DisplayName: '%5', InstanceId: '%6'.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:String|Nazwa typu aktywności błędów.|  
|FaultActivityDisplayName|xs:String|Nazwa wyświetlana aktywności błędów.|  
|FaultActivityInstanceId|xs:String|Identyfikator wystąpienia aktywności błędów.|  
|ExceptionActivity|xs:String|Nazwa typu działania, który wygenerował wyjątek.|  
|ExceptionActivityDisplayName|xs:String|Nazwa wyświetlana działania, który wygenerował wyjątek.|  
|ExceptionActivityInstanceId|xs:String|Identyfikator wystąpienia działania, który wygenerował wyjątek.|  
|Wyjątek|xs:String|Szczegóły wyjątku, dla wyjątku|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
