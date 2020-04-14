---
title: 'Transport: Współdziałanie protokołu TCP z usługami WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: f799f3b6968f31472acc7752846bab34351648db
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278902"
---
# <a name="transport-wse-30-tcp-interoperability"></a><span data-ttu-id="11711-102">Transport: Współdziałanie protokołu TCP z usługami WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="11711-102">Transport: WSE 3.0 TCP Interoperability</span></span>
<span data-ttu-id="11711-103">Przykład transportu interoperacyjności protokołu WSE 3.0 TCP pokazuje, jak zaimplementować sesję dupleksu TCP jako niestandardowy transport programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="11711-103">The WSE 3.0 TCP Interoperability Transport sample demonstrates how to implement a TCP duplex session as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="11711-104">Pokazano również, jak można użyć rozszerzalności warstwy kanału do interfejsu przez przewod z istniejącymi wdrożonymi systemami.</span><span class="sxs-lookup"><span data-stu-id="11711-104">It also demonstrates how you can use the extensibility of the channel layer to interface over the wire with existing deployed systems.</span></span> <span data-ttu-id="11711-105">Poniższe kroki pokazują, jak utworzyć ten niestandardowy transport WCF:</span><span class="sxs-lookup"><span data-stu-id="11711-105">The following steps show how to build this custom WCF transport:</span></span>  
  
1. <span data-ttu-id="11711-106">Począwszy od gniazda TCP, należy utworzyć <xref:System.ServiceModel.Channels.IDuplexSessionChannel> implementacje klienta i serwera, których użycie służy do wytyczania granic wiadomości przez moduł DIME Framing.</span><span class="sxs-lookup"><span data-stu-id="11711-106">Starting with a TCP socket, create client and server implementations of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> that use DIME Framing to delineate message boundaries.</span></span>  
  
2. <span data-ttu-id="11711-107">Utwórz fabrykę kanałów, która łączy się z usługą GPW <xref:System.ServiceModel.Channels.IDuplexSessionChannel>TCP i wysyła wiadomości w ramkach za pomocą klienta s.</span><span class="sxs-lookup"><span data-stu-id="11711-107">Create a channel factory that connects to a WSE TCP service and sends framed messages over the client <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.</span></span>  
  
3. <span data-ttu-id="11711-108">Utwórz odbiornik kanałów, aby akceptować przychodzące połączenia TCP i tworzyć odpowiednie kanały.</span><span class="sxs-lookup"><span data-stu-id="11711-108">Create a channel listener to accept incoming TCP connections and produce corresponding channels.</span></span>  
  
4. <span data-ttu-id="11711-109">Upewnij się, że wszelkie wyjątki specyficzne dla sieci <xref:System.ServiceModel.CommunicationException>są znormalizowane do odpowiedniej klasy pochodnej .</span><span class="sxs-lookup"><span data-stu-id="11711-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
5. <span data-ttu-id="11711-110">Dodaj element wiązania, który dodaje niestandardowy transport do stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="11711-110">Add a binding element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="11711-111">Aby uzyskać więcej informacji, zobacz [Dodawanie elementu wiązania].</span><span class="sxs-lookup"><span data-stu-id="11711-111">For more information, see [Adding a Binding Element].</span></span>  
  
