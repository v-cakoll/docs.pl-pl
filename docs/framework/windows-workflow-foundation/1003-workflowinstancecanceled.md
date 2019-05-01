---
title: 1003 — WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: c76a2dab6a95bda7f3969af07f814aba30071c7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008632"
---
# <a name="1003---workflowinstancecanceled"></a>1003 — WorkflowInstanceCanceled
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1003|  
|słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że wystąpienie przepływu pracy zostało ukończone w stanu Canceled.  
  
## <a name="message"></a>Komunikat  
 WorkflowInstance Id: "%1" została ukończona w stanu Canceled.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|Identyfikator wystąpienia przepływu pracy|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
