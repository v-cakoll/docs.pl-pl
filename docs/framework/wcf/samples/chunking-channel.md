---
title: Kanał dzielący na fragmenty
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 7b436e2ce708a122a7eae3b07ad01515fb2dce96
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463979"
---
# <a name="chunking-channel"></a><span data-ttu-id="7f9a0-102">Kanał dzielący na fragmenty</span><span class="sxs-lookup"><span data-stu-id="7f9a0-102">Chunking Channel</span></span>

<span data-ttu-id="7f9a0-103">Podczas wysyłania dużych wiadomości przy użyciu programu Windows Communication Foundation (WCF), często jest pożądane, aby ograniczyć ilość pamięci używanej do buforowania tych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="7f9a0-104">Jednym z możliwych rozwiązań jest przesyłanie strumieniowe treści wiadomości (przy założeniu, że większość danych znajduje się w treści).</span><span class="sxs-lookup"><span data-stu-id="7f9a0-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="7f9a0-105">Jednak niektóre protokoły wymagają buforowania całej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="7f9a0-106">Niezawodne wiadomości i zabezpieczenia to dwa takie przykłady.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="7f9a0-107">Innym możliwym rozwiązaniem jest podzielenie dużych wiadomości na mniejsze wiadomości o nazwie fragmenty, wysłać te fragmenty jeden fragment na raz i odtworzyć dużą wiadomość po stronie odbierającej.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="7f9a0-108">Sama aplikacja może to zrobić fragmentowanie i de-chunking lub może użyć kanału niestandardowego, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="7f9a0-109">Przykład kanału fragmentowania pokazuje, jak niestandardowy protokół lub warstwowy kanał może służyć do tworzenia fragmentów i usuwania fragmentów dowolnie dużych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>

<span data-ttu-id="7f9a0-110">Fragmentowanie powinny być zawsze stosowane tylko po skonstruowaniu całej wiadomości, która ma zostać wysłana.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="7f9a0-111">Kanał fragmentowania powinien być zawsze warstwowy poniżej kanału zabezpieczeń i niezawodnego kanału sesji.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>

> [!NOTE]
> <span data-ttu-id="7f9a0-112">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7f9a0-113">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7f9a0-114">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7f9a0-115">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7f9a0-116">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="7f9a0-117">Fragmentowanie założeń i ograniczeń kanału</span><span class="sxs-lookup"><span data-stu-id="7f9a0-117">Chunking Channel Assumptions and Limitations</span></span>

### <a name="message-structure"></a><span data-ttu-id="7f9a0-118">Struktura wiadomości</span><span class="sxs-lookup"><span data-stu-id="7f9a0-118">Message Structure</span></span>

<span data-ttu-id="7f9a0-119">Kanał fragmentowania zakłada następującą strukturę komunikatów dla wiadomości, które mają być fragmentowane:</span><span class="sxs-lookup"><span data-stu-id="7f9a0-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>

```xml
<soap:Envelope>
  <!-- headers -->
  <soap:Body>
    <operationElement>
      <paramElement>data to be chunked</paramElement>
    </operationElement>
  </soap:Body>
</soap:Envelope>
```

<span data-ttu-id="7f9a0-120">Podczas korzystania z ServiceModel, operacje umowy, które mają 1 parametr wejściowy są zgodne z tym kształtem komunikatu dla ich komunikatu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="7f9a0-121">Podobnie operacje kontraktowe, które mają 1 parametr wyjściowy lub zwraca wartość są zgodne z tym kształtem komunikatu dla ich komunikatu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="7f9a0-122">Poniżej przedstawiono przykłady takich operacji:</span><span class="sxs-lookup"><span data-stu-id="7f9a0-122">The following are examples of such operations:</span></span>

