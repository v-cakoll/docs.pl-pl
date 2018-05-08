---
title: 'Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: e395300df4cd9917b9662d4bc3b1e8d50d82914d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="transport-custom-transactions-over-udp-sample"></a>Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP
Ten przykład jest oparty na [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) przykład w systemie Windows Communication Foundation (WCF)[rozszerzalność transportu](../../../../docs/framework/wcf/samples/transport-extensibility.md). Rozszerza próbki transportu UDP do obsługi przepływu transakcji niestandardowe i pokazuje użycie <xref:System.ServiceModel.Channels.TransactionMessageProperty> właściwości.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>Zmiany kodu w przykładowym transportu UDP  
 Aby zademonstrować przepływu transakcji, próbki zmienia umowy serwisowej dla `ICalculatorContract` wymagające zakresu transakcji dla `CalculatorService.Add()`. Próbki dodaje również dodatkową `System.Guid` parametru umowy `Add` operacji. Ten parametr jest używany do przekazania identyfikator transakcji klienta do usługi.  
  
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
  
 [Transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) w przykładzie użyto pakietów UDP do przekazywania wiadomości między klientem a usługą. [Transport: niestandardowe transportu próbki](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) używany ten sam mechanizm do transportu wiadomości, ale podczas transakcji jest umieszczane, zostanie on włożony do pakietów UDP razem z zakodowanym wiadomości.  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer` to metoda pomocnika, która zawiera nową funkcję tokenu propagacji dla bieżącej transakcji z jednostką wiadomości i umieszczenie go w buforze.  
  
 Dla transportu przepływu transakcji niestandardowych, implementacja klienta musi wiedzieć, jakie operacje usługi wymaga przepływu transakcji oraz przekazywanie tych informacji do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Należy również mechanizm przekazywania transakcji użytkownika do warstwy transportowej. W przykładzie użyto "[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inspektorzy komunikatów" Aby uzyskać te informacje. Klienta komunikat Inspektor zaimplementowano, która jest wywoływana `TransactionFlowInspector`, wykonuje następujące zadania:  
  
-   Określa, czy transakcja musi przepływ działania danej wiadomości (ma to miejsce w `IsTxFlowRequiredForThisOperation()`).  
  
-   Dołącza do wiadomości przy użyciu bieżąca transakcja otoczenia `TransactionFlowProperty`, gdy jest wymagane przepływu transakcji (jest to wykonywane w `BeforeSendRequest()`).  
  
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
  
 `TransactionFlowInspector` Sam jest przekazywana do framework za pomocą niestandardowego zachowania: `TransactionFlowBehavior`.  
  
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
  
 W poprzednim mechanizmu w miejscu, tworzy kod użytkownika `TransactionScope` przed wywołaniem operacji usługi. Inspektor komunikatów gwarantuje, że transakcja jest przekazywany do transportu w przypadku, gdy jest wymagane jest skierowana do operacji usługi.  
  
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
  
 Po odebraniu pakietów UDP od klienta, usługa deserializuje plik w celu wyodrębnienia wiadomość i prawdopodobnie transakcji.  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()` jest to metoda pomocnika odwraca proces serializacji wykonywane przez `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.  
  
 Jeśli transakcja została skierowana w, jest dołączany do wiadomości w `TransactionMessageProperty`.  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Dzięki temu, że Dyspozytor przejmuje transakcji w czasie wysyłania i używający tych informacji podczas wywoływania operacji usługi opisany w komunikacie.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Przykładowe bieżącego powinny być uruchamiane w podobny [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki. Aby go uruchomić, należy uruchomić usługę z UdpTestService.exe. Jeśli używasz [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)], należy uruchomić usługę z podwyższonym poziomem uprawnień. Aby to zrobić, kliknij prawym przyciskiem myszy UdpTestService.exe w [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] i kliknij przycisk **Uruchom jako administrator**.  
  
3.  Daje to następujące dane wyjściowe.  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4.  W tej chwili można uruchomić, uruchamiając UdpTestClient.exe klienta. Poniżej przedstawiono dane wyjściowe, generowane przez klienta.  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5.  Poniżej przedstawiono dane wyjściowe usługi.  
  
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
  
6.  Aplikacja usługi wyświetla komunikat `The client transaction has flowed to the service` w przypadku znalezienia identyfikatora transakcji wysyłane przez klienta, w `clientTransactionId` parametr `CalculatorService.Add()` na identyfikator transakcji usługi operacji. Dopasowanie uzyskuje się tylko wtedy, gdy transakcja klienta przeszło do usługi.  
  
7.  Aby uruchomić aplikację klienta przed opublikowane za pomocą konfiguracji punktów końcowych, naciśnij klawisz ENTER w oknie aplikacji usługi, a następnie ponownie uruchom klienta testowego. Następujące dane wyjściowe powinny być widoczne w usłudze.  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8.  Teraz uruchamianie klienta z usługą generuje dane wyjściowe podobne jak poprzednio.  
  
9. Można ponownie wygenerować kod klienta i konfiguracji przy użyciu Svcutil.exe, uruchom aplikację usługi, a następnie uruchom następujące polecenie Svcutil.exe z katalogu głównego próbki.  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Należy pamiętać, że Svcutil.exe nie generuje konfiguracji rozszerzenia powiązania dla `sampleProfileUdpBinding`; należy go dodać ręcznie.  
  
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
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Zobacz też  
 [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
