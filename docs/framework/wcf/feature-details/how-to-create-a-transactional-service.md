---
title: 'Instrukcje: tworzenie usługi transakcyjnej'
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: be364e7638394a30c199b05dd15ef4c44e18e688
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964016"
---
# <a name="how-to-create-a-transactional-service"></a><span data-ttu-id="a93ce-102">Instrukcje: tworzenie usługi transakcyjnej</span><span class="sxs-lookup"><span data-stu-id="a93ce-102">How to: Create a Transactional Service</span></span>
<span data-ttu-id="a93ce-103">W tym przykładzie przedstawiono różne aspekty tworzenia usługi transakcyjnej oraz użycie transakcji zainicjowanej przez klienta w celu koordynowania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a93ce-103">This sample demonstrates various aspects of creating a transactional service and the use of a client-initiated transaction to coordinate service operations.</span></span>  
  
### <a name="creating-a-transactional-service"></a><span data-ttu-id="a93ce-104">Tworzenie usługi transakcyjnej</span><span class="sxs-lookup"><span data-stu-id="a93ce-104">Creating a transactional service</span></span>  
  
1. <span data-ttu-id="a93ce-105">Utwórz kontrakt usługi i Dodaj adnotację do operacji z wymaganym ustawieniem z <xref:System.ServiceModel.TransactionFlowOption> wyliczenia, aby określić wymagania dotyczące transakcji przychodzących.</span><span class="sxs-lookup"><span data-stu-id="a93ce-105">Create a service contract and annotate the operations with the desired setting from the <xref:System.ServiceModel.TransactionFlowOption> enumeration to specify the incoming transaction requirements.</span></span> <span data-ttu-id="a93ce-106">Należy zauważyć, że można również umieścić <xref:System.ServiceModel.TransactionFlowAttribute> w implementowanej klasie usług.</span><span class="sxs-lookup"><span data-stu-id="a93ce-106">Note that you can also place the <xref:System.ServiceModel.TransactionFlowAttribute> on the service class being implemented.</span></span> <span data-ttu-id="a93ce-107">Dzięki temu pojedyncze implementacje interfejsu mogą korzystać z tych ustawień transakcji zamiast każdej implementacji.</span><span class="sxs-lookup"><span data-stu-id="a93ce-107">This allows for a single implementation of an interface to use these transaction settings, instead of every implementation.</span></span>  
  
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
  
2. <span data-ttu-id="a93ce-108">Utwórz klasę implementacji i Użyj <xref:System.ServiceModel.ServiceBehaviorAttribute> , aby opcjonalnie <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> określić i <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="a93ce-108">Create an implementation class, and use the <xref:System.ServiceModel.ServiceBehaviorAttribute> to optionally specify a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span></span> <span data-ttu-id="a93ce-109">Należy zauważyć, że w wielu przypadkach wartość domyślna <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> to 60 sekund i wartość `Unspecified` Domyślna <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> to.</span><span class="sxs-lookup"><span data-stu-id="a93ce-109">You should note that in many cases, the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> of 60 seconds and the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> of `Unspecified` are appropriate.</span></span> <span data-ttu-id="a93ce-110">Dla każdej operacji można użyć <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu, aby określić, czy prace wykonywane w ramach metody powinny należeć do zakresu transakcji zgodnie z wartością <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a93ce-110">For each operation, you can use the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute to specify whether work performed within the method should occur within the scope of a transaction scope according to the value of the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribute.</span></span> <span data-ttu-id="a93ce-111">W takim przypadku transakcja użyta dla `Add` metody jest taka sama jak obowiązkowa transakcja przychodząca, która jest przepływa z klienta, a transakcja użyta `Subtract` dla metody jest taka sama jak transakcja przychodząca, jeśli została przepływa od klienta lub nowej niejawnie i lokalnie utworzonej transakcji.</span><span class="sxs-lookup"><span data-stu-id="a93ce-111">In this case, the transaction used for the `Add` method is the same as the mandatory incoming transaction that is flowed from the client, and the transaction used for the `Subtract` method is either the same as the incoming transaction if one was flowed from the client, or a new implicitly and locally created transaction.</span></span>  
  
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
  
