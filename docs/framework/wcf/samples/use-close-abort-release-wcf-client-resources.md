---
title: Użyj Zamknij i Przerwij, aby zwolnić zasoby klienta WCF
description: Dispose może zakończyć się niepowodzeniem i zgłaszają wyjątki, gdy sieć nie powiedzie się. Który może spowodować niepożądane zachowanie. Zamiast tego użyj Zamknij i Przerwij, aby zwolnić zasoby klienta, gdy sieć nie powiodło się.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 4996ccba955d7946bb76b8124b8b28d803b6f3e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736432"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a><span data-ttu-id="2a043-105">Zamknij i przerwania zwolnienia zasobów bezpiecznie w przypadku, gdy połączenia sieciowe zostały odrzucone</span><span class="sxs-lookup"><span data-stu-id="2a043-105">Close and Abort release resources safely when network connections have dropped</span></span>
<span data-ttu-id="2a043-106">Ten przykład demonstruje użycie `Close` i `Abort` metody, aby wyczyścić zasoby, korzystając z klient z typowaniem.</span><span class="sxs-lookup"><span data-stu-id="2a043-106">This sample demonstrates using the `Close` and `Abort` methods to clean up resources when using a typed client.</span></span> <span data-ttu-id="2a043-107">`using` Instrukcja powoduje wyjątki, gdy połączenie sieciowe działa niezawodnie.</span><span class="sxs-lookup"><span data-stu-id="2a043-107">The `using` statement causes exceptions when the network connection is not robust.</span></span> <span data-ttu-id="2a043-108">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="2a043-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="2a043-109">W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="2a043-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a043-110">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2a043-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2a043-111">W tym przykładzie przedstawiono dwie typowe problemy, które występuje w przypadku użycia "za pomocą" instrukcji z kontrolą typów klientów, a także kod, który prawidłowo czyści po wyjątków języka C#.</span><span class="sxs-lookup"><span data-stu-id="2a043-111">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>  
  
 <span data-ttu-id="2a043-112">C# instrukcję "using" powoduje wywołanie `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="2a043-112">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="2a043-113">To jest taka sama jak `Close`(), który może zgłaszać wyjątki, gdy wystąpi błąd sieci.</span><span class="sxs-lookup"><span data-stu-id="2a043-113">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="2a043-114">Ponieważ wywołanie `Dispose`() odbywa się domyślnie na zamykający nawias klamrowy w bloku "za pomocą", to źródło wyjątków jest prawdopodobnie przejście bez zwracania uwagi zarówno przez osoby, pisanie kodu i kodu.</span><span class="sxs-lookup"><span data-stu-id="2a043-114">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="2a043-115">Reprezentuje potencjalnym źródłem błędów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2a043-115">This represents a potential source of application errors.</span></span>  
  
 <span data-ttu-id="2a043-116">Pierwszy problem, przedstawionych `DemonstrateProblemUsingCanThrow` metody jest, że zamykającego nawiasu klamrowego zgłasza wyjątek i kod po nawias zamykający nie jest wykonywane:</span><span class="sxs-lookup"><span data-stu-id="2a043-116">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 <span data-ttu-id="2a043-117">Nawet wtedy, gdy nic wewnątrz przy użyciu block, zgłasza wyjątek, który lub wszystkie wyjątki wewnątrz przy użyciu bloku zostały wykryte, `Console.Writeline` nie może być to, że niejawny `Dispose`wywołania () w zamykającego nawiasu klamrowego może zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2a043-117">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.Writeline` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>  
  
 <span data-ttu-id="2a043-118">Drugi problem, przedstawionych `DemonstrateProblemUsingCanThrowAndMask` metody jest domniemanie innego elementu zamykającego nawiasu klamrowego, zostanie zgłoszony wyjątek:</span><span class="sxs-lookup"><span data-stu-id="2a043-118">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 <span data-ttu-id="2a043-119">Ponieważ `Dispose`() odbywa się wewnątrz bloku "finally" `ApplicationException` nigdy nie są widoczne poza używając zablokować, jeśli `Dispose`() nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="2a043-119">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="2a043-120">Jeśli kod poza musisz wiedzieć o tym, kiedy `ApplicationException` występuje w konstrukcji "using" może spowodować problemy, maskując tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2a043-120">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>  
  
 <span data-ttu-id="2a043-121">Ponadto w przykładzie pokazano jak wyczyścić poprawnie, gdy wyjątki występują w `DemonstrateCleanupWithExceptions`.</span><span class="sxs-lookup"><span data-stu-id="2a043-121">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="2a043-122">Ta metoda korzysta z bloku try/catch, aby raportowanie błędów, a następnie wywołać `Abort`.</span><span class="sxs-lookup"><span data-stu-id="2a043-122">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="2a043-123">Zobacz [oczekiwane wyjątki](../../../../docs/framework/wcf/samples/expected-exceptions.md) przykładowe więcej szczegółowych informacji dotyczących przechwytywania wyjątków z wywołań klienta.</span><span class="sxs-lookup"><span data-stu-id="2a043-123">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>  
  
