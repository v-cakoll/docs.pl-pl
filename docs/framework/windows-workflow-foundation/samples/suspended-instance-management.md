---
title: Zarządzanie wstrzymanymi wystąpieniami
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: c23d2dfd48ecb57a3fb418734c916586178986e9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622421"
---
# <a name="suspended-instance-management"></a>Zarządzanie wstrzymanymi wystąpieniami
Niniejszy przykład pokazuje, jak zarządzać wystąpienia przepływu pracy, które zostało zawieszone.  Domyślna akcja dla <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> jest `AbandonAndSuspend`. Oznacza to, że domyślnie nieobsługiwanych wyjątków zgłoszonych z wystąpienia przepływu pracy hostowane w <xref:System.ServiceModel.WorkflowServiceHost> spowoduje wystąpienie Aby zostać usunięty z pamięci (porzucone) i trwałość/utrwalona wersję wystąpienia został oznaczony jako zawieszone. Wystąpienie Wstrzymany przepływ pracy nie będzie działać, dopóki nie zostało zawieszenia.

 Przedstawia przykładowe, jak narzędzie wiersza polecenia można zaimplementować zapytania dla wystąpień wstrzymania i udzielanie użytkownikowi opcję, aby wznowić lub zakończenie wystąpienia. W tym przykładzie Usługa przepływu pracy celowo zgłasza wyjątek, co powoduje wstrzymane. Narzędzie wiersza polecenia można następnie zapytania dla tego wystąpienia i następnie Wznów lub zakończyć wystąpienia.

## <a name="demonstrates"></a>Demonstracje
 <xref:System.ServiceModel.WorkflowServiceHost> za pomocą <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> i <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> w Windows Workflow Foundation (WF).

## <a name="discussion"></a>Dyskusja
 Narzędzie wiersza polecenia, w tym przykładzie jest specyficzne dla implementacji magazynu wystąpienia SQL, który jest dostarczany w [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Jeśli masz niestandardową implementację magazyn wystąpienia, a następnie to narzędzie można dostosować poprzez zastąpienie `WorkflowInstanceCommand` implementacji w przykładzie z implementacji, które są specyficzne dla sklepu wystąpienia.

 Podana implementacji uruchamia polecenia SQL względem magazynu wystąpienia SQL bezpośrednio po to, aby wyświetlić listę wystąpień wstrzymania i opiera się na <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> dodane do <xref:System.ServiceModel.WorkflowServiceHost> w celu wznowienia lub zakończenie wystąpienia.

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1. Ten przykładowy skrypt wymaga włączenia następujących składników Windows:

    1. Microsoft Message Queues (MSMQ) Server

    2. SQL Server Express

2. Konfigurowanie bazy danych programu SQL Server.

    1. Z wiersza polecenia programu Visual Studio 2010 należy uruchomić "plik setup.cmd" z katalogu przykładowe SuspendedInstanceManagement, który wykonuje następujące czynności:

        1. Tworzy bazę danych trwałości za pomocą programu SQL Server Express. Jeśli baza danych stanów trwałych już istnieje, a następnie jest porzucona i utworzona ponownie

        2. Konfiguruje bazę danych do stanu trwałego.

        3. Dodaje IIS APPPOOL\DefaultAppPool i NT AUTHORITY\Network Service do roli InstanceStoreUsers, która została określona podczas konfigurowania bazy danych dla trwałości.

3. Konfigurowanie usługi kolejki.

    1. W programie Visual Studio 2010, kliknij prawym przyciskiem myszy **SampleWorkflowApp** projektu, a następnie kliknij przycisk **Ustaw jako projekt startowy**.

    2. Kompilowanie i uruchamianie SampleWorkflowApp, naciskając klawisz **F5**. Spowoduje to utworzenie wymaganych kolejki.

    3. Naciśnij klawisz **Enter** przestanie SampleWorkflowApp.

    4. Otwórz konsolę Zarządzanie komputerem, uruchamiając Compmgmt.msc z poziomu wiersza polecenia.

    5. Rozwiń **usługi i aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.

    6. Kliknij prawym przyciskiem myszy **ReceiveTx** kolejki, a następnie wybierz pozycję **właściwości**.

    7. Wybierz **zabezpieczeń** kartę i umożliwiają **wszyscy** musi mieć uprawnienia do **odbieranie wiadomości**, **wglądu do wiadomości**, i  **Wyślij wiadomość**.

4. Teraz uruchom przykład.

    1. W programie Visual Studio 2010, SampleWorkflowApp project należy ponownie uruchomić bez debugowania, naciskając klawisz **kombinację klawiszy Ctrl + F5**. Dwa adresy punktów końcowych, które będą wypisywane w oknie konsoli: jeden dla punktu końcowego aplikacji i następnie inne z <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>. Wystąpienie przepływu pracy zostanie utworzony i śledzenia rekordów dla tego wystąpienia zostaną wyświetlone w oknie konsoli. Wystąpienie przepływu pracy spowoduje zgłoszenie wyjątku powoduje wystąpienie aby je zawieszać i zostało przerwane.

    2. Narzędzie wiersza polecenia, następnie może służyć do podejmowania dalszych działań na dowolnym z tych wystąpień. Składnia służąca do argumentów wiersza polecenia jest następujący:

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         Są obsługiwane polecenia: `Query`, `Resume`, i `Terminate`.  Identyfikator wystąpienia przełącznika jest wymagane tylko dla `Resume` i `Terminate` operacji.

#### <a name="to-cleanup-optional"></a>Aby oczyścić (opcjonalnie)

1. Otwórz konsolę Zarządzanie komputerem, uruchamiając Compmgmt.msc z `vs2010` wiersza polecenia.

2. Rozwiń **usługi i aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.

3. Usuń **ReceiveTx** kolejki.

4. Aby usunąć bazy danych trwałości, uruchom cleanup.cmd.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
