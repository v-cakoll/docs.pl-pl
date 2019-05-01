---
title: 1001 — WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: 430174b96a499fff7e0156327bb15e066ce2ca36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008645"
---
# <a name="1001---workflowapplicationcompleted"></a>1001 — WorkflowApplicationCompleted
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1001|  
|słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że aplikacja przepływu pracy zostało ukończone w stanie zamkniętym.  
  
## <a name="message"></a>Komunikat  
 WorkflowInstance Id: "%1" została zakończona w stanie zamkniętym.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|Identyfikator wystąpienia przepływu pracy|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
