---
title: Dupleks
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: c132b49c3d1ff1cd72c7a02f66ad4bf6d2d65d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506649"
---
# <a name="duplex"></a>Dupleks
Dupleks przykładzie pokazano sposób definiowania i implementowanie kontraktu dwukierunkowego. Komunikację dupleksową występuje, gdy klient ustanawia sesję z usługą i udostępnia usługę kanału, na którym usługa można wysłać wiadomości zwrotnie do klienta. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Kontrakt dupleksu jest zdefiniowany jako pary interfejsów — podstawowy interfejs z klienta do usługi i interfejs wywołania zwrotnego z usługi do klienta. W tym przykładzie `ICalculatorDuplex` interfejs umożliwia klientowi wykonywania operacji matematycznych, obliczania wyniku w sesji. Usługa zwraca wyniki na `ICalculatorDuplexCallback` interfejsu. Kontrakt dupleksowy wymaga elementu session, ponieważ kontekst muszą być ustalane do skorelowania zestaw komunikatów przesyłanych między klientem a usługą.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS). Kontrakt dupleksu jest zdefiniowane w następujący sposób:  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required,  
                 CallbackContract=typeof(ICalculatorDuplexCallback))]  
public interface ICalculatorDuplex  
{  
    [OperationContract(IsOneWay = true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
}  
  
public interface ICalculatorDuplexCallback  
{  
    [OperationContract(IsOneWay = true)]  
    void Result(double result);  
    [OperationContract(IsOneWay = true)]  
    void Equation(string eqn);  
}  
```  
  
 `CalculatorService` Klasa implementuje podstawową `ICalculatorDuplex` interfejsu. Używane przez usługę <xref:System.ServiceModel.InstanceContextMode.PerSession> tryb wystąpienia przechowywać wynik dla każdej sesji. Właściwość prywatna o nazwie `Callback` umożliwia dostęp do kanału wywołania zwrotnego do klienta. Usługa używa wywołania zwrotnego do wysyłania wiadomości do klienta za pośrednictwem interfejsu wywołania zwrotnego.  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorDuplex  
{  
    double result = 0.0D;  
    string equation;  
  
    public CalculatorService()  
    {  
        equation = result.ToString();  
    }  
  
    public void Clear()  
    {  
        Callback.Equation(equation + " = " + result.ToString());  
        equation = result.ToString();  
    }  
  
    public void AddTo(double n)  
    {  
        result += n;  
        equation += " + " + n.ToString();  
        Callback.Result(result);  
    }  
    ...  
    ICalculatorDuplexCallback Callback  
    {  
        get  
        {  
            return OperationContext.Current.GetCallbackChannel<ICalculatorDuplexCallback>();  
        }  
    }  
}  
```  
  
 Klient musi dostarczyć klasy, która implementuje interfejs wywołania zwrotnego kontrakt dupleksu do odbierania wiadomości z usługi. W przykładzie `CallbackHandler` zdefiniowana jest klasa implementacji `ICalculatorDuplexCallback` interfejsu.  
  
```  
public class CallbackHandler : ICalculatorDuplexCallback  
{  
   public void Result(double result)  
   {  
      Console.WriteLine("Result({0})", result);  
   }  
  
   public void Equation(string equation)  
   {  
      Console.WriteLine("Equation({0}", equation);  
   }  
}  
```  
  
 Serwer proxy generowany dla kontraktu dwukierunkowego wymaga <xref:System.ServiceModel.InstanceContext> należy wprowadzić po konstrukcji. To <xref:System.ServiceModel.InstanceContext> jest używany jako lokacji dla obiekt, który implementuje interfejs wywołania zwrotnego i obsługi wiadomości, które są wysyłane z usługi. <xref:System.ServiceModel.InstanceContext> Jest tworzony przy użyciu wystąpienia `CallbackHandler` klasy. Ten obiekt obsługi komunikatów wysyłanych z usługi do klienta w interfejsie wywołania zwrotnego.  
  
```  
// Construct InstanceContext to handle messages on callback interface.  
InstanceContext instanceContext = new InstanceContext(new CallbackHandler());  
  
// Create a client.  
CalculatorDuplexClient client = new CalculatorDuplexClient(instanceContext);  
  
Console.WriteLine("Press <ENTER> to terminate client once the output is displayed.");  
Console.WriteLine();  
  
// Call the AddTo service operation.  
double value = 100.00D;  
client.AddTo(value);  
  
// Call the SubtractFrom service operation.  
value = 50.00D;  
client.SubtractFrom(value);  
  
// Call the MultiplyBy service operation.  
value = 17.65D;  
client.MultiplyBy(value);  
  
// Call the DivideBy service operation.  
value = 2.00D;  
client.DivideBy(value);  
  
// Complete equation.  
client.Clear();  
  
Console.ReadLine();  
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```  
  
 Konfiguracja została zmodyfikowana ma zostać udostępnione wiązanie, która obsługuje zarówno sesji komunikacji i komunikację dupleksową. `wsDualHttpBinding` Obsługuje komunikację sesji i umożliwia komunikację dupleksową zapewniając dwa połączenia HTTP, po jednej dla każdego kierunku. W usłudze jedyną różnicą w konfiguracji jest powiązania, który jest używany. Na komputerze klienckim należy skonfigurować adres serwera można się połączyć do klienta, jak pokazano w poniższych Przykładowa konfiguracja.  
  
```xml  
<client>  
  <endpoint name=""  
            address="http://localhost/servicemodelsamples/service.svc"   
            binding="wsDualHttpBinding"   
            bindingConfiguration="DuplexBinding"   
            contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
</client>  
  
<bindings>  
  <!-- Configure a binding that support duplex communication. -->  
  <wsDualHttpBinding>  
    <binding name="DuplexBinding"   
             clientBaseAddress="http://localhost:8000/myClient/">  
    </binding>  
  </wsDualHttpBinding>  
</bindings>  
```  
  
 Po uruchomieniu próbki widzisz wiadomości, które są zwracane do klienta na interfejsie wywołania zwrotnego, który jest wysyłany z usługi. Zostanie wyświetlona poszczególnych pośrednia wynik, następuje całe równanie po zakończeniu wszystkich operacji. Naciśnij klawisz ENTER, aby zamknąć klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C#, C++ lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!IMPORTANT]
    >  Podczas uruchamiania klienta w konfiguracji między komputerami, należy zastąpić "localhost" zarówno `address` atrybutu [punktu końcowego](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu i `clientBaseAddress` atrybutu [ \< Powiązanie >](../../../../docs/framework/misc/binding.md) elementu [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) elementu o nazwie odpowiednie maszyny, jak pokazano poniżej:  
  
    ```xml  
    <client>  
    <endpoint name = ""  
    address="http://service_machine_name/servicemodelsamples/service.svc"  
    ... />  
    </client>  
    ...  
    <wsDualHttpBinding>  
    <binding name="DuplexBinding" clientBaseAddress="http://client_machine_name:8000/myClient/">  
    </binding>  
    </wsDualHttpBinding>  
    ```  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`  
  
## <a name="see-also"></a>Zobacz też
