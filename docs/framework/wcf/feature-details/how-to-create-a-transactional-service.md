---
title: "Instrukcje: Tworzenie usługi transakcyjnej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 647b551e9b78d89cee3ddaf8f47ba8174a23fc5a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-transactional-service"></a>Instrukcje: Tworzenie usługi transakcyjnej
W tym przykładzie przedstawiono różne aspekty Tworzenie usługi transakcyjnej i użycie transakcji inicjowanych przez klienta do koordynowania operacji usługi.  
  
### <a name="creating-a-transactional-service"></a>Tworzenie usługi transakcyjnej  
  
1.  Tworzenie kontraktu usługi i adnotacje operacje z odpowiednie ustawienie z <xref:System.ServiceModel.TransactionFlowOption> wyliczeniu, aby określić przychodzące wymagania dotyczące transakcji. Należy pamiętać, że możesz również umieścić <xref:System.ServiceModel.TransactionFlowAttribute> w klasie usługi implementowana. Dzięki temu dla pojedynczej implementacji interfejsu za pomocą tych ustawień transakcji, zamiast każdego wdrożenia.  
  
    ```  
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
  
2.  Klasa implementacji tworzenia i używania <xref:System.ServiceModel.ServiceBehaviorAttribute> można opcjonalnie określić <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> i <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>. Należy zauważyć, że w wielu przypadkach domyślna <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 60 sekund i domyślnie <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> z `Unspecified` są odpowiednie. Dla każdej operacji można użyć <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu, aby określić, czy praca jest wykonywana w metodzie powinny występować w zakresie zakresu transakcji zgodnie z wartością <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> atrybutu. W takim przypadku transakcja używana dla `Add` metody jest taka sama jak obowiązkowe transakcji przychodzącej, które jest umieszczane z klienta, a transakcja używana dla `Subtract` metody jest albo taki sam jak transakcji przychodzącej Jeśli jeden została skierowana z klienta lub nowej transakcji utworzony niejawnie i lokalnie.  
  
    ```  
    [ServiceBehavior(  
        TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
        TransactionTimeout = "00:00:45")]  
    public class CalculatorService : ICalculator  
    {  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Adding {0} to {1}", n1, n2));  
            return n1 + n2;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Subtracting {0} from {1}", n2, n1));  
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
  
3.  Skonfiguruj powiązania w pliku konfiguracji, określając, że powinien przepływ kontekstu transakcji i protokołów do użycia w tym celu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Konfiguracja transakcji modelu ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md). W szczególności w elementu punktu końcowego określono typ powiązania `binding` atrybutu. [ \<Punktu końcowego >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie `transactionalOleTransactionsTcpBinding`, jak pokazano w poniższych Przykładowa konfiguracja.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     Przepływ transakcji jest włączona na poziomie konfiguracji za pomocą `transactionFlow` atrybut i Protokół transakcji jest określona za pomocą `transactionProtocol` atrybutu, jak pokazano w poniższej konfiguracji.  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a>Obsługa wielu protokoły transakcji  
  
1.  Aby uzyskać optymalną wydajność, należy używać protokołu OleTransactions dla scenariuszy obejmujących klienta i usługi napisane przy użyciu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Jednak protokołu WS-AtomicTransaction (WS-AT) jest przydatne w scenariuszach, gdy wymagane jest współdziałanie z stosy protokołu innych firm. Można skonfigurować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, aby zaakceptować oba protokoły przez zapewnienie wiele punktów końcowych z odpowiednich powiązań protokołem, jak pokazano w poniższych Przykładowa konfiguracja.  
  
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
  
     Protokół transakcji jest określona za pomocą `transactionProtocol` atrybutu. Jednak ten atrybut jest nieobecny z dostarczane przez system `wsHttpBinding`, ponieważ to powiązanie można używać tylko protokołu WS-AT.  
  
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
  
1.  Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] operacji automatycznie realizacji transakcji, jeśli nie nieobsługiwane wyjątki są zgłaszane. To zachowanie można zmienić za pomocą <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwości i <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> metody. Podczas operacji jest wymagany w tej samej transakcji, jak inna operacja (na przykład operację debetowa i środki), można wyłączyć zachowanie funkcji autocomplete przez ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwości `false` jak pokazano w następującym `Debit` przykład operację. Transakcja `Debit` używa operacji nie jest ukończona, dopóki metodę o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> ustawioną właściwość `true` nosi nazwę, jak pokazano w operacji `Credit1`, lub gdy <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> wywoływana jest metoda jawnie oznaczyć jako ukończonych, jak pokazano w operacji transakcji `Credit2`. Należy pamiętać, że środki dwóch operacji są wyświetlane w celach ilustracyjnych i że pojedynczy karty kredytowej operacji będzie bardziej typowego.  
  
    ```  
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
  
2.  Na potrzeby korelacji transakcji, ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwości `false` wymaga użycia powiązania sesyjnych. To wymaganie jest określany za pomocą `SessionMode` właściwość <xref:System.ServiceModel.ServiceContractAttribute>.  
  
    ```  
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a>Kontrolowanie okres istnienia wystąpienia usługi transakcyjnej  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]używa <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> właściwości w celu określenia, czy źródłowy wystąpienie usługi jest zwolnione po zakończeniu transakcji. Od tej wartości domyślnie przyjmowana `true`, chyba że zostaną skonfigurowane, w przeciwnym razie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spowoduje zachowanie wydajne i przewidywalne aktywacji "just-in-time". Zapewni nowego wystąpienia usługi z nie wszystkie elementy poprzedniej transakcji Państwo wywołań usługi kolejnych transakcji. Często jest to przydatne, czasami można do zarządzania stanem w wystąpieniu usługi, po zakończeniu transakcji. Przykładem tego może dochodzić do stanu wymagane lub dojść do zasobów jest dość kosztowna można pobrać lub odtworzenia. Można to zrobić przez ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> właściwości `false`. Z tego ustawienia, wystąpienia i każdy stan skojarzony będą dostępne w kolejnych wywołaniach. Korzystając z tego, rozważyć zachować ostrożność podczas i jak stanu i transakcji zostanie wyczyszczona i zakończone. W poniższym przykładzie pokazano, jak to zrobić przez wystąpienie o zachowaniu `runningTotal` zmiennej.  
  
    ```  
    [ServiceBehavior(TransactionIsolationLevel = [ServiceBehavior(  
        ReleaseServiceInstanceOnTransactionComplete = false)]  
    public class CalculatorService : ICalculator  
    {  
        double runningTotal = 0;  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Adding {0} to {1}", n, runningTotal));  
            runningTotal = runningTotal + n;  
            return runningTotal;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Subtracting {0} from {1}", n, runningTotal));  
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
    >  Ponieważ okres istnienia wystąpienia jest zachowanie wewnętrzny z usługą i kontrolowane poprzez <xref:System.ServiceModel.ServiceBehaviorAttribute> , żadnych zmian w konfiguracji usługi lub kontraktu usługi jest wymagana właściwość można ustawić zachowanie wystąpienia. Ponadto przesyłania będzie zawierać nie reprezentację.
