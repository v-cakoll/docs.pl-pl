---
title: Zachowanie transakcji usługi
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: 69f65ca833dc9a0f719541733be9e6066db37f6e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858112"
---
# <a name="service-transaction-behavior"></a><span data-ttu-id="5a927-102">Zachowanie transakcji usługi</span><span class="sxs-lookup"><span data-stu-id="5a927-102">Service Transaction Behavior</span></span>
<span data-ttu-id="5a927-103">Niniejszy przykład pokazuje użycie transakcji koordynowane przez klienta i ustawień ServiceBehaviorAttribute i gdy, aby kontrolować zachowanie transakcji usługi.</span><span class="sxs-lookup"><span data-stu-id="5a927-103">This sample demonstrates the use of a client-coordinated transaction and the settings of ServiceBehaviorAttribute and OperationBehaviorAttribute to control service transaction behavior.</span></span> <span data-ttu-id="5a927-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementuje usługi Kalkulator, ale jest rozszerzony do obsługi operacji wykonywanych w tabeli bazy danych i stanowe, Suma operacji Kalkulator dziennika serwera.</span><span class="sxs-lookup"><span data-stu-id="5a927-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service, but is extended to maintain a server log of the performed operations in a database table and a stateful running total for the calculator operations.</span></span> <span data-ttu-id="5a927-105">Utrwalonych zapisy do tabeli dziennika serwera są zależne od wyniku transakcji klienta koordynowany — Jeśli transakcja klienta nie zostanie ukończone, transakcji usługi sieci Web zapewnia aktualizacji do bazy danych nie są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="5a927-105">Persisted writes to the server log table are dependent upon the outcome of a client coordinated transaction - if the client transaction does not complete, the Web service transaction ensures that the updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a927-106">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5a927-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5a927-107">Kontrakt usługi określa, że wszystkie operacje wymagają przepływu za pomocą żądań transakcji:</span><span class="sxs-lookup"><span data-stu-id="5a927-107">The contract for the service defines that all of the operations require a transaction to be flowed with requests:</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples",  
                    SessionMode = SessionMode.Required)]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Subtract(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Multiply(double n);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Divide(double n);  
}  
```  
  
 <span data-ttu-id="5a927-108">Aby umożliwić ruch przychodzący transakcji, usługa jest skonfigurowana z wsHttpBinding dostarczane przez system za pomocą atrybutu transactionFlow równa `true`.</span><span class="sxs-lookup"><span data-stu-id="5a927-108">To enable the incoming transaction flow, the service is configured with the system-provided wsHttpBinding with the transactionFlow attribute set to `true`.</span></span> <span data-ttu-id="5a927-109">Międzyoperacyjne protokołu WSAtomicTransactionOctober2004 używa tego powiązania:</span><span class="sxs-lookup"><span data-stu-id="5a927-109">This binding uses the interoperable WSAtomicTransactionOctober2004 protocol:</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="5a927-110">Po zainicjowaniu zarówno połączenia usługi i transakcji, klient uzyskuje dostęp do kilku operacji usługi w zakresie transakcji wykonuje transakcję i zamyka połączenie:</span><span class="sxs-lookup"><span data-stu-id="5a927-110">After initiating both a connection to the service and a transaction, the client accesses several service operations within the scope of that transaction and then completes the transaction and closes the connection:</span></span>  
  
```  
// Create a client  
CalculatorClient client = new CalculatorClient();  
  
// Create a transaction scope with the default isolation level of Serializable  
using (TransactionScope tx = new TransactionScope())  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation.  
    double value = 100.00D;  
    Console.WriteLine("  Adding {0}, running total={1}",  
                                        value, client.Add(value));  
  
    // Call the Subtract service operation.  
    value = 45.00D;  
    Console.WriteLine("  Subtracting {0}, running total={1}",  
                                        value, client.Subtract(value));  
  
    // Call the Multiply service operation.  
    value = 9.00D;  
    Console.WriteLine("  Multiplying by {0}, running total={1}",  
                                        value, client.Multiply(value));  
  
    // Call the Divide service operation.  
    value = 15.00D;  
    Console.WriteLine("  Dividing by {0}, running total={1}",  
                                        value, client.Divide(value));  
  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
  
// Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
 <span data-ttu-id="5a927-111">W usłudze istnieją trzy atrybuty, które wpływają na zachowanie transakcji usługi i mogą to zrobić w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5a927-111">On the service, there are three attributes that affect the service transaction behavior, and they do so in the following ways:</span></span>  
  
