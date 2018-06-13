---
title: Kanał dzielący na fragmenty
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 1acb635be23b9a838abee714156d818abee6bcd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508845"
---
# <a name="chunking-channel"></a><span data-ttu-id="30d19-102">Kanał dzielący na fragmenty</span><span class="sxs-lookup"><span data-stu-id="30d19-102">Chunking Channel</span></span>
<span data-ttu-id="30d19-103">Podczas wysyłania dużych wiadomości przy użyciu usługi Windows Communication Foundation (WCF), często jest pożądane, aby ograniczyć ilość pamięci użytej do zbuforowania tych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="30d19-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="30d19-104">Możliwe rozwiązanie jest strumienia treści wiadomości (przy założeniu, że większość danych znajduje się w treści).</span><span class="sxs-lookup"><span data-stu-id="30d19-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="30d19-105">Jednak niektóre protokoły wymagają buforowanie cały komunikat.</span><span class="sxs-lookup"><span data-stu-id="30d19-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="30d19-106">Niezawodna obsługa komunikatów i zabezpieczeń są dwa takie przykłady.</span><span class="sxs-lookup"><span data-stu-id="30d19-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="30d19-107">Innym rozwiązaniem możliwe jest do dzielenia dużych wiadomość na mniejsze wiadomości nazywanej fragmentów, wysłać jednym fragmencie tych fragmentów w czasie i Przywróć dużych komunikatów po stronie odbierającej.</span><span class="sxs-lookup"><span data-stu-id="30d19-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="30d19-108">Sama aplikacja może wykonać tego podziału i cofnąć podziału lub można użyć niestandardowego kanału Aby wykonać to zadanie.</span><span class="sxs-lookup"><span data-stu-id="30d19-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="30d19-109">Segmentu przykład kanału pokazuje, jak protokołu niestandardowego lub warstwowego kanału może służyć do podziału i cofnąć podziału dowolnie dużą wiadomości.</span><span class="sxs-lookup"><span data-stu-id="30d19-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>  
  
 <span data-ttu-id="30d19-110">Podziału powinien zawsze można zastosować tylko wtedy, gdy skonstruowane cały komunikat do wysłania.</span><span class="sxs-lookup"><span data-stu-id="30d19-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="30d19-111">Segmentu kanału powinna być zawsze warstwie poniżej kanału zabezpieczeń i kanał niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="30d19-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30d19-112">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="30d19-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="30d19-113">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="30d19-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="30d19-114">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="30d19-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="30d19-115">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="30d19-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="30d19-116">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="30d19-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="30d19-117">Segmentu założenia kanału i ograniczenia</span><span class="sxs-lookup"><span data-stu-id="30d19-117">Chunking Channel Assumptions and Limitations</span></span>  
  
### <a name="message-structure"></a><span data-ttu-id="30d19-118">Komunikat — struktura</span><span class="sxs-lookup"><span data-stu-id="30d19-118">Message Structure</span></span>  
 <span data-ttu-id="30d19-119">Kanał segmentu zakłada następującą strukturę komunikatu dla komunikatów do fragmentarycznego można:</span><span class="sxs-lookup"><span data-stu-id="30d19-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>  
  
```xml  
<soap:Envelope ...>  
  <!-- headers -->  
  <soap:Body>  
    <operationElement>  
      <paramElement>data to be chunked</paramElement>  
    </operationElement>  
  </soap:Body>  
</soap:Envelope>  
```  
  
 <span data-ttu-id="30d19-120">Podczas korzystania z modelu ServiceModel, należy Zwiń operacji, mających 1 parametr wejściowy jest zgodne z tym kształtem komunikatu dla ich komunikatu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="30d19-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="30d19-121">Podobnie kontrakt operacji, które ma 1 parametr danych wyjściowych ani zwracanej wartości są zgodne z komunikatu dla komunikatów ich dane wyjściowe tego kształtu.</span><span class="sxs-lookup"><span data-stu-id="30d19-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="30d19-122">Poniżej przedstawiono przykłady takich operacji:</span><span class="sxs-lookup"><span data-stu-id="30d19-122">The following are examples of such operations:</span></span>  
  
```  
[ServiceContract]  
interface ITestService  
{  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
  
    [OperationContract]  
    Stream DownloadStream();  
  
    [OperationContract(IsOneWay = true)]  
    void UploadStream(Stream stream);  
}  
```  
  
