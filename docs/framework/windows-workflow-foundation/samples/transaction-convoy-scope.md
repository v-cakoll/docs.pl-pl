---
title: Zakres konwoju transakcji
ms.date: 03/30/2017
ms.assetid: 37141708-a29f-4b6a-81fe-f8a11f825061
ms.openlocfilehash: fa1da6df5ad5256665610c9b3c2df7d706cef63c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46000430"
---
# <a name="transaction-convoy-scope"></a>Zakres konwoju transakcji
Ten przykład przedstawia sposób tworzenia równoległych konwoju, obsługi komunikatów wzorzec aktywności w połączeniu z <xref:System.ServiceModel.Activities.TransactedReceiveScope> do modelowania protokołu, na której liczba operacji może się zdarzyć w dowolnej kolejności, wszystkie w ramach tej samej transakcji. Ten przykład ilustruje też sposób <xref:System.ServiceModel.Activities.TransactedReceiveScope> automatycznie tworzy nową transakcję w przypadku jednego jest nie przekazane do serwera, aby klient nie oznacza, że korzystanie z wszystkich transakcji.  
  
 Przykład składa się z dwóch projektów przepływu pracy, które reprezentują klienta i serwera. Projekt klienta uruchamia przepływ pracy, który rozpoczyna się od wysyłania komunikatu do ładowania początkowego serwera przepływu pracy, którą korelacja inicjuje i uruchamia transakcyjnych zakres dla pozostałych działań dotyczących komunikatów. Klient <xref:System.Activities.Statements.Sequence> zawiera działanie po początkowym <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> pary i następnie <xref:System.Activities.Statements.Parallel> działanie przy użyciu trzech gałęzi. Każda gałąź wysyła komunikat jednokierunkowy do serwera. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> Właściwość <xref:System.Activities.Statements.Parallel> działania jest ustawiona na `false` tak, aby wykonać wszystkie trzy gałęzie.  
  
 Przepływ pracy serwera jest podobny do przepływu pracy klienta, z wyjątkiem działań dotyczących komunikatów są ukierunkowane na komunikacji po stronie serwera i są zawarte w obrębie <xref:System.ServiceModel.Activities.TransactedReceiveScope> działanie, aby wszystko działało gotowe wykonywane w ramach tej samej transakcji. Po odebraniu pierwszego komunikatu na serwerze transakcji jest tworzony i wykonano otoczenia w zakresie <xref:System.ServiceModel.Activities.TransactedReceiveScope> treści, tak aby wszystkie działania w tym zakresie mogą uzyskiwać dostęp do transakcji. Dzięki temu wszystkie odbiera równolegle uruchomić. Odbiera wszystkie musi wykonać tylko raz, zgodnie z opisem w warunku zakończenia działania równoległe. Punkt niejawne trwałości występuje na końcu <xref:System.ServiceModel.Activities.TransactedReceiveScope> treści i operacji trwałości jest również wykonywane w ramach tej samej transakcji.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ParallelConvoySample.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Upewnij się, że oba projekty są ustawione na uruchomienie.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Ustaw projekty startowe**.  
  
    2.  Wybierz **wiele projektów startowych** i upewnij się, ustawiono akcję dla obu projektów **Start**.  
  
4.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
     Drukuje serwera `Server is running`, która wskazuje serwer jest gotowy.  
  
     Naciśnij dowolny klawisz, w oknie konsoli klienta do uruchomienia przykładu.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedConvoyScope`