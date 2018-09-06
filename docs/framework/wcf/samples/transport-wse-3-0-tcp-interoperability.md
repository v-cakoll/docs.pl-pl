---
title: 'Transport: Współdziałanie protokołu TCP z usługami WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: b727da998736944afd23f7dcfbf45a1f6049d1d0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43804980"
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="b8dea-102">Transport: Współdziałanie protokołu TCP z usługami WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="b8dea-102">Transport: WSE 3.0 TCP Interoperability</span></span>
<span data-ttu-id="b8dea-103">Przykładowe programu WSE 3.0 protokołu TCP współdziałanie transportu demonstruje sposób implementacji dwukierunkowego sesji TCP jako niestandardowy transportu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b8dea-103">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="b8dea-104">Ilustruje też, jak można użyć rozszerzalności warstwy kanału do interfejsu przez sieć z istniejącymi systemami wdrożone.</span><span class="sxs-lookup"><span data-stu-id="b8dea-104">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="b8dea-105">Poniższe kroki pokazują jak utworzyć niestandardowe transport WCF:</span><span class="sxs-lookup"><span data-stu-id="b8dea-105">The following steps show how to build this custom WCF transport:</span></span>  
  
1.  <span data-ttu-id="b8dea-106">Począwszy od gniazda TCP, utworzyć klienta i serwera implementacje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> używające ramek DIME aby odróżnić granice wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b8dea-106">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2.  <span data-ttu-id="b8dea-107">Tworzenie fabryki kanałów, łączy się z usługą programu WSE TCP, która wysyła komunikaty ramce przez klienta <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span><span class="sxs-lookup"><span data-stu-id="b8dea-107">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3.  <span data-ttu-id="b8dea-108">Utwórz odbiornik kanału, aby zaakceptować połączenia przychodzące TCP i tworzyć kanały.</span><span class="sxs-lookup"><span data-stu-id="b8dea-108">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4.  <span data-ttu-id="b8dea-109">Upewnij się, że wszystkie wyjątki dotyczące sieci są znormalizowane zgodnie z odpowiedniej klasy pochodnej z <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="b8dea-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5.  <span data-ttu-id="b8dea-110">Dodaj element powiązania, który dodaje niestandardowy transportu do stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="b8dea-110">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="b8dea-111">Aby uzyskać więcej informacji zobacz [Dodawanie elementu powiązania].</span><span class="sxs-lookup"><span data-stu-id="b8dea-111">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="b8dea-112">Tworzenie IDuplexSessionChannel</span><span class="sxs-lookup"><span data-stu-id="b8dea-112">Creating IDuplexSessionChannel</span></span>  
 <span data-ttu-id="b8dea-113">Pierwszym krokiem podczas pisania transportu współdziałania programu WSE 3.0 protokołu TCP jest utworzenie implementacji klasy <xref:System.ServiceModel.Channels.IDuplexSessionChannel> w górnej części <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="b8dea-113">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="b8dea-114">`WseTcpDuplexSessionChannel` pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelBase>.</span><span class="sxs-lookup"><span data-stu-id="b8dea-114">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="b8dea-115">Logika wysyłania komunikatu składa się z dwóch głównych elementów: (1) kodowanie wiadomości w bajtach i (2) ramek tych bajtów i wysyłając przesyłania.</span><span class="sxs-lookup"><span data-stu-id="b8dea-115">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="b8dea-116">Ponadto blokady jest pobierana w celu wywołania Send() zachowania gwarancji w kolejności IDuplexSessionChannel i tak, aby wywołania do gniazda podstawowej są poprawnie synchronizowane.</span><span class="sxs-lookup"><span data-stu-id="b8dea-116">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="b8dea-117">`WseTcpDuplexSessionChannel` używa <xref:System.ServiceModel.Channels.MessageEncoder> do tłumaczenia <xref:System.ServiceModel.Channels.Message> do i z byte [].</span><span class="sxs-lookup"><span data-stu-id="b8dea-117">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="b8dea-118">Ponieważ jest on transportu `WseTcpDuplexSessionChannel` jest również odpowiedzialny za stosowanie adresów zdalnych, której skonfigurowano kanał.</span><span class="sxs-lookup"><span data-stu-id="b8dea-118">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="b8dea-119">`EncodeMessage` hermetyzuje logikę tej konwersji.</span><span class="sxs-lookup"><span data-stu-id="b8dea-119">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="b8dea-120">Gdy <xref:System.ServiceModel.Channels.Message> jest zakodowany w bajtach, muszą być przekazywane w sieci.</span><span class="sxs-lookup"><span data-stu-id="b8dea-120">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="b8dea-121">Wymaga to systemu do definiowania granice wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b8dea-121">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="b8dea-122">Programu WSE 3.0 korzysta z wersji [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) jako protokół ramek.</span><span class="sxs-lookup"><span data-stu-id="b8dea-122">WSE 3.0 uses a version of [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) as its framing protocol.</span></span> <span data-ttu-id="b8dea-123">`WriteData` hermetyzuje logikę ramek do opakowania byte [] do zestawu rekordów DIME.</span><span class="sxs-lookup"><span data-stu-id="b8dea-123">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="b8dea-124">Logika do odbierania wiadomości jest bardzo podobne.</span><span class="sxs-lookup"><span data-stu-id="b8dea-124">The logic for receiving messages is very similar.</span></span> <span data-ttu-id="b8dea-125">Złożoność głównego jest obsługa fakt, że gniazdo odczyt może zwrócić mniej bajtów niż zażądano.</span><span class="sxs-lookup"><span data-stu-id="b8dea-125">The main complexity is handling the fact that a socket read can return less bytes than were requested.</span></span> <span data-ttu-id="b8dea-126">Aby otrzymać komunikat, `WseTcpDuplexSessionChannel` odczytuje bajtów wyłączone podczas transmisji, dekoduje ramek DIME, a następnie używa <xref:System.ServiceModel.Channels.MessageEncoder> Włączanie byte [] do <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="b8dea-126">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="b8dea-127">Podstawa `WseTcpDuplexSessionChannel` przyjęto założenie, że będzie ona otrzymywać połączone gniazdo.</span><span class="sxs-lookup"><span data-stu-id="b8dea-127">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="b8dea-128">Klasa bazowa obsługuje zamykania gniazda.</span><span class="sxs-lookup"><span data-stu-id="b8dea-128">The base class handles socket shutdown.</span></span> <span data-ttu-id="b8dea-129">Istnieją trzy miejsca, z gniazda zamknięcia:</span><span class="sxs-lookup"><span data-stu-id="b8dea-129">There are three places that interface with socket closure:</span></span>  
  
