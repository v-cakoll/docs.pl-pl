---
title: Zarządzanie wystąpieniami wstrzymane
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f5073e9de217637141d7e3c9d70bb6a0b7a9cd0
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="suspended-instance-management"></a>Zarządzanie wystąpieniami wstrzymane
W tym przykładzie pokazano, jak zarządzać wystąpienia przepływu pracy, które zostało zawieszone.  Domyślnym działaniem <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> jest `AbandonAndSuspend`. Oznacza to, że domyślnie nieobsługiwane wyjątki rzucane z wystąpieniem przepływu pracy hostowanych w <xref:System.ServiceModel.WorkflowServiceHost> spowoduje wystąpienie można usunąć z pamięci (porzucone) i wersji niezawodny/utrwalony wystąpienia może być oznaczony jako zawieszone. Nie będzie można uruchamiać, dopóki zostanie Anulowano wystąpienie Wstrzymany przepływ pracy.  
  
 W przykładowych pokazano, jak narzędzie wiersza polecenia można zaimplementować zapytania dla wystąpień wstrzymania i sposobu przesyłania opcję, aby wznowić, lub przerywania wystąpienia użytkownika. W tym przykładzie usługi przepływu pracy celowo zgłasza wyjątek, co powoduje stanie zawieszone. Narzędzie wiersza polecenia mogą następnie służyć do zapytania dla tego wystąpienia, a następnie Wznów lub przerywania wystąpienie.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.ServiceModel.WorkflowServiceHost> z <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> i <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> programie Windows Workflow Foundation (WF).  
  
## <a name="discussion"></a>Omówienie  
 Narzędzie wiersza polecenia zaimplementowana w tym przykładzie jest specyficzna dla Implementacja magazynu wystąpienia SQL, który jest dostarczany w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Jeśli masz niestandardowej implementacji w magazynie wystąpień, a następnie tego narzędzia można dostosować poprzez zastąpienie `WorkflowInstanceCommand` implementacji w przykładzie z implementacji, które są specyficzne dla sklepu wystąpienia.  
  
 Podana implementacji jest uruchamiana poleceń SQL dla magazynu wystąpienia SQL bezpośrednio, aby wyświetlić listę wystąpień zawieszone, i opiera się na <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> dodane do <xref:System.ServiceModel.WorkflowServiceHost> Aby wznowić, lub przerwanie wystąpienia.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  W tym przykładzie wymaga włączenia następujące składniki systemu Windows:  
  
    1.  Wiadomości firmy Microsoft (MSMQ) kolejek serwera  
  
    2.  SQL Server Express  
  
2.  Konfigurowanie bazy danych programu SQL Server.  
  
    1.  Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia, uruchom "setup.cmd" w katalogu próbki SuspendedInstanceManagement, który wykonuje następujące czynności:  
  
        1.  Tworzy bazę danych trwałości przy użyciu programu SQL Server Express. Jeśli trwałości bazy danych już istnieje, a następnie jest porzucona i utworzona ponownie  
  
        2.  Konfiguruje bazę danych trwałości.  
  
        3.  Dodaje IIS APPPOOL\DefaultAppPool i NT AUTHORITY\Network Service do roli InstanceStoreUsers, która została określona podczas konfigurowania bazy danych dla trwałości.  
  
3.  Konfigurowanie usługi kolejki.  
  
    1.  W [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], kliknij prawym przyciskiem myszy **SampleWorkflowApp** projekt i kliknij przycisk **Ustaw jako projekt startowy**.  
  
    2.  Kompilowanie i uruchamianie SampleWorkflowApp naciskając **F5**. Spowoduje to utworzenie wymagane kolejki.  
  
    3.  Naciśnij klawisz **Enter** przestanie SampleWorkflowApp.  
  
    4.  Otwórz konsolę Zarządzanie komputerem, uruchamiając Compmgmt.msc z wiersza polecenia.  
  
    5.  Rozwiń węzeł **usługi i aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.  
  
    6.  Kliknij prawym przyciskiem myszy **ReceiveTx** kolejki, a następnie wybierz **właściwości**.  
  
    7.  Wybierz **zabezpieczeń** karcie i umożliwić **wszyscy** uprawnień do **odbieranie wiadomości**, **wglądu do wiadomości**, i  **Wyślij wiadomość**.  
  
4.  Teraz uruchom próbkę.  
  
    1.  W [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], uruchom ponownie projekt SampleWorkflowApp bez debugowania, naciskając klawisz **Ctrl + F5**. Dwa adresy punktów końcowych będą wypisywane w oknie konsoli: jeden dla punktu końcowego aplikacji, a następnie inne z <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>. Wystąpienie przepływu pracy jest tworzona i śledzenie rekordów dla tego wystąpienia zostaną wyświetlone w oknie konsoli. Wystąpienie przepływu pracy spowoduje zgłoszenie wyjątku powoduje wystąpienie można je zawieszać i zostało przerwane.  
  
    2.  Narzędzie wiersza polecenia można następnie wykonywanie dodatkowych działań na żadnym z tych wystąpień. Składnia dla argumentów wiersza polecenia jest następująca:  
  
         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`  
  
         Są obsługiwane polecenia: `Query`, `Resume`, i `Terminate`.  Przełącznik identyfikator wystąpienia jest wymagana tylko dla `Resume` i `Terminate` operacji.  
  
#### <a name="to-cleanup-optional"></a>Do oczyszczania (opcjonalnie)  
  
1.  Otwórz konsolę Zarządzanie komputerem, uruchamiając Compmgmt.msc z `vs2010` wiersza polecenia.  
  
2.  Rozwiń węzeł **usługi i aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.  
  
3.  Usuń **ReceiveTx** kolejki.  
  
4.  Aby usunąć bazę danych trwałości, uruchom cleanup.cmd.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
