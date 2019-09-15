---
title: Rozszerzanie kontroli obsługi i raportowania błędów
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: d7efc87d7d8a913642c4ac0e3d6d19cd0a9259c5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989934"
---
# <a name="extending-control-over-error-handling-and-reporting"></a>Rozszerzanie kontroli obsługi i raportowania błędów
Ten przykład pokazuje, jak rozciągnąć kontrolę nad obsługą błędów i raportowaniem błędów w usłudze Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.IErrorHandler> przy użyciu interfejsu. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) z dodatkowym kodem dodanym do usługi w celu obsługi błędów. Klient wymusza kilka warunków błędu. Usługa przechwytuje błędy i rejestruje je w pliku.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Usługi mogą przechwycić błędy, przetwarzać i wpływać na błędy raportowane <xref:System.ServiceModel.Dispatcher.IErrorHandler> przy użyciu interfejsu. Interfejs ma dwie metody, które mogą być zaimplementowane: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> i <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>. <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> Metoda pozwala dodawać, modyfikować lub pomijać komunikat o błędzie generowany w odpowiedzi na wyjątek. <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Metoda umożliwia przetwarzanie błędów w przypadku błędu i kontroluje, czy można uruchomić dodatkową obsługę błędów.  
  
 W tym przykładzie `CalculatorErrorHandler` typ <xref:System.ServiceModel.Dispatcher.IErrorHandler> implementuje interfejs. W  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>Metoda, `CalculatorErrorHandler` zapisuje dziennik błędu do pliku tekstowego Error. txt w c:\LOGS. Należy zauważyć, że przykład rejestruje błąd i nie pomija go, co umożliwia jego raportowanie z powrotem do klienta programu.  
  
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
  
 `ErrorBehaviorAttribute` Istnieje jako mechanizm do rejestrowania programu obsługi błędów w usłudze. Ten atrybut przyjmuje jeden parametr typu. Ten typ powinien implementować <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejs i powinien mieć publicznego, pustego konstruktora. Ten atrybut następnie tworzy wystąpienie tego typu programu obsługi błędów i instaluje go w usłudze. Robi to przez implementację <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu, a następnie <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> użycie metody w celu dodania wystąpień programu obsługi błędów do usługi.  
  
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
  
 Przykład implementuje usługę kalkulatora. Klient świadomie powoduje wystąpienie dwóch błędów w usłudze, dostarczając parametry z niedozwolonymi wartościami. `CalculatorErrorHandler` Program<xref:System.ServiceModel.Dispatcher.IErrorHandler> używa interfejsu do rejestrowania błędów w pliku lokalnym, a następnie umożliwia ich raportowanie z powrotem do klienta programu. Klient wymusza dzielenie przez zero i warunku argumentu-poza zakresem.  
  
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
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Zobaczysz dzielenie przez zero i Stany argumentów poza zakresem raportowane jako błędy. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
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
  
 Plik c:\logs\errors.txt zawiera rejestrowane informacje o błędach przez usługę. Należy pamiętać, że aby usługa mogła zapisywać w katalogu, należy się upewnić, że proces, w którym jest uruchomiona usługa (zazwyczaj ASP.NET lub usługa sieciowa), ma uprawnienia do zapisu w katalogu.  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Upewnij się, że utworzono katalog c:\LOGS dla pliku Error. txt. Lub zmodyfikuj nazwę pliku używaną w `CalculatorErrorHandler.HandleError`programie.  
  
4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
