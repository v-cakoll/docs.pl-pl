---
title: Transakcyjne kolejki.
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1b011dd-5e0b-482c-9bb0-9d8727038f14
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2373d4d7bec73b6f517c7bd3dfeeb4c26edf7d5d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="transacted-queues"></a>Transakcyjne kolejki.
W tym przykładzie pokazano, jak zintegrować kolejek oraz transakcje w [!INCLUDE[wf](../../../../includes/wf-md.md)] do tworzenia usług niezawodnych i skalowalności. A <!--zz <xref:System.Activities.TransactionScope>--> `System.Activities.TransactionScope` jest używany w przepływie pracy klienta do wysyłania wiadomości do kolejki w transakcji za pomocą <xref:System.ServiceModel.NetMsmqBinding>. A <xref:System.ServiceModel.Activities.TransactedReceiveScope> jest używany na serwerze do odbierania wiadomości z kolejki i zaktualizowanie stanu przepływu pracy w tej samej transakcji.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.Activities.Statements.TransactionScope>, <xref:System.ServiceModel.Activities.TransactedReceiveScope>, <xref:System.ServiceModel.NetMsmqBinding>, <xref:System.ServiceModel.Activities.Receive>i na podstawie zawartości korelacji.  
  
## <a name="discussion"></a>Omówienie  
 Aby zademonstrować funkcje omówione w tym przykładzie `RewardsPoints` usługi przepływu pracy został utworzony, która przechowuje informacje o punktach zdobytych i używany dla danego konta. Klient używa <xref:System.Activities.WorkflowInvoker> do symulowania zamieszczając różnych żądań w kolejce. Aby wysłać wiadomość do kolejki w ramach transakcji <xref:System.ServiceModel.Activities.Send> działania może być umieszczony wewnątrz <xref:System.Activities.Statements.TransactionScope.Body%2A> z <xref:System.Activities.Statements.TransactionScope>. W tym przykładzie klient uruchamia najpierw następuje serwera, aby zademonstrować sposób umieszczonych w kolejce wiadomości mogą rozdzielenie klienta i serwera aplikacji.  
  
 Po zakończeniu pracy klienta, skonfigurowane i usługi hostowanej. Zaraz po otwarciu, rozpoczyna przetwarzanie komunikatów, które już zostały umieszczone w kolejce. Każdy komunikat jest odbierany i przetwarzany w tej samej transakcji serwera. W tym przykładzie jest pierwszy komunikat `CreateAccount` żądania, która tworzy wystąpienie i inicjuje korelację zawartości na podstawie nazwy konta przekazanych jako część komunikatu żądania. Modelowanie rodzaj usługi może oczekiwać w świecie rzeczywistym dwa <xref:System.ServiceModel.Activities.TransactedReceiveScope> działań, które przetwarzają `AddPoints` i `UsePoints` wiadomości są umieszczane w równoległych gałęziach w `while` pętli, dzięki czemu mogą one przetworzone komunikaty wielokrotnie w dowolnej kolejności.  
  
 <xref:System.Activities.Statements.TransactionScope>i <xref:System.ServiceModel.Activities.TransactedReceiveScope> ma każdego punktu niejawne trwałości na końcu ich zakresy przy użyciu tych działań w [!INCLUDE[wf1](../../../../includes/wf1-md.md)] połączeniu z kolejek jest to niezawodny sposób przenoszenia przepływu pracy z jednego spójnego stanu do następnego, przy jednoczesnym zapewnieniu, że komunikaty są nigdy nie zostanie utracone.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Instalowanie i konfigurowanie usługi MSMQ. Zobacz [Instalowanie usługi kolejkowania komunikatów](http://go.microsoft.com/fwlink/?LinkId=178526) szczegółowe informacje.  
  
2.  Upewnij się, że usługa MSDTC jest uruchomiona, wykonując następujące polecenie w wierszu polecenia. `net start msdtc`  
  
3.  Skompiluj projekt i otworzyć plik wykonywalny lub Otwórz projekt w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i wybierz opcję uruchomienia z menu Debugowanie. Najpierw tworzenia kolejki, a następnie klient uruchamia i przesyła wiadomości do kolejki i na koniec uruchomienia usługi i komunikaty są przetwarzane. Aby zakończyć działanie programu, naciśnij klawisz ENTER.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedQueues`
