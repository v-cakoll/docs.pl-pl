---
title: Scenariusz StateMachine używający kombinacji FlowChart i Pick
ms.date: 03/30/2017
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
ms.openlocfilehash: b0f8e884a8a6c62c4e7edaf5cc9727bf7bfe8603
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483929"
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a>Scenariusz StateMachine używający kombinacji FlowChart i Pick
W tym przykładzie pokazano, jak implementować scenariusza proste stopera, przy użyciu kombinacji <xref:System.Activities.Statements.Flowchart> i <xref:System.Activities.Statements.Pick> działań. Używa odbierania i wysyłania w ramach działania Pick do nasłuchiwania zdarzeń stopera.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do (strona pobierania) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a>Przykład szczegółów  
 Poniższa tabela zawiera listę projektów w tym przykładzie.  
  
|Nazwa projektu|Opis|  
|-|-|  
|StopWatchService|Ten projekt zawiera implementację automacie stanów dla przykładu stopera, przy użyciu kombinacji <xref:System.Activities.Statements.Flowchart> i <xref:System.Activities.Statements.Pick> działań.<br /><br /> <xref:System.Activities.Statements.Pick> Działanie ma 3 <xref:System.Activities.Statements.PickBranch> instrukcji <xref:System.Activities.Statements.Pick.Branches%2A> właściwość, która nasłuchuje `GetStart`, `GetStop` i `GetOff` zdarzenia. Oparte na przychodzącym zdarzeniu, Aktywuj wyzwalaczy dla jednej gałęzi i odpowiedni <xref:System.Activities.Statements.PickBranch.Action%2A> zostanie wywołany. W <xref:System.Activities.Statements.PickBranch.Action%2A> właściwości, Brak <xref:System.Activities.Statements.Switch%601> instrukcję, która ocenia, czy przejście jest uzasadnione przejścia i jeśli tak jest, `currentState` właściwości są aktualizowane do stanu przechodzenie i wysłane do klienta.<br /><br /> <xref:System.Activities.Statements.FlowDecision> Działania na końcu <xref:System.Activities.Statements.Flowchart> ocenia `currentState` właściwości w celu określenia, czy stan ma terminala. Jeśli tak jest, kończy się przepływu pracy; inny sposób kontroluje pętli powrót do początku <xref:System.Activities.Statements.Pick> działania, w którym czeka więcej wydarzeń stopera przepływu pracy.|  
|StopWatchClient|Jest to aplikacja konsoli prosty sekwencyjny przepływ pracy, która wysyła różnych zdarzeń stopera, za pomocą prostego wysyłać ani odbierać kombinacje działania.|  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania StateMachineWithPick.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Rozpocznij StopWatchService.exe z [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] jako administrator, klikając prawym przyciskiem myszy plik .exe i wybierając **Uruchom jako administrator**.  
  
    1.  Przejdź do folderu StateMachineWithPick\CS\StopWatchService\bin\Debug.  
  
    2.  Kliknij prawym przyciskiem myszy plik StopWatchService.exe, a następnie wybierz pozycję **Uruchom jako administrator**.  
  
4.  Uruchom aplikację klienta StopWatchClient z poziomu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    1.  W **Eksploratora rozwiązań**, wybierz opcję **StopWatchClient** projektu, a następnie kliknij prawym przyciskiem myszy **Ustaw jako projekt startowy**.  
  
    2.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
5.  Przejdź z powrotem do StopWatchService.exe do wyświetlania przejścia stanu można znaleźć w oknie konsoli.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`