### <a name="sessions"></a><span data-ttu-id="30d19-123">Kategoria Sessions</span><span class="sxs-lookup"><span data-stu-id="30d19-123">Sessions</span></span>  
 <span data-ttu-id="30d19-124">Kanał segmentu wymaga wiadomości dostarczanych tylko raz w uporządkowanego dostarczenia komunikatów (fragmentów).</span><span class="sxs-lookup"><span data-stu-id="30d19-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="30d19-125">Oznacza to, że źródłowy stosu kanału musi być sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="30d19-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="30d19-126">Można podać sesji transportu (na przykład transportu TCP) lub przez protokół zamykania kanał (na przykład ReliableSession kanał).</span><span class="sxs-lookup"><span data-stu-id="30d19-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>  
  
### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="30d19-127">Asynchronicznego wysyłania i odbierania</span><span class="sxs-lookup"><span data-stu-id="30d19-127">Asynchronous Send and Receive</span></span>  
 <span data-ttu-id="30d19-128">Asynchronous wysyłania i odbierania metod nie są zaimplementowane w tej wersji segmentu przykład kanału.</span><span class="sxs-lookup"><span data-stu-id="30d19-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>  
  
## <a name="chunking-protocol"></a><span data-ttu-id="30d19-129">Protokół segmentu</span><span class="sxs-lookup"><span data-stu-id="30d19-129">Chunking Protocol</span></span>  
 <span data-ttu-id="30d19-130">Kanał segmentu Określa protokół, który wskazuje początek i koniec serii fragmentów, a także numer sekwencyjny każdego fragmentu.</span><span class="sxs-lookup"><span data-stu-id="30d19-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="30d19-131">Następujące komunikaty przykładzie trzy pokazują start, fragmentów i na końcu wiadomości z komentarzami, które opisują kluczowe aspekty.</span><span class="sxs-lookup"><span data-stu-id="30d19-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>  
  
### <a name="start-message"></a><span data-ttu-id="30d19-132">Komunikat uruchomienia</span><span class="sxs-lookup"><span data-stu-id="30d19-132">Start Message</span></span>  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
<!—Original message action is replaced with a chunking-specific action. -->  
    <a:Action s:mustUnderstand="1">http://samples.microsoft.com/chunkingAction</a:Action>  
<!--  
Original message is assigned a unique id that is transmitted   
in a MessageId header. Note that this is different from the WS-Addressing MessageId header.  
-->  
    <MessageId s:mustUnderstand="1" xmlns="http://samples.microsoft.com/chunking">  
53f183ee-04aa-44a0-b8d3-e45224563109  
</MessageId>  
<!--  
ChunkingStart header signals the start of a chunked message.  
-->  
    <ChunkingStart s:mustUnderstand="1" i:nil="true" xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://samples.microsoft.com/chunking" />  
<!--  
Original message action is transmitted in OriginalAction.  
This is required to re-create the original message on the other side.  
-->  
    <OriginalAction xmlns="http://samples.microsoft.com/chunking">  
http://tempuri.org/ITestService/EchoStream  
    </OriginalAction>  
   <!--  
    All original message headers are included here.  
   -->  
  </s:Header>  
  <s:Body>  
<!--  
Chunking assumes this structure of Body content:  
<element>  
  <childelement>large data to be chunked<childelement>  
</element>  
The start message contains just <element> and <childelement> without  
the data to be chunked.  
-->  
    <EchoStream xmlns="http://tempuri.org/">  
      <stream />  
    </EchoStream>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="chunk-message"></a><span data-ttu-id="30d19-133">Komunikat fragmentu</span><span class="sxs-lookup"><span data-stu-id="30d19-133">Chunk Message</span></span>  
  