-   <span data-ttu-id="5a927-112">Na `ServiceBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="5a927-112">On the `ServiceBehaviorAttribute`:</span></span>  
  
    -   <span data-ttu-id="5a927-113">`TransactionTimeout` Właściwości określa okres czasu, w którym należy wykonać transakcję.</span><span class="sxs-lookup"><span data-stu-id="5a927-113">The `TransactionTimeout` property specifies the time period within which a transaction must complete.</span></span> <span data-ttu-id="5a927-114">W tym przykładzie jest ustawiona na 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="5a927-114">In this sample it is set to 30 seconds.</span></span>  
  
    -   <span data-ttu-id="5a927-115">`TransactionIsolationLevel` Właściwość określa poziom izolacji, który obsługuje usługę.</span><span class="sxs-lookup"><span data-stu-id="5a927-115">The `TransactionIsolationLevel` property specifies the isolation level that the service supports.</span></span> <span data-ttu-id="5a927-116">Jest to wymagane, aby dopasować poziom izolacji klienta.</span><span class="sxs-lookup"><span data-stu-id="5a927-116">This is required to match the client's isolation level.</span></span>  
  
    -   <span data-ttu-id="5a927-117">`ReleaseServiceInstanceOnTransactionComplete` Właściwość określa, czy wystąpienie usługi zostanie odtworzony po zakończeniu transakcji.</span><span class="sxs-lookup"><span data-stu-id="5a927-117">The `ReleaseServiceInstanceOnTransactionComplete` property specifies whether the service instance is recycled when a transaction completes.</span></span> <span data-ttu-id="5a927-118">Ustawiając wartość `false`, usługa zapewnia tego samego wystąpienia usługi przez żądania operacji.</span><span class="sxs-lookup"><span data-stu-id="5a927-118">By setting it to `false`, the service maintains the same service instance across the operation requests.</span></span> <span data-ttu-id="5a927-119">Jest to wymagane, aby zachować łączna liczba uruchomionych.</span><span class="sxs-lookup"><span data-stu-id="5a927-119">This is required to maintain the running total.</span></span> <span data-ttu-id="5a927-120">Jeśli ustawiono `true`, nowe wystąpienie jest generowany po wykonaniu każdej akcji.</span><span class="sxs-lookup"><span data-stu-id="5a927-120">If set to `true`, a new instance is generated after each completed action.</span></span>  
  
    -   <span data-ttu-id="5a927-121">`TransactionAutoCompleteOnSessionClose` Właściwość określa, czy zaległe transakcje odbywa się po zamknięciu sesji.</span><span class="sxs-lookup"><span data-stu-id="5a927-121">The `TransactionAutoCompleteOnSessionClose` property specifies whether outstanding transactions are completed when the session closes.</span></span> <span data-ttu-id="5a927-122">Ustawiając wartość `false`, poszczególnych operacji są wymagane do któryś zbiór `OperationBehaviorAttribute``TransactionAutoComplete` właściwości `true` lub jawnie wymaga wywołania `SetTransactionComplete` metody do realizowania transakcji.</span><span class="sxs-lookup"><span data-stu-id="5a927-122">By setting it to `false`, the individual operations are required to either set the `OperationBehaviorAttribute``TransactionAutoComplete` property to `true` or to explicitly require a call to the `SetTransactionComplete` method to complete transactions.</span></span> <span data-ttu-id="5a927-123">W przykładzie pokazano oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="5a927-123">This sample demonstrates both approaches.</span></span>  
  
-   <span data-ttu-id="5a927-124">Na `ServiceContractAttribute`:</span><span class="sxs-lookup"><span data-stu-id="5a927-124">On the `ServiceContractAttribute`:</span></span>  
  
    -   <span data-ttu-id="5a927-125">`SessionMode` Właściwość określa, czy usługa jest skorelowane odpowiednich żądań do sesji logicznej.</span><span class="sxs-lookup"><span data-stu-id="5a927-125">The `SessionMode` property specifies whether the service correlates the appropriate requests into a logical session.</span></span> <span data-ttu-id="5a927-126">Ponieważ ta usługa obejmuje operacje, w których ustawiono właściwość wartość gdy TransactionAutoComplete `false` mnożenia i dzielenia, `SessionMode.Required` musi być określona.</span><span class="sxs-lookup"><span data-stu-id="5a927-126">Because this service includes operations where the OperationBehaviorAttribute TransactionAutoComplete property is set to `false` (Multiply and Divide), `SessionMode.Required` must be specified.</span></span> <span data-ttu-id="5a927-127">Na przykład mnożenie operacji transakcji nie zostanie zakończone i zamiast tego opiera się na nowszych wywołanie dzielenia można wykonać przy użyciu `SetTransactionComplete` metody; usługa musi być możliwe ustalenie, czy te operacje są wykonywane w ramach tej samej sesji.</span><span class="sxs-lookup"><span data-stu-id="5a927-127">For example, the Multiply operation does not complete its transaction and instead relies upon a later call to Divide to complete using the `SetTransactionComplete` method; the service must be able to determine that these operations are occurring within the same session.</span></span>  
  
-   <span data-ttu-id="5a927-128">Na `OperationBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="5a927-128">On the `OperationBehaviorAttribute`:</span></span>  
  
    -   <span data-ttu-id="5a927-129">`TransactionScopeRequired` Właściwość określa, czy wykonać operację akcji powinny być wykonywane w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="5a927-129">The `TransactionScopeRequired` property specifies whether the operation's actions should be executed within a transaction scope.</span></span> <span data-ttu-id="5a927-130">Jest ono ustawione na `true` dla wszystkich operacji w tym przykładowy i, ponieważ klient przepływy transakcji do wszystkich operacji, w zakresie transakcji klienta mają być wykonywane akcje.</span><span class="sxs-lookup"><span data-stu-id="5a927-130">This is set to `true` for all operations in this sample and, because the client flows its transaction to all operations, the actions occur within the scope of that client transaction.</span></span>  
  
    -   <span data-ttu-id="5a927-131">`TransactionAutoComplete` Właściwość określa, czy transakcji, w którym metoda jest wykonywana jest wprowadzana automatycznie, jeśli wystąpi żaden nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5a927-131">The `TransactionAutoComplete` property specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions occur.</span></span> <span data-ttu-id="5a927-132">Jak opisano wcześniej, jest ono ustawione na `true` operacji dodawania i odejmowania, ale `false` Multiply i operacji dzielenia.</span><span class="sxs-lookup"><span data-stu-id="5a927-132">As previously described, this is set to `true` for the Add and Subtract operations but `false` for the Multiply and Divide operations.</span></span> <span data-ttu-id="5a927-133">Automatyczne ukończenie operacji dodawania i odejmowania ich działania, dzielenia ukończeniu akcji za pomocą jawnego wywołania `SetTransactionComplete` metoda Multiply swoje działania nie zostanie ukończone, ale zamiast tego opiera się na i wymaga nowszej wywołanie, takich jak Podziel do wykonania akcji.</span><span class="sxs-lookup"><span data-stu-id="5a927-133">The Add and Subtract operations complete their actions automatically, the Divide completes its actions through an explicit call to the `SetTransactionComplete` method, and the Multiply does not complete its actions but instead relies upon and requires a later call, such as to Divide, to complete the actions.</span></span>  
  
 <span data-ttu-id="5a927-134">Implementacja opartego na atrybutach usługi jest w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5a927-134">The attributed service implementation is as follows:</span></span>  
  
