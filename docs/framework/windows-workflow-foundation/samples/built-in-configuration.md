---
title: Wbudowane konfiguracji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34e85c9b-088d-4347-816c-0f77cb73ef2f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ddf9b316074a69a88f08a0d7f519533f2db0002
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="built-in-configuration"></a>Wbudowane konfiguracji
W przykładzie pokazano, używania i konfiguracji w magazynie wystąpień przepływu pracy SQL. W magazynie wystąpień przepływu pracy SQL jest implementacją SQL na podstawie wystąpienia magazynu. Umożliwia on do zapisywania i ładowania stanu z bazy danych programu SQL Server lub SQL Server Express i wystąpienia.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do (stronę pobierania), aby pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="sample-details"></a>Szczegóły próbki  
 W tym przykładzie składa się z przepływu pracy, który implementuje usługi zliczania. Po wywołaniu metody uruchamiania usługi, usługi liczby z zakresu od 0 do 59. Licznik jest zwiększany co 2 sekundy. Po każdej liczby utrzymuje przepływ pracy.  
  
 Zliczania przepływu pracy jest samodzielnie hostowana przez hosta usługi przepływu pracy. Program `Main` metoda tworzy wystąpienie hosta usługi przepływu pracy obsługującego zliczania przepływu pracy. Definiuje punkty końcowe, zgodnie z którymi zliczania przepływu pracy jest osiągalna. Po wykonaniu tej definiuje SQL zachowanie magazynu wystąpienia przepływu pracy, który służy do konfigurowania w magazynie wystąpień przepływu pracy programu SQL. Następnie program tworzy klienta, który wywołuje metodę start zliczania przepływu pracy.  
  
 Po uruchomieniu programu licznik uruchamia się automatycznie zliczania. Należy pamiętać, że może zająć kilka sekund, aby załadować wystąpienie i skonfigurować Magazyn wystąpienia przepływu pracy programu SQL. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]w magazynie wystąpień przepływu pracy, zobacz [magazyn wystąpienia przepływu pracy SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
 Próbka składa się z dwóch części:  
  
1.  Pokazuje InstanceStore1 jak <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> jest konfigurowana przy użyciu kodu C# (zobacz Program.cs).  
  
2.  Pokazuje InstanceStore2 jak <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> jest skonfigurowany za pomocą XML (zobacz App.config).  
  
 Można konfigurować zachowanie magazynu wystąpienia przepływu pracy SQL są następujące ustawienia:  
  
-   Ustaw `HostLockRenewalPeriod`. Teraz Określa interwał, z którym host odnawia blokady własność wystąpień, jego uruchomienie. Informacje blokady są przechowywane w magazynie wystąpień. Jeśli nie zostanie odnowiony własności dla dwóch odstępach czasu zdefiniowanych w `HostLockRenewalPeriod`, wystąpienie jest uznawany za porzucone. Jeśli inny <xref:System.ServiceModel.Activities.WorkflowServiceHost> jest uruchomiona na tym samym przepływie pracy i połączony z tym samym magazynie wystąpienia (albo w tym samym komputerze lub na innym komputerze), odzyskuje tego wystąpienia. (Wystąpienie odzyskiwania jest poza zakresem dla tego przykładu).  
  
-   Ustaw `RunnableInstancesDetectionPeriod`. Ten okres Określa interwał, w którym host sonduje dla wystąpień, które stały się do uruchomienia. Wystąpień, mogą stać się do uruchomienia, jeśli wystąpienia któregokolwiek z następujących zdarzeń:  
  
    -   Trwałe czasomierza (<xref:System.Activities.Statements.Delay>) wygaśnie.  
  
    -   Chybienia hosta innego jego `HostLockRenewal` pulsu (na przykład z powodu awarii komputera) i wystąpienia są odzyskiwane.  
  
-   Ustaw `InstanceCompletionAction`. Tę właściwość, jeśli ustawiono `DeleteNothing`, wystąpień przechowuje ukończone w magazynie wystąpień; w przypadku ustawienia `DeleteAll`, wystąpienia zostaną usunięte z magazynu po zakończeniu. Należy pamiętać, że  
  
    > [!NOTE]
    >  Przerywanie hosta, naciskając klawisz ENTER, zanim liczenie została zakończona, nie zostanie zakończone wystąpienia przepływu pracy.  
  
-   Ustaw `InstanceLockedExceptionAction`. To ustawienie określa, co hosta zrobić, jeśli chce się załadować wystąpienia, który jest zablokowany przez innego hosta. Istnieją następujące opcje:  
  
    -   Jeśli ustawiono `NoRetry`: ponów obciążenia i nie zwraca `InstanceLockedException` do hosta.  
  
    -   Jeśli ustawiono `BasicRetry`: podejmować dalsze próby załadowania wystąpienia. Ponowne próby są planowane zgodnie z prosty algorytm liniową (na przykład, spróbuj co 5 sekund).  
  
    -   Jeśli ustawiono `AggressiveRetry`: podejmować dalsze próby załadowania wystąpienia. Ponowne próby są planowane zgodnie agresywne wykładniczego wycofywania algorytmu.  
  
-   Ustawianie opcji kodowania. To ustawienie określa, jak stan wystąpienia jest przechowywany w magazynie wystąpień przepływu pracy programu SQL. Istnieją następujące opcje:  
  
    -   Stan wystąpienia jest skompresowany, przy użyciu algorytmu kompresji GZip.  
  
    -   Stan wystąpienia nie jest kompresowany.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersz polecenia jako Administrator, jeśli są dostępne uprawnienia.  
  
2.  Przejdź do katalogu próbki (\WF\Basic\Persistence\BuiltInConfiguration\CS), a następnie uruchom CreateInstanceStore.cmd.  
  
3.  Jeśli uprawnienia administratora nie są dostępne, logowania programu SQL Server Utwórz. Przejdź do `Security`, **logowania**. Kliknij prawym przyciskiem myszy **logowania** i Utwórz nowe dane logowania.  
  
4.  Dodaj listę kontroli dostępu użytkownika do roli programu SQL. Otwórz **baz danych**, **InstanceStore**, **zabezpieczeń**. Kliknij prawym przyciskiem myszy **użytkowników** i wybierz **nowych użytkowników**. Ustaw **nazwa logowania** użytkownikowi utworzony w poprzednim kroku. Dodaj użytkownika do członkostwo roli bazy danych **System.Activities.DurableInstancing.InstanceStoreUsers** (i inne). Należy pamiętać, że użytkownik może istnieć już (na przykład użytkownika dbo).  
  
5.  Otwórz plik InstanceStore.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
6.  W [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], przejdź do katalogu bin\debug odpowiednie próbki (\WF\Basic\Persistence\BuiltInConfiguration\cs\InstanceStore(1 or 2)\bin\debug), kliknij prawym przyciskiem myszy InstanceStore.exe i wybierz **Uruchom jako administrator**. W tym przykładzie należy uruchomić z uprawnieniami administracyjnymi, ponieważ spowoduje to otwarcie odbiornika kanałów.  
  
7.  Jeśli w bazie danych innych niż lokalnej instalacji programu SQL Server Express został utworzony w magazynie wystąpień, należy zaktualizować parametry połączenia bazy danych (`const string ConnectionString` w pliku Program.cs projektu InstanceStore1 i `connectionString` atrybutu w pliku App.config programu Projekt InstanceStore2) w przykładowych i skompiluj ponownie próbki.  
  
#### <a name="to-verify-the-sample-is-running-correctly"></a>Aby zweryfikować próbki działa poprawnie  
  
1.  Próbki jest uruchomiona, uruchom program SQL Server Management Studio.  
  
2.  W **Eksplorator obiektów**, wybierz pozycję **baz danych**, **InstanceStore**, **tabel**, a następnie  **System.Activities.DurableInstancing.InstanceTable**.  
  
3.  Kliknij prawym przyciskiem myszy **InstanceTable** i wybierz **zaznacz 1000 pierwszych wierszy**.  
  
4.  Sprawdź, czy znajduje się nowy wpis, a **okresu ważności blokady** zmienia co 5 sekund (kliknij przycisk paska zadań **Execute** przycisk, aby odświeżyć zapytanie). Jest to konsekwencją ustawienie **okres odnawiania blokady hosta** do 5.  
  
5.  Obserwować po zakończeniu inwentaryzacji, że wpis w tabeli wystąpienie zostanie usunięty. Jest to konsekwencją ustawienie **wystąpienia ukończenia akcji** do **DeleteAll**.  
  
6.  Naciśnij klawisz ENTER, aby zakończyć tę aplikację hosta przepływu pracy i że **LockOwnersTable** zostaną usunięte.  
  
#### <a name="to-uninstall-the-sample"></a>Aby odinstalować próbki  
  
1.  Uruchom RemoveInstanceStore.cmd w katalogu próbki (\WF\Basic\Persistence\BuiltInConfiguration).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
