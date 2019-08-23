---
title: Przepływy transakcji do i z usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: 7926c5a8ce1ca1ba3e24c4d1681ae12c18039924
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963340"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Przepływy transakcji do i z usług przepływu pracy
Usługi przepływu pracy i klienci mogą uczestniczyć w transakcjach.  Aby operacja usługi stała się częścią otoczenia transakcji, umieść <xref:System.ServiceModel.Activities.Receive> działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> w ramach działania. Wszystkie wywołania wykonane przez <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> lub działania w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> programu zostaną również wykonane w obrębie transakcji otoczenia. Aplikacja kliencka przepływu pracy może utworzyć otoczenia transakcji przy użyciu <xref:System.Activities.Statements.TransactionScope> operacji działania i wywołania usługi przy użyciu transakcji otoczenia. W tym temacie omówiono tworzenie usługi przepływu pracy i klienta przepływu pracy, który uczestniczy w transakcjach.  
  
> [!WARNING]
>  Jeśli wystąpienie usługi przepływu pracy jest załadowane w ramach transakcji, a przepływ pracy <xref:System.Activities.Statements.Persist> zawiera działanie, wystąpienie przepływu pracy zostanie zablokowane do momentu przełączenia transakcji.  
  
> [!IMPORTANT]
> Za każdym razem, <xref:System.ServiceModel.Activities.TransactedReceiveScope> gdy jest używany, zaleca się umieszczenie wszystkich odbiorów w <xref:System.ServiceModel.Activities.TransactedReceiveScope> przepływie pracy w ramach działań.  
  
> [!IMPORTANT]
> Gdy użycie <xref:System.ServiceModel.Activities.TransactedReceiveScope> i komunikaty docierają w niepoprawnej kolejności, przepływ pracy zostanie przerwany przy próbie dostarczenia pierwszego komunikatu poza kolejnością. Musisz się upewnić, że przepływ pracy zawsze ma spójny punkt zatrzymania, gdy przepływ pracy jest bezczynny. Umożliwi to ponowne uruchomienie przepływu pracy z poprzedniego punktu trwałości, jeśli przepływ pracy zostanie przerwany.  
  
### <a name="create-a-shared-library"></a>Tworzenie biblioteki udostępnionej  
  
1. Utwórz nowe puste rozwiązanie programu Visual Studio.  
  
2. Dodaj nowy projekt biblioteki klas o nazwie `Common`. Dodaj odwołania do następujących zestawów:  
  
    - System.Activities.dll  
  
    - System.ServiceModel.dll  
  
    - System.ServiceModel.Activities.dll  
  
    - System.Transactions.dll  
  
