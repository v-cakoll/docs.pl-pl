---
title: Oczekiwane wyjątki
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 24bb9b483a3f26241f895d68b763a1974b02151b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716451"
---
# <a name="expected-exceptions"></a><span data-ttu-id="a7e73-102">Oczekiwane wyjątki</span><span class="sxs-lookup"><span data-stu-id="a7e73-102">Expected Exceptions</span></span>
<span data-ttu-id="a7e73-103">Ten przykład pokazuje, jak przechwytywać oczekiwane wyjątki przy użyciu klienta z określonym typem.</span><span class="sxs-lookup"><span data-stu-id="a7e73-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="a7e73-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="a7e73-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="a7e73-105">W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="a7e73-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7e73-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a7e73-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a7e73-107">W tym przykładzie pokazano, jak przechwytywać i obsługiwać dwa oczekiwane typy wyjątków, które muszą być obsługiwane przez poprawne programy: `TimeoutException` i `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="a7e73-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="a7e73-108">Wyjątki generowane przez metody komunikacji na kliencie Windows Communication Foundation (WCF) są oczekiwane lub nieoczekiwane.</span><span class="sxs-lookup"><span data-stu-id="a7e73-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="a7e73-109">Nieoczekiwane wyjątki obejmują błędy katastrofalne, takie jak `OutOfMemoryException` i programowanie błędów, takich jak `ArgumentNullException` lub `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="a7e73-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="a7e73-110">Zazwyczaj nie istnieje użyteczny sposób obsługi nieoczekiwanych błędów, więc zazwyczaj nie należy ich przechwytywać podczas wywoływania metody komunikacji z klientem WCF.</span><span class="sxs-lookup"><span data-stu-id="a7e73-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="a7e73-111">Oczekiwane wyjątki od metod komunikacji na kliencie programu WCF obejmują `TimeoutException`, `CommunicationException`i dowolną klasę pochodną `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="a7e73-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="a7e73-112">Wskazuje to na problem podczas komunikacji, która może być bezpiecznie obsługiwana przez przerwanie działania klienta programu WCF i Raportowanie błędu komunikacji.</span><span class="sxs-lookup"><span data-stu-id="a7e73-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="a7e73-113">Ze względu na to, że zewnętrzne czynniki mogą spowodować te błędy w dowolnej aplikacji, poprawne aplikacje muszą przechwycić te wyjątki i odzyskać je po wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="a7e73-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="a7e73-114">Istnieje kilka klas pochodnych `CommunicationException`, które klient może zgłosić.</span><span class="sxs-lookup"><span data-stu-id="a7e73-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="a7e73-115">W niektórych przypadkach aplikacje przechwytuje niektóre z nich w celu przeprowadzenia specjalnej obsługi, ale pozwól, aby inne były obsługiwane jako `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="a7e73-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="a7e73-116">Można to osiągnąć przez przechwycenie najpierw określonego typu wyjątku, a następnie przechwycenie `CommunicationException` w późniejszej klauzuli catch.</span><span class="sxs-lookup"><span data-stu-id="a7e73-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="a7e73-117">Kod, który wywołuje metodę komunikacji klienta, musi przechwycić `TimeoutException` i `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="a7e73-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="a7e73-118">Jednym ze sposobów obsługi takich błędów jest przerwanie działania klienta i zgłaszanie błędu komunikacji.</span><span class="sxs-lookup"><span data-stu-id="a7e73-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```csharp   
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="a7e73-119">Jeśli wystąpi oczekiwany wyjątek, klient może lub nie może być później używany.</span><span class="sxs-lookup"><span data-stu-id="a7e73-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="a7e73-120">Aby określić, czy klient jest nadal zdatny do użytku, sprawdź, czy właściwość `State` jest `CommunicationState`. Otworzyć.</span><span class="sxs-lookup"><span data-stu-id="a7e73-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="a7e73-121">Jeśli nadal jest otwarty, nadal będzie można go użyć.</span><span class="sxs-lookup"><span data-stu-id="a7e73-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="a7e73-122">W przeciwnym razie należy przerwać klienta i zwolnić wszystkie odwołania do niego.</span><span class="sxs-lookup"><span data-stu-id="a7e73-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="a7e73-123">Można zauważyć, że klienci, którzy mają sesję, często nie mogą już korzystać z programu po wystąpieniu wyjątku, a klienci, którzy nie mają sesji, często nadal mogą korzystać po wystąpieniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a7e73-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="a7e73-124">Jednak żadna z nich nie jest gwarantowana, więc jeśli chcesz spróbować kontynuować korzystanie z klienta po wystąpieniu wyjątku, aplikacja powinna sprawdzić Właściwość `State`, aby sprawdzić, czy klient jest nadal otwarty.</span><span class="sxs-lookup"><span data-stu-id="a7e73-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="a7e73-125">Po uruchomieniu przykładu odpowiedzi operacji i wyjątki są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="a7e73-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="a7e73-126">Proces klienta uruchamia dwa scenariusze, z których każdy próbuje wywołać `Add` a następnie `Divide`.</span><span class="sxs-lookup"><span data-stu-id="a7e73-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="a7e73-127">Pierwszy scenariusz symuluje problem z siecią, przerywając działanie klienta przed wywołaniem `Divide`.</span><span class="sxs-lookup"><span data-stu-id="a7e73-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="a7e73-128">Drugi scenariusz powoduje przekroczenie limitu czasu przez ustawienie przekroczenia limitu czasu, aby można było ukończyć metodę.</span><span class="sxs-lookup"><span data-stu-id="a7e73-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="a7e73-129">Oczekiwane dane wyjściowe procesu klienta to:</span><span class="sxs-lookup"><span data-stu-id="a7e73-129">The expected output from the client process is:</span></span>  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a7e73-130">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="a7e73-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a7e73-131">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a7e73-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a7e73-132">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a7e73-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a7e73-133">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a7e73-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a7e73-134">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a7e73-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a7e73-135">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="a7e73-135">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="a7e73-136">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a7e73-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a7e73-137">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a7e73-137">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
