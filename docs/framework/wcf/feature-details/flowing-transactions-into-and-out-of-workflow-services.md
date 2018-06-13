---
title: Przepływy transakcji do i z usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: 8b3d3e85b626d033c9ab50e93e3ceb3b86058a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496100"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Przepływy transakcji do i z usług przepływu pracy
Usługi przepływu pracy i klienci mogą uczestniczyć w transakcji.  Dla operacji usługi stać się częścią transakcja otoczenia, umieść <xref:System.ServiceModel.Activities.Receive> działania w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania. Wywołań przez <xref:System.ServiceModel.Activities.Send> lub <xref:System.ServiceModel.Activities.SendReply> działania w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> również zostaną wprowadzone w ramach transakcja otoczenia. Aplikacja kliencka przepływu pracy można utworzyć transakcja otoczenia przy użyciu <xref:System.Activities.Statements.TransactionScope> działania i wywołania operacji usługi przy użyciu transakcja otoczenia. W tym temacie przedstawiono tworzenie usługi przepływu pracy i klienta przepływu pracy, który uczestniczyć w transakcji.  
  
> [!WARNING]
>  Jeśli wystąpienie usługi przepływu pracy jest ładowany w ramach transakcji i przepływ pracy zawiera <xref:System.Activities.Statements.Persist> działania wystąpienia przepływu pracy zawiesza się dopóki nie upłynie limit czasu transakcji.  
  
> [!IMPORTANT]
>  Zawsze, gdy używana <xref:System.ServiceModel.Activities.TransactedReceiveScope> zaleca się umieścić wszystkie działania Receive w przepływie pracy w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> działań.  
  
> [!IMPORTANT]
>  Korzystając z <xref:System.ServiceModel.Activities.TransactedReceiveScope> i nadchodzą komunikaty w niepoprawna kolejność, przepływ pracy zostanie przerwany podczas próby dostarczenia pierwszego komunikatu poza kolejnością. Należy się upewnić, że przepływ pracy jest zawsze na spójną punktu zatrzymania podczas idles przepływu pracy. Umożliwi to ponowne uruchomienie przepływu pracy od poprzedniego punktu trwałości powinien przerwanie przepływu pracy.  
  
### <a name="create-a-shared-library"></a>Tworzenie biblioteki udostępnionej  
  
1.  Utwórz nowe puste rozwiązanie Visual Studio.  
  
2.  Dodawanie nowego projektu biblioteki klas o nazwie `Common`. Dodaj odwołania do następujących zestawów:  
  
    -   System.Activities.dll  
  
    -   System.ServiceModel.dll  
  
    -   System.ServiceModel.Activities.dll  
  
    -   System.Transactions.dll  
  
3.  Dodaj nową klasę o nazwie `PrintTransactionInfo` do `Common` projektu. Ta klasa pochodzi od <xref:System.Activities.NativeActivity> i overloads <xref:System.Activities.NativeActivity.Execute%2A> metody.  
  
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
  
     Jest to działania natywnego, która wyświetla informacje o transakcja otoczenia i jest używany w przepływach pracy usługa i klient używane w tym temacie. Skompiluj rozwiązanie, aby udostępnić to działanie w **typowe** sekcji **przybornika**.  
  
### <a name="implement-the-workflow-service"></a>Wdrożenie usługi przepływu pracy  
  
1.  Dodaj nową usługę przepływu pracy WCF, nazywany `WorkflowService` do `Common` projektu. Aby zrobić to kliknij prawym przyciskiem myszy `Common` projektu, zaznacz **Dodaj**, **nowy element...** , Wybierz pozycję **przepływu pracy** w obszarze **zainstalowane szablony** i wybierz **usługi przepływu pracy WCF**.  
  
     ![Dodawanie usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/media/addwfservice.JPG "AddWFService")  
  
2.  Usunąć domyślną `ReceiveRequest` i `SendResponse` działań.  
  
3.  Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działania do `Sequential Service` działania. Wartość właściwości text `"Workflow Service starting ..."` jak pokazano w poniższym przykładzie.  
  
     ![Dodawanie działania WriteLine](../../../../docs/framework/wcf/feature-details/media/addwriteline.JPG "AddWriteLine")  
  
4.  Przeciągnij i upuść <xref:System.ServiceModel.Activities.TransactedReceiveScope> po <xref:System.Activities.Statements.WriteLine> działania. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Działania można znaleźć w **wiadomości** sekcji **przybornika**. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Działania składa się z dwóch części **żądania** i **treści**. **Żądania** sekcja zawiera <xref:System.ServiceModel.Activities.Receive> działania. **Treści** sekcja zawiera działania, które można wykonać w ramach transakcji po otrzymaniu komunikatu.  
  
     ![Dodawanie działania TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trs.JPG "TR, Technical Router")  
  
