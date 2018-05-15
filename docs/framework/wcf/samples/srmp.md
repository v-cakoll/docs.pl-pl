---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: c746897666ae78844df35c2989c803d852c3f70e
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="srmp"></a><span data-ttu-id="71190-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="71190-102">SRMP</span></span>
<span data-ttu-id="71190-103">W tym przykładzie pokazano, jak wykonać transakcyjnych w kolejce komunikacji przy użyciu usługi kolejkowania komunikatów (MSMQ) za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="71190-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="71190-104">W kolejce komunikacji klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="71190-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="71190-105">Mówiąc ściślej klient wysyła wiadomości do kolejki.</span><span class="sxs-lookup"><span data-stu-id="71190-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="71190-106">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="71190-106">The service receives messages from the queue.</span></span> <span data-ttu-id="71190-107">Usługi i klienta w związku z tym ma być uruchomiona, w tym samym czasie do komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="71190-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="71190-108">Usługa MSMQ umożliwia korzystanie z protokołu HTTP (łącznie z użyciem protokołu HTTPS) do wysyłania wiadomości do kolejki.</span><span class="sxs-lookup"><span data-stu-id="71190-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="71190-109">W tym przykładzie mamy pokazują, że za pomocą usługi Windows Communication Foundation (WCF) w kolejce komunikacji i jak należy wysyłać komunikaty za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="71190-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="71190-110">Usługa MSMQ używa protokołu o nazwie SRMP, czyli opartego na protokole SOAP protokołu komunikacji za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="71190-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="71190-111">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="71190-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="71190-112">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="71190-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="71190-113">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="71190-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="71190-114">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="71190-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="71190-115">Przed uruchomieniem próbki w **Dodaj/Usuń składniki systemu Windows**, upewnij się, że usługa MSMQ jest zainstalowana z obsługą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="71190-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="71190-116">Instalowanie obsługi protokołu HTTP automatycznie instaluje usługi Internet Information Services (IIS) i dodaje obsługę protokołu w usługach IIS dla usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="71190-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5.  <span data-ttu-id="71190-117">Jeśli chcesz mieć pewność, że używany do komunikacji HTTP, można włączyć usługi MSMQ do pracy w trybie zaostrzonym.</span><span class="sxs-lookup"><span data-stu-id="71190-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="71190-118">Dzięki temu, że żadnych komunikatów do kolejkach obsługiwanych na maszynie można dostarczone przy użyciu dowolnego innego niż HTTP transportu.</span><span class="sxs-lookup"><span data-stu-id="71190-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6.  <span data-ttu-id="71190-119">Po wybraniu usługi MSMQ do pracy w trybie zaostrzonym komputer wymaga ponownego rozruchu na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="71190-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
7.  <span data-ttu-id="71190-120">Uruchom usługę.</span><span class="sxs-lookup"><span data-stu-id="71190-120">Run the service.</span></span>  
  
