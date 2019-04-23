---
title: Dupleks
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: 1dedc6d771e75acd0d657bb5430c178428c0f0ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976706"
---
# <a name="duplex"></a>Dupleks
Dwukierunkowe przykładowych pokazano, jak definiować ani implementować kontraktu dwukierunkowego. Komunikację dupleksową występuje, gdy klient ustanawia sesję z usługą i zapewnia usługi kanału, na którym usługa może wysłać wiadomości zwrotnie do klienta. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Kontrakt dupleksu jest zdefiniowany jako pary interfejsów — podstawowy interfejs od klienta do usługi i interfejs wywołania zwrotnego z usługi do klienta. W tym przykładzie `ICalculatorDuplex` interfejs umożliwia klientowi do wykonywania operacji matematycznych obliczania wyniku za pośrednictwem sesji. Usługa zwraca wyniki w `ICalculatorDuplexCallback` interfejsu. Kontrakt dupleksowy wymaga elementu session, ponieważ kontekst muszą być ustalane do skorelowania zestaw komunikatów przesyłanych między klientem a usługą.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS). Kontraktu dwukierunkowego jest zdefiniowana w następujący sposób:  
  
```csharp
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
  
 `CalculatorService` Klasa implementuje podstawowy `ICalculatorDuplex` interfejsu. Używa usługi <xref:System.ServiceModel.InstanceContextMode.PerSession> tryb wystąpienia do obsługi wyników dla każdej sesji. Właściwość prywatna o nazwie `Callback` umożliwia dostęp do kanału wywołania zwrotnego do klienta. Usługa używa wywołania zwrotnego do wysyłania wiadomości do klienta za pośrednictwem interfejs wywołania zwrotnego.  
  
```csharp
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
        Callback.Equation($"{equation} = {result}");  
        equation = result.ToString();  
    }  
  
    public void AddTo(double n)  
    {  
        result += n;  
        equation += $" + {n}";  
        Callback.Result(result);  
    }  
    
    //...  
    
    ICalculatorDuplexCallback Callback  
    {  
        get  
        {  
            return OperationContext.Current.GetCallbackChannel<ICalculatorDuplexCallback>();  
        }  
    }  
}  
```  
  
 Klient musi podać klasę, która implementuje interfejs wywołania zwrotnego kontraktu dwukierunkowego, do odbierania wiadomości z usługi. W tym przykładzie `CallbackHandler` klasa jest zdefiniowana w celu zaimplementowania `ICalculatorDuplexCallback` interfejsu.  
  
```csharp 
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
  
 Serwer proxy, który jest generowany dla kontraktu dwukierunkowego wymaga <xref:System.ServiceModel.InstanceContext> należy podać podczas konstruowania. To <xref:System.ServiceModel.InstanceContext> jest używana jako witryna dla obiektu, który implementuje interfejs wywołania zwrotnego i obsługuje wiadomości wysyłanych na odpowiedź od usługi. <xref:System.ServiceModel.InstanceContext> Składa się z wystąpieniem `CallbackHandler` klasy. Ten obiekt obsługi komunikatów wysyłanych z usługi na kliencie, na interfejs wywołania zwrotnego.  
  
```csharp
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
  
 Konfiguracja została zmodyfikowana, aby zapewnić powiązania, który obsługuje zarówno sesji komunikacji, jak i komunikację dupleksową. `wsDualHttpBinding` Obsługuje komunikację sesji i umożliwia komunikację dupleksową, zapewniając dwa połączenia HTTP, jedno dla każdego kierunku. W usłudze jedyną różnicą w konfiguracji jest powiązanie, które jest używane. Na komputerze klienckim należy skonfigurować adres który umożliwia Podłącz do klienta, jak pokazano na poniższym Przykładowa konfiguracja serwera.  
  
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
  
 Po uruchomieniu przykładu, zostanie wyświetlone komunikaty, które są zwracane do klienta na interfejs wywołania zwrotnego, które są wysyłane z usługi. Jest wyświetlany wynik każdego pośrednich następuje całe równanie po ukończeniu wszystkich operacji. Naciśnij klawisz ENTER, aby zamknąć klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby kompilować rozwiązania w wersji języka C#, C++ lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!IMPORTANT]
    >  Podczas uruchamiania klienta w konfiguracji między komputerami, należy zastąpić "localhost", w obu `address` atrybutu [ \<punktu końcowego > z \<klienta >](../../configure-apps/file-schema/wcf/endpoint-of-client.md) elementu i `clientBaseAddress` atrybut [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element z nazwą odpowiedniej maszyny, jak pokazano w poniższym:  
  
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
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`  
