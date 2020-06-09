---
title: Zachowanie transakcji usługi
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: 0be5bf0dbe6416febb898fb5150c5a516c8b0969
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591530"
---
# <a name="service-transaction-behavior"></a><span data-ttu-id="d3a61-102">Zachowanie transakcji usługi</span><span class="sxs-lookup"><span data-stu-id="d3a61-102">Service Transaction Behavior</span></span>

<span data-ttu-id="d3a61-103">Ten przykład ilustruje użycie transakcji skoordynowanej przez klienta oraz ustawień ServiceBehaviorAttribute i OperationBehaviorAttribute będący w celu sterowania zachowaniem transakcji usługi.</span><span class="sxs-lookup"><span data-stu-id="d3a61-103">This sample demonstrates the use of a client-coordinated transaction and the settings of ServiceBehaviorAttribute and OperationBehaviorAttribute to control service transaction behavior.</span></span> <span data-ttu-id="d3a61-104">Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md) , który implementuje usługę kalkulatora, ale jest rozszerzony do obsługi dziennika na serwerze wykonanych operacji w tabeli bazy danych, a stanowa suma uruchamiania operacji kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="d3a61-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service, but is extended to maintain a server log of the performed operations in a database table and a stateful running total for the calculator operations.</span></span> <span data-ttu-id="d3a61-105">Utrwalone zapisy w tabeli dziennika serwera są zależne od wyniku skoordynowanej transakcji klienta — Jeśli transakcja klienta nie została ukończona, transakcja usługi sieci Web gwarantuje, że aktualizacje bazy danych nie zostaną zatwierdzone.</span><span class="sxs-lookup"><span data-stu-id="d3a61-105">Persisted writes to the server log table are dependent upon the outcome of a client coordinated transaction - if the client transaction does not complete, the Web service transaction ensures that the updates to the database are not committed.</span></span>

> [!NOTE]
> <span data-ttu-id="d3a61-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d3a61-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="d3a61-107">Umowa dla usługi definiuje, że wszystkie operacje wymagają transakcji, aby można było przepływać żądania:</span><span class="sxs-lookup"><span data-stu-id="d3a61-107">The contract for the service defines that all of the operations require a transaction to be flowed with requests:</span></span>

```csharp
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

<span data-ttu-id="d3a61-108">Aby włączyć przepływ transakcji przychodzących, usługa jest konfigurowana z wsHttpBinding udostępnionym przez system z atrybutem transactionFlow ustawionym na `true` .</span><span class="sxs-lookup"><span data-stu-id="d3a61-108">To enable the incoming transaction flow, the service is configured with the system-provided wsHttpBinding with the transactionFlow attribute set to `true`.</span></span> <span data-ttu-id="d3a61-109">To powiązanie używa protokołu międzyoperacyjnego WSAtomicTransactionOctober2004:</span><span class="sxs-lookup"><span data-stu-id="d3a61-109">This binding uses the interoperable WSAtomicTransactionOctober2004 protocol:</span></span>

```xml
<bindings>
  <wsHttpBinding>
    <binding name="transactionalBinding" transactionFlow="true" />
  </wsHttpBinding>
</bindings>
```

<span data-ttu-id="d3a61-110">Po zainicjowaniu połączenia z usługą i transakcją klient uzyskuje dostęp do kilku operacji usługi w zakresie tej transakcji, a następnie kończy transakcję i zamyka połączenie:</span><span class="sxs-lookup"><span data-stu-id="d3a61-110">After initiating both a connection to the service and a transaction, the client accesses several service operations within the scope of that transaction and then completes the transaction and closes the connection:</span></span>

```csharp
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

<span data-ttu-id="d3a61-111">W usłudze istnieją trzy atrybuty, które mają wpływ na zachowanie transakcji usługi i są one w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d3a61-111">On the service, there are three attributes that affect the service transaction behavior, and they do so in the following ways:</span></span>

