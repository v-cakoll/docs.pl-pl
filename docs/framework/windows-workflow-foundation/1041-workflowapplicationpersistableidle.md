---
title: 1041 — WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 07be0ae603443a1ef06cb539bba7b227d7b3e325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924192"
---
# <a name="1041---workflowapplicationpersistableidle"></a>1041 — WorkflowApplicationPersistableIdle
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1041|  
|słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że aplikacja przepływu pracy jest bezczynny i stałe. Aplikacja przepływu pracy będą bezczynny, czy utrwalone.  
  
## <a name="message"></a>Komunikat  
 Identyfikator WorkflowApplication: "%1" jest bezczynny i stałe.  Zostaną podjęte następujące działania: %2.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|xs:String|Identyfikator aplikacji przepływu pracy|  
|ActionTaken|xs:String|Akcja, która zostaną wykonane w aplikacji przepływu pracy.|  
|AppDomain|xs:String|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
