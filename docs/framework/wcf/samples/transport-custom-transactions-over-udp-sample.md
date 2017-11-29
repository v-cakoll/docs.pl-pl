---
title: "Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9c1586b763d98776468322144019407c7c6cc27a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="dce87-102">Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="dce87-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="dce87-103">Ten przykład jest oparty na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) przykładowa w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] [rozszerzalność transportu](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="dce87-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample in the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)][Transport Extensibility](../../../../docs/framework/wcf/samples/transport-extensibility.md).</span></span> <span data-ttu-id="dce87-104">Rozszerza próbki transportu UDP do obsługi przepływu transakcji niestandardowe i pokazuje użycie <xref:System.ServiceModel.Channels.TransactionMessageProperty> właściwości.</span><span class="sxs-lookup"><span data-stu-id="dce87-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="dce87-105">Zmiany kodu w przykładowym transportu UDP</span><span class="sxs-lookup"><span data-stu-id="dce87-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="dce87-106">Aby zademonstrować przepływu transakcji, próbki zmienia umowy serwisowej dla `ICalculatorContract` wymagające zakresu transakcji dla `CalculatorService.Add()`.</span><span class="sxs-lookup"><span data-stu-id="dce87-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="dce87-107">Próbki dodaje również dodatkową `System.Guid` parametru umowy `Add` operacji.</span><span class="sxs-lookup"><span data-stu-id="dce87-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="dce87-108">Ten parametr jest używany do przekazania identyfikator transakcji klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="dce87-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
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
  
 <span data-ttu-id="dce87-109">[Transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) w przykładzie użyto pakietów UDP do przekazywania wiadomości między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="dce87-109">The [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="dce87-110">[Transport: niestandardowe transportu próbki](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) używany ten sam mechanizm do transportu wiadomości, ale podczas transakcji jest umieszczane, zostanie on włożony do pakietów UDP razem z zakodowanym wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dce87-110">The [Transport: Custom Transport Sample](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="dce87-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer`to metoda pomocnika, która zawiera nową funkcję tokenu propagacji dla bieżącej transakcji z jednostką wiadomości i umieszczenie go w buforze.</span><span class="sxs-lookup"><span data-stu-id="dce87-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="dce87-112">Dla transportu przepływu transakcji niestandardowych, implementacja klienta musi wiedzieć, jakie operacje usługi wymaga przepływu transakcji oraz przekazywanie tych informacji do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dce87-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="dce87-113">Należy również mechanizm przekazywania transakcji użytkownika do warstwy transportowej.</span><span class="sxs-lookup"><span data-stu-id="dce87-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="dce87-114">W przykładzie użyto "[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inspektorzy komunikatów" Aby uzyskać te informacje.</span><span class="sxs-lookup"><span data-stu-id="dce87-114">This sample uses "[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] message inspectors" to obtain this information.</span></span> <span data-ttu-id="dce87-115">Klienta komunikat Inspektor zaimplementowano, która jest wywoływana `TransactionFlowInspector`, wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="dce87-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
-   <span data-ttu-id="dce87-116">Określa, czy transakcja musi przepływ działania danej wiadomości (ma to miejsce w `IsTxFlowRequiredForThisOperation()`).</span><span class="sxs-lookup"><span data-stu-id="dce87-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
-   <span data-ttu-id="dce87-117">Dołącza do wiadomości przy użyciu bieżąca transakcja otoczenia `TransactionFlowProperty`, gdy jest wymagane przepływu transakcji (jest to wykonywane w `BeforeSendRequest()`).</span><span class="sxs-lookup"><span data-stu-id="dce87-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
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
  
 <span data-ttu-id="dce87-118">`TransactionFlowInspector` Sam jest przekazywana do framework za pomocą niestandardowego zachowania: `TransactionFlowBehavior`.</span><span class="sxs-lookup"><span data-stu-id="dce87-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
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
  
 <span data-ttu-id="dce87-119">W poprzednim mechanizmu w miejscu, tworzy kod użytkownika `TransactionScope` przed wywołaniem operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="dce87-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="dce87-120">Inspektor komunikatów gwarantuje, że transakcja jest przekazywany do transportu w przypadku, gdy jest wymagane jest skierowana do operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="dce87-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
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
  
 <span data-ttu-id="dce87-121">Po odebraniu pakietów UDP od klienta, usługa deserializuje plik w celu wyodrębnienia wiadomość i prawdopodobnie transakcji.</span><span class="sxs-lookup"><span data-stu-id="dce87-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="dce87-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()`jest to metoda pomocnika odwraca proces serializacji wykonywane przez `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span><span class="sxs-lookup"><span data-stu-id="dce87-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="dce87-123">Jeśli transakcja została skierowana w, jest dołączany do wiadomości w `TransactionMessageProperty`.</span><span class="sxs-lookup"><span data-stu-id="dce87-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="dce87-124">Dzięki temu, że Dyspozytor przejmuje transakcji w czasie wysyłania i używający tych informacji podczas wywoływania operacji usługi opisany w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="dce87-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dce87-125">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="dce87-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="dce87-126">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dce87-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="dce87-127">Przykładowe bieżącego powinny być uruchamiane w podobny [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="dce87-127">The current sample should be run similarly to the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="dce87-128">Aby go uruchomić, należy uruchomić usługę z UdpTestService.exe.</span><span class="sxs-lookup"><span data-stu-id="dce87-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="dce87-129">Jeśli używasz [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], należy uruchomić usługę z podwyższonym poziomem uprawnień.</span><span class="sxs-lookup"><span data-stu-id="dce87-129">If you are running [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], you must start the service with elevated privileges.</span></span> <span data-ttu-id="dce87-130">Aby to zrobić, kliknij prawym przyciskiem myszy UdpTestService.exe w [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] i kliknij przycisk **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="dce87-130">To do so, right-click UdpTestService.exe in [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and click **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="dce87-131">Daje to następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="dce87-131">This produces the following output.</span></span>  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4.  <span data-ttu-id="dce87-132">W tej chwili można uruchomić, uruchamiając UdpTestClient.exe klienta.</span><span class="sxs-lookup"><span data-stu-id="dce87-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="dce87-133">Poniżej przedstawiono dane wyjściowe, generowane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="dce87-133">The output produced by the client is as follows.</span></span>  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5.  <span data-ttu-id="dce87-134">Poniżej przedstawiono dane wyjściowe usługi.</span><span class="sxs-lookup"><span data-stu-id="dce87-134">The service output is as follows.</span></span>  
  
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
  
6.  <span data-ttu-id="dce87-135">Aplikacja usługi wyświetla komunikat `The client transaction has flowed to the service` w przypadku znalezienia identyfikatora transakcji wysyłane przez klienta, w `clientTransactionId` parametr `CalculatorService.Add()` na identyfikator transakcji usługi operacji.</span><span class="sxs-lookup"><span data-stu-id="dce87-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="dce87-136">Dopasowanie uzyskuje się tylko wtedy, gdy transakcja klienta przeszło do usługi.</span><span class="sxs-lookup"><span data-stu-id="dce87-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7.  <span data-ttu-id="dce87-137">Aby uruchomić aplikację klienta przed opublikowane za pomocą konfiguracji punktów końcowych, naciśnij klawisz ENTER w oknie aplikacji usługi, a następnie ponownie uruchom klienta testowego.</span><span class="sxs-lookup"><span data-stu-id="dce87-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="dce87-138">Następujące dane wyjściowe powinny być widoczne w usłudze.</span><span class="sxs-lookup"><span data-stu-id="dce87-138">You should see the following output on the service.</span></span>  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8.  <span data-ttu-id="dce87-139">Teraz uruchamianie klienta z usługą generuje dane wyjściowe podobne jak poprzednio.</span><span class="sxs-lookup"><span data-stu-id="dce87-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="dce87-140">Można ponownie wygenerować kod klienta i konfiguracji przy użyciu Svcutil.exe, uruchom aplikację usługi, a następnie uruchom następujące polecenie Svcutil.exe z katalogu głównego próbki.</span><span class="sxs-lookup"><span data-stu-id="dce87-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="dce87-141">Należy pamiętać, że Svcutil.exe nie generuje konfiguracji rozszerzenia powiązania dla `sampleProfileUdpBinding`; należy go dodać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="dce87-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
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
>  <span data-ttu-id="dce87-142">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="dce87-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dce87-143">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="dce87-143">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dce87-144">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="dce87-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dce87-145">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="dce87-145">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="dce87-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dce87-146">See Also</span></span>  
 [<span data-ttu-id="dce87-147">Transport: UDP</span><span class="sxs-lookup"><span data-stu-id="dce87-147">Transport: UDP</span></span>](../../../../docs/framework/wcf/samples/transport-udp.md)