- <span data-ttu-id="d3a61-112">Na stronie `ServiceBehaviorAttribute` :</span><span class="sxs-lookup"><span data-stu-id="d3a61-112">On the `ServiceBehaviorAttribute`:</span></span>

  - <span data-ttu-id="d3a61-113">`TransactionTimeout`Właściwość określa czas, w którym transakcja musi zostać zakończona.</span><span class="sxs-lookup"><span data-stu-id="d3a61-113">The `TransactionTimeout` property specifies the time period within which a transaction must complete.</span></span> <span data-ttu-id="d3a61-114">W tym przykładzie jest ustawiony na 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="d3a61-114">In this sample it is set to 30 seconds.</span></span>

  - <span data-ttu-id="d3a61-115">`TransactionIsolationLevel`Właściwość określa poziom izolacji obsługiwanej przez usługę.</span><span class="sxs-lookup"><span data-stu-id="d3a61-115">The `TransactionIsolationLevel` property specifies the isolation level that the service supports.</span></span> <span data-ttu-id="d3a61-116">Jest to wymagane w celu dopasowania do poziomu izolacji klienta.</span><span class="sxs-lookup"><span data-stu-id="d3a61-116">This is required to match the client's isolation level.</span></span>

  - <span data-ttu-id="d3a61-117">`ReleaseServiceInstanceOnTransactionComplete`Właściwość określa, czy wystąpienie usługi jest odtwarzane po zakończeniu transakcji.</span><span class="sxs-lookup"><span data-stu-id="d3a61-117">The `ReleaseServiceInstanceOnTransactionComplete` property specifies whether the service instance is recycled when a transaction completes.</span></span> <span data-ttu-id="d3a61-118">Ustawiając je na `false` , usługa zachowuje to samo wystąpienie usługi w ramach żądań operacji.</span><span class="sxs-lookup"><span data-stu-id="d3a61-118">By setting it to `false`, the service maintains the same service instance across the operation requests.</span></span> <span data-ttu-id="d3a61-119">Jest to wymagane, aby zachować sumę uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="d3a61-119">This is required to maintain the running total.</span></span> <span data-ttu-id="d3a61-120">Jeśli jest ustawiona na `true` , nowe wystąpienie jest generowane po każdej zakończonej akcji.</span><span class="sxs-lookup"><span data-stu-id="d3a61-120">If set to `true`, a new instance is generated after each completed action.</span></span>

  - <span data-ttu-id="d3a61-121">`TransactionAutoCompleteOnSessionClose`Właściwość określa, czy oczekujące transakcje są uzupełniane po zamknięciu sesji.</span><span class="sxs-lookup"><span data-stu-id="d3a61-121">The `TransactionAutoCompleteOnSessionClose` property specifies whether outstanding transactions are completed when the session closes.</span></span> <span data-ttu-id="d3a61-122">Przez ustawienie do `false` , poszczególne operacje są wymagane do ustawienia <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> właściwości na `true` lub, aby jawnie wymagały wywołania <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> metody do ukończenia transakcji.</span><span class="sxs-lookup"><span data-stu-id="d3a61-122">By setting it to `false`, the individual operations are required to either set the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> property to `true` or to explicitly require a call to the <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> method to complete transactions.</span></span> <span data-ttu-id="d3a61-123">Ten przykład ilustruje oba podejścia.</span><span class="sxs-lookup"><span data-stu-id="d3a61-123">This sample demonstrates both approaches.</span></span>

- <span data-ttu-id="d3a61-124">Na stronie `ServiceContractAttribute` :</span><span class="sxs-lookup"><span data-stu-id="d3a61-124">On the `ServiceContractAttribute`:</span></span>

  - <span data-ttu-id="d3a61-125">`SessionMode`Właściwość określa, czy usługa skorelować odpowiednie żądania w sesji logicznej.</span><span class="sxs-lookup"><span data-stu-id="d3a61-125">The `SessionMode` property specifies whether the service correlates the appropriate requests into a logical session.</span></span> <span data-ttu-id="d3a61-126">Ponieważ ta usługa obejmuje operacje, w których Właściwość TransactionAutoComplete OperationBehaviorAttribute będący jest ustawiona na wartość `false` (pomnóż i Podziel), `SessionMode.Required` musi być określona.</span><span class="sxs-lookup"><span data-stu-id="d3a61-126">Because this service includes operations where the OperationBehaviorAttribute TransactionAutoComplete property is set to `false` (Multiply and Divide), `SessionMode.Required` must be specified.</span></span> <span data-ttu-id="d3a61-127">Na przykład operacja mnożenia nie kończy transakcji i zamiast tego używa późniejszego wywołania do dzielenia, aby zakończyć przy użyciu `SetTransactionComplete` metody. usługa musi być w stanie określić, że te operacje są wykonywane w ramach tej samej sesji.</span><span class="sxs-lookup"><span data-stu-id="d3a61-127">For example, the Multiply operation does not complete its transaction and instead relies upon a later call to Divide to complete using the `SetTransactionComplete` method; the service must be able to determine that these operations are occurring within the same session.</span></span>

