---
title: 'Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: b3a105194ceef9d9091dfbc9521fd47978517f89
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521095"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="577e7-102">Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="577e7-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="577e7-103">Ten przykład jest oparty na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki w Windows Communication Foundation (WCF)[rozszerzalność transportu](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="577e7-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span></span> <span data-ttu-id="577e7-104">Rozszerza przykładowe transportu UDP do obsługi przepływu transakcji niestandardowe i zademonstrowano użycie <xref:System.ServiceModel.Channels.TransactionMessageProperty> właściwości.</span><span class="sxs-lookup"><span data-stu-id="577e7-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="577e7-105">Zmiany kodu w przykładzie transportu UDP</span><span class="sxs-lookup"><span data-stu-id="577e7-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="577e7-106">Aby zademonstrować przepływu transakcji, zmienia się kontrakt usługi dla przykładu `ICalculatorContract` będą musieli zakres transakcji `CalculatorService.Add()`.</span><span class="sxs-lookup"><span data-stu-id="577e7-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="577e7-107">Przykładowa aplikacja dodaje również dodatkowy `System.Guid` parametru umowy `Add` operacji.</span><span class="sxs-lookup"><span data-stu-id="577e7-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="577e7-108">Ten parametr jest używany do przekazywania identyfikator transakcja klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="577e7-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
```  
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
  
 <span data-ttu-id="577e7-109">[Transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) przykładowy używa pakietów UDP do przekazywania wiadomości między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="577e7-109">The [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="577e7-110">[Transportu: Przykładowe Transport w niestandardowych](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) używa ten sam mechanizm do transportu komunikatów, ale gdy transakcja jest przepływ, jest wstawiany w pakiecie UDP oraz zakodowanego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="577e7-110">The [Transport: Custom Transport Sample](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="577e7-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` jest metodą pomocnika, która zawiera nowe funkcje, aby scalić tokenu propagacji dla bieżącej transakcji z jednostką wiadomości i umieszczenie go w buforze.</span><span class="sxs-lookup"><span data-stu-id="577e7-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="577e7-112">Transportu przepływu transakcji niestandardowych implementacji klienta musisz wiedzieć, jakie operacje usługi wymagają przepływu transakcji i przekazać te informacje do usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="577e7-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="577e7-113">Należy również mechanizmem przekazywania transakcja użytkownika do warstwy transportowej.</span><span class="sxs-lookup"><span data-stu-id="577e7-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="577e7-114">W tym przykładzie użyto "Inspektorzy komunikatów WCF" Aby uzyskać te informacje.</span><span class="sxs-lookup"><span data-stu-id="577e7-114">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="577e7-115">Klienta wiadomości Inspektor zaimplementowane w tym miejscu, które jest wywoływane `TransactionFlowInspector`, wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="577e7-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
-   <span data-ttu-id="577e7-116">Określa, czy transakcji musi przepływać do działania danej komunikatów (to ma miejsce w `IsTxFlowRequiredForThisOperation()`).</span><span class="sxs-lookup"><span data-stu-id="577e7-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
-   <span data-ttu-id="577e7-117">Dołącza bieżącej transakcji otoczenia do wiadomości przy użyciu `TransactionFlowProperty`, jeśli transakcja jest wymagany do przepływu (jest to realizowane w `BeforeSendRequest()`).</span><span class="sxs-lookup"><span data-stu-id="577e7-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
```  
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
  
 <span data-ttu-id="577e7-118">`TransactionFlowInspector` Sam jest przekazywany do framework za pomocą niestandardowego zachowania: `TransactionFlowBehavior`.</span><span class="sxs-lookup"><span data-stu-id="577e7-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
```  
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
  
 <span data-ttu-id="577e7-119">Przy użyciu poprzednich mechanizmu w miejscu, tworzy kod użytkownika `TransactionScope` przed wywołaniem operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="577e7-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="577e7-120">Inspektor komunikatów gwarantuje, że transakcja jest przekazywany do transportu, w przypadku, gdy musi zostać przekazane do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="577e7-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
```  
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
  
 <span data-ttu-id="577e7-121">Po odebraniu pakietów UDP przez klienta, usługa deserializuje ich w celu wyodrębnienia wiadomość i prawdopodobnie transakcji.</span><span class="sxs-lookup"><span data-stu-id="577e7-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="577e7-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` to metoda pomocnika, która odwraca proces serializacji, wykonywane przez `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span><span class="sxs-lookup"><span data-stu-id="577e7-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="577e7-123">Jeśli transakcja została skierowana w, jest dołączany do wiadomości w `TransactionMessageProperty`.</span><span class="sxs-lookup"><span data-stu-id="577e7-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="577e7-124">Gwarantuje to, że Dyspozytor przejmuje transakcji w czasie wysyłania i używający tych informacji podczas wywoływania operacji usługi opisany w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="577e7-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="577e7-125">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="577e7-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="577e7-126">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="577e7-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="577e7-127">Bieżąca przykładowa powinien zostać uruchomiony podobnie jak [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="577e7-127">The current sample should be run similarly to the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="577e7-128">Aby je uruchomić, należy uruchomić usługę z UdpTestService.exe.</span><span class="sxs-lookup"><span data-stu-id="577e7-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="577e7-129">Jeśli używasz [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], należy uruchomić usługę z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="577e7-129">If you are running [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must start the service with elevated privileges.</span></span> <span data-ttu-id="577e7-130">Aby to zrobić, kliknij prawym przyciskiem myszy UdpTestService.exe w [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] i kliknij przycisk **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="577e7-130">To do so, right-click UdpTestService.exe in [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and click **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="577e7-131">To daje następujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="577e7-131">This produces the following output.</span></span>  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4.  <span data-ttu-id="577e7-132">W tym momencie można uruchomić klienta, uruchamiając UdpTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="577e7-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="577e7-133">Dostępne są następujące dane wyjściowe generowane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="577e7-133">The output produced by the client is as follows.</span></span>  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5.  <span data-ttu-id="577e7-134">Usługa dane wyjściowe wyglądają następująco.</span><span class="sxs-lookup"><span data-stu-id="577e7-134">The service output is as follows.</span></span>  
  
    ```  
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
  
6.  <span data-ttu-id="577e7-135">Aplikacja usługi wyświetla komunikat `The client transaction has flowed to the service` w przypadku znalezienia identyfikatora transakcji wysłane przez klienta, w `clientTransactionId` parametru `CalculatorService.Add()` operacja z identyfikatorem transakcji usługi.</span><span class="sxs-lookup"><span data-stu-id="577e7-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="577e7-136">Dopasowanie uzyskuje się tylko wtedy, gdy transakcja klienta ma przekazane do usługi.</span><span class="sxs-lookup"><span data-stu-id="577e7-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7.  <span data-ttu-id="577e7-137">Aby uruchomić aplikacji klienckiej względem punktów końcowych opublikowanych przy użyciu konfiguracji, naciśnij klawisz ENTER w oknie aplikacji usługi, a następnie ponownie uruchom klienta testowego.</span><span class="sxs-lookup"><span data-stu-id="577e7-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="577e7-138">Następujące dane wyjściowe powinny być widoczne w usłudze.</span><span class="sxs-lookup"><span data-stu-id="577e7-138">You should see the following output on the service.</span></span>  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8.  <span data-ttu-id="577e7-139">Teraz uruchamianie klienta względem usługi generuje dane wyjściowe podobne tak jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="577e7-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="577e7-140">Aby ponownie wygenerować kod klienta i konfiguracji za pomocą Svcutil.exe, uruchamiania aplikacji usługi, a następnie uruchom następujące polecenie Svcutil.exe z katalogu głównego przykładowego.</span><span class="sxs-lookup"><span data-stu-id="577e7-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="577e7-141">Należy pamiętać, Svcutil.exe nie generuje konfigurację rozszerzenia powiązania `sampleProfileUdpBinding`; należy je dodać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="577e7-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
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
>  <span data-ttu-id="577e7-142">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="577e7-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="577e7-143">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="577e7-143">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="577e7-144">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="577e7-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="577e7-145">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="577e7-145">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="577e7-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="577e7-146">See Also</span></span>  
 [<span data-ttu-id="577e7-147">Transport: UDP</span><span class="sxs-lookup"><span data-stu-id="577e7-147">Transport: UDP</span></span>](../../../../docs/framework/wcf/samples/transport-udp.md)
