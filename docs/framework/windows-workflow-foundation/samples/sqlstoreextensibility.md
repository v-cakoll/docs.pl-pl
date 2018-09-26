---
title: SQLStoreExtensibility
ms.date: 03/30/2017
ms.assetid: 5da1b5a3-f144-41ba-b9c4-02818b28b15d
ms.openlocfilehash: f49d05244cf9f65a8e06f39c7e40391aaebd9f77
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090165"
---
# <a name="sqlstoreextensibility"></a>SQLStoreExtensibility
Niniejszy przykład pokazuje, używania i konfigurowania o podwyższonym poziomie właściwości magazynu wystąpień przepływu pracy SQL. Magazyn wystąpień przepływu pracy SQL stanowi implementację oparte na SQL magazynu wystąpienia. Umożliwia to wystąpienie zapisać swój stan i załadować stanu z bazy danych programu SQL Server lub SQL Server Express i. Funkcja rozszerzalność magazynu zezwala użytkownikowi na definiowanie właściwości, które są przechowywane w magazynie wystąpienia. Te właściwości są wyświetlane w widoku właściwości o podwyższonym poziomie, który umożliwia użytkownikowi zapytania dla nich.  
  
 W tym przykładzie składa się z przepływu pracy, który implementuje usługę zliczania. Po wywołaniu metody uruchamiania usługi, ta usługa liczy się od 0 do 29. Licznik jest zwiększany co 2 sekundy. Przepływ pracy po każdym liczba będzie się powtarzać. Bieżąca wartość licznika jest przechowywane w magazynie wystąpienia jako właściwość o podwyższonym poziomie.  
  
 Zliczanie przepływu pracy jest może być samodzielnie hostowane przez hosta usługi przepływu pracy. Program `Main` metoda wykonuje następujące czynności:  
  
-   Tworzy wystąpienie hosta usługi przepływu pracy, który obsługuje zliczania przepływu pracy i definiuje punktów końcowych, zgodnie z którymi zliczanie przepływu pracy można z Tobą skontaktować.  
  
-   Definiuje SQL przepływu pracy wystąpienie magazynu zachowanie, które służy do konfigurowania magazynu wystąpień przepływu pracy SQL. Magazyn jest zobowiązany do traktowania `CountStatus` jako właściwość o podwyższonym poziomie.  
  
-   Tworzy klienta, który wywołuje metodę uruchamiania zliczania przepływu pracy.  
  
 Po uruchomieniu programu wartość licznika automatycznie rozpoczyna się zliczania. Należy pamiętać, że może to potrwać kilka sekund, aby załadować wystąpienia i skonfigurować Magazyn wystąpień przepływu pracy SQL.  
  
 Aby promować wartość licznika, jako właściwość niestandardową, należy podjąć następujące kroki:  
  
1.  Klasy `CounterStatus` definiuje rozszerzenie typu <xref:System.Activities.Persistence.PersistenceParticipant>, który jest używany przez działania umożliwiają określanie wartości zmienne stanu. `Count` jest zdefiniowany jako wartość tylko do zapisu. Gdy wystąpienie przepływu pracy do punktu stanu trwałego, rozszerzenie wystąpienia zapisuje `Count` właściwości do zbierania danych trwałości.  
  
2.  Podczas tworzenia instance store nową właściwość `CountStatus`, jest zdefiniowana za pomocą `store.Promote()` metody.  
  
3.  Przepływ pracy `SaveCounter` działania przypisuje bieżącą wartość licznika `Count` pola stan.  
  
### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Utwórz wystąpienie bazy danych magazynu.  
  
    1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
    2.  Przejdź do katalogu próbki (\WF\Basic\Persistence\SqlStoreExtensibility\CS), a następnie uruchom CreateInstanceStore.cmd w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
        > [!WARNING]
        >  Skrypt CreateInstanceStore.cmd próbuje utworzyć bazę danych w domyślnym wystąpieniu programu SQL Server 2008 Express. Jeśli chcesz zainstalować bazę danych w innym wystąpieniu, należy zmodyfikować skrypt, aby to zrobić.  
  
2.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] załadować rozwiązanie SqlStoreExtensibility.sln i skompiluj go, naciskając klawisze CTRL + SHIFT + B.  
  
    > [!WARNING]
    >  Jeśli baza danych jest zainstalowana na innych niż domyślne wystąpienie programu SQL Server, należy zaktualizować parametry połączenia w kodzie przed kompilowania rozwiązania.  
  
3.  Uruchom aplikację przykładową z uprawnieniami administratora, przejdź do katalogu bin projektu (\WF\Basic\Persistence\SqlStoreExtensibility\bin\Debug) w [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], klikając prawym przyciskiem myszy SqlStoreExtensibility.exe i wybierając opcję **Uruchom jako Administrator**.  
  
### <a name="to-verify-the-sample-is-working-correctly"></a>Aby zweryfikować próbki działa prawidłowo  
  
1.  Użyj programu SQL Server Management Studio do wyświetlenia zawartości tabeli wystąpienia, wybierając **baz danych**, **objekt InstanceStore**, a następnie  **System.ServiceModel.Activities.DurableInstancing.InstanceTable** w Eksploratorze obiektów kliknij prawym przyciskiem myszy **System.ServiceModel.Activities.DurableInstancing.InstanceTable** i wybierz  **Zaznacz 1000 pierwszych wierszy**. Aby uzyskać więcej informacji na temat programu SQL Server Management Studio, zobacz [wprowadzenie do programu SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=165645)  
  
2.  Obserwuj wystąpienia przepływu pracy, na liście.  
  
3.  W [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia, uruchom skrypt QueryInstanceStore.cmd znajduje się w katalogu próbki (\WF\Basic\Persistence\SqlStoreExtensibility).  
  
4.  Sprawdź wartość licznika jest wyświetlany w obszarze **CountStatus**.  
  
5.  Uruchom skrypt kilka razy się **CountStats** wartość zmiany.  
  
6.  Naciśnij klawisz ENTER, aby zakończyć działanie aplikacji przepływu pracy.  
  
### <a name="to-uninstall-the-sample"></a>Aby odinstalować próbki  
  
1.  Usuń wystąpienie bazy danych magazynu, uruchamiając skrypt RemoveInstanceStore.cmd znajduje się w katalogu próbki (\WF\Basic\Persistence\SqlStoreExtensibility).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\SQLStoreExtensibility`  
  
## <a name="see-also"></a>Zobacz też  
 [Trwałość przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