```xml  
<s:Envelope   
  xmlns:a="http://www.w3.org/2005/08/addressing"   
  xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
   <!--  
    All chunking protocol messages have this action.  
   -->  
    <a:Action s:mustUnderstand="1">  
      http://samples.microsoft.com/chunkingAction  
    </a:Action>  
<!--  
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.  
-->  
    <MessageId s:mustUnderstand="1"   
               xmlns="http://samples.microsoft.com/chunking">  
      53f183ee-04aa-44a0-b8d3-e45224563109  
    </MessageId>  
<!--  
The sequence number of the chunk.  
This number restarts at 1 with each new sequence of chunks.  
-->  
    <ChunkNumber s:mustUnderstand="1"   
                 xmlns="http://samples.microsoft.com/chunking">  
      1096  
    </ChunkNumber>  
  </s:Header>  
  <s:Body>  
<!--  
The chunked data is wrapped in a chunk element.  
The encoding of this data (and the entire message)   
depends on the encoder used. The chunking channel does not mandate an encoding.  
-->  
    <chunk xmlns="http://samples.microsoft.com/chunking">  
kfSr2QcBlkHTvQ==  
    </chunk>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="end-message"></a><span data-ttu-id="30d19-134">Komunikat</span><span class="sxs-lookup"><span data-stu-id="30d19-134">End Message</span></span>  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
    <a:Action s:mustUnderstand="1">  
      http://samples.microsoft.com/chunkingAction  
    </a:Action>  
<!--  
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.  
-->  
    <MessageId s:mustUnderstand="1"   
               xmlns="http://samples.microsoft.com/chunking">  
      53f183ee-04aa-44a0-b8d3-e45224563109  
    </MessageId>  
<!--  
ChunkingEnd header signals the end of a chunk sequence.  
-->  
    <ChunkingEnd s:mustUnderstand="1" i:nil="true"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance"   
                 xmlns="http://samples.microsoft.com/chunking" />  
<!--  
ChunkingEnd messages have a sequence number.  
-->  
    <ChunkNumber s:mustUnderstand="1"   
                 xmlns="http://samples.microsoft.com/chunking">  
      79  
    </ChunkNumber>  
  </s:Header>  
  <s:Body>  
<!--  
The ChunkingEnd message has the same <element><childelement> structure  
as the ChunkingStart message.  
-->  
    <EchoStream xmlns="http://tempuri.org/">  
      <stream />  
    </EchoStream>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="chunking-channel-architecture"></a><span data-ttu-id="30d19-135">Architektura kanału segmentu</span><span class="sxs-lookup"><span data-stu-id="30d19-135">Chunking Channel Architecture</span></span>  
 <span data-ttu-id="30d19-136">Kanał segmentu jest `IDuplexSessionChannel` , na wysokim poziomie następujący architektura typowe kanału.</span><span class="sxs-lookup"><span data-stu-id="30d19-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="30d19-137">Brak `ChunkingBindingElement` który można tworzyć `ChunkingChannelFactory` i `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="30d19-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="30d19-138">`ChunkingChannelFactory` Tworzy wystąpienia `ChunkingChannel` gdy otrzyma monit.</span><span class="sxs-lookup"><span data-stu-id="30d19-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="30d19-139">`ChunkingChannelListener` Tworzy wystąpienia `ChunkingChannel` po zaakceptowaniu nowy kanał wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="30d19-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="30d19-140">`ChunkingChannel` Jest odpowiedzialny za wysyłanie i odbieranie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="30d19-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>  
  
 <span data-ttu-id="30d19-141">Na następny poziom w dół `ChunkingChannel` opiera się na kilka składników do implementowania protokołu segmentu.</span><span class="sxs-lookup"><span data-stu-id="30d19-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="30d19-142">Po stronie wysyłającej kanału używa niestandardowego `XmlDictionaryWriter` o nazwie `ChunkingWriter` wykonuje rzeczywiste podziału.</span><span class="sxs-lookup"><span data-stu-id="30d19-142">On the send side, the channel uses a custom `XmlDictionaryWriter` called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="30d19-143">`ChunkingWriter` wysyła przy użyciu kanału wewnętrzny bezpośrednio fragmentów.</span><span class="sxs-lookup"><span data-stu-id="30d19-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="30d19-144">Przy użyciu niestandardowego `XmlDictionaryWriter` umożliwia firmie Microsoft w celu wysłania fragmentów, jak jest zapisywana duża treści oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="30d19-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="30d19-145">Oznacza to, że firma Microsoft nie buforowania całego oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="30d19-145">This means we do not buffer the entire original message.</span></span>  
  
 <span data-ttu-id="30d19-146">![Kanał dzielący na fragmenty](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")</span><span class="sxs-lookup"><span data-stu-id="30d19-146">![Chunking Channel](../../../../docs/framework/wcf/samples/media/chunkingchannel1.gif "ChunkingChannel1")</span></span>  
  
 <span data-ttu-id="30d19-147">Po stronie odbierania `ChunkingChannel` pobiera komunikaty z kanału wewnętrzny i przekazuje je do niestandardowego `XmlDictionaryReader` o nazwie `ChunkingReader`, który reconstitutes z przychodzącego fragmentów oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="30d19-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom `XmlDictionaryReader` called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="30d19-148">`ChunkingChannel` opakowuje to `ChunkingReader` w niestandardowej `Message` wdrożenia o nazwie `ChunkingMessage` i zwraca ten komunikat do warstwy powyżej.</span><span class="sxs-lookup"><span data-stu-id="30d19-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="30d19-149">Ta kombinacja `ChunkingReader` i `ChunkingMessage` pozwala cofnąć bryłkach oryginalnego treść komunikatu zgodnie z są odczytywane przez warstwę powyżej zamiast buforu całej treści oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="30d19-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="30d19-150">`ChunkingReader` ma kolejkę, gdzie buforuje przychodzące fragmentów maksymalnie można skonfigurować maksymalną liczbę buforowanych fragmentów.</span><span class="sxs-lookup"><span data-stu-id="30d19-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="30d19-151">Po osiągnięciu tego limitu maksymalnej czytnik czeka na komunikaty, aby być opróżnione z kolejki przez warstwę powyżej (oznacza to, odczytując tylko z treści oryginalnej wiadomości) lub do momentu odbierania maksymalną osiągnięciu limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="30d19-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>  
  
 <span data-ttu-id="30d19-152">![Kanał dzielący na fragmenty](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")</span><span class="sxs-lookup"><span data-stu-id="30d19-152">![Chunking Channel](../../../../docs/framework/wcf/samples/media/chunkingchannel2.gif "ChunkingChannel2")</span></span>  
  
## <a name="chunking-programming-model"></a><span data-ttu-id="30d19-153">Model programowania podziału</span><span class="sxs-lookup"><span data-stu-id="30d19-153">Chunking Programming Model</span></span>  
 <span data-ttu-id="30d19-154">Deweloperzy usług można określić wiadomości, które mają być fragmentaryczne stosując `ChunkingBehavior` atrybutu z operacjami w ramach umowy.</span><span class="sxs-lookup"><span data-stu-id="30d19-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="30d19-155">Udostępnia atrybut `AppliesTo` właściwość, która umożliwia deweloperowi określić, czy podziału stosuje się do komunikatu wejściowego, komunikatu wyjściowego lub obu.</span><span class="sxs-lookup"><span data-stu-id="30d19-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="30d19-156">W poniższym przykładzie przedstawiono użycie `ChunkingBehavior` atrybutu:</span><span class="sxs-lookup"><span data-stu-id="30d19-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>  
  
```  
[ServiceContract]  
interface ITestService  
{  
    [OperationContract]  
    [ChunkingBehavior(ChunkingAppliesTo.Both)]  
    Stream EchoStream(Stream stream);  
  
    [OperationContract]  
    [ChunkingBehavior(ChunkingAppliesTo.OutMessage)]  
    Stream DownloadStream();  
  
    [OperationContract(IsOneWay=true)]  
    [ChunkingBehavior(ChunkingAppliesTo.InMessage)]  
    void UploadStream(Stream stream);  
  
}  
```  
  
 <span data-ttu-id="30d19-157">Z tego modelu programowania `ChunkingBindingElement` kompiluje listę akcji zidentyfikować komunikaty, aby być fragmentaryczne identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="30d19-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="30d19-158">Akcja każdego komunikatu wychodzącego jest porównywana z tej listy, aby określić, czy fragmentaryczne też wysyłane bezpośrednio wiadomości.</span><span class="sxs-lookup"><span data-stu-id="30d19-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>  
  
## <a name="implementing-the-send-operation"></a><span data-ttu-id="30d19-159">Implementowanie operacji wysyłania</span><span class="sxs-lookup"><span data-stu-id="30d19-159">Implementing the Send Operation</span></span>  
 <span data-ttu-id="30d19-160">Na wysokim poziomie operacji wysyłania najpierw sprawdza, czy wiadomości wychodzącej musi być fragmentaryczne i, jeśli nie, wysyła wiadomość bezpośrednio za pomocą kanału wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="30d19-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>  
  
 <span data-ttu-id="30d19-161">Jeśli wiadomość musi fragmentaryczne, Wyślij tworzy nowy `ChunkingWriter` i wywołania `WriteBodyContents` komunikatu wychodzącego przekazanie jej przez to `ChunkingWriter`.</span><span class="sxs-lookup"><span data-stu-id="30d19-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="30d19-162">`ChunkingWriter` , A następnie jest podziału komunikatów (w tym kopiowanie oryginalne nagłówki wiadomości na komunikat uruchomienia fragmentu) i wysyła fragmentów za pomocą kanału wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="30d19-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>  
  
 <span data-ttu-id="30d19-163">Kilka szczegóły warto zauważyć:</span><span class="sxs-lookup"><span data-stu-id="30d19-163">A few details worth noting:</span></span>  
  
-   <span data-ttu-id="30d19-164">Wyślij pierwsze wywołania `ThrowIfDisposedOrNotOpened` zapewnienie `CommunicationState` jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="30d19-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>  
  
-   <span data-ttu-id="30d19-165">Wysyłanie są synchronizowane, mogą być wysyłane tylko jeden wiadomości w czasie dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="30d19-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="30d19-166">Brak `ManualResetEvent` o nazwie `sendingDone` zresetowania po wysłaniu wiadomości podzielony.</span><span class="sxs-lookup"><span data-stu-id="30d19-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="30d19-167">Wysłany komunikat fragmentu zakończenia tego zdarzenia jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="30d19-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="30d19-168">Metody Send oczekuje dla tego zdarzenia, należy ustawić przed ponowną próbą wysłania wychodzących.</span><span class="sxs-lookup"><span data-stu-id="30d19-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>  
  
-   <span data-ttu-id="30d19-169">Wyślij blokad `CommunicationObject.ThisLock` zapobiegające synchronizacji zmian stanu podczas wysyłania.</span><span class="sxs-lookup"><span data-stu-id="30d19-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="30d19-170">Zobacz <xref:System.ServiceModel.Channels.CommunicationObject> dokumentację, aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Channels.CommunicationObject> stanów i komputera stanu.</span><span class="sxs-lookup"><span data-stu-id="30d19-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>  
  
-   <span data-ttu-id="30d19-171">Limit czasu przekazany do wysyłania jest używany jako limit czasu dla operacji wysyłania całego, która obejmuje wszystkie fragmenty wysyłanie.</span><span class="sxs-lookup"><span data-stu-id="30d19-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>  
  
-   <span data-ttu-id="30d19-172">Niestandardowa `XmlDictionaryWriter` projektu została wybrana, aby uniknąć buforowanie całej treści oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="30d19-172">The custom `XmlDictionaryWriter` design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="30d19-173">Czy możemy uzyskać `XmlDictionaryReader` przy użyciu treści `message.GetReaderAtBodyContents` cały będą buforowane.</span><span class="sxs-lookup"><span data-stu-id="30d19-173">If we were to get an `XmlDictionaryReader` on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="30d19-174">Zamiast tego mamy niestandardowego `XmlDictionaryWriter` przekazywany do `message.WriteBodyContents`.</span><span class="sxs-lookup"><span data-stu-id="30d19-174">Instead, we have a custom `XmlDictionaryWriter` that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="30d19-175">Jako wiadomości wywołania WriteBase64 na składnik zapisywania, moduł zapisujący pakietów się fragmentów w komunikatach i wysyła je przy użyciu kanału wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="30d19-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="30d19-176">Bloki WriteBase64 momentu wysłania fragmentów.</span><span class="sxs-lookup"><span data-stu-id="30d19-176">WriteBase64 blocks until the chunk is sent.</span></span>  
  
## <a name="implementing-the-receive-operation"></a><span data-ttu-id="30d19-177">Implementowanie operacji odbierania</span><span class="sxs-lookup"><span data-stu-id="30d19-177">Implementing the Receive Operation</span></span>  
 <span data-ttu-id="30d19-178">Na wysokim poziomie operacji odbierania najpierw sprawdza, czy komunikat przychodzący nie jest `null` i że jego działanie jest `ChunkingAction`.</span><span class="sxs-lookup"><span data-stu-id="30d19-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="30d19-179">Jeśli nie spełnia kryteriów zarówno, zwracany jest komunikat niezmienione Receive.</span><span class="sxs-lookup"><span data-stu-id="30d19-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="30d19-180">W przeciwnym razie Receive tworzy nowy `ChunkingReader` i nowy `ChunkingMessage` otaczający go (wywołując `GetNewChunkingMessage`).</span><span class="sxs-lookup"><span data-stu-id="30d19-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="30d19-181">Przed powrotem przez nowych `ChunkingMessage`, Receive korzysta z puli wątków do wykonania `ReceiveChunkLoop`, które wywołuje `innerChannel.Receive` w pętli i ręce poza fragmentów do `ChunkingReader` aż do zakończenia fragmentu komunikat jest odbierany lub jest osiągnęła limit czasu odbioru.</span><span class="sxs-lookup"><span data-stu-id="30d19-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>  
  
 <span data-ttu-id="30d19-182">Kilka szczegóły warto zauważyć:</span><span class="sxs-lookup"><span data-stu-id="30d19-182">A few details worth noting:</span></span>  
  
-   <span data-ttu-id="30d19-183">Jak wysyłania, odbierania połączeń pierwszy `ThrowIfDisposedOrNotOepned` zapewnienie `CommunicationState` jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="30d19-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>  
  
-   <span data-ttu-id="30d19-184">Wyświetlany jest synchronizowane, tak że tylko jeden komunikat może zostać odebrany w czasie z sesji.</span><span class="sxs-lookup"><span data-stu-id="30d19-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="30d19-185">Jest to szczególnie ważne, ponieważ po odebraniu komunikatu fragmentu start, wszystkie kolejne odebrane wiadomości powinny być fragmentów w ramach nowej sekwencji fragmentu do momentu otrzymania wiadomości końcowego fragmentu.</span><span class="sxs-lookup"><span data-stu-id="30d19-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="30d19-186">Odbieranie nie może pobierać komunikaty z kanału wewnętrzny, dopóki wszystkie fragmenty należące do komunikatu obecnie cofnąć trwa fragmentaryczne są odbierane.</span><span class="sxs-lookup"><span data-stu-id="30d19-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="30d19-187">W tym celu odbierania używa `ManualResetEvent` o nazwie `currentMessageCompleted`, która ma wartość, gdy komunikat fragmentu zakończenia jest odbierany i zresetować po odebraniu nowego komunikatu fragmentu rozpoczęcia.</span><span class="sxs-lookup"><span data-stu-id="30d19-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>  
  
-   <span data-ttu-id="30d19-188">W przeciwieństwie do wysyłania Receive nie zapobiega przejścia zsynchronizowanie podczas odbierania.</span><span class="sxs-lookup"><span data-stu-id="30d19-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="30d19-189">Na przykład Zamknij można wywołać podczas odbierania i czeka, aż do ukończenia oczekującej receive oryginalnej wiadomości lub osiągnięto wartość określonego limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="30d19-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>  
  
-   <span data-ttu-id="30d19-190">Limit czasu przekazany do odbierania jest używany jako limitu czasu dla całego odbierania operacja, która obejmuje wszystkie fragmenty odbierania.</span><span class="sxs-lookup"><span data-stu-id="30d19-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>  
  
-   <span data-ttu-id="30d19-191">Jeśli warstwy, który wykorzystuje komunikat zajmuje treść komunikatu z szybkością mniejszy niż liczba komunikatów przychodzących fragmentu, `ChunkingReader` buforuje tych fragmentów przychodzące do limitu określonego przez `ChunkingBindingElement.MaxBufferedChunks`.</span><span class="sxs-lookup"><span data-stu-id="30d19-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="30d19-192">Po osiągnięciu tego limitu już fragmentów są pobierane z dolnej warstwy, aż do buforowanego fragmentu jest używany lub osiągnięto limit czasu odbioru.</span><span class="sxs-lookup"><span data-stu-id="30d19-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>  
  
## <a name="communicationobject-overrides"></a><span data-ttu-id="30d19-193">Zastąpienia CommunicationObject</span><span class="sxs-lookup"><span data-stu-id="30d19-193">CommunicationObject Overrides</span></span>  
  
### <a name="onopen"></a><span data-ttu-id="30d19-194">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="30d19-194">OnOpen</span></span>  
 <span data-ttu-id="30d19-195">`OnOpen` wywołania `innerChannel.Open` otworzyć kanału wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="30d19-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>  
  
### <a name="onclose"></a><span data-ttu-id="30d19-196">OnClose</span><span class="sxs-lookup"><span data-stu-id="30d19-196">OnClose</span></span>  
 <span data-ttu-id="30d19-197">`OnClose` najpierw ustawia `stopReceive` do `true` sygnalizują oczekujące `ReceiveChunkLoop` zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="30d19-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="30d19-198">Następnie czeka na `receiveStopped``ManualResetEvent`, która jest ustawiana w przypadku `ReceiveChunkLoop` zatrzymuje.</span><span class="sxs-lookup"><span data-stu-id="30d19-198">It then waits for the `receiveStopped``ManualResetEvent`, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="30d19-199">Zakładając, że `ReceiveChunkLoop` zatrzymuje się przed upływem określonego limitu czasu `OnClose` wywołania `innerChannel.Close` pozostałych limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="30d19-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>  
  
### <a name="onabort"></a><span data-ttu-id="30d19-200">OnAbort</span><span class="sxs-lookup"><span data-stu-id="30d19-200">OnAbort</span></span>  
 <span data-ttu-id="30d19-201">`OnAbort` wywołania `innerChannel.Abort` przerwania wewnętrzny kanału.</span><span class="sxs-lookup"><span data-stu-id="30d19-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="30d19-202">Jeśli istnieje oczekujące `ReceiveChunkLoop` pobiera wyjątku z oczekujących `innerChannel.Receive` wywołania.</span><span class="sxs-lookup"><span data-stu-id="30d19-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>  
  
### <a name="onfaulted"></a><span data-ttu-id="30d19-203">OnFaulted</span><span class="sxs-lookup"><span data-stu-id="30d19-203">OnFaulted</span></span>  
 <span data-ttu-id="30d19-204">`ChunkingChannel` Nie wymaga specjalnego zachowania, gdy kanał komunikacji niezawodnej to `OnFaulted` nie zostanie zastąpiona.</span><span class="sxs-lookup"><span data-stu-id="30d19-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>  
  
## <a name="implementing-channel-factory"></a><span data-ttu-id="30d19-205">Implementowanie fabryki kanałów</span><span class="sxs-lookup"><span data-stu-id="30d19-205">Implementing Channel Factory</span></span>  
 <span data-ttu-id="30d19-206">`ChunkingChannelFactory` Odpowiedzialną za tworzenie wystąpień `ChunkingDuplexSessionChannel` i kaskadowych zmian stanu do wewnętrzna fabryka kanałów.</span><span class="sxs-lookup"><span data-stu-id="30d19-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>  
  
 <span data-ttu-id="30d19-207">`OnCreateChannel` używa wewnętrzna fabryka kanałów w celu utworzenia `IDuplexSessionChannel` wewnętrzny kanału.</span><span class="sxs-lookup"><span data-stu-id="30d19-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="30d19-208">Następnie tworzy nowy `ChunkingDuplexSessionChannel` przekazanie jej przez ten kanał wewnętrzny wraz z listy można fragmentaryczne akcje wiadomości i maksymalną liczbę fragmentów do zbuforowania podczas odbierania.</span><span class="sxs-lookup"><span data-stu-id="30d19-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="30d19-209">Listę można fragmentaryczne akcje wiadomości i maksymalną liczbę fragmentów, aby buforować są dwa parametry przekazywane do `ChunkingChannelFactory` w jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="30d19-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="30d19-210">Sekcję `ChunkingBindingElement` w tym artykule opisano, skąd pochodzą te wartości.</span><span class="sxs-lookup"><span data-stu-id="30d19-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>  
  
 <span data-ttu-id="30d19-211">`OnOpen`, `OnClose`, `OnAbort` i ich odpowiedniki asynchroniczne wywołanie odpowiedniej metody przejścia stanu na wewnętrzna fabryka kanałów.</span><span class="sxs-lookup"><span data-stu-id="30d19-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>  
  
## <a name="implementing-channel-listener"></a><span data-ttu-id="30d19-212">Implementowanie odbiornika kanałów</span><span class="sxs-lookup"><span data-stu-id="30d19-212">Implementing Channel Listener</span></span>  
 <span data-ttu-id="30d19-213">`ChunkingChannelListener` Jest otokę odbiornika kanałów wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="30d19-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="30d19-214">Jej główną funkcją, oprócz delegata wywołania tego odbiornika kanału wewnętrzny jest opakowywać nowych `ChunkingDuplexSessionChannels` wokół kanały akceptowane z odbiornika kanałów wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="30d19-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="30d19-215">Jest to wykonywane w `OnAcceptChannel` i `OnEndAcceptChannel`.</span><span class="sxs-lookup"><span data-stu-id="30d19-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="30d19-216">Nowo utworzony `ChunkingDuplexSessionChannel` jest przekazywany wewnętrzny kanału oraz inne parametry opisane wcześniej.</span><span class="sxs-lookup"><span data-stu-id="30d19-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>  
  
## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="30d19-217">Wdrażanie elementu powiązania i powiązania</span><span class="sxs-lookup"><span data-stu-id="30d19-217">Implementing Binding Element and Binding</span></span>  
 <span data-ttu-id="30d19-218">`ChunkingBindingElement` jest odpowiedzialny za tworzenie `ChunkingChannelFactory` i `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="30d19-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="30d19-219">`ChunkingBindingElement` Sprawdza, czy T w `CanBuildChannelFactory` \<T > i `CanBuildChannelListener` \<T > jest typu `IDuplexSessionChannel` (tylko kanał obsługiwane przez kanał segmentu) i inne elementy powiązania powiązanie obsługuje to Typ kanału.</span><span class="sxs-lookup"><span data-stu-id="30d19-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>  
  
 <span data-ttu-id="30d19-220">`BuildChannelFactory`\<T > najpierw sprawdza, czy typ kanału żądanej mogą być wbudowane, a następnie pobiera listę komunikatów akcje fragmentarycznego można.</span><span class="sxs-lookup"><span data-stu-id="30d19-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="30d19-221">Aby uzyskać więcej informacji zobacz sekcję poniżej.</span><span class="sxs-lookup"><span data-stu-id="30d19-221">For more information, see the following section.</span></span> <span data-ttu-id="30d19-222">Następnie tworzy nowy `ChunkingChannelFactory` przekazanie jej wewnętrzna fabryka kanałów (zwrócony z `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), listy Akcje wiadomości i maksymalną liczbę fragmentów do buforowania.</span><span class="sxs-lookup"><span data-stu-id="30d19-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="30d19-223">Maksymalna liczba fragmentów pochodzi z właściwość o nazwie `MaxBufferedChunks` udostępnianych przez `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="30d19-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>  
  
 <span data-ttu-id="30d19-224">`BuildChannelListener<T>` implementacją podobne do tworzenia `ChunkingChannelListener` i przekazanie jej przez odbiornik kanału wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="30d19-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>  
  
 <span data-ttu-id="30d19-225">Brak powiązania przykład zawarty w tym przykładzie o nazwie `TcpChunkingBinding`.</span><span class="sxs-lookup"><span data-stu-id="30d19-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="30d19-226">To powiązanie składa się z dwóch elementów powiązania: `TcpTransportBindingElement` i `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="30d19-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="30d19-227">Oprócz udostępnianie `MaxBufferedChunks` właściwość powiązania także ustawia niektóre `TcpTransportBindingElement` właściwości, takie jak `MaxReceivedMessageSize` (ustawia ją na `ChunkingUtils.ChunkSize` + 100 KB bajtów dla nagłówków).</span><span class="sxs-lookup"><span data-stu-id="30d19-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>  
  
 <span data-ttu-id="30d19-228">`TcpChunkingBinding` implementuje również `IBindingRuntimePreferences` i zwraca wartość true z `ReceiveSynchronously` metody wskazujący, że są wykonywane tylko synchroniczne wywołania Receive.</span><span class="sxs-lookup"><span data-stu-id="30d19-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>  
  
### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="30d19-229">Określanie, które wiadomości do fragmentu</span><span class="sxs-lookup"><span data-stu-id="30d19-229">Determining Which Messages To Chunk</span></span>  
 <span data-ttu-id="30d19-230">Kanał segmentu chunks tylko komunikaty identyfikowane za pomocą `ChunkingBehavior` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="30d19-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="30d19-231">`ChunkingBehavior` Klasa implementuje `IOperationBehavior` i jest implementowane przez wywołanie metody `AddBindingParameter` metody.</span><span class="sxs-lookup"><span data-stu-id="30d19-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="30d19-232">W przypadku tej metody `ChunkingBehavior` sprawdza, czy wartość jego `AppliesTo` właściwości (`InMessage`, `OutMessage` lub obie) do określenia wiadomości, które powinny być fragmentaryczne.</span><span class="sxs-lookup"><span data-stu-id="30d19-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="30d19-233">Następnie pobiera działania każdego z tych wiadomości (z kolekcji wiadomości na `OperationDescription`) i dodaje go do kolekcji ciągów, zawartych w wystąpienia `ChunkingBindingParameter`.</span><span class="sxs-lookup"><span data-stu-id="30d19-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="30d19-234">Dodaje następnie to `ChunkingBindingParameter` w udostępnionej klasie `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="30d19-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>  
  
 <span data-ttu-id="30d19-235">To `BindingParameterCollection` jest przekazywany wewnątrz `BindingContext` do każdego elementu powiązania w powiązaniu podczas tworzenia elementu powiązania fabryki kanału lub odbiornika kanałów.</span><span class="sxs-lookup"><span data-stu-id="30d19-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="30d19-236">`ChunkingBindingElement`w implementacji `BuildChannelFactory<T>` i `BuildChannelListener<T>` ściągnięcia to `ChunkingBindingParameter` z `BindingContext’`s `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="30d19-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="30d19-237">Zbiór działań zawartych w `ChunkingBindingParameter` są następnie przekazywane do `ChunkingChannelFactory` lub `ChunkingChannelListener`, który z kolei przekazuje go do `ChunkingDuplexSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="30d19-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="30d19-238">Uruchomiona próbki</span><span class="sxs-lookup"><span data-stu-id="30d19-238">Running the Sample</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="30d19-239">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="30d19-239">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="30d19-240">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="30d19-240">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="30d19-241">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="30d19-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="30d19-242">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="30d19-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="30d19-243">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="30d19-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="30d19-244">Uruchom najpierw Service.exe, uruchom Client.exe i obejrzyj oba okna konsoli dla danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="30d19-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>  
  
 <span data-ttu-id="30d19-245">Podczas uruchamiania próbki, oczekiwano następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="30d19-245">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="30d19-246">Klient:</span><span class="sxs-lookup"><span data-stu-id="30d19-246">Client:</span></span>  
  
```  
Press enter when service is available  
  
 > Sent chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 < Received chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
```  
  
 <span data-ttu-id="30d19-247">Serwer:</span><span class="sxs-lookup"><span data-stu-id="30d19-247">Server:</span></span>  
  
```  
Service started, press enter to exit  
 < Received chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 < Received chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10  
 > Sent chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
 > Sent chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd  
```  
  
## <a name="see-also"></a><span data-ttu-id="30d19-248">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30d19-248">See Also</span></span>