```csharp
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

### <a name="sessions"></a><span data-ttu-id="7f9a0-123">Sesje</span><span class="sxs-lookup"><span data-stu-id="7f9a0-123">Sessions</span></span>

<span data-ttu-id="7f9a0-124">Kanał fragmentowania wymaga wiadomości, które mają być dostarczane dokładnie raz, w zamówionej dostarczania wiadomości (fragmentów).</span><span class="sxs-lookup"><span data-stu-id="7f9a0-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="7f9a0-125">Oznacza to, że podstawowy stos kanału musi być sessionful.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="7f9a0-126">Sesje mogą być dostarczane przez transport (na przykład transport TCP) lub przez kanał protokołu sesyjnego (na przykład kanał ReliableSession).</span><span class="sxs-lookup"><span data-stu-id="7f9a0-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>

### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="7f9a0-127">Asynchroniczne wysyłanie i odbieranie</span><span class="sxs-lookup"><span data-stu-id="7f9a0-127">Asynchronous Send and Receive</span></span>

<span data-ttu-id="7f9a0-128">Metody asynchroniczne wysyłania i odbierania nie są implementowane w tej wersji przykładu kanału fragmentowania.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>

## <a name="chunking-protocol"></a><span data-ttu-id="7f9a0-129">Protokół fragmentowania</span><span class="sxs-lookup"><span data-stu-id="7f9a0-129">Chunking Protocol</span></span>

<span data-ttu-id="7f9a0-130">Kanał fragmentowania definiuje protokół, który wskazuje początek i koniec serii fragmentów, a także numer sekwencyjny każdego fragmentu.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="7f9a0-131">Następujące trzy przykładowe komunikaty pokazują wiadomości początkowe, fragmentowe i końcowe za pomocą komentarzy opisujących kluczowe aspekty każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>

### <a name="start-message"></a><span data-ttu-id="7f9a0-132">Rozpocznij wiadomość</span><span class="sxs-lookup"><span data-stu-id="7f9a0-132">Start Message</span></span>

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

### <a name="chunk-message"></a><span data-ttu-id="7f9a0-133">Wiadomość fragmentu</span><span class="sxs-lookup"><span data-stu-id="7f9a0-133">Chunk Message</span></span>

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

### <a name="end-message"></a><span data-ttu-id="7f9a0-134">Zakończ wiadomość</span><span class="sxs-lookup"><span data-stu-id="7f9a0-134">End Message</span></span>

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

## <a name="chunking-channel-architecture"></a><span data-ttu-id="7f9a0-135">Architektura kanału fragmentowania</span><span class="sxs-lookup"><span data-stu-id="7f9a0-135">Chunking Channel Architecture</span></span>

<span data-ttu-id="7f9a0-136">Chunking kanał `IDuplexSessionChannel` jest, który na wysokim poziomie, następuje typowe architektury kanału.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="7f9a0-137">`ChunkingBindingElement` Istnieje, że można `ChunkingChannelFactory` zbudować `ChunkingChannelListener`i .</span><span class="sxs-lookup"><span data-stu-id="7f9a0-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="7f9a0-138">Tworzy `ChunkingChannelFactory` wystąpienia, `ChunkingChannel` gdy jest proszony.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="7f9a0-139">Tworzy `ChunkingChannelListener` `ChunkingChannel` wystąpienia, gdy nowy kanał wewnętrzny jest akceptowany.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="7f9a0-140">Sam `ChunkingChannel` jest odpowiedzialny za wysyłanie i odbieranie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>

<span data-ttu-id="7f9a0-141">Na następnym poziomie `ChunkingChannel` w dół, opiera się na kilka składników do zaimplementowania protokołu fragmentowania.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="7f9a0-142">Po stronie wysyłania kanał używa <xref:System.Xml.XmlDictionaryWriter> niestandardowego wywoływanego, `ChunkingWriter` który wykonuje rzeczywiste fragmentowanie.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-142">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="7f9a0-143">`ChunkingWriter`używa kanału wewnętrznego bezpośrednio do wysyłania fragmentów.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="7f9a0-144">Korzystanie z `XmlDictionaryWriter` niestandardowego pozwala nam wysyłać fragmenty, ponieważ duża treść oryginalnej wiadomości jest zapisywana.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="7f9a0-145">Oznacza to, że nie buforujemy całej oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-145">This means we do not buffer the entire original message.</span></span>

![Diagram, który pokazuje architekturę wysyłania kanału fragmentowania.](./media/chunking-channel/chunking-channel-send.gif)

<span data-ttu-id="7f9a0-147">Po stronie odbierania `ChunkingChannel` pobiera wiadomości z kanału wewnętrznego <xref:System.Xml.XmlDictionaryReader> i `ChunkingReader`przekazuje je do niestandardowego o nazwie , który odtwarza oryginalną wiadomość z przychodzących fragmentów.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="7f9a0-148">`ChunkingChannel`zawija `ChunkingReader` to `Message` w `ChunkingMessage` niestandardowej implementacji o nazwie i zwraca ten komunikat do warstwy powyżej.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="7f9a0-149">Ta `ChunkingReader` kombinacja `ChunkingMessage` i pozwala nam odkrztuszać oryginalną treść wiadomości, ponieważ jest ona odczytywana przez warstwę powyżej, zamiast buforowania całej oryginalnej treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="7f9a0-150">`ChunkingReader`ma kolejkę, w której buforuje przychodzące fragmenty do maksymalnej konfigurowalnej liczby buforowanych fragmentów.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="7f9a0-151">Po osiągnięciu tego maksymalnego limitu czytelnik czeka na wiadomości, które mają być opróżniane z kolejki przez warstwę powyżej (to znaczy, po prostu odczytu z oryginalnej treści wiadomości) lub do osiągnięcia limitu czasu maksymalnego odbioru.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>

![Diagram, który pokazuje architekturę odbierania fragmentów kanału.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a><span data-ttu-id="7f9a0-153">Model programowania fragmentów</span><span class="sxs-lookup"><span data-stu-id="7f9a0-153">Chunking Programming Model</span></span>

<span data-ttu-id="7f9a0-154">Deweloperzy usług można określić, które wiadomości `ChunkingBehavior` mają być fragmentowane przez zastosowanie atrybutu do operacji w ramach umowy.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="7f9a0-155">Atrybut udostępnia `AppliesTo` właściwość, która umożliwia deweloperowi określić, czy fragmentowanie ma zastosowanie do komunikatu wejściowego, komunikat wyjściowy lub obu.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="7f9a0-156">W poniższym przykładzie `ChunkingBehavior` pokazano użycie atrybutu:</span><span class="sxs-lookup"><span data-stu-id="7f9a0-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>

```csharp
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

