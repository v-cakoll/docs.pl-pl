---
title: Oczekiwane wyjątki
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 7611b070df31b7a0997a94c07594716ee264af5e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961595"
---
# <a name="expected-exceptions"></a><span data-ttu-id="ef75d-102">Oczekiwane wyjątki</span><span class="sxs-lookup"><span data-stu-id="ef75d-102">Expected Exceptions</span></span>
<span data-ttu-id="ef75d-103">Ten przykład pokazuje, jak przechwytywać oczekiwane wyjątki przy użyciu klienta z określonym typem.</span><span class="sxs-lookup"><span data-stu-id="ef75d-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="ef75d-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="ef75d-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="ef75d-105">W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="ef75d-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef75d-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ef75d-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ef75d-107">W tym przykładzie pokazano, jak przechwytywać i obsługiwać dwa oczekiwane typy wyjątków, które muszą `TimeoutException` być `CommunicationException`obsługiwane przez poprawne programy: i.</span><span class="sxs-lookup"><span data-stu-id="ef75d-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="ef75d-108">Wyjątki generowane przez metody komunikacji na kliencie Windows Communication Foundation (WCF) są oczekiwane lub nieoczekiwane.</span><span class="sxs-lookup"><span data-stu-id="ef75d-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="ef75d-109">Nieoczekiwane wyjątki obejmują katastrofalne błędy, takie `OutOfMemoryException` jak `InvalidOperationException`i błędy programowania, takie jak `ArgumentNullException` lub.</span><span class="sxs-lookup"><span data-stu-id="ef75d-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="ef75d-110">Zazwyczaj nie istnieje użyteczny sposób obsługi nieoczekiwanych błędów, więc zazwyczaj nie należy ich przechwytywać podczas wywoływania metody komunikacji z klientem WCF.</span><span class="sxs-lookup"><span data-stu-id="ef75d-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="ef75d-111">Oczekiwane wyjątki z metod komunikacji na kliencie WCF obejmują `TimeoutException`, `CommunicationException` `CommunicationException`i dowolną klasę pochodną.</span><span class="sxs-lookup"><span data-stu-id="ef75d-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="ef75d-112">Wskazuje to na problem podczas komunikacji, która może być bezpiecznie obsługiwana przez przerwanie działania klienta programu WCF i Raportowanie błędu komunikacji.</span><span class="sxs-lookup"><span data-stu-id="ef75d-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="ef75d-113">Ze względu na to, że zewnętrzne czynniki mogą spowodować te błędy w dowolnej aplikacji, poprawne aplikacje muszą przechwycić te wyjątki i odzyskać je po wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="ef75d-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="ef75d-114">Istnieje kilka klas `CommunicationException` pochodnych, które klient może zgłosić.</span><span class="sxs-lookup"><span data-stu-id="ef75d-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="ef75d-115">W niektórych przypadkach aplikacje przechwytuje niektóre z nich w celu przeprowadzenia specjalnej obsługi, ale pozwól, aby inne osoby `CommunicationException`były obsługiwane jako.</span><span class="sxs-lookup"><span data-stu-id="ef75d-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="ef75d-116">Można to osiągnąć przez przechwycenie najpierw określonego typu wyjątku, a następnie przechwycenie `CommunicationException` w późniejszej klauzuli catch.</span><span class="sxs-lookup"><span data-stu-id="ef75d-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="ef75d-117">Kod, który wywołuje metodę komunikacji klienta, musi `TimeoutException` przechwycić `CommunicationException`i.</span><span class="sxs-lookup"><span data-stu-id="ef75d-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="ef75d-118">Jednym ze sposobów obsługi takich błędów jest przerwanie działania klienta i zgłaszanie błędu komunikacji.</span><span class="sxs-lookup"><span data-stu-id="ef75d-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
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
  
 <span data-ttu-id="ef75d-119">Jeśli wystąpi oczekiwany wyjątek, klient może lub nie może być później używany.</span><span class="sxs-lookup"><span data-stu-id="ef75d-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="ef75d-120">Aby określić, czy klient jest nadal zdatny do użytku, `State` Sprawdź, `CommunicationState`czy właściwość jest. Otworzyć.</span><span class="sxs-lookup"><span data-stu-id="ef75d-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="ef75d-121">Jeśli nadal jest otwarty, nadal będzie można go użyć.</span><span class="sxs-lookup"><span data-stu-id="ef75d-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="ef75d-122">W przeciwnym razie należy przerwać klienta i zwolnić wszystkie odwołania do niego.</span><span class="sxs-lookup"><span data-stu-id="ef75d-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ef75d-123">Można zauważyć, że klienci, którzy mają sesję, często nie mogą już korzystać z programu po wystąpieniu wyjątku, a klienci, którzy nie mają sesji, często nadal mogą korzystać po wystąpieniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ef75d-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="ef75d-124">Jednak żadna z nich nie jest gwarantowana, więc jeśli chcesz spróbować kontynuować korzystanie z klienta po wystąpieniu wyjątku, aplikacja powinna sprawdzić `State` właściwość, aby sprawdzić, czy klient jest nadal otwarty.</span><span class="sxs-lookup"><span data-stu-id="ef75d-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="ef75d-125">Po uruchomieniu przykładu odpowiedzi operacji i wyjątki są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="ef75d-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="ef75d-126">Proces klienta uruchamia dwa scenariusze, z których każdy próbuje wywołać wywołanie `Add`. `Divide`</span><span class="sxs-lookup"><span data-stu-id="ef75d-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="ef75d-127">Pierwszy scenariusz symuluje problem z siecią, przerywając działanie klienta przed wywołaniem do `Divide`programu.</span><span class="sxs-lookup"><span data-stu-id="ef75d-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="ef75d-128">Drugi scenariusz powoduje przekroczenie limitu czasu przez ustawienie przekroczenia limitu czasu, aby można było ukończyć metodę.</span><span class="sxs-lookup"><span data-stu-id="ef75d-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="ef75d-129">Oczekiwane dane wyjściowe procesu klienta to:</span><span class="sxs-lookup"><span data-stu-id="ef75d-129">The expected output from the client process is:</span></span>  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ef75d-130">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="ef75d-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ef75d-131">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef75d-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ef75d-132">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef75d-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ef75d-133">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef75d-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ef75d-134">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="ef75d-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ef75d-135">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="ef75d-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ef75d-136">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="ef75d-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ef75d-137">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ef75d-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
