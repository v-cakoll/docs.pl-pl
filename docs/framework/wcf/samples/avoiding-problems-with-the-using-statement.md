---
title: Unikanie problemów z instrukcją Using
ms.date: 03/30/2017
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 14a0649c9996158f1503581c906d8dfd1a95ebc8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33503901"
---
# <a name="avoiding-problems-with-the-using-statement"></a><span data-ttu-id="23542-102">Unikanie problemów z instrukcją Using</span><span class="sxs-lookup"><span data-stu-id="23542-102">Avoiding Problems with the Using Statement</span></span>
<span data-ttu-id="23542-103">W przykładzie pokazano, jak nie należy używać "using" — instrukcja automatycznie wyczyścić zasobów, korzystając z klienta typu C#.</span><span class="sxs-lookup"><span data-stu-id="23542-103">This sample demonstrates how you should not use the C# "using" statement to automatically clean up resources when using a typed client.</span></span> <span data-ttu-id="23542-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="23542-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="23542-105">W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="23542-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23542-106">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="23542-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="23542-107">Ten przykład przedstawia dwa typowych problemów występujących podczas przy użyciu "Używanie" instrukcji z klientów typu, a także kod, który prawidłowo czyści po wyjątków języka C#.</span><span class="sxs-lookup"><span data-stu-id="23542-107">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>  
  
 <span data-ttu-id="23542-108">C# instrukcję "using" powoduje wywołanie `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="23542-108">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="23542-109">To jest taka sama jak `Close`(), który może zgłaszać wyjątki po wystąpieniu błędu sieci.</span><span class="sxs-lookup"><span data-stu-id="23542-109">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="23542-110">Ponieważ wywołanie `Dispose`() odbywa się niejawnie na zamykający nawias klamrowy bloku "using", to źródło wyjątki prawdopodobne jest, aby przejść bez zwracania uwagi zarówno przez osoby pisanie kodu i odczytywania kod.</span><span class="sxs-lookup"><span data-stu-id="23542-110">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="23542-111">Stanowi to potencjalne źródło błędów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="23542-111">This represents a potential source of application errors.</span></span>  
  
 <span data-ttu-id="23542-112">Pierwszy problem, przedstawiono w `DemonstrateProblemUsingCanThrow` metoda, to czy zamykający nawias klamrowy zgłasza wyjątek i kod po nawias zamykający nie wykonuj:</span><span class="sxs-lookup"><span data-stu-id="23542-112">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 <span data-ttu-id="23542-113">Nawet jeśli żadne wewnątrz przy użyciu bloków zwraca wyjątek lub wszystkie wyjątki wewnątrz przy użyciu bloku są przechwytywane, `Console.Writeline` nie może być to, że niejawne `Dispose`wywołanie () w nawias zamykający może zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="23542-113">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.Writeline` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>  
  
 <span data-ttu-id="23542-114">Drugi problem, przedstawiono w `DemonstrateProblemUsingCanThrowAndMask` metoda, jest inny wpływ na zamykający nawias klamrowy zgłoszeniu wyjątku:</span><span class="sxs-lookup"><span data-stu-id="23542-114">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 <span data-ttu-id="23542-115">Ponieważ `Dispose`(), wystąpi wewnątrz bloku "finally" `ApplicationException` nigdy nie jest widoczna poza przy użyciu zablokować, jeśli `Dispose`() nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="23542-115">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="23542-116">Jeśli kod poza musi wiedzieć o tym, kiedy `ApplicationException` występuje konstrukcji "przy użyciu" może spowodować problemy przez maskowania tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="23542-116">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>  
  
 <span data-ttu-id="23542-117">Na koniec przykładzie pokazano, jak czyszczenie poprawnie, gdy wyjątki występują w `DemonstrateCleanupWithExceptions`.</span><span class="sxs-lookup"><span data-stu-id="23542-117">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="23542-118">Używa bloku try/catch w celu przesłania raportów o błędach i wywołania `Abort`.</span><span class="sxs-lookup"><span data-stu-id="23542-118">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="23542-119">Zobacz [oczekiwane wyjątki](../../../../docs/framework/wcf/samples/expected-exceptions.md) przykładowa, aby uzyskać więcej informacji o przechwytywanie wyjątków z wywołań klienta.</span><span class="sxs-lookup"><span data-stu-id="23542-119">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>  
  
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
>  <span data-ttu-id="23542-120">Przy użyciu instrukcji i ServiceHost: wiele aplikacji własnym hostingu nieco więcej niż obsługuje usługi i ServiceHost.Close rzadko zgłasza wyjątek, tak aby takich aplikacji bezpiecznie korzystać przy użyciu instrukcji z elementu ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="23542-120">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="23542-121">Należy jednak pamiętać, że może zgłosić ServiceHost.Close `CommunicationException`, więc jeśli aplikacja będzie nadal występować po zamknięciu usługi ServiceHost, należy unikać używania instrukcji i wykonaj wzorzec wcześniej podane.</span><span class="sxs-lookup"><span data-stu-id="23542-121">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>  
  
 <span data-ttu-id="23542-122">Po uruchomieniu próbki odpowiedzi operacji i wyjątków są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="23542-122">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="23542-123">Proces klienta uruchamia trzy scenariusze, każdy podejmuje próbę nawiązania `Divide`.</span><span class="sxs-lookup"><span data-stu-id="23542-123">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="23542-124">Pierwszy scenariusz pokazuje pominięte z powodu wyjątku z kodu `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="23542-124">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="23542-125">Drugi scenariusz przedstawiono ważne wyjątek maskowanego z powodu wyjątku z `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="23542-125">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="23542-126">Trzeci scenariusz przedstawiono poprawne oczyszczania.</span><span class="sxs-lookup"><span data-stu-id="23542-126">The third scenario demonstrates correct clean up.</span></span>  
  
 <span data-ttu-id="23542-127">Oczekiwane dane wyjściowe z procesu klienta jest:</span><span class="sxs-lookup"><span data-stu-id="23542-127">The expected output from the client process is:</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="23542-128">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="23542-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="23542-129">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="23542-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="23542-130">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="23542-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="23542-131">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="23542-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="23542-132">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="23542-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="23542-133">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="23542-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="23542-134">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="23542-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="23542-135">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="23542-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a><span data-ttu-id="23542-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23542-136">See Also</span></span>