-   <span data-ttu-id="b8dea-130">OnAbort — Zamknij ungracefully gniazda (Zamknij twardych).</span><span class="sxs-lookup"><span data-stu-id="b8dea-130">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
-   <span data-ttu-id="b8dea-131">Na [Begin] Zamknij — Zamknij gniazda bez problemu zmieniała (Zamknij nietrwałego).</span><span class="sxs-lookup"><span data-stu-id="b8dea-131">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
-   <span data-ttu-id="b8dea-132">sesji. CloseOutputSession — Zamknij strumień danych wychodzących (Zamknij połowa).</span><span class="sxs-lookup"><span data-stu-id="b8dea-132">session.CloseOutputSession -- shutdown the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="b8dea-133">Fabryka kanałów</span><span class="sxs-lookup"><span data-stu-id="b8dea-133">Channel Factory</span></span>  
 <span data-ttu-id="b8dea-134">Następnym krokiem w pisaniu warstwy transportowej TCP jest utworzenie implementacji klasy <xref:System.ServiceModel.Channels.IChannelFactory> kanałów klienta.</span><span class="sxs-lookup"><span data-stu-id="b8dea-134">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
-   <span data-ttu-id="b8dea-135">`WseTcpChannelFactory` pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >.</span><span class="sxs-lookup"><span data-stu-id="b8dea-135">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="b8dea-136">Jest fabrykę, która zastępuje `OnCreateChannel` można tworzyć kanały klientów.</span><span class="sxs-lookup"><span data-stu-id="b8dea-136">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   <span data-ttu-id="b8dea-137">`ClientWseTcpDuplexSessionChannel` dodaje logikę do podstawy `WseTcpDuplexSessionChannel` nawiązać połączenia z serwerem TCP na `channel.Open` czasu.</span><span class="sxs-lookup"><span data-stu-id="b8dea-137">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="b8dea-138">Nazwa hosta jest najpierw rozpoznać adres IP, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b8dea-138">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   <span data-ttu-id="b8dea-139">Następnie nazwa hosta jest podłączony do pierwszy dostępny adres IP w pętli, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b8dea-139">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   <span data-ttu-id="b8dea-140">W ramach umowy kanału, wszelkie specyficznego dla domeny wyjątki są opakowane, takich jak `SocketException` w <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="b8dea-140">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="b8dea-141">Odbiornik kanału</span><span class="sxs-lookup"><span data-stu-id="b8dea-141">Channel Listener</span></span>  
 <span data-ttu-id="b8dea-142">Następnym krokiem w pisaniu warstwy transportowej TCP jest utworzenie implementacji klasy <xref:System.ServiceModel.Channels.IChannelListener> do akceptowania kanałach serwera.</span><span class="sxs-lookup"><span data-stu-id="b8dea-142">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
