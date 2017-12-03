---
title: "Wystąpienia-utrwalony przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8a7dd9e0ccc29c81426064110eda3e00d2f27b99
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="non-persisted-workflow-instances"></a>Wystąpienia-utrwalony przepływu pracy
Jeśli nowe wystąpienie przepływu pracy jest utworzony utrwala swój stan w <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, host usługi tworzy wpis dla tej usługi w magazynie wystąpień. Później, gdy trwała wystąpienia przepływu pracy po raz pierwszy, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> zapisuje bieżący stan wystąpienia. Jeśli przepływ pracy jest hostowana w usłudze aktywacji procesów systemu Windows, danych wdrożenia usługi są równocześnie zapisywane w magazynie wystąpień, gdy wystąpienie jest zachowywane po raz pierwszy.  
  
 Tak długo, jak wystąpienie przepływu pracy nie zostały utrwalone, znajduje się w **-utrwalony** stanu. W tym stanie, wystąpienie przepływu pracy nie można odzyskać po odtwarzania domen aplikacji, awarii hosta lub awarii komputera.  
  
## <a name="the-non-persisted-state"></a>Stan nietrwałe  
 Wystąpienia przepływu pracy trwałe, które nie zostały utrwalone pozostają w stanie nietrwałe w następujących przypadkach:  
  
-   Host usługi ulegnie awarii, przed wystąpieniem przepływu pracy jest zachowywane po raz pierwszy. Wystąpienie przepływu pracy pozostaje w magazynie wystąpień i nie została odzyskana. Jeśli wiadomość skorelowane, wystąpienie przepływu pracy staje się aktywny ponownie.  
  
-   Wystąpienie przepływu pracy, wystąpi wyjątek przed jest zachowywane po raz pierwszy. W zależności od <xref:System.Activities.UnhandledExceptionAction> zwrócone, występują następujące scenariusze:  
  
    -   <xref:System.Activities.UnhandledExceptionAction>ustawiono <xref:System.Activities.UnhandledExceptionAction.Abort>: po wystąpieniu wyjątku, informacje na temat wdrażania usługi są zapisywane w magazynie wystąpień i wystąpienia przepływu pracy jest usuwane z pamięci. Nie można ponownie załadować wystąpienia przepływu pracy i pozostaje w stanie nietrwałe.  
  
    -   <xref:System.Activities.UnhandledExceptionAction>ustawiono <xref:System.Activities.UnhandledExceptionAction.Cancel> lub <xref:System.Activities.UnhandledExceptionAction.Terminate>: po wystąpieniu wyjątku, informacje na temat wdrażania usługi są zapisywane w magazynie wystąpień i ustawiono stan wystąpienia działania <xref:System.Activities.ActivityInstanceState.Closed>.  
  
 Aby zminimalizować ryzyko napotkania wystąpienia zwolniony-utrwalony przepływu pracy, zalecamy utrwalanie przepływu pracy na wczesnym etapie cyklu życia.  
  
## <a name="detection-and-removal-of-non-persisted-instances"></a>Wykrywanie i usuwanie wystąpienia nietrwałe  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Nie powoduje usunięcia żadnych-utrwalony wystąpienia przepływu pracy z w magazynie wystąpień. Ponadto nie powoduje usunięcia wszystkich właścicieli wygasłe blokady, którzy mają-utrwalony wystąpień przepływów pracy związanych z nimi.  
  
 Zaleca się, że administrator okresowo sprawdza, czy w magazynie wystąpień-utrwalony wystąpień. Administratorzy mogą usunąć te wystąpienia, w sklepie wystąpienia tak długo, jak wiedzieli, że ten przepływ pracy nie będą otrzymywać wiadomości skorelowane. Na przykład jeśli wystąpienie było w bazie danych kilka miesięcy, wiadomo, że przepływ pracy ma zazwyczaj w okresie istnienia kilka dni byłoby bezpiecznie założono było zainicjować wystąpienia awarii.  
  
 Aby znaleźć wystąpień,-utrwalone w magazynie wystąpień przepływu pracy programu SQL można użyć następujące kwerendy SQL:  
  
-   To zapytanie wyszukuje wszystkie wystąpienia, które nie zostały utrwalone i zwraca identyfikator i tworzenia czas (przechowywane w formacie UTC) dla nich.  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0  
    ```  
  
-   To zapytanie wyszukuje wszystkich wystąpień, które nie zostały utrwalone, a które nie są ładowane i zwraca identyfikator i tworzenia czas (przechowywane w formacie UTC) dla nich.  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and CurrentMachine is NULL  
    ```  
  
-   To zapytanie wyszukuje wystąpienia wszystkie zawieszone, które nie zostały utrwalone i zwraca identyfikator, czas utworzenia (przechowywane w formacie UTC), przyczynę zawieszenia i nazwa wyjątku dla nich.  
  
    ```sql  
    select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and IsSuspended = 1  
    ```  
  
 Należy zachować ostrożność, usuwając-utrwalony wystąpień. Ogólnie rzecz biorąc, jest bezpiecznie usunąć-utrwalony wystąpienia utworzone przez <xref:System.ServiceModel.Activities.WorkflowServiceHost> są wstrzymane albo nie są ładowane. Tych określonych wystąpień może zostać usunięta z magazynu przez usuwanie ich z `[System.Activities.DurableInstancing].[Instances]` przy użyciu następującego polecenia SQL, zastępując identyfikatora wystąpienia poprawne.  
  
```sql  
delete [System.Activities.DurableInstancing].[Instances]   
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’  
```  
  
> [!WARNING]
>  Nie zaleca się usunięcie wszystkich wystąpień-utrwalony, ponieważ w tym wystąpienia, które właśnie utworzony i nie zostały utrwalone.
