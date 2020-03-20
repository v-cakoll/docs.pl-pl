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
# <a name="transport-custom-transactions-over-udp-sample"></a>Transport: Przykład niestandardowych transakcji przeprowadzanych za pośrednictwem protokołu UDP
Ten przykład jest oparty na [przykładzie Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) w[rozszerzalności transportu](../../../../docs/framework/wcf/samples/transport-extensibility.md)fundacji Windows Communication Foundation (WCF). Rozszerza przykład transportu UDP do obsługi przepływu transakcji niestandardowych <xref:System.ServiceModel.Channels.TransactionMessageProperty> i pokazuje użycie właściwości.  
  
## <a name="code-changes-in-the-udp-transport-sample"></a>Zmiany kodu w przykładzie transportu UDP  
 Aby zademonstrować przepływ transakcji, w `ICalculatorContract` przykładzie zmienia się `CalculatorService.Add()`kontrakt serwisowy, aby wymagać zakresu transakcji dla . Próbka dodaje również `System.Guid` dodatkowy parametr do `Add` umowy operacji. Ten parametr jest używany do przekazywania identyfikatora transakcji klienta do usługi.  
  
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
  
 Transport: Przykład [UDP](../../../../docs/framework/wcf/samples/transport-udp.md) używa pakietów UDP do przekazywania wiadomości między klientem a usługą. [Transport: Przykład transportu niestandardowego](../../../../docs/framework/wcf/samples/transport-custom-transactions-over-udp-sample.md) używa tego samego mechanizmu do transportu wiadomości, ale gdy transakcja jest przepływa, jest wstawiany do pakietu UDP wraz z zakodowaną wiadomością.  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 `TransactionMessageBuffer.WriteTransactionMessageBuffer`jest metodą pomocniczą, która zawiera nowe funkcje do scalania tokenu propagacji dla bieżącej transakcji z jednostką wiadomości i umieścić go w buforze.  
  
 W przypadku transportu przepływu transakcji niestandardowych implementacja klienta musi wiedzieć, jakie operacje usługi wymagają przepływu transakcji i przekazać te informacje do WCF. Powinien również istnieć mechanizm przesyłania transakcji użytkownika do warstwy transportu. W tym przykładzie użyto "Inspektorów komunikatów WCF" w celu uzyskania tych informacji. Inspektor komunikatów klienta zaimplementowany w tym miejscu, który jest nazywany, `TransactionFlowInspector`wykonuje następujące zadania:  
  
- Określa, czy transakcja musi być przepływana dla danej akcji `IsTxFlowRequiredForThisOperation()`wiadomości (ma to miejsce w ).  
  
- Dołącza bieżącą transakcję otoczenia `TransactionFlowProperty`do wiadomości przy użyciu , jeśli transakcja jest `BeforeSendRequest()`wymagana do przepływu (odbywa się to w ).  
  
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
  
 Sama `TransactionFlowInspector` jest przekazywana do struktury przy `TransactionFlowBehavior`użyciu zachowania niestandardowego: .  
  
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
  
 Z poprzedniego mechanizmu w miejscu, kod `TransactionScope` użytkownika tworzy przed wywołaniem operacji usługi. Inspektor komunikatów zapewnia, że transakcja jest przekazywana do transportu w przypadku, gdy jest to wymagane do przepływu do operacji usługi.  
  
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
  
 Po otrzymaniu pakietu UDP od klienta, usługa deserializes go wyodrębnić komunikat i ewentualnie transakcji.  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 `TransactionMessageBuffer.ReadTransactionMessageBuffer()`jest metodą pomocniczą, która odwraca proces `TransactionMessageBuffer.WriteTransactionMessageBuffer()`serializacji wykonywany przez program .  
  
 Jeśli transakcja została napłynęła, jest dołączana do wiadomości `TransactionMessageProperty`w pliku .  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 Gwarantuje to, że dyspozytor odbiera transakcji w czasie wysyłki i używa go podczas wywoływania operacji usługi adresowane przez komunikat.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Bieżąca próbka powinna być uruchamiana podobnie do [próbki Transport: UDP.](../../../../docs/framework/wcf/samples/transport-udp.md) Aby go uruchomić, uruchom usługę z UdpTestService.exe. Jeśli korzystasz z systemu Windows Vista, musisz uruchomić usługę z podwyższonymi uprawnieniami. W tym celu kliknij prawym przyciskiem myszy program UdpTestService.exe w Eksploratorze plików i kliknij polecenie **Uruchom jako administrator**.  
  
3. Daje to następujące dane wyjściowe.  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. W tej chwili można uruchomić klienta, uruchamiając UdpTestClient.exe. Dane wyjściowe wytwarzane przez klienta są następujące.  
  
    ```console
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. Dane wyjściowe usługi są następujące.  
  
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
  
6. Aplikacja usługi wyświetla `The client transaction has flowed to the service` komunikat, jeśli może być zgodny z identyfikatorem `clientTransactionId` transakcji `CalculatorService.Add()` wysłanym przez klienta w parametrze operacji do identyfikatora transakcji usługi. Dopasowanie jest uzyskiwane tylko wtedy, gdy transakcja klienta przepłynął do usługi.  
  
7. Aby uruchomić aplikację kliencką względem punktów końcowych opublikowanych przy użyciu konfiguracji, naciśnij klawisz ENTER w oknie aplikacji usługi, a następnie ponownie uruchom klienta testowego. W usłudze powinny zostać wyświetlenia następujące dane wyjściowe.  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. Uruchamianie klienta względem usługi teraz daje podobne dane wyjściowe jak poprzednio.  
  
9. Aby ponownie wygenerować kod klienta i konfigurację przy użyciu programu Svcutil.exe, uruchom aplikację usługi, a następnie uruchom następujące polecenie Svcutil.exe z katalogu głównego próbki.  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. Należy zauważyć, że program Svcutil.exe nie `sampleProfileUdpBinding`generuje konfiguracji rozszerzenia wiązania dla ; należy dodać go ręcznie.  
  
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
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a>Zobacz też

- [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
