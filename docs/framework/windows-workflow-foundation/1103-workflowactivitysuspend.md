---
title: 1103 — WorkflowActivitySuspend
ms.date: 03/30/2017
ms.assetid: b64e15c2-cb2c-4314-9074-ce2c6717232e
ms.openlocfilehash: 4311bd8dc1c5e2c43bf21b411a4c52a7bfc7b230
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052784"
---
# <a name="1103---workflowactivitysuspend"></a>1103 — WorkflowActivitySuspend
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1103|  
|słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że działanie przepływu pracy zostało zawieszone.  
  
## <a name="message"></a>Komunikat  
 WorkflowInstance Id: Aktivita E2E "%1"  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|xs:String|Identyfikator wystąpienia przepływu pracy.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
