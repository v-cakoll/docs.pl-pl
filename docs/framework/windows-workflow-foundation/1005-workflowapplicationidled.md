---
title: 1005 — WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 6bbd12e8025b6a127dbfec8e5d3690825c188c4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008606"
---
# <a name="1005---workflowapplicationidled"></a>1005 — WorkflowApplicationIdled
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1005|  
|słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że aplikacja przepływu pracy jest bezczynny.  
  
## <a name="message"></a>Komunikat  
 Identyfikator WorkflowApplication: "%1" Wystąpił bezczynności.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|Identyfikator aplikacji przepływu pracy|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
