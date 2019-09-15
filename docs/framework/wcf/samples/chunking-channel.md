---
title: Kanał dzielący na fragmenty
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 6bd7f1f31426c2d355b42f04ad770aac60183838
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990111"
---
# <a name="chunking-channel"></a><span data-ttu-id="e09e4-102">Kanał dzielący na fragmenty</span><span class="sxs-lookup"><span data-stu-id="e09e4-102">Chunking Channel</span></span>

<span data-ttu-id="e09e4-103">Podczas wysyłania dużych komunikatów przy użyciu Windows Communication Foundation (WCF) często pożądane jest ograniczenie ilości pamięci używanej do buforowania tych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e09e4-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="e09e4-104">Jednym z możliwych rozwiązań jest przesyłanie strumieniowe treści wiadomości (przy założeniu, że dane są zawarte w treści).</span><span class="sxs-lookup"><span data-stu-id="e09e4-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="e09e4-105">Jednak niektóre protokoły wymagają buforowania całej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e09e4-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="e09e4-106">Niezawodna obsługa komunikatów i zabezpieczeń to dwa przykłady.</span><span class="sxs-lookup"><span data-stu-id="e09e4-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="e09e4-107">Innym możliwym rozwiązaniem jest dzielenie dużej liczby wiadomości na mniejsze wiadomości o nazwie fragmenty, wysłanie tych fragmentów z jednego fragmentu jednocześnie i odbudowanie dużej wiadomości po stronie odbiorczej.</span><span class="sxs-lookup"><span data-stu-id="e09e4-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="e09e4-108">Sama aplikacja może wykonać to dzielenie i cofanie fragmentów. w tym celu można użyć niestandardowego kanału.</span><span class="sxs-lookup"><span data-stu-id="e09e4-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="e09e4-109">Przykład kanału fragmentowania pokazuje, w jaki sposób niestandardowy protokół lub kanał warstwowy może służyć do rozdzielania i defragmentowania bardzo dużych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e09e4-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>

<span data-ttu-id="e09e4-110">Dzielenie powinno być zawsze stosowane tylko po skonstruowaniu całej wysyłanej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e09e4-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="e09e4-111">Kanał fragmentowania powinien być zawsze warstwowy poniżej kanału zabezpieczeń i niezawodnego kanału sesji.</span><span class="sxs-lookup"><span data-stu-id="e09e4-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>

> [!NOTE]
> <span data-ttu-id="e09e4-112">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e09e4-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e09e4-113">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e09e4-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e09e4-114">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="e09e4-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e09e4-115">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="e09e4-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e09e4-116">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e09e4-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="e09e4-117">Założenia i ograniczenia kanału podziału</span><span class="sxs-lookup"><span data-stu-id="e09e4-117">Chunking Channel Assumptions and Limitations</span></span>

### <a name="message-structure"></a><span data-ttu-id="e09e4-118">Struktura wiadomości</span><span class="sxs-lookup"><span data-stu-id="e09e4-118">Message Structure</span></span>

<span data-ttu-id="e09e4-119">Kanał fragmentacji przyjmuje następującą strukturę komunikatów, aby można było uzyskać fragmenty komunikatów:</span><span class="sxs-lookup"><span data-stu-id="e09e4-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>

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

<span data-ttu-id="e09e4-120">W przypadku używania elementu ServiceModel operacje kontraktu z 1 parametrem wejściowym są zgodne z tym kształtem komunikatu dla wiadomości wejściowej.</span><span class="sxs-lookup"><span data-stu-id="e09e4-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="e09e4-121">Podobnie operacje kontraktu z 1 parametrem wyjściowym lub wartością zwracaną są zgodne z tym kształtem komunikatu dla wiadomości wyjściowej.</span><span class="sxs-lookup"><span data-stu-id="e09e4-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="e09e4-122">Poniżej przedstawiono przykłady takich operacji:</span><span class="sxs-lookup"><span data-stu-id="e09e4-122">The following are examples of such operations:</span></span>

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

### <a name="sessions"></a><span data-ttu-id="e09e4-123">Kategoria Sessions</span><span class="sxs-lookup"><span data-stu-id="e09e4-123">Sessions</span></span>

