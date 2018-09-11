---
title: Przykład współużytkowania portów Net.TCP
ms.date: 03/30/2017
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
ms.openlocfilehash: db4cd5be73e3c170f2feaa1e76f275eb7d9cd226
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44263878"
---
# <a name="nettcp-port-sharing-sample"></a>Przykład współużytkowania portów Net.TCP
Protokół TCP/IP używa 16-bitową liczbę o nazwie portu do rozróżniania połączeń z wieloma aplikacjami sieciowymi uruchomione na tym samym komputerze. Jeśli aplikacja nasłuchuje na porcie, cały ruch TCP dla tego portu przechodzi do tej aplikacji. Inne aplikacje nie może nasłuchiwać na tym porcie w tym samym czasie.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 Wiele protokołów mają standard lub domyślnego numeru portu, który używają. Na przykład protokołu HTTP zazwyczaj używa portu TCP 80. Internet Information Services (IIS) ma odbiornika do udostępniania portów między wieloma aplikacjami HTTP. Usługi IIS nasłuchuje na porcie bezpośrednio i przekazuje komunikaty do odpowiedniej aplikacji w oparciu o informacje wewnątrz strumienia komunikatów. Dzięki temu wiele aplikacji HTTP używać tego samego numeru portu bez konieczności konkurować zarezerwować portu do odbierania wiadomości.  
  
 Udostępnianie portów NetTcp jest funkcją Windows Communication Foundation (WCF), która podobnie umożliwia wielu aplikacjom sieci współużytkować jeden port. Usługi udostępniania portów NetTcp akceptuje połączenia przy użyciu protokołu net.tcp i przekazuje komunikaty na podstawie ich adresu docelowego.  
  
 Nie włączono usługi udostępniania portów NetTcp domyślnie. Przed uruchomieniem tego przykładu, należy ręcznie włączyć tę usługę. Aby uzyskać więcej informacji, zobacz [porady: Włączanie usługi udostępniania portów Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md). Jeśli usługa jest wyłączona, wyjątek jest generowany po uruchomieniu aplikacji serwera.  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 Udostępnianie portów jest włączona na serwerze <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> właściwość <xref:System.ServiceModel.NetTcpBinding> powiązania lub <xref:System.ServiceModel.Channels.TcpTransportBindingElement> element powiązania. Klient nie musi wiedzieć, jak udostępnianie portów został skonfigurowany z niego korzystać na serwerze.  
  
## <a name="enabling-port-sharing"></a>Włączenie udostępniania portów  
 Poniższy kod ilustruje włączanie udostępniania portów na serwerze. Uruchamia wystąpienie `ICalculator` usługi na stały port za pomocą losowych ścieżka identyfikatora URI. Mimo że dwie usługi mogą udostępniać tego samego portu, ich ogólną adresy punktów końcowych nadal muszą być unikatowe, aby usługi udostępniania portów NetTcp komunikaty można kierować do do właściwej aplikacji.  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address =  
   String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 Udostępnianie portów jest włączona, umożliwia uruchamianie usługi wiele razy bez konfliktu przez numer portu. Jeśli zmienisz kod, aby wyłączyć udostępnianie portów, uruchamianie dwie kopie wyników usługi w drugim zwracając <xref:System.ServiceModel.AddressAlreadyInUseException>.  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>Działa aplikacja przykładowa  
 Klient testowy służy do sprawdzenia, że komunikaty są poprawnie kierowane do usługi udostępniania portów.  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
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

 Każde wystąpienie usługi drukowania jego unikatowy numer i adres. Na przykład następujący tekst może zostać wyświetlony po uruchomieniu service.exe.  
  
```  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 Wprowadź numer usługi widocznej w tym miejscu po uruchomieniu client.exe.  
  
```  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 W tym przykładzie można uruchomić w konfiguracji między komputerami, zmieniając wygenerowany adres, używanego przez klienta. W Client.cs Zmień ciąg formatu adresu punktu końcowego do dopasowania nowy adres usługi. Zastąp wszystkie odwołania do "localhost" adres IP komputera serwera. Po wprowadzeniu tej zmiany, należy ponownie skompilować przykład.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Włącz NetTcp usługi udostępniania portów jak opisano wcześniej w sekcji wprowadzenie.  
  
4.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Szczegółowe informacje dotyczące uruchomieniem tego przykładu znajdują się wcześniej uruchomione sekcji przykład.  
  
## <a name="see-also"></a>Zobacz też