```  
[ServiceBehavior(  
    TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
    TransactionTimeout = "00:00:30",  
    ReleaseServiceInstanceOnTransactionComplete = false,  
    TransactionAutoCompleteOnSessionClose = false)]  
public class CalculatorService : ICalculator  
{  
    double runningTotal;  
  
    public CalculatorService()  
    {  
        Console.WriteLine("Creating new service instance...");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Add(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n, runningTotal));  
        runningTotal = runningTotal + n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public double Subtract(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n, runningTotal));  
        runningTotal = runningTotal - n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Multiply(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal * n;  
        return runningTotal;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]  
    public double Divide(double n)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", runningTotal, n));  
        runningTotal = runningTotal / n;  
        OperationContext.Current.SetTransactionComplete();  
        return runningTotal;  
    }  
  
    // Logging method ommitted for brevity  
}   
```  
  
 <span data-ttu-id="5a927-135">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="5a927-135">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5a927-136">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="5a927-136">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Starting transaction  
Performing calculations...  
  Adding 100, running total=100  
  Subtracting 45, running total=55  
  Multiplying by 9, running total=495  
  Dividing by 15, running total=33  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="5a927-137">Rejestrowanie żądania operacji usług są wyświetlane w oknie konsoli tej usługi.</span><span class="sxs-lookup"><span data-stu-id="5a927-137">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="5a927-138">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="5a927-138">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 <span data-ttu-id="5a927-139">Należy pamiętać, że oprócz utrzymywanie łączna liczba uruchomionych obliczeń, usługa raporty tworzenia wystąpień (jednego wystąpienia w tym przykładzie) i rejestruje żądania operacji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="5a927-139">Note that in addition to keeping the running total of the calculations, the service reports the creation of instances (one instance for this sample) and logs the operation requests to a database.</span></span> <span data-ttu-id="5a927-140">Ponieważ wszystkie żądania przepływu transakcji klienta, jakiekolwiek niepowodzenie, aby ukończyć tej transakcji powoduje we wszystkich operacji wycofywane w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="5a927-140">Because all of the requests flow the client's transaction, any failure to complete that transaction results in all of the database operations being rolled back.</span></span> <span data-ttu-id="5a927-141">To mogą być przedstawiane na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="5a927-141">This can be demonstrated in a number of ways:</span></span>  
  
