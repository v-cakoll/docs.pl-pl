---
title: Rozszerzanie kontroli obsługi i raportowania błędów
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 520a939c5527fa341a6c3a609297c69ec05dd7ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094115"
---
# <a name="extending-control-over-error-handling-and-reporting"></a>Rozszerzanie kontroli obsługi i raportowania błędów
W tym przykładzie pokazano, jak rozszerzyć kontrolę obsługi błędów i raportowania błędów w usługi Windows Communication Foundation (WCF) przy użyciu <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) z dodatkowy kod dodany do usługi w celu obsługi błędów. Klient wymusza kilka warunków błędów. Usługa przechwytuje błędy i rejestruje je w pliku.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Usługi można przechwytywać błędy, przetwarzania i wpływa na sposób zgłaszania błędów przy użyciu <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu. Interfejs ma dwie metody, które można zaimplementować: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> i <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>. <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> Metoda umożliwia dodawanie, modyfikowanie lub Pomiń komunikat o błędzie, który został wygenerowany w odpowiedzi na wyjątek. <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Metoda umożliwia wystąpił błąd podczas przetwarzania się odbywać w przypadku błędu i kontrolek, czy obsługa dodatkowych błędów może uruchamiać.  
  
 W tym przykładzie `CalculatorErrorHandler` typ implementuje <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu. W  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Metoda, `CalculatorErrorHandler` zapisuje dziennik błędu w pliku tekstowym Error.txt w c:\logs. Pamiętaj, że przykład dzienniki błędów, a nie pomija, dzięki któremu być raportowane do klienta.  
  
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
  
 `ErrorBehaviorAttribute` Istnieje jako mechanizm, aby zarejestrować procedurę obsługi błędów za pomocą usługi. Ten atrybut przyjmuje parametr jednego typu. Czy typ powinien implementować <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu, a powinien mieć Konstruktor publiczny, pusty. Atrybut następnie tworzy wystąpienie tego typu obsługi błędów i instaluje je w usłudze. Jest to realizowane poprzez implementację <xref:System.ServiceModel.Description.IServiceBehavior> interfejsu, a następnie używając <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> metodę, aby dodać wystąpienia procedurę obsługi błędów w usłudze.  
  
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
  
 Przykład implementuje usługi kalkulatora. Klient celowo powoduje, że dwa błędów w usłudze, podając parametry z wartościami niedozwolone. `CalculatorErrorHandler` Używa <xref:System.ServiceModel.Dispatcher.IErrorHandler> współpracować w celu lokalnego pliku dziennika błędów, a następnie umożliwia musiały być raportowane do klienta. Klient wymusza dzielenie przez zero i warunek argument poza z zakresu.  
  
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
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Zobaczysz, dzielenie przez zero i warunki argument poza z zakresu zgłaszane jako błędy. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
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
  
 C:\logs\errors.txt Plik zawiera informacje zarejestrowane o błędach przez usługę. Należy pamiętać, że do zapisu do katalogu, należy upewnić się, że usługi w ramach której usługa jest uruchomiona, proces (zazwyczaj ASP.NET lub usługi sieciowej), ma uprawnienia do zapisu do katalogu.  
  
```  
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Upewnij się, że utworzono katalog c:\logs dla pliku error.txt. Lub zmodyfikować nazwy pliku w `CalculatorErrorHandler.HandleError`.  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