<span data-ttu-id="7f9a0-157">Z tego modelu `ChunkingBindingElement` programowania kompiluje listę identyfikatorów URI akcji, które identyfikują komunikaty, które mają być fragmentaryzowane.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="7f9a0-158">Akcja każdej wiadomości wychodzącej jest porównywana z tą listą, aby ustalić, czy wiadomość powinna być fragmentowana lub wysłana bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>

## <a name="implementing-the-send-operation"></a><span data-ttu-id="7f9a0-159">Implementowanie operacji wysyłania</span><span class="sxs-lookup"><span data-stu-id="7f9a0-159">Implementing the Send Operation</span></span>

<span data-ttu-id="7f9a0-160">Na wysokim poziomie Wyślij operacji najpierw sprawdza, czy wychodzące wiadomości muszą być fragmentowane, a jeśli nie, wysyła wiadomość bezpośrednio przy użyciu kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>

<span data-ttu-id="7f9a0-161">Jeśli wiadomość musi być fragmentowany, `ChunkingWriter` Wyślij `WriteBodyContents` tworzy nowy i wywołuje `ChunkingWriter`wiadomość wychodzącą przekazując go w ten sposób .</span><span class="sxs-lookup"><span data-stu-id="7f9a0-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="7f9a0-162">Następnie `ChunkingWriter` nie fragmentowanie wiadomości (w tym kopiowanie nagłówków oryginalnej wiadomości do początkowej wiadomości fragmentu) i wysyła fragmenty przy użyciu kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>

<span data-ttu-id="7f9a0-163">Kilka szczegółów warto zauważyć:</span><span class="sxs-lookup"><span data-stu-id="7f9a0-163">A few details worth noting:</span></span>

- <span data-ttu-id="7f9a0-164">Wyślij pierwsze `ThrowIfDisposedOrNotOpened` połączenia, `CommunicationState` aby upewnić się, że jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>

- <span data-ttu-id="7f9a0-165">Wysyłanie jest synchronizowane, dzięki czemu dla każdej sesji można wysłać tylko jedną wiadomość.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="7f9a0-166">Istnieje `ManualResetEvent` nazwa, `sendingDone` która jest resetowana, gdy wysyłana jest wiadomość fragmentowana.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="7f9a0-167">Po wysłaniu komunikatu o fragmencie końcowym to zdarzenie jest ustawione.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="7f9a0-168">Send Metoda czeka na to zdarzenie, które ma zostać ustawione, zanim spróbuje wysłać wiadomość wychodzącą.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>

