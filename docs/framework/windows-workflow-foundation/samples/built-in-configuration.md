---
title: Wbudowana Konfiguracja
ms.date: 03/30/2017
ms.assetid: 34e85c9b-088d-4347-816c-0f77cb73ef2f
ms.openlocfilehash: e76c019d9fc1b416e6fa8175a70b5fd01d9ff53e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084796"
---
# <a name="built-in-configuration"></a>Wbudowana Konfiguracja
Niniejszy przykład pokazuje, używania i konfigurowania magazynu wystąpień przepływu pracy SQL. Magazyn wystąpień przepływu pracy SQL stanowi implementację oparte na SQL magazynu wystąpienia. Umożliwia to wystąpienie zapisać i załadować stanu do i z bazy danych programu SQL Server lub SQL Server Express.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do (strona pobierania) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="sample-details"></a>Przykład szczegółów  
 W tym przykładzie składa się z przepływu pracy, który implementuje usługę zliczania. Po wywołaniu metody uruchamiania usługi, ta usługa liczy się od 0 do 59. Licznik jest zwiększany co 2 sekundy. Przepływ pracy po każdym liczba będzie się powtarzać.  
  
 Zliczania przepływu pracy jest może być samodzielnie hostowane przez hosta usługi przepływu pracy. Program `Main` metoda tworzy wystąpienie hosta usługi przepływu pracy, który obsługuje zliczania przepływu pracy. Definiuje punktów końcowych, zgodnie z którymi zliczania przepływu pracy można z Tobą skontaktować. Po tym definiuje SQL przepływu pracy wystąpienie magazynu zachowanie, które służy do konfigurowania magazynu wystąpień przepływu pracy SQL. Następnie program tworzy klienta, który wywołuje metodę uruchamiania zliczania przepływu pracy.  
  
 Po uruchomieniu programu wartość licznika automatycznie rozpoczyna się zliczania. Należy pamiętać, że może to potrwać kilka sekund, aby załadować wystąpienia i skonfigurować Magazyn wystąpień przepływu pracy SQL. Aby uzyskać więcej informacji na temat magazynu wystąpień przepływu pracy, zobacz [Store wystąpienia przepływu pracy SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).  
  
 Przykład składa się z dwóch części:  
  
1.  Pokazuje InstanceStore1 jak <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> została skonfigurowana przy użyciu kodu C# (zobacz plik Program.cs).  
  
2.  Pokazuje InstanceStore2 jak <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> jest skonfigurowany za pomocą języka XML (patrz App.config).  
  
 Można skonfigurować zachowanie Store wystąpienia przepływu pracy SQL są następujące ustawienia:  
  
-   Ustaw `HostLockRenewalPeriod`. Tym razem Określa interwał, z którym hosta odnawia blokadę własność wystąpień, w których ono działa. Informacje o blokadzie są przechowywane w Store wystąpienia. Jeśli własność nie zostanie odnowiony dla dwóch odstępach czasu zdefiniowanych w `HostLockRenewalPeriod`, wystąpienie jest uznawany za porzucone. Jeśli w kolejnym <xref:System.ServiceModel.Activities.WorkflowServiceHost> jest uruchomiona na tym samym przepływie pracy i połączony z tym samym magazynie wystąpienia (albo na tym samym komputerze lub na innym komputerze), odzyskuje tego wystąpienia. (Wystąpienia odzyskiwania jest poza zakresem dla tego przykładu).  
  
-   Ustaw `RunnableInstancesDetectionPeriod`. Ten okres Określa interwał, w którym hosta sonduje pod kątem wystąpienia, które stały się możliwy do uruchomienia. Wystąpienia, mogą stać się możliwy do uruchomienia, jeśli wystąpi dowolne z następujących zdarzeń:  
  
    -   Trwałe czasomierza (<xref:System.Activities.Statements.Delay>) wygaśnie.  
  
    -   Inny host Chybienia jego `HostLockRenewal` pulsu (na przykład z powodu awarii komputera), a wystąpienie jest przywracany.  
  
-   Ustaw `InstanceCompletionAction`. Tę właściwość, jeśli ustawiono `DeleteNothing`, wystąpień przechowuje ukończone w Store wystąpienia; Jeśli równa `DeleteAll`, wystąpienia zostaną usunięte z magazynu po zakończeniu. Należy pamiętać, że  
  
    > [!NOTE]
    >  Kończenie hosta, naciskając klawisz ENTER, przed ukończeniem liczenie zakończy się wystąpieniem przepływu pracy.  
  
