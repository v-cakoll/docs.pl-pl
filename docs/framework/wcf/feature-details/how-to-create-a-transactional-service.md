---
title: 'Instrukcje: tworzenie usługi transakcyjnej'
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: 7f7f060db5a4ffd66524e220e3e3291debd8a3fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769661"
---
# <a name="how-to-create-a-transactional-service"></a>Instrukcje: tworzenie usługi transakcyjnej
Niniejszy przykład pokazuje różne aspekty Tworzenie usługi transakcyjnej i użycie transakcji zainicjowanych przez klienta do koordynowania operacji usługi.  
  
### <a name="creating-a-transactional-service"></a>Tworzenie usługi transakcyjnej  
  
1. Tworzenie kontraktu usługi i dodawanie adnotacji do operacji z odpowiednie ustawienie z <xref:System.ServiceModel.TransactionFlowOption> wyliczenia przychodzących wymagania dotyczące transakcji. Należy zauważyć, że możesz również umieścić <xref:System.ServiceModel.TransactionFlowAttribute> w klasie usługi wdrażane. Dzięki temu dla pojedynczej implementacji interfejsu, użyj tych ustawień transakcji, zamiast każdego wdrożenia.  
  
    ```csharp
    [ServiceContract]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // Use this to require an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Mandatory)]  
        double Add(double n1, double n2);  
        [OperationContract]  
        // Use this to permit an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        double Subtract(double n1, double n2);  
    }  
    ```  
  
2. Tworzenie klasy implementacji i używanie <xref:System.ServiceModel.ServiceBehaviorAttribute> aby opcjonalnie określić <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> i <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>. Należy zauważyć, że w wielu przypadkach domyślna <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 60 sekund, a wartość domyślna <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> z `Unspecified` są odpowiednie. Dla każdej operacji, można użyć <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu, aby określić, czy praca wykonywana w metodzie powinny być wykonywane w ramach zakresu zakres transakcji, zgodnie z wartością <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> atrybutu. W tym przypadku transakcji używane dla `Add` metody jest taka sama jak obowiązkowe transakcji przychodzących, która przepływa między klientem i umożliwiający transakcji `Subtract` metoda jest taki sam jak transakcji, jeśli jeden zostało przekazane klient lub niejawnie, jak i lokalnie utworzono nową transakcję.  
  
    ```csharp
    [ServiceBehavior(  
        TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
        TransactionTimeout = "00:00:45")]  
    public class CalculatorService : ICalculator  
    {  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n1} to {n2}");
            return n1 + n2;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n2} from {n1}");
            return n1 - n2;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
            // This is where the transaction provides specific benefit  
            // - changes to the database will be committed only when  
            // the transaction completes.  
        }  
    }  
    ```  
  
3. W pliku konfiguracji, określania, czy kontekst transakcji należy przepływ i protokołów, które ma być używany w tym celu należy skonfigurować powiązania. Aby uzyskać więcej informacji, zobacz [Konfiguracja transakcji modelu ServiceModel](servicemodel-transaction-configuration.md). W szczególności, typ powiązania jest określony w elemencie punktu końcowego `binding` atrybutu. [ \<Punktu końcowego >](../../configure-apps/file-schema/wcf/endpoint-element.md) element zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie `transactionalOleTransactionsTcpBinding`, jak pokazano na poniższym Przykładowa konfiguracja.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     Przepływ transakcji jest włączona na poziomie konfiguracji za pomocą `transactionFlow` atrybut i Protokół transakcji jest określony, przy użyciu `transactionProtocol` atrybutu, jak pokazano na następującej konfiguracji.  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a>Obsługa wielu protokołów transakcji  
  
1. Aby uzyskać optymalną wydajność należy użyć protokołu OleTransactions dla scenariuszy obejmujących klienta i usługi napisane przy użyciu usługi Windows Communication Foundation (WCF). Jednak protokół WS-AtomicTransaction (WS-AT) jest przydatne w scenariuszach, gdy wymagane jest współdziałanie ze stosów protokołu innych firm. Można skonfigurować usługi WCF do akceptowania oba protokoły, zapewniając wiele punktów końcowych przy użyciu odpowiednich powiązań związane z protokołem, jak pokazano w poniższym Przykładowa konfiguracja.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="http://localhost:8000/CalcService"  
        binding="wsHttpBinding"  
        bindingConfiguration="transactionalWsatHttpBinding"  
        contract="ICalculator"  
        name="WSAtomicTransaction_endpoint" />  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     Protokół transakcji jest określony, przy użyciu `transactionProtocol` atrybutu. Jednak ten atrybut jest nieobecne z dostarczanych przez system `wsHttpBinding`, ponieważ to powiązanie można używać tylko protokołu WS-AT.  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
        <binding name="transactionalWsatHttpBinding"  
          transactionFlow="true" />  
      </wsHttpBinding>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="controlling-the-completion-of-a-transaction"></a>Kontrolowanie ukończenia transakcji  
  