-   <span data-ttu-id="5a927-142">Komentarz wywołania klienta `tx.Complete`() i ponownie uruchom - skutkiem klienta Kończenie zakresu transakcji bez ukończenie jego transakcji.</span><span class="sxs-lookup"><span data-stu-id="5a927-142">Comment out the client's call to `tx.Complete`() and rerun - this results in the client exiting the transaction scope without completing its transaction.</span></span>  
  
-   <span data-ttu-id="5a927-143">Komentarz dotyczący out wywołania operacji usługi dzielenia — powoduje to zapobiec akcji zainicjowanej przez mnożenia ukończenie operacji i dlatego transakcji klienta ostatecznie również nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="5a927-143">Comment out the call to the Divide service operation - this results prevent the action initiated by the Multiply operation from completing and thus the client's transaction ultimately also fails to complete.</span></span>  
  
-   <span data-ttu-id="5a927-144">Throw Wystąpił nieobsługiwany wyjątek w dowolnym miejscu w zakresie transakcji klienta — podobnie zapobiega to klient ukończenie jego transakcji.</span><span class="sxs-lookup"><span data-stu-id="5a927-144">Throw an unhandled exception anywhere in the client's transaction scope - this similarly prevents the client from completing its transaction.</span></span>  
  
 <span data-ttu-id="5a927-145">Wynikiem tych jest czy żaden z operacji wykonywanych w tym zakresie nie jest zatwierdzona i liczbę wierszy utrwalone w bazie danych zwiększa się.</span><span class="sxs-lookup"><span data-stu-id="5a927-145">The result of any of these is that none of the operations performed within that scope are committed and the count of rows persisted to the database do not increment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a927-146">Jako część procesu kompilacji pliku bazy danych jest kopiowany do folderu bin.</span><span class="sxs-lookup"><span data-stu-id="5a927-146">As part of the build process the database file is copied to the bin folder.</span></span> <span data-ttu-id="5a927-147">Należy Przyjrzyj się tej kopii pliku bazy danych do obserwowania wierszy, które są zachowywane w dzienniku, a nie plik, który znajduje się w projekcie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a927-147">You must look at that copy of the database file to observe the rows that are persisted to the log rather than the file that is included in the Visual Studio project.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5a927-148">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="5a927-148">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5a927-149">Upewnij się, że zainstalowano program SQL Server 2005 Express Edition lub SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="5a927-149">Ensure that you have installed SQL Server 2005 Express Edition or SQL Server 2005.</span></span> <span data-ttu-id="5a927-150">W pliku App.config usługi bazy danych `connectionString` może być zestaw lub bazy danych, interakcje mogą być wyłączone przez ustawienia appSettings `usingSql` wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="5a927-150">In the service's App.config file, the database `connectionString` may be set or the database interactions may be disabled by setting the appSettings `usingSql` value to `false`.</span></span>  
  
2.  <span data-ttu-id="5a927-151">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a927-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="5a927-152">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a927-152">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="5a927-153">Po uruchomieniu przykładu na komputerach, należy skonfigurować transakcję Koordynator MSDTC (Microsoft Distributed) Włączanie przepływu transakcji sieci i włączanie usługi Windows Communication Foundation (WCF) transakcji sieci za pomocą narzędzia WsatConfig.exe Pomoc techniczna.</span><span class="sxs-lookup"><span data-stu-id="5a927-153">If you run the sample across machines, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable Windows Communication Foundation (WCF) transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a><span data-ttu-id="5a927-154">Aby skonfigurować transakcji Koordynator MSDTC (Microsoft Distributed) do obsługi działa aplikacja przykładowa na komputerach</span><span class="sxs-lookup"><span data-stu-id="5a927-154">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample across machines</span></span>  
  
