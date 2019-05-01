---
title: 1006 — WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 471f3ecea66ebbd07a09686ab536a84b25d46e6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924712"
---
# <a name="1006---workflowapplicationunhandledexception"></a>1006 — WorkflowApplicationUnhandledException
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|1006|  
|słowa kluczowe|WFRuntime|  
|Poziom|Błąd|  
|Kanał|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>Opis  
 Wskazuje, że aplikacja przepływu pracy napotkał nieobsługiwany wyjątek.  
  
## <a name="message"></a>Komunikat  
 WorkflowInstance Id: "%1" napotkał nieobsługiwany wyjątek.  Wyjątek pochodzi z działania "%2", DisplayName: "%3".  Zostaną podjęte następujące działania: %4.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|Identyfikator wystąpienia przepływu pracy|  
|Wyjątek|`xs:string`|Szczegóły wyjątku, dla wyjątku|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|
