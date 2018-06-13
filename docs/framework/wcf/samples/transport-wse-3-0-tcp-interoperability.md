---
title: 'Transport: Współdziałanie protokołu TCP z usługami WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: 8cdd88b354f2e07c84ccfda85c8552d37ca2f519
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808015"
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="5fec8-102">Transport: Współdziałanie protokołu TCP z usługami WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="5fec8-102">Transport: WSE 3.0 TCP Interoperability</span></span>
<span data-ttu-id="5fec8-103">Przykładowe WSE 3.0 TCP współdziałanie transportu pokazano, jak zaimplementować sesji dupleksowej TCP jako niestandardowego transportu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5fec8-103">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="5fec8-104">Przedstawiono również, jak używasz rozszerzalności warstwy kanału do interfejsu przez sieć z istniejącymi systemami wdrożone.</span><span class="sxs-lookup"><span data-stu-id="5fec8-104">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="5fec8-105">W następujących krokach przedstawiono sposób tworzenia niestandardowych transportu WCF:</span><span class="sxs-lookup"><span data-stu-id="5fec8-105">The following steps show how to build this custom WCF transport:</span></span>  
  
1.  <span data-ttu-id="5fec8-106">Począwszy od gniazda TCP, utworzyć klienta i serwera implementacje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> który umożliwia DIME Framing odróżniać granice wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5fec8-106">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2.  <span data-ttu-id="5fec8-107">Tworzenie fabryki kanałów, który jest podłączany do usługi WSE TCP i wysyła ramce wiadomości przez klienta <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span><span class="sxs-lookup"><span data-stu-id="5fec8-107">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3.  <span data-ttu-id="5fec8-108">Utwórz odbiornik kanału do akceptowania przychodzących połączeń TCP oraz tworzenia kanały.</span><span class="sxs-lookup"><span data-stu-id="5fec8-108">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4.  <span data-ttu-id="5fec8-109">Upewnij się, że wszelkie wyjątki dotyczące sieci są znormalizowane do odpowiedniej klasy pochodnej z <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="5fec8-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5.  <span data-ttu-id="5fec8-110">Dodaj element powiązania, który dodaje niestandardowy transportu do stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="5fec8-110">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="5fec8-111">Aby uzyskać więcej informacji zobacz [Dodawanie elementu powiązania].</span><span class="sxs-lookup"><span data-stu-id="5fec8-111">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="5fec8-112">Tworzenie IDuplexSessionChannel</span><span class="sxs-lookup"><span data-stu-id="5fec8-112">Creating IDuplexSessionChannel</span></span>  
 <span data-ttu-id="5fec8-113">Pierwszą czynnością przy tworzeniu transportu współdziałanie programu WSE 3.0 protokołu TCP jest utworzenie implementacja <xref:System.ServiceModel.Channels.IDuplexSessionChannel> nad <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="5fec8-113">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="5fec8-114">`WseTcpDuplexSessionChannel` pochodną <xref:System.ServiceModel.Channels.ChannelBase>.</span><span class="sxs-lookup"><span data-stu-id="5fec8-114">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="5fec8-115">Logika wysyłania wiadomości składa się z dwóch głównych elementów: (1) Kodowanie komunikatu na bajty oraz (2) framing tych bajtów i wysyłania ich przesyłania.</span><span class="sxs-lookup"><span data-stu-id="5fec8-115">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="5fec8-116">Ponadto blokady jest zajęty, aby wywołania Send() zachować gwarancji w kolejności IDuplexSessionChannel i tak, aby wywołania do gniazda podstawowej są poprawnie synchronizowane.</span><span class="sxs-lookup"><span data-stu-id="5fec8-116">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="5fec8-117">`WseTcpDuplexSessionChannel` używa <xref:System.ServiceModel.Channels.MessageEncoder> do tłumaczenia <xref:System.ServiceModel.Channels.Message> do i z byte [].</span><span class="sxs-lookup"><span data-stu-id="5fec8-117">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="5fec8-118">Ponieważ istnieje transportu, `WseTcpDuplexSessionChannel` również jest odpowiedzialna za stosowanie zdalny adres, który kanał został skonfigurowany z.</span><span class="sxs-lookup"><span data-stu-id="5fec8-118">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="5fec8-119">`EncodeMessage` hermetyzuje logikę do konwersji.</span><span class="sxs-lookup"><span data-stu-id="5fec8-119">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="5fec8-120">Raz <xref:System.ServiceModel.Channels.Message> jest zakodowany w bajtach, muszą być przekazywane w sieci.</span><span class="sxs-lookup"><span data-stu-id="5fec8-120">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="5fec8-121">Wymaga to systemu do definiowania granice wiadomości.</span><span class="sxs-lookup"><span data-stu-id="5fec8-121">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="5fec8-122">WSE 3.0 używa wersji [DIME](http://go.microsoft.com/fwlink/?LinkId=94999) jako protokół ramek.</span><span class="sxs-lookup"><span data-stu-id="5fec8-122">WSE 3.0 uses a version of [DIME](http://go.microsoft.com/fwlink/?LinkId=94999) as its framing protocol.</span></span> <span data-ttu-id="5fec8-123">`WriteData` hermetyzuje logiki ramek do opakowywania byte [] w zestawie rekordów DIME.</span><span class="sxs-lookup"><span data-stu-id="5fec8-123">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="5fec8-124">Logika do odbierania wiadomości jest bardzo podobne.</span><span class="sxs-lookup"><span data-stu-id="5fec8-124">The logic for receiving messages is very similar.</span></span> <span data-ttu-id="5fec8-125">Główne złożoności obsługuje fakt, że gniazda do odczytu mogą zwracać mniej bajtów niż żądano.</span><span class="sxs-lookup"><span data-stu-id="5fec8-125">The main complexity is handling the fact that a socket read can return less bytes than were requested.</span></span> <span data-ttu-id="5fec8-126">Aby otrzymywać wiadomość, `WseTcpDuplexSessionChannel` odczytuje bajtów poza przewodowo, dekoduje ramek DIME, a następnie używa <xref:System.ServiceModel.Channels.MessageEncoder> służący do włączania byte [] do <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="5fec8-126">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="5fec8-127">Podstawowym `WseTcpDuplexSessionChannel` przyjęto założenie, że odbiera połączenia gniazda.</span><span class="sxs-lookup"><span data-stu-id="5fec8-127">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="5fec8-128">Klasa podstawowa obsługuje zamknięcia gniazda.</span><span class="sxs-lookup"><span data-stu-id="5fec8-128">The base class handles socket shutdown.</span></span> <span data-ttu-id="5fec8-129">Istnieją trzy miejsca z zamknięcia gniazda:</span><span class="sxs-lookup"><span data-stu-id="5fec8-129">There are three places that interface with socket closure:</span></span>  
  
-   <span data-ttu-id="5fec8-130">OnAbort — Zamknij gniazda ungracefully (Zamknij twarde).</span><span class="sxs-lookup"><span data-stu-id="5fec8-130">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
-   <span data-ttu-id="5fec8-131">Na [Begin] Zamknij — Zamknij gniazda bezpiecznie (Zamknij nietrwałego).</span><span class="sxs-lookup"><span data-stu-id="5fec8-131">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
-   <span data-ttu-id="5fec8-132">sesji. CloseOutputSession — zamknięcie strumień danych wychodzących (Zamknij połowa).</span><span class="sxs-lookup"><span data-stu-id="5fec8-132">session.CloseOutputSession -- shutdown the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="5fec8-133">Fabryka kanałów</span><span class="sxs-lookup"><span data-stu-id="5fec8-133">Channel Factory</span></span>  
 <span data-ttu-id="5fec8-134">Następnym krokiem w pisaniu transportu TCP jest utworzenie implementacja <xref:System.ServiceModel.Channels.IChannelFactory> kanałów klienta.</span><span class="sxs-lookup"><span data-stu-id="5fec8-134">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
-   <span data-ttu-id="5fec8-135">`WseTcpChannelFactory` pochodną <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >.</span><span class="sxs-lookup"><span data-stu-id="5fec8-135">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="5fec8-136">Fabryka, która zastępuje jest `OnCreateChannel` do tworzenia kanałów klienta.</span><span class="sxs-lookup"><span data-stu-id="5fec8-136">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   <span data-ttu-id="5fec8-137">`ClientWseTcpDuplexSessionChannel` dodaje logikę do podstawy `WseTcpDuplexSessionChannel` do nawiązania połączenia z serwerem TCP `channel.Open` czasu.</span><span class="sxs-lookup"><span data-stu-id="5fec8-137">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="5fec8-138">Nazwa hosta jest najpierw rozpoznana jako adres IP, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5fec8-138">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   <span data-ttu-id="5fec8-139">Następnie nazwa hosta jest podłączony do pierwszy dostępny adres IP w pętli, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5fec8-139">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   <span data-ttu-id="5fec8-140">W ramach umowy kanału, wszelkie wyjątki specyficznego dla domeny są opakowywane, takich jak `SocketException` w <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="5fec8-140">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="5fec8-141">Odbiornik kanału</span><span class="sxs-lookup"><span data-stu-id="5fec8-141">Channel Listener</span></span>  
 <span data-ttu-id="5fec8-142">Następnym krokiem w pisaniu transportu TCP jest utworzenie implementacja <xref:System.ServiceModel.Channels.IChannelListener> akceptowania kanały serwera.</span><span class="sxs-lookup"><span data-stu-id="5fec8-142">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
-   <span data-ttu-id="5fec8-143">`WseTcpChannelListener` pochodną <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > i zastąpienia na otwieranie [Begin] i [Begin] Zamknij, aby kontrolować okres istnienia jego gniazdo.</span><span class="sxs-lookup"><span data-stu-id="5fec8-143">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="5fec8-144">W zdarzenia gniazda jest tworzony do nasłuchiwania IP_ANY.</span><span class="sxs-lookup"><span data-stu-id="5fec8-144">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="5fec8-145">Implementacje bardziej zaawansowanych można utworzyć drugi gniazda do nasłuchiwania protokołu IPv6, jak również.</span><span class="sxs-lookup"><span data-stu-id="5fec8-145">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="5fec8-146">Umożliwiają one również adres IP, należy określić w nazwie hosta.</span><span class="sxs-lookup"><span data-stu-id="5fec8-146">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="5fec8-147">Po zaakceptowaniu nowe gniazdo kanału serwera jest inicjowany z tego gniazda.</span><span class="sxs-lookup"><span data-stu-id="5fec8-147">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="5fec8-148">Wszystkie dane wejściowe i wyjściowe został już zaimplementowany w klasie podstawowej, dlatego ten kanał jest odpowiedzialny za inicjowanie gniazda.</span><span class="sxs-lookup"><span data-stu-id="5fec8-148">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="5fec8-149">Dodawanie elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="5fec8-149">Adding a Binding Element</span></span>  
 <span data-ttu-id="5fec8-150">Teraz, kiedy są tworzone i fabryki kanałów, muszą być widoczne dla środowiska uruchomieniowego ServiceModel za pośrednictwem powiązania.</span><span class="sxs-lookup"><span data-stu-id="5fec8-150">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="5fec8-151">Powiązanie to kolekcja elementów powiązań reprezentujący stosu komunikacji skojarzony z adresem usługi.</span><span class="sxs-lookup"><span data-stu-id="5fec8-151">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="5fec8-152">Każdy element na stosie jest reprezentowany przez element powiązania.</span><span class="sxs-lookup"><span data-stu-id="5fec8-152">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="5fec8-153">W przykładzie jest element powiązania `WseTcpTransportBindingElement`, która jest pochodną <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="5fec8-153">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="5fec8-154">Obsługuje ona <xref:System.ServiceModel.Channels.IDuplexSessionChannel> i zastępuje następujące metody umożliwiające tworzenie fabryki skojarzony z powiązaniem naszych.</span><span class="sxs-lookup"><span data-stu-id="5fec8-154">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="5fec8-155">Zawiera także członków do klonowania `BindingElement` i zwracanie naszych schematu (wse.tcp).</span><span class="sxs-lookup"><span data-stu-id="5fec8-155">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="5fec8-156">Konsolę programu WSE TCP testu</span><span class="sxs-lookup"><span data-stu-id="5fec8-156">The WSE TCP Test Console</span></span>  
 <span data-ttu-id="5fec8-157">Za pomocą tego transportu przykładowy kod testu jest dostępny w TestCode.cs.</span><span class="sxs-lookup"><span data-stu-id="5fec8-157">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="5fec8-158">Poniższe instrukcje przedstawiają sposób konfigurowania programu WSE `TcpSyncStockService` próbki.</span><span class="sxs-lookup"><span data-stu-id="5fec8-158">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="5fec8-159">Kod testu tworzy niestandardowego powiązania, który używa jako kodowanie MTOM i `WseTcpTransport` jako transportu.</span><span class="sxs-lookup"><span data-stu-id="5fec8-159">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="5fec8-160">Konfiguruje również wersja adresowania mogła być być zgodność z programu WSE 3.0, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5fec8-160">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="5fec8-161">Składa się z dwóch testów — jeden test konfiguruje klient z typowaniem przy użyciu kodu wygenerowane z pliku programu WSE 3.0 WSDL.</span><span class="sxs-lookup"><span data-stu-id="5fec8-161">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="5fec8-162">Drugi test używa WCF jako klient i serwer wysyła komunikaty bezpośrednio na kanale interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="5fec8-162">The second test uses WCF as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="5fec8-163">Podczas uruchamiania próbki, oczekiwano następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="5fec8-163">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="5fec8-164">Klient:</span><span class="sxs-lookup"><span data-stu-id="5fec8-164">Client:</span></span>  
  
```  
Calling soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Symbol: FABRIKAM  
        Name: Fabrikam, Inc.  
        Last Price: 120  
  
Symbol: CONTOSO  
        Name: Contoso Corp.  
        Last Price: 50.07  
Press enter.  
  
Received Action: http://SayHello  
Received Body: to you.  
Hello to you.  
Press enter.  
  
Received Action: http://NotHello  
Received Body: to me.  
Press enter.  
```  
  
 <span data-ttu-id="5fec8-165">Serwer:</span><span class="sxs-lookup"><span data-stu-id="5fec8-165">Server:</span></span>  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5fec8-166">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="5fec8-166">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5fec8-167">Aby uruchomić ten przykład, musi mieć WSE 3.0 i WSE `TcpSyncStockService` próbki zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="5fec8-167">To run this sample, you must have WSE 3.0 and the WSE `TcpSyncStockService` sample installed.</span></span> <span data-ttu-id="5fec8-168">Możesz pobrać [WSE 3.0 w sieci MSDN](http://go.microsoft.com/fwlink/?LinkId=95000).</span><span class="sxs-lookup"><span data-stu-id="5fec8-168">You can download [WSE 3.0 from MSDN](http://go.microsoft.com/fwlink/?LinkId=95000).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fec8-169">Ponieważ WSE 3.0 nie jest obsługiwany na [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nie można zainstalować ani uruchomić `TcpSyncStockService` przykładowa w tym systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="5fec8-169">Because WSE 3.0 is not supported on [!INCLUDE[lserver](../../../../includes/lserver-md.md)], you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1.  <span data-ttu-id="5fec8-170">Po zainstalowaniu `TcpSyncStockService` przykładowe, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5fec8-170">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1.  <span data-ttu-id="5fec8-171">Otwórz `TcpSyncStockService` w programie Visual Studio (należy pamiętać, że przykładowe TcpSyncStockService jest instalowany z programu WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="5fec8-171">Open the `TcpSyncStockService` in Visual Studio (Note that the TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="5fec8-172">Nie jest częścią ten przykład kodu).</span><span class="sxs-lookup"><span data-stu-id="5fec8-172">It is not part of this sample's code).</span></span>  
  
    2.  <span data-ttu-id="5fec8-173">Ustaw projekt StockService jako projekt startowy.</span><span class="sxs-lookup"><span data-stu-id="5fec8-173">Set the StockService project as the start up project.</span></span>  
  
    3.  <span data-ttu-id="5fec8-174">Otwórz StockService.cs w StockService projektu i komentarz dla atrybutu [zasad] `StockService` klasy.</span><span class="sxs-lookup"><span data-stu-id="5fec8-174">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="5fec8-175">Powoduje wyłączenie zabezpieczeń z próbki.</span><span class="sxs-lookup"><span data-stu-id="5fec8-175">This disables security from the sample.</span></span> <span data-ttu-id="5fec8-176">Gdy WCF może współdziałać z bezpieczne punkty końcowe programu WSE 3.0, zabezpieczenia są wyłączone do zachowania w tym przykładzie koncentruje się na niestandardowe transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="5fec8-176">While WCF can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4.  <span data-ttu-id="5fec8-177">Naciśnij klawisz F5, aby uruchomić `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="5fec8-177">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="5fec8-178">Usługa jest uruchamiana w nowym oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="5fec8-178">The service starts in a new console window.</span></span>  
  
    5.  <span data-ttu-id="5fec8-179">Otwórz ten przykład transportu TCP w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5fec8-179">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6.  <span data-ttu-id="5fec8-180">Zaktualizować zmiennej "Nazwa hosta" w TestCode.cs odpowiadające działa Nazwa maszyny `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="5fec8-180">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7.  <span data-ttu-id="5fec8-181">Naciśnij klawisz F5, aby uruchomić przykładowe transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="5fec8-181">Press F5 to start the TCP transport sample.</span></span>  
  
    8.  <span data-ttu-id="5fec8-182">Klient testowy transportu TCP rozpoczyna się w nowej konsoli.</span><span class="sxs-lookup"><span data-stu-id="5fec8-182">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="5fec8-183">Klient żąda giełdowych z usługi i następnie wyświetla wyniki w oknie swojej konsoli.</span><span class="sxs-lookup"><span data-stu-id="5fec8-183">The client requests stock quotes from the service and then displays the results in its console window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fec8-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5fec8-184">See Also</span></span>
