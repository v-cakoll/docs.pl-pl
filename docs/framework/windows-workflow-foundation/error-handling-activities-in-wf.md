---
title: Obsługa błędów działań w WF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1c0459dd562f6292a8fe9a42f8b1b48cd175516a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="error-handling-activities-in-wf"></a>Obsługa błędów działań w WF
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Implementowanie obsługi błędów i odzyskiwania zawiera kilka działań dostarczane przez system. Aby uzyskać więcej informacji, zobacz [wyjątki](../../../docs/framework/windows-workflow-foundation/exceptions.md).  
  
## <a name="error-handling-activities"></a>Błąd obsługi działań  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|Ponownie zgłasza wyjątek ostatniego z poziomu `TryCatch` działania.|  
|<xref:System.Activities.Statements.Throw>|Zgłasza wyjątek.|  
|<xref:System.Activities.Statements.TryCatch>|Implementuje obsługi wyjątków.|
