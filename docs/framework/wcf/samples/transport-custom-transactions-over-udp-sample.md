---
title: 'Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: 931cedfeb5604b00ec1cf3f4d2742e2dff2eacca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552215"
---
# <a name="transport-custom-transactions-over-udp-sample"></a>Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP
Ten przykład jest oparty na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki w Windows Communication Foundation (WCF)[rozszerzalność transportu](../../../../docs/framework/wcf/samples/transport-extensibility.md). Rozszerza przykładowe transportu UDP do obsługi przepływu transakcji niestandardowe i zademonstrowano użycie <xref:System.ServiceModel.Channels.TransactionMessageProperty> właściwości.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>Zmiany kodu w przykładzie transportu UDP  
 Aby zademonstrować przepływu transakcji, zmienia się kontrakt usługi dla przykładu `ICalculatorContract` będą musieli zakres transakcji `CalculatorService.Add()`. Przykładowa aplikacja dodaje również dodatkowy `System.Guid` parametru umowy `Add` operacji. Ten parametr jest używany do przekazywania identyfikator transakcja klienta do usługi.  
  
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
  
 [Transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) przykładowy używa pakietów UDP do przekazywania wiadomości między klientem a usługą. [Transportu: Niestandardowe przykładowe transportu](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) używa ten sam mechanizm do transportu komunikatów, ale gdy transakcja jest przepływ, jest wstawiany w pakiecie UDP oraz zakodowanego komunikatu.  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer` jest metodą pomocnika, która zawiera nowe funkcje, aby scalić tokenu propagacji dla bieżącej transakcji z jednostką wiadomości i umieszczenie go w buforze.  
  
 Transportu przepływu transakcji niestandardowych implementacji klienta musisz wiedzieć, jakie operacje usługi wymagają przepływu transakcji i przekazać te informacje do usługi WCF. Należy również mechanizmem przekazywania transakcja użytkownika do warstwy transportowej. W tym przykładzie użyto "Inspektorzy komunikatów WCF" Aby uzyskać te informacje. Klienta wiadomości Inspektor zaimplementowane w tym miejscu, które jest wywoływane `TransactionFlowInspector`, wykonuje następujące zadania:  
  
-   Określa, czy transakcji musi przepływać do działania danej komunikatów (to ma miejsce w `IsTxFlowRequiredForThisOperation()`).  
  
-   Dołącza bieżącej transakcji otoczenia do wiadomości przy użyciu `TransactionFlowProperty`, jeśli transakcja jest wymagany do przepływu (jest to realizowane w `BeforeSendRequest()`).  
  
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
  
 `TransactionFlowInspector` Sam jest przekazywany do framework za pomocą niestandardowego zachowania: `TransactionFlowBehavior`.  
  
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
  
 Przy użyciu poprzednich mechanizmu w miejscu, tworzy kod użytkownika `TransactionScope` przed wywołaniem operacji usługi. Inspektor komunikatów gwarantuje, że transakcja jest przekazywany do transportu, w przypadku, gdy musi zostać przekazane do operacji usługi.  
  
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
  
 Po odebraniu pakietów UDP przez klienta, usługa deserializuje ich w celu wyodrębnienia wiadomość i prawdopodobnie transakcji.  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()` to metoda pomocnika, która odwraca proces serializacji, wykonywane przez `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.  
  
 Jeśli transakcja została skierowana w, jest dołączany do wiadomości w `TransactionMessageProperty`.  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Gwarantuje to, że Dyspozytor przejmuje transakcji w czasie wysyłania i używający tych informacji podczas wywoływania operacji usługi opisany w komunikacie.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Bieżąca przykładowa powinien zostać uruchomiony podobnie jak [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki. Aby je uruchomić, należy uruchomić usługę z UdpTestService.exe. Jeśli używasz [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], należy uruchomić usługę z podwyższonym poziomem uprawnień. Aby to zrobić, kliknij prawym przyciskiem myszy UdpTestService.exe w [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] i kliknij przycisk **Uruchom jako administrator**.  
  
3.  To daje następujące wyniki.  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4.  W tym momencie można uruchomić klienta, uruchamiając UdpTestClient.exe. Dostępne są następujące dane wyjściowe generowane przez klienta.  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5.  Usługa dane wyjściowe wyglądają następująco.  
  
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
  
6.  Aplikacja usługi wyświetla komunikat `The client transaction has flowed to the service` w przypadku znalezienia identyfikatora transakcji wysłane przez klienta, w `clientTransactionId` parametru `CalculatorService.Add()` operacja z identyfikatorem transakcji usługi. Dopasowanie uzyskuje się tylko wtedy, gdy transakcja klienta ma przekazane do usługi.  
  
7.  Aby uruchomić aplikacji klienckiej względem punktów końcowych opublikowanych przy użyciu konfiguracji, naciśnij klawisz ENTER w oknie aplikacji usługi, a następnie ponownie uruchom klienta testowego. Następujące dane wyjściowe powinny być widoczne w usłudze.  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8.  Teraz uruchamianie klienta względem usługi generuje dane wyjściowe podobne tak jak poprzednio.  
  
9. Aby ponownie wygenerować kod klienta i konfiguracji za pomocą Svcutil.exe, uruchamiania aplikacji usługi, a następnie uruchom następujące polecenie Svcutil.exe z katalogu głównego przykładowego.  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Należy pamiętać, Svcutil.exe nie generuje konfigurację rozszerzenia powiązania `sampleProfileUdpBinding`; należy je dodać ręcznie.  
  
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
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Zobacz także
- [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
