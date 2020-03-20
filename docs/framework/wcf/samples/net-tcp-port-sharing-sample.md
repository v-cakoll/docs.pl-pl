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
# <a name="nettcp-port-sharing-sample"></a><span data-ttu-id="dc047-102">Przykład współużytkowania portów Net.TCP</span><span class="sxs-lookup"><span data-stu-id="dc047-102">Net.TCP Port Sharing Sample</span></span>
<span data-ttu-id="dc047-103">Protokół TCP/IP używa numeru 16-bitowego, zwanego portem, do rozróżniania połączeń z wieloma aplikacjami sieciowymi działającymi na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="dc047-103">The TCP/IP protocol uses a 16-bit number, called a port, to differentiate connections to multiple network applications running on the same machine.</span></span> <span data-ttu-id="dc047-104">Jeśli aplikacja nasłuchuje na porcie, cały ruch TCP dla tego portu przechodzi do tej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc047-104">If an application is listening on a port, then all TCP traffic for that port goes to that application.</span></span> <span data-ttu-id="dc047-105">Inne aplikacje nie mogą nasłuchiwają na tym porcie w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="dc047-105">Other applications cannot listen on that port at the same time.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dc047-106">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="dc047-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dc047-107">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="dc047-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="dc047-108">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="dc047-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dc047-109">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="dc047-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 <span data-ttu-id="dc047-110">Wiele protokołów ma standardowy lub domyślny numer portu, którego używają.</span><span class="sxs-lookup"><span data-stu-id="dc047-110">Many protocols have a standard or default port number that they use.</span></span> <span data-ttu-id="dc047-111">Na przykład protokół HTTP zazwyczaj używa portu TCP 80.</span><span class="sxs-lookup"><span data-stu-id="dc047-111">For example, the HTTP protocol typically uses TCP port 80.</span></span> <span data-ttu-id="dc047-112">Internetowe usługi informacyjne (IIS) mają odbiornik do udostępniania portu między wieloma aplikacjami HTTP.</span><span class="sxs-lookup"><span data-stu-id="dc047-112">Internet Information Services (IIS) has a listener to share a port between multiple HTTP applications.</span></span> <span data-ttu-id="dc047-113">Usługi IIS nasłuchują bezpośrednio na porcie i przesyłają dalej wiadomości do odpowiedniej aplikacji na podstawie informacji wewnątrz strumienia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="dc047-113">IIS listens on the port directly and forwards messages to the appropriate application based on information inside the message stream.</span></span> <span data-ttu-id="dc047-114">Dzięki temu wiele aplikacji HTTP używać tego samego numeru portu bez konieczności konkurowania, aby zarezerwować port do odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dc047-114">This allows multiple HTTP applications to use the same port number without having to compete to reserve the port for receiving messages.</span></span>  
  
 <span data-ttu-id="dc047-115">Udostępnianie portów NetTcp to funkcja Programu Windows Communication Foundation (WCF), która podobnie umożliwia wielu aplikacjom sieciowym współużytkowanie jednego portu.</span><span class="sxs-lookup"><span data-stu-id="dc047-115">NetTcp Port Sharing is a Windows Communication Foundation (WCF)feature that similarly allows multiple network applications to share a single port.</span></span> <span data-ttu-id="dc047-116">Usługa udostępniania portów NetTcp akceptuje połączenia przy użyciu protokołu net.tcp i przesyła dalej wiadomości na podstawie ich adresu docelowego.</span><span class="sxs-lookup"><span data-stu-id="dc047-116">The NetTcp Port Sharing Service accepts connections using the net.tcp protocol and forwards messages based on their destination address.</span></span>  
  
 <span data-ttu-id="dc047-117">Usługa udostępniania portów NetTcp nie jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="dc047-117">The NetTcp Port Sharing Service is not enabled by default.</span></span> <span data-ttu-id="dc047-118">Przed uruchomieniem tego przykładu należy ręcznie włączyć usługę.</span><span class="sxs-lookup"><span data-stu-id="dc047-118">Before running this sample, you must manually enable the service.</span></span> <span data-ttu-id="dc047-119">Aby uzyskać więcej informacji, zobacz [Jak: Włączanie usługi udostępniania portów Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="dc047-119">For more information, see [How to: Enable the Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span></span> <span data-ttu-id="dc047-120">Jeśli usługa jest wyłączona, wyjątek jest zgłaszany po uruchomieniu aplikacji serwera.</span><span class="sxs-lookup"><span data-stu-id="dc047-120">If the service is disabled, an exception is thrown when the server application is started.</span></span>  
  
```console
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 <span data-ttu-id="dc047-121">Udostępnianie portu jest włączone na serwerze przez <xref:System.ServiceModel.NetTcpBinding> ustawienie <xref:System.ServiceModel.Channels.TcpTransportBindingElement> <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> właściwości powiązania lub elementu wiązania.</span><span class="sxs-lookup"><span data-stu-id="dc047-121">Port sharing is enabled on the server by setting the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property of the <xref:System.ServiceModel.NetTcpBinding> binding or the <xref:System.ServiceModel.Channels.TcpTransportBindingElement> binding element.</span></span> <span data-ttu-id="dc047-122">Klient nie musi wiedzieć, jak udostępnianie portów zostało skonfigurowane do używania go na serwerze.</span><span class="sxs-lookup"><span data-stu-id="dc047-122">The client does not have to know how port sharing has been configured to use it on the server.</span></span>  
  
## <a name="enabling-port-sharing"></a><span data-ttu-id="dc047-123">Włączanie udostępniania portów</span><span class="sxs-lookup"><span data-stu-id="dc047-123">Enabling Port Sharing</span></span>  
 <span data-ttu-id="dc047-124">Poniższy kod demonstruje włączanie udostępniania portów na serwerze.</span><span class="sxs-lookup"><span data-stu-id="dc047-124">The following code demonstrates enabling port sharing on the server.</span></span> <span data-ttu-id="dc047-125">Uruchamia wystąpienie `ICalculator` usługi na stałym porcie z losową ścieżką URI.</span><span class="sxs-lookup"><span data-stu-id="dc047-125">It starts an instance of the `ICalculator` service on a fixed port with a random URI path.</span></span> <span data-ttu-id="dc047-126">Mimo że dwie usługi mogą współużytkować ten sam port, ich ogólne adresy punktów końcowych nadal muszą być unikatowe, aby usługa udostępniania portów NetTcp mogła kierować wiadomości do poprawnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc047-126">Even though two services can share the same port, their overall endpoint addresses still must be unique so that the NetTcp Port Sharing Service can route messages to the correct application.</span></span>  

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

 <span data-ttu-id="dc047-127">Po włączeniu udostępniania portów można uruchomić usługę wiele razy bez konfliktu o numer portu.</span><span class="sxs-lookup"><span data-stu-id="dc047-127">With port sharing enabled, you can run the service multiple times without having a conflict over the port number.</span></span> <span data-ttu-id="dc047-128">Jeśli zmienisz kod, aby wyłączyć udostępnianie portów, uruchomienie dwóch kopii usługi <xref:System.ServiceModel.AddressAlreadyInUseException>spowoduje niepowodzenie drugiej z .</span><span class="sxs-lookup"><span data-stu-id="dc047-128">If you change the code to disable port sharing, starting up two copies of the service results in the second failing with an <xref:System.ServiceModel.AddressAlreadyInUseException>.</span></span>  
  
```console  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="dc047-129">Uruchamianie próbki</span><span class="sxs-lookup"><span data-stu-id="dc047-129">Running the Sample</span></span>  
 <span data-ttu-id="dc047-130">Za pomocą klienta testowego można sprawdzić, czy wiadomości są poprawnie kierowane do usług współużytkowania portu.</span><span class="sxs-lookup"><span data-stu-id="dc047-130">You can use the test client to check that messages are correctly routed to services sharing the port.</span></span>  

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

 <span data-ttu-id="dc047-131">Każde wystąpienie usługi wypisuje jego unikatowy numer i adres.</span><span class="sxs-lookup"><span data-stu-id="dc047-131">Each instance of the service prints out its unique number and address.</span></span> <span data-ttu-id="dc047-132">Na przykład po uruchomieniu pliku service.exe może zostać wyświetlony następujący tekst.</span><span class="sxs-lookup"><span data-stu-id="dc047-132">For instance, you may see the following text when you run service.exe.</span></span>  
  
```console  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="dc047-133">Wprowadź numer usługi widoczny w tym miejscu podczas uruchamiania pliku client.exe.</span><span class="sxs-lookup"><span data-stu-id="dc047-133">Enter the service number you see here when you run client.exe.</span></span>  
  
```console  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="dc047-134">Ten przykład można uruchomić w konfiguracji między komputerami, zmieniając wygenerowany adres, którego używa klient.</span><span class="sxs-lookup"><span data-stu-id="dc047-134">This sample can be run in a cross-machine configuration by changing the generated address that the client uses.</span></span> <span data-ttu-id="dc047-135">W Client.cs zmień ciąg formatu adresu punktu końcowego, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="dc047-135">In the Client.cs, change the endpoint address format string to match the new address of your service.</span></span> <span data-ttu-id="dc047-136">Zastąp wszelkie odwołania do "localhost" adresem IP komputera serwerowego.</span><span class="sxs-lookup"><span data-stu-id="dc047-136">Replace any references to "localhost" with the IP address of the server machine.</span></span> <span data-ttu-id="dc047-137">Należy ponownie skompiltować próbkę po dokonaniu tej zmiany.</span><span class="sxs-lookup"><span data-stu-id="dc047-137">You must recompile the sample after making this change.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dc047-138">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="dc047-138">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="dc047-139">Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="dc047-139">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="dc047-140">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dc047-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="dc047-141">Włącz usługę udostępniania portów NetTcp, jak opisano wcześniej w sekcji wprowadzającej.</span><span class="sxs-lookup"><span data-stu-id="dc047-141">Enable the NetTcp Port Sharing Service as previously described in the introduction section.</span></span>  
  
4. <span data-ttu-id="dc047-142">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dc047-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="dc047-143">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dc047-143">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="dc047-144">Szczegółowe informacje dotyczące uruchamiania tego przykładu są zawarte wcześniej w sekcji Uruchamianie przykładu.</span><span class="sxs-lookup"><span data-stu-id="dc047-144">Specific details for running this sample are included previously in the Running the Sample section.</span></span>  
