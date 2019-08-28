---
title: 'Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: aeab56c122cff4c8a1ee87cb067f03ee0c2f3227
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044704"
---
# <a name="transport-custom-transactions-over-udp-sample"></a>Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP
Ten przykład jest oparty na [transportach: Przykład](../../../../docs/framework/wcf/samples/transport-udp.md) UDP w ramach[rozszerzalności](../../../../docs/framework/wcf/samples/transport-extensibility.md)transportowej Windows Communication Foundation (WCF). Rozszerza on przykład transportu UDP w celu obsługi niestandardowego przepływu transakcji i demonstruje użycie <xref:System.ServiceModel.Channels.TransactionMessageProperty> właściwości.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>Zmiany kodu w próbce transportu UDP  
 W celu pokazania przepływu transakcji przykład zmienia kontrakt usługi dla `ICalculatorContract` , aby wymagać zakresu transakcji dla. `CalculatorService.Add()` W przykładzie dodano również dodatkowy `System.Guid` parametr do kontraktu `Add` operacji. Ten parametr służy do przekazywania identyfikatora transakcji klienta do usługi.  
  
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
  
 [Transport: Przykład](../../../../docs/framework/wcf/samples/transport-udp.md) UDP używa pakietów UDP do przekazywania komunikatów między klientem a usługą. [Transport: Niestandardowy przykład](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) transportu używa tego samego mechanizmu do transportu komunikatów, ale w przypadku przepełnienia transakcji jest on wstawiany do pakietu UDP wraz z zakodowanym komunikatem.  
  
```  
byte[] txmsgBuffer =                TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer`to metoda pomocnika, która zawiera nowe funkcje umożliwiające scalenie tokenu propagacji dla bieżącej transakcji z jednostką komunikatów i umieszczenie go w buforze.  
  
 W przypadku funkcji niestandardowego transportu przepływów transakcji implementacja klienta musi wiedzieć, jakie operacje usługi wymagają przepływu transakcji i przekazać te informacje do usługi WCF. Powinien być również mechanizm przesyłania transakcji użytkownika do warstwy transportowej. Ten przykład używa "inspektorów komunikatów WCF", aby uzyskać te informacje. W tym miejscu zostanie wykonany Inspektor komunikatów klienta, który `TransactionFlowInspector`jest wywoływany, wykonuje następujące zadania:  
  
- Określa, czy należy wykonać transakcję dla danej akcji komunikatu (ma to miejsce w programie `IsTxFlowRequiredForThisOperation()`).  
  
- Dołącza bieżącą transakcję otoczenia do wiadomości przy użyciu `TransactionFlowProperty`, jeśli transakcja jest wymagana do przepływania (jest to wykonywane w programie `BeforeSendRequest()`).  
  
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
  
 Sama wartość jest przenoszona do struktury przy użyciu zachowania niestandardowego `TransactionFlowBehavior`:. `TransactionFlowInspector`  
  
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
  
 Po powyższym mechanizmie kod użytkownika tworzy `TransactionScope` przed wywołaniem operacji usługi. Inspektor komunikatów zapewnia, że transakcja jest przenoszona do transportu w przypadku, gdy wymagane jest przeprowadzenie operacji usługi.  
  
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
  
 Po odebraniu pakietu UDP od klienta usługa deserializacji ją w celu wyodrębnienia komunikatu i prawdopodobnie transakcji.  
  
```  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()`to metoda pomocnika, która odwraca proces serializacji wykonywany przez `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.  
  
 Jeśli transakcja została przepływa w programie, jest ona dołączana do wiadomości w `TransactionMessageProperty`.  
  
```  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Gwarantuje to, że Dyspozytor pobiera transakcję w czasie wysyłania i używa jej podczas wywoływania operacji usługi rozkierowanej przez komunikat.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Bieżący przykład powinien być uruchamiany podobnie do [transportu: Przykład](../../../../docs/framework/wcf/samples/transport-udp.md) protokołu UDP. Aby go uruchomić, uruchom usługę przy użyciu programu UdpTestService. exe. W przypadku korzystania [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]z programu należy uruchomić usługę z podniesionymi uprawnieniami. Aby to zrobić, kliknij prawym przyciskiem myszy plik UdpTestService. exe w Eksploratorze plików, a następnie kliknij polecenie **Uruchom jako administrator**.  
  
3. Spowoduje to utworzenie następujących danych wyjściowych.  
  
    ```  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. W tej chwili można uruchomić klienta programu, uruchamiając program UdpTestClient. exe. Dane wyjściowe generowane przez klienta programu są następujące.  
  
    ```  
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. Dane wyjściowe usługi są następujące.  
  
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
  
6. Aplikacja usługi wyświetla komunikat `The client transaction has flowed to the service` , jeśli może być zgodny z identyfikatorem transakcji wysyłanym przez klienta `clientTransactionId` w parametrze `CalculatorService.Add()` operacji do identyfikatora transakcji usługi. Dopasowanie jest uzyskiwane tylko wtedy, gdy transakcja klienta została przepływa do usługi.  
  
7. Aby uruchomić aplikację kliencką dla punktów końcowych publikowanych za pomocą konfiguracji, naciśnij klawisz ENTER w oknie aplikacji usługi, a następnie ponownie uruchom klienta testowego. W usłudze powinny zostać wyświetlone następujące dane wyjściowe.  
  
    ```  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. Uruchomienie klienta w usłudze w ramach usługi daje teraz podobne dane wyjściowe tak jak wcześniej.  
  
9. Aby ponownie wygenerować kod i konfigurację klienta przy użyciu programu Svcutil. exe, uruchom aplikację usługi, a następnie uruchom następujące polecenie Svcutil. exe z katalogu głównego przykładu.  
  
    ```  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Należy pamiętać, że Svcutil. exe nie generuje konfiguracji rozszerzenia powiązania dla `sampleProfileUdpBinding`; należy dodać ją ręcznie.  
  
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
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Zobacz także

- [Transportu UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