- <span data-ttu-id="d3a61-128">Na stronie `OperationBehaviorAttribute` :</span><span class="sxs-lookup"><span data-stu-id="d3a61-128">On the `OperationBehaviorAttribute`:</span></span>

  - <span data-ttu-id="d3a61-129">`TransactionScopeRequired`Właściwość określa, czy akcje operacji powinny być wykonywane w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="d3a61-129">The `TransactionScopeRequired` property specifies whether the operation's actions should be executed within a transaction scope.</span></span> <span data-ttu-id="d3a61-130">Ta wartość jest ustawiona na `true` dla wszystkich operacji w tym przykładzie, a ponieważ klient przepływa do wszystkich operacji, akcje są wykonywane w zakresie tej transakcji klienta.</span><span class="sxs-lookup"><span data-stu-id="d3a61-130">This is set to `true` for all operations in this sample and, because the client flows its transaction to all operations, the actions occur within the scope of that client transaction.</span></span>

  - <span data-ttu-id="d3a61-131">`TransactionAutoComplete`Właściwość określa, czy transakcja, w której wykonywana jest metoda, jest automatycznie uzupełniana w przypadku braku nieobsłużonych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="d3a61-131">The `TransactionAutoComplete` property specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions occur.</span></span> <span data-ttu-id="d3a61-132">Jak opisano wcześniej, jest to ustawienie `true` dla operacji dodawania i odejmowania, ale `false` dla operacji mnożenia i dzielenia.</span><span class="sxs-lookup"><span data-stu-id="d3a61-132">As previously described, this is set to `true` for the Add and Subtract operations but `false` for the Multiply and Divide operations.</span></span> <span data-ttu-id="d3a61-133">Operacje dodawania i odejmowania automatycznie uzupełniają swoje akcje, podział wykonuje swoje działania za pomocą jawnego wywołania `SetTransactionComplete` metody, a mnożenie nie kończy wykonywania akcji, ale zamiast tego jest wymagane i wymaga późniejszego wywołania, takiego jak dzielenie, w celu wykonania akcji.</span><span class="sxs-lookup"><span data-stu-id="d3a61-133">The Add and Subtract operations complete their actions automatically, the Divide completes its actions through an explicit call to the `SetTransactionComplete` method, and the Multiply does not complete its actions but instead relies upon and requires a later call, such as to Divide, to complete the actions.</span></span>

<span data-ttu-id="d3a61-134">Implementacja usługi z atrybutami jest następująca:</span><span class="sxs-lookup"><span data-stu-id="d3a61-134">The attributed service implementation is as follows:</span></span>

```csharp
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

    // Logging method omitted for brevity
}
```

<span data-ttu-id="d3a61-135">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="d3a61-135">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d3a61-136">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="d3a61-136">Press ENTER in the client window to shut down the client.</span></span>

```console
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

<span data-ttu-id="d3a61-137">Rejestrowanie żądań operacji usługi jest wyświetlane w oknie konsoli usługi.</span><span class="sxs-lookup"><span data-stu-id="d3a61-137">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="d3a61-138">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="d3a61-138">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate service.
Creating new service instance...
  Writing row 1 to database: Adding 100 to 0
  Writing row 2 to database: Subtracting 45 from 100
  Writing row 3 to database: Multiplying 55 by 9
  Writing row 4 to database: Dividing 495 by 15
```

<span data-ttu-id="d3a61-139">Należy pamiętać, że oprócz przechowywania sumy całkowitej obliczeń usługa zgłasza Tworzenie wystąpień (jedno wystąpienie dla tego przykładu) i rejestruje żądania operacji w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="d3a61-139">Note that in addition to keeping the running total of the calculations, the service reports the creation of instances (one instance for this sample) and logs the operation requests to a database.</span></span> <span data-ttu-id="d3a61-140">Ze względu na to, że wszystkie żądania przepływają transakcję klienta, wszelkie niepowodzenie wykonania tej transakcji spowoduje wycofanie wszystkich operacji bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d3a61-140">Because all of the requests flow the client's transaction, any failure to complete that transaction results in all of the database operations being rolled back.</span></span> <span data-ttu-id="d3a61-141">Można to przedstawić na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="d3a61-141">This can be demonstrated in a number of ways:</span></span>

