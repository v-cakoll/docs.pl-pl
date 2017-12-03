---
title: "Hosting opcje przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72c9c2078f694a1739a7f33689a0d8275d786937
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-hosting-options"></a>Hosting opcje przepływu pracy
Większość [!INCLUDE[wf](../../../includes/wf-md.md)] przykłady użycia przepływy pracy, które znajdują się w aplikacji konsoli, ale nie jest to realistyczne scenariusz dla przepływów pracy w rzeczywistych. Przepływy pracy w aplikacjach biznesowych rzeczywiste będzie obsługiwana w trwałych procesów — usługi systemu Windows utworzone przez dewelopera lub aplikacji serwera, takich jak [!INCLUDE[iisver](../../../includes/iisver-md.md)] lub AppFabric. Dostępne są następujące różnice między tych metod.  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>Hosting przepływów pracy w programie IIS z AppFabric systemu Windows  
 Za pomocą usług IIS z AppFabric jest preferowanym hosta dla przepływów pracy. Aplikacja hosta dla przepływów pracy za pomocą AppFabric to usługa aktywacji systemu Windows, która usuwa zależność od protokołu HTTP za pośrednictwem usług IIS tylko.  
  
## <a name="hosting-workflows-in-iis-alone"></a>Hosting przepływów pracy w programie IIS samodzielnie  
 Przy użyciu [!INCLUDE[iisver](../../../includes/iisver-md.md)] samodzielnie nie jest zalecane, ponieważ istnieją do zarządzania i monitorowania z AppFabric dostępne narzędzia, które ułatwiają utrzymanie uruchomionych aplikacji. Przepływy pracy powinien być obsługiwany tylko na [!INCLUDE[iisver](../../../includes/iisver-md.md)] tylko w przypadku infrastruktury problemy z przenoszeniem do AppFabric.  
  
> [!WARNING]
>  [!INCLUDE[iisver](../../../includes/iisver-md.md)]przeprowadza recykling pul aplikacji i okresowo z różnych przyczyn. Podczas odtwarzania puli aplikacji, usługi IIS zatrzymuje akceptowanie komunikatów do starego pulę i tworzy nową pulę aplikacji do akceptowania nowych żądań. Jeśli przepływ pracy będzie nadal występować po wysłaniu odpowiedzi, [!INCLUDE[iisver](../../../includes/iisver-md.md)] nie będą świadomi pracy i może odtworzyć obsługi puli aplikacji. Jeśli tak się stanie, spowoduje przerwanie przepływu pracy i zarejestruje usługi śledzenia [1004 - WorkflowInstanceAborted](../../../docs/framework/windows-workflow-foundation/1004-workflowinstanceaborted.md) wiadomości z puste pole przyczyny.  
>   
>  Jeśli jest używana opcja trwałości, host jawnie należy ponownie uruchomić wystąpień zostało przerwane z ostatniego punktu trwałości.  
>   
>  Użycie AppFabric usługi przepływu pracy zarządzania po pewnym czasie wznowić przepływ pracy z ostatniego punktu pomyślne trwałości, jeśli używane jest trwałości. Jeśli jest używana żadna trwałość i przepływu pracy wykonuje operacje poza wzorcem żądanie/odpowiedź, dane zostaną utracone, jeśli przerwanie przepływu pracy.  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>Hosting przepływ pracy w niestandardowych usługi systemu Windows  
 Tworzenie usługi niestandardowego przepływu pracy do przepływu pracy obsługi będzie wymagać deweloperowi zduplikowane dużo funkcjonalność out-of-box AppFabric, ale pozwoli większą elastyczność z funkcji niestandardowych. Tylko należy traktować tę opcję, jeśli AppFabric nie okaże się, że opcja.
