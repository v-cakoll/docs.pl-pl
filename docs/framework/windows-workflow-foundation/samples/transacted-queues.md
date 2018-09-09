---
title: Kolejki transakcyjne
ms.date: 03/30/2017
ms.assetid: b1b011dd-5e0b-482c-9bb0-9d8727038f14
ms.openlocfilehash: db6a9686334eefb02b9360827a23ca8363127eb5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253198"
---
# <a name="transacted-queues"></a>Kolejki transakcyjne
Niniejszy przykład pokazuje, jak zintegrować kolejek oraz transakcje w Windows Workflow Foundation (WF) do tworzenia niezawodnych i skalowalnych usług. A <!--zz <xref:System.Activities.TransactionScope>--> `System.Activities.TransactionScope` jest używany w przepływie pracy klienta, aby wysłać wiadomość do kolejki w ramach transakcji przy użyciu <xref:System.ServiceModel.NetMsmqBinding>. Element <xref:System.ServiceModel.Activities.TransactedReceiveScope> jest używany na serwerze do odbierania komunikatów z kolejki i aktualizacja stanu przepływu pracy w ramach tej samej transakcji.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.Activities.Statements.TransactionScope>, <xref:System.ServiceModel.Activities.TransactedReceiveScope>, <xref:System.ServiceModel.NetMsmqBinding>, <xref:System.ServiceModel.Activities.Receive>i na podstawie zawartości korelacji.  
  
## <a name="discussion"></a>Dyskusja  
 Aby zademonstrować funkcje omówione w tym przykładzie `RewardsPoints` usługi przepływu pracy jest tworzony, która przechowuje informacje o punktach zdobytych i używany dla danego konta. Klient używa <xref:System.Activities.WorkflowInvoker> zasymulować, publikowanie różnych żądań w kolejce. Do publikowania komunikatów w kolejce w ramach transakcji, <xref:System.ServiceModel.Activities.Send> działanie może być umieszczone wewnątrz <xref:System.Activities.Statements.TransactionScope.Body%2A> z <xref:System.Activities.Statements.TransactionScope>. W tym przykładzie klient uruchamia najpierw następuje serwera, aby zademonstrować sposób umieszczonych w kolejce wiadomości można rozdzielić aplikacje klienta i serwera.  
  
 Po ukończeniu klient skonfigurowany i usługi hostowanej. Jak najszybciej po jego otwarciu rozpoczyna się przetwarzanie komunikatów, które już zostały umieszczone w kolejce. Każdy komunikat jest odbierany i przetwarzany w ramach tej samej transakcji serwera. W tym przykładzie jest pierwszy komunikat odebrany `CreateAccount` żądania, który tworzy wystąpienie i inicjuje korelację zawartości na podstawie nazwy konta przekazany jako część komunikatu żądania. Do modelowania rodzaj usługi można by oczekiwać w świecie rzeczywistym następujące dwa <xref:System.ServiceModel.Activities.TransactedReceiveScope> działań, które przetwarzają `AddPoints` i `UsePoints` wiadomości są umieszczane w gałęzi równoległych w ramach `while` pętli, dzięki czemu mogą one przetwarzają je komunikaty wielokrotnie w dowolnej kolejności.  
  
 <xref:System.Activities.Statements.TransactionScope> i <xref:System.ServiceModel.Activities.TransactedReceiveScope> mają punkt niejawne trwałości na końcu ich zakresach, za pomocą tych działań w [!INCLUDE[wf1](../../../../includes/wf1-md.md)] w połączeniu z kolejki jest niezawodny sposób można przenieść przepływu pracy z jednego spójnego stanu do drugiego, przy jednoczesnym zapewnieniu, że wiadomości są nigdy nie zostanie utracone.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Instalowanie i konfigurowanie usługi MSMQ. Zobacz [Instalowanie usługi kolejkowania komunikatów](https://go.microsoft.com/fwlink/?LinkId=178526) Aby uzyskać szczegółowe informacje.  
  
2.  Upewnij się, że usługa MSDTC jest uruchomiona, wykonując następujące polecenie w wierszu polecenia. `net start msdtc`  
  
3.  Skompilować projekt i Otwórz plik wykonywalny lub otworzyć projekt w programie [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i wybierz opcję rozpoczęcia z menu Debugowanie. Najpierw tworzenia kolejki, a następnie klient uruchamia i publikuje komunikaty do kolejki i na koniec uruchomienie usługi i komunikaty są przetwarzane. Aby zakończyć program, naciśnij klawisz ENTER.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedQueues`
