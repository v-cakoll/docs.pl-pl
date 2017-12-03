---
title: 1004 - WorkflowInstanceAborted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 564e94d94dc5e3579dc4a80d734db78e90db91fb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1004---workflowinstanceaborted"></a>1004 - WorkflowInstanceAborted
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1004|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że wystąpienie worfklow została przerwana z powodu wyjątku.  
  
## <a name="message"></a>Komunikat  
 Obiekt WorkflowInstance o identyfikatorze: "%1" zostało przerwane z powodu wyjątku.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|`xs:string`|Identyfikator wystąpienia przepływu pracy|  
|Wyjątek|`xs:string`|Szczegóły wyjątku dla wyjątku|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
