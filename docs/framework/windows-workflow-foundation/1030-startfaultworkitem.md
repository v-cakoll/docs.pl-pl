---
title: 1030 — StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 3848d644e77041a62a52eb2eae5eeef286dfe334
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924322"
---
# <a name="1030---startfaultworkitem"></a>1030 — StartFaultWorkItem
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1030|  
|słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że FaultWorkItem Trwa uruchamianie wykonywania.  
  
## <a name="message"></a>Komunikat  
 Rozpoczynanie wykonywania FaultWorkItem dla działania "%1", DisplayName: "%2", InstanceId: "%3".  Wyjątek został rozpropagowany działania "%4", DisplayName: '%5', InstanceId: '%6'.  
  
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
