---
title: Opcje hostowania przepływu pracy
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: 4eaed147f312f3963aa1ca1d4f5dbe010c4189ad
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037824"
---
# <a name="workflow-hosting-options"></a>Opcje hostowania przepływu pracy
Większość przykładów Windows Workflow Foundation (WF) używa przepływów pracy, które są hostowane w aplikacji konsolowej, ale nie jest to realistyczny scenariusz dla rzeczywistych przepływów pracy. Przepływy pracy w rzeczywistych aplikacjach firmowych będą hostowane w trwałych procesach — w przypadku usługi systemu Windows opracowanej przez dewelopera lub aplikacji serwera, takiej jak IIS 7,0 lub AppFabric. Różnice między tymi podejściami są następujące.

## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a>Hostowanie przepływów pracy w usługach IIS przy użyciu programu Windows AppFabric

Korzystanie z usług IIS z programem AppFabric jest preferowanym hostem dla przepływów pracy. Aplikacja hosta dla przepływów pracy korzystających z programu AppFabric to usługa aktywacji systemu Windows, która usuwa zależność od samego protokołu HTTP przez usługi IIS.

## <a name="hosting-workflows-in-iis-alone"></a>Obsługa przepływów pracy w programie IIS

Nie zaleca się korzystania wyłącznie z usług IIS 7,0, ponieważ dostępne są narzędzia do zarządzania i monitorowania z programem AppFabric, które ułatwiają konserwację uruchomionych aplikacji. Przepływy pracy powinny być hostowane tylko w usługach IIS 7,0, tylko jeśli istnieją problemy związane z infrastrukturą dotyczące przechodzenia do programu AppFabric.

> [!WARNING]
> Usługi IIS 7,0 okresowo odtwarza pule aplikacji z różnych powodów. Gdy pula aplikacji jest odtwarzana, usługi IIS nie akceptują komunikatów do starej puli i tworzy wystąpienie nowej puli aplikacji, aby akceptować nowe żądania. Jeśli przepływ pracy będzie kontynuował pracę po wysłaniu odpowiedzi, usługi IIS 7,0 nie będą znać wykonywanej pracy i mogą odtworzyć pulę aplikacji hostingowych. W takim przypadku przepływ pracy zostanie przerwany, a usługi śledzenia będą rejestrować komunikat [1004-WorkflowInstanceAborted](1004-workflowinstanceaborted.md) z pustym polem przyczyna.
>
> Jeśli jest używana wartość trwałości, host musi jawnie ponownie uruchomić przerwane wystąpienia z ostatniego punktu trwałości.
>
> Jeśli jest używany program AppFabric, usługa zarządzania przepływem pracy ostatecznie wznowi przepływ pracy od ostatniego pomyślnego momentu trwałości, jeśli zostanie użyta trwałość. Jeśli nie jest używana żadna trwałość, a przepływ pracy wykonuje operacje poza wzorcem żądania/odpowiedzi, dane zostaną utracone po przerwaniu przepływu pracy.

## <a name="hosting-a-workflow-in-a-custom-windows-service"></a>Hostowanie przepływu pracy w niestandardowej usłudze systemu Windows

Tworzenie niestandardowej usługi przepływu pracy w celu hostowania przepływu pracy wymaga, aby deweloper duplikuje wiele funkcji zapewnianych przez program AppFabric, ale będzie zapewnić większą elastyczność dzięki funkcjom niestandardowym. Tę opcję należy wziąć pod uwagę tylko wtedy, gdy w programie AppFabric nie można wybrać opcji.
