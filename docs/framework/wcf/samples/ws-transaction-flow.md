---
title: Przepływ transakcji WS
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 781934e9ab27f761e71841c2edc509f9b8022aa7
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094751"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="5f2bf-102">Przepływ transakcji WS</span><span class="sxs-lookup"><span data-stu-id="5f2bf-102">WS Transaction Flow</span></span>
<span data-ttu-id="5f2bf-103">Ten przykład ilustruje użycie transakcji skoordynowanej przez klienta oraz opcji klienta i serwera dla przepływu transakcji przy użyciu protokołu transakcji WS-lub OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="5f2bf-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora, ale operacje są przypisane do zademonstrowania użycia `TransactionFlowAttribute` z wyliczeniem **parametru TransactionFlowOption** w celu określenia, jaki przepływ transakcji jest włączony.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="5f2bf-105">W ramach przetworzonej transakcji dziennik żądanych operacji jest zapisywana w bazie danych i utrzymuje się do momentu ukończenia transakcji skoordynowanej klienta — Jeśli transakcja klienta nie zostanie ukończona, transakcja usługi sieci Web gwarantuje, że odpowiednie aktualizacje bazy danych nie są zatwierdzone.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f2bf-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5f2bf-107">Po zainicjowaniu połączenia z usługą i transakcją klient uzyskuje dostęp do kilku operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="5f2bf-108">Umowa dla usługi jest definiowana w następujący sposób z każdą operacją, która wykazuje inne ustawienia dla `TransactionFlowOption`.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

