---
title: Magazyny wystąpień
ms.date: 03/30/2017
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
ms.openlocfilehash: 352ffad56c77d0bd16f7e3b9aa1d82090f3a29b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791173"
---
# <a name="instance-stores"></a>Magazyny wystąpień
Magazyn wystąpień jest kontenerem logicznym wystąpień. Jest miejscem, gdzie są przechowywane dane wystąpienia i metadanych. Magazyn wystąpień nie oznacza dedykowanych dla magazynu fizycznego. Magazyn wystąpień mogą zawierać informacje o stanie nietrwałe w pamięci lub trwałe informacji z bazy danych programu SQL Server. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Dostarczany z Store wystąpienia przepływu pracy SQL, który jest konkretną implementację magazyn wystąpienia, umożliwiająca przepływów pracy zachować dane wystąpienia i metadane do bazy danych programu SQL Server 2005 lub SQL Server 2008. Ponadto AppFabric w systemie Windows Server udostępnia konkretną implementację magazynu wystąpienia. Aby uzyskać więcej informacji, zobacz [systemu Windows Server App Fabric wystąpienia Store, zapytań i dostawców kontroli](https://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x409).  
  
 Utrwalanie interfejsu API jest interfejs między hostem i Magazyn wystąpienia, umożliwiająca hosta na potrzeby wysyłania żądań polecenia (na przykład <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> i <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>) Magazyn wystąpienia. Wykonanie tego interfejsu API nosi nazwę dostawcy stanów trwałych. Dostawcy stanów trwałych odbiera żądania od hosta i modyfikuje magazyn wystąpienia.  
  
 Hosty i magazyny wystąpień są podłączane co host może być używany z wielu magazynów wystąpienia i Magazyn wystąpienia mogą być używane z wielu hostach. Magazyn wystąpień zwykle jest zoptymalizowany pod kątem wzorców użycia określonego hosta, mimo że SIS i hosta może się rozwijać na niezależne cykle życia. Na przykład **WorkflowServiceHost** i **SqlWorkflowInstanceStore** zostały zaprojektowane do pracy ze sobą współdziałały. Można utworzyć własny magazyn wystąpienia utrwalić dane i metadane wystąpień usługi przepływu pracy i używać tego magazynu wystąpienia z **WorkflowServiceHost**. Na przykład można utworzyć OracleWorkflowInstanceStore umożliwiający przepływy pracy utrwalania informacji w bazie danych programu Oracle zamiast zapisywania ich w bazie danych programu SQL Server.  
  
 Jest to typowe dla hostów, aby można rozszerzyć za pomocą dodatkowych funkcji, która modyfikuje utrwalonych obiektów. Na przykład system trwałości wystąpienie może mieć hosta przepływu pracy, rozszerzenia, które obsługuje operację "Zawieszania" i wystąpienie magazynu danych SQL.  Hosta przepływu pracy może wysyłać standardowe polecenia takie jak zapisać lub załadować zapisać ani załadować przepływu pracy ze sklepu wystąpienia lub zapisać przepływ pracy do magazynu wystąpienia. Rozszerzenie Wstrzymaj może dodać dodatkowej semantyki do polecenia zapisywanie i ładowanie wystąpienia przepływu pracy, tak aby nie można załadować wystąpienia Wstrzymany przepływ pracy. Dostawcy stanów trwałych dla magazynu wystąpienia SQL rozumie polecenia zapisywanie i ładowanie wystąpienia przepływu pracy i implementuje poleceń przez wywołanie odpowiedniej procedury składowane, które zmieniają tabele trwałe obiekty w bazie danych programu SQL Server.  
  
 Host działa jako właściciela wystąpienia w magazynie wystąpienia. Host może działać jako więcej niż jednego właściciela wystąpienia z więcej niż jeden magazyn wystąpienia w tym samym czasie. Host zawiera identyfikatory GUID dla wystąpienia kluczy skojarzone z wystąpieniami. Klucz wystąpienia jest unikatowego aliasu, który identyfikuje wystąpienia. System trwałości tworzy, aktualizuje i usuwa informacje o właścicielu wystąpienia podczas wykonywania polecenia żądana przez hosty.  
  
 Poniższa lista zawiera ważne czynności związane z hosta interakcji z magazynem wystąpienie:  
  
1. Uzyskaj **objekt InstanceStore** od dostawcy trwałości.  

2. Uzyskaj dojście do wystąpienia, wywołując <xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A> metody **objekt InstanceStore**.  
  
3. Wywołania poleceń względem dojście wystąpienia, wywołując <xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A> metody **objekt InstanceStore**.  
  
4. Sprawdź <xref:System.Runtime.DurableInstancing.InstanceView> zwrócone przez **InstanceStore.Execute** do określenia wyników poleceń.