- <span data-ttu-id="7f9a0-169">Wyślij blokuje, `CommunicationObject.ThisLock` aby zapobiec zsynchronizowanym zmianom stanu podczas wysyłania.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="7f9a0-170">Zobacz <xref:System.ServiceModel.Channels.CommunicationObject> dokumentację, aby <xref:System.ServiceModel.Channels.CommunicationObject> uzyskać więcej informacji na temat stanów i komputera stanu.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>

- <span data-ttu-id="7f9a0-171">Limit czasu przekazany do wysyłania jest używany jako limit czasu dla całej operacji wysyłania, która obejmuje wysyłanie wszystkich fragmentów.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>

- <span data-ttu-id="7f9a0-172">Niestandardowy <xref:System.Xml.XmlDictionaryWriter> projekt został wybrany, aby uniknąć buforowania całego oryginalnego obiektu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-172">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="7f9a0-173">Gdybyśmy mieli dostać <xref:System.Xml.XmlDictionaryReader> na ciele `message.GetReaderAtBodyContents` za pomocą całego ciała byłoby buforowane.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-173">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="7f9a0-174">Zamiast tego mamy zwyczaj, <xref:System.Xml.XmlDictionaryWriter> który `message.WriteBodyContents`jest przekazywany do .</span><span class="sxs-lookup"><span data-stu-id="7f9a0-174">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="7f9a0-175">Jak komunikat wywołuje WriteBase64 na modułu zapisującego, moduł zapisujący pakiety do fragmentów do wiadomości i wysyła je przy użyciu kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="7f9a0-176">WriteBase64 blokuje, dopóki fragment nie zostanie wysłany.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-176">WriteBase64 blocks until the chunk is sent.</span></span>

## <a name="implementing-the-receive-operation"></a><span data-ttu-id="7f9a0-177">Wdrażanie operacji odbierania</span><span class="sxs-lookup"><span data-stu-id="7f9a0-177">Implementing the Receive Operation</span></span>

<span data-ttu-id="7f9a0-178">Na wysokim poziomie Receive operacji najpierw sprawdza, czy `null` wiadomość przychodząca `ChunkingAction`nie jest i że jego działanie jest .</span><span class="sxs-lookup"><span data-stu-id="7f9a0-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="7f9a0-179">Jeśli nie spełnia obu kryteriów, wiadomość jest zwracana bez zmian z Receive.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="7f9a0-180">W przeciwnym razie `ChunkingReader` Receive tworzy `ChunkingMessage` nowy i nowy `GetNewChunkingMessage`owinięty wokół niego (przez wywołanie ).</span><span class="sxs-lookup"><span data-stu-id="7f9a0-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="7f9a0-181">Przed zwróceniem `ChunkingMessage`tego nowego , Receive używa `ReceiveChunkLoop`wątku `innerChannel.Receive` wątku do wykonania , który `ChunkingReader` wywołuje w pętli i przekazuje fragmenty do momentu odebrania komunikatu fragmentu końcowego lub zostanie trafiony limit czasu odbioru.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>

<span data-ttu-id="7f9a0-182">Kilka szczegółów warto zauważyć:</span><span class="sxs-lookup"><span data-stu-id="7f9a0-182">A few details worth noting:</span></span>

- <span data-ttu-id="7f9a0-183">Podobnie jak Wyślij, `ThrowIfDisposedOrNotOepned` odbierz pierwsze połączenia, aby upewnić się, `CommunicationState` że jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>

- <span data-ttu-id="7f9a0-184">Receive jest również synchronizowany, dzięki czemu można odbierać tylko jedną wiadomość naraz z sesji.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="7f9a0-185">Jest to szczególnie ważne, ponieważ po odebraniu komunikatu fragmentu początkowego wszystkie kolejne odebrane wiadomości powinny być fragmentami w tej nowej sekwencji fragmentów, dopóki nie zostanie odebrana komunikat o fragmencie końcowym.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="7f9a0-186">Receive nie może pobierać wiadomości z kanału wewnętrznego, dopóki nie zostaną odebrane wszystkie fragmenty, które należą do wiadomości, która jest obecnie usuwana z fragmentami.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="7f9a0-187">Aby to osiągnąć, Receive `ManualResetEvent` `currentMessageCompleted`używa nazwanego , który jest ustawiany po odebraniu komunikatu o fragmencie końcowym i zresetowaniu po odebraniu nowej wiadomości fragmentu początkowego.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>

