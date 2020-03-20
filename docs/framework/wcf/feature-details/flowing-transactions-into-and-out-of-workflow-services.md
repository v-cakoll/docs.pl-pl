---
title: Przepływy transakcji do i z usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: fe03047dd931d25ec94bbc5e00c479d1b42397bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185277"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Przepływy transakcji do i z usług przepływu pracy
Usługi przepływu pracy i klienci mogą uczestniczyć w transakcjach.  Aby operacja usługi stała się częścią transakcji <xref:System.ServiceModel.Activities.Receive> otoczenia, <xref:System.ServiceModel.Activities.TransactedReceiveScope> umieść działanie w działaniu. Wszelkie połączenia wykonane <xref:System.ServiceModel.Activities.Send> przez <xref:System.ServiceModel.Activities.SendReply> lub <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania w ramach będą również dokonywane w ramach transakcji otoczenia. Aplikacja kliencka przepływu pracy można utworzyć <xref:System.Activities.Statements.TransactionScope> transakcję otoczenia przy użyciu operacji działania i wywołania usługi przy użyciu transakcji otoczenia. W tym temacie opracowywanie tworzenia usługi przepływu pracy i klienta przepływu pracy, które uczestniczą w transakcjach.  
  
> [!WARNING]
> Jeśli wystąpienie usługi przepływu pracy jest ładowane <xref:System.Activities.Statements.Persist> w ramach transakcji, a przepływ pracy zawiera działanie, wystąpienie przepływu pracy zostanie zablokowane, dopóki nie wydłuży się limit czasu transakcji.  
  
> [!IMPORTANT]
> Za każdym razem, gdy używasz <xref:System.ServiceModel.Activities.TransactedReceiveScope> zaleca się umieścić <xref:System.ServiceModel.Activities.TransactedReceiveScope> wszystkie odbiera w przepływie pracy w działaniach.  
  
> [!IMPORTANT]
> Podczas <xref:System.ServiceModel.Activities.TransactedReceiveScope> korzystania i wiadomości przychodzą w niewłaściwej kolejności, przepływ pracy zostanie przerwana podczas próby dostarczenia pierwszego komunikatu poza kolejnością. Należy upewnić się, że przepływ pracy jest zawsze w spójnym punkcie zatrzymania, gdy przepływ pracy jest bezczynny. Umożliwi to ponowne uruchomienie przepływu pracy z poprzedniego punktu trwałości w przypadku przerwania przepływu pracy.  
  
### <a name="create-a-shared-library"></a>Tworzenie biblioteki udostępnionej  
  
1. Utwórz nowe puste rozwiązanie programu Visual Studio.  
  
2. Dodaj nowy projekt biblioteki klas o nazwie `Common`. Dodaj odwołania do następujących zestawów:  
  
    - Plik System.Activities.dll  
  
    - System.ServiceModel.dll  
  
    - Plik System.ServiceModel.Activities.dll  
  
    - System.Transactions.dll  
  
3. Dodaj nową klasę `PrintTransactionInfo` wywoływaną `Common` do projektu. Ta klasa jest <xref:System.Activities.NativeActivity> pochodną i <xref:System.Activities.NativeActivity.Execute%2A> przeciąża metodę.  
  
    ```csharp
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
    ```  
  
     Jest to działanie macierzyste, które wyświetla informacje o transakcji otoczenia i jest używany zarówno w przepływach pracy usługi i klienta używane w tym temacie. Skompiluj rozwiązanie, aby udostępnić to działanie w sekcji **Wspólne** **przybornika**.  
  
### <a name="implement-the-workflow-service"></a>Implementowanie usługi przepływu pracy  
  
