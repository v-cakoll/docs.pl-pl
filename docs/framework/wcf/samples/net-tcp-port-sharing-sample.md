---
title: Przykład współużytkowania portów Net.TCP
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: 240579ef36405d730bb04ea171846c8e5ef9322e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73416760"
---
# <a name="nettcp-port-sharing-sample"></a>Przykład współużytkowania portów Net.TCP
Protokół TCP/IP używa liczby 16-bitowej zwanej portem do rozróżniania połączeń z wieloma aplikacjami sieciowymi uruchomionymi na tym samym komputerze. Jeśli aplikacja nasłuchuje na porcie, cały ruch TCP dla tego portu przechodzi do tej aplikacji. Inne aplikacje nie mogą nasłuchiwać tego portu w tym samym czasie.  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 Wiele protokołów ma standardowy lub domyślny numer portu, którego używają. Na przykład protokół HTTP zwykle używa portu TCP 80. Internet Information Services (IIS) ma odbiornik do udostępniania portu między wieloma aplikacjami HTTP. Usługi IIS nasłuchują na porcie bezpośrednio i przesyłają komunikaty do odpowiedniej aplikacji w oparciu o informacje znajdujące się w strumieniu wiadomości. Pozwala to wielu aplikacjom HTTP korzystać z tego samego numeru portu bez konieczności konkurowania, aby zarezerwować port do odbioru wiadomości.  
  
 Udostępnianie portów NetTcp to funkcja programu Windows Communication Foundation (WCF), która w podobny sposób pozwala wielu aplikacjom sieciowym współużytkować jeden port. Usługa udostępniania portów NetTcp akceptuje połączenia za pomocą protokołu net. TCP i przekazuje komunikaty na podstawie ich adresu docelowego.  
  
 Usługa udostępniania portów NetTcp nie jest domyślnie włączona. Przed uruchomieniem tego przykładu należy ręcznie włączyć usługę. Aby uzyskać więcej informacji, zobacz [jak: Włączanie usługi udostępniania portów Net. TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md). Jeśli usługa jest wyłączona, podczas uruchamiania aplikacji serwera zostanie zgłoszony wyjątek.  
  
```console
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 Udostępnianie portów jest włączone na serwerze przez ustawienie właściwości <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> powiązania <xref:System.ServiceModel.NetTcpBinding> lub elementu powiązania <xref:System.ServiceModel.Channels.TcpTransportBindingElement>. Klient nie musi wiedzieć, jak Udostępnianie portów zostało skonfigurowane do korzystania z niego na serwerze.  
  
## <a name="enabling-port-sharing"></a>Włączanie udostępniania portów  
 Poniższy kod demonstruje włączenie udostępniania portów na serwerze. Uruchamia wystąpienie usługi `ICalculator` na stałym porcie ze losową ścieżką URI. Mimo że dwie usługi mogą współużytkować ten sam port, ich ogólne adresy punktów końcowych nadal muszą być unikatowe, aby usługa udostępniania portów NetTcp mogła kierować komunikaty do odpowiedniej aplikacji.  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address = $"net.tcp://localhost:9000/calculator/{salt}";
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 Włączenie udostępniania portów umożliwia uruchomienie usługi wiele razy bez konfliktu przez numer portu. Jeśli zmienisz kod w celu wyłączenia udostępniania portów, uruchomienie dwóch kopii usługi powoduje, że w drugim kończy się niepowodzeniem z <xref:System.ServiceModel.AddressAlreadyInUseException>.  
  
```console  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>Uruchamianie przykładu  
 Możesz użyć klienta testowego, aby sprawdzić, czy komunikaty są prawidłowo kierowane do usług udostępniających port.  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = $"net.tcp://localhost:9000/calculator/{salt}";
      ChannelFactory<ICalculator> factory = new ChannelFactory<ICalculator>(new NetTcpBinding());  
      ICalculator proxy = factory.CreateChannel(new EndpointAddress(address));  
  
      // Call the Add service operation.  
      double value1 = 100.00D;  
      double value2 = 15.99D;  
      double result = proxy.Add(value1, value2);  
      Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Subtract service operation.  
      value1 = 145.00D;  
      value2 = 76.54D;  
      result = proxy.Subtract(value1, value2);  
      Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Multiply service operation.  
      value1 = 9.00D;  
      value2 = 81.25D;  
      result = proxy.Multiply(value1, value2);  
      Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Divide service operation.  
      value1 = 22.00D;  
      value2 = 7.00D;  
      result = proxy.Divide(value1, value2);  
      Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
      Console.WriteLine();  
      Console.WriteLine("Press <ENTER> to terminate client.");  
      Console.ReadLine();  
  
      factory.Close();  
   }  
}  
```

 Każde wystąpienie usługi drukuje swój unikatowy numer i adres. Na przykład po uruchomieniu programu Service. exe może zostać wyświetlony następujący tekst.  
  
```console  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 Wprowadź numer usługi widoczny w tym miejscu podczas uruchamiania programu Client. exe.  
  
```console  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Ten przykład można uruchomić w konfiguracji między maszynami, zmieniając wygenerowany adres wykorzystywany przez klienta. W Client.cs Zmień ciąg formatu adresu punktu końcowego, aby odpowiadał nowemu adresowi usługi. Zastąp wszystkie odwołania do "localhost" adresem IP komputera serwera. Po wprowadzeniu tej zmiany należy ponownie skompilować przykład.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Włącz usługę udostępniania portów NetTcp, jak opisano wcześniej w sekcji wprowadzenie.  
  
4. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Szczegółowe informacje na temat uruchamiania tego przykładu są zawarte wcześniej w sekcji Uruchamianie przykładu.  