## <a name="creating-iduplexsessionchannel"></a><span data-ttu-id="11711-112">Tworzenie iduplexSessionChannel</span><span class="sxs-lookup"><span data-stu-id="11711-112">Creating IDuplexSessionChannel</span></span>  
 <span data-ttu-id="11711-113">Pierwszym krokiem w pisaniu GPW 3.0 TCP Interoperability <xref:System.ServiceModel.Channels.IDuplexSessionChannel> Transport jest <xref:System.Net.Sockets.Socket>stworzenie implementacji na szczycie .</span><span class="sxs-lookup"><span data-stu-id="11711-113">The first step in writing the WSE 3.0 TCP Interoperability Transport is to create an implementation of <xref:System.ServiceModel.Channels.IDuplexSessionChannel> on top of a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="11711-114">`WseTcpDuplexSessionChannel`pochodzi od <xref:System.ServiceModel.Channels.ChannelBase>.</span><span class="sxs-lookup"><span data-stu-id="11711-114">`WseTcpDuplexSessionChannel` derives from <xref:System.ServiceModel.Channels.ChannelBase>.</span></span> <span data-ttu-id="11711-115">Logika wysyłania wiadomości składa się z dwóch głównych elementów: (1) kodowania wiadomości w bajty i (2) kadrowania tych bajtów i wysyłania ich na sieć.</span><span class="sxs-lookup"><span data-stu-id="11711-115">The logic of sending a message consists of two main pieces: (1) Encoding the message into bytes, and (2) framing those bytes and sending them on the wire.</span></span>  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 <span data-ttu-id="11711-116">Ponadto blokada jest pobierana tak, że Send() wywołania zachować IDuplexSessionChannel gwarancji w kolejności i tak, że wywołania do gniazda źródłowego są poprawnie zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="11711-116">In addition, a lock is taken so that the Send() calls preserve the IDuplexSessionChannel in-order guarantee, and so that calls to the underlying socket are synchronized correctly.</span></span>  
  
 <span data-ttu-id="11711-117">`WseTcpDuplexSessionChannel`używa a <xref:System.ServiceModel.Channels.MessageEncoder> do tłumaczenia na bajt <xref:System.ServiceModel.Channels.Message> i z bajtu[].</span><span class="sxs-lookup"><span data-stu-id="11711-117">`WseTcpDuplexSessionChannel` uses a <xref:System.ServiceModel.Channels.MessageEncoder> for translating a <xref:System.ServiceModel.Channels.Message> to and from byte[].</span></span> <span data-ttu-id="11711-118">Ponieważ jest to `WseTcpDuplexSessionChannel` transport, jest również odpowiedzialny za zastosowanie adresu zdalnego, który został skonfigurowany z kanałem.</span><span class="sxs-lookup"><span data-stu-id="11711-118">Because it is a transport, `WseTcpDuplexSessionChannel` is also responsible for applying the remote address that the channel was configured with.</span></span> <span data-ttu-id="11711-119">`EncodeMessage`hermetyzuje logikę tej konwersji.</span><span class="sxs-lookup"><span data-stu-id="11711-119">`EncodeMessage` encapsulates the logic for this conversion.</span></span>  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 <span data-ttu-id="11711-120">Gdy <xref:System.ServiceModel.Channels.Message> jest zakodowany w bajtach, musi być przesyłany na przewodach.</span><span class="sxs-lookup"><span data-stu-id="11711-120">Once the <xref:System.ServiceModel.Channels.Message> is encoded into bytes, it must be transmitted on the wire.</span></span> <span data-ttu-id="11711-121">Wymaga to systemu do definiowania granic wiadomości.</span><span class="sxs-lookup"><span data-stu-id="11711-121">This requires a system for defining message boundaries.</span></span> <span data-ttu-id="11711-122">WSE 3.0 używa wersji [DIME](https://docs.microsoft.com/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) jako protokołu kadrowania.</span><span class="sxs-lookup"><span data-stu-id="11711-122">WSE 3.0 uses a version of [DIME](https://docs.microsoft.com/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) as its framing protocol.</span></span> <span data-ttu-id="11711-123">`WriteData`hermetyzuje logikę kadrowania, aby zawinąć bajt[] w zestaw rekordów DIME.</span><span class="sxs-lookup"><span data-stu-id="11711-123">`WriteData` encapsulates the framing logic to wrap a byte[] into a set of DIME records.</span></span>  
  
 <span data-ttu-id="11711-124">Logika odbierania wiadomości jest podobna.</span><span class="sxs-lookup"><span data-stu-id="11711-124">The logic for receiving messages is similar.</span></span> <span data-ttu-id="11711-125">Główną złożonością jest obsługa faktu, że odczyt gniazda może zwrócić mniej bajtów niż zostały wymagane.</span><span class="sxs-lookup"><span data-stu-id="11711-125">The main complexity is handling the fact that a socket read can return fewer bytes than were requested.</span></span> <span data-ttu-id="11711-126">Aby otrzymać wiadomość, `WseTcpDuplexSessionChannel` odczytuje bajty z przewodu, dekoduje kadrowanie DIME, a następnie używa <xref:System.ServiceModel.Channels.Message> <xref:System.ServiceModel.Channels.MessageEncoder> do przekształcania bajtu[] w plik .</span><span class="sxs-lookup"><span data-stu-id="11711-126">To receive a message, `WseTcpDuplexSessionChannel` reads bytes off the wire, decodes the DIME framing, and then uses the <xref:System.ServiceModel.Channels.MessageEncoder> for turning the byte[] into a <xref:System.ServiceModel.Channels.Message>.</span></span>  
  
 <span data-ttu-id="11711-127">Podstawa `WseTcpDuplexSessionChannel` zakłada, że odbiera podłączone gniazdo.</span><span class="sxs-lookup"><span data-stu-id="11711-127">The base `WseTcpDuplexSessionChannel` assumes that it receives a connected socket.</span></span> <span data-ttu-id="11711-128">Klasa podstawowa obsługuje zamknięcie gniazda.</span><span class="sxs-lookup"><span data-stu-id="11711-128">The base class handles socket shutdown.</span></span> <span data-ttu-id="11711-129">Istnieją trzy miejsca, które interfejs z zamknięciem gniazda:</span><span class="sxs-lookup"><span data-stu-id="11711-129">There are three places that interface with socket closure:</span></span>  
  
- <span data-ttu-id="11711-130">OnAbort -- zamknij gniazdo bezgranicznie (twarde zamknięcie).</span><span class="sxs-lookup"><span data-stu-id="11711-130">OnAbort -- close the socket ungracefully (hard close).</span></span>  
  
- <span data-ttu-id="11711-131">On[Begin]Close -- zamknij gniazdo bezpiecznie (miękkie zamknięcie).</span><span class="sxs-lookup"><span data-stu-id="11711-131">On[Begin]Close -- close the socket gracefully (soft close).</span></span>  
  
- <span data-ttu-id="11711-132">Sesji. CloseOutputSession - zamknij strumień danych wychodzących (połowa zamknięcia).</span><span class="sxs-lookup"><span data-stu-id="11711-132">session.CloseOutputSession -- shut down the outbound data stream (half close).</span></span>  
  
## <a name="channel-factory"></a><span data-ttu-id="11711-133">Fabryka kanałów</span><span class="sxs-lookup"><span data-stu-id="11711-133">Channel Factory</span></span>  
 <span data-ttu-id="11711-134">Następnym krokiem w pisaniu transportu TCP <xref:System.ServiceModel.Channels.IChannelFactory> jest utworzenie implementacji dla kanałów klienta.</span><span class="sxs-lookup"><span data-stu-id="11711-134">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels.</span></span>  
  
- <span data-ttu-id="11711-135">`WseTcpChannelFactory`pochodzi z <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel>.</span><span class="sxs-lookup"><span data-stu-id="11711-135">`WseTcpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel>.</span></span> <span data-ttu-id="11711-136">Jest to fabryka, `OnCreateChannel` która zastępuje do produkcji kanałów klienta.</span><span class="sxs-lookup"><span data-stu-id="11711-136">It is a factory that overrides `OnCreateChannel` to produce client channels.</span></span>  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- <span data-ttu-id="11711-137">`ClientWseTcpDuplexSessionChannel`dodaje logikę `WseTcpDuplexSessionChannel` do bazy, aby połączyć się z serwerem TCP w `channel.Open` czasie.</span><span class="sxs-lookup"><span data-stu-id="11711-137">`ClientWseTcpDuplexSessionChannel` adds logic to the base `WseTcpDuplexSessionChannel` to connect to a TCP server at `channel.Open` time.</span></span> <span data-ttu-id="11711-138">Najpierw nazwa hosta jest rozpoznawana na adres IP, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="11711-138">First the hostname is resolved to an IP address, as shown in the following code.</span></span>  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- <span data-ttu-id="11711-139">Następnie nazwa hosta jest podłączona do pierwszego dostępnego adresu IP w pętli, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="11711-139">Then the hostname is connected to the first available IP address in a loop, as shown in the following code.</span></span>  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- <span data-ttu-id="11711-140">W ramach umowy kanału wszelkie wyjątki specyficzne dla `SocketException` domeny <xref:System.ServiceModel.CommunicationException>są zawijane, na przykład w .</span><span class="sxs-lookup"><span data-stu-id="11711-140">As part of the channel contract, any domain-specific exceptions are wrapped, such as `SocketException` in <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
## <a name="channel-listener"></a><span data-ttu-id="11711-141">Odbiornik kanałów</span><span class="sxs-lookup"><span data-stu-id="11711-141">Channel Listener</span></span>  
 <span data-ttu-id="11711-142">Następnym krokiem w pisaniu transportu TCP <xref:System.ServiceModel.Channels.IChannelListener> jest utworzenie implementacji do akceptowania kanałów serwera.</span><span class="sxs-lookup"><span data-stu-id="11711-142">The next step in writing the TCP transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelListener> for accepting server channels.</span></span>  
  
- <span data-ttu-id="11711-143">`WseTcpChannelListener`pochodzi z <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel> i zastępuje On[Begin]Open i On[Begin]Close, aby kontrolować okres istnienia gniazda nasłuchicia.</span><span class="sxs-lookup"><span data-stu-id="11711-143">`WseTcpChannelListener` derives from <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel> and overrides On[Begin]Open and On[Begin]Close to control the lifetime of its listen socket.</span></span> <span data-ttu-id="11711-144">W OnOpen, gniazdo jest tworzony do nasłuchiwać na IP_ANY.</span><span class="sxs-lookup"><span data-stu-id="11711-144">In OnOpen, a socket is created to listen on IP_ANY.</span></span> <span data-ttu-id="11711-145">Bardziej zaawansowane implementacje można utworzyć drugie gniazdo do nasłuchiwać na IPv6, jak również.</span><span class="sxs-lookup"><span data-stu-id="11711-145">More advanced implementations can create a second socket to listen on IPv6 as well.</span></span> <span data-ttu-id="11711-146">Mogą również zezwolić na adres IP, który ma być określony w nazwach hosta.</span><span class="sxs-lookup"><span data-stu-id="11711-146">They can also allow the IP address to be specified in the hostname.</span></span>  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 <span data-ttu-id="11711-147">Po zaakceptowaniu nowego gniazda kanał serwera jest inicjowany za pomocą tego gniazda.</span><span class="sxs-lookup"><span data-stu-id="11711-147">When a new socket is accepted, a server channel is initialized with this socket.</span></span> <span data-ttu-id="11711-148">Wszystkie dane wejściowe i wyjściowe są już zaimplementowane w klasie podstawowej, więc ten kanał jest odpowiedzialny za inicjowanie gniazda.</span><span class="sxs-lookup"><span data-stu-id="11711-148">All the input and output is already implemented in the base class, so this channel is responsible for initializing the socket.</span></span>  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="11711-149">Dodawanie elementu wiązania</span><span class="sxs-lookup"><span data-stu-id="11711-149">Adding a Binding Element</span></span>  
 <span data-ttu-id="11711-150">Teraz, gdy fabryki i kanały są budowane, muszą być widoczne na servicemodel środowiska uruchomieniowego za pośrednictwem powiązania.</span><span class="sxs-lookup"><span data-stu-id="11711-150">Now that the factories and channels are built, they must be exposed to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="11711-151">Powiązanie jest kolekcją elementów wiązania, który reprezentuje stos komunikacji skojarzony z adresem usługi.</span><span class="sxs-lookup"><span data-stu-id="11711-151">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="11711-152">Każdy element w stosie jest reprezentowany przez element wiązania.</span><span class="sxs-lookup"><span data-stu-id="11711-152">Each element in the stack is represented by a binding element.</span></span>  
  
 <span data-ttu-id="11711-153">W próbce element wiązania `WseTcpTransportBindingElement`jest , <xref:System.ServiceModel.Channels.TransportBindingElement>który pochodzi z .</span><span class="sxs-lookup"><span data-stu-id="11711-153">In the sample, the binding element is `WseTcpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="11711-154">Obsługuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> i zastępuje następujące metody tworzenia fabryk skojarzonych z naszym powiązaniem.</span><span class="sxs-lookup"><span data-stu-id="11711-154">It supports <xref:System.ServiceModel.Channels.IDuplexSessionChannel> and overrides the following methods to build the factories associated with our binding.</span></span>  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 <span data-ttu-id="11711-155">Zawiera również członków do `BindingElement` klonowania i zwracania naszego programu (wse.tcp).</span><span class="sxs-lookup"><span data-stu-id="11711-155">It also contains members for cloning the `BindingElement` and returning our scheme (wse.tcp).</span></span>  
  
## <a name="the-wse-tcp-test-console"></a><span data-ttu-id="11711-156">Konsola testna GPW TCP</span><span class="sxs-lookup"><span data-stu-id="11711-156">The WSE TCP Test Console</span></span>  
 <span data-ttu-id="11711-157">Kod testowy do korzystania z tego przykładowego transportu jest dostępny w TestCode.cs.</span><span class="sxs-lookup"><span data-stu-id="11711-157">Test code for using this sample transport is available in TestCode.cs.</span></span> <span data-ttu-id="11711-158">Poniższe instrukcje pokazują, jak skonfigurować `TcpSyncStockService` przykład GPW.</span><span class="sxs-lookup"><span data-stu-id="11711-158">The following instructions show how to set up the WSE `TcpSyncStockService` sample.</span></span>  
  
 <span data-ttu-id="11711-159">Kod testowy tworzy niestandardowe powiązanie, które używa `WseTcpTransport` MTOM jako kodowania i jako transportu.</span><span class="sxs-lookup"><span data-stu-id="11711-159">The test code creates a custom binding that uses MTOM as the encoding and `WseTcpTransport` as the transport.</span></span> <span data-ttu-id="11711-160">Konfiguruje również AddressingVersion być zgodne z GPW 3.0, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="11711-160">It also sets up the AddressingVersion to be conformant with WSE 3.0, as shown in the following code.</span></span>  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 <span data-ttu-id="11711-161">Składa się z dwóch testów — jeden test konfiguruje wpisanego klienta przy użyciu kodu wygenerowanego z WSDL WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="11711-161">It consists of two tests—one test sets up a typed client using code generated from the WSE 3.0 WSDL.</span></span> <span data-ttu-id="11711-162">Drugi test używa WCF jako klienta i serwera, wysyłając wiadomości bezpośrednio na górze interfejsów API kanału.</span><span class="sxs-lookup"><span data-stu-id="11711-162">The second test uses WCF as both the client and the server by sending messages directly on top of the channel APIs.</span></span>  
  
 <span data-ttu-id="11711-163">Podczas uruchamiania próbki oczekuje się następującego wyjścia.</span><span class="sxs-lookup"><span data-stu-id="11711-163">When running the sample, the following output is expected.</span></span>  
  
 <span data-ttu-id="11711-164">Klient:</span><span class="sxs-lookup"><span data-stu-id="11711-164">Client:</span></span>  
  
```console  
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
  
 <span data-ttu-id="11711-165">Serwer:</span><span class="sxs-lookup"><span data-stu-id="11711-165">Server:</span></span>  
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="11711-166">Konfigurowanie, tworzenie i uruchamianie próbki</span><span class="sxs-lookup"><span data-stu-id="11711-166">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="11711-167">Aby uruchomić ten przykład, musisz mieć [ulepszenia usług sieci Web (GPSE) 3.0 dla firmy Microsoft .NET](https://www.microsoft.com/download/details.aspx?id=14089) i `TcpSyncStockService` zainstalowano przykład gpw.</span><span class="sxs-lookup"><span data-stu-id="11711-167">To run this sample, you must have [Web Services Enhancements (WSE) 3.0 for Microsoft .NET](https://www.microsoft.com/download/details.aspx?id=14089) and the WSE `TcpSyncStockService` sample installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="11711-168">Ponieważ usługa WSE 3.0 nie jest obsługiwana w systemie Windows Server `TcpSyncStockService` 2008, nie można zainstalować ani uruchomić próbki w tym systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="11711-168">Because WSE 3.0 is not supported on Windows Server 2008, you cannot install or run the `TcpSyncStockService` sample on that operating system.</span></span>  
  
1. <span data-ttu-id="11711-169">Po zainstalowaniu `TcpSyncStockService` próbki wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="11711-169">Once you install the `TcpSyncStockService` sample, do the following:</span></span>  
  
    1. <span data-ttu-id="11711-170">Otwórz `TcpSyncStockService` program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11711-170">Open the `TcpSyncStockService` in Visual Studio.</span></span> <span data-ttu-id="11711-171">(Próbka TcpSyncStockService jest zainstalowana z gpw 3.0.</span><span class="sxs-lookup"><span data-stu-id="11711-171">(The TcpSyncStockService sample is installed with WSE 3.0.</span></span> <span data-ttu-id="11711-172">Nie jest częścią kodu tego przykładu.)</span><span class="sxs-lookup"><span data-stu-id="11711-172">It is not part of this sample's code.)</span></span>  
  
    2. <span data-ttu-id="11711-173">Ustaw projekt StockService jako projekt startowy.</span><span class="sxs-lookup"><span data-stu-id="11711-173">Set the StockService project as the start-up project.</span></span>  
  
    3. <span data-ttu-id="11711-174">Otwórz StockService.cs w projekcie StockService i skomentuj atrybut `StockService` [Zasady] w klasie.</span><span class="sxs-lookup"><span data-stu-id="11711-174">Open StockService.cs in the StockService project and comment out the [Policy] attribute on the `StockService` class.</span></span> <span data-ttu-id="11711-175">Spowoduje to wyłączenie zabezpieczeń z przykładu.</span><span class="sxs-lookup"><span data-stu-id="11711-175">This disables security from the sample.</span></span> <span data-ttu-id="11711-176">Podczas WCF można współpracować z gpw 3.0 bezpiecznych punktów końcowych, zabezpieczenia jest wyłączona, aby utrzymać ten przykład koncentruje się na niestandardowy transport TCP.</span><span class="sxs-lookup"><span data-stu-id="11711-176">While WCF can interoperate with WSE 3.0 secure endpoints, security is disabled to keep this sample focused on the custom TCP transport.</span></span>  
  
    4. <span data-ttu-id="11711-177">Naciśnij klawisz F5, aby uruchomić przycisk `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="11711-177">Press F5 to start the `TcpSyncStockService`.</span></span> <span data-ttu-id="11711-178">Usługa zostanie uruchomiony w nowym oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="11711-178">The service starts in a new console window.</span></span>  
  
    5. <span data-ttu-id="11711-179">Otwórz ten przykład transportu TCP w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11711-179">Open this TCP transport sample in Visual Studio.</span></span>  
  
    6. <span data-ttu-id="11711-180">Zaktualizuj zmienną "nazwa hosta" w TestCode.cs, aby dopasować nazwę komputera z uruchomionym programem `TcpSyncStockService`.</span><span class="sxs-lookup"><span data-stu-id="11711-180">Update the "hostname" variable in TestCode.cs to match the machine name running the `TcpSyncStockService`.</span></span>  
  
    7. <span data-ttu-id="11711-181">Naciśnij klawisz F5, aby uruchomić próbkę transportu TCP.</span><span class="sxs-lookup"><span data-stu-id="11711-181">Press F5 to start the TCP transport sample.</span></span>  
  
    8. <span data-ttu-id="11711-182">Klient testu transportu TCP uruchamia się w nowej konsoli.</span><span class="sxs-lookup"><span data-stu-id="11711-182">The TCP transport test client starts in a new console.</span></span> <span data-ttu-id="11711-183">Klient żąda notowań akcji z usługi, a następnie wyświetla wyniki w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="11711-183">The client requests stock quotes from the service and then displays the results in its console window.</span></span>  
