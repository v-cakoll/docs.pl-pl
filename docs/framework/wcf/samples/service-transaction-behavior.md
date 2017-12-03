---
title: "Zachowanie transakcji usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4777136c80f7dba368c85fac7d7dd1db9c945c5b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="service-transaction-behavior"></a><span data-ttu-id="ebb6b-102">Zachowanie transakcji usługi</span><span class="sxs-lookup"><span data-stu-id="ebb6b-102">Service Transaction Behavior</span></span>
<span data-ttu-id="ebb6b-103">W przykładzie pokazano użycie transakcji koordynowane przez klienta i ustawienia atrybutu ServiceBehaviorAttribute i OperationBehaviorAttribute można kontrolować zachowanie transakcji usługi.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-103">This sample demonstrates the use of a client-coordinated transaction and the settings of ServiceBehaviorAttribute and OperationBehaviorAttribute to control service transaction behavior.</span></span> <span data-ttu-id="ebb6b-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementuje usługi Kalkulator, ale jest rozszerzony do obsługi serwera dziennik działań wykonywanych w tabeli bazy danych i stanowego Suma operacji Kalkulator bieżąca.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service, but is extended to maintain a server log of the performed operations in a database table and a stateful running total for the calculator operations.</span></span> <span data-ttu-id="ebb6b-105">Utrwalonych zapisuje dane w tabeli dziennika serwera są zależne od wyniku transakcji klienta koordynowane — Jeśli transakcja klienta nie zostanie ukończone, transakcja usługi sieci Web zapewnia aktualizacji do bazy danych nie są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-105">Persisted writes to the server log table are dependent upon the outcome of a client coordinated transaction - if the client transaction does not complete, the Web service transaction ensures that the updates to the database are not committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebb6b-106">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ebb6b-107">Kontrakt usługi określa, że wszystkie operacje wymaga przepływu z żądaniami transakcji:</span><span class="sxs-lookup"><span data-stu-id="ebb6b-107">The contract for the service defines that all of the operations require a transaction to be flowed with requests:</span></span>  
  
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
  
 <span data-ttu-id="ebb6b-108">Aby umożliwić ruch przychodzący transakcji, usługa jest skonfigurowana z wsHttpBinding dostarczane przez system z atrybutem transactionFlow ustawioną `true`.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-108">To enable the incoming transaction flow, the service is configured with the system-provided wsHttpBinding with the transactionFlow attribute set to `true`.</span></span> <span data-ttu-id="ebb6b-109">Współdziałanie protokołu WSAtomicTransactionOctober2004 używa tego powiązania:</span><span class="sxs-lookup"><span data-stu-id="ebb6b-109">This binding uses the interoperable WSAtomicTransactionOctober2004 protocol:</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="transactionalBinding" transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="ebb6b-110">Po zainicjowaniu zarówno połączenia usługi i transakcji, klient uzyskuje dostęp do wielu operacji usługi w zakresie transakcji wykonuje transakcję i zamyka połączenie:</span><span class="sxs-lookup"><span data-stu-id="ebb6b-110">After initiating both a connection to the service and a transaction, the client accesses several service operations within the scope of that transaction and then completes the transaction and closes the connection:</span></span>  
  
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
  
 <span data-ttu-id="ebb6b-111">W usłudze istnieją trzy atrybuty, które mają wpływ na zachowanie transakcji usługi, a w tym celu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="ebb6b-111">On the service, there are three attributes that affect the service transaction behavior, and they do so in the following ways:</span></span>  
  