- <span data-ttu-id="7f9a0-188">W przeciwieństwie do Wysyłania, Odbierania nie zapobiega zsynchronizowanych przejściach stanu podczas odbierania.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="7f9a0-189">Na przykład Close można wywołać podczas odbierania i czeka, aż oczekujące odbieranie oryginalnej wiadomości zostanie zakończona lub zostanie osiągnięta określona wartość limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>

- <span data-ttu-id="7f9a0-190">Limit czasu przekazany do receive jest używany jako limit czasu dla całej operacji odbierania, która obejmuje odbieranie wszystkich fragmentów.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>

- <span data-ttu-id="7f9a0-191">Jeśli warstwa, która zużywa wiadomość zużywa treść wiadomości z szybkością niższą niż `ChunkingReader` szybkość przychodzących wiadomości fragmentów, `ChunkingBindingElement.MaxBufferedChunks`buforuje te przychodzące fragmenty do limitu określonego przez program .</span><span class="sxs-lookup"><span data-stu-id="7f9a0-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="7f9a0-192">Po osiągnięciu tego limitu nie więcej fragmentów są pobierane z dolnej warstwy, dopóki nie zostanie wykorzystany buforowany fragment lub limit czasu odbioru zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>

## <a name="communicationobject-overrides"></a><span data-ttu-id="7f9a0-193">Przesłonięcia znacznicy komunikacyjnej</span><span class="sxs-lookup"><span data-stu-id="7f9a0-193">CommunicationObject Overrides</span></span>

### <a name="onopen"></a><span data-ttu-id="7f9a0-194">Onopen</span><span class="sxs-lookup"><span data-stu-id="7f9a0-194">OnOpen</span></span>

<span data-ttu-id="7f9a0-195">`OnOpen`wezwań `innerChannel.Open` do otwarcia kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>

### <a name="onclose"></a><span data-ttu-id="7f9a0-196">Onclose</span><span class="sxs-lookup"><span data-stu-id="7f9a0-196">OnClose</span></span>

<span data-ttu-id="7f9a0-197">`OnClose`pierwsze `stopReceive` zestawy, aby `true` `ReceiveChunkLoop` zasygnalizować oczekujące zatrzymanie.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="7f9a0-198">Następnie czeka na `receiveStopped` <xref:System.Threading.ManualResetEvent>, który jest `ReceiveChunkLoop` ustawiany po zatrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-198">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="7f9a0-199">Przy `ReceiveChunkLoop` założeniu, że zatrzymuje `OnClose` `innerChannel.Close` się w określonym limit czasu, wywołuje z pozostałym limit czasu.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>

### <a name="onabort"></a><span data-ttu-id="7f9a0-200">Onabort</span><span class="sxs-lookup"><span data-stu-id="7f9a0-200">OnAbort</span></span>

<span data-ttu-id="7f9a0-201">`OnAbort`wzywa `innerChannel.Abort` do przerwania kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="7f9a0-202">Jeśli istnieje oczekujące `ReceiveChunkLoop` pobiera wyjątek `innerChannel.Receive` od oczekującego wywołania.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>

### <a name="onfaulted"></a><span data-ttu-id="7f9a0-203">OnFaulted ( OnFaulted )</span><span class="sxs-lookup"><span data-stu-id="7f9a0-203">OnFaulted</span></span>

<span data-ttu-id="7f9a0-204">Nie `ChunkingChannel` wymaga specjalnego zachowania, gdy kanał `OnFaulted` jest uszkodzony, więc nie jest zastępowany.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>

## <a name="implementing-channel-factory"></a><span data-ttu-id="7f9a0-205">Wdrożenie fabryki kanałów</span><span class="sxs-lookup"><span data-stu-id="7f9a0-205">Implementing Channel Factory</span></span>

