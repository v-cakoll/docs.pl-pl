---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: b1b61c18c801059e95cd0b13a3135132a583882f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183337"
---
# <a name="srmp"></a><span data-ttu-id="fd663-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="fd663-102">SRMP</span></span>
<span data-ttu-id="fd663-103">W tym przykładzie pokazano, jak wykonywać komunikację w kolejce za pomocą usługi kolejkowania wiadomości (MSMQ) za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="fd663-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="fd663-104">W komunikacji w kolejce klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="fd663-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="fd663-105">Dokładniej, klient wysyła wiadomości do kolejki.</span><span class="sxs-lookup"><span data-stu-id="fd663-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="fd663-106">Usługa odbiera wiadomości z kolejki.</span><span class="sxs-lookup"><span data-stu-id="fd663-106">The service receives messages from the queue.</span></span> <span data-ttu-id="fd663-107">W związku z tym usługi i klienta, nie muszą być uruchomione w tym samym czasie do komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="fd663-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="fd663-108">Usługa MSMQ umożliwia używanie protokołu HTTP (w tym korzystania z protokołu HTTPS) do wysyłania wiadomości do kolejki.</span><span class="sxs-lookup"><span data-stu-id="fd663-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="fd663-109">W tym przykładzie zademonstrujemy przy użyciu komunikacji w kolejce programu Windows Communication Foundation (WCF) i jak wysyłać wiadomości za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="fd663-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="fd663-110">Usługa MSMQ używa protokołu o nazwie SRMP, który jest protokołem opartym na mydle do komunikacji za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="fd663-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fd663-111">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="fd663-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fd663-112">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fd663-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fd663-113">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fd663-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fd663-114">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fd663-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="fd663-115">Przed uruchomieniem próbki w **add/remove Windows Components**należy upewnić się, że usługa MSMQ jest zainstalowana z obsługą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="fd663-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="fd663-116">Zainstalowanie obsługi protokołu HTTP automatycznie instaluje internetowe usługi informacyjne (IIS) i dodaje obsługę protokołu w usługach IIS dla usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fd663-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5. <span data-ttu-id="fd663-117">Jeśli chcesz mieć pewność, że protokół HTTP jest używany do komunikacji, możesz włączyć obsługę usługi MSMQ w trybie wzmocnionym.</span><span class="sxs-lookup"><span data-stu-id="fd663-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="fd663-118">Dzięki temu żadne wiadomości do dowolnej kolejki hostowane na komputerze można dotrzeć przy użyciu dowolnego transportu innego niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="fd663-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6. <span data-ttu-id="fd663-119">Po wybraniu usługi MSMQ do uruchomienia w trybie wzmocnionym komputer wymaga ponownego rozruchu w systemie Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="fd663-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on Windows Server 2003.</span></span>  
  
7. <span data-ttu-id="fd663-120">Uruchom usługę.</span><span class="sxs-lookup"><span data-stu-id="fd663-120">Run the service.</span></span>  
  
8. <span data-ttu-id="fd663-121">Uruchom klienta.</span><span class="sxs-lookup"><span data-stu-id="fd663-121">Run the client.</span></span> <span data-ttu-id="fd663-122">Upewnij się, że zmienisz adres punktu końcowego, aby wskazać nazwę komputera lub adres IP zamiast localhost.</span><span class="sxs-lookup"><span data-stu-id="fd663-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="fd663-123">Klient wysyła wiadomość i kończy pracę.</span><span class="sxs-lookup"><span data-stu-id="fd663-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd663-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd663-124">Requirements</span></span>  
 <span data-ttu-id="fd663-125">Aby uruchomić ten przykład, usługi IIS muszą być zainstalowane zarówno na usłudze, jak i na komputerach klienckich oprócz usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fd663-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="fd663-126">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="fd663-126">Demonstrates</span></span>  
 <span data-ttu-id="fd663-127">W przykładzie pokazano wysyłanie wiadomości w kolejce WCF przy użyciu usługi MSMQ za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="fd663-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="fd663-128">Jest to również nazywane wiadomościami SRMP.</span><span class="sxs-lookup"><span data-stu-id="fd663-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="fd663-129">Po wysłaniu wiadomości w kolejce usługa MSMQ na komputerze wysyłającym przenosi wiadomości do menedżera kolejek odbierających za pośrednictwem transportu TCP lub HTTP.</span><span class="sxs-lookup"><span data-stu-id="fd663-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="fd663-130">Wybierając protokół SRMP, użytkownik wskazuje wybór protokołu HTTP jako transportu do transferu kolejek.</span><span class="sxs-lookup"><span data-stu-id="fd663-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="fd663-131">SRMP Secure umożliwia korzystanie z protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="fd663-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd663-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd663-132">Example</span></span>  
 <span data-ttu-id="fd663-133">Przykładowy kod jest oparty na próbce transakcji.</span><span class="sxs-lookup"><span data-stu-id="fd663-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="fd663-134">Sposób wysyłania wiadomości do kolejki i odbierania wiadomości z kolejki przy użyciu protokołu SRMP jest taki sam jak wysyłanie i odbieranie wiadomości przy użyciu protokołu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="fd663-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="fd663-135">Konfiguracja klienta zostanie zmieniona, aby wskazać wybór protokołu transferu kolejki.</span><span class="sxs-lookup"><span data-stu-id="fd663-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="fd663-136">Protokół transferu kolejki może być jednym z Native, SRMP lub SrmpSecure.</span><span class="sxs-lookup"><span data-stu-id="fd663-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="fd663-137">Domyślnie protokół transferu jest macierzysty.</span><span class="sxs-lookup"><span data-stu-id="fd663-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="fd663-138">Klient i usługa określić w konfiguracji, aby użyć SRMP w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="fd663-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="fd663-139">Istnieją ograniczenia dotyczące SRMP w odniesieniu do bezpieczeństwa transportu.</span><span class="sxs-lookup"><span data-stu-id="fd663-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="fd663-140">Domyślne zabezpieczenia transportu usługi MSMQ wymagają usługi Active Directory, która wymaga, aby menedżer kolejek wysyłających i menedżer kolejek odbierających rezydują w tej samej domenie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fd663-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="fd663-141">Nie jest to możliwe podczas wysyłania wiadomości za pośrednictwem granicy HTTP.</span><span class="sxs-lookup"><span data-stu-id="fd663-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="fd663-142">W związku z tym domyślne zabezpieczenia transportu nie działa.</span><span class="sxs-lookup"><span data-stu-id="fd663-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="fd663-143">Zabezpieczenia transportu musi być ustawiona na Certyfikat, jeśli jest to pożądane zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="fd663-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="fd663-144">Zabezpieczenia wiadomości mogą być również używane do zabezpieczania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fd663-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="fd663-145">W tym przykładzie zabezpieczeń transportu i wiadomości jest wyłączony, aby zilustrować wiadomości SRMP.</span><span class="sxs-lookup"><span data-stu-id="fd663-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
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
  
 <span data-ttu-id="fd663-146">Uruchamianie próbki daje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="fd663-146">Running the sample yields the following output.</span></span>  
  
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
> <span data-ttu-id="fd663-147">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="fd663-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fd663-148">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="fd663-148">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fd663-149">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="fd663-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fd663-150">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fd663-150">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
