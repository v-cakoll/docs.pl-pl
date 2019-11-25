---
title: Przepływy transakcji do i z usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: ea14bc651258684fd31940aa6b88f9731348dcd1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978281"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Przepływy transakcji do i z usług przepływu pracy
Usługi przepływu pracy i klienci mogą uczestniczyć w transakcjach.  Aby operacja usługi była częścią otoczenia transakcji, umieść <xref:System.ServiceModel.Activities.Receive> działania w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania. Wszystkie wywołania podejmowane przez <xref:System.ServiceModel.Activities.Send> lub <xref:System.ServiceModel.Activities.SendReply> działania w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> również zostaną wykonane w obrębie transakcji otoczenia. Aplikacja kliencka przepływu pracy może utworzyć otoczenia transakcji przy użyciu działania <xref:System.Activities.Statements.TransactionScope> i operacji wywołania usługi przy użyciu transakcji otoczenia. W tym temacie omówiono tworzenie usługi przepływu pracy i klienta przepływu pracy, który uczestniczy w transakcjach.  
  
> [!WARNING]
> Jeśli wystąpienie usługi przepływu pracy jest załadowane w ramach transakcji, a przepływ pracy zawiera działanie <xref:System.Activities.Statements.Persist>, wystąpienie przepływu pracy będzie blokowane do momentu przełączenia transakcji.  
  
> [!IMPORTANT]
> Za każdym razem, gdy korzystasz z <xref:System.ServiceModel.Activities.TransactedReceiveScope>, zaleca się umieszczenie wszystkich odbiorów w przepływie pracy w <xref:System.ServiceModel.Activities.TransactedReceiveScope> działaniach.  
  
> [!IMPORTANT]
> W przypadku używania <xref:System.ServiceModel.Activities.TransactedReceiveScope> i komunikatów w niepoprawnej kolejności przepływ pracy zostanie przerwany przy próbie dostarczenia pierwszego komunikatu poza kolejnością. Musisz się upewnić, że przepływ pracy zawsze ma spójny punkt zatrzymania, gdy przepływ pracy jest bezczynny. Umożliwi to ponowne uruchomienie przepływu pracy z poprzedniego punktu trwałości, jeśli przepływ pracy zostanie przerwany.  
  
### <a name="create-a-shared-library"></a>Tworzenie biblioteki udostępnionej  
  
1. Utwórz nowe puste rozwiązanie programu Visual Studio.  
  
2. Dodaj nowy projekt biblioteki klas o nazwie `Common`. Dodaj odwołania do następujących zestawów:  
  
    - System. Activities. dll  
  
    - System.ServiceModel.dll  
  
    - System. ServiceModel. Activities. dll  
  
    - System.Transactions.dll  
  
3. Dodaj nową klasę o nazwie `PrintTransactionInfo` do projektu `Common`. Ta klasa jest pochodną <xref:System.Activities.NativeActivity> i przeciążania metody <xref:System.Activities.NativeActivity.Execute%2A>.  
  
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
  
     Jest to działanie natywne, które wyświetla informacje o otaczającej transakcji i jest używane w przepływach pracy usługi i klienta używanych w tym temacie. Skompiluj rozwiązanie, aby to działanie było dostępne w sekcji **wspólne** w **przyborniku**.  
  
### <a name="implement-the-workflow-service"></a>Implementowanie usługi przepływu pracy  
  
