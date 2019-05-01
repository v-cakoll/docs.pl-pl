---
title: Oczekiwane wyjątki
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 3add9faa9a07249639c1ff3e83469d0634008472
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990200"
---
# <a name="expected-exceptions"></a><span data-ttu-id="cdf4b-102">Oczekiwane wyjątki</span><span class="sxs-lookup"><span data-stu-id="cdf4b-102">Expected Exceptions</span></span>
<span data-ttu-id="cdf4b-103">W tym przykładzie pokazano, jak przechwytywać wyjątki oczekiwane, korzystając z klient z typowaniem.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="cdf4b-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="cdf4b-105">W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="cdf4b-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdf4b-106">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cdf4b-107">Niniejszy przykład pokazuje, przechwytywanie i dwa typy oczekiwanego wyjątku, które poprawić programy obsługi musi obsługiwać: `TimeoutException` i `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="cdf4b-108">Wyjątki, które są generowane przez metody komunikacji w kliencie programu Windows Communication Foundation (WCF) są oczekiwane lub nieoczekiwany.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="cdf4b-109">Nieoczekiwane wyjątki obejmują katastrofalnych awarii, takich jak `OutOfMemoryException` i błędy programowania, takich jak `ArgumentNullException` lub `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="cdf4b-110">Zazwyczaj jest przydatny sposób obsługi nieoczekiwanych błędów, więc zazwyczaj nie należy przechwytywać je podczas wywoływania metody komunikacji klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="cdf4b-111">Oczekiwane wyjątki od metod komunikacji klienta programu WCF obejmują `TimeoutException`, `CommunicationException`, oraz wszelkie otrzymane klasy `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="cdf4b-112">Oznaczają one problem podczas komunikacji, który może być bezpiecznie obsługiwane przez przerywanie klienta WCF i zgłaszanie błędu komunikacji.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="cdf4b-113">Ponieważ czynniki zewnętrzne mogą spowodować błędy w dowolnej aplikacji, poprawny aplikacji należy przechwytywać te wyjątki i odzyskiwanie po ich wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="cdf4b-114">Istnieje kilka klas pochodnych `CommunicationException` który klient może zgłosić.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="cdf4b-115">W niektórych przypadkach aplikacje również catch niektóre z nich są specjalnej obsługi, ale inni obsługiwany jako `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="cdf4b-116">Można to zrobić, najpierw Przechwytywanie bardziej specyficznego typu wyjątku i następnie Przechwytywanie `CommunicationException` w późniejszym klauzuli catch.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="cdf4b-117">Kod, który wywołuje metodę komunikacji klienta należy wyłapać `TimeoutException` i `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="cdf4b-118">Jest jednym ze sposobów, aby obsłużyć takie błędy przerwać klienta i zgłoś błąd komunikacji.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
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
  
 <span data-ttu-id="cdf4b-119">Jeśli wystąpi oczekiwanego wyjątku, klient może lub może nie dawać później.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="cdf4b-120">Aby ustalić, czy klient jest nadal można używać, sprawdź, czy `State` właściwość `CommunicationState`. Otwarty.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="cdf4b-121">Jeśli jest wciąż otwarty, jest nadal można używać.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="cdf4b-122">W przeciwnym razie należy przerwać klienta i zwolnić wszystkie odwołania do niego.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="cdf4b-123">Można zaobserwować, że klienci, którzy mają sesję często nie są już można używać po wystąpieniu wyjątku, i klienci, którzy nie mają sesji są często nadal można używać po wystąpieniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="cdf4b-124">Jednak żadnej z tych metod jest gwarantowane, więc jeśli chcesz podjąć próbę kontynuowania działania przy użyciu klienta po wystąpieniu wyjątku, Twoja aplikacja ma sprawdzać `State` właściwości, aby sprawdzić, klient jest wciąż otwarty.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="cdf4b-125">Po uruchomieniu przykładu odpowiedzi operacji i wyjątków są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="cdf4b-126">Proces klienta jest uruchamiane dwa scenariusze, każda z których próby wywołania `Add` następuje `Divide`.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="cdf4b-127">Pierwszy scenariusz symuluje problem z siecią przerywanie klienta przed wprowadzeniem wywołanie `Divide`.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="cdf4b-128">Drugi scenariusz powoduje, że warunek limitu czasu przez ustawienie limitu czasu zbyt mała w przypadku metody, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="cdf4b-129">Oczekiwane dane wyjściowe z procesu klienta jest:</span><span class="sxs-lookup"><span data-stu-id="cdf4b-129">The expected output from the client process is:</span></span>  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cdf4b-130">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="cdf4b-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cdf4b-131">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cdf4b-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cdf4b-132">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cdf4b-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="cdf4b-133">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cdf4b-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cdf4b-134">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cdf4b-135">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="cdf4b-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cdf4b-136">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cdf4b-137">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cdf4b-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