-   <span data-ttu-id="b8dea-143">`WseTcpChannelListener` pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > i zastąpienia podczas otwierania [Begin] i [Begin] Zamknij, aby kontrolować okres istnienia jego gniazdo.</span><span class="sxs-lookup"><span data-stu-id="b8dea-143">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="b8dea-144">Na zdarzenia gniazdo jest tworzona do nasłuchiwania IP_ANY.</span><span class="sxs-lookup"><span data-stu-id="b8dea-144">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="b8dea-145">Implementacje bardziej zaawansowanych można utworzyć drugi gniazda do nasłuchiwania protokołu IPv6, jak również.</span><span class="sxs-lookup"><span data-stu-id="b8dea-145">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="b8dea-146">Można również zezwolić adresu IP, należy określić w nazwie hosta.</span><span class="sxs-lookup"><span data-stu-id="b8dea-146">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="b8dea-147">Po zaakceptowaniu nowe gniazdo kanał firmowy serwer jest inicjowany z tego gniazda.</span><span class="sxs-lookup"><span data-stu-id="b8dea-147">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="b8dea-148">Wszystkie dane wejściowe i wyjściowe został już zaimplementowany w klasie bazowej, więc ten kanał jest odpowiedzialny za inicjowanie gniazda.</span><span class="sxs-lookup"><span data-stu-id="b8dea-148">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="b8dea-149">Dodawanie elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="b8dea-149">Adding a Binding Element</span></span>  
 <span data-ttu-id="b8dea-150">Teraz, gdy są kompilowane fabryk i kanałów, muszą być widoczne do środowiska uruchomieniowego ServiceModel za pośrednictwem powiązania.</span><span class="sxs-lookup"><span data-stu-id="b8dea-150">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="b8dea-151">Powiązanie to kolekcja elementów wiązania, który reprezentuje stos komunikacji skojarzone z adresem usługi.</span><span class="sxs-lookup"><span data-stu-id="b8dea-151">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="b8dea-152">Każdy element w stosie jest reprezentowany przez element powiązania.</span><span class="sxs-lookup"><span data-stu-id="b8dea-152">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="b8dea-153">W tym przykładzie jest element powiązania `WseTcpTransportBindingElement`, która jest pochodną <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="b8dea-153">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="b8dea-154">Obsługuje ona <xref:System.ServiceModel.Channels.IDuplexSessionChannel> i zastępuje następujące metody do tworzenia fabryk skojarzony z powiązaniem naszych.</span><span class="sxs-lookup"><span data-stu-id="b8dea-154">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="b8dea-155">Zawiera również członków do klonowania `BindingElement` i zwracanie tym schemacie (wse.tcp).</span><span class="sxs-lookup"><span data-stu-id="b8dea-155">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="b8dea-156">TCP z usługami WSE konsoli testów</span><span class="sxs-lookup"><span data-stu-id="b8dea-156">The WSE TCP Test Console</span></span>  
 <span data-ttu-id="b8dea-157">Za pomocą transportu ten przykładowy kod testu jest dostępna w TestCode.cs.</span><span class="sxs-lookup"><span data-stu-id="b8dea-157">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="b8dea-158">Poniższe instrukcje przedstawiają sposób konfigurowania programu WSE `TcpSyncStockService` próbki.</span><span class="sxs-lookup"><span data-stu-id="b8dea-158">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="b8dea-159">Kod testu, tworzy niestandardowego powiązania, który używa kodowanie MTOM i `WseTcpTransport` transportu.</span><span class="sxs-lookup"><span data-stu-id="b8dea-159">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="b8dea-160">Konfiguruje również wersja adresowania mogła być jako zgodność z usługami WSE 3.0, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b8dea-160">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="b8dea-161">Składa się z dwóch testów — jeden test konfiguruje klient z typowaniem przy użyciu kodu wygenerowanego z usługami WSE 3.0 WSDL.</span><span class="sxs-lookup"><span data-stu-id="b8dea-161">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="b8dea-162">Drugi test używa programu WCF jako klient i serwer, wysyłając komunikaty bezpośrednio na kanale interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="b8dea-162">The second test uses WCF as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="b8dea-163">Podczas uruchamiania przykładu, należy się następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="b8dea-163">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="b8dea-164">Klient:</span><span class="sxs-lookup"><span data-stu-id="b8dea-164">Client:</span></span>  
  
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
  
 <span data-ttu-id="b8dea-165">Serwer:</span><span class="sxs-lookup"><span data-stu-id="b8dea-165">Server:</span></span>  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8dea-166">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="b8dea-166">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b8dea-167">Aby uruchomić ten przykład, konieczne jest posiadanie programu WSE 3.0 i WSE `TcpSyncStockService` przykładowe zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="b8dea-167">To run this sample, you must have WSE 3.0 and the WSE `TcpSyncStockService` sample installed.</span></span> <span data-ttu-id="b8dea-168">Możesz pobrać [programu WSE 3.0 z witryny MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).</span><span class="sxs-lookup"><span data-stu-id="b8dea-168">You can download [WSE 3.0 from MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8dea-169">Ponieważ programu WSE 3.0 nie jest obsługiwany na [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nie można zainstalować ani uruchomić `TcpSyncStockService` przykład w tym systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="b8dea-169">Because WSE 3.0 is not supported on [!INCLUDE[lserver](../../../../includes/lserver-md.md)], you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1.  <span data-ttu-id="b8dea-170">Po zainstalowaniu `TcpSyncStockService` przykładowy, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="b8dea-170">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1.  <span data-ttu-id="b8dea-171">Otwórz `TcpSyncStockService` w programie Visual Studio (Uwaga zainstalowania przykładowej TcpSyncStockService z usługami WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="b8dea-171">Open the `TcpSyncStockService` in Visual Studio (Note that the TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="b8dea-172">Nie jest częścią tego przykładu kodu).</span><span class="sxs-lookup"><span data-stu-id="b8dea-172">It is not part of this sample's code).</span></span>  
  
    2.  <span data-ttu-id="b8dea-173">Ustaw projekt StockService jako projekt startowy.</span><span class="sxs-lookup"><span data-stu-id="b8dea-173">Set the StockService project as the start up project.</span></span>  
  
    3.  <span data-ttu-id="b8dea-174">Otwórz StockService.cs w projekcie StockService i komentarz dla atrybutu [zasady] na `StockService` klasy.</span><span class="sxs-lookup"><span data-stu-id="b8dea-174">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="b8dea-175">Powoduje to wyłączenie zabezpieczeń z próbki.</span><span class="sxs-lookup"><span data-stu-id="b8dea-175">This disables security from the sample.</span></span> <span data-ttu-id="b8dea-176">Gdy WCF może współpracować z usługami WSE 3.0 bezpieczne punkty końcowe, zabezpieczeń jest wyłączona, aby zachować ten przykład koncentruje się na niestandardowej warstwy transportowej TCP.</span><span class="sxs-lookup"><span data-stu-id="b8dea-176">While WCF can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4.  <span data-ttu-id="b8dea-177">Naciśnij klawisz F5, aby rozpocząć `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="b8dea-177">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="b8dea-178">Usługa jest uruchamiana w nowym oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="b8dea-178">The service starts in a new console window.</span></span>  
  
    5.  <span data-ttu-id="b8dea-179">Otwórz w tym przykładzie transportu TCP w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b8dea-179">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6.  <span data-ttu-id="b8dea-180">Aktualizacja zmiennej "Nazwa hosta" w TestCode.cs do dopasowania uruchomiona Nazwa maszyny `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="b8dea-180">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7.  <span data-ttu-id="b8dea-181">Naciśnij klawisz F5, aby uruchomić przykład transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="b8dea-181">Press F5 to start the TCP transport sample.</span></span>  
  
    8.  <span data-ttu-id="b8dea-182">Klient testowy transportu TCP rozpoczyna się w nowej konsoli.</span><span class="sxs-lookup"><span data-stu-id="b8dea-182">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="b8dea-183">Klient żąda giełdowych z usługi i następnie wyświetla wyniki w oknie swojej konsoli.</span><span class="sxs-lookup"><span data-stu-id="b8dea-183">The client requests stock quotes from the service and then displays the results in its console window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8dea-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8dea-184">See Also</span></span>
