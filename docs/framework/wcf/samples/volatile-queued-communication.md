---
title: Komunikacja za pomocą nietrwałych kolejek
ms.date: 03/30/2017
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
ms.openlocfilehash: 4a3c67de2966bb9b7379a191039f6405b4007c78
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424678"
---
# <a name="volatile-queued-communication"></a><span data-ttu-id="496a8-102">Komunikacja za pomocą nietrwałych kolejek</span><span class="sxs-lookup"><span data-stu-id="496a8-102">Volatile Queued Communication</span></span>

<span data-ttu-id="496a8-103">W tym przykładzie pokazano, jak wykonać nietrwałą komunikację w kolejce za pośrednictwem transportu kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="496a8-103">This sample demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="496a8-104">Ten przykład używa <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="496a8-104">This sample uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="496a8-105">Usługa w tym przypadku jest samoobsługową aplikacją konsolową, która umożliwia obserwowanie usługi do odebrania komunikatów znajdujących się w kolejce.</span><span class="sxs-lookup"><span data-stu-id="496a8-105">The service in this case is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="496a8-106">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="496a8-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="496a8-107">W kolejce komunikacja klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="496a8-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="496a8-108">Dokładniej, klient wysyła komunikaty do kolejki.</span><span class="sxs-lookup"><span data-stu-id="496a8-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="496a8-109">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="496a8-109">The service receives messages from the queue.</span></span> <span data-ttu-id="496a8-110">W związku z tym usługa i klient nie muszą być uruchomione w tym samym czasie w celu komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="496a8-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="496a8-111">W przypadku wysłania wiadomości bez żadnych gwarancji usługa MSMQ najlepiej sprawdza się tylko w celu dostarczenia komunikatu, w przeciwieństwie do tego, że jest to możliwe tylko wtedy, gdy usługa MSMQ zagwarantuje, że wiadomość zostanie dostarczona lub, jeśli nie zostanie dostarczona, informuje o tym, że nie można dostarczyć wiadomości.</span><span class="sxs-lookup"><span data-stu-id="496a8-111">When you send a message with no assurances, MSMQ only makes a best effort to deliver the message, unlike with Exactly Once assurances where MSMQ ensures that the message gets delivered or, if it cannot be delivered, lets you know that the message cannot be delivered.</span></span>

<span data-ttu-id="496a8-112">W niektórych scenariuszach możesz chcieć wysłać nietrwały komunikat bez gwarancji dla kolejki, gdy czas dostarczania jest ważniejszy niż utrata komunikatów.</span><span class="sxs-lookup"><span data-stu-id="496a8-112">In certain scenarios, you may want to send a volatile message with no assurances over a queue, when timely delivery is more important than losing messages.</span></span> <span data-ttu-id="496a8-113">Komunikaty nietrwałe nie przeżyły do awarii Menedżera kolejki.</span><span class="sxs-lookup"><span data-stu-id="496a8-113">Volatile messages do not survive queue manager crashes.</span></span> <span data-ttu-id="496a8-114">W związku z tym w przypadku awarii Menedżera kolejki nietransakcyjnej kolejki używanej do przechowywania nietransakcyjnych komunikatów, ale same wiadomości nie są przechowywane na dysku.</span><span class="sxs-lookup"><span data-stu-id="496a8-114">Therefore if the queue manager crashes, the non-transactional queue used to store volatile messages survives but the messages themselves do not because the messages are not stored on the disk.</span></span>

> [!NOTE]
> <span data-ttu-id="496a8-115">Nie można wysyłać nietrwałych komunikatów bez gwarancji w zakresie transakcji przy użyciu usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="496a8-115">You cannot send volatile messages with no assurances within the scope of a transaction using MSMQ.</span></span> <span data-ttu-id="496a8-116">Należy również utworzyć kolejkę nietransakcyjną do wysyłania komunikatów nietransakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="496a8-116">You also must create a non-transactional queue to send volatile messages.</span></span>