3. Dodaj nową klasę o nazwie `PrintTransactionInfo` `Common` do projektu. Ta klasa jest pochodną <xref:System.Activities.NativeActivity> i <xref:System.Activities.NativeActivity.Execute%2A> przeciążania metody.  
  
    ```  
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
  
     Jest to działanie natywne, które wyświetla informacje o otaczającej transakcji i jest używane w przepływach pracy usługi i klienta używanych w tym temacie. Skompiluj rozwiązanie, aby to działanie było dostępne w sekcji **wspólne** w przyborniku.  
  
### <a name="implement-the-workflow-service"></a>Implementowanie usługi przepływu pracy  
  
1. Dodaj nową usługę przepływu pracy WCF, `WorkflowService` `Common` która jest wywoływana do projektu. `Common` Aby to zrobić, kliknij projekt, wybierz pozycję **Dodaj**, **nowy element...** , wybierz pozycję **przepływ pracy** w obszarze **zainstalowane szablony** i wybierz pozycję **Usługa przepływu pracy WCF**.  
  
     ![Dodawanie usługi przepływu pracy](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Usuń ustawienia domyślne `ReceiveRequest` i `SendResponse` działania.  
  
3. Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie `Sequential Service` do działania. Ustaw właściwość Text na `"Workflow Service starting ..."` tak, jak pokazano w poniższym przykładzie.  
  
     ! [Dodawanie działania WriteLine do działania sekwencyjnego usługi (./Media/Flowing-Transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-Service.jpg)  
  
4. Przeciągnij i upuść <xref:System.ServiceModel.Activities.TransactedReceiveScope> <xref:System.Activities.Statements.WriteLine> po działaniu. Działanie można znaleźć w sekcji **komunikaty** w przyborniku. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Działanie składa się z dwóch sekcji **żądania** i **treści.** <xref:System.ServiceModel.Activities.TransactedReceiveScope> Sekcja **żądania** zawiera <xref:System.ServiceModel.Activities.Receive> działanie. Sekcja **treść** zawiera działania, które należy wykonać w ramach transakcji po odebraniu komunikatu.  
  
     ![Dodawanie działania TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. Wybierz działanie, a następnie kliknij przycisk **zmienne.** <xref:System.ServiceModel.Activities.TransactedReceiveScope> Dodaj następujące zmienne.  
  
     ![Dodawanie zmiennych do TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > Istnieje możliwość usunięcia zmiennej danych, która jest domyślnie dostępna. Możesz również użyć istniejącej zmiennej dojścia.  
  
6. Przeciągnij i upuść <xref:System.ServiceModel.Activities.Receive> działanie w sekcji <xref:System.ServiceModel.Activities.TransactedReceiveScope> **żądanie** działania. Ustaw następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |CanCreateInstance|True (zaznacz pole wyboru)|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     Przepływ pracy powinien wyglądać następująco:  
  
     ![Dodawanie działania Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. Kliknij link **Definiuj...** w <xref:System.ServiceModel.Activities.Receive> działaniu i wprowadź następujące ustawienia:  
  
     ![Ustawianie ustawień komunikatów dla działania Odbierz](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Przeciągnij i upuść <xref:System.Activities.Statements.Sequence> działanie do sekcji <xref:System.ServiceModel.Activities.TransactedReceiveScope>treść. W ramach <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.WriteLine.Text%2A> działania przeciągnij i upuść dwa działania, a następnie ustaw właściwości, jak pokazano w poniższej tabeli. <xref:System.Activities.Statements.Sequence>  
  
    |Działanie|Wartość|  
    |--------------|-----------|  
    |1\. WriteLine|Usługi Ukończono odbieranie "|  
    |Druga WriteLine|Usługi Odebrano = "+ requestMessage|  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Sekwencja po dodaniu operacji WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. Przeciągnij `PrintTransactionInfo` i upuść działanie po <xref:System.Activities.Statements.WriteLine> drugim działaniu <xref:System.ServiceModel.Activities.TransactedReceiveScope> w **treści** działania.  
  
     ![Sekwencja po dodaniu PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. Przeciągnij i upuść <xref:System.Activities.Statements.Assign> działanie `PrintTransactionInfo` po działaniu i ustaw jego właściwości zgodnie z poniższą tabelą.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |Zadanie|replyMessage|  
    |Wartość|Usługi Wysyłanie odpowiedzi ".|  
  
11. Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie <xref:System.Activities.Statements.Assign> po działaniu i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość na wartość "Usługa: Rozpocznij odpowiedź ".  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Po dodaniu elementu Assign i WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Kliknij prawym przyciskiem <xref:System.ServiceModel.Activities.Receive> myszy działanie i wybierz polecenie **Utwórz SendReply** i wklej je <xref:System.Activities.Statements.WriteLine> po ostatnim działaniu. Kliknij link **Definiuj...** w `SendReplyToReceive` działaniu, a następnie wprowadź następujące ustawienia.  
  
     ![Ustawienia komunikatu odpowiedzi](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie `SendReplyToReceive` po <xref:System.Activities.Statements.WriteLine.Text%2A> działaniu i ustaw jego właściwość na wartość "Usługa: Wysłano odpowiedź ".  
  
14. Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie u dołu przepływu pracy i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość na wartość "Usługa: Przepływ pracy zakończy się, naciśnij klawisz ENTER, aby zakończyć.  
  
     Ukończony przepływ pracy usługi powinien wyglądać następująco:  
  
     ![Pełny przepływ pracy usługi](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>Implementowanie klienta przepływu pracy  
  
1. Dodaj nową aplikację przepływu pracy WCF, `WorkflowClient` `Common` która jest wywoływana do projektu. Aby `Common` to zrobić, kliknij projekt, wybierz pozycję **Dodaj**, **nowy element...** , wybierz pozycję **przepływ pracy** w obszarze **zainstalowane szablony** i wybierz pozycję **działanie**.  
  
     ![Dodaj projekt działania](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. Przeciągnij i upuść <xref:System.Activities.Statements.Sequence> działanie na powierzchnię projektu.  
  
3. W ramach <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.WriteLine.Text%2A> działania przeciągnij i upuść działanie i ustaw jego właściwość na `"Client: Workflow starting"`. <xref:System.Activities.Statements.Sequence> Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Dodawanie działania WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. Przeciągnij i upuść <xref:System.Activities.Statements.TransactionScope> działanie <xref:System.Activities.Statements.WriteLine> po działaniu.  <xref:System.Activities.Statements.TransactionScope> Wybierz działanie, kliknij przycisk zmienne i Dodaj następujące zmienne.  
  
     ![Dodaj zmienne do elementu TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Przeciągnij i upuść <xref:System.Activities.Statements.Sequence> działanie do treści <xref:System.Activities.Statements.TransactionScope> działania.  
  
6. Przeciągnij i upuść `PrintTransactionInfo` działanie w ramach<xref:System.Activities.Statements.Sequence>  
  
7. Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie `PrintTransactionInfo` po działaniu i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość na "Client: Rozpoczynanie wysyłania ". Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Dodawanie klienta: Rozpoczynanie wysyłania działań](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. Przeciągnij i upuść <xref:System.ServiceModel.Activities.Send> działanie <xref:System.Activities.Statements.Assign> po działaniu i ustaw następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Ustawianie właściwości działania wysyłania](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. Kliknij link **Definiuj...** i wprowadź następujące ustawienia:  
  
     ![Ustawienia wysyłania komunikatu dotyczącego działania](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. Kliknij prawym przyciskiem <xref:System.ServiceModel.Activities.Send> myszy działanie i wybierz pozycję **Utwórz ReceiveReply**. Działanie zostanie automatycznie umieszczone <xref:System.ServiceModel.Activities.Send> po działaniu. <xref:System.ServiceModel.Activities.ReceiveReply>  
  
11. Kliknij przycisk Definiuj... Połącz się z działaniem ReceiveReplyForSend i wprowadź następujące ustawienia:  
  
     ![Ustawianie ustawień komunikatu ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie <xref:System.ServiceModel.Activities.Send> między <xref:System.ServiceModel.Activities.ReceiveReply> działaniami i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość na wartość "klient: Wyślij ukończone. "  
  
13. Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie <xref:System.ServiceModel.Activities.ReceiveReply> po działaniu i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość na "po stronie klienta: Odebrano odpowiedź = "+ replyMessage  
  
14. Przeciągnij i upuść `PrintTransactionInfo` działanie <xref:System.Activities.Statements.WriteLine> po działaniu.  
  
15. Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie na końcu przepływu pracy i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość na "zakończenie przepływu pracy klienta". Ukończony przepływ pracy klienta powinien wyglądać podobnie do poniższego diagramu.  
  
     ![Ukończony przepływ pracy klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Skompiluj rozwiązanie.  
  
### <a name="create-the-service-application"></a>Tworzenie aplikacji usługi  
  
1. Dodaj nowy projekt aplikacji konsoli o nazwie `Service` do rozwiązania. Dodaj odwołania do następujących zestawów:  
  
    1. System.Activities.dll  
  
    2. System.ServiceModel.dll  
  
    3. System.ServiceModel.Activities.dll  
  
2. Otwórz wygenerowany plik Program.cs i następujący kod:  
  
    ```  
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
  
    ```  
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
