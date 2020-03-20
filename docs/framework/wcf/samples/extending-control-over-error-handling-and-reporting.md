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
# <a name="extending-control-over-error-handling-and-reporting"></a>Rozszerzanie kontroli obsługi i raportowania błędów
W tym przykładzie pokazano, jak rozszerzyć kontrolę nad obsługą błędów i raportowania <xref:System.ServiceModel.Dispatcher.IErrorHandler> błędów w usłudze Windows Communication Foundation (WCF) przy użyciu interfejsu. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) z niektórych dodatkowy kod dodany do usługi do obsługi błędów. Klient wymusza kilka warunków błędu. Usługa przechwytuje błędy i rejestruje je w pliku.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Usługi mogą przechwytywać błędy, wykonywać przetwarzanie i wpływać <xref:System.ServiceModel.Dispatcher.IErrorHandler> na sposób zgłaszania błędów za pomocą interfejsu. Interfejs ma dwie metody, które <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> można <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>zaimplementować: i . Metoda <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> umożliwia dodawanie, modyfikowanie lub pomijanie komunikatu o błędzie, który jest generowany w odpowiedzi na wyjątek. Metoda <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> umożliwia przetwarzanie błędów odbywa się w przypadku błędu i kontroluje, czy można uruchomić obsługę dodatkowych błędów.  
  
 W tym przykładzie `CalculatorErrorHandler` typ <xref:System.ServiceModel.Dispatcher.IErrorHandler> implementuje interfejs. W  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>metoda, `CalculatorErrorHandler` zapisuje dziennik błędu do pliku tekstowego Error.txt w c:\logs. Należy zauważyć, że przykład rejestruje błąd i nie pomija go, dzięki czemu mają być zgłaszane z powrotem do klienta.  
  
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
  
 Istnieje `ErrorBehaviorAttribute` jako mechanizm do rejestrowania obsługi błędów w usłudze. Ten atrybut przyjmuje parametr pojedynczego typu. Ten typ powinien <xref:System.ServiceModel.Dispatcher.IErrorHandler> implementować interfejs i powinien mieć publiczny, pusty konstruktor. Atrybut następnie wystąpienia tego typu obsługi błędów i instaluje go w usłudze. Robi to implementując <xref:System.ServiceModel.Description.IServiceBehavior> interfejs, a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> następnie za pomocą metody, aby dodać wystąpienia programu obsługi błędów do usługi.  
  
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
  
 Przykład implementuje usługę kalkulatora. Klient celowo powoduje dwa błędy występują w usłudze, podając parametry z wartościami niedozwolone. Interfejs `CalculatorErrorHandler` służy <xref:System.ServiceModel.Dispatcher.IErrorHandler> do rejestrowania błędów w pliku lokalnym, a następnie umożliwia ich zgłaszanie z powrotem do klienta. Klient wymusza dzielenie przez zero i warunek argumentu poza zakresem.  
  
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
  
 Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Zobaczysz podział przez zero i argument-out-of-range warunki zgłaszane jako błędy. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
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
  
 Plik c:\logs\errors.txt zawiera informacje zarejestrowane o błędach przez usługę. Należy zauważyć, że aby usługa zapisywała w katalogu, należy upewnić się, że proces, w którym usługa jest uruchomiona (zazwyczaj ASP.NET lub usługa sieciowa) ma uprawnienia do zapisu w katalogu.  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Upewnij się, że utworzono katalog c:\logs dla pliku error.txt. Lub zmodyfikuj nazwę pliku używanego w pliku `CalculatorErrorHandler.HandleError`.  
  
4. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