5.  Wybierz <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania i kliknij przycisk **zmienne** przycisku. Dodaj następujące zmienne.  
  
     ![Dodawanie zmiennych do TransactedReceiveScope](../../../../docs/framework/wcf/feature-details/media/trsvariables.JPG "TRSVariables")  
  
    > [!NOTE]
    >  Można usunąć zmiennej danych, która jest domyślnie. Umożliwia także istniejącą zmienną dojścia.  
  
6.  Przeciągnij i upuść <xref:System.ServiceModel.Activities.Receive> działania w ramach **żądania** sekcji <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania. Ustaw następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |CanCreateInstance|Wartość true (zaznacz pole wyboru)|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     Przepływ pracy powinien wyglądać następująco:  
  
     ![Dodawanie działania Receive](../../../../docs/framework/wcf/feature-details/media/serviceaddreceive.JPG "ServiceAddReceive")  
  
7.  Kliknij przycisk **zdefiniuj...**  łącze w <xref:System.ServiceModel.Activities.Receive> działania i wprowadź następujące ustawienia:  
  
     ![Konfigurowanie ustawień wiadomości dla działania Odbierz](../../../../docs/framework/wcf/feature-details/media/receivemessagesettings.JPG "ReceiveMessageSettings")  
  
8.  Przeciągnij i upuść <xref:System.Activities.Statements.Sequence> działania w sekcji Body <xref:System.ServiceModel.Activities.TransactedReceiveScope>. W ramach <xref:System.Activities.Statements.Sequence> działania przeciągnij i upuść dwa <xref:System.Activities.Statements.WriteLine> działań i zestaw <xref:System.Activities.Statements.WriteLine.Text%2A> właściwości, jak pokazano w poniższej tabeli.  
  
    |Działanie|Wartość|  
    |--------------|-----------|  
    |WriteLine 1.|"Usługa: odbieranie ukończone"|  
    |WriteLine 2|"Usługa: odebrano =" + requestMessage|  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Dodawanie działań WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingwritelines.JPG "AfterAddingWriteLines")  
  
9. Przeciągnij i upuść `PrintTransactionInfo` działanie po drugim <xref:System.Activities.Statements.WriteLine> działania w **treści** w <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania.  
  
     ![Po dodaniu PrintTransactionInfo](../../../../docs/framework/wcf/feature-details/media/afteraddingprinttransactioninfo.JPG "AfterAddingPrintTransactionInfo")  
  
10. Przeciągnij i upuść <xref:System.Activities.Statements.Assign> działanie po `PrintTransactionInfo` działania i ustawienia swoich właściwości zgodnie z poniższą tabelą.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |Do|replyMessage|  
    |Wartość|"Usługa: wysyłania odpowiedzi."|  
  
11. Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie po <xref:System.Activities.Statements.Assign> działania i zestaw jej <xref:System.Activities.Statements.WriteLine.Text%2A> dla właściwości "usługi: rozpocząć odpowiedzi."  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Po dodaniu przypisania i WriteLine](../../../../docs/framework/wcf/feature-details/media/afteraddingsbrwriteline.JPG "AfterAddingSBRWriteLine")  
  
12. Kliknij prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Receive> działanie i wybierz **utworzyć SendReply** i wklej go po ostatniej <xref:System.Activities.Statements.WriteLine> działania. Kliknij przycisk **zdefiniuj...**  łącze w `SendReplyToReceive` działania i wprowadź następujące ustawienia.  
  
     ![Ustawienia wiadomości odpowiedzi](../../../../docs/framework/wcf/feature-details/media/replymessagesettings.JPG "ReplyMessageSettings")  
  
13. Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie po `SendReplyToReceive` działania i zestaw składa się z <xref:System.Activities.Statements.WriteLine.Text%2A> dla właściwości "Usługa: Wysłano odpowiedź."  
  
14. Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działania w dolnej części przepływu pracy i zestaw jej <xref:System.Activities.Statements.WriteLine.Text%2A> dla właściwości "usługi: kończy się przepływu pracy, naciśnij klawisz ENTER, aby wyjść."  
  
     Ukończono usługi przepływu pracy powinna wyglądać następująco:  
  
     ![Ukończ przepływ pracy usługi](../../../../docs/framework/wcf/feature-details/media/servicecomplete.jpg "ServiceComplete")  
  
### <a name="implement-the-workflow-client"></a>Wdrożenie klienta przepływu pracy  
  
1.  Dodaj nową aplikację przepływu pracy WCF, o nazwie `WorkflowClient` do `Common` projektu. Aby zrobić to kliknij prawym przyciskiem myszy `Common` projektu, zaznacz **Dodaj**, **nowy element...** , Wybierz pozycję **przepływu pracy** w obszarze **zainstalowane szablony** i wybierz **działania**.  
  
     ![Dodaj projekt działania](../../../../docs/framework/wcf/feature-details/media/addactivity.JPG "AddActivity")  
  
2.  Przeciągnij i upuść <xref:System.Activities.Statements.Sequence> działania na powierzchnię projektu.  
  