<span data-ttu-id="7f9a0-206">Jest `ChunkingChannelFactory` odpowiedzialny za tworzenie wystąpień `ChunkingDuplexSessionChannel` i dla kaskadowych przejść stanu do fabryki kanałów wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>

<span data-ttu-id="7f9a0-207">`OnCreateChannel`wykorzystuje fabrykę kanałów wewnętrznych `IDuplexSessionChannel` do utworzenia kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="7f9a0-208">Następnie tworzy nowy `ChunkingDuplexSessionChannel` przekazując go tego kanału wewnętrznego wraz z listą akcji wiadomości, które mają być fragmentowane i maksymalną liczbę fragmentów do buforowania po otrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="7f9a0-209">Lista akcji wiadomości, które mają być fragmentowane i maksymalna liczba `ChunkingChannelFactory` fragmentów do buforu są dwa parametry przekazywane do jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="7f9a0-210">W sekcji `ChunkingBindingElement` opisano, skąd pochodzą te wartości.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>

<span data-ttu-id="7f9a0-211">The `OnOpen` `OnClose`, `OnAbort` i ich odpowiedniki asynchroniczne wywołać odpowiednią metodę przejścia stanu w fabryce kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>

## <a name="implementing-channel-listener"></a><span data-ttu-id="7f9a0-212">Implementowanie odbiornika kanałów</span><span class="sxs-lookup"><span data-stu-id="7f9a0-212">Implementing Channel Listener</span></span>

<span data-ttu-id="7f9a0-213">Jest `ChunkingChannelListener` otoka wokół odbiornika kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="7f9a0-214">Jego główną funkcją, oprócz delegowania wywołań do `ChunkingDuplexSessionChannels` tego odbiornika kanału wewnętrznego, jest zawijanie nowych wokół kanałów akceptowanych z odbiornika kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="7f9a0-215">Odbywa się `OnAcceptChannel` to `OnEndAcceptChannel`w i .</span><span class="sxs-lookup"><span data-stu-id="7f9a0-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="7f9a0-216">Nowo utworzony `ChunkingDuplexSessionChannel` jest przekazywany kanał wewnętrzny wraz z innymi parametrami wcześniej opisane.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>

## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="7f9a0-217">Implementowanie elementu wiążącego i powiązania</span><span class="sxs-lookup"><span data-stu-id="7f9a0-217">Implementing Binding Element and Binding</span></span>

<span data-ttu-id="7f9a0-218">`ChunkingBindingElement`jest odpowiedzialny za `ChunkingChannelFactory` tworzenie `ChunkingChannelListener`i .</span><span class="sxs-lookup"><span data-stu-id="7f9a0-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="7f9a0-219">Sprawdza, `ChunkingBindingElement` czy `CanBuildChannelFactory` \<T w T `CanBuildChannelListener` \<> i T> `IDuplexSessionChannel` jest typu (tylko kanał obsługiwany przez kanał fragmentowania) i czy inne elementy powiązania w powiązaniu obsługuje ten typ kanału.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>

<span data-ttu-id="7f9a0-220">`BuildChannelFactory`\<T> najpierw sprawdza, czy żądany typ kanału może być zbudowany, a następnie pobiera listę akcji wiadomości, które mają być fragmentowane.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="7f9a0-221">Aby uzyskać więcej informacji, zobacz następującą sekcję.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-221">For more information, see the following section.</span></span> <span data-ttu-id="7f9a0-222">Następnie tworzy nowy `ChunkingChannelFactory` przekazując go wewnętrznej fabryki `context.BuildInnerChannelFactory<IDuplexSessionChannel>`kanału (jako zwrócone z ), lista akcji wiadomości i maksymalna liczba fragmentów do bufora.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="7f9a0-223">Maksymalna liczba fragmentów pochodzi z `MaxBufferedChunks` właściwości `ChunkingBindingElement`o nazwie exposed przez .</span><span class="sxs-lookup"><span data-stu-id="7f9a0-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>

<span data-ttu-id="7f9a0-224">`BuildChannelListener<T>`ma podobną implementację `ChunkingChannelListener` do tworzenia i przekazywania go odbiornika kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>