3. <span data-ttu-id="a93ce-112">Skonfiguruj powiązania w pliku konfiguracji, określając, że kontekst transakcji powinien być przepływem, i protokoły, które mają być używane w tym celu.</span><span class="sxs-lookup"><span data-stu-id="a93ce-112">Configure the bindings in the configuration file, specifying that the transaction context should be flowed, and the protocols to be used to do so.</span></span> <span data-ttu-id="a93ce-113">Aby uzyskać więcej informacji, zobacz [Konfiguracja transakcji ServiceModel](servicemodel-transaction-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="a93ce-113">For more information, see [ServiceModel Transaction Configuration](servicemodel-transaction-configuration.md).</span></span> <span data-ttu-id="a93ce-114">W każdym przypadku typ powiązania jest określony w `binding` atrybucie elementu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="a93ce-114">Specifically, the binding type is specified in the endpoint element’s `binding` attribute.</span></span> <span data-ttu-id="a93ce-115">Element > `bindingConfiguration` `transactionalOleTransactionsTcpBinding`punktu końcowego zawiera atrybut odwołujący się do konfiguracji powiązania o nazwie, jak pokazano w poniższej konfiguracji przykładowej. [ \<](../../configure-apps/file-schema/wcf/endpoint-element.md)</span><span class="sxs-lookup"><span data-stu-id="a93ce-115">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element contains a `bindingConfiguration` attribute that references a binding configuration named `transactionalOleTransactionsTcpBinding`, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="a93ce-116">Przepływ transakcji jest włączony na poziomie konfiguracji przy użyciu `transactionFlow` atrybutu, a protokół transakcji jest określany `transactionProtocol` przy użyciu atrybutu, jak pokazano w poniższej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a93ce-116">Transaction flow is enabled at the configuration level by using the `transactionFlow` attribute, and the transaction protocol is specified using the `transactionProtocol` attribute, as shown in the following configuration.</span></span>  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a><span data-ttu-id="a93ce-117">Obsługa wielu protokołów transakcji</span><span class="sxs-lookup"><span data-stu-id="a93ce-117">Supporting multiple transaction protocols</span></span>  
  
1. <span data-ttu-id="a93ce-118">Aby uzyskać optymalną wydajność, należy użyć protokołu OleTransactions na potrzeby scenariuszy obejmujących klienta i usługę zapisaną przy użyciu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a93ce-118">For optimal performance, you should use the OleTransactions protocol for scenarios involving a client and service written using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="a93ce-119">Jednak protokół WS-AtomicTransaction (WS-AT) jest użyteczny w scenariuszach, gdy wymagane jest współdziałanie z stosami protokołu innych firm.</span><span class="sxs-lookup"><span data-stu-id="a93ce-119">However, the WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span> <span data-ttu-id="a93ce-120">Usługi WCF można skonfigurować tak, aby akceptowały oba protokoły, dostarczając wiele punktów końcowych z odpowiednimi powiązaniami specyficznymi dla protokołu, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="a93ce-120">You can configure WCF services to accept both protocols by providing multiple endpoints with appropriate protocol-specific bindings, as shown in the following sample configuration.</span></span>  
  
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
  
     <span data-ttu-id="a93ce-121">Protokół transakcji jest określony przy użyciu `transactionProtocol` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a93ce-121">The transaction protocol is specified using the `transactionProtocol` attribute.</span></span> <span data-ttu-id="a93ce-122">Jednak ten atrybut jest nieobecny w dostarczonych `wsHttpBinding`przez system, ponieważ to powiązanie może korzystać tylko z protokołu WS-AT.</span><span class="sxs-lookup"><span data-stu-id="a93ce-122">However, this attribute is absent from the system-provided `wsHttpBinding`, because this binding can only use the WS-AT protocol.</span></span>  
  
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
  
### <a name="controlling-the-completion-of-a-transaction"></a><span data-ttu-id="a93ce-123">Kontrolowanie ukończenia transakcji</span><span class="sxs-lookup"><span data-stu-id="a93ce-123">Controlling the completion of a transaction</span></span>  
  
1. <span data-ttu-id="a93ce-124">Domyślnie operacje WCF automatycznie uzupełniają transakcje, jeśli nie zostaną zgłoszone żadne Nieobsłużone wyjątki.</span><span class="sxs-lookup"><span data-stu-id="a93ce-124">By default, WCF operations automatically complete transactions if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="a93ce-125">To zachowanie można zmodyfikować przy użyciu <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwości <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> i metody.</span><span class="sxs-lookup"><span data-stu-id="a93ce-125">You can modify this behavior by using the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property and the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method.</span></span> <span data-ttu-id="a93ce-126">Gdy operacja jest wymagana w ramach tej samej transakcji co inna operacja (na przykład Debet i kredyt), można wyłączyć zachowanie autouzupełniania, ustawiając <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwość na `false` tak, jak pokazano w poniższej tabeli.`Debit` przykład operacji.</span><span class="sxs-lookup"><span data-stu-id="a93ce-126">When an operation is required to occur within the same transaction as another operation (for example, a debit and credit operation), you can disable the autocomplete behavior by setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` as shown in the following `Debit` operation example.</span></span> <span data-ttu-id="a93ce-127">Transakcja, której `Debit` używa operacja, nie zostanie zakończona do momentu wywołania <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> metody z ustawioną `true` właściwością, jak <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> pokazano w operacji `Credit1`, lub gdy wywoływana jest metoda, aby jawnie oznaczyć transakcja jako kompletna, jak pokazano w operacji `Credit2`.</span><span class="sxs-lookup"><span data-stu-id="a93ce-127">The transaction the `Debit` operation uses is not completed until a method with the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property set to `true` is called, as shown in the operation `Credit1`, or when the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method is called to explicitly mark the transaction as complete, as shown in the operation `Credit2`.</span></span> <span data-ttu-id="a93ce-128">Należy zauważyć, że dwie operacje kredytowe są przedstawiane na potrzeby ilustracji i że pojedyncze operacje kredytowe byłyby bardziej typowe.</span><span class="sxs-lookup"><span data-stu-id="a93ce-128">Note that the two credit operations are shown for illustration purposes, and that a single credit operation would be more typical.</span></span>  
  
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
  
2. <span data-ttu-id="a93ce-129">Na potrzeby korelacji transakcji ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> `false` właściwości wymaga użycia powiązania sesji.</span><span class="sxs-lookup"><span data-stu-id="a93ce-129">For the purposes of transaction correlation, setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` requires the use of a sessionful binding.</span></span> <span data-ttu-id="a93ce-130">To wymaganie jest określone za `SessionMode` pomocą właściwości <xref:System.ServiceModel.ServiceContractAttribute>w.</span><span class="sxs-lookup"><span data-stu-id="a93ce-130">This requirement is specified with the `SessionMode` property on the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span>  
  
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a><span data-ttu-id="a93ce-131">Kontrolowanie okresu istnienia wystąpienia usługi transakcyjnej</span><span class="sxs-lookup"><span data-stu-id="a93ce-131">Controlling the lifetime of a transactional service instance</span></span>  
  
1. <span data-ttu-id="a93ce-132">Funkcja WCF używa <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> właściwości, aby określić, czy bazowe wystąpienie usługi jest wydawany po zakończeniu transakcji.</span><span class="sxs-lookup"><span data-stu-id="a93ce-132">WCF uses the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to specify whether the underlying service instance is released when a transaction completes.</span></span> <span data-ttu-id="a93ce-133">Ponieważ ta wartość domyślna `true`to, o ile nie zostanie skonfigurowany w inny sposób, usługa WCF wykazuje wydajne i przewidywalne zachowanie aktywacji "just-in-Time".</span><span class="sxs-lookup"><span data-stu-id="a93ce-133">Since this defaults to `true`, unless configured otherwise, WCF exhibits an efficient and predictable "just-in-time" activation behavior.</span></span> <span data-ttu-id="a93ce-134">Wywołania usługi w kolejnej transakcji są gwarantowane nowym wystąpieniem usługi bez postanowień poprzedniego stanu transakcji.</span><span class="sxs-lookup"><span data-stu-id="a93ce-134">Calls to a service on a subsequent transaction are assured a new service instance with no remnants of the previous transaction's state.</span></span> <span data-ttu-id="a93ce-135">Chociaż jest to często przydatne, czasami warto zachować stan w ramach wystąpienia usługi poza ukończeniem transakcji.</span><span class="sxs-lookup"><span data-stu-id="a93ce-135">While this is often useful, sometimes you may want to maintain state within the service instance beyond the transaction completion.</span></span> <span data-ttu-id="a93ce-136">Przykłady tego stanu byłyby kosztowne do pobrania lub odtworzenia zasobów.</span><span class="sxs-lookup"><span data-stu-id="a93ce-136">Examples of this would be when required state or handles to resources are expensive to retrieve or reconstitute.</span></span> <span data-ttu-id="a93ce-137">Można to zrobić, ustawiając <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> właściwość na. `false`</span><span class="sxs-lookup"><span data-stu-id="a93ce-137">You can do this by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to `false`.</span></span> <span data-ttu-id="a93ce-138">W przypadku tego ustawienia wystąpienie i wszystkie powiązane Stany będą dostępne po kolejnych wywołaniach.</span><span class="sxs-lookup"><span data-stu-id="a93ce-138">With that setting, the instance and any associated state will be available on subsequent calls.</span></span> <span data-ttu-id="a93ce-139">W tym celu należy zwrócić szczególną uwagę na to, kiedy i w jaki sposób stan i transakcje zostaną wyczyszczone i zakończone.</span><span class="sxs-lookup"><span data-stu-id="a93ce-139">When using this, give careful consideration to when and how state and transactions will be cleared and completed.</span></span> <span data-ttu-id="a93ce-140">Poniższy przykład demonstruje, jak to zrobić, utrzymując wystąpienie ze `runningTotal` zmienną.</span><span class="sxs-lookup"><span data-stu-id="a93ce-140">The following sample demonstrates how to do this by maintaining the instance with the `runningTotal` variable.</span></span>  
  
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
    > <span data-ttu-id="a93ce-141">Ponieważ okres istnienia wystąpienia jest zachowaniem wewnętrznym dla usługi i kontrolowanym przez <xref:System.ServiceModel.ServiceBehaviorAttribute> właściwość, nie jest wymagane żadne modyfikacje w konfiguracji usługi lub kontrakcie usługi, aby można było ustawić zachowanie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a93ce-141">Since the instance lifetime is a behavior that is internal to the service, and controlled through the <xref:System.ServiceModel.ServiceBehaviorAttribute> property, no modification to the service configuration or service contract is required to set the instance behavior.</span></span> <span data-ttu-id="a93ce-142">Ponadto drut nie będzie zawierał żadnych reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="a93ce-142">In addition, the wire will contain no representation of this.</span></span>
