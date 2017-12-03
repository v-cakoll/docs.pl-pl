---
title: "Oczekiwane wyjątki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 093480ae4c1932cdf3294945a3f981527cdd7a6d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="expected-exceptions"></a><span data-ttu-id="5e102-102">Oczekiwane wyjątki</span><span class="sxs-lookup"><span data-stu-id="5e102-102">Expected Exceptions</span></span>
<span data-ttu-id="5e102-103">W tym przykładzie pokazano, jak catch oczekiwane wyjątki, używając typu klienta.</span><span class="sxs-lookup"><span data-stu-id="5e102-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="5e102-104">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="5e102-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="5e102-105">W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="5e102-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e102-106">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5e102-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5e102-107">W tym przykładzie pokazano przechwytywanie i dwa typy oczekiwanego wyjątku, które Popraw programy obsługi musi obsługiwać: `TimeoutException` i `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="5e102-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="5e102-108">Wyjątki, które są generowane z metody komunikacji na [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta są oczekiwane lub nieoczekiwany.</span><span class="sxs-lookup"><span data-stu-id="5e102-108">Exceptions that are thrown from communication methods on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client are either expected or unexpected.</span></span> <span data-ttu-id="5e102-109">Nieoczekiwany wyjątków należą poważnej awarii, takich jak `OutOfMemoryException` i programowania błędów, takich jak `ArgumentNullException` lub `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="5e102-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="5e102-110">Zwykle nie istnieje sposób przydatne do obsługi błędów nieoczekiwany, dlatego zazwyczaj nie należy przechwytywać ich podczas wywoływania metody [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] metodę komunikacji z klientem.</span><span class="sxs-lookup"><span data-stu-id="5e102-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client communication method.</span></span>  
  
 <span data-ttu-id="5e102-111">Oczekiwano wyjątki od metody komunikacji na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta obejmują `TimeoutException`, `CommunicationException`, oraz wszelkie otrzymane z klasy `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="5e102-111">Expected exceptions from communication methods on a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="5e102-112">Te wskazują na problem podczas komunikacji, który może być bezpiecznie obsługiwanych przez przerywanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta oraz raportowania błędów komunikacji.</span><span class="sxs-lookup"><span data-stu-id="5e102-112">These indicate a problem during communication that can be safely handled by aborting the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and reporting a communication failure.</span></span> <span data-ttu-id="5e102-113">Ponieważ czynniki zewnętrzne mogą powodować błędy w dowolnej aplikacji, poprawne aplikacji należy przechwytywać tych wyjątków i odzyskać wystąpieniach.</span><span class="sxs-lookup"><span data-stu-id="5e102-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="5e102-114">Istnieje kilka klas pochodnych `CommunicationException` który klient może zgłosić.</span><span class="sxs-lookup"><span data-stu-id="5e102-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="5e102-115">W niektórych przypadkach aplikacji również catch niektóre z nich, aby nie specjalnej obsługi, ale inni traktowane jako `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="5e102-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="5e102-116">Można to zrobić przez najpierw Przechwytywanie więcej określony typ wyjątku, a następnie Przechwytywanie `CommunicationException` w późniejszym klauzuli catch.</span><span class="sxs-lookup"><span data-stu-id="5e102-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="5e102-117">Kod, który wywołuje metodę komunikacji z klientem muszą catch `TimeoutException` i `CommunicationException`.</span><span class="sxs-lookup"><span data-stu-id="5e102-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="5e102-118">Jednym ze sposobów obsługi tych błędów ma przerwać klienta i zgłoś błąd komunikacji.</span><span class="sxs-lookup"><span data-stu-id="5e102-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```  
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
  
 <span data-ttu-id="5e102-119">Sytuacji oczekiwanego wyjątku klient może lub nie można używać później.</span><span class="sxs-lookup"><span data-stu-id="5e102-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="5e102-120">Aby ustalić, czy klient jest nadal można używać, sprawdź, czy `State` jest właściwość `CommunicationState`. Otwarty.</span><span class="sxs-lookup"><span data-stu-id="5e102-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="5e102-121">Jeśli jest wciąż otwarty, następnie jest nadal możliwe.</span><span class="sxs-lookup"><span data-stu-id="5e102-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="5e102-122">W przeciwnym razie należy przerwać klienta i zwolnić wszystkie odwołania do niego.</span><span class="sxs-lookup"><span data-stu-id="5e102-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="5e102-123">Można zauważyć, że klienci, którzy mają sesję często nie są już można używać po wystąpieniu wyjątku i klientów, którzy nie mają sesji są wciąż często można używać po wystąpieniu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="5e102-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="5e102-124">Jednak żadnej z tych jest gwarantowana, dlatego jeśli chcesz spróbować kontynuowanie po wystąpieniu wyjątku, zapoznaj się z aplikacji przy użyciu klienta `State` właściwości, aby sprawdzić, klient jest nadal otwarty.</span><span class="sxs-lookup"><span data-stu-id="5e102-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="5e102-125">Po uruchomieniu próbki odpowiedzi operacji i wyjątków są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="5e102-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="5e102-126">Proces klienta uruchamia dwa scenariusze każdego podejmuje próbę nawiązania `Add` następuje `Divide`.</span><span class="sxs-lookup"><span data-stu-id="5e102-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="5e102-127">Pierwszy scenariusz symuluje problem z siecią przez przerywanie klienta przed wprowadzeniem wywołanie `Divide`.</span><span class="sxs-lookup"><span data-stu-id="5e102-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="5e102-128">Drugi scenariusz powoduje, że warunek limitu czasu przez ustawienie limitu czasu zbyt krótka dla metody, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="5e102-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="5e102-129">Oczekiwane dane wyjściowe z procesu klienta jest:</span><span class="sxs-lookup"><span data-stu-id="5e102-129">The expected output from the client process is:</span></span>  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5e102-130">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="5e102-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5e102-131">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e102-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5e102-132">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e102-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="5e102-133">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e102-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5e102-134">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5e102-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5e102-135">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5e102-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5e102-136">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="5e102-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5e102-137">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5e102-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
  
## <a name="see-also"></a><span data-ttu-id="5e102-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e102-138">See Also</span></span>