-   <span data-ttu-id="ebb6b-112">Na `ServiceBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="ebb6b-112">On the `ServiceBehaviorAttribute`:</span></span>  
  
    -   <span data-ttu-id="ebb6b-113">`TransactionTimeout` Właściwość określa okres czasu, w ramach którego transakcja musi zostać zakończona.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-113">The `TransactionTimeout` property specifies the time period within which a transaction must complete.</span></span> <span data-ttu-id="ebb6b-114">W tym przykładzie jest ustawiona na 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-114">In this sample it is set to 30 seconds.</span></span>  
  
    -   <span data-ttu-id="ebb6b-115">`TransactionIsolationLevel` Właściwość określa poziom izolacji, który obsługuje usługę.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-115">The `TransactionIsolationLevel` property specifies the isolation level that the service supports.</span></span> <span data-ttu-id="ebb6b-116">Jest to wymagane, aby dopasować poziom izolacji klienta.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-116">This is required to match the client's isolation level.</span></span>  
  
    -   <span data-ttu-id="ebb6b-117">`ReleaseServiceInstanceOnTransactionComplete` Właściwość określa, czy wystąpienie usługi jest ponownie przetwarzany po zakończeniu transakcji.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-117">The `ReleaseServiceInstanceOnTransactionComplete` property specifies whether the service instance is recycled when a transaction completes.</span></span> <span data-ttu-id="ebb6b-118">Przez ustawienie jej na `false`, usługa utrzymuje tego samego wystąpienia usługi między żądania operacji.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-118">By setting it to `false`, the service maintains the same service instance across the operation requests.</span></span> <span data-ttu-id="ebb6b-119">Jest to wymagane, aby kontynuować obliczanie całkowitej.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-119">This is required to maintain the running total.</span></span> <span data-ttu-id="ebb6b-120">Jeśli ustawiono `true`, nowe wystąpienie jest generowany po zakończeniu każdej akcji.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-120">If set to `true`, a new instance is generated after each completed action.</span></span>  
  
    -   <span data-ttu-id="ebb6b-121">`TransactionAutoCompleteOnSessionClose` Właściwość określa, czy transakcje oczekujące są wykonywane po zamknięciu sesji.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-121">The `TransactionAutoCompleteOnSessionClose` property specifies whether outstanding transactions are completed when the session closes.</span></span> <span data-ttu-id="ebb6b-122">Przez ustawienie jej na `false`, poszczególnych operacji są wymagane do obu zestawów `OperationBehaviorAttribute``TransactionAutoComplete` właściwości `true` lub aby jawnie wymaga wywołania `SetTransactionComplete` sposób realizacji transakcji.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-122">By setting it to `false`, the individual operations are required to either set the `OperationBehaviorAttribute``TransactionAutoComplete` property to `true` or to explicitly require a call to the `SetTransactionComplete` method to complete transactions.</span></span> <span data-ttu-id="ebb6b-123">W tym przykładzie przedstawiono obu podejść.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-123">This sample demonstrates both approaches.</span></span>  
  
-   <span data-ttu-id="ebb6b-124">Na `ServiceContractAttribute`:</span><span class="sxs-lookup"><span data-stu-id="ebb6b-124">On the `ServiceContractAttribute`:</span></span>  
  
    -   <span data-ttu-id="ebb6b-125">`SessionMode` Właściwość określa, czy usługi są powiązane z odpowiednich żądań do logicznego sesji.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-125">The `SessionMode` property specifies whether the service correlates the appropriate requests into a logical session.</span></span> <span data-ttu-id="ebb6b-126">Ponieważ ta usługa obejmuje operacje, których właściwość OperationBehaviorAttribute Wartość TransactionAutoComplete jest wartość `false` (mnożenia i dzielenia) `SessionMode.Required` musi być określona.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-126">Because this service includes operations where the OperationBehaviorAttribute TransactionAutoComplete property is set to `false` (Multiply and Divide), `SessionMode.Required` must be specified.</span></span> <span data-ttu-id="ebb6b-127">Na przykład wielokrotnie operacja nie zostanie zakończone transakcję i zamiast tego, opiera się na nowsze wywołanie do dzielenia wykonania za pomocą `SetTransactionComplete` metody; usługi musi być możliwe ustalenie, czy te operacje są wykonywane w ramach tej samej sesji.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-127">For example, the Multiply operation does not complete its transaction and instead relies upon a later call to Divide to complete using the `SetTransactionComplete` method; the service must be able to determine that these operations are occurring within the same session.</span></span>  
  
-   <span data-ttu-id="ebb6b-128">Na `OperationBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="ebb6b-128">On the `OperationBehaviorAttribute`:</span></span>  
  
    -   <span data-ttu-id="ebb6b-129">`TransactionScopeRequired` Właściwość określa, czy mają zostać wykonane akcje wykonać operację w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-129">The `TransactionScopeRequired` property specifies whether the operation's actions should be executed within a transaction scope.</span></span> <span data-ttu-id="ebb6b-130">Ta wartość jest równa `true` dla wszystkich operacji w tym przykładowe i, ponieważ klient przepływy transakcji do wszystkich operacji, wykonywane akcje w zakresie transakcji klienta.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-130">This is set to `true` for all operations in this sample and, because the client flows its transaction to all operations, the actions occur within the scope of that client transaction.</span></span>  
  
    -   <span data-ttu-id="ebb6b-131">`TransactionAutoComplete` Właściwość określa, czy transakcja, w której wykonuje metodę jest wprowadzana automatycznie, jeśli wystąpi żaden nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-131">The `TransactionAutoComplete` property specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions occur.</span></span> <span data-ttu-id="ebb6b-132">Jak opisano wcześniej, to ma ustawioną wartość `true` operacji Dodawanie i odejmowanie, ale `false` Multiply i operacji dzielenia.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-132">As previously described, this is set to `true` for the Add and Subtract operations but `false` for the Multiply and Divide operations.</span></span> <span data-ttu-id="ebb6b-133">Dodawanie i odejmowanie operacji wykonania swoich akcji automatycznie, dzielenia zakończeniem za pomocą jawnego wywołania do `SetTransactionComplete` — metoda i Multiply nie zakończy działania, ale zamiast tego opiera się i wymaga nowszej wywołanie, takich jak Dzielenie, aby wykonać akcje.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-133">The Add and Subtract operations complete their actions automatically, the Divide completes its actions through an explicit call to the `SetTransactionComplete` method, and the Multiply does not complete its actions but instead relies upon and requires a later call, such as to Divide, to complete the actions.</span></span>  
  
 <span data-ttu-id="ebb6b-134">Implementacja usługi oparte na atrybutach wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="ebb6b-134">The attributed service implementation is as follows:</span></span>  
  
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
  
 <span data-ttu-id="ebb6b-135">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-135">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ebb6b-136">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-136">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
 <span data-ttu-id="ebb6b-137">Rejestrowanie żądań operacji usługi są wyświetlane w oknie konsoli usługi.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-137">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="ebb6b-138">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-138">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate service.  
