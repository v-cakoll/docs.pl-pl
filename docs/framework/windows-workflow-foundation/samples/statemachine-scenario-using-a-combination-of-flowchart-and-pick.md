---
title: Obiekt StateMachine scenariusz przy użyciu kombinacji schematu blokowego i pobrania
ms.date: 03/30/2017
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
ms.openlocfilehash: 0f7fc809b2fb7107de355546ca52a4d2ba2b39f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517939"
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a>Obiekt StateMachine scenariusz przy użyciu kombinacji schematu blokowego i pobrania
W tym przykładzie pokazano, jak wdrożyć scenariusz proste stopera, przy użyciu kombinacji <xref:System.Activities.Statements.Flowchart> i <xref:System.Activities.Statements.Pick> działań. Używa odbierania i wysyłania w działaniu wybierz do nasłuchiwania zdarzeń stopera.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do (stronę pobierania) można pobrać wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a>Szczegóły próbki  
 W poniższej tabeli wymieniono projekty w tym przykładzie.  
  
|Nazwa projektu|Opis|  
|-|-|  
|StopWatchService|Ten projekt zawiera implementację automatu stanów przykładowej stopera przy użyciu kombinacji <xref:System.Activities.Statements.Flowchart> i <xref:System.Activities.Statements.Pick> działań.<br /><br /> <xref:System.Activities.Statements.Pick> Działanie ma 3 <xref:System.Activities.Statements.PickBranch> instrukcje <xref:System.Activities.Statements.Pick.Branches%2A> właściwość, która nasłuchuje `GetStart`, `GetStop` i `GetOff` zdarzenia. Oparte na zdarzeniu przychodzących, aktywować Wyzwalacze dla jednej z gałęzi i odpowiadający mu <xref:System.Activities.Statements.PickBranch.Action%2A> zostanie wywołany. W <xref:System.Activities.Statements.PickBranch.Action%2A> właściwości, Brak <xref:System.Activities.Statements.Switch%601> instrukcji, która ocenia, czy przejście jest uzasadnione przejścia i jeśli istnieje, `currentState` właściwości jest zaktualizowany stan przechodzenie i wysłane do klienta.<br /><br /> <xref:System.Activities.Statements.FlowDecision> Działania na końcu <xref:System.Activities.Statements.Flowchart> ocenia `currentState` właściwości w celu określenia, czy stan jest terminala. Jeśli tak jest, kończy się przepływu pracy; inny sposób kontroluje pętle powrót do początku <xref:System.Activities.Statements.Pick> działania, w którym przepływ pracy czeka na więcej zdarzeń stopera.|  
|StopWatchClient|Jest to prosty sekwencyjny przepływ pracy aplikacja konsolowa, która wysyła różnych zdarzeń stopera przy prostego wysłać lub odebrać kombinacji działania.|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania StateMachineWithPick.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Uruchom StopWatchService.exe z [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] jako administrator, kliknięcie prawym przyciskiem myszy plik .exe i wybierając **Uruchom jako administrator**.  
  
    1.  Przejdź do folderu StateMachineWithPick\CS\StopWatchService\bin\Debug.  
  
    2.  Kliknij prawym przyciskiem myszy plik StopWatchService.exe i wybierz **Uruchom jako administrator**.  
  
4.  Uruchom aplikację klienta StopWatchClient z poziomu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    1.  W **Eksploratora rozwiązań**, wybierz pozycję **StopWatchClient** projekt i kliknij prawym przyciskiem myszy **Ustaw jako projekt startowy**.  
  
    2.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
5.  Przejdź do okna konsoli dla StopWatchService.exe wyświetlić przejścia stanu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`