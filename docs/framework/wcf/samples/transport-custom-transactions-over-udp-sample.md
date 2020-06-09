---
title: 'Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: ce1e6f0aedff46aaf58e22d8c23c37b03f8789dd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596542"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="a9fb4-102">Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP</span><span class="sxs-lookup"><span data-stu-id="a9fb4-102">Transport: Custom Transactions over UDP Sample</span></span>
<span data-ttu-id="a9fb4-103">Ten przykład jest oparty na [transportach: przykład UDP](transport-udp.md) w ramach[rozszerzalności transportowej](transport-extensibility.md)Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a9fb4-103">This sample is based on the [Transport: UDP](transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](transport-extensibility.md).</span></span> <span data-ttu-id="a9fb4-104">Rozszerza on przykład transportu UDP w celu obsługi niestandardowego przepływu transakcji i demonstruje użycie <xref:System.ServiceModel.Channels.TransactionMessageProperty> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-104">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="a9fb4-105">Zmiany kodu w próbce transportu UDP</span><span class="sxs-lookup"><span data-stu-id="a9fb4-105">Code Changes in the UDP Transport Sample</span></span>  
 <span data-ttu-id="a9fb4-106">W celu pokazania przepływu transakcji przykład zmienia kontrakt usługi dla, `ICalculatorContract` Aby wymagać zakresu transakcji dla `CalculatorService.Add()` .</span><span class="sxs-lookup"><span data-stu-id="a9fb4-106">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="a9fb4-107">W przykładzie dodano również dodatkowy `System.Guid` parametr do kontraktu `Add` operacji.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-107">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="a9fb4-108">Ten parametr służy do przekazywania identyfikatora transakcji klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-108">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
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
  
 <span data-ttu-id="a9fb4-109">[Transport: przykład UDP](transport-udp.md) używa pakietów UDP do przekazywania komunikatów między klientem a usługą.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-109">The [Transport: UDP](transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="a9fb4-110">[Transport: niestandardowy przykład transportu](transport-custom-transactions-over-udp-sample.md) używa tego samego mechanizmu do transportu komunikatów, ale w przypadku przepełnienia transakcji jest on wstawiany do pakietu UDP wraz z zakodowanym komunikatem.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-110">The [Transport: Custom Transport Sample](transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="a9fb4-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer`to metoda pomocnika, która zawiera nowe funkcje umożliwiające scalenie tokenu propagacji dla bieżącej transakcji z jednostką komunikatów i umieszczenie go w buforze.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-111">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="a9fb4-112">W przypadku funkcji niestandardowego transportu przepływów transakcji implementacja klienta musi wiedzieć, jakie operacje usługi wymagają przepływu transakcji i przekazać te informacje do usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-112">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="a9fb4-113">Powinien być również mechanizm przesyłania transakcji użytkownika do warstwy transportowej.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-113">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="a9fb4-114">Ten przykład używa "inspektorów komunikatów WCF", aby uzyskać te informacje.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-114">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="a9fb4-115">W tym miejscu zostanie wykonany Inspektor komunikatów klienta, który jest wywoływany `TransactionFlowInspector` , wykonuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="a9fb4-115">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
- <span data-ttu-id="a9fb4-116">Określa, czy należy wykonać transakcję dla danej akcji komunikatu (ma to miejsce w programie `IsTxFlowRequiredForThisOperation()` ).</span><span class="sxs-lookup"><span data-stu-id="a9fb4-116">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
- <span data-ttu-id="a9fb4-117">Dołącza bieżącą transakcję otoczenia do wiadomości przy użyciu `TransactionFlowProperty` , jeśli transakcja jest wymagana do przepływania (jest to wykonywane w programie `BeforeSendRequest()` ).</span><span class="sxs-lookup"><span data-stu-id="a9fb4-117">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
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
  
 <span data-ttu-id="a9fb4-118">`TransactionFlowInspector`Sama wartość jest przenoszona do struktury przy użyciu zachowania niestandardowego: `TransactionFlowBehavior` .</span><span class="sxs-lookup"><span data-stu-id="a9fb4-118">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
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
  
 <span data-ttu-id="a9fb4-119">Po powyższym mechanizmie kod użytkownika tworzy `TransactionScope` przed wywołaniem operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-119">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="a9fb4-120">Inspektor komunikatów zapewnia, że transakcja jest przenoszona do transportu w przypadku, gdy wymagane jest przeprowadzenie operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-120">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
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
  
 <span data-ttu-id="a9fb4-121">Po odebraniu pakietu UDP od klienta usługa deserializacji ją w celu wyodrębnienia komunikatu i prawdopodobnie transakcji.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-121">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="a9fb4-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()`to metoda pomocnika, która odwraca proces serializacji wykonywany przez `TransactionMessageBuffer.WriteTransactionMessageBuffer()` .</span><span class="sxs-lookup"><span data-stu-id="a9fb4-122">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="a9fb4-123">Jeśli transakcja została przepływa w programie, jest ona dołączana do wiadomości w `TransactionMessageProperty` .</span><span class="sxs-lookup"><span data-stu-id="a9fb4-123">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="a9fb4-124">Gwarantuje to, że Dyspozytor pobiera transakcję w czasie wysyłania i używa jej podczas wywoływania operacji usługi rozkierowanej przez komunikat.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-124">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a9fb4-125">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="a9fb4-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a9fb4-126">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a9fb4-126">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="a9fb4-127">Bieżący przykład powinien być uruchamiany podobnie do [transportu: przykład protokołu UDP](transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="a9fb4-127">The current sample should be run similarly to the [Transport: UDP](transport-udp.md) sample.</span></span> <span data-ttu-id="a9fb4-128">Aby go uruchomić, uruchom usługę przy użyciu programu UdpTestService. exe.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-128">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="a9fb4-129">W przypadku korzystania z systemu Windows Vista należy uruchomić usługę z podniesionymi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-129">If you are running Windows Vista, you must start the service with elevated privileges.</span></span> <span data-ttu-id="a9fb4-130">Aby to zrobić, kliknij prawym przyciskiem myszy plik UdpTestService. exe w Eksploratorze plików, a następnie kliknij polecenie **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-130">To do so, right-click UdpTestService.exe in File Explorer and click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="a9fb4-131">Spowoduje to utworzenie następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-131">This produces the following output.</span></span>  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. <span data-ttu-id="a9fb4-132">W tej chwili można uruchomić klienta programu, uruchamiając program UdpTestClient. exe.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-132">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="a9fb4-133">Dane wyjściowe generowane przez klienta programu są następujące.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-133">The output produced by the client is as follows.</span></span>  
  
    ```console
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. <span data-ttu-id="a9fb4-134">Dane wyjściowe usługi są następujące.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-134">The service output is as follows.</span></span>  
  
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
  
6. <span data-ttu-id="a9fb4-135">Aplikacja usługi wyświetla komunikat, `The client transaction has flowed to the service` Jeśli może być zgodny z identyfikatorem transakcji wysyłanym przez klienta w `clientTransactionId` parametrze `CalculatorService.Add()` operacji do identyfikatora transakcji usługi.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-135">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="a9fb4-136">Dopasowanie jest uzyskiwane tylko wtedy, gdy transakcja klienta została przepływa do usługi.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-136">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7. <span data-ttu-id="a9fb4-137">Aby uruchomić aplikację kliencką dla punktów końcowych publikowanych za pomocą konfiguracji, naciśnij klawisz ENTER w oknie aplikacji usługi, a następnie ponownie uruchom klienta testowego.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-137">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="a9fb4-138">W usłudze powinny zostać wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-138">You should see the following output on the service.</span></span>  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. <span data-ttu-id="a9fb4-139">Uruchomienie klienta w usłudze w ramach usługi daje teraz podobne dane wyjściowe tak jak wcześniej.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-139">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="a9fb4-140">Aby ponownie wygenerować kod i konfigurację klienta przy użyciu programu Svcutil. exe, uruchom aplikację usługi, a następnie uruchom następujące polecenie Svcutil. exe z katalogu głównego przykładu.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-140">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="a9fb4-141">Należy pamiętać, że Svcutil. exe nie generuje konfiguracji rozszerzenia powiązania dla `sampleProfileUdpBinding` ; należy dodać ją ręcznie.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-141">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
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
> <span data-ttu-id="a9fb4-142">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a9fb4-143">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="a9fb4-143">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a9fb4-144">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a9fb4-145">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a9fb4-145">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="a9fb4-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9fb4-146">See also</span></span>

- [<span data-ttu-id="a9fb4-147">Transport: UDP</span><span class="sxs-lookup"><span data-stu-id="a9fb4-147">Transport: UDP</span></span>](transport-udp.md)
