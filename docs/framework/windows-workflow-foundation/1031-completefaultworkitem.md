---
title: 1031 — CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008801"
---
# <a name="1031---completefaultworkitem"></a>1031 — CompleteFaultWorkItem
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1031|  
|słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że FaultWorkItem zostało zakończone.  
  
## <a name="message"></a>Komunikat  
 FaultWorkItem zostało ukończone dla działania "%1", DisplayName: "%2", InstanceId: "%3". Wyjątek został rozpropagowany działania "%4", DisplayName: '%5', InstanceId: '%6'.  
  
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
