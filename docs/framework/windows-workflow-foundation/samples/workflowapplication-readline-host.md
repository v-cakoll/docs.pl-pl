---
title: "Działanie obiektu WorkflowApplication ReadLine hosta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7b362be-cb42-40d7-b9ef-cfc4aed2455b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8426dd3835f53eeb85711a691c878ce2b877d09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="workflowapplication-readline-host"></a>Działanie obiektu WorkflowApplication ReadLine hosta
Ten przykład jest hostem ReadLine ogólnego. Można załadować i uruchomić każdy przepływ pracy, przy użyciu dołączonej `ReadLine` działania (lub innych działań podoba Ci się pobierające dane z zakładek przywrócone ciągi). Dane wyjściowe z `WriteLine` działania lub jakikolwiek zapisywania <xref:System.Activities.Statements.WriteLine.TextWriter%2A> rozszerzenia jest kierowany do okna hosta. Gdy wystąpienie jest w stanie bezczynności, dostępne zakładki dla danego wystąpienia są wyświetlane w polu kombi. Zakładki, wybierając wprowadzanie za tekstem i naciskając przycisk zakładki Wznów kontynuować wykonywanie przepływu pracy. Można również anulować, przerwania lub przerywania wybrany przepływ pracy. Trwałości jest domyślnie — można zamknąć hosta i przywrócić go, a lista wystąpień jest wypełniana wystąpień w bazie danych. Jest używane śledzenie danych wyjściowych <xref:System.Activities.WorkflowApplication>— poziom zdarzenia do hosta z opcją, aby dodać szczegółowe śledzenie na poziomie działania.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 Istnieją dwie warstwy z tym hostem: widok i Menedżer wystąpienia. Widok składa się z `HostView` i `WorkflowApplicationInfo` klasy. Ogólne deseń dla tego hosta `HostView` na podstawie klasy, aby wyświetlić dostępne opcje użytkownikowi `WorkflowApplicationInfo` obiektów, które są przechowywane w rozsądny sposób w synchronizacji z wystąpieniami reprezentują. Warstwa Menedżera wystąpienia składa się z `WorkflowApplicationManager` klasy, która jest podstawową cała komunikacja z hosta, i `WorkflowDefinitionExtension` klasy, która będzie nadal występować relacja między wystąpieniem i definicji programu został uruchomiony z i kilka innych klas. `HostView` Wywołania kontrolowania operacji na `WorkflowApplicationManager`. Wywołania te są zwykle asynchroniczne do obsługi interfejsu użytkownika reakcji. Gdy asynchroniczną wywołuje zakończeniu `WorkflowApplicationManager` wykonywania wywołań do warstwy widoku za pomocą dobrze zdefiniowanych interfejsu (`IHostView`). `HostView` Klasa najczęściej dysponuje tymi połączeniami z `WorkflowApplicationManager` klasy do wątku interfejsu użytkownika. Pisania tekstu odbywa się wątkowo <xref:System.Activities.Statements.WriteLine.TextWriter%2A> obiekty dostarczane przez `HostView` klasy. Interfejs użytkownika nie jest jedynym elementem generujących zdarzenia. <xref:System.Activities.WorkflowApplication> Obiektów również sygnału `WorkflowApplicationManager` po Przejdź `Idle`, `Complete`, czy `Aborted`, na przykład. `WorkflowApplicationManager` Klasy pobiera poza wątku zdarzeń Oczyszczanie wysyłki lub aktualizowanie pracy do hosta.  
  
 Zapisywanie plików używane do uruchomienia <xref:System.Activities.WorkflowApplication> umożliwiają to `WorkflowDefinitionExtension` klasy. Implementuje <xref:System.Activities.Persistence.PersistenceIOParticipant> interfejs do uczestnictwa w trwałości i utrwalić ścieżkę do definicji przepływu pracy.  
  
 `WorkflowApplicationManager.Load` Metoda używa zachowaną ścieżkę do utworzenia wystąpienia programy przepływu pracy, wymagane do załadowania niedokończone <xref:System.Activities.WorkflowApplication> obiektów.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  W tym przykładzie wymaga programu SQL Express do zainstalowania. Program SQL Express jest dostarczany z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Otwórz wiersz polecenia programu Visual Studio 2010.  
  
3.  Przejdź do katalogu próbki (\WF\Basic\Execution\ControllingWorkflowApplications), a następnie uruchom CreateInstanceStore.cmd.  
  
4.  Skrypt CreateInstanceStore.cmd próbuje utworzyć bazę danych w domyślnym wystąpieniu programu SQL Server 2008 Express. Jeśli chcesz zainstalować bazy danych w innym wystąpieniu, należy zmodyfikować skrypt, aby to zrobić.  
  
5.  Kompiluj projekt WorkflowApplicationReadLineHost i uruchom go z poziomu wiersza polecenia.  
  
6.  Po uruchomieniu trwałości można opcjonalnie Włączanie lub wyłączanie. Ponadto można włączyć opcjonalnie szczegółowe działania lub wyłącza śledzenie.  
  
7.  Kliknij przycisk wielokropka obok **Uruchom** przycisk, aby przeglądać przepływu pracy zdefiniowanego w pliku XAML  
  
     Dwa przykłady znajdują się w folderze SampleWorkflows. W przykładzie parallel1.xaml przechodzi bezczynności.  
  
8.  Po wybraniu przykład naciśnij **Uruchom** przycisku.  
  
9. Jeśli lub gdy przepływ pracy bezczynny, **zakładki** pola kombi jest wypełniana dostępne zakładki.  
  
10. Opcje są w tym momencie wznowić zakładki, Anuluj, przerwania lub zakończenie przepływu pracy. Można również wyłączyć hosta i uruchom go ponownie. Jeśli pozostanie na trwałości, wystąpienia są zwalnianie podczas zamykania i załadowana ponownie po uruchomieniu w górę.  
  
     Aby wznowić zakładki, wybierz żądany zakładki, wpisz wartość w polu tekstowym obok pole kombi i naciśnij klawisz **wznowić zakładki**.  
  
#### <a name="to-remove-the-instance-store-database"></a>Aby usunąć bazę danych magazynu wystąpienia  
  
1.  Otwórz wiersz polecenia programu Visual Studio 2010.  
  
2.  Przejdź do katalogu próbki (\WF\Basic\Execution\ControllingWorkflowApplications), a następnie uruchom RemoveInstanceStore.cmd.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ControllingWorkflowApplications`