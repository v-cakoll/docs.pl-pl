---
title: SQLStoreExtensibility
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5da1b5a3-f144-41ba-b9c4-02818b28b15d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e3e63a11ce87c95a5afc8e7f60c8e262da5c6bd1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="sqlstoreextensibility"></a>SQLStoreExtensibility
W przykładzie pokazano, używanie i konfigurację awansowanej właściwości w magazynie wystąpień przepływu pracy SQL. W magazynie wystąpień przepływu pracy SQL jest implementacją SQL na podstawie wystąpienia magazynu. Umożliwia on wystąpienie do zapisywania stanu i ładowania stanu do i z bazy danych programu SQL Server lub SQL Server Express. Funkcja rozszerzalność magazyn zezwala użytkownikowi na definiowanie właściwości, które są przechowywane w magazynie wystąpień. Te właściwości są wyświetlane w widoku awansowanej właściwości, które umożliwia użytkownikowi zapytania dla nich.  
  
 W tym przykładzie składa się z przepływu pracy, który implementuje usługi zliczania. Po wywołaniu metody uruchamiania usługi, usługi liczby z zakresu od 0 do 29. Licznik jest zwiększany co 2 sekundy. Po każdej liczby utrzymuje przepływ pracy. Bieżącą wartość licznika jest przechowywane w magazynie wystąpień jako awansowanej właściwości.  
  
 Przepływ pracy zliczania własnym jest hostowana przez hosta usługi przepływu pracy. Program `Main` metoda wykonuje następujące czynności:  
  
-   Tworzy wystąpienie obsługuje zliczania przepływu pracy, który definiuje punkty końcowe, w których zliczania przepływu pracy można połączyć się z hosta usługi przepływu pracy.  
  
-   Definiuje SQL zachowanie magazynu wystąpienia przepływu pracy, który służy do konfigurowania w magazynie wystąpień przepływu pracy programu SQL. Magazyn jest instrukcją traktować `CountStatus` jako awansowanej właściwości.  
  
-   Tworzy klienta, który wywołuje metodę start zliczania przepływu pracy.  
  
 Po uruchomieniu programu licznik uruchamia się automatycznie zliczania. Należy pamiętać, że może zająć kilka sekund, aby załadować wystąpienie i skonfigurować Magazyn wystąpienia przepływu pracy programu SQL.  
  
 Aby promować wartość licznika jako właściwość niestandardową, należy podjąć następujące kroki:  
  
1.  Klasa `CounterStatus` definiuje rozszerzenie wystąpienia typu <xref:System.Activities.Persistence.PersistenceParticipant>, używany do dostarczania zmienne stanu przez działania. `Count`nie zdefiniowano jako wartość tylko do zapisu. Gdy do punktu utrwalania wystąpienia przepływu pracy, rozszerzenie wystąpienia zapisuje `Count` właściwości do zbierania danych trwałości.  
  
2.  Podczas tworzenia w magazynie wystąpień nową właściwość `CountStatus`, jest zdefiniowana za pomocą `store.Promote()` metody.  
  
3.  Przepływ pracy `SaveCounter` działania przypisuje bieżącą wartość licznika `Count` pole stanu.  
  
### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Utwórz wystąpienie bazy danych magazynu.  
  
    1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
    2.  Przejdź do katalogu próbki (\WF\Basic\Persistence\SqlStoreExtensibility\CS) i uruchom CreateInstanceStore.cmd [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
        > [!WARNING]
        >  Skrypt CreateInstanceStore.cmd próbuje utworzyć bazę danych w domyślnym wystąpieniu programu SQL Server 2008 Express. Jeśli chcesz zainstalować bazy danych w innym wystąpieniu, należy zmodyfikować skrypt, aby to zrobić.  
  
2.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i załadowania rozwiązania SqlStoreExtensibility.sln i skompiluj go, naciskając klawisze CTRL + SHIFT + B.  
  
    > [!WARNING]
    >  Jeśli zainstalowano bazy danych w innych niż domyślne wystąpienie programu SQL Server, należy zaktualizować parametry połączenia w kodzie przed kompilacją rozwiązania.  
  
3.  Uruchom próbki z uprawnieniami administratora, przechodząc do katalogu bin projektu (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) w [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], klikając prawym przyciskiem myszy SqlStoreExtensibility.exe i wybierając **Uruchom jako Administrator**.  
  
### <a name="to-verify-the-sample-is-working-correctly"></a>Aby zweryfikować próbki działa poprawnie  
  
1.  Użyj programu SQL Server Management Studio, aby wyświetlić zawartość tej tabeli wystąpienia, wybierając **baz danych**, **InstanceStore**, a następnie  **System.ServiceModel.Activities.DurableInstancing.InstanceTable** w Eksploratorze obiektów kliknij prawym przyciskiem myszy **System.ServiceModel.Activities.DurableInstancing.InstanceTable** i wybierz  **Zaznacz 1000 pierwszych wierszy**. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]SQL Server Management Studio, zobacz [wprowadzenie do programu SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645)  
  
2.  Obserwować wystąpień przepływu pracy.  
  
3.  W [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia, uruchom skrypt QueryInstanceStore.cmd znajduje się w katalogu próbki (\WF\Basic\Persistence\SqlStoreExtensibility).  
  
4.  Sprawdź wartość licznika jest wyświetlany w obszarze **CountStatus**.  
  
5.  Uruchom skrypt kilka razy wyświetlić **CountStats** wartość zmiany.  
  
6.  Naciśnij klawisz ENTER, aby zakończyć działanie aplikacji przepływu pracy.  
  
### <a name="to-uninstall-the-sample"></a>Aby odinstalować próbki  
  
1.  Usuń bazę danych magazynu wystąpienia przez uruchomienie skryptu RemoveInstanceStore.cmd znajduje się w katalogu próbki (\WF\Basic\Persistence\SqlStoreExtensibility).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\SQLStoreExtensibility`  
  
## <a name="see-also"></a>Zobacz też  
 [Trwałość przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