<span data-ttu-id="e09e4-124">Kanał fragmentowania wymaga, aby komunikaty były dostarczane dokładnie raz, w zamówionej dostawie komunikatów (fragmentów).</span><span class="sxs-lookup"><span data-stu-id="e09e4-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="e09e4-125">Oznacza to, że bazowy stos kanałów musi być sesją.</span><span class="sxs-lookup"><span data-stu-id="e09e4-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="e09e4-126">Sesje mogą być dostarczane przez transporty (na przykład transport TCP) lub kanał protokołu sesji (na przykład kanał ReliableSession).</span><span class="sxs-lookup"><span data-stu-id="e09e4-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>

### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="e09e4-127">Wysyłanie i odbieranie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="e09e4-127">Asynchronous Send and Receive</span></span>

<span data-ttu-id="e09e4-128">Asynchroniczne metody wysyłania i odbierania nie są zaimplementowane w tej wersji przykładowego kanału fragmentu.</span><span class="sxs-lookup"><span data-stu-id="e09e4-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>

## <a name="chunking-protocol"></a><span data-ttu-id="e09e4-129">Protokół fragmentaryczny</span><span class="sxs-lookup"><span data-stu-id="e09e4-129">Chunking Protocol</span></span>

<span data-ttu-id="e09e4-130">Kanał fragmentowania definiuje protokół, który wskazuje początek i koniec serii fragmentów, jak również numer sekwencyjny każdego fragmentu.</span><span class="sxs-lookup"><span data-stu-id="e09e4-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="e09e4-131">Poniższe trzy przykładowe komunikaty pokazują, jak rozpocząć, fragmenty i końcowe wiadomości z komentarzami opisującymi kluczowe aspekty każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="e09e4-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>

### <a name="start-message"></a><span data-ttu-id="e09e4-132">Rozpocznij komunikat</span><span class="sxs-lookup"><span data-stu-id="e09e4-132">Start Message</span></span>

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

### <a name="chunk-message"></a><span data-ttu-id="e09e4-133">Komunikat fragmentu</span><span class="sxs-lookup"><span data-stu-id="e09e4-133">Chunk Message</span></span>

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

### <a name="end-message"></a><span data-ttu-id="e09e4-134">Zakończ komunikat</span><span class="sxs-lookup"><span data-stu-id="e09e4-134">End Message</span></span>

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

## <a name="chunking-channel-architecture"></a><span data-ttu-id="e09e4-135">Architektura kanału podziału</span><span class="sxs-lookup"><span data-stu-id="e09e4-135">Chunking Channel Architecture</span></span>

<span data-ttu-id="e09e4-136">Kanał fragmentowania to `IDuplexSessionChannel` na wysokim poziomie, zgodnie z typową architekturą kanału.</span><span class="sxs-lookup"><span data-stu-id="e09e4-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="e09e4-137">`ChunkingBindingElement` Istnieje możliwość`ChunkingChannelFactory` utworzenia i `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="e09e4-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="e09e4-138">`ChunkingChannelFactory` Tworzy`ChunkingChannel` wystąpienia, gdy zostanie wyświetlony monit.</span><span class="sxs-lookup"><span data-stu-id="e09e4-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="e09e4-139">`ChunkingChannelListener` Tworzy`ChunkingChannel` wystąpienia po zaakceptowaniu nowego kanału wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="e09e4-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="e09e4-140">`ChunkingChannel` Sam jest odpowiedzialny za wysyłanie i otrzymywanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e09e4-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>

<span data-ttu-id="e09e4-141">Na następnym poziomie w dół `ChunkingChannel` polega na kilku składnikach w celu zaimplementowania protokołu dzielącego.</span><span class="sxs-lookup"><span data-stu-id="e09e4-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="e09e4-142">Na stronie wysyłanie kanał używa niestandardowego <xref:System.Xml.XmlDictionaryWriter> wywołana `ChunkingWriter` , który wykonuje rzeczywiste fragmenty.</span><span class="sxs-lookup"><span data-stu-id="e09e4-142">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="e09e4-143">`ChunkingWriter`używa wewnętrznego kanału bezpośrednio do wysyłania fragmentów.</span><span class="sxs-lookup"><span data-stu-id="e09e4-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="e09e4-144">Użycie niestandardowych `XmlDictionaryWriter` pozwala nam wysyłać fragmenty w miarę pisania dużej treści oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e09e4-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="e09e4-145">Oznacza to, że nie buforuje całej oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e09e4-145">This means we do not buffer the entire original message.</span></span>

