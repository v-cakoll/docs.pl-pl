---
title: 1002 — WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: 01c9aba6e863e07a1a999a28fccefbab95a34d5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008658"
---
# <a name="1002---workflowapplicationterminated"></a>1002 — WorkflowApplicationTerminated
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1002|  
|słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że aplikacja przepływu pracy został zakończony w stanie Faulted z powodu wyjątku.  
  
## <a name="message"></a>Komunikat  
 Identyfikator WorkflowApplication: "%1" została zakończona. Ukończono się w stanie Faulted z powodu wyjątku.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|`xs:string`|Identyfikator aplikacji przepływu pracy|  
|Wyjątek|`xs:string`|Szczegóły wyjątku, dla wyjątku|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
