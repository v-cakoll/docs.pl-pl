---
title: ReadLine klasy Workflowapplication
ms.date: 03/30/2017
ms.assetid: f7b362be-cb42-40d7-b9ef-cfc4aed2455b
ms.openlocfilehash: 4388ff0285de58b0dc6f86af93aad84b2894373f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43470856"
---
# <a name="workflowapplication-readline-host"></a>ReadLine klasy Workflowapplication
W tym przykładzie jest hostem ReadLine ogólnego. Możesz załadować i uruchomić każdy przepływ pracy za pomocą dołączonej `ReadLine` działania (lub innych działań, takich jak go, które pobierają dane z zakładki wznowiono z użyciem ciągów). Dane wyjściowe z `WriteLine` działania lub cokolwiek zapisywania <xref:System.Activities.Statements.WriteLine.TextWriter%2A> rozszerzenia są kierowane do okna hosta. Jeśli wystąpienie jest w stanie bezczynności, w polu kombi są wyświetlane dostępne zakładki dla tego wystąpienia. Wybierając zakładkę, wprowadzanie za jakiś tekst i naciśnięcie przycisku zakładki wznowienie kontynuować wykonywanie przepływu pracy. Możesz również anulować, przerwać lub wybrany przepływ pracy zostanie zakończony. Trwałość jest domyślnie włączone — można zamknąć hosta i go przywrócić i listy wystąpień jest wypełniana wystąpień w bazie danych. Jest używane śledzenie danych wyjściowych <xref:System.Activities.WorkflowApplication>-zdarzeń do hosta o możliwość dodania szczegółowe śledzenie na poziomie działania na poziomie.  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Istnieją dwie warstwy na tym hoście: widok i Menadżerze wystąpień. Widok składa się z `HostView` i `WorkflowApplicationInfo` klasy. Ogólny wzorzec dla tego hosta polega na `HostView` na podstawie klasy, aby wyświetlić dostępne opcje użytkownikowi `WorkflowApplicationInfo` obiektów, które są przechowywane w uzasadniony sposób w synchronizacji z wystąpieniami, stanowią one. Warstwa Menedżera wystąpienia składa się z `WorkflowApplicationManager` klasy, czyli podstawowy cała komunikacja z hosta i `WorkflowDefinitionExtension` klasy, która będzie nadal występować relacja między wystąpienia, jak i definicja program został uruchomiony z i kilka innych klas. `HostView` Wywołania sterowania operacjami na `WorkflowApplicationManager`. Te wywołania są zazwyczaj asynchronicznych do obsługi interfejsu użytkownika dynamiczne. Gdy asynchroniczną wywołuje zakończeniu `WorkflowApplicationManager` wykonywania wywołań do warstwy widok za pomocą dobrze zdefiniowanych interfejsu (`IHostView`). `HostView` Klasa wywołuje w większości przypadków te wywołania z `WorkflowApplicationManager` klasy do wątku interfejsu użytkownika. Pisanie tekstu jest przeprowadzane sprawdzanie wątkowo <xref:System.Activities.Statements.WriteLine.TextWriter%2A> obiekty dostarczane przez `HostView` klasy. Interfejs użytkownika nie jest jedyną czynnością generujących zdarzenia. <xref:System.Activities.WorkflowApplication> Obiektów również sygnał `WorkflowApplicationManager` po przejściu `Idle`, `Complete`, czy `Aborted`, na przykład. `WorkflowApplicationManager` Klasa otrzymuje off wątek zdarzenia wysyłki czyszczenia lub aktualizowanie pracy do hosta.  
  
 Rejestrowanie plików używane do uruchomienia <xref:System.Activities.WorkflowApplication> jest zapewniana przez `WorkflowDefinitionExtension` klasy. Implementuje <xref:System.Activities.Persistence.PersistenceIOParticipant> interfejsu do uczestnictwa w trwałości i utrzymują się ścieżkę do definicji przepływu pracy.  
  
 `WorkflowApplicationManager.Load` Metoda używa przechowywanych ścieżki do utworzenia wystąpienia programy przepływu pracy wymagane do załadowania niedokończone <xref:System.Activities.WorkflowApplication> obiektów.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Ten przykładowy skrypt wymaga zainstalowania programu SQL Express. Program SQL Express jest dostarczany z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Otwórz wiersz polecenia programu Visual Studio 2010.  
  
3.  Przejdź do katalogu próbki (\WF\Basic\Execution\ControllingWorkflowApplications), a następnie uruchom CreateInstanceStore.cmd.  
  
4.  Skrypt CreateInstanceStore.cmd próbuje utworzyć bazę danych w domyślnym wystąpieniu programu SQL Server 2008 Express. Jeśli chcesz zainstalować bazę danych w innym wystąpieniu, należy zmodyfikować skrypt, aby to zrobić.  
  
5.  Kompilowanie projektu WorkflowApplicationReadLineHost i uruchom go z poziomu wiersza polecenia.  
  
6.  Po uruchomieniu trwałości można opcjonalnie Włączanie i wyłączanie. Dodatkowo można włączyć opcjonalnie szczegółowe działania lub wyłącza śledzenie.  
  
7.  Naciśnij przycisk wielokropka obok **Uruchom** przycisk, aby przejść do przepływu pracy zdefiniowanego w pliku XAML  
  
     Dwa przykłady można znaleźć w folderze SampleWorkflows. W przykładzie parallel1.xaml przechodzi bezczynności.  
  
8.  Po wybraniu przykład naciśnij **Uruchom** przycisku.  
  
9. Jeśli lub gdy przepływ pracy przechodzi w stan bezczynności, **zakładki** pola kombi jest wypełniana przy użyciu dostępnych zakładek.  
  
10. Opcje dotyczą na tym etapie wznowienie zakładki, anulować, przerwać lub zakończyć przepływ pracy. Można również zamknąć hosta i uruchom go ponownie. Jeśli pole pozostanie na trwałości, wystąpienia są załadowane podczas zamykania i ponownie załadowany w menu start w górę.  
  
     Aby wznowić zakładki, wybierz żądane zakładkę, wpisz wartość w polu tekstowym, obok pola kombi, a następnie naciśnij klawisz **wznowienie zakładki**.  
  
#### <a name="to-remove-the-instance-store-database"></a>Aby usunąć wystąpienie bazy danych magazynu  
  
1.  Otwórz wiersz polecenia programu Visual Studio 2010.  
  
2.  Przejdź do katalogu próbki (\WF\Basic\Execution\ControllingWorkflowApplications), a następnie uruchom RemoveInstanceStore.cmd.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ControllingWorkflowApplications`