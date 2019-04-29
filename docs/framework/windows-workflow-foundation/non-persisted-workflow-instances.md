---
title: Nietrwałe wystąpienia przepływu pracy
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 410451f0dfeb91111e77634245aa786c4afc5b04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644268"
---
# <a name="non-persisted-workflow-instances"></a>Nietrwałe wystąpienia przepływu pracy
Nowe wystąpienie przepływu pracy utworzenia trwające jego stan w <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, host usługi tworzy wpis dla tej usługi w sklepie wystąpienia. Później, gdy wystąpienie przepływu pracy jest trwały po raz pierwszy <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zapisuje bieżący stan wystąpienia. Jeśli przepływ pracy znajduje się w usłudze aktywacji procesów Windows, danych wdrożenia usługi są również zapisywane do magazynu wystąpienia, gdy wystąpienie jest trwały po raz pierwszy.  
  
 Tak długo, jak nie został utrwalony wystąpienia przepływu pracy, jest **nieutrwaloną** stanu. W tym stanie wystąpienie przepływu pracy nie można odzyskać po odtwarzanie domeny aplikacji, awarii komputera lub awarii hosta.  
  
## <a name="the-non-persisted-state"></a>Stan nietrwałe  
 Wystąpienia trwałość przepływu pracy, które nie zostały utrwalone pozostają w stanie nieutrwaloną w następujących przypadkach:  
  
- Host usługi ulegnie awarii, przed wystąpieniem przepływu pracy jest trwały po raz pierwszy. Wystąpienie przepływu pracy pozostaje w magazynie wystąpienia i nie została odzyskana. Jeśli zostanie odebrana wiadomość skorelowane, wystąpienie przepływu pracy staje się aktywny ponownie.  
  
- Wystąpienie przepływu pracy napotka wyjątek, zanim są utrwalane po raz pierwszy. W zależności od <xref:System.Activities.UnhandledExceptionAction> zwrócone, występują następujące scenariusze:  
  
    - <xref:System.Activities.UnhandledExceptionAction> ustawiono <xref:System.Activities.UnhandledExceptionAction.Abort>: Gdy wystąpi wyjątek, informacje o wdrożeniu usługi są zapisywane do magazynu wystąpienia, a wystąpienie przepływu pracy jest usuwane z pamięci. Wystąpienie przepływu pracy pozostaje w stanie nietrwałe i nie można ponownie załadować.  
  
    - <xref:System.Activities.UnhandledExceptionAction> ustawiono <xref:System.Activities.UnhandledExceptionAction.Cancel> lub <xref:System.Activities.UnhandledExceptionAction.Terminate>: Gdy wystąpi wyjątek, informacje o wdrożeniu usługi są zapisywane do magazynu wystąpienie i stan wystąpienia działania jest równa <xref:System.Activities.ActivityInstanceState.Closed>.  
  
 Aby zminimalizować ryzyko zostają zwolnione przepływu pracy, które są nietrwałe wystąpienia, firma Microsoft zaleca utrwalanie przepływu pracy na wczesnym etapie cyklu życia.  
  
## <a name="detection-and-removal-of-non-persisted-instances"></a>Wykrywanie i usuwanie wystąpień nietrwałych  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Nie powoduje usunięcia wszelkich nietrwałe wystąpienia przepływu pracy w sklepie wystąpienia. Ponadto nie powoduje usunięcia wszystkich właścicieli blokada wygasła, którzy mają nietrwałe wystąpienia przepływu pracy skojarzonych z nimi.  
  
 Zaleca się, że administrator okresowo sprawdza magazyn wystąpień do wystąpień nietrwałych. Administratorzy mogą usunąć te wystąpienia w sklepie wystąpienia, tak długo, jak, które znają tego przepływu pracy nie będą otrzymywać skorelowanych komunikatów. Na przykład jeśli wystąpienie było w bazie danych przez kilka miesięcy, a wiadomo, że przepływ pracy ma zazwyczaj ważności kilka dni, będzie bezpiecznie przyjąć założenie było to wystąpienie zainicjowane, które miały wystąpiła awaria.  
  
 Aby znaleźć wystąpień nietrwałych w Store wystąpienia przepływu pracy SQL można użyć następujących zapytań SQL:  
  
- To zapytanie wyszukuje wszystkie wystąpienia, które nie zostały utrwalone i zwraca identyfikator i tworzenia czas (przechowywany w czasie UTC) dla nich.  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0  
    ```  
  
- To zapytanie wyszukuje wszystkie wystąpienia, która nie została utrwalona i nie są ładowane i zwraca identyfikator i tworzenia czas (przechowywany w czasie UTC) dla nich.  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and CurrentMachine is NULL  
    ```  
  
- To zapytanie wyszukuje wszystkie wstrzymane wystąpień, które nie zostały utrwalone i zwraca identyfikator, czas utworzenia (przechowywanej w czasie UTC), powodem zawieszenia, a nazwa wyjątku dla nich.  
  
    ```sql  
    select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and IsSuspended = 1  
    ```  
  
 Usunięcie wystąpień nietrwałych, należy zachować ostrożność. Ogólnie rzecz biorąc, jest bezpieczne usuwanie nietrwałe wystąpienia utworzone przez <xref:System.ServiceModel.Activities.WorkflowServiceHost> , są zawieszone lub nie są ładowane. Tych konkretnych wystąpień może zostać usunięta z magazynu przez usuwanie ich z `[System.Activities.DurableInstancing].[Instances]` za pomocą następującego polecenia SQL, podstawiając identyfikator wystąpienia jest poprawny.  
  
```sql  
delete [System.Activities.DurableInstancing].[Instances]   
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’  
```  
  
> [!WARNING]
>  Firma Microsoft nie zaleca się usunięcie wszystkich wystąpień nietrwałych, ponieważ w tym wystąpienia, które właśnie utworzony i nie zostały jeszcze utrwalone.
