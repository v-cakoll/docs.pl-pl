---
title: Transport i kodowanie powiązań niestandardowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: d293ccb45a3af85ca5ca23fec9e3c01a55564581
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767574"
---
# <a name="custom-binding-transport-and-encoding"></a>Transport i kodowanie powiązań niestandardowych
Powiązanie niestandardowe jest definiowany przez uporządkowaną listą elementy powiązania dyskretnych. Niniejszy przykład pokazuje, jak skonfigurować powiązania niestandardowego z różnymi transport i kodowanie elementów wiadomości.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Ten przykład jest oparty na [hosta samodzielnego](../../../../docs/framework/wcf/samples/self-host.md)i została zmodyfikowana, aby skonfigurować trzy punkty końcowe do obsługi protokołu HTTP, TCP i nazwany potok transportów powiązań niestandardowych. Podobnie modyfikacji konfiguracji klienta, a następnie zmienić kodu klienta do komunikowania się z każdym z trzech punktów końcowych.  
  
 W przykładzie pokazano, jak skonfigurować niestandardowe powiązanie, które obsługuje danego transportu i kodowanie komunikatu. Jest to realizowane przez skonfigurowanie transport i kodowanie komunikatu `binding` elementu. Określanie kolejności elementów wiązania jest ważny w celu definiowania niestandardowego powiązania, ponieważ każdy z nich reprezentuje warstwę w stosie kanału (zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md)). Ten przykład umożliwia skonfigurowanie trzy powiązań niestandardowych: protokół transportu HTTP przy użyciu kodowania tekstu, warstwy transportowej TCP za pomocą kodowania tekstu i transport nazwany potok przy użyciu kodowania binarnego.  
  
 Konfiguracja usługi definiuje powiązań niestandardowych w następujący sposób:  
  
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
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli usługi i klienta. Klient komunikuje się z każdym z trzech punktów końcowych, uzyskiwanie dostępu do pierwszego HTTP, a następnie TCP, a na końcu nazwany potok. Naciśnij klawisz ENTER każdego okna konsoli, aby zamknąć usługę i klienta.  
  
 `namedPipeTransport` Powiązanie nie obsługuje operacji od maszyny. Jest on używany tylko do komunikacji na tym samym komputerze. W związku z tym gdy działa aplikacja przykładowa w scenariuszu między komputerami, jako komentarz następujące wiersze w pliku kodu klienta:  
  
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
>  Jeśli używasz Svcutil.exe ponownego generowania konfiguracji dla tego przykładu, należy zmodyfikować nazwę punktu końcowego w konfiguracji klienta, aby dopasować kod klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby kompilować rozwiązania w wersji języka C#, C++ lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
