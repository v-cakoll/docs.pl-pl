---
title: Rozszerzanie kontroli obsługi i raportowania błędów
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 83df5ffb790ee69ab290ad703c46b421cd6a02e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="extending-control-over-error-handling-and-reporting"></a><span data-ttu-id="b8d9a-102">Rozszerzanie kontroli obsługi i raportowania błędów</span><span class="sxs-lookup"><span data-stu-id="b8d9a-102">Extending Control Over Error Handling and Reporting</span></span>
<span data-ttu-id="b8d9a-103">W tym przykładzie pokazano, jak rozszerzyć kontrolę obsługi błędów i raportowania błędów w usługi Windows Communication Foundation (WCF) przy użyciu <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-103">This sample demonstrates how to extend control over error handling and error reporting in a Windows Communication Foundation (WCF) service using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="b8d9a-104">Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) z dodatkowy kod dodane do usługi do obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) with some additional code added to the service to handle errors.</span></span> <span data-ttu-id="b8d9a-105">Klient wymusza kilka błędów.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-105">The client forces several error conditions.</span></span> <span data-ttu-id="b8d9a-106">Usługa przechwytuje błędy i rejestruje je w pliku.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-106">The service intercepts the errors and logs them in a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8d9a-107">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b8d9a-108">Usługi można przechwytywać błędy, przetwarzania i mają wpływ na sposób zgłaszania błędów przy użyciu <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-108">Services can intercept errors, perform processing, and affect how errors are reported using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="b8d9a-109">Interfejs ma dwie metody, które można implementować: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> i <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-109">The interface has two methods that can be implemented: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> and <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span></span> <span data-ttu-id="b8d9a-110"><xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> Metoda umożliwia dodawanie, zmianę lub Pomiń komunikat o błędzie wygenerowanego w odpowiedzi na wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-110">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> method allows you to add, modify, or suppress a fault message that is generated in response to an exception.</span></span> <span data-ttu-id="b8d9a-111"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Metoda pozwala wystąpił błąd podczas przetwarzania została wykonana w przypadku błędu i kontrolek, czy można uruchomić obsługi dodatkowych błędów.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-111">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method allows error processing to take place in the event of an error and controls whether additional error handling can run.</span></span>  
  
 <span data-ttu-id="b8d9a-112">W tym przykładzie `CalculatorErrorHandler` typ implementuje <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-112">In this sample, the `CalculatorErrorHandler` type implements the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="b8d9a-113">W</span><span class="sxs-lookup"><span data-stu-id="b8d9a-113">In the</span></span>  
  
 <span data-ttu-id="b8d9a-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Metoda, `CalculatorErrorHandler` zapisuje dziennik błędu w pliku tekstowym Error.txt w c:\logs.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method, the `CalculatorErrorHandler` writes a log of the error to an Error.txt text file in c:\logs.</span></span> <span data-ttu-id="b8d9a-115">Należy pamiętać, że próbki rejestruje błąd i nie odrzuca, dzięki któremu zgłaszana z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-115">Note that the sample logs the fault and does not suppress it, allowing it to be reported back to the client.</span></span>  
  
```  
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
  
 <span data-ttu-id="b8d9a-116">`ErrorBehaviorAttribute` Istnieje jako mechanizm rejestrowania program obsługi błędów z usługi.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-116">The `ErrorBehaviorAttribute` exists as a mechanism to register an error handler with a service.</span></span> <span data-ttu-id="b8d9a-117">Ten atrybut przyjmuje parametr jednego typu.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-117">This attribute takes a single type parameter.</span></span> <span data-ttu-id="b8d9a-118">Czy typ powinien implementować <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu i powinna mieć publicznego konstruktora puste.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-118">That type should implement the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface and should have a public, empty constructor.</span></span> <span data-ttu-id="b8d9a-119">Atrybut następnie tworzy wystąpienie tego typu obsługi błędów i instaluje je w usłudze.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-119">The attribute then instantiates an instance of that error handler type and installs it into the service.</span></span> <span data-ttu-id="b8d9a-120">Robi to zaimplementowanie <xref:System.ServiceModel.Description.IServiceBehavior> interfejs, a następnie użyć <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> metodę, aby dodać wystąpienia program obsługi błędów do usługi.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-120">It does this by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface and then using the <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> method to add instances of the error handler to the service.</span></span>  
  
```  
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
  
 <span data-ttu-id="b8d9a-121">Przykład implementuje usługi Kalkulator.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-121">The sample implements a calculator service.</span></span> <span data-ttu-id="b8d9a-122">Klient celowo przyczyną dwóch błędów w usłudze, podając parametry z wartościami niedozwolony.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-122">The client deliberately causes two errors to occur on the service by providing parameters with illegal values.</span></span> <span data-ttu-id="b8d9a-123">`CalculatorErrorHandler` Używa <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu do lokalnego pliku dziennika błędów, a następnie umożliwia im to zgłaszana z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-123">The `CalculatorErrorHandler` uses the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface to log the errors to a local file and then allows them to be reported back to the client.</span></span> <span data-ttu-id="b8d9a-124">Klient wymusza dzielenie przez zero i warunek argumentu out-of-range.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-124">The client forces a divide by zero and an argument-out-of-range condition.</span></span>  
  
```  
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
  
 <span data-ttu-id="b8d9a-125">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b8d9a-126">Zostanie wyświetlony dzielenie przez zero oraz warunki argumentu out-of-range zgłaszają się jako błędy.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-126">You see the division by zero and the argument-out-of-range conditions being reported as faults.</span></span> <span data-ttu-id="b8d9a-127">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-127">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Forcing an error in Divide  
FaultException: FaultException - Invalid Argument: The second argument must not be zero.  
Forcing an error in Factorial  
FaultException: FaultException - Invalid Argument: The argument must be greater than zero.  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="b8d9a-128">C:\logs\errors.txt Plik zawiera informacje o zarejestrowanych o błędach przez usługę.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-128">The file c:\logs\errors.txt contains the information logged about the errors by the service.</span></span> <span data-ttu-id="b8d9a-129">Należy zwrócić uwagę na zapis w katalogu, należy się upewnić, że usługi pod którą jest uruchomiona usługa, proces (zwykle ASP.NET lub usługi sieciowej), ma uprawnienia do zapisu w katalogu.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-129">Note that for the service to write to the directory you must make sure that the process under which the service is running, (typically ASP.NET or Network Service), has the permission to write to the directory.</span></span>  
  
```  
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8d9a-130">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="b8d9a-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b8d9a-131">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8d9a-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b8d9a-132">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8d9a-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b8d9a-133">Upewnij się, że utworzono katalog c:\logs dla pliku error.txt.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-133">Ensure you have created the c:\logs directory for the error.txt file.</span></span> <span data-ttu-id="b8d9a-134">Lub zmodyfikować nazwy pliku w `CalculatorErrorHandler.HandleError`.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-134">Or modify the file name used in `CalculatorErrorHandler.HandleError`.</span></span>  
  
4.  <span data-ttu-id="b8d9a-135">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8d9a-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8d9a-136">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b8d9a-137">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="b8d9a-137">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b8d9a-138">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8d9a-139">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b8d9a-139">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
  
## <a name="see-also"></a><span data-ttu-id="b8d9a-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8d9a-140">See Also</span></span>
