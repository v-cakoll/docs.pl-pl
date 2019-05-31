---
title: Przepływy transakcji do i z usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: 2a837e446ec65caa6d481d3a5f141f87fe509910
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421906"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Przepływy transakcji do i z usług przepływu pracy
Usługi przepływu pracy i klienci mogą uczestniczyć w transakcji.  Dla operacji usługowej, które staną się częścią otoczenia transakcji, należy umieścić <xref:System.ServiceModel.Activities.Receive> działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania. Wywołania przez <xref:System.ServiceModel.Activities.Send> lub <xref:System.ServiceModel.Activities.SendReply> działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> również zostaną wprowadzone w ramach transakcji otoczenia. Aplikacja kliencka przepływu pracy można utworzyć otoczenia transakcji przy użyciu <xref:System.Activities.Statements.TransactionScope> działania i wywoływać operacje usługi, za pomocą otoczenia transakcji. Ten temat przeprowadzi Cię przez tworzenie usługi przepływu pracy i klienta przepływu pracy, który uczestniczyć w transakcji.  
  
> [!WARNING]
>  Jeśli wystąpienie usługi przepływu pracy jest ładowany w obrębie transakcji i przepływ pracy zawiera <xref:System.Activities.Statements.Persist> działania spowoduje zablokowanie wystąpienia przepływu pracy, dopóki nie upłynie limit czasu transakcji.  
  
> [!IMPORTANT]
>  Zawsze, gdy używasz <xref:System.ServiceModel.Activities.TransactedReceiveScope> zalecane jest umieszczenie wszystkich odbiera w przepływie pracy w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> działań.  
  
> [!IMPORTANT]
>  Korzystając z <xref:System.ServiceModel.Activities.TransactedReceiveScope> i dociera nieprawidłowa kolejność, przepływ pracy zostanie przerwany podczas próby dostarczenia pierwszego komunikatu poza kolejnością. Upewnij się, że przepływ pracy jest zawsze w spójny punktu zatrzymania podczas idles przepływu pracy. Pozwoli to ponowne uruchomienie przepływu pracy od poprzedniego punktu trwałości powinien przerwanie przepływu pracy.  
  
### <a name="create-a-shared-library"></a>Tworzenie biblioteki udostępnionej  
  
1. Utwórz nowe puste rozwiązanie Visual Studio.  
  
2. Dodaj nowy projekt biblioteki klas o nazwie `Common`. Dodaj odwołania do następujących zestawów:  
  
    - System.Activities.dll  
  
    - System.ServiceModel.dll  
  
    - System.ServiceModel.Activities.dll  
  
    - System.Transactions.dll  
  
3. Dodaj nową klasę o nazwie `PrintTransactionInfo` do `Common` projektu. Ta klasa jest pochodną <xref:System.Activities.NativeActivity> i przeciążenia <xref:System.Activities.NativeActivity.Execute%2A> metody.  
  
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
  
     Jest to działania natywnego, wyświetla informacje o otoczenia transakcji, która jest używana w przepływach pracy usługa i klient używaną w tym temacie. Kompiluj rozwiązanie, aby udostępnić to działanie w **typowe** części **przybornika**.  
  
### <a name="implement-the-workflow-service"></a>Implementowanie usługi przepływu pracy  
  
