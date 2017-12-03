---
title: 1041 - WorkflowApplicationPersistableIdle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b321f8c20fbd79b5e748601ee06f975dc75a7d56
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a>1041 - WorkflowApplicationPersistableIdle
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1041|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że aplikacja przepływu pracy jest bezczynny i możliwy do utrwalenia. Aplikacja przepływu pracy będą idled lub utrwalone.  
  
## <a name="message"></a>Komunikat  
 Obiekt WorkflowApplication o identyfikatorze: "%1" jest bezczynny i możliwy do utrwalenia.  Zostanie podjęta następująca Akcja: %2.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|xs:String|Identyfikator aplikacji przepływu pracy|  
|ActionTaken|xs:String|Akcja, która wpłynie na aplikacji przepływu pracy.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
