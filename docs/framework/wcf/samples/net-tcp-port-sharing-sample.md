---
title: Przykład współużytkowania portów Net.TCP
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: ac90a50c6fe06a643881da2889fdea308404508e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144295"
---
# <a name="nettcp-port-sharing-sample"></a>Przykład współużytkowania portów Net.TCP
Protokół TCP/IP używa numeru 16-bitowego, zwanego portem, do rozróżniania połączeń z wieloma aplikacjami sieciowymi działającymi na tym samym komputerze. Jeśli aplikacja nasłuchuje na porcie, cały ruch TCP dla tego portu przechodzi do tej aplikacji. Inne aplikacje nie mogą nasłuchiwają na tym porcie w tym samym czasie.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 Wiele protokołów ma standardowy lub domyślny numer portu, którego używają. Na przykład protokół HTTP zazwyczaj używa portu TCP 80. Internetowe usługi informacyjne (IIS) mają odbiornik do udostępniania portu między wieloma aplikacjami HTTP. Usługi IIS nasłuchują bezpośrednio na porcie i przesyłają dalej wiadomości do odpowiedniej aplikacji na podstawie informacji wewnątrz strumienia komunikatów. Dzięki temu wiele aplikacji HTTP używać tego samego numeru portu bez konieczności konkurowania, aby zarezerwować port do odbierania wiadomości.  
  
 Udostępnianie portów NetTcp to funkcja Programu Windows Communication Foundation (WCF), która podobnie umożliwia wielu aplikacjom sieciowym współużytkowanie jednego portu. Usługa udostępniania portów NetTcp akceptuje połączenia przy użyciu protokołu net.tcp i przesyła dalej wiadomości na podstawie ich adresu docelowego.  
  
 Usługa udostępniania portów NetTcp nie jest domyślnie włączona. Przed uruchomieniem tego przykładu należy ręcznie włączyć usługę. Aby uzyskać więcej informacji, zobacz [Jak: Włączanie usługi udostępniania portów Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md). Jeśli usługa jest wyłączona, wyjątek jest zgłaszany po uruchomieniu aplikacji serwera.  
  
```console
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 Udostępnianie portu jest włączone na serwerze przez <xref:System.ServiceModel.NetTcpBinding> ustawienie <xref:System.ServiceModel.Channels.TcpTransportBindingElement> <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> właściwości powiązania lub elementu wiązania. Klient nie musi wiedzieć, jak udostępnianie portów zostało skonfigurowane do używania go na serwerze.  
  
## <a name="enabling-port-sharing"></a>Włączanie udostępniania portów  
 Poniższy kod demonstruje włączanie udostępniania portów na serwerze. Uruchamia wystąpienie `ICalculator` usługi na stałym porcie z losową ścieżką URI. Mimo że dwie usługi mogą współużytkować ten sam port, ich ogólne adresy punktów końcowych nadal muszą być unikatowe, aby usługa udostępniania portów NetTcp mogła kierować wiadomości do poprawnej aplikacji.  

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

 Po włączeniu udostępniania portów można uruchomić usługę wiele razy bez konfliktu o numer portu. Jeśli zmienisz kod, aby wyłączyć udostępnianie portów, uruchomienie dwóch kopii usługi <xref:System.ServiceModel.AddressAlreadyInUseException>spowoduje niepowodzenie drugiej z .  
  
```console  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>Uruchamianie próbki  
 Za pomocą klienta testowego można sprawdzić, czy wiadomości są poprawnie kierowane do usług współużytkowania portu.  

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

 Każde wystąpienie usługi wypisuje jego unikatowy numer i adres. Na przykład po uruchomieniu pliku service.exe może zostać wyświetlony następujący tekst.  
  
```console  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 Wprowadź numer usługi widoczny w tym miejscu podczas uruchamiania pliku client.exe.  
  
```console  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Ten przykład można uruchomić w konfiguracji między komputerami, zmieniając wygenerowany adres, którego używa klient. W Client.cs zmień ciąg formatu adresu punktu końcowego, aby dopasować nowy adres usługi. Zastąp wszelkie odwołania do "localhost" adresem IP komputera serwerowego. Należy ponownie skompiltować próbkę po dokonaniu tej zmiany.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Włącz usługę udostępniania portów NetTcp, jak opisano wcześniej w sekcji wprowadzającej.  
  
4. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md). Szczegółowe informacje dotyczące uruchamiania tego przykładu są zawarte wcześniej w sekcji Uruchamianie przykładu.  