<span data-ttu-id="496a8-117">Kontrakt usługi w tym przykładzie jest `IStockTicker`, który definiuje jednokierunkowe usługi, które najlepiej pasują do użycia z kolejkami.</span><span class="sxs-lookup"><span data-stu-id="496a8-117">The service contract in this sample is `IStockTicker` that defines one-way services that are best suited for use with queuing.</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void StockTick(string symbol, float price);
}
```

<span data-ttu-id="496a8-118">Operacja usługi wyświetla symbol i cenę znacznika giełdowego, jak pokazano w poniższym przykładowym kodzie:</span><span class="sxs-lookup"><span data-stu-id="496a8-118">The service operation displays the stock ticker symbol and price, as shown in the following sample code:</span></span>

```csharp
public class StockTickerService : IStockTicker
{
    public void StockTick(string symbol, float price)
    {
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);
     }
     …
}
```

<span data-ttu-id="496a8-119">Usługa jest samodzielna.</span><span class="sxs-lookup"><span data-stu-id="496a8-119">The service is self hosted.</span></span> <span data-ttu-id="496a8-120">W przypadku korzystania z transportu usługi MSMQ użyta Kolejka musi zostać utworzona z góry.</span><span class="sxs-lookup"><span data-stu-id="496a8-120">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="496a8-121">Można to zrobić ręcznie lub przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="496a8-121">This can be done manually or through code.</span></span> <span data-ttu-id="496a8-122">W tym przykładzie usługa zawiera kod, aby sprawdzić istnienie kolejki i utworzyć ją, jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="496a8-122">In this sample, the service contains code to check for the existence of the queue and create it if required.</span></span> <span data-ttu-id="496a8-123">Nazwa kolejki jest odczytywana z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="496a8-123">The queue name is read from the configuration file.</span></span> <span data-ttu-id="496a8-124">Adres podstawowy jest używany przez narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wygenerowania serwera proxy dla usługi.</span><span class="sxs-lookup"><span data-stu-id="496a8-124">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy for the service.</span></span>

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get MSMQ queue name from app settings in configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];

    // Create the transacted MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName);

    // Create a ServiceHost for the StockTickerService type.
    using (ServiceHost serviceHost = new ServiceHost(typeof(StockTickerService)))
    {
        // Open the ServiceHost to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHost to shutdown the service.
        serviceHost.Close();
    }
}
```

<span data-ttu-id="496a8-125">Nazwa kolejki MSMQ jest określona w sekcji appSettings w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="496a8-125">The MSMQ queue name is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="496a8-126">Punkt końcowy usługi jest zdefiniowany w sekcji System. serviceModel w pliku konfiguracji i określa powiązanie `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="496a8-126">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>

> [!NOTE]
> <span data-ttu-id="496a8-127">Nazwa kolejki używa kropki (.) dla komputera lokalnego i separatorów ukośników odwrotnych w ścieżce podczas tworzenia kolejki przy użyciu <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="496a8-127">The queue name uses a dot (.) for the local machine and backslash separators in its path when creating a queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="496a8-128">Adres punktu końcowego Windows Communication Foundation (WCF) określa schemat net. MSMQ:, używa "localhost" dla komputera lokalnego i ukośników w swojej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="496a8-128">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine and forward slashes in its path.</span></span>

<span data-ttu-id="496a8-129">Gwarancje i trwałość lub lotność komunikatów są również określone w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="496a8-129">The assurances and durability or volatility of messages are also specified in the configuration.</span></span>

```xml
<appSettings>
  <!-- use appSetting to configure MSMQ queue name -->
  <add key="queueName" value=".\private$\ServiceModelSamplesVolatile" />
</appSettings>

<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.StockTickerService"
             behaviorConfiguration="CalculatorServiceBehavior">
    ...
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                binding="netMsmqBinding"
                bindingConfiguration="volatileBinding"
                contract="Microsoft.ServiceModel.Samples.IStockTicker" />
    ...
    </service>
  </services>

  <bindings>
    <netMsmqBinding>
      <binding name="volatileBinding"
             durable="false"
           exactlyOnce="false"/>
    </netMsmqBinding>
  </bindings>
  ...
</system.serviceModel>
```

<span data-ttu-id="496a8-130">Ponieważ przykład wysyła wiadomości w kolejce przy użyciu kolejki nietransakcyjnej, wiadomości transakcyjne nie mogą być wysyłane do kolejki.</span><span class="sxs-lookup"><span data-stu-id="496a8-130">Because the sample sends queued messages by using a non-transactional queue, transacted messages cannot be sent to the queue.</span></span>

```csharp
// Create a client.
Random r = new Random(137);

StockTickerClient client = new StockTickerClient();

