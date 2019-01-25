---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 2f42db91db4983c80ebb42168cf7bf1ddb3e5023
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649667"
---
# <a name="srmp"></a><span data-ttu-id="a6ed0-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="a6ed0-102">SRMP</span></span>
<span data-ttu-id="a6ed0-103">W tym przykładzie pokazano, jak wykonać transakcyjnych w kolejce komunikacji przy użyciu usługi kolejkowania komunikatów (MSMQ) za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="a6ed0-104">W komunikacie w kolejce klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="a6ed0-105">Mówiąc ściślej klient wysyła komunikaty do kolejki.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="a6ed0-106">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-106">The service receives messages from the queue.</span></span> <span data-ttu-id="a6ed0-107">Usługi i klienta w związku z tym, nie musi być uruchomiona w tym samym czasie do komunikowania się za pomocą kolejki.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="a6ed0-108">Usługi MSMQ umożliwia korzystanie z protokołu HTTP (w tym użycie protokołu HTTPS), aby wysyłać komunikaty do kolejki.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="a6ed0-109">W tym przykładzie firma Microsoft pokazują, czy przy użyciu usługi Windows Communication Foundation (WCF) w kolejce komunikacji oraz jak wysyłać komunikaty za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="a6ed0-110">Usługa MSMQ używa protokołu o nazwie SRMP, czyli opartego na protokole SOAP protokół komunikacji za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a6ed0-111">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="a6ed0-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a6ed0-112">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a6ed0-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a6ed0-113">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a6ed0-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a6ed0-114">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a6ed0-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="a6ed0-115">Przed uruchomieniem przykładu **Dodaj/Usuń składniki Windows**, upewnij się, że usługa MSMQ jest zainstalowana z obsługą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="a6ed0-116">Instalowanie obsługi HTTP automatycznie instaluje Internet Information Services (IIS) i dodaje obsługę protokołu w usługach IIS dla usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5.  <span data-ttu-id="a6ed0-117">Jeśli chcesz mieć pewność, że HTTP jest używany do komunikacji, można włączyć usługi MSMQ do pracy w trybie zaostrzonym.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="a6ed0-118">Daje to gwarancję, że żadnych komunikatów do kolejkach obsługiwanych na maszynie mogą pojawić się za pomocą transportu dowolnego innego niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6.  <span data-ttu-id="a6ed0-119">Po wybraniu usługi MSMQ do pracy w trybie zaostrzonym komputer wymaga ponownego rozruchu na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6ed0-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
7.  <span data-ttu-id="a6ed0-120">Uruchom usługę.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-120">Run the service.</span></span>  
  
8.  <span data-ttu-id="a6ed0-121">Uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-121">Run the client.</span></span> <span data-ttu-id="a6ed0-122">Upewnij się, że zmienisz adres punktu końcowego, aby wskazywał nazwę komputera lub adres IP zamiast nazwy localhost.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="a6ed0-123">Klient wysyła komunikat i kończy pracę.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6ed0-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6ed0-124">Requirements</span></span>  
 <span data-ttu-id="a6ed0-125">Aby uruchomić ten przykład, usługi IIS musi być zainstalowany zarówno usługi, jak i na komputerach klienckich, oprócz usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a6ed0-126">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="a6ed0-126">Demonstrates</span></span>  
 <span data-ttu-id="a6ed0-127">W przykładzie pokazano WCF wysyłanie wiadomości przy użyciu usługi MSMQ za pośrednictwem protokołu HTTP w kolejce.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="a6ed0-128">Jest to tak zwane SRMP komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="a6ed0-129">Gdy wiadomość w kolejce są wysyłane, usługi MSMQ na wysyłanie przeniesień maszyny komunikaty odbierający Menedżer kolejki przy użyciu transportu TCP lub HTTP.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="a6ed0-130">Wybierając SRMP, użytkownik wskazuje wybór HTTP jako transportu do kolejki transferu.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="a6ed0-131">Zabezpieczanie SRMP umożliwia korzystanie z protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6ed0-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="a6ed0-132">Example</span></span>  
 <span data-ttu-id="a6ed0-133">Przykładowy kod jest oparty na przykład transakcyjne.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="a6ed0-134">Jak wysyłać komunikat do kolejki i odebrania komunikatu z kolejki, używając SRMP jest taka sama jak wysyłanie i odbieranie wiadomości przy użyciu natywnego protokołu.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="a6ed0-135">Konfiguracja klienta jest zmieniany na wskazują wybór protokół transferu kolejki.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="a6ed0-136">Protokół transferu kolejki może być jednym z natywnych, SRMP lub SrmpSecure.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="a6ed0-137">Domyślnie protokół transferu jest Native.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="a6ed0-138">Klient i usługa określ w konfiguracji, aby użyć SRMP w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="a6ed0-139">Istnieją ograniczenia dotyczące SRMP w odniesieniu do zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="a6ed0-140">Zabezpieczenia transportu usługi MSMQ domyślne wymaga usługi Active Directory, która wymaga, że Menedżer kolejki wysyłania i odbierania menedżera kolejek znajdują się w tej samej domenie Windows.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="a6ed0-141">To nie jest możliwe podczas wysyłania komunikatów za pośrednictwem protokołu HTTP granic.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="a6ed0-142">W efekcie domyślnych zabezpieczeń transportu nie działa.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="a6ed0-143">Zabezpieczenia transportu musi być równa certyfikatu, jeśli pożądane jest zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="a6ed0-144">Zabezpieczenia komunikatów również może służyć do zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="a6ed0-145">W tym przykładzie zabezpieczeń transportu i komunikatów jest wyłączona do zilustrowania SRMP komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
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
          <security mode="None" />  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="a6ed0-146">Działa aplikacja przykładowa daje następujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-146">Running the sample yields the following output.</span></span>  
  
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
>  <span data-ttu-id="a6ed0-147">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a6ed0-148">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a6ed0-148">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a6ed0-149">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a6ed0-150">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a6ed0-150">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
  
## <a name="see-also"></a><span data-ttu-id="a6ed0-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6ed0-151">See also</span></span>
