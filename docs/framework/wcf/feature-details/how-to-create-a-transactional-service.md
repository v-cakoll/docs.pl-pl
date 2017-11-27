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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a7ef8d4778b21d33501e3f3d4478b722bf1e1cc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-transactional-service"></a><span data-ttu-id="869ce-102">Instrukcje: Tworzenie usługi transakcyjnej</span><span class="sxs-lookup"><span data-stu-id="869ce-102">How to: Create a Transactional Service</span></span>
<span data-ttu-id="869ce-103">W tym przykładzie przedstawiono różne aspekty Tworzenie usługi transakcyjnej i użycie transakcji inicjowanych przez klienta do koordynowania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="869ce-103">This sample demonstrates various aspects of creating a transactional service and the use of a client-initiated transaction to coordinate service operations.</span></span>  
  
### <a name="creating-a-transactional-service"></a><span data-ttu-id="869ce-104">Tworzenie usługi transakcyjnej</span><span class="sxs-lookup"><span data-stu-id="869ce-104">Creating a transactional service</span></span>  
  
1.  <span data-ttu-id="869ce-105">Tworzenie kontraktu usługi i adnotacje operacje z odpowiednie ustawienie z <xref:System.ServiceModel.TransactionFlowOption> wyliczeniu, aby określić przychodzące wymagania dotyczące transakcji.</span><span class="sxs-lookup"><span data-stu-id="869ce-105">Create a service contract and annotate the operations with the desired setting from the <xref:System.ServiceModel.TransactionFlowOption> enumeration to specify the incoming transaction requirements.</span></span> <span data-ttu-id="869ce-106">Należy pamiętać, że możesz również umieścić <xref:System.ServiceModel.TransactionFlowAttribute> w klasie usługi implementowana.</span><span class="sxs-lookup"><span data-stu-id="869ce-106">Note that you can also place the <xref:System.ServiceModel.TransactionFlowAttribute> on the service class being implemented.</span></span> <span data-ttu-id="869ce-107">Dzięki temu dla pojedynczej implementacji interfejsu za pomocą tych ustawień transakcji, zamiast każdego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="869ce-107">This allows for a single implementation of an interface to use these transaction settings, instead of every implementation.</span></span>  
  
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
  
2.  <span data-ttu-id="869ce-108">Klasa implementacji tworzenia i używania <xref:System.ServiceModel.ServiceBehaviorAttribute> można opcjonalnie określić <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> i <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="869ce-108">Create an implementation class, and use the <xref:System.ServiceModel.ServiceBehaviorAttribute> to optionally specify a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span></span> <span data-ttu-id="869ce-109">Należy zauważyć, że w wielu przypadkach domyślna <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 60 sekund i domyślnie <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> z `Unspecified` są odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="869ce-109">You should note that in many cases, the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> of 60 seconds and the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> of `Unspecified` are appropriate.</span></span> <span data-ttu-id="869ce-110">Dla każdej operacji można użyć <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu, aby określić, czy praca jest wykonywana w metodzie powinny występować w zakresie zakresu transakcji zgodnie z wartością <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="869ce-110">For each operation, you can use the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute to specify whether work performed within the method should occur within the scope of a transaction scope according to the value of the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribute.</span></span> <span data-ttu-id="869ce-111">W takim przypadku transakcja używana dla `Add` metody jest taka sama jak obowiązkowe transakcji przychodzącej, które jest umieszczane z klienta, a transakcja używana dla `Subtract` metody jest albo taki sam jak transakcji przychodzącej Jeśli jeden została skierowana z klienta lub nowej transakcji utworzony niejawnie i lokalnie.</span><span class="sxs-lookup"><span data-stu-id="869ce-111">In this case, the transaction used for the `Add` method is the same as the mandatory incoming transaction that is flowed from the client, and the transaction used for the `Subtract` method is either the same as the incoming transaction if one was flowed from the client, or a new implicitly and locally created transaction.</span></span>  
  
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
  
