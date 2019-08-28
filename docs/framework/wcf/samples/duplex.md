---
title: Dupleks
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: b00f5dd31ba572a2c8fb5301cc7ae9ddda77f0e5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045039"
---
# <a name="duplex"></a><span data-ttu-id="0777c-102">Dupleks</span><span class="sxs-lookup"><span data-stu-id="0777c-102">Duplex</span></span>

<span data-ttu-id="0777c-103">Przykład dupleksu ilustruje sposób definiowania i implementowania kontraktu dupleksowego.</span><span class="sxs-lookup"><span data-stu-id="0777c-103">The Duplex sample demonstrates how to define and implement a duplex contract.</span></span> <span data-ttu-id="0777c-104">Komunikacja dupleksowa występuje, gdy klient nawiązuje sesję z usługą i nadaje usłudze kanał, w której usługa może wysyłać komunikaty z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="0777c-104">Duplex communication occurs when a client establishes a session with a service and gives the service a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="0777c-105">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0777c-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="0777c-106">Kontrakt dupleksowy jest definiowany jako para interfejsów — interfejs podstawowy od klienta do usługi i interfejs wywołania zwrotnego z usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="0777c-106">A duplex contract is defined as a pair of interfaces—a primary interface from the client to the service and a callback interface from the service to the client.</span></span> <span data-ttu-id="0777c-107">W tym przykładzie `ICalculatorDuplex` interfejs pozwala klientowi wykonywać operacje matematyczne, obliczając wynik w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="0777c-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating the result over a session.</span></span> <span data-ttu-id="0777c-108">Usługa zwraca wyniki w `ICalculatorDuplexCallback` interfejsie.</span><span class="sxs-lookup"><span data-stu-id="0777c-108">The service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="0777c-109">Kontrakt dupleksowy wymaga sesji, ponieważ należy ustanowić kontekst w celu skorelowania zestawu komunikatów wysyłanych między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="0777c-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span>

> [!NOTE]
> <span data-ttu-id="0777c-110">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="0777c-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="0777c-111">W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="0777c-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="0777c-112">Umowę dupleksową definiuje się w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0777c-112">The duplex contract is defined as follows:</span></span>

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

<span data-ttu-id="0777c-113">Klasa implementuje interfejs podstawowy `ICalculatorDuplex`. `CalculatorService`</span><span class="sxs-lookup"><span data-stu-id="0777c-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="0777c-114">Usługa używa trybu wystąpienia <xref:System.ServiceModel.InstanceContextMode.PerSession> , aby zachować wynik dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="0777c-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="0777c-115">Właściwość Private o nazwie `Callback` jest używana do uzyskiwania dostępu do kanału wywołania zwrotnego do klienta.</span><span class="sxs-lookup"><span data-stu-id="0777c-115">A private property named `Callback` is used to access the callback channel to the client.</span></span> <span data-ttu-id="0777c-116">Usługa używa wywołania zwrotnego do wysyłania komunikatów z powrotem do klienta za pośrednictwem interfejsu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="0777c-116">The service uses the callback for sending messages back to the client through the callback interface.</span></span>

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

<span data-ttu-id="0777c-117">Klient musi dostarczyć klasę, która implementuje interfejs wywołania zwrotnego kontraktu dupleksowego na potrzeby otrzymywania komunikatów z usługi.</span><span class="sxs-lookup"><span data-stu-id="0777c-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="0777c-118">W przykładzie `CallbackHandler` Klasa jest zdefiniowana do `ICalculatorDuplexCallback` implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0777c-118">In the sample, a `CallbackHandler` class is defined to implement the `ICalculatorDuplexCallback` interface.</span></span>

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

<span data-ttu-id="0777c-119">Serwer proxy, który jest generowany dla kontraktu dupleksowego, <xref:System.ServiceModel.InstanceContext> wymaga, aby można go było dostarczyć podczas konstruowania.</span><span class="sxs-lookup"><span data-stu-id="0777c-119">The proxy that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> to be provided upon construction.</span></span> <span data-ttu-id="0777c-120">Ta <xref:System.ServiceModel.InstanceContext> wartość jest używana jako witryna obiektu, który implementuje interfejs wywołania zwrotnego i obsługuje komunikaty wysyłane z powrotem z usługi.</span><span class="sxs-lookup"><span data-stu-id="0777c-120">This <xref:System.ServiceModel.InstanceContext> is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="0777c-121">Jest zbudowany z wystąpieniem `CallbackHandler` klasy. <xref:System.ServiceModel.InstanceContext></span><span class="sxs-lookup"><span data-stu-id="0777c-121">An <xref:System.ServiceModel.InstanceContext> is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="0777c-122">Ten obiekt obsługuje komunikaty wysyłane z usługi do klienta w interfejsie wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="0777c-122">This object handles messages sent from the service to the client on the callback interface.</span></span>

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

<span data-ttu-id="0777c-123">Konfiguracja została zmodyfikowana w celu zapewnienia powiązania, które obsługuje komunikację zarówno z komunikacją z sesją, jak i dupleksem.</span><span class="sxs-lookup"><span data-stu-id="0777c-123">The configuration has been modified to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="0777c-124">`wsDualHttpBinding` Obsługuje komunikację z sesją i umożliwia komunikację dwukierunkową przez dostarczanie podwójnych połączeń HTTP, po jednym dla każdego kierunku.</span><span class="sxs-lookup"><span data-stu-id="0777c-124">The `wsDualHttpBinding` supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span> <span data-ttu-id="0777c-125">W usłudze jedyną różnicą w konfiguracji jest używane powiązanie.</span><span class="sxs-lookup"><span data-stu-id="0777c-125">On the service, the only difference in configuration is the binding that is used.</span></span> <span data-ttu-id="0777c-126">Na kliencie należy skonfigurować adres, który może być używany przez serwer do łączenia się z klientem, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="0777c-126">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>

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

<span data-ttu-id="0777c-127">Po uruchomieniu przykładu są wyświetlane komunikaty, które są zwracane do klienta w interfejsie wywołania zwrotnego, który jest wysyłany z usługi.</span><span class="sxs-lookup"><span data-stu-id="0777c-127">When you run the sample, you see the messages that are returned to the client on the callback interface that is sent from the service.</span></span> <span data-ttu-id="0777c-128">Zostanie wyświetlony każdy wynik pośredni, po którym następuje całe równanie po zakończeniu wszystkich operacji.</span><span class="sxs-lookup"><span data-stu-id="0777c-128">Each intermediate result is displayed, followed by the entire equation upon the completion of all operations.</span></span> <span data-ttu-id="0777c-129">Naciśnij klawisz ENTER, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="0777c-129">Press ENTER to shut down the client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0777c-130">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="0777c-130">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="0777c-131">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0777c-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="0777c-132">Aby skompilować C# C++lub Visual Basic wersję .NET rozwiązania, należy postępować zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0777c-132">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="0777c-133">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0777c-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0777c-134">W przypadku uruchamiania klienta programu w konfiguracji obejmującej wiele komputerów należy zamienić wartość "localhost" w `address` atrybucie [ \<> \<punktu końcowego elementu > klienta](../../configure-apps/file-schema/wcf/endpoint-of-client.md) i atrybutu `clientBaseAddress` [ Powiązywanie\<](../../../../docs/framework/misc/binding.md) [ elementu\<> elementu > WSDualHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) o nazwie odpowiedniej maszyny, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0777c-134">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown in the following:</span></span>

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
> <span data-ttu-id="0777c-135">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="0777c-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0777c-136">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="0777c-136">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="0777c-137">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="0777c-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0777c-138">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0777c-138">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`