1. Dodaj nową usługę przepływu pracy WCF o nazwie `WorkflowService` do projektu `Common`. Aby to zrobić, kliknij projekt `Common`, wybierz pozycję **Dodaj**, **nowy element...** , wybierz pozycję **przepływ pracy** w obszarze **zainstalowane szablony** i wybierz pozycję **Usługa przepływu pracy WCF**.  
  
     ![Dodawanie usługi przepływu pracy](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Usuń domyślne działania `ReceiveRequest` i `SendResponse`.  
  
3. Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> do działania `Sequential Service`. Ustaw właściwość Text na `"Workflow Service starting ..."`, jak pokazano w poniższym przykładzie.  
  
     ! [Dodawanie działania WriteLine do działania sekwencyjnego usługi (./Media/Flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)  
  
4. Przeciągnij i upuść <xref:System.ServiceModel.Activities.TransactedReceiveScope> po działaniu <xref:System.Activities.Statements.WriteLine>. Działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> można znaleźć w sekcji **komunikaty** w **przyborniku**. Działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> składa się z dwóch sekcji jako **żądanie** i **treść**. Sekcja **żądania** zawiera działanie <xref:System.ServiceModel.Activities.Receive>. Sekcja **treść** zawiera działania, które należy wykonać w ramach transakcji po odebraniu komunikatu.  
  
     ![Dodawanie działania TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. Wybierz działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> i kliknij przycisk **zmienne** . Dodaj następujące zmienne.  
  
     ![Dodawanie zmiennych do TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > Istnieje możliwość usunięcia zmiennej danych, która jest domyślnie dostępna. Możesz również użyć istniejącej zmiennej dojścia.  
  
6. Przeciągnij i upuść działanie <xref:System.ServiceModel.Activities.Receive> w sekcji **żądanie** działania <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Ustaw następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |CanCreateInstance|True (zaznacz pole wyboru)|  
    |OperationName|StartSample|  
    |Samych ServiceContractName|ITransactionSample|  
  
     Przepływ pracy powinien wyglądać następująco:  
  
     ![Dodawanie działania Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. Kliknij link **Definiuj...** w działaniu <xref:System.ServiceModel.Activities.Receive> i wprowadź następujące ustawienia:  
  
     ![Ustawianie ustawień komunikatów dla działania Odbierz](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Przeciągnij i upuść działanie <xref:System.Activities.Statements.Sequence> w sekcji treść <xref:System.ServiceModel.Activities.TransactedReceiveScope>. W ramach działania <xref:System.Activities.Statements.Sequence> przeciągnij i upuść dwa działania <xref:System.Activities.Statements.WriteLine> i ustaw właściwości <xref:System.Activities.Statements.WriteLine.Text%2A>, jak pokazano w poniższej tabeli.  
  
    |Działanie|Wartość|  
    |--------------|-----------|  
    |1\. WriteLine|"Usługa: odbieranie ukończone"|  
    |Druga WriteLine|"Usługa: Received =" + requestMessage|  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Sekwencja po dodaniu operacji WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. Przeciągnij i upuść działanie `PrintTransactionInfo` po drugim działaniu <xref:System.Activities.Statements.WriteLine> w **treści** w działaniu <xref:System.ServiceModel.Activities.TransactedReceiveScope>.  
  
     ![Sekwencja po dodaniu PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. Przeciągnij i upuść działanie <xref:System.Activities.Statements.Assign> po działaniu `PrintTransactionInfo` i ustaw jego właściwości zgodnie z poniższą tabelą.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |Do|replyMessage|  
    |Wartość|"Usługa: wysyłanie odpowiedzi".|  
  
11. Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> po działaniu <xref:System.Activities.Statements.Assign> i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na "Service: BEGIN Reply".  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Po dodaniu elementu Assign i WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Kliknij prawym przyciskiem myszy działanie <xref:System.ServiceModel.Activities.Receive> i wybierz polecenie **Utwórz SendReply** i wklej je po ostatnim działaniu <xref:System.Activities.Statements.WriteLine>. Kliknij link **Definiuj...** w działaniu `SendReplyToReceive` i wprowadź następujące ustawienia.  
  
     ![Ustawienia komunikatu odpowiedzi](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> po działaniu `SendReplyToReceive` i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na wartość "Usługa: odpowiedź wysłana".  
  
14. Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> u dołu przepływu pracy i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na wartość "Usługa: przepływ pracy Zakończ, a następnie naciśnij klawisz ENTER, aby wyjść".  
  
     Ukończony przepływ pracy usługi powinien wyglądać następująco:  
  
     ![Pełny przepływ pracy usługi](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>Implementowanie klienta przepływu pracy  
  
1. Dodaj nową aplikację przepływu pracy WCF o nazwie `WorkflowClient` do projektu `Common`. Aby to zrobić, kliknij projekt `Common`, wybierz pozycję **Dodaj**, **nowy element...** , wybierz **pozycję przepływ pracy** w obszarze **zainstalowane szablony** i wybierz pozycję **działanie**.  
  
     ![Dodaj projekt działania](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. Przeciągnij i upuść działanie <xref:System.Activities.Statements.Sequence> na powierzchnię projektu.  
  
3. W ramach działania <xref:System.Activities.Statements.Sequence> przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na `"Client: Workflow starting"`. Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Dodawanie działania WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. Przeciągnij i upuść działanie <xref:System.Activities.Statements.TransactionScope> po działaniu <xref:System.Activities.Statements.WriteLine>.  Wybierz działanie <xref:System.Activities.Statements.TransactionScope>, kliknij przycisk zmienne, a następnie Dodaj następujące zmienne.  
  
     ![Dodaj zmienne do elementu TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Przeciągnij i upuść działanie <xref:System.Activities.Statements.Sequence> w treści <xref:System.Activities.Statements.TransactionScope> działania.  
  
6. Przeciągnij i upuść działanie `PrintTransactionInfo` w <xref:System.Activities.Statements.Sequence>  
  
7. Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> po działaniu `PrintTransactionInfo` i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na wartość "klient: Rozpoczynanie wysyłania". Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Dodawanie klienta: Rozpoczynanie wysyłania działań](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. Przeciągnij i upuść działanie <xref:System.ServiceModel.Activities.Send> po działaniu <xref:System.Activities.Statements.Assign> i ustaw następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |Samych ServiceContractName|ITransactionSample|  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Ustawianie właściwości działania wysyłania](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. Kliknij link **Definiuj...** i wprowadź następujące ustawienia:  
  
     ![Ustawienia wysyłania komunikatu dotyczącego działania](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. Kliknij prawym przyciskiem myszy działanie <xref:System.ServiceModel.Activities.Send> i wybierz pozycję **Utwórz ReceiveReply**. Działanie <xref:System.ServiceModel.Activities.ReceiveReply> zostanie automatycznie umieszczone po działaniu <xref:System.ServiceModel.Activities.Send>.  
  
11. Kliknij przycisk Definiuj... Połącz się z działaniem ReceiveReplyForSend i wprowadź następujące ustawienia:  
  
     ![Ustawianie ustawień komunikatu ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> między działaniami <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na wartość "Client: Send Complete".  
  
13. Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> po działaniu <xref:System.ServiceModel.Activities.ReceiveReply> i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na "po stronie klienta: odebrano odpowiedź =" + replyMessage  
  
14. Przeciągnij i upuść działanie `PrintTransactionInfo` po działaniu <xref:System.Activities.Statements.WriteLine>.  
  
15. Przeciągnij i upuść działanie <xref:System.Activities.Statements.WriteLine> na końcu przepływu pracy i ustaw jego właściwość <xref:System.Activities.Statements.WriteLine.Text%2A> na "zakończenie przepływu pracy klienta". Ukończony przepływ pracy klienta powinien wyglądać podobnie do poniższego diagramu.  
  
     ![Ukończony przepływ pracy klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Skompiluj rozwiązanie.  
  
### <a name="create-the-service-application"></a>Tworzenie aplikacji usługi  
  
1. Dodaj nowy projekt aplikacji konsoli o nazwie `Service` do rozwiązania. Dodaj odwołania do następujących zestawów:  
  
    1. System. Activities. dll  
  
    2. System.ServiceModel.dll  
  
    3. System. ServiceModel. Activities. dll  
  
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
  
3. Dodaj do projektu następujący plik App. config.  
  
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
  
1. Dodaj nowy projekt aplikacji konsoli o nazwie `Client` do rozwiązania. Dodaj odwołanie do elementu System. Activities. dll.  
  
2. Otwórz plik program.cs i Dodaj następujący kod.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Omówienie transakcji WCF (Windows Communication Foundation)](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