3.  <span data-ttu-id="869ce-112">Skonfiguruj powiązania w pliku konfiguracji, określając, że powinien przepływ kontekstu transakcji i protokołów do użycia w tym celu.</span><span class="sxs-lookup"><span data-stu-id="869ce-112">Configure the bindings in the configuration file, specifying that the transaction context should be flowed, and the protocols to be used to do so.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="869ce-113">[Konfiguracja transakcji modelu ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="869ce-113"> [ServiceModel Transaction Configuration](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md).</span></span> <span data-ttu-id="869ce-114">W szczególności w elementu punktu końcowego określono typ powiązania `binding` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="869ce-114">Specifically, the binding type is specified in the endpoint element’s `binding` attribute.</span></span> <span data-ttu-id="869ce-115">[ \<Punktu końcowego >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie `transactionalOleTransactionsTcpBinding`, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="869ce-115">The [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element contains a `bindingConfiguration` attribute that references a binding configuration named `transactionalOleTransactionsTcpBinding`, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="869ce-116">Przepływ transakcji jest włączona na poziomie konfiguracji za pomocą `transactionFlow` atrybut i Protokół transakcji jest określona za pomocą `transactionProtocol` atrybutu, jak pokazano w poniższej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="869ce-116">Transaction flow is enabled at the configuration level by using the `transactionFlow` attribute, and the transaction protocol is specified using the `transactionProtocol` attribute, as shown in the following configuration.</span></span>  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a><span data-ttu-id="869ce-117">Obsługa wielu protokoły transakcji</span><span class="sxs-lookup"><span data-stu-id="869ce-117">Supporting multiple transaction protocols</span></span>  
  
1.  <span data-ttu-id="869ce-118">Aby uzyskać optymalną wydajność, należy używać protokołu OleTransactions dla scenariuszy obejmujących klienta i usługi napisane przy użyciu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="869ce-118">For optimal performance, you should use the OleTransactions protocol for scenarios involving a client and service written using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="869ce-119">Jednak protokołu WS-AtomicTransaction (WS-AT) jest przydatne w scenariuszach, gdy wymagane jest współdziałanie z stosy protokołu innych firm.</span><span class="sxs-lookup"><span data-stu-id="869ce-119">However, the WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span> <span data-ttu-id="869ce-120">Można skonfigurować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, aby zaakceptować oba protokoły przez zapewnienie wiele punktów końcowych z odpowiednich powiązań protokołem, jak pokazano w poniższych Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="869ce-120">You can configure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to accept both protocols by providing multiple endpoints with appropriate protocol-specific bindings, as shown in the following sample configuration.</span></span>  
  
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
  
     <span data-ttu-id="869ce-121">Protokół transakcji jest określona za pomocą `transactionProtocol` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="869ce-121">The transaction protocol is specified using the `transactionProtocol` attribute.</span></span> <span data-ttu-id="869ce-122">Jednak ten atrybut jest nieobecny z dostarczane przez system `wsHttpBinding`, ponieważ to powiązanie można używać tylko protokołu WS-AT.</span><span class="sxs-lookup"><span data-stu-id="869ce-122">However, this attribute is absent from the system-provided `wsHttpBinding`, because this binding can only use the WS-AT protocol.</span></span>  
  
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
  
### <a name="controlling-the-completion-of-a-transaction"></a><span data-ttu-id="869ce-123">Kontrolowanie ukończenia transakcji</span><span class="sxs-lookup"><span data-stu-id="869ce-123">Controlling the completion of a transaction</span></span>  
  
1.  <span data-ttu-id="869ce-124">Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] operacji automatycznie realizacji transakcji, jeśli nie nieobsługiwane wyjątki są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="869ce-124">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] operations automatically complete transactions if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="869ce-125">To zachowanie można zmienić za pomocą <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwości i <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="869ce-125">You can modify this behavior by using the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property and the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method.</span></span> <span data-ttu-id="869ce-126">Podczas operacji jest wymagany w tej samej transakcji, jak inna operacja (na przykład operację debetowa i środki), można wyłączyć zachowanie funkcji autocomplete przez ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwości `false` jak pokazano w następującym `Debit` przykład operację.</span><span class="sxs-lookup"><span data-stu-id="869ce-126">When an operation is required to occur within the same transaction as another operation (for example, a debit and credit operation), you can disable the autocomplete behavior by setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` as shown in the following `Debit` operation example.</span></span> <span data-ttu-id="869ce-127">Transakcja `Debit` używa operacji nie jest ukończona, dopóki metodę o <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> ustawioną właściwość `true` nosi nazwę, jak pokazano w operacji `Credit1`, lub gdy <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> wywoływana jest metoda jawnie oznaczyć jako ukończonych, jak pokazano w operacji transakcji `Credit2`.</span><span class="sxs-lookup"><span data-stu-id="869ce-127">The transaction the `Debit` operation uses is not completed until a method with the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property set to `true` is called, as shown in the operation `Credit1`, or when the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method is called to explicitly mark the transaction as complete, as shown in the operation `Credit2`.</span></span> <span data-ttu-id="869ce-128">Należy pamiętać, że środki dwóch operacji są wyświetlane w celach ilustracyjnych i że pojedynczy karty kredytowej operacji będzie bardziej typowego.</span><span class="sxs-lookup"><span data-stu-id="869ce-128">Note that the two credit operations are shown for illustration purposes, and that a single credit operation would be more typical.</span></span>  
  
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
  
2.  <span data-ttu-id="869ce-129">Na potrzeby korelacji transakcji, ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwości `false` wymaga użycia powiązania sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="869ce-129">For the purposes of transaction correlation, setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` requires the use of a sessionful binding.</span></span> <span data-ttu-id="869ce-130">To wymaganie jest określany za pomocą `SessionMode` właściwość <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="869ce-130">This requirement is specified with the `SessionMode` property on the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span>  
  
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a><span data-ttu-id="869ce-131">Kontrolowanie okres istnienia wystąpienia usługi transakcyjnej</span><span class="sxs-lookup"><span data-stu-id="869ce-131">Controlling the lifetime of a transactional service instance</span></span>  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="869ce-132">używa <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> właściwości w celu określenia, czy źródłowy wystąpienie usługi jest zwolnione po zakończeniu transakcji.</span><span class="sxs-lookup"><span data-stu-id="869ce-132"> uses the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to specify whether the underlying service instance is released when a transaction completes.</span></span> <span data-ttu-id="869ce-133">Od tej wartości domyślnie przyjmowana `true`, chyba że zostaną skonfigurowane, w przeciwnym razie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spowoduje zachowanie wydajne i przewidywalne aktywacji "just-in-time".</span><span class="sxs-lookup"><span data-stu-id="869ce-133">Since this defaults to `true`, unless configured otherwise, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exhibits an efficient and predictable "just-in-time" activation behavior.</span></span> <span data-ttu-id="869ce-134">Zapewni nowego wystąpienia usługi z nie wszystkie elementy poprzedniej transakcji Państwo wywołań usługi kolejnych transakcji.</span><span class="sxs-lookup"><span data-stu-id="869ce-134">Calls to a service on a subsequent transaction are assured a new service instance with no remnants of the previous transaction's state.</span></span> <span data-ttu-id="869ce-135">Często jest to przydatne, czasami można do zarządzania stanem w wystąpieniu usługi, po zakończeniu transakcji.</span><span class="sxs-lookup"><span data-stu-id="869ce-135">While this is often useful, sometimes you may want to maintain state within the service instance beyond the transaction completion.</span></span> <span data-ttu-id="869ce-136">Przykładem tego może dochodzić do stanu wymagane lub dojść do zasobów jest dość kosztowna można pobrać lub odtworzenia.</span><span class="sxs-lookup"><span data-stu-id="869ce-136">Examples of this would be when required state or handles to resources are expensive to retrieve or reconstitute.</span></span> <span data-ttu-id="869ce-137">Można to zrobić przez ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="869ce-137">You can do this by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to `false`.</span></span> <span data-ttu-id="869ce-138">Z tego ustawienia, wystąpienia i każdy stan skojarzony będą dostępne w kolejnych wywołaniach.</span><span class="sxs-lookup"><span data-stu-id="869ce-138">With that setting, the instance and any associated state will be available on subsequent calls.</span></span> <span data-ttu-id="869ce-139">Korzystając z tego, rozważyć zachować ostrożność podczas i jak stanu i transakcji zostanie wyczyszczona i zakończone.</span><span class="sxs-lookup"><span data-stu-id="869ce-139">When using this, give careful consideration to when and how state and transactions will be cleared and completed.</span></span> <span data-ttu-id="869ce-140">W poniższym przykładzie pokazano, jak to zrobić przez wystąpienie o zachowaniu `runningTotal` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="869ce-140">The following sample demonstrates how to do this by maintaining the instance with the `runningTotal` variable.</span></span>  
  
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
    >  <span data-ttu-id="869ce-141">Ponieważ okres istnienia wystąpienia jest zachowanie wewnętrzny z usługą i kontrolowane poprzez <xref:System.ServiceModel.ServiceBehaviorAttribute> , żadnych zmian w konfiguracji usługi lub kontraktu usługi jest wymagana właściwość można ustawić zachowanie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="869ce-141">Since the instance lifetime is a behavior that is internal to the service, and controlled through the <xref:System.ServiceModel.ServiceBehaviorAttribute> property, no modification to the service configuration or service contract is required to set the instance behavior.</span></span> <span data-ttu-id="869ce-142">Ponadto przesyłania będzie zawierać nie reprezentację.</span><span class="sxs-lookup"><span data-stu-id="869ce-142">In addition, the wire will contain no representation of this.</span></span>