```csharp   
try  
{  
    ...  
    client.Close();  
}  
catch (CommunicationException e)  
{  
    ...  
    client.Abort();  
}  
catch (TimeoutException e)  
{  
    ...  
    client.Abort();  
}  
catch (Exception e)  
{  
    ...  
    client.Abort();  
    throw;  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="2a043-124">Za pomocą instrukcji i ServiceHost: Wiele aplikacji samodzielnie hostingu nieco ponad hostowanie usługi i ServiceHost.Close rzadko zgłasza wyjątek, więc takie aplikacje mogą bezpiecznie korzystać przy użyciu instrukcji za pomocą elementu ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="2a043-124">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="2a043-125">Należy jednak pamiętać, że może zgłosić ServiceHost.Close `CommunicationException`, więc jeśli aplikacja będzie nadal występował po zamknięciu elementu ServiceHost, należy unikać używania instrukcji i postępuj zgodnie z wzorcem podane wcześniej.</span><span class="sxs-lookup"><span data-stu-id="2a043-125">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>  
  
 <span data-ttu-id="2a043-126">Po uruchomieniu przykładu odpowiedzi operacji i wyjątków są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="2a043-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="2a043-127">Proces klienta uruchamia trzy scenariusze, każda z których próby wywołania `Divide`.</span><span class="sxs-lookup"><span data-stu-id="2a043-127">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="2a043-128">Pierwszy scenariusz pokazuje kod pominięte z powodu wyjątku z `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="2a043-128">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="2a043-129">Drugi scenariusz pokazuje ważny wyjątek maskowaniu z powodu wyjątku z `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="2a043-129">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="2a043-130">Trzeci scenariusz pokazuje poprawne oczyszczania.</span><span class="sxs-lookup"><span data-stu-id="2a043-130">The third scenario demonstrates correct clean up.</span></span>  
  
 <span data-ttu-id="2a043-131">Oczekiwane dane wyjściowe z procesu klienta jest:</span><span class="sxs-lookup"><span data-stu-id="2a043-131">The expected output from the client process is:</span></span>  
  
```  
=  
= Demonstrating problem:  closing brace of using statement can throw.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating cleanup with Exceptions.  
=  
Calling client.Add(0.0, 0.0);  
        client.Add(0.0, 0.0); returned 0  
Calling client.Divide(0.0, 0.0);  
Got System.ServiceModel.CommunicationException from Divide.  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2a043-132">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="2a043-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2a043-133">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2a043-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="2a043-134">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2a043-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="2a043-135">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2a043-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2a043-136">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2a043-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2a043-137">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2a043-137">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2a043-138">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="2a043-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2a043-139">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2a043-139">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a><span data-ttu-id="2a043-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a043-140">See also</span></span>
