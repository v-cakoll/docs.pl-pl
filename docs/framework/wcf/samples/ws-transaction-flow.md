---
title: "Przepływ transakcji WS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bf441831a205b022899999b1bf34e1505b8fb6bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="fec38-102">Przepływ transakcji WS</span><span class="sxs-lookup"><span data-stu-id="fec38-102">WS Transaction Flow</span></span>
<span data-ttu-id="fec38-103">W tym przykładzie przedstawiono użycie transakcji koordynowane przez klienta i opcji na kliencie i serwerze dla transakcji przepływu przy użyciu protokołu WS-Atomic Transaction albo OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="fec38-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="fec38-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator, ale operacje są przypisane do przedstawiają sposób używania `TransactionFlowAttribute` z **właściwość TransactionFlowOption** wyliczenie, aby ustalić, jakie transakcji stopnia przepływu jest włączone.</span><span class="sxs-lookup"><span data-stu-id="fec38-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="fec38-105">W zakresie transakcji dziennik żądanych operacji są zapisywane do bazy danych i będzie się powtarzał dopiero po ukończeniu transakcji klienta koordynowane — Jeśli transakcja klienta nie zostanie ukończone, transakcja usługi sieci Web zapewnia, że odpowiednie aktualizacje bazy danych nie są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="fec38-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fec38-106">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="fec38-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fec38-107">Po zainicjowaniu połączenia usługi i transakcji, klient uzyskuje dostęp do wielu operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="fec38-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="fec38-108">Kontrakt usługi jest zdefiniowana w następujący sposób z każdej operacji prezentacja inne ustawienie `TransactionFlowOption`.</span><span class="sxs-lookup"><span data-stu-id="fec38-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);   
}  
```  
  
 <span data-ttu-id="fec38-109">Definiuje operacje w kolejności, które mają być przetwarzane:</span><span class="sxs-lookup"><span data-stu-id="fec38-109">This defines the operations in the order they are to be processed:</span></span>  
  
-   <span data-ttu-id="fec38-110">`Add` Żądanie operacji musi zawierać przesłanej transakcji.</span><span class="sxs-lookup"><span data-stu-id="fec38-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
-   <span data-ttu-id="fec38-111">A `Subtract` żądanie operacji mogą obejmować przesłanej transakcji.</span><span class="sxs-lookup"><span data-stu-id="fec38-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
-   <span data-ttu-id="fec38-112">A `Multiply` żądanie operacji nie może zawierać przesłanej transakcji przez jawne ustawienie NotAllowed.</span><span class="sxs-lookup"><span data-stu-id="fec38-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
-   <span data-ttu-id="fec38-113">A `Divide` żądanie operacji nie może zawierać przesłanej transakcji przez pominięcie `TransactionFlow` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="fec38-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="fec38-114">Aby włączyć przepływu transakcji, powiązania z [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) właściwość włączone, należy użyć oprócz atrybutów odpowiednie działania.</span><span class="sxs-lookup"><span data-stu-id="fec38-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="fec38-115">W tym przykładzie konfiguracji usługi przedstawia punktu końcowego TCP i punkt końcowy HTTP oprócz punkt końcowy wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="fec38-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="fec38-116">Punkt końcowy protokołu TCP i punkt końcowy HTTP należy użyć następujących powiązania, które mają [ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) właściwości włączone.</span><span class="sxs-lookup"><span data-stu-id="fec38-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="fec38-117">NetTcpBinding dostarczane przez system umożliwia specyfikacji element transactionProtocol, natomiast wsHttpBinding dostarczane przez system używa tylko więcej współdziałanie protokołu WSAtomicTransactionOctober2004.</span><span class="sxs-lookup"><span data-stu-id="fec38-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="fec38-118">Protokołu OleTransactions jest dostępna tylko na użytek [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klientów.</span><span class="sxs-lookup"><span data-stu-id="fec38-118">The OleTransactions protocol is only available for use by [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] clients.</span></span>  
  
 <span data-ttu-id="fec38-119">Dla klasy implementującej `ICalculator` interfejsu, wszystkie metody atrybut z <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> ustawioną właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="fec38-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="fec38-120">To ustawienie deklaruje, że wszystkie akcje wykonywane w metodzie występuje w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="fec38-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="fec38-121">W takim przypadku akcje wykonywane obejmują rejestrowanie do dziennika bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fec38-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="fec38-122">Jeśli żądanie operacji zawiera przesłanej transakcji zachodzą akcje w zakresie transakcji przychodzącej lub nowego zakresu transakcji są generowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="fec38-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fec38-123"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> Właściwość definiuje zachowanie lokalnej do implementacji metody usługi i nie definiuje możliwość klienta lub wymaganie przepływu transakcji.</span><span class="sxs-lookup"><span data-stu-id="fec38-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  
  
```  
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```  
  
 <span data-ttu-id="fec38-124">Na klienta, usługa `TransactionFlowOption` ustawień na operacje są uwzględniane w definicji wygenerowanego klienta `ICalculator` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fec38-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="fec38-125">Ponadto usługi `transactionFlow` ustawienia właściwości są uwzględniane w konfiguracji aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="fec38-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="fec38-126">Klient może wybrać transportu i protokół przez wybranie odpowiedniej `endpointConfigurationName`.</span><span class="sxs-lookup"><span data-stu-id="fec38-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  
  
```  
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```  
  
> [!NOTE]
>  <span data-ttu-id="fec38-127">Obserwowanych zachowanie w tym przykładzie jest taka sama niezależnie od tego, który jest wybierany protokołu lub transportu.</span><span class="sxs-lookup"><span data-stu-id="fec38-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="fec38-128">Po zainicjowaniu połączenia z usługą Klient tworzy nową `TransactionScope` wokół wywołania do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="fec38-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  
  
```  
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```  
  
 <span data-ttu-id="fec38-129">Wywołania do operacji są następujące:</span><span class="sxs-lookup"><span data-stu-id="fec38-129">The calls to the operations are as follows:</span></span>  
  
-   <span data-ttu-id="fec38-130">`Add` Żądania przepływu transakcji wymagane do usługi i są wykonywane działania usługi w zakresie transakcji klienta.</span><span class="sxs-lookup"><span data-stu-id="fec38-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
-   <span data-ttu-id="fec38-131">Pierwszy `Subtract` żądania przepływa również dozwolonych transakcji do usługi i ponownie wykonywane działania usługi w zakresie transakcji klienta.</span><span class="sxs-lookup"><span data-stu-id="fec38-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
-   <span data-ttu-id="fec38-132">Drugi `Subtract` żądania odbywa się w zakresie nowych transakcji zadeklarowana z `TransactionScopeOption.Suppress` opcji.</span><span class="sxs-lookup"><span data-stu-id="fec38-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="fec38-133">Pomija to początkowa transakcji zewnętrznej klienta i żądania nie przepływu transakcji z usługą.</span><span class="sxs-lookup"><span data-stu-id="fec38-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="fec38-134">Takie podejście umożliwia klientowi jawnie zrezygnować z i chronić przepływu transakcji do usługi, po którym nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="fec38-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="fec38-135">Akcje usługi występuje w zakresie nowych i odłączony transakcji.</span><span class="sxs-lookup"><span data-stu-id="fec38-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
-   <span data-ttu-id="fec38-136">`Multiply` Żądania nie przepływu transakcji do usługi, ponieważ klient obiektu wygenerowana definicji `ICalculator` interfejs zawiera <xref:System.ServiceModel.TransactionFlowAttribute> ustawioną <xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`.</span><span class="sxs-lookup"><span data-stu-id="fec38-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
-   <span data-ttu-id="fec38-137">`Divide` Żądania nie przepływu transakcji do usługi, ponieważ ponownie klienta do wygenerowanych definicji `ICalculator` nie ma interfejsu `TransactionFlowAttribute`.</span><span class="sxs-lookup"><span data-stu-id="fec38-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="fec38-138">W zakresie nowych i odłączony transakcja wykonywane ponownie działania usługi.</span><span class="sxs-lookup"><span data-stu-id="fec38-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="fec38-139">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="fec38-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fec38-140">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="fec38-140">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="fec38-141">Rejestrowanie żądań operacji usługi są wyświetlane w oknie konsoli usługi.</span><span class="sxs-lookup"><span data-stu-id="fec38-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="fec38-142">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="fec38-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="fec38-143">Po pomyślnym wykonaniu kończy zakresu transakcji klienta, a wszystkie akcje wykonywane w ramach tego zakresu są zatwierdzone.</span><span class="sxs-lookup"><span data-stu-id="fec38-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="fec38-144">W szczególności dostrzeżone 5 rekordów są zachowywane w bazie danych usługi.</span><span class="sxs-lookup"><span data-stu-id="fec38-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="fec38-145">Pierwsze 2 one wystąpiły w zakresie transakcji klienta.</span><span class="sxs-lookup"><span data-stu-id="fec38-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="fec38-146">Jeśli wystąpił wyjątek dowolne miejsce w ramach klienta `TransactionScope` , a następnie nie może ukończyć transakcji.</span><span class="sxs-lookup"><span data-stu-id="fec38-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="fec38-147">Powoduje to, że rekordy zarejestrowane w ramach tego zakresu, które mają nie być przekazane do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fec38-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="fec38-148">W tym celu można zaobserwować, powtarzając próbki po komentowania limit wywołania do wykonania zewnętrznego `TransactionScope`.</span><span class="sxs-lookup"><span data-stu-id="fec38-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="fec38-149">Takie uruchomieniu tylko ostatnich 3 akcje (od drugiego `Subtract`, `Multiply` i `Divide` żądań) są rejestrowane, ponieważ transakcja klienta nie przepływać do tych.</span><span class="sxs-lookup"><span data-stu-id="fec38-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fec38-150">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="fec38-150">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fec38-151">Aby utworzyć wersję języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)</span><span class="sxs-lookup"><span data-stu-id="fec38-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2.  <span data-ttu-id="fec38-152">Upewnij się, że zainstalowano program SQL Server Express Edition lub SQL Server i czy ciąg połączenia został poprawnie ustawiony w pliku konfiguracyjnym aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="fec38-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="fec38-153">Aby uruchomić przykładowy bez korzystania z bazy danych, ustaw `usingSql` wartości w pliku konfiguracyjnym aplikacji usługi do`false`</span><span class="sxs-lookup"><span data-stu-id="fec38-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3.  <span data-ttu-id="fec38-154">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fec38-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fec38-155">Do konfiguracji między komputerami Włącz Koordynator transakcji rozproszonych, korzystając z poniższych instrukcji, a narzędzie WsatConfig.exe z zestawu Windows SDK, aby włączyć obsługę sieci transakcji WCF.</span><span class="sxs-lookup"><span data-stu-id="fec38-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="fec38-156">Zobacz [Konfigurowanie obsługi transakcji protokołu WS-AT](http://go.microsoft.com/fwlink/?LinkId=190370) informacji na temat konfigurowania WsatConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="fec38-156">See [Configuring WS-Atomic Transaction Support](http://go.microsoft.com/fwlink/?LinkId=190370) for information on setting up WsatConfig.exe.</span></span>  
  
 <span data-ttu-id="fec38-157">Czy można uruchomić przykład na tym samym komputerze lub na różnych komputerach, należy skonfigurować MSDTC Microsoft Distributed Transaction Coordinator () do włączenia przepływu transakcji sieci i włączyć za pomocą narzędzia WsatConfig.exe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transakcji Obsługa sieci.</span><span class="sxs-lookup"><span data-stu-id="fec38-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="fec38-158">Aby skonfigurować MSDTC Microsoft Distributed Transaction Coordinator () do obsługi systemem próbki</span><span class="sxs-lookup"><span data-stu-id="fec38-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1.  <span data-ttu-id="fec38-159">Na maszynie usługi z systemem Windows Server 2003 lub Windows XP należy skonfigurować usługi MSDTC umożliwia przychodzących transakcji sieci, wykonując następujące instrukcje.</span><span class="sxs-lookup"><span data-stu-id="fec38-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1.  <span data-ttu-id="fec38-160">Z **Start** menu, przejdź do **Panelu sterowania**, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="fec38-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="fec38-161">Rozwiń węzeł **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="fec38-161">Expand **Component Services**.</span></span> <span data-ttu-id="fec38-162">Otwórz **komputery** folderu.</span><span class="sxs-lookup"><span data-stu-id="fec38-162">Open the **Computers** folder.</span></span>  
  
    3.  <span data-ttu-id="fec38-163">Kliknij prawym przyciskiem myszy **Mój komputer** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fec38-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4.  <span data-ttu-id="fec38-164">Na **MSDTC** , kliknij pozycję **konfiguracji zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="fec38-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5.  <span data-ttu-id="fec38-165">Sprawdź **sieci dostęp do usługi DTC** i **Zezwalaj na przychodzące**.</span><span class="sxs-lookup"><span data-stu-id="fec38-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6.  <span data-ttu-id="fec38-166">Kliknij przycisk **OK**, następnie kliknij przycisk **tak** ponowne uruchomienie usługi MSDTC.</span><span class="sxs-lookup"><span data-stu-id="fec38-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7.  <span data-ttu-id="fec38-167">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="fec38-167">Click **OK** to close the dialog box.</span></span>  
  
