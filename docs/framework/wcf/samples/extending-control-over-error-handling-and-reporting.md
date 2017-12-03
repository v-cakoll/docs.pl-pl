---
title: "Rozszerzanie kontroli obsługi i raportowania błędów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4284f07a21a9bb176a78a8a2abefe7c7c7c6b66
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="extending-control-over-error-handling-and-reporting"></a>Rozszerzanie kontroli obsługi i raportowania błędów
W tym przykładzie pokazano, jak rozszerzyć kontrolę obsługi błędów oraz raportowania błędów w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi przy użyciu <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu. Próbki jest oparta na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) z dodatkowy kod dodane do usługi do obsługi błędów. Klient wymusza kilka błędów. Usługa przechwytuje błędy i rejestruje je w pliku.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Usługi można przechwytywać błędy, przetwarzania i mają wpływ na sposób zgłaszania błędów przy użyciu <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu. Interfejs ma dwie metody, które można implementować: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> i <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>. <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> Metoda umożliwia dodawanie, zmianę lub Pomiń komunikat o błędzie wygenerowanego w odpowiedzi na wyjątek. <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Metoda pozwala wystąpił błąd podczas przetwarzania została wykonana w przypadku błędu i kontrolek, czy można uruchomić obsługi dodatkowych błędów.  
  
 W tym przykładzie `CalculatorErrorHandler` typ implementuje <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu. W  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>Metoda, `CalculatorErrorHandler` zapisuje dziennik błędu w pliku tekstowym Error.txt w c:\logs. Należy pamiętać, że próbki rejestruje błąd i nie odrzuca, dzięki któremu zgłaszana z powrotem do klienta.  
  
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
  
 `ErrorBehaviorAttribute` Istnieje jako mechanizm rejestrowania program obsługi błędów z usługi. Ten atrybut przyjmuje parametr jednego typu. Czy typ powinien implementować <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu i powinna mieć publicznego konstruktora puste. Atrybut następnie tworzy wystąpienie tego typu obsługi błędów i instaluje je w usłudze. Robi to zaimplementowanie <xref:System.ServiceModel.Description.IServiceBehavior> interfejs, a następnie użyć <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> metodę, aby dodać wystąpienia program obsługi błędów do usługi.  
  
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
  
 Przykład implementuje usługi Kalkulator. Klient celowo przyczyną dwóch błędów w usłudze, podając parametry z wartościami niedozwolony. `CalculatorErrorHandler` Używa <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu do lokalnego pliku dziennika błędów, a następnie umożliwia im to zgłaszana z powrotem do klienta. Klient wymusza dzielenie przez zero i warunek argumentu out-of-range.  
  
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
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Zostanie wyświetlony dzielenie przez zero oraz warunki argumentu out-of-range zgłaszają się jako błędy. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
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
  
 C:\logs\errors.txt Plik zawiera informacje o zarejestrowanych o błędach przez usługę. Należy zwrócić uwagę na zapis w katalogu, należy się upewnić, że usługi pod którą jest uruchomiona usługa, proces (zwykle ASP.NET lub usługi sieciowej), ma uprawnienia do zapisu w katalogu.  
  
```  
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Upewnij się, że utworzono katalog c:\logs dla pliku error.txt. Lub zmodyfikować nazwy pliku w `CalculatorErrorHandler.HandleError`.  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
  
## <a name="see-also"></a>Zobacz też
