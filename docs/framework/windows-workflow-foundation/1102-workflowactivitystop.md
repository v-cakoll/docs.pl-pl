---
title: 1102 — WorkflowActivityStop
ms.date: 03/30/2017
ms.assetid: 285e5cb8-e90d-4914-ac06-e9b176ffefa2
ms.openlocfilehash: 44617e9f53be0e601424746f83b171d33956197e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052797"
---
# <a name="1102---workflowactivitystop"></a>1102 — WorkflowActivityStop
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1102|  
|słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że działanie przepływu pracy zostało zatrzymane.  
  
## <a name="message"></a>Komunikat  
 WorkflowInstance Id: Aktivita E2E "%1"  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|xs:String|Identyfikator wystąpienia przepływu pracy.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