- <span data-ttu-id="d3a61-142">Dodaj komentarz do wywołania klienta do `tx.Complete` () i uruchom ponownie — spowoduje to wyjście z zakresu transakcji bez wykonywania transakcji.</span><span class="sxs-lookup"><span data-stu-id="d3a61-142">Comment out the client's call to `tx.Complete`() and rerun - this results in the client exiting the transaction scope without completing its transaction.</span></span>

- <span data-ttu-id="d3a61-143">Dodaj komentarz do wywołania operacji dzielenia usługi — spowoduje to uniemożliwienie akcji zainicjowanej przez operację mnożenia i w ten sposób zakończenie transakcji klienta kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d3a61-143">Comment out the call to the Divide service operation - this results prevent the action initiated by the Multiply operation from completing and thus the client's transaction ultimately also fails to complete.</span></span>

- <span data-ttu-id="d3a61-144">Zgłoś nieobsługiwany wyjątek w dowolnym miejscu w zakresie transakcji klienta — w podobny sposób uniemożliwia klientowi wykonywanie transakcji.</span><span class="sxs-lookup"><span data-stu-id="d3a61-144">Throw an unhandled exception anywhere in the client's transaction scope - this similarly prevents the client from completing its transaction.</span></span>

<span data-ttu-id="d3a61-145">Wynik któregokolwiek z tych elementów polega na tym, że żadna z operacji wykonywanych w ramach tego zakresu nie zostanie zatwierdzona, a liczba wierszy utrwalonych w bazie danych nie jest zwiększana.</span><span class="sxs-lookup"><span data-stu-id="d3a61-145">The result of any of these is that none of the operations performed within that scope are committed and the count of rows persisted to the database do not increment.</span></span>

> [!NOTE]
> <span data-ttu-id="d3a61-146">W ramach procesu kompilacji plik bazy danych jest kopiowany do folderu bin.</span><span class="sxs-lookup"><span data-stu-id="d3a61-146">As part of the build process the database file is copied to the bin folder.</span></span> <span data-ttu-id="d3a61-147">Należy przyjrzeć się tej kopii pliku bazy danych, aby obserwować wiersze, które są utrwalane w dzienniku, a nie plik, który jest zawarty w projekcie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d3a61-147">You must look at that copy of the database file to observe the rows that are persisted to the log rather than the file that is included in the Visual Studio project.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d3a61-148">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="d3a61-148">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d3a61-149">Upewnij się, że zainstalowano SQL Server 2005 Express Edition lub SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="d3a61-149">Ensure that you have installed SQL Server 2005 Express Edition or SQL Server 2005.</span></span> <span data-ttu-id="d3a61-150">W pliku App. config usługi `connectionString` może być ustawiona baza danych lub interakcje bazy danych można wyłączyć, ustawiając `usingSql` wartość AppSettings na `false` .</span><span class="sxs-lookup"><span data-stu-id="d3a61-150">In the service's App.config file, the database `connectionString` may be set or the database interactions may be disabled by setting the appSettings `usingSql` value to `false`.</span></span>

2. <span data-ttu-id="d3a61-151">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d3a61-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="d3a61-152">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d3a61-152">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="d3a61-153">W przypadku uruchamiania przykładu między maszynami należy skonfigurować usługę Microsoft Distributed Transaction Coordinator (MSDTC) w celu włączenia przepływu transakcji sieciowych i użyć narzędzia WsatConfig. exe w celu włączenia obsługi sieci Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d3a61-153">If you run the sample across machines, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable Windows Communication Foundation (WCF) transactions network support.</span></span>

### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a><span data-ttu-id="d3a61-154">Aby skonfigurować Distributed Transaction Coordinator firmy Microsoft (MSDTC) do obsługi przykładowego między maszynami</span><span class="sxs-lookup"><span data-stu-id="d3a61-154">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample across machines</span></span>

