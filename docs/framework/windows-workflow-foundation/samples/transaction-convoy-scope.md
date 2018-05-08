---
title: Zakres który transakcji
ms.date: 03/30/2017
ms.assetid: 37141708-a29f-4b6a-81fe-f8a11f825061
ms.openlocfilehash: 4b053c15768a20ade4a469c9a40af797f49c268b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="transaction-convoy-scope"></a>Zakres który transakcji
Ten przykład przedstawia sposób tworzenia równoległych który wiadomości wzorzec działania w połączeniu z <xref:System.ServiceModel.Activities.TransactedReceiveScope> do modelowania protokołu, na której liczba operacji może się zdarzyć w dowolnej kolejności, wszystkie w tej samej transakcji. W tym przykładzie również pokazano, jak <xref:System.ServiceModel.Activities.TransactedReceiveScope> automatycznie tworzy nową transakcję, gdy jeden jest nie umieszczane na serwerze, więc klienta nie powoduje użycie wszystkich transakcji.  
  
 Przykład zawiera dwa projekty przepływu pracy, które reprezentują klienta i serwera. Projekt klienta uruchamia przepływ pracy, który rozpoczyna się od wysyłania komunikatu do ładowania początkowego serwera przepływu pracy, które inicjuje korelację i uruchamia transakcyjne zakresu w pozostałej części działania obsługi wiadomości. Klient <xref:System.Activities.Statements.Sequence> działania zawiera wstępne <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> pary, a następnie <xref:System.Activities.Statements.Parallel> działania o trzy gałęzie. Każda gałąź wysyła komunikat jednokierunkowy do serwera. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> Właściwość <xref:System.Activities.Statements.Parallel> działanie ma ustawioną wartość `false` tak, aby wykonać wszystkie trzy gałęzie.  
  
 Przepływ pracy serwera jest podobny do przepływu pracy klienta, z wyjątkiem działania obsługi komunikatów są ukierunkowane na komunikację po stronie serwera i są zawarte w <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania, aby wszystkie pracy wykonywanej wykonuje w tej samej transakcji. Po odebraniu pierwszego komunikatu na serwerze transakcji jest tworzony i staje się w zakresie otaczającym <xref:System.ServiceModel.Activities.TransactedReceiveScope> body, tak aby wszystkie działania w tym zakresie mogą uzyskiwać dostęp do transakcji. Dzięki temu wszystkie odbiera wykonywanie równoległe. Odbiera wszystkie musi wykonać tylko raz w sposób opisany w stan ukończenia działania równoległe. Istnieje punkt niejawne trwałości na końcu <xref:System.ServiceModel.Activities.TransactedReceiveScope> treści i operacji trwałości również jest wykonywane w ramach tej samej transakcji.  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania ParallelConvoySample.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Upewnij się, że oba projekty są ustawione na uruchomienie.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy rozwiązanie i wybierz **Ustaw projekty startowe**.  
  
    2.  Wybierz **wiele projektów startowych** i upewnij się, ustawiono akcję dla obu projektów **Start**.  
  
4.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
     Serwer wydruku `Server is running`, co oznacza serwera jest gotowy.  
  
     Naciśnij dowolny klawisz, w oknie konsoli klienta do uruchomienia przykładu.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedConvoyScope`