---
title: Hosting opcje przepływu pracy
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: 7713044e40532c431d090b1cb1795876ead2a899
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="workflow-hosting-options"></a>Hosting opcje przepływu pracy
Większość przykładów programu Windows Workflow Foundation (WF) używane przepływy pracy, które znajdują się w aplikacji konsoli, ale nie jest to realistyczne scenariusz dla przepływów pracy w rzeczywistych. Przepływy pracy w aplikacjach biznesowych rzeczywiste będzie obsługiwana w trwałych procesów — usługi systemu Windows utworzone przez dewelopera lub aplikacji serwera, takich jak [!INCLUDE[iisver](../../../includes/iisver-md.md)] lub AppFabric. Dostępne są następujące różnice między tych metod.  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>Hosting przepływów pracy w programie IIS z AppFabric systemu Windows  
 Za pomocą usług IIS z AppFabric jest preferowanym hosta dla przepływów pracy. Aplikacja hosta dla przepływów pracy za pomocą AppFabric to usługa aktywacji systemu Windows, która usuwa zależność od protokołu HTTP za pośrednictwem usług IIS tylko.  
  
## <a name="hosting-workflows-in-iis-alone"></a>Hosting przepływów pracy w programie IIS samodzielnie  
 Przy użyciu [!INCLUDE[iisver](../../../includes/iisver-md.md)] samodzielnie nie jest zalecane, ponieważ istnieją do zarządzania i monitorowania z AppFabric dostępne narzędzia, które ułatwiają utrzymanie uruchomionych aplikacji. Przepływy pracy powinien być obsługiwany tylko na [!INCLUDE[iisver](../../../includes/iisver-md.md)] tylko w przypadku infrastruktury problemy z przenoszeniem do AppFabric.  
  
> [!WARNING]
>  [!INCLUDE[iisver](../../../includes/iisver-md.md)] przeprowadza recykling pul aplikacji i okresowo z różnych przyczyn. Podczas odtwarzania puli aplikacji, usługi IIS zatrzymuje akceptowanie komunikatów do starego pulę i tworzy nową pulę aplikacji do akceptowania nowych żądań. Jeśli przepływ pracy będzie nadal występować po wysłaniu odpowiedzi, [!INCLUDE[iisver](../../../includes/iisver-md.md)] nie będą świadomi pracy i może odtworzyć obsługi puli aplikacji. Jeśli tak się stanie, spowoduje przerwanie przepływu pracy i zarejestruje usługi śledzenia [1004 - WorkflowInstanceAborted](../../../docs/framework/windows-workflow-foundation/1004-workflowinstanceaborted.md) wiadomości z puste pole przyczyny.  
>   
>  Jeśli jest używana opcja trwałości, host jawnie należy ponownie uruchomić wystąpień zostało przerwane z ostatniego punktu trwałości.  
>   
>  Użycie AppFabric usługi przepływu pracy zarządzania po pewnym czasie wznowić przepływ pracy z ostatniego punktu pomyślne trwałości, jeśli używane jest trwałości. Jeśli jest używana żadna trwałość i przepływu pracy wykonuje operacje poza wzorcem żądanie/odpowiedź, dane zostaną utracone, jeśli przerwanie przepływu pracy.  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>Hosting przepływ pracy w niestandardowych usługi systemu Windows  
 Tworzenie usługi niestandardowego przepływu pracy do przepływu pracy obsługi będzie wymagać deweloperowi zduplikowane dużo funkcjonalność out-of-box AppFabric, ale pozwoli większą elastyczność z funkcji niestandardowych. Tylko należy traktować tę opcję, jeśli AppFabric nie okaże się, że opcja.
