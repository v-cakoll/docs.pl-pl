---
title: "Przykład współużytkowania portów Net.TCP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dea3a0f0d69662021c78b0f1d57ad0ba8c11fcb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="nettcp-port-sharing-sample"></a>Przykład współużytkowania portów Net.TCP
Protokół TCP/IP używa 16-bitową liczbę zwanej portem do rozróżniania połączeń z wieloma aplikacjami sieciowymi uruchomiona na tym samym komputerze. Jeśli aplikacja nasłuchuje na porcie, cały ruch TCP dla tego portu przechodzi do tej aplikacji. Inne aplikacje nie może nasłuchiwać na tym porcie w tym samym czasie.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 Wiele protokołów ma standard lub domyślny numer portu, które korzystają z. Na przykład protokołu HTTP zazwyczaj używa portu TCP 80. Internet Information Services (IIS) ma odbiornika Udostępnianie portów między wiele aplikacji HTTP. Usługi IIS nasłuchuje na porcie bezpośrednio i przekazuje dalej wiadomości do odpowiedniej aplikacji na podstawie informacji w strumieniu wiadomości. Dzięki temu wiele aplikacji HTTP użyć tego samego numeru portu bez konieczności konkurować zarezerwować portu do odbierania wiadomości.  
  
 Udostępnianie portów NetTcp jest [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]funkcja umożliwiająca podobnie wiele aplikacji sieci może współużytkować jeden port. Usługa udostępniania portów NetTcp akceptuje połączenia za pomocą protokołu net.tcp i przekazuje dalej wiadomości na podstawie ich adresu docelowego.  
  
 Nie włączono usługi udostępniania portów NetTcp domyślnie. Przed uruchomieniem tego przykładu, musisz ręcznie włączyć usługę. Aby uzyskać więcej informacji, zobacz [porady: Włączanie usługi udostępniania portów Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md). Jeśli usługa zostanie wyłączona, jest wyjątek po uruchomieniu aplikacji serwera.  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 Udostępnianie portów jest włączona na serwerze <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> właściwość <xref:System.ServiceModel.NetTcpBinding> powiązanie lub <xref:System.ServiceModel.Channels.TcpTransportBindingElement> elementu powiązania. Klient nie trzeba wiedzieć, jak udostępnianie portów został skonfigurowany do używania go na serwerze.  
  
## <a name="enabling-port-sharing"></a>Włączenie udostępniania portów  
 Poniższy kod ilustruje, włączanie Udostępnianie portów na serwerze. Rozpoczyna wystąpienia `ICalculator` usługi na stały port o losowy ścieżka identyfikatora URI. Mimo że dwie usługi mogą współużytkować tego samego portu, ich ogólną adresy punktów końcowych nadal musi być unikatowa, aby Usługa udostępniania portów NetTcp rozesłać komunikaty do odpowiedniej aplikacji.  
  
```  
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
  
 Udostępnianie portów jest włączona, umożliwia uruchamianie usługi wiele razy bez konfliktu przez numer portu. Jeśli zmienisz kod, aby wyłączyć udostępnianie portów uruchamiania dwie kopie wyników usługi w drugim Niepowodzenie z <xref:System.ServiceModel.AddressAlreadyInUseException>.  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a>Uruchomiona próbki  
 Klient testowy służy do sprawdzania, czy komunikaty są poprawnie kierowane do usługi udostępniania portów.  
  
```  
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
  
 Każde wystąpienie usługi drukowania jego unikatowy numer oraz adres. Na przykład może zostać wyświetlony następujący tekst po uruchomieniu service.exe.  
  
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
  
 W tym przykładzie można uruchomić w konfiguracji między komputerami, zmieniając wygenerowany adres używany przez klienta. W Client.cs Zmień ciąg formatu adresu punktu końcowego do dopasowania nowy adres z usługą. Zamień wszystkie odwołania do "localhost" adres IP serwera. Po wprowadzeniu tej zmiany, należy ponownie skompilować próbki.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Włącz NetTcp usługi udostępniania portów jak opisano wcześniej w sekcji wprowadzenie.  
  
4.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md). Szczegółowe informacje dotyczące uruchamiania tego przykładu znajdują się wcześniej w działaniu sekcji przykładowe.  
  
## <a name="see-also"></a>Zobacz też
