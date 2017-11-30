---
title: "Porady: zapytanie o-utrwalony wystąpień"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c83e9364fa599d4356b69fe93ae3eaaa618c2f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-for-non-persisted-instances"></a>Porady: zapytanie o-utrwalony wystąpień
Po utworzeniu nowego wystąpienia usługi, a usługa zachowanie magazynu wystąpienia przepływu pracy SQL zdefiniowane, host usługi tworzy początkowej wpis dla tego wystąpienia usługi w magazynie wystąpień. Następnie, gdy wystąpienie usługi będzie nadal występować po raz pierwszy, zachowanie magazynu wystąpienia przepływu pracy SQL przechowuje bieżący stan wystąpienia oraz dodatkowe dane, które jest wymagane dla aktywacji, odzyskiwania i kontroli.  
  
 Jeśli wystąpienie nie jest trwały, po utworzeniu początkowej wpis dla tego wystąpienia, wystąpienie usługi jest określany jako nietrwałe stan. Wszystkie wystąpienia usług utrwalonych można zbadać i kontrolowane. Wystąpienie usługi non utrwalony nie można można zbadać ani pod kontrolą. Jeśli wystąpienie-utrwalony jest wstrzymana z powodu nieobsługiwanego wyjątku można zbadać ale nie kontroluje.  
  
 Usługa trwała wystąpień, które nie są jeszcze utrwalone pozostają w stanie nietrwałe w następujących scenariuszach:  
  
-   Host usługi ulegnie awarii przed wystąpienie utrwalone po raz pierwszy. Zapis początkowa dla wystąpienia pozostaje w magazynie wystąpień. Wystąpienie nie jest możliwe do odzyskania. Jeśli wiadomość skorelowane, wystąpienie stanie się ponownie aktywna.  
  
-   Wystąpienie napotka nieobsługiwany wyjątek, przed jego utrwalone po raz pierwszy. Następujące scenariusze wystąpić  
  
    -   Jeśli wartość **wartość UnhandledExceptionAction** właściwość jest ustawiona na **Abandon**, informacje na temat wdrażania usługi są zapisywane w magazynie wystąpień, a wystąpienie jest usuwane z pamięci. Wystąpienie pozostaje w stanie nietrwałe w bazie danych trwałości.  
  
    -   Jeśli wartość **wartość UnhandledExceptionAction** właściwość jest ustawiona na **AbandonAndSuspsend**, informacje na temat wdrażania usługi jest zapisane w bazie danych trwałości i ustawionystanwystąpienia **Zawieszone**. Wystąpienie nie może zostać wznowione, anulowania lub zakończenia. Host usługi nie można załadować wystąpienia, ponieważ wystąpienie nie jeszcze utrwalone, i dlatego wpis bazy danych dla tego wystąpienia nie jest ukończone.  
  
    -   Jeśli wartość **wartość UnhandledExceptionAction** właściwość jest ustawiona na **anulować** lub **przerwania**, informacje na temat wdrażania usługi są zapisywane w magazynie wystąpień i stan wystąpienia ma ustawioną wartość **Ukończono**.  
  
 Przykładowe zapytania można znaleźć w bazie danych SQL trwałości-utrwalony wystąpień i usunąć te wystąpienia z bazy danych można znaleźć w poniższych sekcjach.  
  
## <a name="to-find-all-instances-not-persisted-yet"></a>Aby znaleźć wszystkie wystąpienia nie jeszcze utrwalone  
 Następujące zapytanie SQL zwraca identyfikator i tworzenia czasu dla wszystkich wystąpień, które nie są zachowywane w jeszcze w bazie danych trwałości.  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;  
```  
  
## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a>Aby znaleźć wszystkie wystąpienia nie jest jeszcze utrwalone i również nie załadowany  
 Następujące zapytanie SQL zwraca identyfikator i tworzenia czasu dla wszystkich wystąpień, które nie są zachowywane, a także nie są ładowane.  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;  
```  
  
## <a name="to-find-all-suspended-instances-not-persisted-yet"></a>Aby znaleźć wszystkie wstrzymane wystąpienia nie jeszcze utrwalone  
 Następujące zapytanie SQL zwraca identyfikator, czas utworzenia przyczyna zawieszenia i zawieszenie nazwa wyjątku dla wszystkich wystąpień, które nie są zachowywane, a także w stanie wstrzymania.  
  
```  
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;  
```  
  
## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a>Aby usunąć-utrwalony wystąpienia z bazy danych trwałości  
 Należy okresowo Wyszukaj w sklepie wystąpienia-utrwalony wystąpień i usuń wystąpienia w sklepie wystąpienia, jeśli masz pewności, czy wystąpienie nie zostanie wyświetlony komunikat z skorelowane. Na przykład jeśli wystąpienie było w bazie danych kilka miesięcy, wiadomo, że przepływ pracy ma zazwyczaj w okresie istnienia za kilka dni byłoby bezpiecznie założono, że jest to niezainicjowanym wystąpieniem, w którym miała awaria.  
  
 Ogólnie rzecz biorąc jest bezpiecznie usunąć-utrwalony wystąpień, które nie jest wstrzymana lub nie został załadowany. Nie należy usuwać **wszystkie** wystąpień-utrwalony, ponieważ ten zestaw wystąpienia zawiera wystąpień, które zostały utworzone, ale nie są jeszcze utrwalone. Należy usunąć tylko-utrwalony wystąpień, które są pozostawione ponieważ hosta usługi przepływu pracy, który miał załadować wystąpienia spowodowała wyjątek lub wystąpienie spowodowała wyjątek.  
  
> [!WARNING]
>  Usuwanie instancji nietrwałe w sklepie wystąpienia zmniejsza rozmiar magazynu i może zwiększyć wydajność operacji magazynu.
