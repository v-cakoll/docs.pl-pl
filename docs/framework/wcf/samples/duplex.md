---
title: Dupleks
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: 77eab6a4975fc67c20558a53f399c7e709215587
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575202"
---
# <a name="duplex"></a>Dupleks

Przykład dupleksu ilustruje sposób definiowania i implementowania kontraktu dupleksowego. Komunikacja dupleksowa występuje, gdy klient nawiązuje sesję z usługą i nadaje usłudze kanał, w której usługa może wysyłać komunikaty z powrotem do klienta. Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md). Kontrakt dupleksowy jest definiowany jako para interfejsów — interfejs podstawowy od klienta do usługi i interfejs wywołania zwrotnego z usługi do klienta. W tym przykładzie `ICalculatorDuplex` interfejs pozwala klientowi wykonywać operacje matematyczne, obliczając wynik w ramach sesji. Usługa zwraca wyniki w `ICalculatorDuplexCallback` interfejsie. Kontrakt dupleksowy wymaga sesji, ponieważ należy ustanowić kontekst w celu skorelowania zestawu komunikatów wysyłanych między klientem a usługą.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS). Umowę dupleksową definiuje się w następujący sposób:

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

`CalculatorService`Klasa implementuje `ICalculatorDuplex` interfejs podstawowy. Usługa używa <xref:System.ServiceModel.InstanceContextMode.PerSession> trybu wystąpienia, aby zachować wynik dla każdej sesji. Właściwość Private o nazwie `Callback` jest używana do uzyskiwania dostępu do kanału wywołania zwrotnego do klienta. Usługa używa wywołania zwrotnego do wysyłania komunikatów z powrotem do klienta za pośrednictwem interfejsu wywołania zwrotnego.

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

Klient musi dostarczyć klasę, która implementuje interfejs wywołania zwrotnego kontraktu dupleksowego na potrzeby otrzymywania komunikatów z usługi. W przykładzie `CallbackHandler` Klasa jest zdefiniowana do implementacji `ICalculatorDuplexCallback` interfejsu.

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

Serwer proxy, który jest generowany dla kontraktu dupleksowego, wymaga, <xref:System.ServiceModel.InstanceContext> Aby można go było dostarczyć podczas konstruowania. Ta <xref:System.ServiceModel.InstanceContext> wartość jest używana jako witryna obiektu, który implementuje interfejs wywołania zwrotnego i obsługuje komunikaty wysyłane z powrotem z usługi. <xref:System.ServiceModel.InstanceContext>Jest zbudowany z wystąpieniem `CallbackHandler` klasy. Ten obiekt obsługuje komunikaty wysyłane z usługi do klienta w interfejsie wywołania zwrotnego.

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

Konfiguracja została zmodyfikowana w celu zapewnienia powiązania, które obsługuje komunikację zarówno z komunikacją z sesją, jak i dupleksem. `wsDualHttpBinding`Obsługuje komunikację z sesją i umożliwia komunikację dwukierunkową przez dostarczanie podwójnych połączeń HTTP, po jednym dla każdego kierunku. W usłudze jedyną różnicą w konfiguracji jest używane powiązanie. Na kliencie należy skonfigurować adres, który może być używany przez serwer do łączenia się z klientem, jak pokazano w poniższej konfiguracji przykładowej.

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

Po uruchomieniu przykładu są wyświetlane komunikaty, które są zwracane do klienta w interfejsie wywołania zwrotnego, który jest wysyłany z usługi. Zostanie wyświetlony każdy wynik pośredni, po którym następuje całe równanie po zakończeniu wszystkich operacji. Naciśnij klawisz ENTER, aby zamknąć klienta.

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować wersję rozwiązania dla języka C#, C++ lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

    > [!IMPORTANT]
    > W przypadku uruchamiania klienta programu w konfiguracji obejmującej wiele komputerów należy zamienić wartość "localhost" w `address` [ \<endpoint> \<client> ](../../configure-apps/file-schema/wcf/endpoint-of-client.md) atrybucie elementu i `clientBaseAddress` atrybut elementu elementu na [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) nazwę odpowiedniej maszyny, jak pokazano na poniższej liście:

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
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`
