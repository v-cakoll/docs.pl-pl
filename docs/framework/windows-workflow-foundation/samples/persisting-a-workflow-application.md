---
title: "Utrwalanie aplikacji przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abcff14c-f047-4195-ba26-d27f4a82c24e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf23b8e33766ea7a15135418142082a0e7b715ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="persisting-a-workflow-application"></a>Utrwalanie aplikacji przepływu pracy
W tym przykładzie pokazano, jak uruchomić <xref:System.Activities.WorkflowApplication>, zwolnić ją, gdy przechodzi on bezczynny, a następnie ponownie załaduj może kontynuować działania.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 <xref:System.Activities.WorkflowApplication>jest hostem dla wystąpienia jednym przepływie pracy, który udostępnia prosty interfejs i umożliwia kilka więcej typowych scenariuszy hostingu. Taki scenariusz jest długa uruchamiania przepływów pracy w ramach trwałości. Host kontroli trwałości jest wykonywana albo przez wywołanie operacji trwałości w <xref:System.Activities.WorkflowApplication>, lub obsługa <xref:System.Activities.WorkflowApplication> zdarzeń i wskazujący, że <xref:System.Activities.WorkflowApplication> ma utrwalić.  
  
 Przykładowy przepływ pracy jest <xref:System.Activities.Statements.WriteLine> działania monitowania użytkownika o ich nazw, `ReadLine` działania odbierania nazwę jako dane wejściowe do wznowienia <xref:System.Activities.Bookmark>i innym <xref:System.Activities.Statements.WriteLine> do wyświetlania pozdrowienia użytkownikowi. Gdy przepływ pracy oczekuje na dane wejściowe, zapewnia punkt fizycznych trwałości. Jest to często określane jako <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> punktu. <xref:System.Activities.WorkflowApplication>zgłasza <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> zdarzeń zawsze, gdy program przepływu pracy może zostać utrwalony, oczekuje na wznowienie zakładki, i jest wykonywane żadne inne czynności. W tym przykładowym przepływie pracy, punkt dołączanego bezpośrednio po `ReadLine` rozpoczyna się działanie wykonywania.  
  
 A <xref:System.Activities.WorkflowApplication> jest skonfigurowany do wykonywania trwałości z <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`. W przykładzie użyto <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>. <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore` Musi być przypisany do <xref:System.Activities.WorkflowApplication.InstanceStore%2A> właściwości przed <xref:System.Activities.WorkflowApplication> jest uruchamiany.  
  
 Przykład dodaje program obsługi do <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> zdarzeń. Program obsługi dla tego zdarzenia wskazuje co <xref:System.Activities.WorkflowApplication> zrobić, zwracając <xref:System.Activities.PersistableIdleAction>. Gdy <xref:System.Activities.PersistableIdleAction.Unload> jest zwracany, <xref:System.Activities.WorkflowApplication> zostanie zwolniona.  
  
 Przykład następnie akceptuje dane wejściowe użytkownika i ładuje utrwalonych przepływów pracy w nowym <xref:System.Activities.WorkflowApplication>. Robi to przez utworzenie nowej <xref:System.Activities.WorkflowApplication>, odtwarzanie <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`i kojarzenie została zakończona i zwolniony zdarzenia do wystąpienia, a następnie podczas wywoływania <xref:System.Activities.WorkflowApplication.Load%2A> o identyfikatorze wystąpienia przepływu pracy docelowej. Gdy wystąpienie jest uzyskiwana, `ReadLine` wznowieniu działania zakładki. Przepływ pracy prowadzi wykonywania z poziomu `ReadLine` działanie i uruchamia do zakończenia. Po zakończeniu przepływu pracy i zwalnia, <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore` jest wywoływana raz ostatni, aby usunąć przepływ pracy.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
     W tym przykładzie wymaga programu SQL Server Express, który jest instalowany domyślnie z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Przejdź do katalogu próbki (\WF\Basic\Persistence\InstancePersistence\CS), a następnie uruchom CreateInstanceStore.cmd.  
  
    > [!CAUTION]
    >  Skrypt CreateInstanceStore.cmd próbuje utworzyć bazę danych w domyślnym wystąpieniu programu SQL Server 2008 Express. Jeśli chcesz zainstalować bazy danych w innym wystąpieniu, należy zmodyfikować skrypt, aby to zrobić.  
  
3.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania Persistence.sln i naciśnij klawisze CTRL + SHIFT + B, aby go skompilować.  
  
    > [!CAUTION]
    >  Jeśli zainstalowano bazy danych w innych niż domyślne wystąpienie programu SQL Server, należy zaktualizować parametry połączenia w kodzie przed kompilacją rozwiązania.  
  
4.  Uruchom próbki z uprawnieniami administratora, przechodząc do katalogu bin projektu (\WF\Basic\Persistence\InstancePersistence\bin\Debug) w [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], klikając prawym przyciskiem myszy Workflow.exe i wybierając **Uruchom jako Administrator**.  
  
#### <a name="to-remove-the-instance-store-database"></a>Aby usunąć bazę danych magazynu wystąpienia  
  
1.  Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.  
  
2.  Przejdź do katalogu próbki i uruchom RemoveInstanceStore.cmd.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\InstancePersistence`  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