3.  W ramach <xref:System.Activities.Statements.Sequence> działania przeciąganie i upuszczanie <xref:System.Activities.Statements.WriteLine> działania i zestaw jej <xref:System.Activities.Statements.WriteLine.Text%2A> właściwości `"Client: Workflow starting"`. Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Dodaj działanie WriteLine](../../../../docs/framework/wcf/feature-details/media/clientaddwriteline.JPG "ClientAddWriteLine")  
  
4.  Przeciągnij i upuść <xref:System.Activities.Statements.TransactionScope> działanie po <xref:System.Activities.Statements.WriteLine> działania.  Wybierz <xref:System.Activities.Statements.TransactionScope> działania, kliknij przycisk Zmienne i dodaj następujące zmienne.  
  
     ![Zmienne można dodawać do elementu TransactionScope](../../../../docs/framework/wcf/feature-details/media/tsvariables.JPG "TSVariables")  
  
5.  Przeciągnij i upuść <xref:System.Activities.Statements.Sequence> działania w treści <xref:System.Activities.Statements.TransactionScope> działania.  
  
6.  Przeciągnij i upuść `PrintTransactionInfo` działanie w <xref:System.Activities.Statements.Sequence>  
  
7.  Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie po `PrintTransactionInfo` działania i zestaw jej <xref:System.Activities.Statements.WriteLine.Text%2A> "Klienta: początku wysyłania" dla właściwości. Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Dodawanie działań](../../../../docs/framework/wcf/feature-details/media/clientaddcbswriteline.JPG "ClientAddCBSWriteLine")  
  
8.  Przeciągnij i upuść <xref:System.ServiceModel.Activities.Send> działanie po <xref:System.Activities.Statements.Assign> działania i ustaw następujące właściwości:  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     Przepływ pracy powinien teraz wyglądać następująco:  
  
     ![Ustawianie właściwości działania Send](../../../../docs/framework/wcf/feature-details/media/clientsendsettings.JPG "ClientSendSettings")  
  
9. Kliknij przycisk **zdefiniuj...**  łącze i wprowadź następujące ustawienia:  
  
     ![Wyślij działania ustawienia wiadomości](../../../../docs/framework/wcf/feature-details/media/sendmessagesettings.JPG "SendMessageSettings")  
  
10. Kliknij prawym przyciskiem myszy <xref:System.ServiceModel.Activities.Send> działanie i wybierz **utworzyć ReceiveReply**. <xref:System.ServiceModel.Activities.ReceiveReply> Działania zostaną automatycznie umieszczone po <xref:System.ServiceModel.Activities.Send> działania.  
  
11. Kliknij przycisk Definiuj... link w działaniu ReceiveReplyForSend i wprowadź następujące ustawienia:  
  
     ![Konfigurowanie ustawień wiadomości ReceiveForSend](../../../../docs/framework/wcf/feature-details/media/clientreplymessagesettings.JPG "ClientReplyMessageSettings")  
  
12. Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działania między <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań i zestaw jej <xref:System.Activities.Statements.WriteLine.Text%2A> dla właściwości "klienta: wysyłanie pełną."  
  
13. Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działanie po <xref:System.ServiceModel.Activities.ReceiveReply> działania i zestaw jej <xref:System.Activities.Statements.WriteLine.Text%2A> dla właściwości "po stronie klienta: odebrano odpowiedzi =" + replyMessage  
  
14. Przeciągnij i upuść `PrintTransactionInfo` działanie po <xref:System.Activities.Statements.WriteLine> działania.  
  
15. Przeciągnij i upuść <xref:System.Activities.Statements.WriteLine> działania na końcu przepływu pracy i zestaw jej <xref:System.Activities.Statements.WriteLine.Text%2A> dla właściwości "Kończy się przepływu pracy klienta". Przepływ pracy ukończonych klienta powinien wyglądać w poniższym diagramie.  
  
     ![Workfliow klienta zakończonych](../../../../docs/framework/wcf/feature-details/media/clientcompleteworkflow.jpg "ClientCompleteWorkflow")  
  
16. Skompiluj rozwiązanie.  
  
### <a name="create-the-service-application"></a>Tworzenie aplikacji usługi  
  
1.  Dodaj nowy projekt aplikacji konsoli o nazwie `Service` do rozwiązania. Dodaj odwołania do następujących zestawów:  
  
    1.  System.Activities.dll  
  
    2.  System.ServiceModel.dll  
  
    3.  System.ServiceModel.Activities.dll  
  
2.  Otwórz wygenerowany plik Program.cs i następujący kod:  
  
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
  
3.  Dodaj następujący plik app.config do projektu.  
  
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
  
### <a name="create-the-client-application"></a>Tworzenie aplikacji klienckich  
  
1.  Dodaj nowy projekt aplikacji konsoli o nazwie `Client` do rozwiązania. Dodaj odwołanie do System.Activities.dll.  
  
2.  Otwórz plik program.cs i Dodaj następujący kod.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Omówienie transakcji WCF (Windows Communication Foundation)](../../../../docs/framework/wcf/feature-details/transactions-overview.md)  
 [Używanie elementu TransactedReceiveScope](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)
