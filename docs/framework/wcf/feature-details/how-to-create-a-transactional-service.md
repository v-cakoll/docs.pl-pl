---
title: 'Instrukcje: tworzenie usługi transakcyjnej'
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: 7f7f060db5a4ffd66524e220e3e3291debd8a3fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787598"
---
# <a name="how-to-create-a-transactional-service"></a><span data-ttu-id="77950-102">Instrukcje: tworzenie usługi transakcyjnej</span><span class="sxs-lookup"><span data-stu-id="77950-102">How to: Create a Transactional Service</span></span>
<span data-ttu-id="77950-103">Niniejszy przykład pokazuje różne aspekty Tworzenie usługi transakcyjnej i użycie transakcji zainicjowanych przez klienta do koordynowania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="77950-103">This sample demonstrates various aspects of creating a transactional service and the use of a client-initiated transaction to coordinate service operations.</span></span>  
  
### <a name="creating-a-transactional-service"></a><span data-ttu-id="77950-104">Tworzenie usługi transakcyjnej</span><span class="sxs-lookup"><span data-stu-id="77950-104">Creating a transactional service</span></span>  
  
1. <span data-ttu-id="77950-105">Tworzenie kontraktu usługi i dodawanie adnotacji do operacji z odpowiednie ustawienie z <xref:System.ServiceModel.TransactionFlowOption> wyliczenia przychodzących wymagania dotyczące transakcji.</span><span class="sxs-lookup"><span data-stu-id="77950-105">Create a service contract and annotate the operations with the desired setting from the <xref:System.ServiceModel.TransactionFlowOption> enumeration to specify the incoming transaction requirements.</span></span> <span data-ttu-id="77950-106">Należy zauważyć, że możesz również umieścić <xref:System.ServiceModel.TransactionFlowAttribute> w klasie usługi wdrażane.</span><span class="sxs-lookup"><span data-stu-id="77950-106">Note that you can also place the <xref:System.ServiceModel.TransactionFlowAttribute> on the service class being implemented.</span></span> <span data-ttu-id="77950-107">Dzięki temu dla pojedynczej implementacji interfejsu, użyj tych ustawień transakcji, zamiast każdego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="77950-107">This allows for a single implementation of an interface to use these transaction settings, instead of every implementation.</span></span>  
  
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
  
2. <span data-ttu-id="77950-108">Tworzenie klasy implementacji i używanie <xref:System.ServiceModel.ServiceBehaviorAttribute> aby opcjonalnie określić <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> i <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="77950-108">Create an implementation class, and use the <xref:System.ServiceModel.ServiceBehaviorAttribute> to optionally specify a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span></span> <span data-ttu-id="77950-109">Należy zauważyć, że w wielu przypadkach domyślna <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 60 sekund, a wartość domyślna <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> z `Unspecified` są odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="77950-109">You should note that in many cases, the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> of 60 seconds and the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> of `Unspecified` are appropriate.</span></span> <span data-ttu-id="77950-110">Dla każdej operacji, można użyć <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu, aby określić, czy praca wykonywana w metodzie powinny być wykonywane w ramach zakresu zakres transakcji, zgodnie z wartością <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="77950-110">For each operation, you can use the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute to specify whether work performed within the method should occur within the scope of a transaction scope according to the value of the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribute.</span></span> <span data-ttu-id="77950-111">W tym przypadku transakcji używane dla `Add` metody jest taka sama jak obowiązkowe transakcji przychodzących, która przepływa między klientem i umożliwiający transakcji `Subtract` metoda jest taki sam jak transakcji, jeśli jeden zostało przekazane klient lub niejawnie, jak i lokalnie utworzono nową transakcję.</span><span class="sxs-lookup"><span data-stu-id="77950-111">In this case, the transaction used for the `Add` method is the same as the mandatory incoming transaction that is flowed from the client, and the transaction used for the `Subtract` method is either the same as the incoming transaction if one was flowed from the client, or a new implicitly and locally created transaction.</span></span>  
  
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
  
