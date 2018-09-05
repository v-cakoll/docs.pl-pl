---
title: Utrwalanie aplikacji przepływu pracy
ms.date: 03/30/2017
ms.assetid: abcff14c-f047-4195-ba26-d27f4a82c24e
ms.openlocfilehash: 0c225a9ed56a742fce0aaff3704bab31dabb0b9a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500007"
---
# <a name="persisting-a-workflow-application"></a>Utrwalanie aplikacji przepływu pracy
W tym przykładzie pokazano, jak uruchomić <xref:System.Activities.WorkflowApplication>zwolnić ją, gdy usługa zostanie wprowadzona bezczynności i ponownie załadować go, aby kontynuować wykonywanie.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 <xref:System.Activities.WorkflowApplication> jest hostem dla wystąpienia jeden przepływ pracy, która zapewnia prosty interfejs oraz umożliwia niektóre typowe scenariusze hostingu. Taki scenariusz jest długa uruchamiania przepływów pracy wspieranego przez stan trwały. Sterowanie hostem trwałość odbywa się to przez wywołanie operacji trwałości na <xref:System.Activities.WorkflowApplication>, lub obsługując <xref:System.Activities.WorkflowApplication> zdarzeń i wskazuje, że <xref:System.Activities.WorkflowApplication> utrwalać.  
  
 Przykładowy przepływ pracy jest <xref:System.Activities.Statements.WriteLine> działania monitowania użytkownika o ich nazwy `ReadLine` działania do odbierania nazwę jako dane wejściowe do wznowienia <xref:System.Activities.Bookmark>, a inny <xref:System.Activities.Statements.WriteLine> do wyświetlania pozdrowienia do użytkownika. Gdy przepływ pracy jest oczekiwanie na dane wejściowe, dzięki temu naturalny punkt potrzeby stanu trwałego. To jest często nazywany <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> punktu. <xref:System.Activities.WorkflowApplication> wywołuje <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> wydarzenie w dowolnym momencie może być utrwalony program przepływu pracy, trwa oczekiwanie na wznowienie zakładki, a nie innych zadań jest wykonywana. W tym przykładowym przepływie pracy, dostarczanego przez punkt natychmiast po `ReadLine` działania rozpoczyna wykonywanie.  
  
 A <xref:System.Activities.WorkflowApplication> jest skonfigurowany do wykonywania trwałości za pomocą <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`. W tym przykładzie użyto <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>. <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore` Muszą być przypisane do <xref:System.Activities.WorkflowApplication.InstanceStore%2A> właściwości przed <xref:System.Activities.WorkflowApplication> jest uruchamiany.  
  
 Przykładowa aplikacja dodaje program obsługi do <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> zdarzeń. Obsługa to zdarzenie wskazuje, co <xref:System.Activities.WorkflowApplication> należy wykonać, zwracając <xref:System.Activities.PersistableIdleAction>. Gdy <xref:System.Activities.PersistableIdleAction.Unload> zwracany jest <xref:System.Activities.WorkflowApplication> jest zwalniana.  
  
 Przykład następnie akceptuje dane wejściowe od użytkownika i ładuje utrwalonych przepływów pracy w nowym <xref:System.Activities.WorkflowApplication>. Robi to przez utworzenie nowego <xref:System.Activities.WorkflowApplication>, odtwarzanie <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`oraz skojarzyć ukończone i nie załadowany zdarzenia do wystąpienia, a następnie wywołując <xref:System.Activities.WorkflowApplication.Load%2A> z identyfikatorem wystąpienia docelowego przepływu pracy. Gdy wystąpienie jest uzyskana, `ReadLine` zakładki tego działania zostanie wznowione. Przepływ pracy niesie ze sobą na wykonywanie z poziomu `ReadLine` działania i uruchomienia do ukończenia. Gdy przepływ pracy zakończy i zwalnia, <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore` jest wywoływana raz ostatni, aby usunąć przepływ pracy.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
     Ten przykładowy skrypt wymaga programu SQL Server Express, który jest instalowany domyślnie z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Przejdź do katalogu próbki (\WF\Basic\Persistence\InstancePersistence\CS), a następnie uruchom CreateInstanceStore.cmd.  
  
    > [!CAUTION]
    >  Skrypt CreateInstanceStore.cmd próbuje utworzyć bazę danych w domyślnym wystąpieniu programu SQL Server 2008 Express. Jeśli chcesz zainstalować bazę danych w innym wystąpieniu, należy zmodyfikować skrypt, aby to zrobić.  
  
3.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania Persistence.sln i naciśnij klawisze CTRL + SHIFT + B do jego tworzenia.  
  
    > [!CAUTION]
    >  Jeśli baza danych jest zainstalowana na innych niż domyślne wystąpienie programu SQL Server, należy zaktualizować parametry połączenia w kodzie przed kompilowania rozwiązania.  
  
4.  Uruchom aplikację przykładową z uprawnieniami administratora, przejdź do katalogu bin projektu (\WF\Basic\Persistence\InstancePersistence\bin\Debug) w [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], klikając prawym przyciskiem myszy Workflow.exe i wybierając opcję **Uruchom jako Administrator**.  
  
#### <a name="to-remove-the-instance-store-database"></a>Aby usunąć wystąpienie bazy danych magazynu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
2.  Przejdź do katalogu próbki, a następnie uruchom RemoveInstanceStore.cmd.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\InstancePersistence`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
