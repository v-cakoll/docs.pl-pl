---
title: Oczekiwane wyjątki
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 6c4af62e0870cdd670c46ead169033ff72902fc0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="expected-exceptions"></a><span data-ttu-id="d826b-102">Oczekiwane wyjątki</span><span class="sxs-lookup"><span data-stu-id="d826b-102">Expected Exceptions</span></span>
<span data-ttu-id="d826b-103">W tym przykładzie pokazano, jak catch oczekiwane wyjątki, używając typu klienta.</span><span class="sxs-lookup"><span data-stu-id="d826b-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="d826b-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="d826b-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="d826b-105">W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="d826b-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d826b-106">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d826b-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d826b-107">W tym przykładzie pokazano przechwytywanie i dwa typy oczekiwanego wyjątku, które Popraw programy obsługi musi obsługiwać: `TimeoutException` i `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="d826b-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="d826b-108">Wyjątki, które są generowane z metody komunikacji na kliencie systemu Windows Communication Foundation (WCF) są oczekiwane lub nieoczekiwany.</span><span class="sxs-lookup"><span data-stu-id="d826b-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="d826b-109">Nieoczekiwany wyjątków należą poważnej awarii, takich jak `OutOfMemoryException` i programowania błędów, takich jak `ArgumentNullException` lub `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="d826b-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="d826b-110">Zwykle nie istnieje sposób przydatne do obsługi tak zwykle nie należy przechwytywać je w wywołaniu metody komunikacji klienta WCF nieoczekiwane błędy.</span><span class="sxs-lookup"><span data-stu-id="d826b-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="d826b-111">Oczekiwano obejmują wyjątki od metody komunikacji klienta WCF `TimeoutException`, `CommunicationException`, oraz wszelkie otrzymane z klasy `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="d826b-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="d826b-112">Oznaczają one problem podczas komunikacji, który można bezpiecznie obsłużyć przerywanie klienta WCF i raportowania błędów komunikacji.</span><span class="sxs-lookup"><span data-stu-id="d826b-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="d826b-113">Ponieważ czynniki zewnętrzne mogą powodować błędy w dowolnej aplikacji, poprawne aplikacji należy przechwytywać tych wyjątków i odzyskać wystąpieniach.</span><span class="sxs-lookup"><span data-stu-id="d826b-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="d826b-114">Istnieje kilka klas pochodnych `CommunicationException` który klient może zgłosić.</span><span class="sxs-lookup"><span data-stu-id="d826b-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="d826b-115">W niektórych przypadkach aplikacji również catch niektóre z nich, aby nie specjalnej obsługi, ale inni traktowane jako `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="d826b-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="d826b-116">Można to zrobić przez najpierw Przechwytywanie więcej określony typ wyjątku, a następnie Przechwytywanie `CommunicationException` w późniejszym klauzuli catch.</span><span class="sxs-lookup"><span data-stu-id="d826b-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="d826b-117">Kod, który wywołuje metodę komunikacji z klientem muszą catch `TimeoutException` i `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="d826b-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="d826b-118">Jednym ze sposobów obsługi tych błędów ma przerwać klienta i zgłoś błąd komunikacji.</span><span class="sxs-lookup"><span data-stu-id="d826b-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
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
  
 <span data-ttu-id="d826b-119">Sytuacji oczekiwanego wyjątku klient może lub nie można używać później.</span><span class="sxs-lookup"><span data-stu-id="d826b-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="d826b-120">Aby ustalić, czy klient jest nadal można używać, sprawdź, czy `State` jest właściwość `CommunicationState`. Otwarty.</span><span class="sxs-lookup"><span data-stu-id="d826b-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="d826b-121">Jeśli jest wciąż otwarty, następnie jest nadal możliwe.</span><span class="sxs-lookup"><span data-stu-id="d826b-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="d826b-122">W przeciwnym razie należy przerwać klienta i zwolnić wszystkie odwołania do niego.</span><span class="sxs-lookup"><span data-stu-id="d826b-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="d826b-123">Można zauważyć, że klienci, którzy mają sesję często nie są już można używać po wystąpieniu wyjątku i klientów, którzy nie mają sesji są wciąż często można używać po wystąpieniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="d826b-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="d826b-124">Jednak żadnej z tych jest gwarantowana, dlatego jeśli chcesz spróbować kontynuowanie po wystąpieniu wyjątku, zapoznaj się z aplikacji przy użyciu klienta `State` właściwości, aby sprawdzić, klient jest nadal otwarty.</span><span class="sxs-lookup"><span data-stu-id="d826b-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="d826b-125">Po uruchomieniu próbki odpowiedzi operacji i wyjątków są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="d826b-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="d826b-126">Proces klienta uruchamia dwa scenariusze każdego podejmuje próbę nawiązania `Add` następuje `Divide`.</span><span class="sxs-lookup"><span data-stu-id="d826b-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="d826b-127">Pierwszy scenariusz symuluje problem z siecią przez przerywanie klienta przed wprowadzeniem wywołanie `Divide`.</span><span class="sxs-lookup"><span data-stu-id="d826b-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="d826b-128">Drugi scenariusz powoduje, że warunek limitu czasu przez ustawienie limitu czasu zbyt krótka dla metody, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="d826b-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="d826b-129">Oczekiwane dane wyjściowe z procesu klienta jest:</span><span class="sxs-lookup"><span data-stu-id="d826b-129">The expected output from the client process is:</span></span>  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d826b-130">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="d826b-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d826b-131">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d826b-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d826b-132">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d826b-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d826b-133">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d826b-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d826b-134">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d826b-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d826b-135">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="d826b-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d826b-136">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="d826b-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d826b-137">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d826b-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
  
## <a name="see-also"></a><span data-ttu-id="d826b-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d826b-138">See Also</span></span>
