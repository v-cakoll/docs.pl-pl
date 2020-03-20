---
title: 'Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: ba9fb91623606d3aaba5ba56784b20bb92d343a7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143801"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="275ed-102">Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="275ed-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="275ed-103">Ten przykład jest oparty na [przykładzie Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) w[rozszerzalności transportu](../../../../docs/framework/wcf/samples/transport-extensibility.md)fundacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="275ed-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span></span> <span data-ttu-id="275ed-104">Rozszerza przykład transportu UDP do obsługi przepływu transakcji niestandardowych <xref:System.ServiceModel.Channels.TransactionMessageProperty> i pokazuje użycie właściwości.</span><span class="sxs-lookup"><span data-stu-id="275ed-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="275ed-105">Zmiany kodu w przykładzie transportu UDP</span><span class="sxs-lookup"><span data-stu-id="275ed-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="275ed-106">Aby zademonstrować przepływ transakcji, w `ICalculatorContract` przykładzie zmienia się `CalculatorService.Add()`kontrakt serwisowy, aby wymagać zakresu transakcji dla .</span><span class="sxs-lookup"><span data-stu-id="275ed-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="275ed-107">Próbka dodaje również `System.Guid` dodatkowy parametr do `Add` umowy operacji.</span><span class="sxs-lookup"><span data-stu-id="275ed-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="275ed-108">Ten parametr jest używany do przekazywania identyfikatora transakcji klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="275ed-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
```csharp  
class CalculatorService : IDatagramContract, ICalculatorContract  
{  
    [OperationBehavior(TransactionScopeRequired=true)]  
    public int Add(int x, int y, Guid clientTransactionId)  
    {  
        if(Transaction.Current.TransactionInformation.DistributedIdentifier == clientTransactionId)  
    {  
        Console.WriteLine("The client transaction has flowed to the service");  
    }  
    else  
    {  
     Console.WriteLine("The client transaction has NOT flowed to the service");  
    }  
  
    Console.WriteLine("   adding {0} + {1}", x, y);
    return (x + y);  
    }  
  
    [...]  
}  
```  
  
 <span data-ttu-id="275ed-109">Transport: Przykład [UDP](../../../../docs/framework/wcf/samples/transport-udp.md) używa pakietów UDP do przekazywania wiadomości między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="275ed-109">The [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="275ed-110">[Transport: Przykład transportu niestandardowego](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) używa tego samego mechanizmu do transportu wiadomości, ale gdy transakcja jest przepływa, jest wstawiany do pakietu UDP wraz z zakodowaną wiadomością.</span><span class="sxs-lookup"><span data-stu-id="275ed-110">The [Transport: Custom Transport Sample](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="275ed-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer`jest metodą pomocniczą, która zawiera nowe funkcje do scalania tokenu propagacji dla bieżącej transakcji z jednostką wiadomości i umieścić go w buforze.</span><span class="sxs-lookup"><span data-stu-id="275ed-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="275ed-112">W przypadku transportu przepływu transakcji niestandardowych implementacja klienta musi wiedzieć, jakie operacje usługi wymagają przepływu transakcji i przekazać te informacje do WCF.</span><span class="sxs-lookup"><span data-stu-id="275ed-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="275ed-113">Powinien również istnieć mechanizm przesyłania transakcji użytkownika do warstwy transportu.</span><span class="sxs-lookup"><span data-stu-id="275ed-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="275ed-114">W tym przykładzie użyto "Inspektorów komunikatów WCF" w celu uzyskania tych informacji.</span><span class="sxs-lookup"><span data-stu-id="275ed-114">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="275ed-115">Inspektor komunikatów klienta zaimplementowany w tym miejscu, który jest nazywany, `TransactionFlowInspector`wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="275ed-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
- <span data-ttu-id="275ed-116">Określa, czy transakcja musi być przepływana dla danej akcji `IsTxFlowRequiredForThisOperation()`wiadomości (ma to miejsce w ).</span><span class="sxs-lookup"><span data-stu-id="275ed-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
- <span data-ttu-id="275ed-117">Dołącza bieżącą transakcję otoczenia `TransactionFlowProperty`do wiadomości przy użyciu , jeśli transakcja jest `BeforeSendRequest()`wymagana do przepływu (odbywa się to w ).</span><span class="sxs-lookup"><span data-stu-id="275ed-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
```csharp  
public class TransactionFlowInspector : IClientMessageInspector  
{  
   void IClientMessageInspector.AfterReceiveReply(ref           System.ServiceModel.Channels.Message reply, object correlationState)  
  {  
  }  
  
   public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
   {  
       // obtain the tx propagation token  
       byte[] propToken = null;
       if (Transaction.Current != null && IsTxFlowRequiredForThisOperation(request.Headers.Action))  
       {  
           try  
           {  
               propToken = TransactionInterop.GetTransmitterPropagationToken(Transaction.Current);  
           }  
           catch (TransactionException e)  
           {  
              throw new CommunicationException("TransactionInterop.GetTransmitterPropagationToken failed.", e);  
           }  
       }  
  
      // set the propToken on the message in a TransactionFlowProperty  
       TransactionFlowProperty.Set(propToken, request);  
  
       return null;
    }  
  }  
  
  static bool IsTxFlowRequiredForThisOperation(String action)  
 {  
       // In general, this should contain logic to identify which operations (actions)      require transaction flow.  
      [...]  
 }  
}  
```  
  
 <span data-ttu-id="275ed-118">Sama `TransactionFlowInspector` jest przekazywana do struktury przy `TransactionFlowBehavior`użyciu zachowania niestandardowego: .</span><span class="sxs-lookup"><span data-stu-id="275ed-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
```csharp  
public class TransactionFlowBehavior : IEndpointBehavior  
{  
       public void AddBindingParameters(ServiceEndpoint endpoint,            System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
      {  
      }  
  
       public void ApplyClientBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
      {  
            TransactionFlowInspector inspector = new TransactionFlowInspector();  
            clientRuntime.MessageInspectors.Add(inspector);  
      }  
  
      public void ApplyDispatchBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.EndpointDispatcher endpointDispatcher)  
     {  
     }  
  
      public void Validate(ServiceEndpoint endpoint)  
      {  
      }  
}  
```  
  
 <span data-ttu-id="275ed-119">Z poprzedniego mechanizmu w miejscu, kod `TransactionScope` użytkownika tworzy przed wywołaniem operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="275ed-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="275ed-120">Inspektor komunikatów zapewnia, że transakcja jest przekazywana do transportu w przypadku, gdy jest to wymagane do przepływu do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="275ed-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
```csharp  
CalculatorContractClient calculatorClient = new CalculatorContractClient("SampleProfileUdpBinding_ICalculatorContract");  
calculatorClient.Endpoint.Behaviors.Add(new TransactionFlowBehavior());
  
try  
{  
       for (int i = 0; i < 5; ++i)  
      {  
              // call the 'Add' service operation under a transaction scope  
             using (TransactionScope ts = new TransactionScope())  
             {  
        [...]  
        Console.WriteLine(calculatorClient.Add(i, i * 2));  
         }  
      }
       calculatorClient.Close();  
}  
catch (TimeoutException)  
{  
    calculatorClient.Abort();  
}  
catch (CommunicationException)  
{  
    calculatorClient.Abort();  
}  
catch (Exception)  
{  
    calculatorClient.Abort();  
    throw;  
}  
```  
  
 <span data-ttu-id="275ed-121">Po otrzymaniu pakietu UDP od klienta, usługa deserializes go wyodrębnić komunikat i ewentualnie transakcji.</span><span class="sxs-lookup"><span data-stu-id="275ed-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="275ed-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()`jest metodą pomocniczą, która odwraca proces `TransactionMessageBuffer.WriteTransactionMessageBuffer()`serializacji wykonywany przez program .</span><span class="sxs-lookup"><span data-stu-id="275ed-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="275ed-123">Jeśli transakcja została napłynęła, jest dołączana do wiadomości `TransactionMessageProperty`w pliku .</span><span class="sxs-lookup"><span data-stu-id="275ed-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="275ed-124">Gwarantuje to, że dyspozytor odbiera transakcji w czasie wysyłki i używa go podczas wywoływania operacji usługi adresowane przez komunikat.</span><span class="sxs-lookup"><span data-stu-id="275ed-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="275ed-125">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="275ed-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="275ed-126">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="275ed-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="275ed-127">Bieżąca próbka powinna być uruchamiana podobnie do [próbki Transport: UDP.](../../../../docs/framework/wcf/samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="275ed-127">The current sample should be run similarly to the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="275ed-128">Aby go uruchomić, uruchom usługę z UdpTestService.exe.</span><span class="sxs-lookup"><span data-stu-id="275ed-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="275ed-129">Jeśli korzystasz z systemu Windows Vista, musisz uruchomić usługę z podwyższonymi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="275ed-129">If you are running Windows Vista, you must start the service with elevated privileges.</span></span> <span data-ttu-id="275ed-130">W tym celu kliknij prawym przyciskiem myszy program UdpTestService.exe w Eksploratorze plików i kliknij polecenie **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="275ed-130">To do so, right-click UdpTestService.exe in File Explorer and click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="275ed-131">Daje to następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="275ed-131">This produces the following output.</span></span>  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. <span data-ttu-id="275ed-132">W tej chwili można uruchomić klienta, uruchamiając UdpTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="275ed-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="275ed-133">Dane wyjściowe wytwarzane przez klienta są następujące.</span><span class="sxs-lookup"><span data-stu-id="275ed-133">The output produced by the client is as follows.</span></span>  
  
    ```console
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. <span data-ttu-id="275ed-134">Dane wyjściowe usługi są następujące.</span><span class="sxs-lookup"><span data-stu-id="275ed-134">The service output is as follows.</span></span>  
  
    ```console
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    The client transaction has flowed to the service  
       adding 0 + 0  
    The client transaction has flowed to the service  
       adding 1 + 2  
    The client transaction has flowed to the service  
       adding 2 + 4  
    The client transaction has flowed to the service  
       adding 3 + 6  
    The client transaction has flowed to the service  
       adding 4 + 8  
    ```  
  
6. <span data-ttu-id="275ed-135">Aplikacja usługi wyświetla `The client transaction has flowed to the service` komunikat, jeśli może być zgodny z identyfikatorem `clientTransactionId` transakcji `CalculatorService.Add()` wysłanym przez klienta w parametrze operacji do identyfikatora transakcji usługi.</span><span class="sxs-lookup"><span data-stu-id="275ed-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="275ed-136">Dopasowanie jest uzyskiwane tylko wtedy, gdy transakcja klienta przepłynął do usługi.</span><span class="sxs-lookup"><span data-stu-id="275ed-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7. <span data-ttu-id="275ed-137">Aby uruchomić aplikację kliencką względem punktów końcowych opublikowanych przy użyciu konfiguracji, naciśnij klawisz ENTER w oknie aplikacji usługi, a następnie ponownie uruchom klienta testowego.</span><span class="sxs-lookup"><span data-stu-id="275ed-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="275ed-138">W usłudze powinny zostać wyświetlenia następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="275ed-138">You should see the following output on the service.</span></span>  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. <span data-ttu-id="275ed-139">Uruchamianie klienta względem usługi teraz daje podobne dane wyjściowe jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="275ed-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="275ed-140">Aby ponownie wygenerować kod klienta i konfigurację przy użyciu programu Svcutil.exe, uruchom aplikację usługi, a następnie uruchom następujące polecenie Svcutil.exe z katalogu głównego próbki.</span><span class="sxs-lookup"><span data-stu-id="275ed-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="275ed-141">Należy zauważyć, że program Svcutil.exe nie `sampleProfileUdpBinding`generuje konfiguracji rozszerzenia wiązania dla ; należy dodać go ręcznie.</span><span class="sxs-lookup"><span data-stu-id="275ed-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>
            …  
            <extensions>  
                <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
                <bindingExtensions>  
                    <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
                </bindingExtensions>  
            </extensions>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
> [!IMPORTANT]
> <span data-ttu-id="275ed-142">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="275ed-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="275ed-143">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="275ed-143">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="275ed-144">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="275ed-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="275ed-145">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="275ed-145">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="275ed-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="275ed-146">See also</span></span>

- [<span data-ttu-id="275ed-147">Transport: UDP</span><span class="sxs-lookup"><span data-stu-id="275ed-147">Transport: UDP</span></span>](../../../../docs/framework/wcf/samples/transport-udp.md)
