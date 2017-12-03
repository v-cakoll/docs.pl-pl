---
title: "Obsługa błędów działań w WF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a8b7ed6837e9ee88e85324ed5d7a2b9ff3e419a9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="error-handling-activities-in-wf"></a>Obsługa błędów działań w WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]Implementowanie obsługi błędów i odzyskiwania zawiera kilka działań dostarczane przez system. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Wyjątki](../../../docs/framework/windows-workflow-foundation/exceptions.md).  
  
## <a name="error-handling-activities"></a>Błąd obsługi działań  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|Ponownie zgłasza wyjątek ostatniego z poziomu `TryCatch` działania.|  
|<xref:System.Activities.Statements.Throw>|Zgłasza wyjątek.|  
|<xref:System.Activities.Statements.TryCatch>|Implementuje obsługi wyjątków.|
