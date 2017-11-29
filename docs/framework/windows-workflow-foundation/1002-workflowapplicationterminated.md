---
title: 1002 - WorkflowApplicationTerminated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 54ef06c3aded628e18325b78f55e80e4470ecd01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1002---workflowapplicationterminated"></a>1002 - WorkflowApplicationTerminated
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1002|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że aplikacja przepływu pracy zostało przerwane w stanie Faulted z wyjątkiem.  
  
## <a name="message"></a>Komunikat  
 Obiekt WorkflowApplication o identyfikatorze: '%1' została zakończona. Została ukończona w stan końcowy: Faulted z wyjątkiem.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|WorkflowApplicationId|`xs:string`|Identyfikator aplikacji przepływu pracy|  
|Wyjątek|`xs:string`|Szczegóły wyjątku dla wyjątku|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
