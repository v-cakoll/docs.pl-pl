---
title: Oczekiwane wyjątki
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: f250e526b528adf0b67365ceb07f13e4087d773d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144712"
---
# <a name="expected-exceptions"></a><span data-ttu-id="4d8d5-102">Oczekiwane wyjątki</span><span class="sxs-lookup"><span data-stu-id="4d8d5-102">Expected Exceptions</span></span>
<span data-ttu-id="4d8d5-103">W tym przykładzie pokazano, jak przechwytywać oczekiwane wyjątki podczas korzystania z wpisanego klienta.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="4d8d5-104">Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="4d8d5-105">W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="4d8d5-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d8d5-106">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4d8d5-107">W tym przykładzie pokazano, że wyłapywanie i `TimeoutException` `CommunicationException`obsługa dwóch oczekiwanych typów wyjątków, które muszą obsługiwać poprawne programy: i .</span><span class="sxs-lookup"><span data-stu-id="4d8d5-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="4d8d5-108">Wyjątki, które są generowane z metod komunikacji na kliencie Programu Windows Communication Foundation (WCF) są oczekiwane lub nieoczekiwane.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-108">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="4d8d5-109">Nieoczekiwane wyjątki obejmują `OutOfMemoryException` katastrofalne błędy, `ArgumentNullException` `InvalidOperationException`takie jak i błędy programowania, takie jak lub .</span><span class="sxs-lookup"><span data-stu-id="4d8d5-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="4d8d5-110">Zazwyczaj nie ma użytecznego sposobu obsługi nieoczekiwanych błędów, więc zazwyczaj nie należy ich przechwytywać podczas wywoływania metody komunikacji klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="4d8d5-111">Oczekiwane wyjątki od metod komunikacji na `TimeoutException` `CommunicationException`kliencie WCF `CommunicationException`obejmują , i dowolną klasę pochodną .</span><span class="sxs-lookup"><span data-stu-id="4d8d5-111">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="4d8d5-112">Wskazują one na problem podczas komunikacji, które mogą być bezpiecznie obsługiwane przez przerwanie klienta WCF i raportowania awarii komunikacji.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-112">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="4d8d5-113">Ponieważ czynniki zewnętrzne mogą powodować te błędy w dowolnej aplikacji, poprawne aplikacje muszą przechwytywać te wyjątki i odzyskać, gdy wystąpią.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="4d8d5-114">Istnieje kilka klas pochodnych, `CommunicationException` które klient może wrzucić.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="4d8d5-115">W niektórych przypadkach aplikacje również złapać niektóre z nich do specjalnej `CommunicationException`obsługi, ale niech inne być traktowane jako .</span><span class="sxs-lookup"><span data-stu-id="4d8d5-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="4d8d5-116">Można to osiągnąć, przechwytywając najpierw bardziej `CommunicationException` szczegółowy typ wyjątku, a następnie przechwytywając w późniejszej klauzuli catch.This can be accomplished by catching the more specific exception type first and then catching in a later catch-clause.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="4d8d5-117">Kod, który wywołuje metodę komunikacji `TimeoutException` `CommunicationException`klienta musi przechwytyć i .</span><span class="sxs-lookup"><span data-stu-id="4d8d5-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="4d8d5-118">Jednym ze sposobów obsługi takich błędów jest przerwanie klienta i zgłoszenie awarii komunikacji.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
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
  
 <span data-ttu-id="4d8d5-119">Jeśli wystąpi oczekiwany wyjątek, klient może lub nie może być użyteczny później.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="4d8d5-120">Aby ustalić, czy klient jest nadal `State` użyteczny, sprawdź, czy właściwość jest `CommunicationState`. Otwarte.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="4d8d5-121">Jeśli jest nadal otwarty, to nadal nadaje się do użyteczności.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="4d8d5-122">W przeciwnym razie należy przerwać klienta i zwolnić wszystkie odwołania do niego.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="4d8d5-123">Można zaobserwować, że klienci, którzy mają sesję często nie są już użyteczne po wyjątku i klientów, którzy nie mają sesji są często nadal użyteczne po wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="4d8d5-124">Jednak żadna z nich nie jest gwarantowana, więc jeśli chcesz spróbować kontynuować `State` korzystanie z klienta po wyjątku aplikacja powinna sprawdzić właściwość, aby sprawdzić, czy klient jest nadal otwarty.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="4d8d5-125">Po uruchomieniu przykładu odpowiedzi operacji i wyjątki są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="4d8d5-126">Proces klienta uruchamia dwa scenariusze, z `Add` których `Divide`każdy próbuje wywołać, a następnie .</span><span class="sxs-lookup"><span data-stu-id="4d8d5-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="4d8d5-127">Pierwszy scenariusz symuluje problem z siecią, przerywając `Divide`klienta przed wykonaniem połączenia z programem .</span><span class="sxs-lookup"><span data-stu-id="4d8d5-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="4d8d5-128">Drugi scenariusz powoduje warunek limitu czasu, ustawiając limit czasu zbyt krótki dla metody, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="4d8d5-129">Oczekiwane dane wyjściowe z procesu klienta są następujące:</span><span class="sxs-lookup"><span data-stu-id="4d8d5-129">The expected output from the client process is:</span></span>  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4d8d5-130">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="4d8d5-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4d8d5-131">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d8d5-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4d8d5-132">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d8d5-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4d8d5-133">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d8d5-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4d8d5-134">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4d8d5-135">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4d8d5-136">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d8d5-137">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4d8d5-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