1. Dodaj nową usługę przepływu pracy WCF, o nazwie `WorkflowService` do `Common` projektu. Aby zrobić to kliknij prawym przyciskiem myszy `Common` projektu, wybierz opcję **Dodaj**, **nowy element...** , Wybierz opcję **przepływu pracy** w obszarze **zainstalowane szablony** i wybierz **usługi przepływu pracy WCF**.  
  
     ![Dodawanie usługi przepływu pracy](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Usuń domyślną `ReceiveRequest` i `SendResponse` działań.  
  
3. Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie do `Sequential Service` działania. Ustawienie właściwości text `"Workflow Service starting ..."` jak pokazano w poniższym przykładzie.  
  
     ! [Dodawanie działań WriteLine activity(./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-sequential-service.jpg) usługa Sekwencyjna  
  
4. Przeciąganie i upuszczanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> po <xref:System.Activities.Statements.WriteLine> działania. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Działania można znaleźć w **komunikatów** części **przybornika**. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Działania składa się z dwóch części **żądania** i **treści**. **Żądania** sekcja zawiera <xref:System.ServiceModel.Activities.Receive> działania. **Treści** sekcja zawiera czynności do wykonania w ramach transakcji po otrzymaniu komunikatu.  
  
     ![Dodawanie działania elementu TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. Wybierz <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania i kliknij przycisk **zmienne** przycisku. Dodaj następujące zmienne.  
  
     ![Dodawanie zmiennych do TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    >  Można usunąć zmiennej danych, która jest domyślnie. Można również użyć istniejącą zmienną dojście.  
  
6. Przeciąganie i upuszczanie <xref:System.ServiceModel.Activities.Receive> działania w ramach **żądania** części <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania. Ustaw następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |CanCreateInstance|Wartość true (zaznacz pole wyboru)|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     Przepływ pracy powinien wyglądać następująco:  
  
     ![Dodawanie działania odbierania](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. Kliknij przycisk **zdefiniować...**  łącze w <xref:System.ServiceModel.Activities.Receive> działania i wprowadź następujące ustawienia:  
  
     ![Konfigurowanie ustawień wiadomości działania odbierania](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Przeciąganie i upuszczanie <xref:System.Activities.Statements.Sequence> działanie do sekcji Body <xref:System.ServiceModel.Activities.TransactedReceiveScope>. W ramach <xref:System.Activities.Statements.Sequence> działanie przeciągnij i upuść dwa <xref:System.Activities.Statements.WriteLine> działań i zestaw <xref:System.Activities.Statements.WriteLine.Text%2A> właściwości, jak pokazano w poniższej tabeli.  
  
    |Działanie|Wartość|  
    |--------------|-----------|  
    |WriteLine 1.|"Usługa: Otrzymywać ukończone"|  
    |WriteLine 2|"Usługa: Odebrano = "+ requestMessage|  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Sekwencja po dodaniu działania WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. Przeciąganie i upuszczanie `PrintTransactionInfo` działanie po drugim <xref:System.Activities.Statements.WriteLine> działania w **treści** w <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.  
  
     ![Sekwencja po dodaniu PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. Przeciąganie i upuszczanie <xref:System.Activities.Statements.Assign> działanie po `PrintTransactionInfo` działania i ustaw jego właściwości, zgodnie z poniższą tabelą.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |Zadanie|replyMessage|  
    |Wartość|"Usługa: Wysyłanie odpowiedzi."|  
  
11. Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie po <xref:System.Activities.Statements.Assign> działania i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "usługi: Rozpocznij odpowiedzi."  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Po dodaniu Przypisywanie i WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Kliknij prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Receive> działania, a następnie wybierz pozycję **tworzenie SendReply** i wkleić go po ostatnim <xref:System.Activities.Statements.WriteLine> działania. Kliknij przycisk **zdefiniować...**  łącze w `SendReplyToReceive` działania i wprowadź następujące ustawienia.  
  
     ![Ustawienia wiadomości odpowiedzi](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie po `SendReplyToReceive` działanie i zestaw ma <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "usługi: Odpowiedź wysłana".  
  
14. Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działania w dolnej części przepływu pracy i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "Service: Przepływ pracy zostaje zakończona, naciśnij klawisz ENTER, aby zakończyć pracę."  
  
     Przepływu pracy zakończonych usługi powinien wyglądać następująco:  
  
     ![Ukończ przepływ pracy usługi](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>Implementowanie klienta przepływu pracy  
  
1. Dodaj nową aplikację przepływu pracy WCF o nazwie `WorkflowClient` do `Common` projektu. Aby zrobić to kliknij prawym przyciskiem myszy `Common` projektu, wybierz opcję **Dodaj**, **nowy element...** , Wybierz opcję **przepływu pracy** w obszarze **zainstalowane szablony** i wybierz **działania**.  
  
     ![Dodaj projekt działania](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. Przeciąganie i upuszczanie <xref:System.Activities.Statements.Sequence> działania na powierzchnię projektu.  
  
3. W ramach <xref:System.Activities.Statements.Sequence> działania przeciągania i upuszczania <xref:System.Activities.Statements.WriteLine> działania i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość `"Client: Workflow starting"`. Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Dodaj działanie WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. Przeciąganie i upuszczanie <xref:System.Activities.Statements.TransactionScope> działanie po <xref:System.Activities.Statements.WriteLine> działania.  Wybierz <xref:System.Activities.Statements.TransactionScope> działania, kliknij przycisk Zmienne i dodaj następujące zmienne.  
  
     ![Dodaj zmienne do elementu TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Przeciąganie i upuszczanie <xref:System.Activities.Statements.Sequence> działania w treści <xref:System.Activities.Statements.TransactionScope> działania.  
  
6. Przeciąganie i upuszczanie `PrintTransactionInfo` działanie <xref:System.Activities.Statements.Sequence>  
  
7. Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie po `PrintTransactionInfo` działania i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "klienta: Rozpoczynanie wysyłania". Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Dodawanie klienta: Począwszy od działań wysyłania](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. Przeciąganie i upuszczanie <xref:System.ServiceModel.Activities.Send> działanie po <xref:System.Activities.Statements.Assign> działania i ustaw następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Ustawianie właściwości działań wysyłania](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. Kliknij przycisk **zdefiniować...**  połączyć, a następnie wprowadź następujące ustawienia:  
  
     ![Wysyłanie działania ustawienia wiadomości](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. Kliknij prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Send> działania, a następnie wybierz pozycję **tworzenie ReceiveReply**. <xref:System.ServiceModel.Activities.ReceiveReply> Działania zostaną automatycznie umieszczone po <xref:System.ServiceModel.Activities.Send> działania.  
  
11. Kliknij przycisk Definiuj... link działanie ReceiveReplyForSend i wprowadź następujące ustawienia:  
  
     ![Konfigurowanie ustawień wiadomości ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działania między <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "klienta: Wyślij pełne."  
  
13. Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działanie po <xref:System.ServiceModel.Activities.ReceiveReply> działania i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "po stronie klienta: Otrzymana odpowiedź = "+ replyMessage  
  
14. Przeciąganie i upuszczanie `PrintTransactionInfo` działanie po <xref:System.Activities.Statements.WriteLine> działania.  
  
15. Przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działania na końcu przepływu pracy i ustaw jego <xref:System.Activities.Statements.WriteLine.Text%2A> właściwość "Kończy się przepływu pracy klienta". Przepływ pracy ukończonej klienta powinien wyglądać jak poniższy diagram.  
  
     ![Przepływ pracy ukończonej klienta](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
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
  
1. Dodaj nowy projekt aplikacji konsoli o nazwie `Client` do rozwiązania. Dodaj odwołanie do System.Activities.dll.  
  
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
