---
title: Rozszerzanie kontroli obsługi i raportowania błędów
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 68f3381e8db9d7c0222720dda335b47e30f57ac7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183681"
---
# <a name="extending-control-over-error-handling-and-reporting"></a><span data-ttu-id="b7c31-102">Rozszerzanie kontroli obsługi i raportowania błędów</span><span class="sxs-lookup"><span data-stu-id="b7c31-102">Extending Control Over Error Handling and Reporting</span></span>
<span data-ttu-id="b7c31-103">W tym przykładzie pokazano, jak rozszerzyć kontrolę nad obsługą błędów i raportowania <xref:System.ServiceModel.Dispatcher.IErrorHandler> błędów w usłudze Windows Communication Foundation (WCF) przy użyciu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b7c31-103">This sample demonstrates how to extend control over error handling and error reporting in a Windows Communication Foundation (WCF) service using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="b7c31-104">Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) z niektórych dodatkowy kod dodany do usługi do obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="b7c31-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) with some additional code added to the service to handle errors.</span></span> <span data-ttu-id="b7c31-105">Klient wymusza kilka warunków błędu.</span><span class="sxs-lookup"><span data-stu-id="b7c31-105">The client forces several error conditions.</span></span> <span data-ttu-id="b7c31-106">Usługa przechwytuje błędy i rejestruje je w pliku.</span><span class="sxs-lookup"><span data-stu-id="b7c31-106">The service intercepts the errors and logs them in a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7c31-107">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b7c31-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b7c31-108">Usługi mogą przechwytywać błędy, wykonywać przetwarzanie i wpływać <xref:System.ServiceModel.Dispatcher.IErrorHandler> na sposób zgłaszania błędów za pomocą interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b7c31-108">Services can intercept errors, perform processing, and affect how errors are reported using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="b7c31-109">Interfejs ma dwie metody, które <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> można <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>zaimplementować: i .</span><span class="sxs-lookup"><span data-stu-id="b7c31-109">The interface has two methods that can be implemented: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> and <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span></span> <span data-ttu-id="b7c31-110">Metoda <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> umożliwia dodawanie, modyfikowanie lub pomijanie komunikatu o błędzie, który jest generowany w odpowiedzi na wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b7c31-110">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> method allows you to add, modify, or suppress a fault message that is generated in response to an exception.</span></span> <span data-ttu-id="b7c31-111">Metoda <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> umożliwia przetwarzanie błędów odbywa się w przypadku błędu i kontroluje, czy można uruchomić obsługę dodatkowych błędów.</span><span class="sxs-lookup"><span data-stu-id="b7c31-111">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method allows error processing to take place in the event of an error and controls whether additional error handling can run.</span></span>  
  
 <span data-ttu-id="b7c31-112">W tym przykładzie `CalculatorErrorHandler` typ <xref:System.ServiceModel.Dispatcher.IErrorHandler> implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="b7c31-112">In this sample, the `CalculatorErrorHandler` type implements the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="b7c31-113">W</span><span class="sxs-lookup"><span data-stu-id="b7c31-113">In the</span></span>  
  
 <span data-ttu-id="b7c31-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>metoda, `CalculatorErrorHandler` zapisuje dziennik błędu do pliku tekstowego Error.txt w c:\logs.</span><span class="sxs-lookup"><span data-stu-id="b7c31-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method, the `CalculatorErrorHandler` writes a log of the error to an Error.txt text file in c:\logs.</span></span> <span data-ttu-id="b7c31-115">Należy zauważyć, że przykład rejestruje błąd i nie pomija go, dzięki czemu mają być zgłaszane z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="b7c31-115">Note that the sample logs the fault and does not suppress it, allowing it to be reported back to the client.</span></span>  
  
```csharp
public class CalculatorErrorHandler : IErrorHandler
{
    // Provide a fault. The Message fault parameter can be replaced, or set to
    // null to suppress reporting a fault.

    public void ProvideFault(Exception error, MessageVersion version, ref Message fault)
    {
    }

    // HandleError. Log an error, then allow the error to be handled as usual.
    // Return true if the error is considered as already handled

    public bool HandleError(Exception error)
    {
        using (TextWriter tw = File.AppendText(@"c:\logs\error.txt"))
        {
            if (error != null)
            {
                tw.WriteLine("Exception: " + error.GetType().Name + " - " + error.Message);
            }
            tw.Close();
        }
        return true;
    }
}  
```  
  
 <span data-ttu-id="b7c31-116">Istnieje `ErrorBehaviorAttribute` jako mechanizm do rejestrowania obsługi błędów w usłudze.</span><span class="sxs-lookup"><span data-stu-id="b7c31-116">The `ErrorBehaviorAttribute` exists as a mechanism to register an error handler with a service.</span></span> <span data-ttu-id="b7c31-117">Ten atrybut przyjmuje parametr pojedynczego typu.</span><span class="sxs-lookup"><span data-stu-id="b7c31-117">This attribute takes a single type parameter.</span></span> <span data-ttu-id="b7c31-118">Ten typ powinien <xref:System.ServiceModel.Dispatcher.IErrorHandler> implementować interfejs i powinien mieć publiczny, pusty konstruktor.</span><span class="sxs-lookup"><span data-stu-id="b7c31-118">That type should implement the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface and should have a public, empty constructor.</span></span> <span data-ttu-id="b7c31-119">Atrybut następnie wystąpienia tego typu obsługi błędów i instaluje go w usłudze.</span><span class="sxs-lookup"><span data-stu-id="b7c31-119">The attribute then instantiates an instance of that error handler type and installs it into the service.</span></span> <span data-ttu-id="b7c31-120">Robi to implementując <xref:System.ServiceModel.Description.IServiceBehavior> interfejs, a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> następnie za pomocą metody, aby dodać wystąpienia programu obsługi błędów do usługi.</span><span class="sxs-lookup"><span data-stu-id="b7c31-120">It does this by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface and then using the <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> method to add instances of the error handler to the service.</span></span>  
  