float price = 43.23F;
for (int i = 0; i < 10; i++)
{
    float increment = 0.01f * (r.Next(10));
    client.StockTick("zzz" + i, price + increment);
}

//Closing the client gracefully cleans up resources.
client.Close();
```

<span data-ttu-id="496a8-131">Po uruchomieniu przykładu działania klienta i usługi są wyświetlane zarówno w systemie, jak i w oknach konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="496a8-131">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="496a8-132">Możesz zobaczyć, że usługa odbiera komunikaty od klienta.</span><span class="sxs-lookup"><span data-stu-id="496a8-132">You can see the service receive messages from the client.</span></span> <span data-ttu-id="496a8-133">Naciśnij klawisz ENTER w każdym oknie konsoli, aby zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="496a8-133">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="496a8-134">Należy pamiętać, że ponieważ usługa kolejkowania jest w użyciu, klient i usługi nie muszą działać w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="496a8-134">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="496a8-135">Można uruchomić klienta programu, zamknąć go, a następnie uruchomić usługę i nadal otrzymywać wiadomości.</span><span class="sxs-lookup"><span data-stu-id="496a8-135">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Stock Tick zzz0:43.25
Stock Tick zzz1:43.23
Stock Tick zzz2:43.28
Stock Tick zzz3:43.3
Stock Tick zzz4:43.23
Stock Tick zzz5:43.25
Stock Tick zzz6:43.25
Stock Tick zzz7:43.24
Stock Tick zzz8:43.32
Stock Tick zzz9:43.3
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="496a8-136">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="496a8-136">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="496a8-137">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="496a8-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="496a8-138">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="496a8-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="496a8-139">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="496a8-139">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

<span data-ttu-id="496a8-140">Domyślnie przy <xref:System.ServiceModel.NetMsmqBinding>włączono zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="496a8-140">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="496a8-141">Istnieją dwie odpowiednie właściwości zabezpieczeń transportu usługi MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` Domyślnie tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="496a8-141">There are two pertinent properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="496a8-142">Aby usługa MSMQ zapewniała funkcję uwierzytelniania i podpisywania, musi być częścią domeny, a dla usługi MSMQ należy zainstalować opcję Integracja z usługą Active Directory.</span><span class="sxs-lookup"><span data-stu-id="496a8-142">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="496a8-143">Jeśli ten przykład zostanie uruchomiony na komputerze, który nie spełnia tych kryteriów, wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="496a8-143">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="496a8-144">Aby uruchomić przykład na komputerze przyłączonym do grupy roboczej lub bez integracji z usługą Active Directory</span><span class="sxs-lookup"><span data-stu-id="496a8-144">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>

1. <span data-ttu-id="496a8-145">Jeśli komputer nie jest częścią domeny lub nie zainstalowano integracji z usługą Active Directory, Wyłącz zabezpieczenia transportu, ustawiając tryb uwierzytelniania i poziom ochrony na `None`, jak pokazano w poniższym przykładowym kodzie konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="496a8-145">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code:</span></span>

    ```xml
    <system.serviceModel>
        <services>
          <service name="Microsoft.ServiceModel.Samples.StockTickerService"
                   behaviorConfiguration="StockTickerServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>

            <!-- Define NetMsmqEndpoint -->
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                      binding="netMsmqBinding"
                      bindingConfiguration="volatileBinding"
                      contract="Microsoft.ServiceModel.Samples.IStockTicker" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />

          </service>
        </services>

        <bindings>
          <netMsmqBinding>
            <binding name="volatileBinding"
                  durable="false"
                  exactlyOnce="false">
              <security mode="None" />
            </binding>
          </netMsmqBinding>
        </bindings>

        <behaviors>
          <serviceBehaviors>
            <behavior name="StockTickerServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. <span data-ttu-id="496a8-146">Przed uruchomieniem przykładu należy zmienić konfigurację na serwerze i kliencie programu.</span><span class="sxs-lookup"><span data-stu-id="496a8-146">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="496a8-147">Ustawienie `security mode` `None` jest równoznaczne z ustawieniem <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>i `Message` zabezpieczenia `None`.</span><span class="sxs-lookup"><span data-stu-id="496a8-147">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="496a8-148">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="496a8-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="496a8-149">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="496a8-149">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="496a8-150">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="496a8-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="496a8-151">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="496a8-151">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`