![Diagram przedstawiający architekturę wysyłania kanału.](./media/chunking-channel/chunking-channel-send.gif)

<span data-ttu-id="e09e4-147">Po stronie `ChunkingChannel` odbierającej odbierane są komunikaty z kanału wewnętrznego i są one dołączane do <xref:System.Xml.XmlDictionaryReader> niestandardowego `ChunkingReader`wywołania, które polega na tym, że oryginalny komunikat zostanie utworzony z przychodzących fragmentów.</span><span class="sxs-lookup"><span data-stu-id="e09e4-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="e09e4-148">`ChunkingChannel`Zawija ten `ChunkingReader` element w niestandardowej `Message` implementacji o nazwie `ChunkingMessage` i zwraca ten komunikat do warstwy powyżej.</span><span class="sxs-lookup"><span data-stu-id="e09e4-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="e09e4-149">Ta kombinacja `ChunkingReader` i `ChunkingMessage` pozwala nam oddzielać pierwotną treść wiadomości w miarę ich odczytywania przez warstwę powyżej zamiast konieczności buforowania całej oryginalnej treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e09e4-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="e09e4-150">`ChunkingReader`ma kolejkę, w której buforuje przychodzące fragmenty do maksymalnej konfigurowalnej liczby buforowanych fragmentów.</span><span class="sxs-lookup"><span data-stu-id="e09e4-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="e09e4-151">Po osiągnięciu tego maksymalnego limitu czytnik czeka na opróżnianie komunikatów z kolejki przez warstwę powyżej (czyli przez właśnie odczytywanie z oryginalnej treści wiadomości) lub do czasu osiągnięcia maksymalnego limitu czasu odbierania.</span><span class="sxs-lookup"><span data-stu-id="e09e4-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>