1. Domyślnie operacji WCF automatycznego ukończenia transakcji, jeśli nie nieobsłużone wyjątki są zgłaszane. To zachowanie można zmienić za pomocą <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwości i <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> metody. Podczas operacji musi występować w tej samej transakcji jako inna operacja (na przykład dla operacji debetowych i środków), można wyłączyć zachowanie automatycznego uzupełniania, ustawiając <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwość `false` jak pokazano w następującym `Debit` przykład operacji. Transakcji `Debit` używa operacja zakończy się aż do metody z <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwością `true` nosi nazwę, jak pokazano w operacji `Credit1`, lub gdy <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> metoda jest wywoływana, aby wyraźnie oznaczyć jako ukończony, jak pokazano w operacji transakcji `Credit2`. Należy pamiętać, że operacje dwóch środki są wyświetlane w celach ilustracyjnych i że pojedynczy środki operacji byłoby bardziej typowego.  
  
    ```csharp
    [ServiceBehavior]  
    public class CalculatorService : IAccount  
    {  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Debit(double n)  
        {  
            // Perform debit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = true)]  
        public void Credit1(double n)  
        {  
            // Perform credit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Credit2(double n)  
        {  
            // Perform alternate credit operation  
  
            OperationContext.Current.SetTransactionComplete();  
            return;  
        }  
    }  
    ```  
  
2. Na potrzeby korelacji transakcji, ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwość `false` wymaga użycia sesji powiązania. Wymóg ten jest określony za pomocą `SessionMode` właściwość <xref:System.ServiceModel.ServiceContractAttribute>.  
  
    ```csharp
    [ServiceContract(SessionMode = SessionMode.Required)]  
    public interface IAccount  
    {  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Debit(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit1(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit2(double n);  
    }  
    ```  
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a>Kontrolowanie okresu istnienia wystąpienia usługi transakcyjnej  
  
1. Korzysta z usługi WCF <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> właściwości w celu określenia, czy podstawowe wystąpienie usługi jest wydane po zakończeniu transakcji. Ponieważ jest to `true`, chyba że skonfigurowano inaczej, zachowanie aktywacji programu WCF wystawach efektywne i przewidywalne "just-in-time". Wywołań do usługi kolejnych transakcji zapewnione zostaną nowe wystąpienie usługi z nie pozostałości transakcji poprzedniego stanu. Chociaż często jest to przydatne, czasami możesz chcieć zarządzania stanem w wystąpieniu usługi poza ukończenia transakcji. Przykłady tego byłoby w przypadku stanu wymagane lub dojścia do zasobów kosztowne można pobrać lub odtworzenia. Można to zrobić, ustawiając <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> właściwość `false`. Z tym ustawieniem wystąpienie i każdy stan skojarzony będą dostępne w kolejnych wywołaniach. Korzystając z tego, dokładnie rozważyć do kiedy i jak stanu i transakcje zostaną wyczyszczone i zakończone. W poniższym przykładzie pokazano, jak to zrobić poprzez utrzymywanie wystąpienie z `runningTotal` zmiennej.  
  
    ```csharp
    [ServiceBehavior(TransactionIsolationLevel = [ServiceBehavior(  
        ReleaseServiceInstanceOnTransactionComplete = false)]  
    public class CalculatorService : ICalculator  
    {  
        double runningTotal = 0;  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n} to {runningTotal}");
            runningTotal = runningTotal + n;  
            return runningTotal;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n} from {runningTotal}");
            runningTotal = runningTotal - n;  
            return runningTotal;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  Ponieważ okres istnienia wystąpienia jest zachowanie wewnętrznych z usługą i kontrolowany za pośrednictwem <xref:System.ServiceModel.ServiceBehaviorAttribute> , nie modyfikacji konfiguracji usługi lub kontraktu usługi jest wymagana właściwość można ustawić zachowanie wystąpienia. Ponadto podczas transmisji będzie zawierać nie reprezentację.
