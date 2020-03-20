---
title: Zarządzanie wstrzymanymi wystąpieniami
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: 784ec3cdda8eedb188c3c776ed412ea40baf37ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182788"
---
# <a name="suspended-instance-management"></a>Zarządzanie wstrzymanymi wystąpieniami
W tym przykładzie pokazano, jak zarządzać wystąpień przepływu pracy, które zostały zawieszone.  Domyślną <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> akcją `AbandonAndSuspend`jest . Oznacza to, że domyślnie nieobsługiwane wyjątki generowane <xref:System.ServiceModel.WorkflowServiceHost> z wystąpienia przepływu pracy hostowane w spowoduje wystąpienie, które mają być usuwane z pamięci (porzucone) i trwałe/utrwalone wersji wystąpienia, które mają być oznaczone jako zawieszone. Wystąpienie zawieszonego przepływu pracy nie będzie można uruchomić, dopóki nie zostanie wstrzymane.

 Przykład pokazuje, jak narzędzie wiersza polecenia można zaimplementować do wykonywania zapytań o zawieszone wystąpienia i jak dać użytkownikowi możliwość wznowienia lub zakończenia wystąpienia. W tym przykładzie usługa przepływu pracy celowo zgłasza wyjątek, powodując, że zostanie zawieszony. Narzędzie wiersza polecenia może następnie służyć do wykonywania kwerend dla wystąpienia, a następnie wznawiania lub zakończenia wystąpienia.

## <a name="demonstrates"></a>Demonstracje
 <xref:System.ServiceModel.WorkflowServiceHost>z <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> i w Windows Workflow Foundation (WF).

## <a name="discussion"></a>Dyskusji
 Narzędzie wiersza polecenia zaimplementowane w tym przykładzie jest [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]specyficzne dla implementacji magazynu wystąpień SQL, która jest dostarczana w programie . Jeśli masz niestandardową implementację magazynu wystąpień, możesz dostosować `WorkflowInstanceCommand` to narzędzie, zastępując implementacje w przykładzie implementacjami specyficznymi dla magazynu wystąpień.

 Podana implementacja uruchamia polecenia SQL względem magazynu wystąpień SQL bezpośrednio do <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> listy zawieszonych wystąpień i opiera się na dodane <xref:System.ServiceModel.WorkflowServiceHost> do w celu wznowienia lub zakończenia wystąpień.

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę

1. W tym przykładzie wymaga włączenia następujących składników systemu Windows:

    1. Serwer kolejek komunikatów firmy Microsoft (MSMQ)

    2. SQL Server Express

2. Konfigurowanie bazy danych programu SQL Server.

    1. Z wiersza polecenia programu Visual Studio 2010 uruchom polecenie "setup.cmd" z przykładowego katalogu SuspendedInstanceManagement, który wykonuje następujące czynności:

        1. Tworzy bazę danych trwałości przy użyciu programu SQL Server Express. Jeśli baza danych trwałości już istnieje, zostanie ona porzucona i ponownie utworzona

        2. Konfiguruje bazę danych dla trwałości.

        3. Dodaje usługi IIS APPPOOL\DefaultAppPool i NT AUTHORITY\Network Service do roli InstanceStoreUsers, która została zdefiniowana podczas konfigurowania bazy danych pod kątem trwałości.

3. Skonfiguruj kolejkę usługi.

    1. W programie Visual Studio 2010 kliknij prawym przyciskiem myszy projekt **SampleWorkflowApp** i kliknij polecenie **Ustaw jako projekt startowy**.

    2. Skompiluj i uruchom SampleWorkflowApp, naciskając **klawisz F5**. Spowoduje to utworzenie wymaganej kolejki.

    3. Naciśnij **klawisz Enter,** aby zatrzymać plik SampleWorkflowApp.

    4. Otwórz konsolę Zarządzanie komputerem, uruchamiając plik Compmgmt.msc w wierszu polecenia.

    5. Rozwiń **węzeł Usługi i aplikacje**, **Kolejkowanie wiadomości,** **Kolejki prywatne**.

    6. Kliknij prawym przyciskiem myszy kolejkę **ReceiveTx** i wybierz polecenie **Właściwości**.

    7. Wybierz kartę **Zabezpieczenia** i **zezwalaj wszystkim** na uprawnienia do **odbierania wiadomości,** **wglądu**do wiadomości i **wysyłania wiadomości**.

4. Teraz uruchom próbkę.

    1. W programie Visual Studio 2010 uruchom ponownie projekt SampleWorkflowApp bez debugowania, naciskając **klawisze Ctrl+F5**. W oknie konsoli zostaną wydrukowane dwa adresy punktów końcowych: jeden dla <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>punktu końcowego aplikacji, a drugi z pliku . Następnie zostanie utworzone wystąpienie przepływu pracy, a rekordy śledzenia dla tego wystąpienia pojawią się w oknie konsoli. Wystąpienie przepływu pracy zda wyjątek powodujący zawieszenie i przerwanie wystąpienia.

    2. Narzędzie wiersza polecenia może następnie służyć do podejmowania dalszych działań na każdym z tych wystąpień. Składnia argumentów wiersza polecenia jest następująca::

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         Obsługiwane polecenia to: `Query`, `Resume`, `Terminate`i .  Przełącznik InstanceId jest wymagany `Resume` tylko `Terminate` dla i operacji.

#### <a name="to-cleanup-optional"></a>Aby wyczyścić (opcjonalnie)

1. Otwórz konsolę Zarządzanie komputerem, uruchamiając plik `vs2010` Compmgmt.msc w wierszu polecenia.

2. Rozwiń **węzeł Usługi i aplikacje**, **Kolejkowanie wiadomości,** **Kolejki prywatne**.

3. Usuń kolejkę **ReceiveTx.**

4. Aby usunąć bazę danych trwałości, uruchom cleanup.cmd.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