```csharp
// This attribute can be used to install a custom error handler for a service.  
public class ErrorBehaviorAttribute : Attribute, IServiceBehavior  
{  
    Type errorHandlerType;  
  
    public ErrorBehaviorAttribute(Type errorHandlerType)  
    {  
        this.errorHandlerType = errorHandlerType;  
    }  
  
    void IServiceBehavior.Validate(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
    }  
  
    void IServiceBehavior.AddBindingParameters(ServiceDescription description, ServiceHostBase serviceHostBase, System.Collections.ObjectModel.Collection<ServiceEndpoint> endpoints, BindingParameterCollection parameters)  
    {  
    }  
  
    void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
        IErrorHandler errorHandler;  
  
        try  
        {  
            errorHandler = (IErrorHandler)Activator.CreateInstance(errorHandlerType);  
        }  
        catch (MissingMethodException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must have a public empty constructor.", e);  
        }  
        catch (InvalidCastException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must implement System.ServiceModel.Dispatcher.IErrorHandler.", e);  
        }  
  
        foreach (ChannelDispatcherBase channelDispatcherBase in serviceHostBase.ChannelDispatchers)  
        {  
            ChannelDispatcher channelDispatcher = channelDispatcherBase as ChannelDispatcher;  
            channelDispatcher.ErrorHandlers.Add(errorHandler);  
        }
    }  
}  
```  
  
 <span data-ttu-id="b7c31-121">Przykład implementuje usługę kalkulatora.</span><span class="sxs-lookup"><span data-stu-id="b7c31-121">The sample implements a calculator service.</span></span> <span data-ttu-id="b7c31-122">Klient celowo powoduje dwa błędy występują w usłudze, podając parametry z wartościami niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="b7c31-122">The client deliberately causes two errors to occur on the service by providing parameters with illegal values.</span></span> <span data-ttu-id="b7c31-123">Interfejs `CalculatorErrorHandler` służy <xref:System.ServiceModel.Dispatcher.IErrorHandler> do rejestrowania błędów w pliku lokalnym, a następnie umożliwia ich zgłaszanie z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="b7c31-123">The `CalculatorErrorHandler` uses the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface to log the errors to a local file and then allows them to be reported back to the client.</span></span> <span data-ttu-id="b7c31-124">Klient wymusza dzielenie przez zero i warunek argumentu poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="b7c31-124">The client forces a divide by zero and an argument-out-of-range condition.</span></span>  
  
```csharp
try
{  
    Console.WriteLine("Forcing an error in Divide");  
    // Call the Divide service operation - trigger a divide by 0 error.  
    value1 = 22;  
    value2 = 0;  
    result = proxy.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
}  
catch (FaultException e)  
{  
    Console.WriteLine("FaultException: " + e.GetType().Name + " - " + e.Message);  
}  
catch (Exception e)  
{  
    Console.WriteLine("Exception: " + e.GetType().Name + " - " + e.Message);  
}  
```  
  
 <span data-ttu-id="b7c31-125">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="b7c31-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b7c31-126">Zobaczysz podział przez zero i argument-out-of-range warunki zgłaszane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="b7c31-126">You see the division by zero and the argument-out-of-range conditions being reported as faults.</span></span> <span data-ttu-id="b7c31-127">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="b7c31-127">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Forcing an error in Divide  
FaultException: FaultException - Invalid Argument: The second argument must not be zero.  
Forcing an error in Factorial  
FaultException: FaultException - Invalid Argument: The argument must be greater than zero.  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="b7c31-128">Plik c:\logs\errors.txt zawiera informacje zarejestrowane o błędach przez usługę.</span><span class="sxs-lookup"><span data-stu-id="b7c31-128">The file c:\logs\errors.txt contains the information logged about the errors by the service.</span></span> <span data-ttu-id="b7c31-129">Należy zauważyć, że aby usługa zapisywała w katalogu, należy upewnić się, że proces, w którym usługa jest uruchomiona (zazwyczaj ASP.NET lub usługa sieciowa) ma uprawnienia do zapisu w katalogu.</span><span class="sxs-lookup"><span data-stu-id="b7c31-129">Note that for the service to write to the directory you must make sure that the process under which the service is running (typically ASP.NET or Network Service) has permission to write to the directory.</span></span>  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b7c31-130">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="b7c31-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b7c31-131">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7c31-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b7c31-132">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7c31-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b7c31-133">Upewnij się, że utworzono katalog c:\logs dla pliku error.txt.</span><span class="sxs-lookup"><span data-stu-id="b7c31-133">Ensure you have created the c:\logs directory for the error.txt file.</span></span> <span data-ttu-id="b7c31-134">Lub zmodyfikuj nazwę pliku używanego w pliku `CalculatorErrorHandler.HandleError`.</span><span class="sxs-lookup"><span data-stu-id="b7c31-134">Or modify the file name used in `CalculatorErrorHandler.HandleError`.</span></span>  
  
4. <span data-ttu-id="b7c31-135">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b7c31-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b7c31-136">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b7c31-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b7c31-137">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="b7c31-137">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b7c31-138">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="b7c31-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b7c31-139">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b7c31-139">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
