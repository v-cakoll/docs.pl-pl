---
title: Opcje hostowania przepływu pracy
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: 2a03c7b5e15b76eabc714f44624f04d3385720d4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713322"
---
# <a name="workflow-hosting-options"></a>Opcje hostowania przepływu pracy
Większość przykładów programu Windows Workflow Foundation (WF) korzystanie z przepływów pracy, które znajdują się w aplikacji konsoli, ale nie jest to realistyczny scenariusz dla przepływów pracy w rzeczywistych warunkach. Przepływy pracy w aplikacjach biznesowych rzeczywiste będzie obsługiwana w trwałych procesów — usługa Windows opracowane przez dewelopera lub aplikację serwera, takich jak [!INCLUDE[iisver](../../../includes/iisver-md.md)] lub rozwiązania AppFabric. Dostępne są następujące różnice w tych metod.  
  
## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>Hostowanie przepływów pracy w usługach IIS przy użyciu rozwiązania AppFabric Windows  
 Za pomocą usług IIS przy użyciu rozwiązania AppFabric jest preferowany hosta dla przepływów pracy. Aplikacja hosta dla przepływów pracy przy użyciu rozwiązania AppFabric to usługa aktywacji Windows, która usuwa zależność od protokołu HTTP za pośrednictwem usług IIS samodzielnie.  
  
## <a name="hosting-workflows-in-iis-alone"></a>Hostowanie przepływów pracy w usługach IIS samodzielnie  
 Za pomocą [!INCLUDE[iisver](../../../includes/iisver-md.md)] samodzielnie nie jest zalecane, ponieważ istnieją narzędzia dostępne przy użyciu rozwiązania AppFabric, które ułatwiają utrzymanie działających aplikacji, zarządzania i monitorowania. Przepływy pracy powinien być obsługiwany tylko na [!INCLUDE[iisver](../../../includes/iisver-md.md)] tylko, jeśli występują problemy infrastruktury z przeniesieniem do rozwiązania AppFabric.  
  
> [!WARNING]
>  [!INCLUDE[iisver](../../../includes/iisver-md.md)] przeprowadza recykling pul aplikacji i okresowo z różnych powodów. Pula aplikacji zostanie odtworzona, usługi IIS zatrzymuje akceptowanie komunikatów do starego puli i tworzy nową pulę aplikacji, aby zaakceptować nowe żądania. Jeśli przepływ pracy kontynuuje pracę po wysłaniu odpowiedzi, [!INCLUDE[iisver](../../../includes/iisver-md.md)] nie będzie pamiętać o wykonywanej pracy i może odtworzyć hostingu pulę aplikacji. Jeśli tak się stanie, przepływ pracy zostanie przerwany i zarejestruje usługi śledzenia [1004 — WorkflowInstanceAborted](1004-workflowinstanceaborted.md) wiadomości z pustym polem przyczyna.  
>   
>  Jeśli trwałości jest używany, host jawnie ponownie uruchomić wystąpienia przerwane z ostatniego punktu stanu trwałego.  
>   
>  Użycie rozwiązania AppFabric usługi zarządzania przepływu pracy po pewnym czasie zostanie wznowiona przepływu pracy od ostatniego punktu pomyślne trwałości, jeśli trwałości jest używany. Jeśli jest używana żadna trwałość i przepływ pracy wykonuje operacje poza wzorzec żądań/odpowiedzi, dane zostaną utracone podczas przerywa przepływ pracy.  
  
## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>Hostowanie przepływu pracy w usłudze Windows niestandardowe  
 Tworzenie usługi przepływu pracy niestandardowych do przepływu pracy obsługi będzie wymagać deweloperowi zduplikowane mnóstwo funkcjonalność out-of-box AppFabric, ale pozwoli uzyskać większą elastyczność przy użyciu funkcji niestandardowych. Tę opcję, należy rozważyć, tylko jeśli AppFabric nie okaże się, że opcja.