Creating new service instance...  
  Writing row 1 to database: Adding 100 to 0  
  Writing row 2 to database: Subtracting 45 from 100  
  Writing row 3 to database: Multiplying 55 by 9  
  Writing row 4 to database: Dividing 495 by 15  
```  
  
 <span data-ttu-id="ebb6b-139">Należy pamiętać, że oprócz zachowaniu całkowitej działanie obliczeń, usługa raporty tworzenia wystąpień (jedno wystąpienie dla tego przykładu) i rejestruje żądania operacji do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-139">Note that in addition to keeping the running total of the calculations, the service reports the creation of instances (one instance for this sample) and logs the operation requests to a database.</span></span> <span data-ttu-id="ebb6b-140">Ponieważ wszystkie żądania przepływu transakcji klienta, jakiekolwiek niepowodzenie do ukończenia tej transakcji powoduje wszystkie operacje bazy danych Trwa wycofywanie.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-140">Because all of the requests flow the client's transaction, any failure to complete that transaction results in all of the database operations being rolled back.</span></span> <span data-ttu-id="ebb6b-141">Mogą to być przedstawiane na kilka różnych sposobów:</span><span class="sxs-lookup"><span data-stu-id="ebb6b-141">This can be demonstrated in a number of ways:</span></span>  
  
-   <span data-ttu-id="ebb6b-142">Komentarz wywołania klienta `tx.Complete`() i uruchom ponownie — spowoduje to klienta Kończenie zakresu transakcji bez ukończenia transakcji.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-142">Comment out the client's call to `tx.Complete`() and rerun - this results in the client exiting the transaction scope without completing its transaction.</span></span>  
  
-   <span data-ttu-id="ebb6b-143">Komentarz dotyczący out wywołania operacji usługi dzielenia — powoduje to zapobiec zainicjowane przez akcję mnożenia ukończenie operacji i w związku z tym transakcji klienta ostatecznie również nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-143">Comment out the call to the Divide service operation - this results prevent the action initiated by the Multiply operation from completing and thus the client's transaction ultimately also fails to complete.</span></span>  
  
-   <span data-ttu-id="ebb6b-144">Throw Wystąpił nieobsługiwany wyjątek w dowolnym miejscu w zakresie transakcji klienta — podobnie zapobiega to klient wykonanie jego transakcji.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-144">Throw an unhandled exception anywhere in the client's transaction scope - this similarly prevents the client from completing its transaction.</span></span>  
  
 <span data-ttu-id="ebb6b-145">Wynikiem tych jest żadna z operacji wykonywanych w tym zakresie nie jest zatwierdzona, a liczba wierszy utrwalone w bazie danych zwiększa się.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-145">The result of any of these is that none of the operations performed within that scope are committed and the count of rows persisted to the database do not increment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebb6b-146">W ramach procesu tworzenia pliku bazy danych jest kopiowany do folderu bin.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-146">As part of the build process the database file is copied to the bin folder.</span></span> <span data-ttu-id="ebb6b-147">Należy przyjrzeć się tej kopii pliku bazy danych do przestrzegania tych wierszy, które są zachowywane w dzienniku, a nie w pliku, który jest dołączony do projektu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-147">You must look at that copy of the database file to observe the rows that are persisted to the log rather than the file that is included in the Visual Studio project.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ebb6b-148">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="ebb6b-148">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ebb6b-149">Upewnij się, że zainstalowano program SQL Server 2005 Express Edition lub SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-149">Ensure that you have installed SQL Server 2005 Express Edition or SQL Server 2005.</span></span> <span data-ttu-id="ebb6b-150">W pliku App.config usługi bazy danych `connectionString` może być zestawu lub baza danych interakcje mogą być wyłączone przez ustawienia appSettings `usingSql` do wartości `false`.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-150">In the service's App.config file, the database `connectionString` may be set or the database interactions may be disabled by setting the appSettings `usingSql` value to `false`.</span></span>  
  
2.  <span data-ttu-id="ebb6b-151">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ebb6b-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ebb6b-152">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ebb6b-152">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="ebb6b-153">Po uruchomieniu próbki na komputerach, należy skonfigurować MSDTC Microsoft Distributed Transaction Coordinator () do włączenia przepływu transakcji sieci i włączyć za pomocą narzędzia WsatConfig.exe [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transakcji sieci pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-153">If you run the sample across machines, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a><span data-ttu-id="ebb6b-154">Aby skonfigurować MSDTC Microsoft Distributed Transaction Coordinator () do obsługi systemem próbki na komputerach</span><span class="sxs-lookup"><span data-stu-id="ebb6b-154">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample across machines</span></span>  
  
1.  <span data-ttu-id="ebb6b-155">Na komputerze usługi należy skonfigurować usługi MSDTC, aby umożliwić przychodzących transakcji sieci.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-155">On the service machine, configure MSDTC to allow incoming network transactions.</span></span>  
  
    1.  <span data-ttu-id="ebb6b-156">Z **Start** menu, przejdź do **Panelu sterowania**, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-156">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="ebb6b-157">Kliknij prawym przyciskiem myszy **Mój komputer** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-157">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="ebb6b-158">Na **MSDTC** , kliknij pozycję **konfiguracji zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-158">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="ebb6b-159">Sprawdź **sieci dostęp do usługi DTC** i **Zezwalaj na przychodzące**.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-159">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5.  <span data-ttu-id="ebb6b-160">Kliknij przycisk **tak** Uruchom ponownie usługę MS DTC, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-160">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="ebb6b-161">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-161">Click **OK** to close the dialog box.</span></span>  
  
2.  <span data-ttu-id="ebb6b-162">Na komputerze usługi i na komputerze klienta należy skonfigurować zapory systemu Windows, aby uwzględnić MSDTC Microsoft Distributed Transaction Coordinator () do listy aplikacji wyjątku:</span><span class="sxs-lookup"><span data-stu-id="ebb6b-162">On the service machine and the client machine, configure the Windows Firewall to include the Microsoft Distributed Transaction Coordinator (MSDTC) to the list of excepted applications:</span></span>  
  
    1.  <span data-ttu-id="ebb6b-163">Uruchom aplikację Zapora systemu Windows w Panelu sterowania.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-163">Run the Windows Firewall application from Control Panel.</span></span>  
  
    2.  <span data-ttu-id="ebb6b-164">Z **wyjątki** , kliknij pozycję **Dodaj Program**.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-164">From the **Exceptions** tab, click **Add Program**.</span></span>  
  
    3.  <span data-ttu-id="ebb6b-165">Przejdź do folderu C:\WINDOWS\System32.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-165">Browse to the folder C:\WINDOWS\System32.</span></span>  
  
    4.  <span data-ttu-id="ebb6b-166">Wybierz Msdtc.exe i kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-166">Select Msdtc.exe and click **Open**.</span></span>  
  
    5.  <span data-ttu-id="ebb6b-167">Kliknij przycisk **OK** zamknąć **Dodaj Program** okno dialogowe, a następnie kliknij przycisk **OK** ponownie, aby zamknąć aplet Zapora systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-167">Click **OK** to close the **Add Program** dialog box, and click **OK** again to close the Windows Firewall applet.</span></span>  
  
3.  <span data-ttu-id="ebb6b-168">Na komputerze klienckim należy skonfigurować usługi MSDTC, aby umożliwić wychodzących transakcji sieci:</span><span class="sxs-lookup"><span data-stu-id="ebb6b-168">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1.  <span data-ttu-id="ebb6b-169">Z **Start** menu, przejdź do **Panelu sterowania**, następnie **narzędzia administracyjne**, a następnie **usługi składowe**.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2.  <span data-ttu-id="ebb6b-170">Kliknij prawym przyciskiem myszy **Mój komputer** i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-170">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="ebb6b-171">Na **MSDTC** , kliknij pozycję **konfiguracji zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-171">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4.  <span data-ttu-id="ebb6b-172">Sprawdź **sieci dostęp do usługi DTC** i **Zezwalaj na wychodzące**.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-172">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5.  <span data-ttu-id="ebb6b-173">Kliknij przycisk **tak** Uruchom ponownie usługę MS DTC, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-173">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="ebb6b-174">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-174">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ebb6b-175">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-175">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ebb6b-176">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ebb6b-176">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ebb6b-177">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-177">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ebb6b-178">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ebb6b-178">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`  
  
## <a name="see-also"></a><span data-ttu-id="ebb6b-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebb6b-179">See Also</span></span>