8.  <span data-ttu-id="71190-121">Uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="71190-121">Run the client.</span></span> <span data-ttu-id="71190-122">Upewnij się, musisz zmienić adres punktu końcowego, aby wskazywała nazwę komputera lub adresu IP, a localhost.</span><span class="sxs-lookup"><span data-stu-id="71190-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="71190-123">Klient wysyła komunikat i kończy działanie.</span><span class="sxs-lookup"><span data-stu-id="71190-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71190-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="71190-124">Requirements</span></span>  
 <span data-ttu-id="71190-125">Aby uruchomić ten przykład, usługi IIS musi być zainstalowany na usługi i komputerów klienckich, oprócz usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="71190-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="71190-126">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="71190-126">Demonstrates</span></span>  
 <span data-ttu-id="71190-127">W przykładzie pokazano, wysyłanie WCF za pośrednictwem protokołu HTTP przy użyciu usługi MSMQ wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="71190-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="71190-128">Jest to tak zwane SRMP wiadomości.</span><span class="sxs-lookup"><span data-stu-id="71190-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="71190-129">Kiedy wiadomość w kolejce jest wysyłane, usługi MSMQ na wysyłanie przeniesień maszyny komunikaty odbierającego menedżera kolejek przy użyciu transportu TCP lub HTTP.</span><span class="sxs-lookup"><span data-stu-id="71190-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="71190-130">Wybierając SRMP użytkownik wskazuje wybór HTTP jako transportu do przeniesienia kolejki.</span><span class="sxs-lookup"><span data-stu-id="71190-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="71190-131">Zabezpieczanie SRMP umożliwia korzystanie z protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="71190-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71190-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="71190-132">Example</span></span>  
 <span data-ttu-id="71190-133">Przykładowy kod jest oparta na przykład transakcyjne.</span><span class="sxs-lookup"><span data-stu-id="71190-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="71190-134">Jak wysłać wiadomości do kolejki i odbierania wiadomości z kolejki przy użyciu SRMP jest taka sama jak wysyłanie i odbieranie komunikatów za pomocą natywnego protokołu.</span><span class="sxs-lookup"><span data-stu-id="71190-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="71190-135">Aby wskazać wybór protokół transferu kolejki jest zmieniła się konfiguracja klienta.</span><span class="sxs-lookup"><span data-stu-id="71190-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="71190-136">Protokół transferu kolejki może być jedną z macierzystego, SRMP lub SrmpSecure.</span><span class="sxs-lookup"><span data-stu-id="71190-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="71190-137">Domyślnie protokół transferu ma wartość Native.</span><span class="sxs-lookup"><span data-stu-id="71190-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="71190-138">Klient i usługa określ w konfiguracji, aby użyć SRMP w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="71190-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="71190-139">Istnieją pewne ograniczenia SRMP w odniesieniu do zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="71190-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="71190-140">Domyślne zabezpieczenia transportu usługi MSMQ wymaga usługi Active Directory wymaga, aby wysyłania menedżera kolejek i odbierającego menedżera kolejek znajdują się w tej samej domenie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="71190-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="71190-141">Nie jest możliwe podczas wysyłania wiadomości za pośrednictwem protokołu HTTP granic.</span><span class="sxs-lookup"><span data-stu-id="71190-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="71190-142">W efekcie domyślne zabezpieczenia transportu nie działa.</span><span class="sxs-lookup"><span data-stu-id="71190-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="71190-143">Zabezpieczenia transportu musi mieć ustawioną certyfikatu, jeśli wymagane jest zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="71190-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="71190-144">Zabezpieczenia komunikatów mogą służyć do zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="71190-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="71190-145">W tym przykładzie zabezpieczenia transportowe i wiadomość jest wyłączone w celu zilustrowania SRMP wiadomości.</span><span class="sxs-lookup"><span data-stu-id="71190-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
           address=  
          "net.msmq://localhost/private/ServiceModelSamplesSrmp"   
           bindingConfiguration="srmpBinding"   
           binding="netMsmqBinding"   
           contract="IOrderProcessor" />  
    </client>  
    <bindings>  
      <netMsmqBinding>  
        <binding name="srmpBinding"  
                 queueTransferProtocol="Srmp">  
          <security mode="None"></security>  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="71190-146">Uruchamianie przykładowej daje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="71190-146">Running the sample yields the following output.</span></span>  
  
```  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4   
Customer: somecustomer.com   
OrderDetails   
    Order LineItem: 54 of Blue Widget @unit price: $29.99   
    Order LineItem: 890 of Red Widget @unit price: $45.89   
    Total cost of this order: $42461.56   
    Order status: Pending  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="71190-147">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="71190-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="71190-148">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="71190-148">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="71190-149">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="71190-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="71190-150">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="71190-150">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
  
## <a name="see-also"></a><span data-ttu-id="71190-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71190-151">See Also</span></span>