![Diagram przedstawiający architekturę odbierania w kanale.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a><span data-ttu-id="e09e4-153">Model programowania fragmentarycznego</span><span class="sxs-lookup"><span data-stu-id="e09e4-153">Chunking Programming Model</span></span>

<span data-ttu-id="e09e4-154">Deweloperzy usług mogą określić, które wiadomości mają być dzielone przez zastosowanie `ChunkingBehavior` atrybutu do operacji w ramach kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e09e4-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="e09e4-155">Ten atrybut uwidacznia `AppliesTo` właściwość, która umożliwia deweloperowi określenie, czy fragmentacja dotyczy wiadomości wejściowej, wiadomości wyjściowej czy obu.</span><span class="sxs-lookup"><span data-stu-id="e09e4-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="e09e4-156">W poniższym przykładzie pokazano użycie `ChunkingBehavior` atrybutu:</span><span class="sxs-lookup"><span data-stu-id="e09e4-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>

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

<span data-ttu-id="e09e4-157">Z tego modelu `ChunkingBindingElement` programowania kompiluje listę identyfikatorów URI akcji, które identyfikują komunikaty do rozdzielenia.</span><span class="sxs-lookup"><span data-stu-id="e09e4-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="e09e4-158">Akcja każdej wiadomości wychodzącej jest porównywana z tą listą, aby określić, czy komunikat powinien zostać podzielony lub wysłany bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="e09e4-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>

## <a name="implementing-the-send-operation"></a><span data-ttu-id="e09e4-159">Implementowanie operacji wysyłania</span><span class="sxs-lookup"><span data-stu-id="e09e4-159">Implementing the Send Operation</span></span>

<span data-ttu-id="e09e4-160">Na wysokim poziomie operacja wysyłania najpierw sprawdza, czy komunikat wychodzący musi zostać podzielony i, jeśli nie, wysyła komunikat bezpośrednio przy użyciu wewnętrznego kanału.</span><span class="sxs-lookup"><span data-stu-id="e09e4-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>

<span data-ttu-id="e09e4-161">Jeśli komunikat musi zostać podzielony na fragmenty, polecenie Wyślij powoduje utworzenie `ChunkingWriter` nowego i `WriteBodyContents` wywołania komunikatu `ChunkingWriter`wychodzącego.</span><span class="sxs-lookup"><span data-stu-id="e09e4-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="e09e4-162">`ChunkingWriter` Następnie wykonuje fragmenty komunikatów (łącznie z kopiowaniem oryginalnych nagłówków wiadomości do startowego komunikatu fragmentu) i wysyła fragmenty przy użyciu wewnętrznego kanału.</span><span class="sxs-lookup"><span data-stu-id="e09e4-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>

<span data-ttu-id="e09e4-163">Oto kilka szczegółów:</span><span class="sxs-lookup"><span data-stu-id="e09e4-163">A few details worth noting:</span></span>

- <span data-ttu-id="e09e4-164">Wysyłaj pierwsze `ThrowIfDisposedOrNotOpened` wywołania, aby `CommunicationState` upewnić się, że jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="e09e4-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>

- <span data-ttu-id="e09e4-165">Wysyłanie jest synchronizowane, aby w danym momencie można było wysyłać tylko jeden komunikat dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="e09e4-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="e09e4-166">`ManualResetEvent` Istnieje nazwa `sendingDone` , która jest resetowana podczas wysyłania komunikatu z fragmentem.</span><span class="sxs-lookup"><span data-stu-id="e09e4-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="e09e4-167">Po wysłaniu komunikatu o końcowym fragmencie to zdarzenie jest ustawiane.</span><span class="sxs-lookup"><span data-stu-id="e09e4-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="e09e4-168">Metoda Send czeka na ustawienie tego zdarzenia przed podjęciem próby wysłania wiadomości wychodzącej.</span><span class="sxs-lookup"><span data-stu-id="e09e4-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>

- <span data-ttu-id="e09e4-169">Send blokuje, `CommunicationObject.ThisLock` aby zapobiec zmianom stanu zsynchronizowanych podczas wysyłania.</span><span class="sxs-lookup"><span data-stu-id="e09e4-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="e09e4-170">Zapoznaj <xref:System.ServiceModel.Channels.CommunicationObject> się z dokumentacją, aby <xref:System.ServiceModel.Channels.CommunicationObject> uzyskać więcej informacji na temat stanów i automatu Stanów.</span><span class="sxs-lookup"><span data-stu-id="e09e4-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>

- <span data-ttu-id="e09e4-171">Przekroczenie limitu czasu, który został przesłany do wysłania, jest używany jako limit czasu dla całej operacji wysyłania, który obejmuje wysłanie wszystkich fragmentów.</span><span class="sxs-lookup"><span data-stu-id="e09e4-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>

- <span data-ttu-id="e09e4-172">Projekt niestandardowy <xref:System.Xml.XmlDictionaryWriter> został wybrany tak, aby uniknąć buforowania całej oryginalnej treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e09e4-172">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="e09e4-173">Jeśli firma Microsoft musiała uzyskać <xref:System.Xml.XmlDictionaryReader> zawartość w treści przy `message.GetReaderAtBodyContents` użyciu całej treści, będzie buforowana.</span><span class="sxs-lookup"><span data-stu-id="e09e4-173">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="e09e4-174">Zamiast tego mamy niestandardowy <xref:System.Xml.XmlDictionaryWriter> , który jest przesyłany do. `message.WriteBodyContents`</span><span class="sxs-lookup"><span data-stu-id="e09e4-174">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="e09e4-175">Ponieważ komunikat wywołuje WriteBase64 na składniku zapisywania, pakiet składnika zapisywania umieszcza fragmenty w wiadomości i wysyła je przy użyciu wewnętrznego kanału.</span><span class="sxs-lookup"><span data-stu-id="e09e4-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="e09e4-176">WriteBase64 bloki do momentu wysłania fragmentu.</span><span class="sxs-lookup"><span data-stu-id="e09e4-176">WriteBase64 blocks until the chunk is sent.</span></span>

## <a name="implementing-the-receive-operation"></a><span data-ttu-id="e09e4-177">Implementowanie operacji odbierania</span><span class="sxs-lookup"><span data-stu-id="e09e4-177">Implementing the Receive Operation</span></span>

<span data-ttu-id="e09e4-178">Na wysokim poziomie operacja odbierania najpierw sprawdza, czy komunikat przychodzący nie `null` jest i czy jego Akcja `ChunkingAction`jest.</span><span class="sxs-lookup"><span data-stu-id="e09e4-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="e09e4-179">Jeśli nie spełnia obydwu kryteriów, komunikat jest zwracany niezmieniony z odbierania.</span><span class="sxs-lookup"><span data-stu-id="e09e4-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="e09e4-180">W przeciwnym razie polecenie Receive tworzy `ChunkingReader` nową i nową `ChunkingMessage` opakowaną w ten sposób ( `GetNewChunkingMessage`poprzez wywoływanie).</span><span class="sxs-lookup"><span data-stu-id="e09e4-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="e09e4-181">Przed zwróceniem nowego `ChunkingMessage`elementu, funkcja Receive używa wątku puli wątków `ReceiveChunkLoop`do wykonania, `innerChannel.Receive` który wywołuje `ChunkingReader` pętlę i rozrywane fragmenty do momentu otrzymania komunikatu końca fragmentu lub gdy zostanie osiągnięty limit czasu odbierania.</span><span class="sxs-lookup"><span data-stu-id="e09e4-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>

<span data-ttu-id="e09e4-182">Oto kilka szczegółów:</span><span class="sxs-lookup"><span data-stu-id="e09e4-182">A few details worth noting:</span></span>

- <span data-ttu-id="e09e4-183">Jak wysyłać, odbieraj pierwsze `ThrowIfDisposedOrNotOepned` wywołania, aby `CommunicationState` upewnić się, że jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="e09e4-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>

- <span data-ttu-id="e09e4-184">Odbieranie jest również synchronizowane, dzięki czemu w danej chwili można odbierać tylko jeden komunikat z sesji.</span><span class="sxs-lookup"><span data-stu-id="e09e4-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="e09e4-185">Jest to szczególnie ważne, ponieważ po odebraniu komunikatu o początkowym fragmencie wszystkie kolejne odebrane komunikaty powinny być fragmentami w tej nowej sekwencji fragmentów do momentu odebrania komunikatu końcowego fragmentu.</span><span class="sxs-lookup"><span data-stu-id="e09e4-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="e09e4-186">Wartość Receive nie może ściągać komunikatów z kanału wewnętrznego, dopóki nie zostaną odebrane wszystkie fragmenty należące do komunikatu, który jest obecnie usuwany.</span><span class="sxs-lookup"><span data-stu-id="e09e4-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="e09e4-187">Aby to osiągnąć, funkcja Receive używa `ManualResetEvent` nazwy `currentMessageCompleted`, która jest ustawiana, gdy końcowy komunikat fragmentu zostanie odebrany i zresetowany po odebraniu nowego komunikatu o początkowym fragmencie.</span><span class="sxs-lookup"><span data-stu-id="e09e4-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>

- <span data-ttu-id="e09e4-188">W przeciwieństwie do wysyłania, odbieranie nie zapobiega przeniesieniu zsynchronizowanych zmian stanu podczas odbierania.</span><span class="sxs-lookup"><span data-stu-id="e09e4-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="e09e4-189">Na przykład Zamknij można wywołać podczas odbierania i czeka na zakończenie oczekiwania na odebranie oryginalnego komunikatu lub osiągnięcie określonej wartości limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="e09e4-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>

- <span data-ttu-id="e09e4-190">Limit czasu przekazywania jest używany jako limit czasu dla całej operacji odbierania, który obejmuje odbieranie wszystkich fragmentów.</span><span class="sxs-lookup"><span data-stu-id="e09e4-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>

- <span data-ttu-id="e09e4-191">Jeśli warstwa korzystająca z komunikatów zużywa komunikat z szybkością niższą niż szybkość przychodzących komunikatów fragmentów, `ChunkingReader` bufory te przychodzące te fragmenty do limitu określonego przez. `ChunkingBindingElement.MaxBufferedChunks`</span><span class="sxs-lookup"><span data-stu-id="e09e4-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="e09e4-192">Po osiągnięciu tego limitu żadne fragmenty nie są ściągane z warstwy niższej do momentu użycia zbuforowanego fragmentu lub przekroczenia limitu czasu odbierania.</span><span class="sxs-lookup"><span data-stu-id="e09e4-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>

## <a name="communicationobject-overrides"></a><span data-ttu-id="e09e4-193">Przesłonięcia komunikacjiobject</span><span class="sxs-lookup"><span data-stu-id="e09e4-193">CommunicationObject Overrides</span></span>

### <a name="onopen"></a><span data-ttu-id="e09e4-194">OnOpen</span><span class="sxs-lookup"><span data-stu-id="e09e4-194">OnOpen</span></span>

<span data-ttu-id="e09e4-195">`OnOpen`wywołuje `innerChannel.Open` , aby otworzyć wewnętrzny kanał.</span><span class="sxs-lookup"><span data-stu-id="e09e4-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>

### <a name="onclose"></a><span data-ttu-id="e09e4-196">OnClose —</span><span class="sxs-lookup"><span data-stu-id="e09e4-196">OnClose</span></span>

<span data-ttu-id="e09e4-197">`OnClose`najpierw ustawia `stopReceive` `true` , aby sygnalizować oczekiwanie `ReceiveChunkLoop` na zatrzymanie.</span><span class="sxs-lookup"><span data-stu-id="e09e4-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="e09e4-198">Następnie czeka na `receiveStopped` <xref:System.Threading.ManualResetEvent>, który jest ustawiony po `ReceiveChunkLoop` zatrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="e09e4-198">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="e09e4-199">Przy założeniu, że `OnClose` `innerChannel.Close` zatrzymasięwokreślonymlimicieczasu,wywołujezpozostałym`ReceiveChunkLoop` limitem czasu.</span><span class="sxs-lookup"><span data-stu-id="e09e4-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>

### <a name="onabort"></a><span data-ttu-id="e09e4-200">OnAbort</span><span class="sxs-lookup"><span data-stu-id="e09e4-200">OnAbort</span></span>

<span data-ttu-id="e09e4-201">`OnAbort`wywołuje `innerChannel.Abort` przerwanie wewnętrznego kanału.</span><span class="sxs-lookup"><span data-stu-id="e09e4-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="e09e4-202">Jeśli istnieje oczekujące `ReceiveChunkLoop` , pobiera wyjątek z oczekującego `innerChannel.Receive` wywołania.</span><span class="sxs-lookup"><span data-stu-id="e09e4-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>

### <a name="onfaulted"></a><span data-ttu-id="e09e4-203">Onfaultd</span><span class="sxs-lookup"><span data-stu-id="e09e4-203">OnFaulted</span></span>

<span data-ttu-id="e09e4-204">W `ChunkingChannel` przypadku awarii kanału nie jest wymagane specjalne zachowanie, które `OnFaulted` nie jest zastępowane.</span><span class="sxs-lookup"><span data-stu-id="e09e4-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>

## <a name="implementing-channel-factory"></a><span data-ttu-id="e09e4-205">Implementowanie fabryki kanałów</span><span class="sxs-lookup"><span data-stu-id="e09e4-205">Implementing Channel Factory</span></span>

<span data-ttu-id="e09e4-206">Jest odpowiedzialny za tworzenie `ChunkingDuplexSessionChannel` wystąpień i dla przejścia stanu kaskadowego do fabryki kanałów wewnętrznych. `ChunkingChannelFactory`</span><span class="sxs-lookup"><span data-stu-id="e09e4-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>

<span data-ttu-id="e09e4-207">`OnCreateChannel`używa wewnętrznej fabryki kanałów do tworzenia `IDuplexSessionChannel` wewnętrznego kanału.</span><span class="sxs-lookup"><span data-stu-id="e09e4-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="e09e4-208">Następnie tworzy nowe `ChunkingDuplexSessionChannel` przekazanie go do tego kanału wewnętrznego wraz z listą akcji komunikatów, które mają być rozłożone, oraz maksymalną liczbę fragmentów do buforowania po odebraniu.</span><span class="sxs-lookup"><span data-stu-id="e09e4-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="e09e4-209">Lista akcji komunikatów, które mają zostać rozłączone, a maksymalna liczba fragmentów do buforu to dwa parametry przesłane do `ChunkingChannelFactory` w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="e09e4-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="e09e4-210">Sekcja `ChunkingBindingElement` opisująca, z której pochodzą te wartości.</span><span class="sxs-lookup"><span data-stu-id="e09e4-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>

<span data-ttu-id="e09e4-211">`OnOpen`, ,I`OnAbort` ich równoważne asynchronicznie wywołują odpowiednią metodę przechodzenia stanu w wewnętrznej fabryki kanałów. `OnClose`</span><span class="sxs-lookup"><span data-stu-id="e09e4-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>

## <a name="implementing-channel-listener"></a><span data-ttu-id="e09e4-212">Implementowanie odbiornika kanału</span><span class="sxs-lookup"><span data-stu-id="e09e4-212">Implementing Channel Listener</span></span>

<span data-ttu-id="e09e4-213">`ChunkingChannelListener` Jest otoką wokół odbiornika wewnętrznego kanału.</span><span class="sxs-lookup"><span data-stu-id="e09e4-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="e09e4-214">Jej główna funkcja, oprócz wywołań delegatów tego odbiornika kanału wewnętrznego, polega na zawijaniu `ChunkingDuplexSessionChannels` nowych kanałów, które zaakceptowały z odbiornika wewnętrznego kanału.</span><span class="sxs-lookup"><span data-stu-id="e09e4-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="e09e4-215">Jest to realizowane w `OnAcceptChannel` i `OnEndAcceptChannel`.</span><span class="sxs-lookup"><span data-stu-id="e09e4-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="e09e4-216">Nowo utworzony `ChunkingDuplexSessionChannel` został przekazaną wewnętrzny kanał wraz z innymi opisanymi wcześniej parametrami.</span><span class="sxs-lookup"><span data-stu-id="e09e4-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>

## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="e09e4-217">Implementowanie elementu powiązania i powiązania</span><span class="sxs-lookup"><span data-stu-id="e09e4-217">Implementing Binding Element and Binding</span></span>

<span data-ttu-id="e09e4-218">`ChunkingBindingElement`jest odpowiedzialny za tworzenie `ChunkingChannelFactory` i `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="e09e4-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="e09e4-219">Sprawdza `ChunkingBindingElement` , czy t w `CanBuildChannelFactory` \<t > i `CanBuildChannelListener` \<t > jest typu `IDuplexSessionChannel` (jedyny kanał obsługiwany przez kanał fragmentu) i że inne elementy powiązania w powiązaniu obsługują tę Typ kanału.</span><span class="sxs-lookup"><span data-stu-id="e09e4-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>

<span data-ttu-id="e09e4-220">`BuildChannelFactory`\<T > najpierw sprawdza, czy żądany typ kanału można skompilować, a następnie pobiera listę akcji komunikatów, które mają zostać rozbudowane.</span><span class="sxs-lookup"><span data-stu-id="e09e4-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="e09e4-221">Aby uzyskać więcej informacji, zobacz następującą sekcję.</span><span class="sxs-lookup"><span data-stu-id="e09e4-221">For more information, see the following section.</span></span> <span data-ttu-id="e09e4-222">Następnie tworzy nowe `ChunkingChannelFactory` przekazanie do niego wewnętrzną fabrykę kanałów (w wyniku `context.BuildInnerChannelFactory<IDuplexSessionChannel>`powrotu z), listę akcji komunikatów oraz maksymalną liczbę fragmentów do buforowania.</span><span class="sxs-lookup"><span data-stu-id="e09e4-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="e09e4-223">Maksymalna liczba fragmentów pochodzi z właściwości o nazwie `MaxBufferedChunks` uwidocznionej `ChunkingBindingElement`przez.</span><span class="sxs-lookup"><span data-stu-id="e09e4-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>

<span data-ttu-id="e09e4-224">`BuildChannelListener<T>`ma podobną implementację do `ChunkingChannelListener` tworzenia i przekazywania do niego wewnętrznego odbiornika kanału.</span><span class="sxs-lookup"><span data-stu-id="e09e4-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>

<span data-ttu-id="e09e4-225">Istnieje przykładowe powiązanie dołączone do tego przykładu o nazwie `TcpChunkingBinding`.</span><span class="sxs-lookup"><span data-stu-id="e09e4-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="e09e4-226">To powiązanie składa się z dwóch elementów `TcpTransportBindingElement` powiązań `ChunkingBindingElement`: i.</span><span class="sxs-lookup"><span data-stu-id="e09e4-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="e09e4-227">Oprócz ujawniania `MaxBufferedChunks` właściwości, powiązanie również ustawia niektóre `TcpTransportBindingElement` właściwości, takie jak `MaxReceivedMessageSize` (ustawia go na `ChunkingUtils.ChunkSize` + 100KB bajtów dla nagłówków).</span><span class="sxs-lookup"><span data-stu-id="e09e4-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>

<span data-ttu-id="e09e4-228">`TcpChunkingBinding`Ponadto implementuje `IBindingRuntimePreferences` i zwraca wartość true `ReceiveSynchronously` z metody wskazującej, że zaimplementowano tylko synchroniczne wywołania odbioru.</span><span class="sxs-lookup"><span data-stu-id="e09e4-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>

### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="e09e4-229">Określanie komunikatów do fragmentu</span><span class="sxs-lookup"><span data-stu-id="e09e4-229">Determining Which Messages To Chunk</span></span>

<span data-ttu-id="e09e4-230">Segment segmentu fragmentu tylko komunikaty identyfikowane za pośrednictwem `ChunkingBehavior` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e09e4-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="e09e4-231">Klasa implementuje `IOperationBehavior` i`AddBindingParameter` jest implementowana przez wywołanie metody. `ChunkingBehavior`</span><span class="sxs-lookup"><span data-stu-id="e09e4-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="e09e4-232">W tej metodzie `ChunkingBehavior` sprawdza wartość jej `AppliesTo` właściwości (`InMessage` `OutMessage` lub obie), aby określić, które komunikaty powinny zostać rozdzieleniem.</span><span class="sxs-lookup"><span data-stu-id="e09e4-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="e09e4-233">Następnie pobiera akcję każdego z tych komunikatów (z kolekcji messages on `OperationDescription`) i dodaje ją do kolekcji ciągów zawartej w `ChunkingBindingParameter`wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="e09e4-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="e09e4-234">Następnie dodaje to `ChunkingBindingParameter` do podanego `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="e09e4-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>

<span data-ttu-id="e09e4-235">Jest `BindingParameterCollection` to przesyłane w `BindingContext` obrębie do każdego elementu wiązania w powiązaniu, gdy ten element powiązania kompiluje fabrykę kanałów lub odbiornik kanału.</span><span class="sxs-lookup"><span data-stu-id="e09e4-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="e09e4-236">`ChunkingBindingElement` Implementacja`BuildChannelListener<T>` i wyciągnij te`ChunkingBindingParameter` elementy zprogramu`BindingParameterCollection`. `BuildChannelFactory<T>` `BindingContext’`</span><span class="sxs-lookup"><span data-stu-id="e09e4-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="e09e4-237">Kolekcja `ChunkingBindingParameter` akcji zawartych w elemencie jest następnie przekazywana `ChunkingChannelFactory` do lub `ChunkingChannelListener` `ChunkingDuplexSessionChannel`, co z kolei przekazuje go do.</span><span class="sxs-lookup"><span data-stu-id="e09e4-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>

## <a name="running-the-sample"></a><span data-ttu-id="e09e4-238">Uruchamianie przykładu</span><span class="sxs-lookup"><span data-stu-id="e09e4-238">Running the Sample</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e09e4-239">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="e09e4-239">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e09e4-240">Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="e09e4-240">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="e09e4-241">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e09e4-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="e09e4-242">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e09e4-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="e09e4-243">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e09e4-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

5. <span data-ttu-id="e09e4-244">Uruchom najpierw plik Service. exe, a następnie uruchom program Client. exe i obejrzyj oba okna konsoli dla danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e09e4-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>

<span data-ttu-id="e09e4-245">Podczas uruchamiania przykładu, oczekiwane są następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e09e4-245">When running the sample, the following output is expected.</span></span>

<span data-ttu-id="e09e4-246">Klient:</span><span class="sxs-lookup"><span data-stu-id="e09e4-246">Client:</span></span>

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

<span data-ttu-id="e09e4-247">Server</span><span class="sxs-lookup"><span data-stu-id="e09e4-247">Server:</span></span>

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
