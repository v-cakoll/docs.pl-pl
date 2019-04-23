---
title: Kanał dzielący na fragmenty
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: a60cae7ad3dcfdaa139b8be974ed2d3996b5211d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302702"
---
# <a name="chunking-channel"></a><span data-ttu-id="d0dc4-102">Kanał dzielący na fragmenty</span><span class="sxs-lookup"><span data-stu-id="d0dc4-102">Chunking Channel</span></span>
<span data-ttu-id="d0dc4-103">Podczas wysyłania dużych komunikatów za pomocą usługi Windows Communication Foundation (WCF), często jest pożądane, aby ograniczyć ilość pamięci używana do buforowania te komunikaty.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="d0dc4-104">Jedno z możliwych rozwiązań jest przesyłanie strumieniowe treść wiadomości (przy założeniu, że duża część danych znajduje się w treści).</span><span class="sxs-lookup"><span data-stu-id="d0dc4-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="d0dc4-105">Jednak niektóre protokoły wymagają buforowanie cały komunikat.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="d0dc4-106">Niezawodna obsługa komunikatów i zabezpieczenia są dwa takie przykłady.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="d0dc4-107">Inne możliwe rozwiązanie jest dzielenia dużych wiadomość na mniejsze wiadomości o nazwie fragmentów, Wyślij jednym fragmencie tych fragmentów w danym momencie i odtworzenia dużych komunikatów po stronie odbierającej.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="d0dc4-108">Sama aplikacja może wykonać tego segmentu i cofnąć segmentu lub użyć niestandardowy kanał to zrobić.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="d0dc4-109">Segmentu przykład kanału pokazuje, jak niestandardowego protokołu lub warstwowej kanału może służyć do segmentu i cofnąć segmentu arbitralnie dużych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>  
  
 <span data-ttu-id="d0dc4-110">Dzielący na fragmenty należy zawsze można zastosować tylko wtedy, gdy został skonstruowany cały komunikat do wysłania.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="d0dc4-111">Kanał segmentu powinien zawsze warstwowe w poniżej kanału zabezpieczeń i kanał niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0dc4-112">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d0dc4-113">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d0dc4-114">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="d0dc4-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d0dc4-115">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d0dc4-116">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`  
  
## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="d0dc4-117">Segmentu kanału założenia i ograniczenia</span><span class="sxs-lookup"><span data-stu-id="d0dc4-117">Chunking Channel Assumptions and Limitations</span></span>  
  
### <a name="message-structure"></a><span data-ttu-id="d0dc4-118">Struktura wiadomości</span><span class="sxs-lookup"><span data-stu-id="d0dc4-118">Message Structure</span></span>  
 <span data-ttu-id="d0dc4-119">Kanał segmentu zakłada następującą strukturę komunikatu dla komunikatów jest podzielony:</span><span class="sxs-lookup"><span data-stu-id="d0dc4-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>  
  
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
  
 <span data-ttu-id="d0dc4-120">Korzystając z modelu ServiceModel, kontrakt operacji, które mają 1 parametr wejściowy jest zgodne z tym kształtem komunikatu dla ich komunikat wejściowy.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="d0dc4-121">Podobnie operacji kontraktu, które mają 1 parametru wyjściowego lub wartości zwracanej zgodne z tym kształtem komunikatu dla ich komunikatu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="d0dc4-122">Poniżej przedstawiono przykłady takich operacji:</span><span class="sxs-lookup"><span data-stu-id="d0dc4-122">The following are examples of such operations:</span></span>  
  
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
  
### <a name="sessions"></a><span data-ttu-id="d0dc4-123">Kategoria Sessions</span><span class="sxs-lookup"><span data-stu-id="d0dc4-123">Sessions</span></span>  
 <span data-ttu-id="d0dc4-124">Kanał segmentu wymaga wiadomości dostarczanych tylko raz w uporządkowanej dostarczania wiadomości (fragmentów).</span><span class="sxs-lookup"><span data-stu-id="d0dc4-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="d0dc4-125">Oznacza to, że podstawowy stos kanału musi być sesji.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="d0dc4-126">Sesje mogą otrzymywać przez transportu (na przykład warstwy transportowej TCP) lub kanału sesji protokołu (na przykład, ReliableSession kanał).</span><span class="sxs-lookup"><span data-stu-id="d0dc4-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>  
  
### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="d0dc4-127">Asynchroniczne wysyłanie i odbieranie</span><span class="sxs-lookup"><span data-stu-id="d0dc4-127">Asynchronous Send and Receive</span></span>  
 <span data-ttu-id="d0dc4-128">Asynchroniczne wysyłanie i odbieranie metod nie są implementowane przez tę wersję segmentu przykład kanału.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>  
  
## <a name="chunking-protocol"></a><span data-ttu-id="d0dc4-129">Protokół segmentu</span><span class="sxs-lookup"><span data-stu-id="d0dc4-129">Chunking Protocol</span></span>  
 <span data-ttu-id="d0dc4-130">Kanał segmentu Określa protokół, który wskazuje początek i koniec szereg fragmenty, a także numer sekwencyjny każdego fragmentu.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="d0dc4-131">Następujące komunikaty trzy przykładowe pokazują, uruchamianie i fragmentów i na końcu komunikatów za pomocą komentarzy opisujących kluczowych aspektów każdej.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>  
  
### <a name="start-message"></a><span data-ttu-id="d0dc4-132">Komunikat rozpoczęcia</span><span class="sxs-lookup"><span data-stu-id="d0dc4-132">Start Message</span></span>  
  
```xml  
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"   
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">  
  <s:Header>  
