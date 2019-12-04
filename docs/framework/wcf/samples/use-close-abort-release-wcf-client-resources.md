---
title: Zwalnianie zasobów klienta programu WCF za pomocą poleceń Zamknij i Przerwij
description: Metody Dispose mogą kończyć się niepowodzeniem i generować wyjątki w przypadku niepowodzenia sieci. Może to spowodować niepożądane zachowanie. Zamiast tego należy użyć Zamknij i Przerwij, aby zwolnić zasoby klienta w przypadku niepowodzenia sieci.
ms.date: 11/12/2018
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
ms.openlocfilehash: 38861252a470f71a6fa88554e289344e2918d710
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715333"
---
# <a name="close-and-abort-release-resources-safely-when-network-connections-have-dropped"></a><span data-ttu-id="b3557-105">Bezpieczne zamykanie i przerywanie zasobów wydań po porzucenia połączeń sieciowych</span><span class="sxs-lookup"><span data-stu-id="b3557-105">Close and Abort release resources safely when network connections have dropped</span></span>

<span data-ttu-id="b3557-106">Ten przykład ilustruje użycie metod `Close` i `Abort` w celu oczyszczenia zasobów przy użyciu klienta z określonym typem.</span><span class="sxs-lookup"><span data-stu-id="b3557-106">This sample demonstrates using the `Close` and `Abort` methods to clean up resources when using a typed client.</span></span> <span data-ttu-id="b3557-107">Instrukcja `using` powoduje wyjątki, gdy połączenie sieciowe nie jest niezawodne.</span><span class="sxs-lookup"><span data-stu-id="b3557-107">The `using` statement causes exceptions when the network connection is not robust.</span></span> <span data-ttu-id="b3557-108">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) , który implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="b3557-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="b3557-109">W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="b3557-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="b3557-110">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b3557-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="b3557-111">Ten przykład przedstawia dwa typowe problemy występujące podczas korzystania z instrukcji C# "Using" z klientami z określonym typem, jak również kod, który poprawnie czyści po wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="b3557-111">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>

<span data-ttu-id="b3557-112">Instrukcja C# "Using" powoduje wywołanie `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="b3557-112">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="b3557-113">Jest to taka sama jak `Close`(), która może generować wyjątki w przypadku wystąpienia błędu sieci.</span><span class="sxs-lookup"><span data-stu-id="b3557-113">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="b3557-114">Ponieważ wywołanie do `Dispose`() występuje niejawnie w zamykającym nawiasie klamrowym bloku "Using", to źródło wyjątków może być niezauważalne, przez co osoby piszące kod i odczytujące kod.</span><span class="sxs-lookup"><span data-stu-id="b3557-114">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="b3557-115">Reprezentuje to potencjalne źródło błędów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b3557-115">This represents a potential source of application errors.</span></span>

<span data-ttu-id="b3557-116">Pierwszym problemem, przedstawionym w metodzie `DemonstrateProblemUsingCanThrow`, jest to, że zamykający nawias klamrowy zgłasza wyjątek, a kod po zamykającym nawiasie klamrowym nie jest wykonywany:</span><span class="sxs-lookup"><span data-stu-id="b3557-116">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
} // <-- this line might throw
Console.WriteLine("Hope this code wasn't important, because it might not happen.");
```

<span data-ttu-id="b3557-117">Nawet jeśli żadne elementy wewnątrz bloku using nie zgłasza wyjątku lub wszystkie wyjątki wewnątrz bloku using są przechwytywane, `Console.WriteLine` może się nie zdarzyć, ponieważ niejawne wywołanie `Dispose`() w zamykającym nawiasie klamrowym może zgłosić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b3557-117">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.WriteLine` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>

<span data-ttu-id="b3557-118">Drugi problem, przedstawiony w metodzie `DemonstrateProblemUsingCanThrowAndMask`, jest kolejną implikacją zamykającego nawiasu klamrowego, który zgłasza wyjątek:</span><span class="sxs-lookup"><span data-stu-id="b3557-118">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>

```csharp
using (CalculatorClient client = new CalculatorClient())
{
    ...
    throw new ApplicationException("Hope this exception was not important, because "+
                                   "it might be masked by the Close exception.");
} // <-- this line might throw an exception.
```

<span data-ttu-id="b3557-119">Ponieważ `Dispose`() występuje wewnątrz bloku "finally", `ApplicationException` nigdy nie jest wyświetlany poza blokiem using, jeśli `Dispose`() zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="b3557-119">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="b3557-120">Jeśli kod poza programem musi wiedzieć o wystąpieniu `ApplicationException`, konstrukcja "Using" może spowodować problemy, maskując ten wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b3557-120">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>

<span data-ttu-id="b3557-121">Na koniec przykład pokazuje, jak oczyścić prawidłowo, gdy występują wyjątki w `DemonstrateCleanupWithExceptions`.</span><span class="sxs-lookup"><span data-stu-id="b3557-121">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="b3557-122">Używa bloku try/catch do zgłaszania błędów i wywoływania `Abort`.</span><span class="sxs-lookup"><span data-stu-id="b3557-122">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="b3557-123">Zapoznaj się z przykładem [oczekiwanych wyjątków](../../../../docs/framework/wcf/samples/expected-exceptions.md) , aby uzyskać więcej informacji na temat przechwytywania wyjątków z wywołań klientów.</span><span class="sxs-lookup"><span data-stu-id="b3557-123">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>

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
> <span data-ttu-id="b3557-124">Instrukcja using i ServiceHost: wiele aplikacji do samodzielnego udostępniania jest nieco więcej niż Hostowanie usługi i ServiceHost. zamknięcie sporadycznie zgłasza wyjątek, dzięki czemu takie aplikacje mogą bezpiecznie używać instrukcji using z elementem ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="b3557-124">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="b3557-125">Należy jednak pamiętać, że obiekt ServiceHost. Close może zgłosić `CommunicationException`, więc jeśli aplikacja będzie kontynuować działanie po zamknięciu ServiceHost, należy unikać instrukcji using i postępować zgodnie ze wzorcem.</span><span class="sxs-lookup"><span data-stu-id="b3557-125">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>

<span data-ttu-id="b3557-126">Po uruchomieniu przykładu odpowiedzi operacji i wyjątki są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="b3557-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>

<span data-ttu-id="b3557-127">Proces klienta uruchamia trzy scenariusze, z których każdy próbuje wywołać `Divide`.</span><span class="sxs-lookup"><span data-stu-id="b3557-127">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="b3557-128">Pierwszy scenariusz ilustruje pominięty kod z powodu wyjątku z `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="b3557-128">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="b3557-129">W drugim scenariuszu przedstawiono ważny wyjątek, który jest maskowany z powodu wyjątku z `Dispose`().</span><span class="sxs-lookup"><span data-stu-id="b3557-129">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="b3557-130">Trzeci scenariusz przedstawia poprawne czyszczenie.</span><span class="sxs-lookup"><span data-stu-id="b3557-130">The third scenario demonstrates correct clean up.</span></span>

<span data-ttu-id="b3557-131">Oczekiwane dane wyjściowe procesu klienta to:</span><span class="sxs-lookup"><span data-stu-id="b3557-131">The expected output from the client process is:</span></span>

```console
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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b3557-132">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="b3557-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b3557-133">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b3557-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="b3557-134">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b3557-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="b3557-135">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b3557-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b3557-136">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b3557-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b3557-137">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="b3557-137">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b3557-138">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b3557-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b3557-139">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b3557-139">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`