3. <span data-ttu-id="77950-112">W pliku konfiguracji, określania, czy kontekst transakcji należy przepływ i protokołów, które ma być używany w tym celu należy skonfigurować powiązania.</span><span class="sxs-lookup"><span data-stu-id="77950-112">Configure the bindings in the configuration file, specifying that the transaction context should be flowed, and the protocols to be used to do so.</span></span> <span data-ttu-id="77950-113">Aby uzyskać więcej informacji, zobacz [Konfiguracja transakcji modelu ServiceModel](servicemodel-transaction-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="77950-113">For more information, see [ServiceModel Transaction Configuration](servicemodel-transaction-configuration.md).</span></span> <span data-ttu-id="77950-114">W szczególności, typ powiązania jest określony w elemencie punktu końcowego `binding` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="77950-114">Specifically, the binding type is specified in the endpoint element’s `binding` attribute.</span></span> <span data-ttu-id="77950-115">[ \<Punktu końcowego >](../../configure-apps/file-schema/wcf/endpoint-element.md) element zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie `transactionalOleTransactionsTcpBinding`, jak pokazano na poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="77950-115">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element contains a `bindingConfiguration` attribute that references a binding configuration named `transactionalOleTransactionsTcpBinding`, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="77950-116">Przepływ transakcji jest włączona na poziomie konfiguracji za pomocą `transactionFlow` atrybut i Protokół transakcji jest określony, przy użyciu `transactionProtocol` atrybutu, jak pokazano na następującej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="77950-116">Transaction flow is enabled at the configuration level by using the `transactionFlow` attribute, and the transaction protocol is specified using the `transactionProtocol` attribute, as shown in the following configuration.</span></span>  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a><span data-ttu-id="77950-117">Obsługa wielu protokołów transakcji</span><span class="sxs-lookup"><span data-stu-id="77950-117">Supporting multiple transaction protocols</span></span>  
  
1. <span data-ttu-id="77950-118">Aby uzyskać optymalną wydajność należy użyć protokołu OleTransactions dla scenariuszy obejmujących klienta i usługi napisane przy użyciu usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="77950-118">For optimal performance, you should use the OleTransactions protocol for scenarios involving a client and service written using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="77950-119">Jednak protokół WS-AtomicTransaction (WS-AT) jest przydatne w scenariuszach, gdy wymagane jest współdziałanie ze stosów protokołu innych firm.</span><span class="sxs-lookup"><span data-stu-id="77950-119">However, the WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span> <span data-ttu-id="77950-120">Można skonfigurować usługi WCF do akceptowania oba protokoły, zapewniając wiele punktów końcowych przy użyciu odpowiednich powiązań związane z protokołem, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="77950-120">You can configure WCF services to accept both protocols by providing multiple endpoints with appropriate protocol-specific bindings, as shown in the following sample configuration.</span></span>  
  
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
  
     <span data-ttu-id="77950-121">Protokół transakcji jest określony, przy użyciu `transactionProtocol` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="77950-121">The transaction protocol is specified using the `transactionProtocol` attribute.</span></span> <span data-ttu-id="77950-122">Jednak ten atrybut jest nieobecne z dostarczanych przez system `wsHttpBinding`, ponieważ to powiązanie można używać tylko protokołu WS-AT.</span><span class="sxs-lookup"><span data-stu-id="77950-122">However, this attribute is absent from the system-provided `wsHttpBinding`, because this binding can only use the WS-AT protocol.</span></span>  
  
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
  
### <a name="controlling-the-completion-of-a-transaction"></a><span data-ttu-id="77950-123">Kontrolowanie ukończenia transakcji</span><span class="sxs-lookup"><span data-stu-id="77950-123">Controlling the completion of a transaction</span></span>  
  
1. <span data-ttu-id="77950-124">Domyślnie operacji WCF automatycznego ukończenia transakcji, jeśli nie nieobsłużone wyjątki są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="77950-124">By default, WCF operations automatically complete transactions if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="77950-125">To zachowanie można zmienić za pomocą <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwości i <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="77950-125">You can modify this behavior by using the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property and the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method.</span></span> <span data-ttu-id="77950-126">Podczas operacji musi występować w tej samej transakcji jako inna operacja (na przykład dla operacji debetowych i środków), można wyłączyć zachowanie automatycznego uzupełniania, ustawiając <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwość `false` jak pokazano w następującym `Debit` przykład operacji.</span><span class="sxs-lookup"><span data-stu-id="77950-126">When an operation is required to occur within the same transaction as another operation (for example, a debit and credit operation), you can disable the autocomplete behavior by setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` as shown in the following `Debit` operation example.</span></span> <span data-ttu-id="77950-127">Transakcji `Debit` używa operacja zakończy się aż do metody z <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwością `true` nosi nazwę, jak pokazano w operacji `Credit1`, lub gdy <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> metoda jest wywoływana, aby wyraźnie oznaczyć jako ukończony, jak pokazano w operacji transakcji `Credit2`.</span><span class="sxs-lookup"><span data-stu-id="77950-127">The transaction the `Debit` operation uses is not completed until a method with the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property set to `true` is called, as shown in the operation `Credit1`, or when the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method is called to explicitly mark the transaction as complete, as shown in the operation `Credit2`.</span></span> <span data-ttu-id="77950-128">Należy pamiętać, że operacje dwóch środki są wyświetlane w celach ilustracyjnych i że pojedynczy środki operacji byłoby bardziej typowego.</span><span class="sxs-lookup"><span data-stu-id="77950-128">Note that the two credit operations are shown for illustration purposes, and that a single credit operation would be more typical.</span></span>  
  
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
  
2. <span data-ttu-id="77950-129">Na potrzeby korelacji transakcji, ustawienie <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> właściwość `false` wymaga użycia sesji powiązania.</span><span class="sxs-lookup"><span data-stu-id="77950-129">For the purposes of transaction correlation, setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` requires the use of a sessionful binding.</span></span> <span data-ttu-id="77950-130">Wymóg ten jest określony za pomocą `SessionMode` właściwość <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="77950-130">This requirement is specified with the `SessionMode` property on the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span>  
  
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a><span data-ttu-id="77950-131">Kontrolowanie okresu istnienia wystąpienia usługi transakcyjnej</span><span class="sxs-lookup"><span data-stu-id="77950-131">Controlling the lifetime of a transactional service instance</span></span>  
  
1. <span data-ttu-id="77950-132">Korzysta z usługi WCF <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> właściwości w celu określenia, czy podstawowe wystąpienie usługi jest wydane po zakończeniu transakcji.</span><span class="sxs-lookup"><span data-stu-id="77950-132">WCF uses the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to specify whether the underlying service instance is released when a transaction completes.</span></span> <span data-ttu-id="77950-133">Ponieważ jest to `true`, chyba że skonfigurowano inaczej, zachowanie aktywacji programu WCF wystawach efektywne i przewidywalne "just-in-time".</span><span class="sxs-lookup"><span data-stu-id="77950-133">Since this defaults to `true`, unless configured otherwise, WCF exhibits an efficient and predictable "just-in-time" activation behavior.</span></span> <span data-ttu-id="77950-134">Wywołań do usługi kolejnych transakcji zapewnione zostaną nowe wystąpienie usługi z nie pozostałości transakcji poprzedniego stanu.</span><span class="sxs-lookup"><span data-stu-id="77950-134">Calls to a service on a subsequent transaction are assured a new service instance with no remnants of the previous transaction's state.</span></span> <span data-ttu-id="77950-135">Chociaż często jest to przydatne, czasami możesz chcieć zarządzania stanem w wystąpieniu usługi poza ukończenia transakcji.</span><span class="sxs-lookup"><span data-stu-id="77950-135">While this is often useful, sometimes you may want to maintain state within the service instance beyond the transaction completion.</span></span> <span data-ttu-id="77950-136">Przykłady tego byłoby w przypadku stanu wymagane lub dojścia do zasobów kosztowne można pobrać lub odtworzenia.</span><span class="sxs-lookup"><span data-stu-id="77950-136">Examples of this would be when required state or handles to resources are expensive to retrieve or reconstitute.</span></span> <span data-ttu-id="77950-137">Można to zrobić, ustawiając <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="77950-137">You can do this by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to `false`.</span></span> <span data-ttu-id="77950-138">Z tym ustawieniem wystąpienie i każdy stan skojarzony będą dostępne w kolejnych wywołaniach.</span><span class="sxs-lookup"><span data-stu-id="77950-138">With that setting, the instance and any associated state will be available on subsequent calls.</span></span> <span data-ttu-id="77950-139">Korzystając z tego, dokładnie rozważyć do kiedy i jak stanu i transakcje zostaną wyczyszczone i zakończone.</span><span class="sxs-lookup"><span data-stu-id="77950-139">When using this, give careful consideration to when and how state and transactions will be cleared and completed.</span></span> <span data-ttu-id="77950-140">W poniższym przykładzie pokazano, jak to zrobić poprzez utrzymywanie wystąpienie z `runningTotal` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="77950-140">The following sample demonstrates how to do this by maintaining the instance with the `runningTotal` variable.</span></span>  
  
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
    >  <span data-ttu-id="77950-141">Ponieważ okres istnienia wystąpienia jest zachowanie wewnętrznych z usługą i kontrolowany za pośrednictwem <xref:System.ServiceModel.ServiceBehaviorAttribute> , nie modyfikacji konfiguracji usługi lub kontraktu usługi jest wymagana właściwość można ustawić zachowanie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="77950-141">Since the instance lifetime is a behavior that is internal to the service, and controlled through the <xref:System.ServiceModel.ServiceBehaviorAttribute> property, no modification to the service configuration or service contract is required to set the instance behavior.</span></span> <span data-ttu-id="77950-142">Ponadto podczas transmisji będzie zawierać nie reprezentację.</span><span class="sxs-lookup"><span data-stu-id="77950-142">In addition, the wire will contain no representation of this.</span></span>