```csharp
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

 <span data-ttu-id="5f2bf-109">Definiuje operacje w kolejności, w jakiej mają być przetwarzane:</span><span class="sxs-lookup"><span data-stu-id="5f2bf-109">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="5f2bf-110">Żądanie operacji `Add` musi zawierać transakcję przepływaną.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="5f2bf-111">Żądanie operacji `Subtract` może obejmować transakcję przepływaną.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="5f2bf-112">Żądanie operacji `Multiply` nie może zawierać przepływającej transakcji za pomocą jawnego ustawienia nołojud.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="5f2bf-113">Żądanie operacji `Divide` nie może zawierać przepływającej transakcji za pomocą pomijania atrybutu `TransactionFlow`.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="5f2bf-114">Aby włączyć przepływ transakcji, oprócz odpowiednich atrybutów operacji należy użyć powiązań z włączoną właściwością [\<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) .</span><span class="sxs-lookup"><span data-stu-id="5f2bf-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="5f2bf-115">W tym przykładzie konfiguracja usługi uwidacznia punkt końcowy protokołu TCP i punkt końcowy HTTP oprócz punktu końcowego wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="5f2bf-116">Punkt końcowy TCP i punkt końcowy HTTP używają następujących powiązań, z których oba mają włączoną właściwość [\<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) .</span><span class="sxs-lookup"><span data-stu-id="5f2bf-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
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
> <span data-ttu-id="5f2bf-117">NetTcpBinding udostępnione przez system umożliwia specyfikację element TransactionProtocol, podczas gdy w przypadku systemu wsHttpBinding jest wykorzystywany tylko bardziej międzyoperacyjny protokół WSAtomicTransactionOctober2004.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="5f2bf-118">Protokół OleTransactions jest dostępny tylko dla klientów Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5f2bf-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="5f2bf-119">Dla klasy implementującej interfejs `ICalculator` wszystkie metody są przypisane do właściwości <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> ustawionej na `true`.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="5f2bf-120">To ustawienie deklaruje, że wszystkie akcje podjęte w ramach metody są wykonywane w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="5f2bf-121">W takim przypadku wykonane działania obejmują rejestrowanie do bazy danych dziennika.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="5f2bf-122">Jeśli żądanie operacji obejmuje przetworzoną transakcję, akcje są wykonywane w ramach zakresu transakcji przychodzącej lub automatycznie generowane są nowe zakresy transakcji.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f2bf-123">Właściwość <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> definiuje zachowanie lokalne dla implementacji metod usługi i nie definiuje możliwości lub wymagania dotyczącego przepływania transakcji przez klienta.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

```csharp
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

 <span data-ttu-id="5f2bf-124">W przypadku klienta ustawienia `TransactionFlowOption` usługi dla operacji są odzwierciedlane w wygenerowanej definicji klienta interfejsu `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="5f2bf-125">Ponadto ustawienia właściwości `transactionFlow` usługi są odzwierciedlone w konfiguracji aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="5f2bf-126">Klient może wybrać transport i protokół, wybierając odpowiednie `endpointConfigurationName`.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> <span data-ttu-id="5f2bf-127">Obserwowane zachowanie tego przykładu jest takie samo, niezależnie od tego, który protokół lub transport jest wybierany.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="5f2bf-128">Po zainicjowaniu połączenia z usługą Klient tworzy nowy `TransactionScope` wokół wywołań operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

```csharp
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

 <span data-ttu-id="5f2bf-129">Wywołania operacji są następujące:</span><span class="sxs-lookup"><span data-stu-id="5f2bf-129">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="5f2bf-130">Żądanie `Add` przeprowadzi transakcję wymaganą przez usługę, a akcje usługi są wykonywane w zakresie transakcji klienta.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="5f2bf-131">Pierwsze żądanie `Subtract` również przepływie dozwolonej transakcji do usługi, a następnie akcje usługi są wykonywane w zakresie transakcji klienta.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="5f2bf-132">Drugie żądanie `Subtract` jest wykonywane w ramach nowego zakresu transakcji zadeklarowanego za pomocą opcji `TransactionScopeOption.Suppress`.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="5f2bf-133">Pomija to początkową transakcję klienta i żądanie nie powoduje przepływania transakcji do usługi.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="5f2bf-134">Takie podejście pozwala klientowi jawnie zrezygnować z usługi i chronić ją przed przepływaniem transakcji w usłudze, gdy nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="5f2bf-135">Akcje usługi są wykonywane w zakresie nowej i niepołączonej transakcji.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="5f2bf-136">Żądanie `Multiply` nie przepływ transakcji do usługi, ponieważ wygenerowana definicja interfejsu `ICalculator` przez klienta zawiera <xref:System.ServiceModel.TransactionFlowAttribute> ustawioną <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="5f2bf-137">Żądanie `Divide` nie powoduje przepływania transakcji do usługi, ponieważ wywygenerowana przez klienta definicja interfejsu `ICalculator` nie zawiera `TransactionFlowAttribute`.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="5f2bf-138">Akcje usługi są ponownie wykonywane w zakresie innej nowej i niepołączonej transakcji.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="5f2bf-139">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5f2bf-140">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-140">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
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
  
 <span data-ttu-id="5f2bf-141">Rejestrowanie żądań operacji usługi jest wyświetlane w oknie konsoli usługi.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="5f2bf-142">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="5f2bf-143">Po pomyślnym wykonaniu zakres transakcji klienta zostaje zakończony i wszystkie akcje podjęte w ramach tego zakresu zostaną zatwierdzone.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="5f2bf-144">W odróżnieniu od 5 rekordów w bazie danych usługi są utrwalane.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="5f2bf-145">Pierwsze 2 z nich wystąpiło w zakresie transakcji klienta.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="5f2bf-146">Jeśli wystąpi wyjątek w dowolnym miejscu w `TransactionScope` klienta, nie można ukończyć transakcji.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="5f2bf-147">Powoduje to, że rekordy zarejestrowane w tym zakresie nie są zatwierdzone do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="5f2bf-148">Ten efekt można zaobserwować przez powtórzenie przykładowego przebiegu po wprowadzeniu komentarza do wywołania `TransactionScope`zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="5f2bf-149">W takim przebiegu są rejestrowane tylko ostatnie 3 akcje (od drugiego `Subtract`, `Multiply` i `Divide` żądania), ponieważ transakcja klienta nie przepływa do tych.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5f2bf-150">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="5f2bf-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5f2bf-151">Aby skompilować wersję C# rozwiązania lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)</span><span class="sxs-lookup"><span data-stu-id="5f2bf-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="5f2bf-152">Upewnij się, że masz zainstalowaną wersję SQL Server Express lub SQL Server i że parametry połączenia zostały prawidłowo ustawione w pliku konfiguracyjnym aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="5f2bf-153">Aby uruchomić przykład bez korzystania z bazy danych, ustaw wartość `usingSql` w pliku konfiguracyjnym aplikacji usługi na `false`</span><span class="sxs-lookup"><span data-stu-id="5f2bf-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="5f2bf-154">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5f2bf-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5f2bf-155">W przypadku konfiguracji między maszynami Włącz Distributed Transaction Coordinator przy użyciu poniższych instrukcji i użyj narzędzia WsatConfig. exe z Windows SDK, aby włączyć obsługę transakcji WCF w sieci.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="5f2bf-156">Aby uzyskać informacje na temat konfigurowania programu WsatConfig. exe, zobacz [Konfigurowanie obsługi transakcji WS-AT](../feature-details/configuring-ws-atomic-transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="5f2bf-156">For information on setting up WsatConfig.exe, see [Configuring WS-Atomic Transaction Support](../feature-details/configuring-ws-atomic-transaction-support.md).</span></span>  
  
 <span data-ttu-id="5f2bf-157">Bez względu na to, czy uruchamiasz przykład na tym samym komputerze, czy na różnych komputerach, należy skonfigurować usługę Microsoft Distributed Transaction Coordinator (MSDTC) w celu włączenia przepływu transakcji sieci i użyć narzędzia WsatConfig. exe, aby włączyć obsługę sieci transakcji WCF.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="5f2bf-158">Aby skonfigurować Distributed Transaction Coordinator firmy Microsoft (MSDTC) do obsługi uruchamiania przykładu</span><span class="sxs-lookup"><span data-stu-id="5f2bf-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="5f2bf-159">Na maszynie usługi z systemem Windows Server 2003 lub Windows XP Skonfiguruj usługę MSDTC tak, aby zezwalała na przychodzące transakcje sieciowe, wykonując te instrukcje.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="5f2bf-160">W menu **Start** przejdź do **Panelu sterowania**, a następnie **Narzędzia administracyjne**, a następnie **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="5f2bf-161">Rozwiń węzeł **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-161">Expand **Component Services**.</span></span> <span data-ttu-id="5f2bf-162">Otwórz folder **komputery** .</span><span class="sxs-lookup"><span data-stu-id="5f2bf-162">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="5f2bf-163">Kliknij prawym przyciskiem myszy pozycję **mój komputer** , a następnie wybierz pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="5f2bf-164">Na karcie **MSDTC** kliknij pozycję **Konfiguracja zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="5f2bf-165">Sprawdź **dostęp do usługi Network DTC** i **Zezwalaj na ruch przychodzący**.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="5f2bf-166">Kliknij przycisk **OK**, a następnie kliknij przycisk **tak** , aby ponownie uruchomić usługę MSDTC.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="5f2bf-167">Kliknij przycisk **OK**, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-167">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="5f2bf-168">Na maszynie usługi z systemem Windows Server 2008 lub Windows Vista Skonfiguruj usługę MSDTC tak, aby zezwalała na przychodzące transakcje sieciowe, wykonując te instrukcje.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="5f2bf-169">W menu **Start** przejdź do **Panelu sterowania**, a następnie **Narzędzia administracyjne**, a następnie **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="5f2bf-170">Rozwiń węzeł **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-170">Expand **Component Services**.</span></span> <span data-ttu-id="5f2bf-171">Otwórz folder **komputery** .</span><span class="sxs-lookup"><span data-stu-id="5f2bf-171">Open the **Computers** folder.</span></span> <span data-ttu-id="5f2bf-172">Wybierz **Distributed Transaction Coordinator**.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="5f2bf-173">Kliknij prawym przyciskiem myszy pozycję **koordynator usługi DTC** i wybierz pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="5f2bf-174">Na karcie **zabezpieczenia** Sprawdź **dostęp do usługi Network DTC** i **Zezwalaj na ruch przychodzący**.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="5f2bf-175">Kliknij przycisk **OK**, a następnie kliknij przycisk **tak** , aby ponownie uruchomić usługę MSDTC.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="5f2bf-176">Kliknij przycisk **OK**, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-176">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="5f2bf-177">Na komputerze klienckim Skonfiguruj usługę MSDTC tak, aby zezwalała na wychodzące transakcje sieciowe:</span><span class="sxs-lookup"><span data-stu-id="5f2bf-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="5f2bf-178">W menu **Start** przejdź do `Control Panel`, następnie **Narzędzia administracyjne**, a następnie pozycję **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="5f2bf-179">Kliknij prawym przyciskiem myszy pozycję **mój komputer** , a następnie wybierz pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="5f2bf-180">Na karcie **MSDTC** kliknij pozycję **Konfiguracja zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="5f2bf-181">Sprawdź **dostęp do usługi Network DTC** i **Zezwalaj na ruch wychodzący**.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="5f2bf-182">Kliknij przycisk **OK**, a następnie kliknij przycisk **tak** , aby ponownie uruchomić usługę MSDTC.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="5f2bf-183">Kliknij przycisk **OK**, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5f2bf-184">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5f2bf-185">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="5f2bf-185">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="5f2bf-186">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5f2bf-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5f2bf-187">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5f2bf-187">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