<!--Original message action is replaced with a chunking-specific action. -->  
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
  
### <a name="chunk-message"></a><span data-ttu-id="d0dc4-133">Komunikat fragmentów</span><span class="sxs-lookup"><span data-stu-id="d0dc4-133">Chunk Message</span></span>  
  
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
  
### <a name="end-message"></a><span data-ttu-id="d0dc4-134">Komunikat zakończenia</span><span class="sxs-lookup"><span data-stu-id="d0dc4-134">End Message</span></span>  
  
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
  
## <a name="chunking-channel-architecture"></a><span data-ttu-id="d0dc4-135">Architektura kanał dzielący na fragmenty</span><span class="sxs-lookup"><span data-stu-id="d0dc4-135">Chunking Channel Architecture</span></span>  
 <span data-ttu-id="d0dc4-136">Kanał segmentu jest `IDuplexSessionChannel` , na wysokim poziomie następujący architektury typowego kanału.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="d0dc4-137">Brak `ChunkingBindingElement` , można tworzyć `ChunkingChannelFactory` i `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="d0dc4-138">`ChunkingChannelFactory` Tworzy wystąpienia `ChunkingChannel` gdy otrzyma monit.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="d0dc4-139">`ChunkingChannelListener` Tworzy wystąpienia `ChunkingChannel` po zaakceptowaniu nowy kanał wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="d0dc4-140">`ChunkingChannel` Jest odpowiedzialny za wysyłanie i odbieranie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>  
  
 <span data-ttu-id="d0dc4-141">Na następnym poziomie, `ChunkingChannel` opiera się na kilka składników, aby zaimplementować protokół segmentu.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="d0dc4-142">Na stronie wysyłania kanał używa niestandardowego <xref:System.Xml.XmlDictionaryWriter> o nazwie `ChunkingWriter` wykonujący rzeczywiste segmentu.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-142">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="d0dc4-143">`ChunkingWriter` używa wewnętrznego kanału bezpośrednio, aby wysłać fragmenty.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="d0dc4-144">Za pomocą niestandardowego `XmlDictionaryWriter` pozwala nam wysyłanie fragmentów podczas zapisywania dużą porcję oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="d0dc4-145">Oznacza to, że firma Microsoft nie Buforuj całego oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-145">This means we do not buffer the entire original message.</span></span>  
  
 ![Diagram przedstawiający segmentu kanał wysyłania architektury.](./media/chunking-channel/chunking-channel-send.gif)  
  
 <span data-ttu-id="d0dc4-147">Po stronie odbierającej `ChunkingChannel` baza danych ściąga wiadomości z kanału wewnętrzny i przekazuje je do niestandardowego <xref:System.Xml.XmlDictionaryReader> o nazwie `ChunkingReader`, który reconstitutes oryginalnego komunikatu z przychodzącego fragmentów.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="d0dc4-148">`ChunkingChannel` to opakowuje `ChunkingReader` w niestandardowym `Message` wdrożenia o nazwie `ChunkingMessage` i zwraca ten komunikat do wyższej warstwie.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="d0dc4-149">Ta kombinacja `ChunkingReader` i `ChunkingMessage` pozwala nam cofnąć Podziel oryginalnego treści wiadomości, jak jest odczytywany przez warstwę powyżej, nie trzeba buforować całej treści oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="d0dc4-150">`ChunkingReader` ma kolejki, gdzie buforuje przychodzących fragmentów maksymalnie można skonfigurować maksymalną liczbę buforowanych fragmentów.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="d0dc4-151">Po osiągnięciu tego limitu maksymalnej czytnik czeka na komunikaty, aby być opróżniane z kolejki przez w wyższej warstwie (oznacza to, odczytując tylko z oryginalnego treść wiadomości) lub dopóki nie otrzymywać maksymalną osiągnięciu limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>  
  
 ![Diagram przedstawiający segmentu kanału otrzymują architektury.](./media/chunking-channel/chunking-channel-receive.gif)  
  
## <a name="chunking-programming-model"></a><span data-ttu-id="d0dc4-153">Model programowania dzielący na fragmenty</span><span class="sxs-lookup"><span data-stu-id="d0dc4-153">Chunking Programming Model</span></span>  
 <span data-ttu-id="d0dc4-154">Deweloperzy usług można określić wiadomości, które mają być podzielony przez zastosowanie `ChunkingBehavior` atrybutu do operacji w ramach umowy.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="d0dc4-155">Udostępnia atrybut `AppliesTo` właściwość, która umożliwia deweloperom określić, czy segmentu stosuje się do komunikatu wejściowego, komunikatu wyjściowego lub obu.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="d0dc4-156">W poniższym przykładzie pokazano użycie `ChunkingBehavior` atrybutu:</span><span class="sxs-lookup"><span data-stu-id="d0dc4-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>  
  
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
  
 <span data-ttu-id="d0dc4-157">W tym modelu programowania `ChunkingBindingElement` kompiluje listę akcji elementy URI identyfikujące komunikaty, aby być fragmentaryczne.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="d0dc4-158">Akcja każdej wiadomości wychodzących jest porównywana z tej listy w celu ustalenia, czy fragmentaryczne lub wysyłane bezpośrednio wiadomość.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>  
  
## <a name="implementing-the-send-operation"></a><span data-ttu-id="d0dc4-159">Implementowanie operacji wysyłania</span><span class="sxs-lookup"><span data-stu-id="d0dc4-159">Implementing the Send Operation</span></span>  
 <span data-ttu-id="d0dc4-160">Na wysokim poziomie operacji wysyłania najpierw sprawdza, czy wychodzącej wiadomości musi być podzielony, a jeśli nie, wysyła komunikat bezpośrednio przy użyciu wewnętrznego kanału.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>  
  
 <span data-ttu-id="d0dc4-161">Jeśli komunikat należy fragmentaryczne, Wyślij tworzy nową `ChunkingWriter` i wywołania `WriteBodyContents` wiadomości wychodzących przekazanie do niej to `ChunkingWriter`.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="d0dc4-162">`ChunkingWriter` , A następnie jest segmentu komunikatu (w tym kopiowanie oryginalne nagłówki wiadomości na komunikat fragmentów uruchomienia), a następnie wysyła fragmentów przy użyciu wewnętrznego kanału.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>  
  
 <span data-ttu-id="d0dc4-163">Kilka szczegóły warte odnotowania:</span><span class="sxs-lookup"><span data-stu-id="d0dc4-163">A few details worth noting:</span></span>  
  
-   <span data-ttu-id="d0dc4-164">Wyślij pierwszego wywołania `ThrowIfDisposedOrNotOpened` zapewnienie `CommunicationState` jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>  
  
-   <span data-ttu-id="d0dc4-165">Wysyłanie są synchronizowane, dzięki czemu mogą być wysyłane tylko jedna wiadomość na raz dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="d0dc4-166">Brak `ManualResetEvent` o nazwie `sendingDone` , jest resetowany po wysłaniu fragmentaryczne wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="d0dc4-167">Wysłany komunikat fragmentów zakończenia tego zdarzenia jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="d0dc4-168">Metoda wysyłania czeka dla tego zdarzenia, należy ustawić przed ponowną próbą wysłania wychodzących wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>  
  
-   <span data-ttu-id="d0dc4-169">Wyślij blokad `CommunicationObject.ThisLock` zapobiegające synchronizacji zmian stanu podczas wysyłania.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="d0dc4-170">Zobacz <xref:System.ServiceModel.Channels.CommunicationObject> dokumentacji, aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Channels.CommunicationObject> stanów i stan maszyny.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>  
  
-   <span data-ttu-id="d0dc4-171">Limit czasu, przekazana do wysyłania służy jako limit czasu operacji wysyłania całego, która obejmuje rozsyłanie wszystkich fragmentów.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>  
  
-   <span data-ttu-id="d0dc4-172">Niestandardowy <xref:System.Xml.XmlDictionaryWriter> projekt został wybrany w celu uniknięcia buforowanie całej treści oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-172">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="d0dc4-173">Gdybyśmy wybrali, aby uzyskać <xref:System.Xml.XmlDictionaryReader> w treści przy użyciu `message.GetReaderAtBodyContents` całej treści będą buforowane.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-173">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="d0dc4-174">Zamiast tego oferujemy niestandardowego <xref:System.Xml.XmlDictionaryWriter> przekazana do `message.WriteBodyContents`.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-174">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="d0dc4-175">Jak wiadomość wywołania WriteBase64 w edytorze, moduł zapisujący pakietów się fragmentów do wiadomości i wysyła je za pomocą wewnętrznego kanału.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="d0dc4-176">Bloki WriteBase64 do momentu wysłania jest fragmentów.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-176">WriteBase64 blocks until the chunk is sent.</span></span>  
  
## <a name="implementing-the-receive-operation"></a><span data-ttu-id="d0dc4-177">Implementowanie operacji odbioru</span><span class="sxs-lookup"><span data-stu-id="d0dc4-177">Implementing the Receive Operation</span></span>  
 <span data-ttu-id="d0dc4-178">Na wysokim poziomie operacji odbierania najpierw sprawdza, czy przychodzące wiadomości nie jest `null` oraz że jej działaniem jest `ChunkingAction`.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="d0dc4-179">Jeśli nie spełnia kryteriów obu, zwracany jest komunikat niezmienione Receive.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="d0dc4-180">W przeciwnym razie Receive tworzy nową `ChunkingReader` i nowy `ChunkingMessage` otaczający go (przez wywołanie metody `GetNewChunkingMessage`).</span><span class="sxs-lookup"><span data-stu-id="d0dc4-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="d0dc4-181">Przed zwróceniem przez nowych `ChunkingMessage`, Receive korzysta z puli wątków do wykonywania `ReceiveChunkLoop`, która wywołuje metodę `innerChannel.Receive` w pętli i zdejmowania rąk fragmentach, aby `ChunkingReader` aż do zakończenia fragmentów wiadomość zostaje odebrana lub zostanie osiągnięty limit czasu odbioru.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>  
  
 <span data-ttu-id="d0dc4-182">Kilka szczegóły warte odnotowania:</span><span class="sxs-lookup"><span data-stu-id="d0dc4-182">A few details worth noting:</span></span>  
  
-   <span data-ttu-id="d0dc4-183">Takie jak wysyłanie, odbieranie połączeń pierwszy `ThrowIfDisposedOrNotOepned` zapewnienie `CommunicationState` jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>  
  
-   <span data-ttu-id="d0dc4-184">Wyświetlany jest również synchronizowane, tak że tylko jeden komunikat może zostać odebrany w czasie z sesji.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="d0dc4-185">Jest to szczególnie ważne, ponieważ po otrzymaniu komunikatu fragmentów start wszystkie kolejne Odebrane komunikaty powinny być fragmentów w ramach tej nowej sekwencji fragmentów, do momentu zakończenia fragmentów wiadomość zostaje odebrana.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="d0dc4-186">Odbieranie nie ściągają komunikaty z kanału wewnętrzny, otrzymanie wszystkich fragmentów, do których należą do wiadomości, obecnie cofnąć jest podzielony.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="d0dc4-187">W tym celu odbierania używa `ManualResetEvent` o nazwie `currentMessageCompleted`, która ma wartość, gdy komunikat fragmentów zakończenia jest odbierany i zresetować po odebraniu nowej wiadomości fragmentów rozpoczęcia.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>  
  
-   <span data-ttu-id="d0dc4-188">W przeciwieństwie do wysłania Receive nie uniemożliwia zsynchronizowane stanami podczas odbierania.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="d0dc4-189">Na przykład Zamknij można wywołać podczas odbierania i czeka, aż do ukończenia oczekujących odbieranie oryginalnego komunikatu lub określona wartość limitu czasu zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>  
  
-   <span data-ttu-id="d0dc4-190">Limit czasu, przekazana do odbierania jest używany, podobnie jak limit czasu dla całego otrzymują operacji, która obejmuje dostęp do wszystkich fragmentów.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>  
  
-   <span data-ttu-id="d0dc4-191">Jeśli warstwy, która zużywa komunikat zużywa treść komunikatu z szybkością niższa niż stopa wiadomości przychodzących fragmentów, `ChunkingReader` buforuje te fragmenty przychodzących do limitu określonego przez `ChunkingBindingElement.MaxBufferedChunks`.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="d0dc4-192">Po osiągnięciu tego limitu nie ma więcej fragmentów są pobierane z niższej warstwie, aż do buforowanego fragmentów jest używany lub zostanie osiągnięty limit czasu odbioru.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>  
  
## <a name="communicationobject-overrides"></a><span data-ttu-id="d0dc4-193">CommunicationObject zastąpień</span><span class="sxs-lookup"><span data-stu-id="d0dc4-193">CommunicationObject Overrides</span></span>  
  
### <a name="onopen"></a><span data-ttu-id="d0dc4-194">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d0dc4-194">OnOpen</span></span>  
 <span data-ttu-id="d0dc4-195">`OnOpen` wywołania `innerChannel.Open` do otwierania kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>  
  
### <a name="onclose"></a><span data-ttu-id="d0dc4-196">OnClose</span><span class="sxs-lookup"><span data-stu-id="d0dc4-196">OnClose</span></span>  
 <span data-ttu-id="d0dc4-197">`OnClose` najpierw ustawia `stopReceive` do `true` celu sygnalizowania, że oczekujące `ReceiveChunkLoop` zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="d0dc4-198">Następnie czeka na zatwierdzenie `receiveStopped` <xref:System.Threading.ManualResetEvent>, która jest ustawiona, gdy `ReceiveChunkLoop` zatrzymuje.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-198">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="d0dc4-199">Zakładając, że `ReceiveChunkLoop` zatrzymuje się przed upływem określonego limitu czasu, `OnClose` wywołania `innerChannel.Close` z pozostałych przekroczeniem limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>  
  
### <a name="onabort"></a><span data-ttu-id="d0dc4-200">OnAbort</span><span class="sxs-lookup"><span data-stu-id="d0dc4-200">OnAbort</span></span>  
 <span data-ttu-id="d0dc4-201">`OnAbort` wywołania `innerChannel.Abort` przerwania wewnętrzny kanału.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="d0dc4-202">Jeśli istnieje oczekujące `ReceiveChunkLoop` otrzymuje wyjątku z Oczekujące `innerChannel.Receive` wywołania.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>  
  
### <a name="onfaulted"></a><span data-ttu-id="d0dc4-203">OnFaulted</span><span class="sxs-lookup"><span data-stu-id="d0dc4-203">OnFaulted</span></span>  
 <span data-ttu-id="d0dc4-204">`ChunkingChannel` Nie wymaga specjalnego zachowania, gdy kanał komunikacji niezawodnej, więc `OnFaulted` nie zostanie zastąpione.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>  
  
## <a name="implementing-channel-factory"></a><span data-ttu-id="d0dc4-205">Implementowanie fabryki kanałów</span><span class="sxs-lookup"><span data-stu-id="d0dc4-205">Implementing Channel Factory</span></span>  
 <span data-ttu-id="d0dc4-206">`ChunkingChannelFactory` Jest odpowiedzialny za tworzenie wystąpień `ChunkingDuplexSessionChannel` i kaskadowych stanów przejść do wewnętrzna fabryka kanałów.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>  
  
 <span data-ttu-id="d0dc4-207">`OnCreateChannel` używa wewnętrzna fabryka kanałów w celu utworzenia `IDuplexSessionChannel` wewnętrzny kanału.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="d0dc4-208">Następnie tworzy nową `ChunkingDuplexSessionChannel` przekazanie jej w tym kanale wewnętrzny wraz z listą działań komunikat na być podzielony i maksymalną liczbę fragmentów do zbuforowania podczas odbierania.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="d0dc4-209">Lista wiadomości działania, aby być podzielony i maksymalną liczbę fragmentów do buforowania są dwa parametry przekazywane do `ChunkingChannelFactory` w jego konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="d0dc4-210">W sekcji na `ChunkingBindingElement` opisuje pochodzenie tych wartości.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>  
  
 <span data-ttu-id="d0dc4-211">`OnOpen`, `OnClose`, `OnAbort` i ich odpowiedniki asynchroniczne wywoływanie odpowiednia metoda przejścia stanu na wewnętrzna fabryka kanałów.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>  
  
## <a name="implementing-channel-listener"></a><span data-ttu-id="d0dc4-212">Implementowanie odbiornika kanałów</span><span class="sxs-lookup"><span data-stu-id="d0dc4-212">Implementing Channel Listener</span></span>  
 <span data-ttu-id="d0dc4-213">`ChunkingChannelListener` Tworzy otokę wokół odbiornika kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="d0dc4-214">Jego funkcję main, oprócz delegata wywołania tego odbiornika kanału wewnętrzny jest opakowanie nowe `ChunkingDuplexSessionChannels` wokół kanały akceptowana od odbiornika kanałów wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="d0dc4-215">Jest to realizowane w `OnAcceptChannel` i `OnEndAcceptChannel`.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="d0dc4-216">Nowo utworzony `ChunkingDuplexSessionChannel` jest przekazywany wewnętrzny kanał wraz z innymi parametrami, które opisano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>  
  
## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="d0dc4-217">Implementowanie elementu powiązania i powiązania</span><span class="sxs-lookup"><span data-stu-id="d0dc4-217">Implementing Binding Element and Binding</span></span>  
 <span data-ttu-id="d0dc4-218">`ChunkingBindingElement` jest odpowiedzialny za tworzenie `ChunkingChannelFactory` i `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="d0dc4-219">`ChunkingBindingElement` Sprawdza, czy T w `CanBuildChannelFactory` \<T > i `CanBuildChannelListener` \<T > typu `IDuplexSessionChannel` (tylko kanał obsługiwane segmentu kanał) i inne elementy powiązania powiązanie obsługuje to Typ kanału.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>  
  
 <span data-ttu-id="d0dc4-220">`BuildChannelFactory`\<T > najpierw sprawdza, czy typ żądanego kanału mogą być wbudowane, a następnie pobiera listę akcji komunikat na być podzielony.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="d0dc4-221">Aby uzyskać więcej informacji zobacz następującą sekcję.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-221">For more information, see the following section.</span></span> <span data-ttu-id="d0dc4-222">Następnie tworzy nową `ChunkingChannelFactory` przekazanie do niej wewnętrzna fabryka kanałów (postaci zwracanej przez `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), lista akcji wiadomości i maksymalną liczbę fragmentów do buforowania.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="d0dc4-223">Maksymalna liczba fragmentów pochodzi z właściwością o nazwie `MaxBufferedChunks` udostępnianych przez `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>  
  
 <span data-ttu-id="d0dc4-224">`BuildChannelListener<T>` zawiera podobne implementację tworzenia `ChunkingChannelListener` i przekazanie do niej odbiornik kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>  
  
 <span data-ttu-id="d0dc4-225">Brak powiązanie przykład zawarty w tym przykładzie o nazwie `TcpChunkingBinding`.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="d0dc4-226">To powiązanie zawiera dwa elementy wiązania: `TcpTransportBindingElement` i `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="d0dc4-227">Oprócz udostępnianie `MaxBufferedChunks` właściwości powiązania ustawia również niektóre `TcpTransportBindingElement` właściwości, takie jak `MaxReceivedMessageSize` (ustawia ją na `ChunkingUtils.ChunkSize` + 100 KB bajtów dla nagłówków).</span><span class="sxs-lookup"><span data-stu-id="d0dc4-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>  
  
 <span data-ttu-id="d0dc4-228">`TcpChunkingBinding` implementuje również `IBindingRuntimePreferences` i zwraca wartość true z `ReceiveSynchronously` metoda wskazujący, że są wykonywane tylko synchroniczne wywołania Receive.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>  
  
### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="d0dc4-229">Określanie, które komunikaty dotyczące fragmentów</span><span class="sxs-lookup"><span data-stu-id="d0dc4-229">Determining Which Messages To Chunk</span></span>  
 <span data-ttu-id="d0dc4-230">Kanał segmentu chunks tylko komunikaty, które są identyfikowane za pomocą `ChunkingBehavior` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="d0dc4-231">`ChunkingBehavior` Klasy implementuje `IOperationBehavior` i jest implementowany przez wywołanie metody `AddBindingParameter` metody.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="d0dc4-232">W przypadku tej metody `ChunkingBehavior` sprawdza, czy wartość jego `AppliesTo` właściwości (`InMessage`, `OutMessage` i / lub) do określenia wiadomości, które powinny być fragmentaryczne.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="d0dc4-233">Następnie pobiera akcji każdego z tych komunikatów (z kolekcji wiadomości na `OperationDescription`) i dodaje go do kolekcji ciągów, zawartych w instancji `ChunkingBindingParameter`.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="d0dc4-234">Następnie dodaje to `ChunkingBindingParameter` podanego `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>  
  
 <span data-ttu-id="d0dc4-235">To `BindingParameterCollection` są przekazywane wewnątrz `BindingContext` do każdego elementu powiązania w powiązaniu w przypadku tego elementu powiązania kompilacji fabryki kanału lub odbiornika kanałów.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="d0dc4-236">`ChunkingBindingElement`Przez implementację `BuildChannelFactory<T>` i `BuildChannelListener<T>` tego `ChunkingBindingParameter` poza `BindingContext’`s `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="d0dc4-237">Zbiór działań zawartych w `ChunkingBindingParameter` jest następnie przekazywany do `ChunkingChannelFactory` lub `ChunkingChannelListener`, który z kolei przekazuje go do `ChunkingDuplexSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="d0dc4-238">Działa aplikacja przykładowa</span><span class="sxs-lookup"><span data-stu-id="d0dc4-238">Running the Sample</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d0dc4-239">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="d0dc4-239">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d0dc4-240">Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-240">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="d0dc4-241">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d0dc4-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="d0dc4-242">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d0dc4-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="d0dc4-243">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d0dc4-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="d0dc4-244">Uruchom najpierw Service.exe, a następnie uruchom Client.exe i obejrzyj oba okna konsoli danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>  
  
 <span data-ttu-id="d0dc4-245">Podczas uruchamiania przykładu, należy się następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="d0dc4-245">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="d0dc4-246">Klient:</span><span class="sxs-lookup"><span data-stu-id="d0dc4-246">Client:</span></span>  
  
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
  
 <span data-ttu-id="d0dc4-247">Serwer:</span><span class="sxs-lookup"><span data-stu-id="d0dc4-247">Server:</span></span>  
  
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
