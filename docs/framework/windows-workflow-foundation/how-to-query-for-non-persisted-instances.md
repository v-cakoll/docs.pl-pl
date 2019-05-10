---
title: 'Instrukcje: Zapytanie dotyczące wystąpień nietrwałych'
ms.date: 03/30/2017
ms.assetid: 294019b1-c1a7-4b81-a14f-b47c106cd723
ms.openlocfilehash: cbc3ec59bc0fbd8c39d351c248a664dc9231044c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584944"
---
# <a name="how-to-query-for-non-persisted-instances"></a>Instrukcje: Zapytanie dotyczące wystąpień nietrwałych
Gdy tworzone jest nowe wystąpienie usługi, a usługa ma zachowanie Store wystąpienia przepływu pracy SQL zdefiniowane, host usługi tworzy wpis określający początkowej dla tego wystąpienia usługi w magazynie wystąpienia. Później, gdy wystąpienie usługi będzie nadal występować po raz pierwszy, zachowanie Store wystąpienia przepływu pracy SQL przechowuje bieżące wystąpienie przechodzi w stan wraz z dodatkowych danych, która jest wymagana aktywacja, odzyskiwania i kontroli.  
  
 Jeśli wystąpienie nie jest trwały, po utworzeniu początkowego wpis dla wystąpienia, wystąpienie usługi jest nazywany będzie w stanie nietrwałe. Wszystkie wystąpienia usług utrwalonych można można tworzyć zapytania i kontrolowany. Wystąpienia utrwalone spoza usługi nie można zapytań ani kontrolowany. Jeśli wystąpienie programu nieutrwaloną zostanie wstrzymany z powodu nieobsługiwanego wyjątku może być badane ale nie jest kontrolowany.  
  
 Wystąpień trwałych usług, które nie zostaną jeszcze utrwalone pozostają w stanie nieutrwaloną w następujących scenariuszach:  
  
- Host usługi ulegnie awarii, przed wystąpienie utrwalone po raz pierwszy. Początkowa wpis dla wystąpienia pozostaje w magazynie wystąpienia. Wystąpienie nie jest możliwe do odzyskania. Jeśli zostanie odebrana wiadomość skorelowane, wystąpienie stanie się aktywny ponownie.  
  
- Wystąpienie środowisk nieobsługiwany wyjątek, zanim ją utrwalone po raz pierwszy. Wystąpić w następujących scenariuszach  
  
    - Jeśli wartość **UnhandledExceptionAction** właściwość jest ustawiona na **Abandon**, informacje na temat wdrażania usługi są zapisywane do magazynu wystąpienia i wystąpienie jest usuwane z pamięci. Wystąpienie pozostaje w nieutrwaloną stan w bazie danych trwałości.  
  
    - Jeśli wartość **UnhandledExceptionAction** właściwość jest ustawiona na **AbandonAndSuspsend**, informacje na temat wdrażania usługi są zapisywane w bazie danych trwałości i stan wystąpienia jest równa  **Zawieszone**. Wystąpienie nie może zostać wznowione, anulowania lub zakończenia. Host usługi nie można załadować wystąpienia, ponieważ wystąpienie nie zostało jeszcze utrwalone, a więc wpis w bazie danych dla tego wystąpienia nie zostało zakończone.  
  
    - Jeśli wartość **UnhandledExceptionAction** właściwość jest ustawiona na **anulować** lub **Zakończ**, informacje na temat wdrażania usługi są zapisywane do magazynu wystąpienia i stan wystąpienia jest równa **Ukończono**.  
  
 Przykładowe zapytania, aby znaleźć wystąpień nietrwałych w bazie danych stanów trwałych programu SQL i usuń te wystąpienia z bazy danych można znaleźć w poniższych sekcjach.  
  
## <a name="to-find-all-instances-not-persisted-yet"></a>Aby znaleźć wszystkie wystąpienia nie jeszcze utrwalone  
 Następujące zapytanie SQL zwraca identyfikator i tworzenia czasu dla wszystkich wystąpień, które nie są zachowywane w jeszcze do bazy danych trwałości.  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0;  
```  
  
## <a name="to-find-all-instances-not-persisted-yet-and-also-not-loaded"></a>Aby znaleźć wszystkie wystąpienia nie jest jeszcze utrwalone i również nie załadowany  
 Następujące zapytanie SQL zwraca identyfikator i tworzenia czasu dla wszystkich wystąpień, które nie są zachowywane i również nie są ładowane.  
  
```  
select InstanceId, CreationTime from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and CurrentMachine is NULL;  
```  
  
## <a name="to-find-all-suspended-instances-not-persisted-yet"></a>Aby znaleźć wszystkie wstrzymane wystąpienia nie jeszcze utrwalone  
 Następujące zapytanie SQL zwraca identyfikator, czas utworzenia, powodem zawieszenia i zawieszenia nazwa wyjątku dla wszystkich wystąpień, które nie są zachowywane, a także w stanie wstrzymania.  
  
```  
select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName from [System.Activities.DurableInstancing].[Instances] where IsInitialized = 0 and IsSuspended = 1;  
```  
  
## <a name="to-delete-non-persisted-instances-from-the-persistence-database"></a>Można usunąć wystąpień nietrwałych z bazy danych stanów trwałych  
 Należy okresowo Sprawdź magazyn wystąpień do wystąpień nietrwałych i usuwania wystąpień z magazyn wystąpienia, jeśli masz pewności, czy wystąpienie nie zostanie wyświetlony komunikat z skorelowane. Na przykład jeśli wystąpienie było w bazie danych przez kilka miesięcy, a wiadomo, że przepływ pracy ma zazwyczaj ważności przez kilka dni, będzie można bezpiecznie przyjąć założenie, że to wystąpienie niezainicjowanej, które miały wystąpiła awaria.  
  
 Ogólnie rzecz biorąc jest bezpieczne usuwanie wystąpień nietrwałych, które nie jest wstrzymana lub nie załadowano. Nie należy usuwać **wszystkich** wystąpień nietrwałych, ponieważ ten zestaw instancji zawiera wystąpienia, które są właśnie utworzony, ale nie są jeszcze utrwalone. Należy usunąć tylko wystąpień nietrwałych, które są pozostawione przez, ponieważ hosta usługi przepływu pracy, który miał załadować wystąpienia spowodowała wyjątek lub samego spowodowała wyjątek wystąpienia.  
  
> [!WARNING]
>  Usuwanie wystąpień nietrwałych sklepie wystąpienia zmniejszenie rozmiaru magazynu i może zwiększyć wydajność operacji magazynu.