-   Ustaw `InstanceLockedExceptionAction`. To ustawienie określa, co host powinien zrobić, jeśli chce się załadować wystąpienia, który jest zablokowany przez inny host. Istnieją następujące opcje:  
  
    -   Jeśli ustawiono `NoRetry`: ponów próbę wykonania obciążenia i nie zwracają `InstanceLockedException` do hosta.  
  
    -   Jeśli ustawiono `BasicRetry`: ponawiać próbę ładowania wystąpienia. Ponowne próby są planowane zgodnie z algorytmem liniowy prosty (na przykład, ponów próbę wykonania co 5 sekund).  
  
    -   Jeśli ustawiono `AggressiveRetry`: ponawiać próbę ładowania wystąpienia. Ponowne próby są planowane zgodnie z agresywne wykładniczego wycofywania algorytmu.  
  
-   Ustaw opcję kodowania. To ustawienie określa, jak stan wystąpienia jest przechowywany w Store wystąpienia przepływu pracy SQL. Istnieją następujące opcje:  
  
    -   Kondycja tego wystąpienia jest skompresowany za pomocą algorytmu kompresji GZip.  
  
    -   Kondycja tego wystąpienia nie jest skompresowany.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersz polecenia jako Administrator, jeśli uprawnienia są dostępne.  
  
2.  Przejdź do katalogu próbki (\WF\Basic\Persistence\BuiltInConfiguration\CS), a następnie uruchom CreateInstanceStore.cmd.  
  
3.  Jeśli uprawnienia administratora nie są dostępne, Utwórz serwer SQL logowania. Przejdź do `Security`, **logowania**. Kliknij prawym przyciskiem myszy **logowania** i Utwórz nową nazwę logowania.  
  
4.  Dodaj użytkownika listy ACL do roli programu SQL. Otwórz **baz danych**, **objekt InstanceStore**, **zabezpieczeń**. Kliknij prawym przyciskiem myszy **użytkowników** i wybierz **nowi użytkownicy**. Ustaw **nazwa logowania** użytkownika utworzony w poprzednim kroku. Dodaj użytkownika do członkostwo roli bazy danych **System.Activities.DurableInstancing.InstanceStoreUsers** (i inne). Należy pamiętać, że użytkownik może istnieć już (na przykład użytkownik dbo).  
  
5.  Otwórz plik InstanceStore.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i Skompiluj rozwiązanie, naciskając klawisze CTRL + SHIFT + B.  
  
6.  W [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], przejdź do katalogu bin\debug odpowiedni przykład (\WF\Basic\Persistence\BuiltInConfiguration\cs\InstanceStore(1 or 2)\bin\debug), kliknij prawym przyciskiem myszy InstanceStore.exe i wybierz **Uruchom jako administrator**. W tym przykładzie należy uruchomić z uprawnieniami administracyjnymi, ponieważ spowoduje to otwarcie odbiornika kanałów.  
  
7.  Jeśli utworzono magazyn wystąpienia w bazie danych innych niż lokalna instalacja programu SQL Server Express, należy zaktualizować parametry połączenia bazy danych (`const string ConnectionString` w pliku Program.cs projektu InstanceStore1 i `connectionString` atrybutu w pliku App.config programu Projekt InstanceStore2) w próbce i skompiluj ponownie przykład.  
  
#### <a name="to-verify-the-sample-is-running-correctly"></a>Aby zweryfikować próbki działa poprawnie  
  
1.  Po uruchomieniu przykładu należy uruchomić program SQL Server Management Studio.  
  
2.  W **Eksplorator obiektów**, wybierz opcję **baz danych**, **objekt InstanceStore**, **tabel**, a następnie  **System.Activities.DurableInstancing.InstanceTable**.  
  
3.  Kliknij prawym przyciskiem myszy **InstanceTable** i wybierz **zaznacz 1000 pierwszych wierszy**.  
  
4.  Zwróć uwagę nowy wpis oraz że **wygaśnięcia blokady** zmienia się co 5 sekund (kliknij na pasku zadań **Execute** przycisk, aby odświeżyć zapytanie). Jest to konsekwencją ustawienie **okres odnowienia blokady hosta** do 5.  
  
5.  Obserwuj po ukończeniu liczenie usunięcie wpisu w tabeli wystąpienia. Jest to konsekwencją ustawienie **działanie ukończenia wystąpienia** do **DeleteAll**.  
  
6.  Naciśnij klawisz ENTER, aby zakończyć aplikację hosta przepływu pracy i Zauważ, że **LockOwnersTable** zostanie usunięty.  
  
#### <a name="to-uninstall-the-sample"></a>Aby odinstalować próbki  
  
1.  Uruchom RemoveInstanceStore.cmd w katalogu próbki (\WF\Basic\Persistence\BuiltInConfiguration).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\BuiltInConfiguration`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
