---
title: Magazyny wystąpień
ms.date: 03/30/2017
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
ms.openlocfilehash: 69b50942c36406bd29147d243e0501b8048d56dc
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802560"
---
# <a name="instance-stores"></a>Magazyny wystąpień
Magazyn wystąpień jest logicznym kontenerem wystąpień. Miejsce, w którym są przechowywane dane wystąpienia i metadane. Magazyn wystąpień nie implikuje dedykowanego magazynu fizycznego. Magazyn wystąpień może zawierać trwałe informacje w bazie danych SQL Server lub nietrwałe informacje o stanie w pamięci. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] jest dostarczany z magazynem wystąpień przepływu pracy SQL, który jest konkretną implementacją magazynu wystąpień, dzięki czemu przepływy pracy mogą utrwalać dane wystąpienia i metadane w bazie danych SQL Server 2005 lub SQL Server 2008. Ponadto program Windows Server App Fabric oferuje konkretną implementację magazynu wystąpień. Aby uzyskać więcej informacji, zobacz temat [Magazyn wystąpień, zapytanie i dostawcy kontroli usługi Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10)).  
  
 Trwałość interfejsu API to interfejs między hostem i magazynem wystąpień, który umożliwia hostowi wysyłanie żądań poleceń (na przykład <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> i <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>) do magazynu wystąpień. Konkretna implementacja tego interfejsu API jest nazywana dostawcą trwałości. Dostawca trwałości odbiera żądania od hosta i modyfikuje magazyn wystąpień.  
  
 Hosty i magazyny wystąpień są podłączane, dzięki czemu host może być używany z wieloma magazynami wystąpień, a magazyn wystąpień może być używany z wieloma hostami. Magazyn wystąpień jest zwykle zoptymalizowany pod kątem wzorców użycia określonego hosta, chociaż magazyn wystąpień i Host mogą się rozwijać w niezależnych cyklach życia. Na przykład obiekt **WorkflowServiceHost** i **obiekt SqlWorkflowInstanceStore** są zaprojektowane tak, aby dobrze współpracowały ze sobą. Możesz utworzyć własny magazyn wystąpień, aby zachować dane i metadane wystąpień usługi przepływu pracy i użyć tego magazynu wystąpień z obiektem **WorkflowServiceHost**. Można na przykład utworzyć element OracleWorkflowInstanceStore, który pozwala przepływom pracy utrzymywać informacje w bazie danych Oracle, zamiast zapisywać je w bazie danych SQL Server.  
  
 Często hosty są rozszerzone o dodatkowe funkcje, które modyfikują utrwalone obiekty. Na przykład system trwałości wystąpienia może mieć hosta przepływu pracy, rozszerzenie, które obsługuje operację "wstrzymania" i magazyn wystąpień SQL.  Host przepływu pracy może wysyłać standardowe polecenie, takie jak Save lub Load, w celu zapisania lub załadowania przepływu pracy z magazynu wystąpień lub zapisania przepływu pracy w magazynie wystąpień. Rozszerzenie Suspend może dodać dodatkową semantykę do poleceń służących do zapisywania i ładowania wystąpień przepływu pracy, aby nie można było załadować wstrzymanego wystąpienia przepływu pracy. Dostawca trwałości dla magazynu wystąpień SQL zawiera informacje o poleceniach służących do zapisywania i ładowania wystąpień przepływu pracy oraz implementuje polecenia, wywołując odpowiednie procedury składowane, które zmieniają tabele obiektów trwałych w bazie danych SQL Server.  
  
 Host działa jako właściciel wystąpienia w magazynie wystąpień. Host może działać jako więcej niż jeden właściciel wystąpienia z więcej niż jednym magazynem wystąpień w tym samym czasie. Host zawiera identyfikatory GUID dla kluczy wystąpienia skojarzonych z wystąpieniami. Klucz wystąpienia jest unikatowym aliasem identyfikującym wystąpienie. System trwałości tworzy, aktualizuje i usuwa informacje o właścicielu wystąpienia w miarę wykonywania poleceń zleconych przez hosty.  
  
 Poniższa lista zawiera ważne czynności związane z interakcją hosta z magazynem wystąpień:  
  
1. Uzyskaj obiekt **InstanceStore** od dostawcy trwałości.  

2. Uzyskaj dojście do wystąpienia, wywołując metodę <xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A> na **obiekcie InstanceStore**.  
  
3. Wywoływanie poleceń względem dojścia wystąpienia, wywołując metodę <xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A> na **obiekcie InstanceStore**.  
  
4. Sprawdź <xref:System.Runtime.DurableInstancing.InstanceView> zwrócone przez **obiektu InstanceStore. Execute** , aby określić wyniki poleceń.