<span data-ttu-id="7f9a0-225">Istnieje przykład powiązania zawarte w tym `TcpChunkingBinding`przykładzie o nazwie .</span><span class="sxs-lookup"><span data-stu-id="7f9a0-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="7f9a0-226">To powiązanie składa się `TcpTransportBindingElement` `ChunkingBindingElement`z dwóch elementów wiążących: i .</span><span class="sxs-lookup"><span data-stu-id="7f9a0-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="7f9a0-227">Oprócz uwidaczniania `MaxBufferedChunks` właściwości powiązanie ustawia również `TcpTransportBindingElement` niektóre właściwości, `MaxReceivedMessageSize` takie jak `ChunkingUtils.ChunkSize` (ustawia go na + 100 KB bajtów dla nagłówków).</span><span class="sxs-lookup"><span data-stu-id="7f9a0-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>

<span data-ttu-id="7f9a0-228">`TcpChunkingBinding`implementuje `IBindingRuntimePreferences` i zwraca true `ReceiveSynchronously` z metody wskazującej, że implementowane są tylko wywołania synchroniczne odbieranie.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>

### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="7f9a0-229">Określanie, które wiadomości mają być fragmentowe</span><span class="sxs-lookup"><span data-stu-id="7f9a0-229">Determining Which Messages To Chunk</span></span>

<span data-ttu-id="7f9a0-230">Fragmenty kanału fragmenty tylko wiadomości zidentyfikowane `ChunkingBehavior` za pośrednictwem atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="7f9a0-231">Klasa `ChunkingBehavior` implementuje `IOperationBehavior` i jest implementowana `AddBindingParameter` przez wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="7f9a0-232">W tej `ChunkingBehavior` metodzie sprawdza wartość `AppliesTo` jego`InMessage`właściwości `OutMessage` ( lub obu), aby określić, które komunikaty powinny być fragmentowane.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="7f9a0-233">Następnie pobiera akcję każdej z tych wiadomości (z `OperationDescription`messages collection on ) i dodaje go `ChunkingBindingParameter`do kolekcji ciągów zawartych w wystąpieniu .</span><span class="sxs-lookup"><span data-stu-id="7f9a0-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="7f9a0-234">Następnie dodaje `ChunkingBindingParameter` to do `BindingParameterCollection`dostarczonego .</span><span class="sxs-lookup"><span data-stu-id="7f9a0-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>

<span data-ttu-id="7f9a0-235">To `BindingParameterCollection` jest przekazywane `BindingContext` wewnątrz do każdego elementu wiązania w powiązanie, gdy ten element wiązania tworzy fabryki kanału lub odbiornika kanału.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="7f9a0-236">Realizacji `ChunkingBindingElement` `BuildChannelFactory<T>` `BuildChannelListener<T>` i wyciągnąć `ChunkingBindingParameter` to z `BindingContext’`s `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="7f9a0-237">Zbiór działań zawartych `ChunkingBindingParameter` w a następnie `ChunkingChannelFactory` `ChunkingChannelListener`jest przekazywana do `ChunkingDuplexSessionChannel`lub , który z kolei przekazuje go do .</span><span class="sxs-lookup"><span data-stu-id="7f9a0-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>

## <a name="running-the-sample"></a><span data-ttu-id="7f9a0-238">Uruchamianie próbki</span><span class="sxs-lookup"><span data-stu-id="7f9a0-238">Running the Sample</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7f9a0-239">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="7f9a0-239">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="7f9a0-240">Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-240">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="7f9a0-241">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f9a0-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="7f9a0-242">Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f9a0-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="7f9a0-243">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7f9a0-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

5. <span data-ttu-id="7f9a0-244">Najpierw uruchom program Service.exe, a następnie uruchom program Client.exe i obserwuj oba okna konsoli w celu uzyskania danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>

<span data-ttu-id="7f9a0-245">Podczas uruchamiania próbki oczekuje się następującego wyjścia.</span><span class="sxs-lookup"><span data-stu-id="7f9a0-245">When running the sample, the following output is expected.</span></span>

<span data-ttu-id="7f9a0-246">Klient:</span><span class="sxs-lookup"><span data-stu-id="7f9a0-246">Client:</span></span>

```console
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

<span data-ttu-id="7f9a0-247">Serwer:</span><span class="sxs-lookup"><span data-stu-id="7f9a0-247">Server:</span></span>

```console
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