1. <span data-ttu-id="d3a61-155">Na maszynie usługi Skonfiguruj usługę MSDTC w taki sposób, aby zezwalała na przychodzące transakcje sieciowe.</span><span class="sxs-lookup"><span data-stu-id="d3a61-155">On the service machine, configure MSDTC to allow incoming network transactions.</span></span>

    1. <span data-ttu-id="d3a61-156">W menu **Start** przejdź do **Panelu sterowania**, a następnie **Narzędzia administracyjne**, a następnie **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="d3a61-156">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>

    2. <span data-ttu-id="d3a61-157">Kliknij prawym przyciskiem myszy pozycję **mój komputer** , a następnie wybierz pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d3a61-157">Right-click **My Computer** and select **Properties**.</span></span>

    3. <span data-ttu-id="d3a61-158">Na karcie **MSDTC** kliknij pozycję **Konfiguracja zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="d3a61-158">On the **MSDTC** tab, click **Security Configuration**.</span></span>

    4. <span data-ttu-id="d3a61-159">Sprawdź **dostęp do usługi Network DTC** i **Zezwalaj na ruch przychodzący**.</span><span class="sxs-lookup"><span data-stu-id="d3a61-159">Check **Network DTC Access** and **Allow Inbound**.</span></span>

    5. <span data-ttu-id="d3a61-160">Kliknij przycisk **tak** , aby ponownie uruchomić usługę MS DTC, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3a61-160">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>

    6. <span data-ttu-id="d3a61-161">Kliknij przycisk **OK**, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d3a61-161">Click **OK** to close the dialog box.</span></span>

2. <span data-ttu-id="d3a61-162">Na maszynie usługi i na komputerze klienckim Skonfiguruj zaporę systemu Windows w taki sposób, aby zawierała Distributed Transaction Coordinator firmy Microsoft (MSDTC) do listy wykluczonych aplikacji:</span><span class="sxs-lookup"><span data-stu-id="d3a61-162">On the service machine and the client machine, configure the Windows Firewall to include the Microsoft Distributed Transaction Coordinator (MSDTC) to the list of excepted applications:</span></span>

    1. <span data-ttu-id="d3a61-163">Uruchom aplikację Zapora systemu Windows z panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="d3a61-163">Run the Windows Firewall application from Control Panel.</span></span>

    2. <span data-ttu-id="d3a61-164">Na karcie **wyjątki** kliknij pozycję **Dodaj program**.</span><span class="sxs-lookup"><span data-stu-id="d3a61-164">From the **Exceptions** tab, click **Add Program**.</span></span>

    3. <span data-ttu-id="d3a61-165">Przejdź do folderu C:\WINDOWS\System32.</span><span class="sxs-lookup"><span data-stu-id="d3a61-165">Browse to the folder C:\WINDOWS\System32.</span></span>

    4. <span data-ttu-id="d3a61-166">Wybierz pozycję MSDTC. exe i kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="d3a61-166">Select Msdtc.exe and click **Open**.</span></span>

    5. <span data-ttu-id="d3a61-167">Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Dodawanie programu** , a następnie kliknij przycisk **OK** ponownie, aby zamknąć aplet Zapora systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d3a61-167">Click **OK** to close the **Add Program** dialog box, and click **OK** again to close the Windows Firewall applet.</span></span>

3. <span data-ttu-id="d3a61-168">Na komputerze klienckim Skonfiguruj usługę MSDTC tak, aby zezwalała na wychodzące transakcje sieciowe:</span><span class="sxs-lookup"><span data-stu-id="d3a61-168">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>

    1. <span data-ttu-id="d3a61-169">W menu **Start** przejdź do **Panelu sterowania**, a następnie **Narzędzia administracyjne**, a następnie **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="d3a61-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>

    2. <span data-ttu-id="d3a61-170">Kliknij prawym przyciskiem myszy pozycję **mój komputer** , a następnie wybierz pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d3a61-170">Right-click **My Computer** and select **Properties**.</span></span>

    3. <span data-ttu-id="d3a61-171">Na karcie **MSDTC** kliknij pozycję **Konfiguracja zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="d3a61-171">On the **MSDTC** tab, click **Security Configuration**.</span></span>

    4. <span data-ttu-id="d3a61-172">Sprawdź **dostęp do usługi Network DTC** i **Zezwalaj na ruch wychodzący**.</span><span class="sxs-lookup"><span data-stu-id="d3a61-172">Check **Network DTC Access** and **Allow Outbound**.</span></span>

    5. <span data-ttu-id="d3a61-173">Kliknij przycisk **tak** , aby ponownie uruchomić usługę MS DTC, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d3a61-173">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>

    6. <span data-ttu-id="d3a61-174">Kliknij przycisk **OK**, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d3a61-174">Click **OK** to close the dialog box.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d3a61-175">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d3a61-175">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d3a61-176">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="d3a61-176">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d3a61-177">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="d3a61-177">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d3a61-178">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d3a61-178">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`
