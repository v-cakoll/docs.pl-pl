---
title: Dupleks
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: 54b941541ae0da4900608e61f08f4ed99c9ea472
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724399"
---
# <a name="duplex"></a><span data-ttu-id="19a6d-102">Dupleks</span><span class="sxs-lookup"><span data-stu-id="19a6d-102">Duplex</span></span>
<span data-ttu-id="19a6d-103">Dwukierunkowe przykładowych pokazano, jak definiować ani implementować kontraktu dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="19a6d-103">The Duplex sample demonstrates how to define and implement a duplex contract.</span></span> <span data-ttu-id="19a6d-104">Komunikację dupleksową występuje, gdy klient ustanawia sesję z usługą i zapewnia usługi kanału, na którym usługa może wysłać wiadomości zwrotnie do klienta.</span><span class="sxs-lookup"><span data-stu-id="19a6d-104">Duplex communication occurs when a client establishes a session with a service and gives the service a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="19a6d-105">Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="19a6d-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="19a6d-106">Kontrakt dupleksu jest zdefiniowany jako pary interfejsów — podstawowy interfejs od klienta do usługi i interfejs wywołania zwrotnego z usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="19a6d-106">A duplex contract is defined as a pair of interfaces—a primary interface from the client to the service and a callback interface from the service to the client.</span></span> <span data-ttu-id="19a6d-107">W tym przykładzie `ICalculatorDuplex` interfejs umożliwia klientowi do wykonywania operacji matematycznych obliczania wyniku za pośrednictwem sesji.</span><span class="sxs-lookup"><span data-stu-id="19a6d-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating the result over a session.</span></span> <span data-ttu-id="19a6d-108">Usługa zwraca wyniki w `ICalculatorDuplexCallback` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="19a6d-108">The service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="19a6d-109">Kontrakt dupleksowy wymaga elementu session, ponieważ kontekst muszą być ustalane do skorelowania zestaw komunikatów przesyłanych między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="19a6d-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19a6d-110">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="19a6d-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="19a6d-111">W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="19a6d-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="19a6d-112">Kontraktu dwukierunkowego jest zdefiniowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="19a6d-112">The duplex contract is defined as follows:</span></span>  
  
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
  
 <span data-ttu-id="19a6d-113">`CalculatorService` Klasa implementuje podstawowy `ICalculatorDuplex` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="19a6d-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="19a6d-114">Używa usługi <xref:System.ServiceModel.InstanceContextMode.PerSession> tryb wystąpienia do obsługi wyników dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="19a6d-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="19a6d-115">Właściwość prywatna o nazwie `Callback` umożliwia dostęp do kanału wywołania zwrotnego do klienta.</span><span class="sxs-lookup"><span data-stu-id="19a6d-115">A private property named `Callback` is used to access the callback channel to the client.</span></span> <span data-ttu-id="19a6d-116">Usługa używa wywołania zwrotnego do wysyłania wiadomości do klienta za pośrednictwem interfejs wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="19a6d-116">The service uses the callback for sending messages back to the client through the callback interface.</span></span>  
  
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
  
 <span data-ttu-id="19a6d-117">Klient musi podać klasę, która implementuje interfejs wywołania zwrotnego kontraktu dwukierunkowego, do odbierania wiadomości z usługi.</span><span class="sxs-lookup"><span data-stu-id="19a6d-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="19a6d-118">W tym przykładzie `CallbackHandler` klasa jest zdefiniowana w celu zaimplementowania `ICalculatorDuplexCallback` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="19a6d-118">In the sample, a `CallbackHandler` class is defined to implement the `ICalculatorDuplexCallback` interface.</span></span>  
  
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
  
 <span data-ttu-id="19a6d-119">Serwer proxy, który jest generowany dla kontraktu dwukierunkowego wymaga <xref:System.ServiceModel.InstanceContext> należy podać podczas konstruowania.</span><span class="sxs-lookup"><span data-stu-id="19a6d-119">The proxy that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> to be provided upon construction.</span></span> <span data-ttu-id="19a6d-120">To <xref:System.ServiceModel.InstanceContext> jest używana jako witryna dla obiektu, który implementuje interfejs wywołania zwrotnego i obsługuje wiadomości wysyłanych na odpowiedź od usługi.</span><span class="sxs-lookup"><span data-stu-id="19a6d-120">This <xref:System.ServiceModel.InstanceContext> is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="19a6d-121"><xref:System.ServiceModel.InstanceContext> Składa się z wystąpieniem `CallbackHandler` klasy.</span><span class="sxs-lookup"><span data-stu-id="19a6d-121">An <xref:System.ServiceModel.InstanceContext> is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="19a6d-122">Ten obiekt obsługi komunikatów wysyłanych z usługi na kliencie, na interfejs wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="19a6d-122">This object handles messages sent from the service to the client on the callback interface.</span></span>  
  
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
  
 <span data-ttu-id="19a6d-123">Konfiguracja została zmodyfikowana, aby zapewnić powiązania, który obsługuje zarówno sesji komunikacji, jak i komunikację dupleksową.</span><span class="sxs-lookup"><span data-stu-id="19a6d-123">The configuration has been modified to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="19a6d-124">`wsDualHttpBinding` Obsługuje komunikację sesji i umożliwia komunikację dupleksową, zapewniając dwa połączenia HTTP, jedno dla każdego kierunku.</span><span class="sxs-lookup"><span data-stu-id="19a6d-124">The `wsDualHttpBinding` supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span> <span data-ttu-id="19a6d-125">W usłudze jedyną różnicą w konfiguracji jest powiązanie, które jest używane.</span><span class="sxs-lookup"><span data-stu-id="19a6d-125">On the service, the only difference in configuration is the binding that is used.</span></span> <span data-ttu-id="19a6d-126">Na komputerze klienckim należy skonfigurować adres który umożliwia Podłącz do klienta, jak pokazano na poniższym Przykładowa konfiguracja serwera.</span><span class="sxs-lookup"><span data-stu-id="19a6d-126">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="19a6d-127">Po uruchomieniu przykładu, zostanie wyświetlone komunikaty, które są zwracane do klienta na interfejs wywołania zwrotnego, które są wysyłane z usługi.</span><span class="sxs-lookup"><span data-stu-id="19a6d-127">When you run the sample, you see the messages that are returned to the client on the callback interface that is sent from the service.</span></span> <span data-ttu-id="19a6d-128">Jest wyświetlany wynik każdego pośrednich następuje całe równanie po ukończeniu wszystkich operacji.</span><span class="sxs-lookup"><span data-stu-id="19a6d-128">Each intermediate result is displayed, followed by the entire equation upon the completion of all operations.</span></span> <span data-ttu-id="19a6d-129">Naciśnij klawisz ENTER, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="19a6d-129">Press ENTER to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="19a6d-130">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="19a6d-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="19a6d-131">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="19a6d-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="19a6d-132">Aby kompilować rozwiązania w wersji języka C#, C++ lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="19a6d-132">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="19a6d-133">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="19a6d-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="19a6d-134">Podczas uruchamiania klienta w konfiguracji między komputerami, należy zastąpić "localhost", w obu `address` atrybutu [punktu końcowego](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) elementu i `clientBaseAddress` atrybutu [ \< Powiązanie >](../../../../docs/framework/misc/binding.md) elementu [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element z nazwą odpowiedniej maszyny, jak pokazano w poniższym:</span><span class="sxs-lookup"><span data-stu-id="19a6d-134">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [endpoint](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element and the `clientBaseAddress` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown in the following:</span></span>  
  
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
>  <span data-ttu-id="19a6d-135">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="19a6d-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="19a6d-136">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="19a6d-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="19a6d-137">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="19a6d-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="19a6d-138">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="19a6d-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`  
  
## <a name="see-also"></a><span data-ttu-id="19a6d-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19a6d-139">See Also</span></span>