2.  <span data-ttu-id="fec38-168">Na maszynie usługi z systemem Windows Server 2008 lub Windows Vista należy skonfigurować usługi MSDTC umożliwia przychodzących transakcji sieci, wykonując następujące instrukcje.</span><span class="sxs-lookup"><span data-stu-id="fec38-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1.  <span data-ttu-id="fec38-169">Z **Start** menu, przejdź do **Panelu sterowania**, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="fec38-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="fec38-170">Rozwiń węzeł **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="fec38-170">Expand **Component Services**.</span></span> <span data-ttu-id="fec38-171">Otwórz **komputery** folderu.</span><span class="sxs-lookup"><span data-stu-id="fec38-171">Open the **Computers** folder.</span></span> <span data-ttu-id="fec38-172">Wybierz **Koordynator transakcji rozproszonych**.</span><span class="sxs-lookup"><span data-stu-id="fec38-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3.  <span data-ttu-id="fec38-173">Kliknij prawym przyciskiem myszy **koordynator usługi DTC** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fec38-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4.  <span data-ttu-id="fec38-174">Na **zabezpieczeń** karcie wyboru **usługa DTC Network Access** i **Zezwalaj na przychodzące**.</span><span class="sxs-lookup"><span data-stu-id="fec38-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5.  <span data-ttu-id="fec38-175">Kliknij przycisk **OK**, następnie kliknij przycisk **tak** ponowne uruchomienie usługi MSDTC.</span><span class="sxs-lookup"><span data-stu-id="fec38-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6.  <span data-ttu-id="fec38-176">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="fec38-176">Click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="fec38-177">Na komputerze klienckim należy skonfigurować usługi MSDTC, aby umożliwić wychodzących transakcji sieci:</span><span class="sxs-lookup"><span data-stu-id="fec38-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1.  <span data-ttu-id="fec38-178">Z **Start** menu, przejdź do `Control Panel`, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="fec38-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="fec38-179">Kliknij prawym przyciskiem myszy **Mój komputer** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fec38-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="fec38-180">Na **MSDTC** , kliknij pozycję **konfiguracji zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="fec38-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="fec38-181">Sprawdź **sieci dostęp do usługi DTC** i **Zezwalaj na wychodzące**.</span><span class="sxs-lookup"><span data-stu-id="fec38-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5.  <span data-ttu-id="fec38-182">Kliknij przycisk **OK**, następnie kliknij przycisk **tak** ponowne uruchomienie usługi MSDTC.</span><span class="sxs-lookup"><span data-stu-id="fec38-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6.  <span data-ttu-id="fec38-183">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="fec38-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fec38-184">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fec38-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fec38-185">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fec38-185">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fec38-186">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="fec38-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fec38-187">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fec38-187">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