1. Dodaj nową usługę przepływu pracy WCF, wywoływaną `WorkflowService` do `Common` projektu. Aby to zrobić, `Common` kliknij prawym przyciskiem myszy projekt, wybierz pozycję **Dodaj**, **Nowy element ...**, Wybierz przepływ **pracy** w obszarze **Zainstalowane szablony** i wybierz pozycję Usługa przepływu pracy **WCF**.  
  
     ![Dodawanie usługi przepływu pracy](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Usuń ustawienia `ReceiveRequest` `SendResponse` domyślne i działania.  
  
3. Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść aktywność do `Sequential Service` działania. Ustaw właściwość `"Workflow Service starting ..."` text, jak pokazano w poniższym przykładzie.  
  
     ! [Dodawanie działania WriteLine do działania Sekwencyjnej usługi(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg)  
  
4. Przeciągnij i <xref:System.ServiceModel.Activities.TransactedReceiveScope> upuść po <xref:System.Activities.Statements.WriteLine> aktywności. Działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> można znaleźć w sekcji **Wiadomości** w **przyborniku**. Działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> składa się z dwóch sekcji **Żądanie** i **Treść**. Sekcja **Żądanie** zawiera <xref:System.ServiceModel.Activities.Receive> działanie. **Treść** Sekcja zawiera działania do wykonania w ramach transakcji po odebraniu wiadomości.  
  
     ![Dodawanie działania TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. Wybierz <xref:System.ServiceModel.Activities.TransactedReceiveScope> działanie i kliknij przycisk **Zmienne.** Dodaj następujące zmienne.  
  
     ![Dodawanie zmiennych do skrytu TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > Zmienną danych, która jest tam domyślnie. Można również użyć istniejącej zmiennej dojścia.  
  
6. Przeciągnij i <xref:System.ServiceModel.Activities.Receive> upuść działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> w sekcji **Żądanie** działania. Ustaw następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |Cancreateinstance|Prawda (zaznacz pole wyboru)|  
    |OperationName|PoczątekPróby|  
    |Nazwa kontraktu servicecontract|ITransactionPróbuj|  
  
     Przepływ pracy powinien wyglądać następująco:  
  
     ![Dodawanie działania odbierania](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. Kliknij **łącze Definiuj...** w <xref:System.ServiceModel.Activities.Receive> działaniu i wykonuj następujące ustawienia:  
  
     ![Ustawianie ustawień komunikatu dla działania Odbierania](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Przeciągnij i <xref:System.Activities.Statements.Sequence> upuść aktywność <xref:System.ServiceModel.Activities.TransactedReceiveScope>do sekcji Treść . W <xref:System.Activities.Statements.Sequence> ramach działania przeciągnij i upuść dwa <xref:System.Activities.Statements.WriteLine> działania i ustaw <xref:System.Activities.Statements.WriteLine.Text%2A> właściwości, jak pokazano w poniższej tabeli.  
  
    |Działanie|Wartość|  
    |--------------|-----------|  
    |1. WriteLine|"Usługa: Odbiór zakończony"|  
    |2. WriteLine|"Usługa: Odebrane = " + requestMessage|  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Sekwencja po dodaniu działań WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. Przeciągnij i `PrintTransactionInfo` upuść <xref:System.Activities.Statements.WriteLine> aktywność po <xref:System.ServiceModel.Activities.TransactedReceiveScope> drugim działaniu w **treści** w działaniu.  
  
     ![Sekwencja po dodaniu PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. Przeciągnij i <xref:System.Activities.Statements.Assign> upuść działanie po `PrintTransactionInfo` działaniu i ustaw jej właściwości zgodnie z poniższą tabelą.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |Do|replyMessage|  
    |Wartość|"Usługa: Wysyłanie odpowiedzi".|  
  
11. Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść działanie po <xref:System.Activities.Statements.Assign> działaniu i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość na "Usługa: Rozpocznij odpowiedź".  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Po dodaniu Przypisz i WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Kliknij prawym <xref:System.ServiceModel.Activities.Receive> przyciskiem myszy działanie i wybierz polecenie **Utwórz wyślijReply** i wklej je po ostatnim <xref:System.Activities.Statements.WriteLine> działaniu. Kliknij **łącze Definiuj...** w `SendReplyToReceive` działaniu i wykonuj następujące ustawienia.  
  
     ![Ustawienia wiadomości odpowiedzi](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść działanie po `SendReplyToReceive` <xref:System.Activities.Statements.WriteLine.Text%2A> działaniu i ustaw jego właściwość na "Usługa: Odpowiedź wysłana".  
  
14. Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść działanie u dołu <xref:System.Activities.Statements.WriteLine.Text%2A> przepływu pracy i ustaw jego właściwość na "Service: Workflow ends, press ENTER to exit".  
  
     Ukończony przepływ pracy usługi powinien wyglądać następująco:  
  
     ![Ukończ przepływ pracy serwisu](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>Zaimplementowanie klienta przepływu pracy  
  
1. Dodaj nową aplikację przepływu pracy WCF, wywoływaną `WorkflowClient` `Common` do projektu. Aby to zrobić, `Common` kliknij prawym przyciskiem myszy projekt, wybierz pozycję **Dodaj**, **Nowy element ...**, Wybierz przepływ **pracy** w obszarze **Zainstalowane szablony** i wybierz **pozycję Aktywność**.  
  
     ![Dodawanie projektu działania](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. Przeciągnij i <xref:System.Activities.Statements.Sequence> upuść aktywność na powierzchnię projektową.  
  
3. W <xref:System.Activities.Statements.Sequence> obrębie działania przeciągnij i <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.WriteLine.Text%2A> upuść działanie i ustaw jego właściwość na `"Client: Workflow starting"`. Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Dodawanie działania WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. Przeciągnij i <xref:System.Activities.Statements.TransactionScope> upuść aktywność po działaniu. <xref:System.Activities.Statements.WriteLine>  Wybierz <xref:System.Activities.Statements.TransactionScope> działanie, kliknij przycisk Zmienne i dodaj następujące zmienne.  
  
     ![Dodawanie zmiennych do transactionscope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Przeciągnij i <xref:System.Activities.Statements.Sequence> upuść działanie <xref:System.Activities.Statements.TransactionScope> do treści działania.  
  
6. Przeciąganie `PrintTransactionInfo` i upuszczanie aktywności w obrębie<xref:System.Activities.Statements.Sequence>  
  
7. Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść działanie po `PrintTransactionInfo` działaniu i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość na "Klient: Początek wysyłania". Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Dodawanie klienta: rozpoczynanie wysyłania działań](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. Przeciągnij i <xref:System.ServiceModel.Activities.Send> upuść działanie po <xref:System.Activities.Statements.Assign> działaniu i ustaw następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |Nazwa konfiguracji punktu końcowego|punkt usługi przepływu pracy|  
    |OperationName|PoczątekPróby|  
    |Nazwa kontraktu servicecontract|ITransactionPróbuj|  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Ustawianie właściwości działania Wyślij](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. Kliknij **łącze Definiuj...** i wykonuj następujące ustawienia:  
  
     ![Ustawienia wiadomości o działaniu](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. Kliknij prawym <xref:System.ServiceModel.Activities.Send> przyciskiem myszy aktywność i wybierz polecenie **Utwórz receivereply**. Działanie <xref:System.ServiceModel.Activities.ReceiveReply> zostanie automatycznie umieszczone po <xref:System.ServiceModel.Activities.Send> zakończeniu działania.  
  
11. Kliknij przycisk Definiuj... łącze do działania ReceiveReplyForSend i wykonuj następujące ustawienia:  
  
     ![Ustawianie ustawień komunikatu ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść <xref:System.ServiceModel.Activities.ReceiveReply> działanie między <xref:System.Activities.Statements.WriteLine.Text%2A> <xref:System.ServiceModel.Activities.Send> i działania i ustawić jego właściwość na "Klient: Wyślij zakończone."  
  
13. Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść działanie po <xref:System.ServiceModel.Activities.ReceiveReply> działaniu i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość na "Strona klienta: Odpowiedź odebrana = " + replyMessage  
  
14. Przeciągnij i `PrintTransactionInfo` upuść aktywność po działaniu. <xref:System.Activities.Statements.WriteLine>  
  
15. Przeciągnij i <xref:System.Activities.Statements.WriteLine> upuść działanie na końcu <xref:System.Activities.Statements.WriteLine.Text%2A> przepływu pracy i ustaw jego właściwość na "Kończy się przepływ pracy klienta". Ukończony przepływ pracy klienta powinien wyglądać jak na poniższym diagramie.  
  
     ![Ukończony przepływ pracy klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Skompiluj rozwiązanie.  
  
### <a name="create-the-service-application"></a>Tworzenie aplikacji usługi  
  
1. Dodaj nowy projekt aplikacji `Service` konsoli wywoływany do rozwiązania. Dodaj odwołania do następujących zestawów:  
  
    1. Plik System.Activities.dll  
  
    2. System.ServiceModel.dll  
  
    3. Plik System.ServiceModel.Activities.dll  
  
2. Otwórz wygenerowany plik Program.cs i następujący kod:  
  
    ```csharp
          static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };
          }  
    ```  
  
3. Dodaj następujący plik app.config do projektu.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="create-the-client-application"></a>Tworzenie aplikacji klienckiej  
  
1. Dodaj nowy projekt aplikacji `Client` konsoli wywoływany do rozwiązania. Dodaj odwołanie do pliku System.Activities.dll.  
  
2. Otwórz plik program.cs i dodaj następujący kod.  
  
    ```csharp
    class Program  
    {  

        private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
        static void Main(string[] args)  
        {  
            //Build client  
            Console.WriteLine("Building the client.");  
            WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
            client.Completed = Program.Completed;  
            client.Aborted = Program.Aborted;  
            client.OnUnhandledException = Program.OnUnhandledException;  
            //Wait for service to start  
            Console.WriteLine("Press ENTER once service is started.");  
            Console.ReadLine();  
  
            //Start the client
            Console.WriteLine("Starting the client.");  
            client.Run();  
            syncEvent.WaitOne();  
  
            //Sample complete  
            Console.WriteLine();  
            Console.WriteLine("Client complete. Press ENTER to exit.");  
            Console.ReadLine();  
        }  
  
        private static void Completed(WorkflowApplicationCompletedEventArgs e)  
        {  
            Program.syncEvent.Set();  
        }  
  
        private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
        {  
            Console.WriteLine("Client Aborted: {0}", e.Reason);  
            Program.syncEvent.Set();  
        }  
  
        private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
            return UnhandledExceptionAction.Cancel;  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Omówienie transakcji WCF (Windows Communication Foundation)](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
