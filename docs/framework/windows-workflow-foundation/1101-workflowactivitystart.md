---
title: 1101 - WorkflowActivityStart
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd7cbf98cb51005fbae5b56a0136e0bb3efe08be
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1101---workflowactivitystart"></a>1101 - WorkflowActivityStart
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1101|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że działanie przepływu pracy została uruchomiona.  
  
## <a name="message"></a>Komunikat  
 Obiekt WorkflowInstance o identyfikatorze: '%1' E2E działania  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|xs:String|Identyfikator wystąpienia przepływu pracy.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
