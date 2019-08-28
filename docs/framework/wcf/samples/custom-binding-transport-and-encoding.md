---
title: Transport i kodowanie powiązań niestandardowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: f5a5add36d0d93785a8f63793ff4bc296ffebc8b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040027"
---
# <a name="custom-binding-transport-and-encoding"></a>Transport i kodowanie powiązań niestandardowych
Niestandardowe powiązanie jest definiowane przez uporządkowaną listę elementów powiązania dyskretnego. W tym przykładzie pokazano, jak skonfigurować powiązanie niestandardowe z różnymi elementami transportu i przenoszenia komunikatów.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład jest oparty na [samym hoście](../../../../docs/framework/wcf/samples/self-host.md)i został zmodyfikowany w celu skonfigurowania trzech punktów końcowych do obsługi transportów http, TCP i nazwany potok z powiązaniami niestandardowymi. Konfiguracja klienta została zmodyfikowana w podobny sposób, a kod klienta został zmieniony, aby komunikować się z każdym z trzech punktów końcowych.  
  
 W przykładzie przedstawiono sposób konfigurowania niestandardowego powiązania, które obsługuje określony transport i kodowanie komunikatów. W tym celu należy skonfigurować Transport i kodowanie komunikatów dla `binding` elementu. Kolejność elementów powiązania jest istotna dla definiowania niestandardowego powiązania, ponieważ każdy reprezentuje warstwę w stosie kanału (zobacz [powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)). Ten przykład konfiguruje trzy powiązania niestandardowe: transport HTTP z kodowaniem tekstu, transport TCP z kodowaniem tekstu oraz transport nazwany potok z kodowaniem binarnym.  
  
 Konfiguracja usługi definiuje niestandardowe powiązania w następujący sposób:  
  
```xml  
<bindings>  
    <customBinding>  
        <binding name="HttpBinding" >  
            <textMessageEncoding   
                messageVersion="Soap12Addressing10"/>  
            <httpTransport />  
        </binding>  
        <binding name="TcpBinding" >  
            <textMessageEncoding />  
            <tcpTransport />  
        </binding>  
        <binding name="NamedPipeBinding" >  
            <binaryMessageEncoding />  
            <namedPipeTransport />  
        </binding>  
    </customBinding>  
</bindings>  
```  
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane zarówno w oknie usługi, jak i w konsoli klienta. Klient komunikuje się z każdym z trzech punktów końcowych, uzyskując dostęp do pierwszego protokołu HTTP, a następnie TCP i finally nazwany potok. Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.  
  
 `namedPipeTransport` Powiązanie nie obsługuje operacji na komputerze. Jest on używany tylko do komunikacji na tym samym komputerze. W związku z tym podczas uruchamiania przykładu w scenariuszu między maszynami należy dodać komentarz do następujących wierszy w pliku kodu klienta:  
  
```csharp  
CalculatorClient client = new CalculatorClient("default");  
Console.WriteLine("Communicate with named pipe endpoint.");  
// Call operations.  
DoCalculations(client);  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
```vb  
Dim client As New CalculatorClient("default")  
Console.WriteLine("Communicate with named pipe endpoint.")  
' call operations  
DoCalculations(client)  
'Closing the client gracefully closes the connection and cleans up resources  
client.Close()  
```  
  
> [!NOTE]
> Jeśli używasz programu Svcutil. exe w celu ponownego wygenerowania konfiguracji dla tego przykładu, pamiętaj, aby zmodyfikować nazwę punktu końcowego w konfiguracji klienta w celu dopasowania go do kodu klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# C++lub Visual Basic wersję .NET rozwiązania, należy postępować zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