1.  <span data-ttu-id="5a927-155">Na komputerze usługi należy skonfigurować usługi MSDTC, aby zezwolić na przychodzące transakcje sieciowe.</span><span class="sxs-lookup"><span data-stu-id="5a927-155">On the service machine, configure MSDTC to allow incoming network transactions.</span></span>  
  
    1.  <span data-ttu-id="5a927-156">Z **Start** menu, przejdź do **Panelu sterowania**, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="5a927-156">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="5a927-157">Kliknij prawym przyciskiem myszy **Mój komputer** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5a927-157">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="5a927-158">Na **MSDTC** kliknij pozycję **konfiguracji zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="5a927-158">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="5a927-159">Sprawdź **DTC dostęp sieciowy** i **zezwolić na przychodzący**.</span><span class="sxs-lookup"><span data-stu-id="5a927-159">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5.  <span data-ttu-id="5a927-160">Kliknij przycisk **tak** Uruchom ponownie usługę MS DTC, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="5a927-160">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="5a927-161">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5a927-161">Click **OK** to close the dialog box.</span></span>  
  
2.  <span data-ttu-id="5a927-162">Na komputerze usługi i komputerze klienckim należy skonfigurować zaporę Windows obejmujący transakcji Koordynator MSDTC (Microsoft Distributed) do listy aplikacji wyjątku:</span><span class="sxs-lookup"><span data-stu-id="5a927-162">On the service machine and the client machine, configure the Windows Firewall to include the Microsoft Distributed Transaction Coordinator (MSDTC) to the list of excepted applications:</span></span>  
  
    1.  <span data-ttu-id="5a927-163">Uruchom aplikację Zapora Windows z poziomu Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="5a927-163">Run the Windows Firewall application from Control Panel.</span></span>  
  
    2.  <span data-ttu-id="5a927-164">Z **wyjątki** kliknij pozycję **Dodaj Program**.</span><span class="sxs-lookup"><span data-stu-id="5a927-164">From the **Exceptions** tab, click **Add Program**.</span></span>  
  
    3.  <span data-ttu-id="5a927-165">Przejdź do folderu C:\WINDOWS\System32.</span><span class="sxs-lookup"><span data-stu-id="5a927-165">Browse to the folder C:\WINDOWS\System32.</span></span>  
  
    4.  <span data-ttu-id="5a927-166">Msdtc.exe wybierz i kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="5a927-166">Select Msdtc.exe and click **Open**.</span></span>  
  
    5.  <span data-ttu-id="5a927-167">Kliknij przycisk **OK** zamknąć **Dodaj Program** okno dialogowe, a następnie kliknij przycisk **OK** ponownie, aby zamknąć aplet Zapora Windows.</span><span class="sxs-lookup"><span data-stu-id="5a927-167">Click **OK** to close the **Add Program** dialog box, and click **OK** again to close the Windows Firewall applet.</span></span>  
  
3.  <span data-ttu-id="5a927-168">Na komputerze klienckim należy skonfigurować usługi MSDTC, aby zezwolić na wychodzące transakcje sieciowe:</span><span class="sxs-lookup"><span data-stu-id="5a927-168">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1.  <span data-ttu-id="5a927-169">Z **Start** menu, przejdź do **Panelu sterowania**, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="5a927-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="5a927-170">Kliknij prawym przyciskiem myszy **Mój komputer** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5a927-170">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="5a927-171">Na **MSDTC** kliknij pozycję **konfiguracji zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="5a927-171">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="5a927-172">Sprawdź **DTC dostęp sieciowy** i **Zezwalaj na wychodzące**.</span><span class="sxs-lookup"><span data-stu-id="5a927-172">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5.  <span data-ttu-id="5a927-173">Kliknij przycisk **tak** Uruchom ponownie usługę MS DTC, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="5a927-173">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="5a927-174">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5a927-174">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5a927-175">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5a927-175">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5a927-176">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5a927-176">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5a927-177">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="5a927-177">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5a927-178">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5a927-178">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
  
## <a name="see-also"></a><span data-ttu-id="5a927-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a927-179">See Also</span></span>
