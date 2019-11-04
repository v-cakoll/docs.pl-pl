---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 51b0e0513ba20bf7aeae461dee6ac864f1d55897
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417096"
---
# <a name="srmp"></a><span data-ttu-id="8083f-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="8083f-102">SRMP</span></span>
<span data-ttu-id="8083f-103">Ten przykład pokazuje, jak przeprowadzić komunikację z kolejką w kolejce przy użyciu usługi kolejkowania komunikatów (MSMQ) za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8083f-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="8083f-104">W kolejce komunikacja klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="8083f-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="8083f-105">Dokładniej, klient wysyła komunikaty do kolejki.</span><span class="sxs-lookup"><span data-stu-id="8083f-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="8083f-106">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="8083f-106">The service receives messages from the queue.</span></span> <span data-ttu-id="8083f-107">W związku z tym usługa i klient nie muszą być uruchomione w tym samym czasie w celu komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="8083f-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="8083f-108">Usługa MSMQ umożliwia wysyłanie komunikatów do kolejki przy użyciu protokołu HTTP (łącznie z użyciem protokołu HTTPS).</span><span class="sxs-lookup"><span data-stu-id="8083f-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="8083f-109">W tym przykładzie pokazano, jak używać funkcji komunikacji z kolejką Windows Communication Foundation (WCF) oraz jak wysyłać komunikaty za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8083f-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="8083f-110">Usługa MSMQ korzysta z protokołu o nazwie SRMP, czyli protokołu opartego na protokole SOAP do komunikacji za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8083f-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8083f-111">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="8083f-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8083f-112">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8083f-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8083f-113">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8083f-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8083f-114">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8083f-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="8083f-115">Przed uruchomieniem przykładu w obszarze **Dodawanie/usuwanie składników systemu Windows**upewnij się, że usługa MSMQ jest zainstalowana z obsługą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8083f-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="8083f-116">Zainstalowanie obsługi protokołu HTTP powoduje automatyczne zainstalowanie Internet Information Services (IIS) i dodanie obsługi protokołu w usługach IIS dla usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="8083f-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5. <span data-ttu-id="8083f-117">Jeśli chcesz mieć pewność, że protokół HTTP jest używany do komunikacji, możesz włączyć usługę MSMQ do działania w trybie zaostrzonym.</span><span class="sxs-lookup"><span data-stu-id="8083f-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="8083f-118">Pozwala to zagwarantować, że żadne komunikaty do żadnej kolejki hostowanej na komputerze nie mogą zostać dostarczone przy użyciu żadnego transportu innego niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="8083f-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6. <span data-ttu-id="8083f-119">Po wybraniu usługi MSMQ do uruchomienia w trybie zaostrzonym maszyna wymaga ponownego uruchomienia w [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8083f-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
7. <span data-ttu-id="8083f-120">Uruchom usługę.</span><span class="sxs-lookup"><span data-stu-id="8083f-120">Run the service.</span></span>  
  
8. <span data-ttu-id="8083f-121">Uruchom klienta programu.</span><span class="sxs-lookup"><span data-stu-id="8083f-121">Run the client.</span></span> <span data-ttu-id="8083f-122">Upewnij się, że adres punktu końcowego został zmieniony tak, aby wskazywał nazwę lub adres IP maszyny zamiast hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="8083f-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="8083f-123">Klient wysyła komunikat i kończy pracę.</span><span class="sxs-lookup"><span data-stu-id="8083f-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8083f-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8083f-124">Requirements</span></span>  
 <span data-ttu-id="8083f-125">Aby można było uruchomić ten przykład, usługi IIS muszą być zainstalowane na komputerach klienckich i klientach oprócz usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="8083f-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="8083f-126">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="8083f-126">Demonstrates</span></span>  
 <span data-ttu-id="8083f-127">Przykład ilustruje wysyłanie komunikatów w kolejce WCF przy użyciu usługi MSMQ za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8083f-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="8083f-128">Jest to również nazywane wiadomościami SRMP.</span><span class="sxs-lookup"><span data-stu-id="8083f-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="8083f-129">Po wysłaniu komunikatu w kolejce usługa MSMQ na komputerze wysyłającym przesyła komunikaty do Menedżera kolejki odbioru przez TCP lub HTTP.</span><span class="sxs-lookup"><span data-stu-id="8083f-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="8083f-130">Po wybraniu opcji SRMP użytkownik wskazuje wybór protokołu HTTP jako transportu do przeniesienia kolejki.</span><span class="sxs-lookup"><span data-stu-id="8083f-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="8083f-131">Funkcja SRMP Secure umożliwia korzystanie z protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8083f-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8083f-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="8083f-132">Example</span></span>  
 <span data-ttu-id="8083f-133">Przykładowy kod jest oparty na przykładach transakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="8083f-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="8083f-134">Jak wysłać komunikat do kolejki i odebrać komunikat z kolejki przy użyciu protokołu SRMP jest taka sama jak wysyłanie i odbieranie komunikatów przy użyciu natywnych protokołów.</span><span class="sxs-lookup"><span data-stu-id="8083f-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="8083f-135">Konfiguracja klienta zostanie zmieniona, aby wskazać wybór protokołu transferu kolejki.</span><span class="sxs-lookup"><span data-stu-id="8083f-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="8083f-136">Protokół transferu kolejki może być jednym z natywnych, SRMP lub SrmpSecure.</span><span class="sxs-lookup"><span data-stu-id="8083f-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="8083f-137">Domyślnie protokół transferu jest natywny.</span><span class="sxs-lookup"><span data-stu-id="8083f-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="8083f-138">Klient i usługa Określ w konfiguracji, aby użyć SRMP w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8083f-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="8083f-139">W odniesieniu do zabezpieczeń transportu istnieją ograniczenia dotyczące protokołu SRMP.</span><span class="sxs-lookup"><span data-stu-id="8083f-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="8083f-140">Domyślne zabezpieczenia transportu usługi MSMQ wymagają Active Directory, które wymagają, aby Menedżer kolejki wysyłania i Menedżer kolejki odbiorczej znajdowały się w tej samej domenie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8083f-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="8083f-141">Nie jest to możliwe w przypadku wysyłania komunikatów za pośrednictwem granicy protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8083f-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="8083f-142">W związku z tym domyślne zabezpieczenia transportu nie działają.</span><span class="sxs-lookup"><span data-stu-id="8083f-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="8083f-143">Zabezpieczenia transportu muszą być ustawione na wartość certyfikat, jeśli są wymagane zabezpieczenia transportu.</span><span class="sxs-lookup"><span data-stu-id="8083f-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="8083f-144">Zabezpieczenia komunikatów mogą również służyć do zabezpieczania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8083f-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="8083f-145">W tym przykładzie zabezpieczenia transportu i komunikatów są wyłączone w celu zilustrowania wiadomości SRMP.</span><span class="sxs-lookup"><span data-stu-id="8083f-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
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
  
 <span data-ttu-id="8083f-146">Uruchomienie przykładu daje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="8083f-146">Running the sample yields the following output.</span></span>  
  
```console  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4   
Customer: somecustomer.com   
OrderDetails   
    Order LineItem: 54 of Blue Widget @unit price: $29.99   
    Order LineItem: 890 of Red Widget @unit price: $45.89   
    Total cost of this order: $42461.56   
    Order status: Pending  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="8083f-147">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8083f-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8083f-148">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="8083f-148">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="8083f-149">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8083f-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8083f-150">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8083f-150">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
