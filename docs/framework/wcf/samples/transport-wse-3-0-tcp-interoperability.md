---
title: 'Transport: Współdziałanie protokołu TCP z usługami WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
ms.openlocfilehash: b727da998736944afd23f7dcfbf45a1f6049d1d0
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085969"
---
# <a name="transport-wse-30-tcp-interoperability"></a>Transport: Współdziałanie protokołu TCP z usługami WSE 3.0
Przykładowe programu WSE 3.0 protokołu TCP współdziałanie transportu demonstruje sposób implementacji dwukierunkowego sesji TCP jako niestandardowy transportu Windows Communication Foundation (WCF). Ilustruje też, jak można użyć rozszerzalności warstwy kanału do interfejsu przez sieć z istniejącymi systemami wdrożone. Poniższe kroki pokazują jak utworzyć niestandardowe transport WCF:  
  
1.  Począwszy od gniazda TCP, utworzyć klienta i serwera implementacje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> używające ramek DIME aby odróżnić granice wiadomości.  
  
2.  Tworzenie fabryki kanałów, łączy się z usługą programu WSE TCP, która wysyła komunikaty ramce przez klienta <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.  
  
3.  Utwórz odbiornik kanału, aby zaakceptować połączenia przychodzące TCP i tworzyć kanały.  
  
4.  Upewnij się, że wszystkie wyjątki dotyczące sieci są znormalizowane zgodnie z odpowiedniej klasy pochodnej z <xref:System.ServiceModel.CommunicationException>.  
  
5.  Dodaj element powiązania, który dodaje niestandardowy transportu do stosu kanału. Aby uzyskać więcej informacji zobacz [Dodawanie elementu powiązania].  
  
## <a name="creating-iduplexsessionchannel"></a>Tworzenie IDuplexSessionChannel  
 Pierwszym krokiem podczas pisania transportu współdziałania programu WSE 3.0 protokołu TCP jest utworzenie implementacji klasy <xref:System.ServiceModel.Channels.IDuplexSessionChannel> w górnej części <xref:System.Net.Sockets.Socket>. `WseTcpDuplexSessionChannel` pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelBase>. Logika wysyłania komunikatu składa się z dwóch głównych elementów: (1) kodowanie wiadomości w bajtach i (2) ramek tych bajtów i wysyłając przesyłania.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Ponadto blokady jest pobierana w celu wywołania Send() zachowania gwarancji w kolejności IDuplexSessionChannel i tak, aby wywołania do gniazda podstawowej są poprawnie synchronizowane.  
  
 `WseTcpDuplexSessionChannel` używa <xref:System.ServiceModel.Channels.MessageEncoder> do tłumaczenia <xref:System.ServiceModel.Channels.Message> do i z byte []. Ponieważ jest on transportu `WseTcpDuplexSessionChannel` jest również odpowiedzialny za stosowanie adresów zdalnych, której skonfigurowano kanał. `EncodeMessage` hermetyzuje logikę tej konwersji.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 Gdy <xref:System.ServiceModel.Channels.Message> jest zakodowany w bajtach, muszą być przekazywane w sieci. Wymaga to systemu do definiowania granice wiadomości. Programu WSE 3.0 korzysta z wersji [DIME](https://go.microsoft.com/fwlink/?LinkId=94999) jako protokół ramek. `WriteData` hermetyzuje logikę ramek do opakowania byte [] do zestawu rekordów DIME.  
  
 Logika do odbierania wiadomości jest bardzo podobne. Złożoność głównego jest obsługa fakt, że gniazdo odczyt może zwrócić mniej bajtów niż zażądano. Aby otrzymać komunikat, `WseTcpDuplexSessionChannel` odczytuje bajtów wyłączone podczas transmisji, dekoduje ramek DIME, a następnie używa <xref:System.ServiceModel.Channels.MessageEncoder> Włączanie byte [] do <xref:System.ServiceModel.Channels.Message>.  
  
 Podstawa `WseTcpDuplexSessionChannel` przyjęto założenie, że będzie ona otrzymywać połączone gniazdo. Klasa bazowa obsługuje zamykania gniazda. Istnieją trzy miejsca, z gniazda zamknięcia:  
  
-   OnAbort — Zamknij ungracefully gniazda (Zamknij twardych).  
  
-   Na [Begin] Zamknij — Zamknij gniazda bez problemu zmieniała (Zamknij nietrwałego).  
  
-   sesji. CloseOutputSession — Zamknij strumień danych wychodzących (Zamknij połowa).  
  
## <a name="channel-factory"></a>Fabryka kanałów  
 Następnym krokiem w pisaniu warstwy transportowej TCP jest utworzenie implementacji klasy <xref:System.ServiceModel.Channels.IChannelFactory> kanałów klienta.  
  
-   `WseTcpChannelFactory` pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >. Jest fabrykę, która zastępuje `OnCreateChannel` można tworzyć kanały klientów.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   `ClientWseTcpDuplexSessionChannel` dodaje logikę do podstawy `WseTcpDuplexSessionChannel` nawiązać połączenia z serwerem TCP na `channel.Open` czasu. Nazwa hosta jest najpierw rozpoznać adres IP, jak pokazano w poniższym kodzie.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   Następnie nazwa hosta jest podłączony do pierwszy dostępny adres IP w pętli, jak pokazano w poniższym kodzie.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   W ramach umowy kanału, wszelkie specyficznego dla domeny wyjątki są opakowane, takich jak `SocketException` w <xref:System.ServiceModel.CommunicationException>.  
  
## <a name="channel-listener"></a>Odbiornik kanału  
 Następnym krokiem w pisaniu warstwy transportowej TCP jest utworzenie implementacji klasy <xref:System.ServiceModel.Channels.IChannelListener> do akceptowania kanałach serwera.  
  
-   `WseTcpChannelListener` pochodzi od klasy <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > i zastąpienia podczas otwierania [Begin] i [Begin] Zamknij, aby kontrolować okres istnienia jego gniazdo. Na zdarzenia gniazdo jest tworzona do nasłuchiwania IP_ANY. Implementacje bardziej zaawansowanych można utworzyć drugi gniazda do nasłuchiwania protokołu IPv6, jak również. Można również zezwolić adresu IP, należy określić w nazwie hosta.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Po zaakceptowaniu nowe gniazdo kanał firmowy serwer jest inicjowany z tego gniazda. Wszystkie dane wejściowe i wyjściowe został już zaimplementowany w klasie bazowej, więc ten kanał jest odpowiedzialny za inicjowanie gniazda.  
  
## <a name="adding-a-binding-element"></a>Dodawanie elementu powiązania  
 Teraz, gdy są kompilowane fabryk i kanałów, muszą być widoczne do środowiska uruchomieniowego ServiceModel za pośrednictwem powiązania. Powiązanie to kolekcja elementów wiązania, który reprezentuje stos komunikacji skojarzone z adresem usługi. Każdy element w stosie jest reprezentowany przez element powiązania.  
  
 W tym przykładzie jest element powiązania `WseTcpTransportBindingElement`, która jest pochodną <xref:System.ServiceModel.Channels.TransportBindingElement>. Obsługuje ona <xref:System.ServiceModel.Channels.IDuplexSessionChannel> i zastępuje następujące metody do tworzenia fabryk skojarzony z powiązaniem naszych.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Zawiera również członków do klonowania `BindingElement` i zwracanie tym schemacie (wse.tcp).  
  
## <a name="the-wse-tcp-test-console"></a>TCP z usługami WSE konsoli testów  
 Za pomocą transportu ten przykładowy kod testu jest dostępna w TestCode.cs. Poniższe instrukcje przedstawiają sposób konfigurowania programu WSE `TcpSyncStockService` próbki.  
  
 Kod testu, tworzy niestandardowego powiązania, który używa kodowanie MTOM i `WseTcpTransport` transportu. Konfiguruje również wersja adresowania mogła być jako zgodność z usługami WSE 3.0, jak pokazano w poniższym kodzie.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 Składa się z dwóch testów — jeden test konfiguruje klient z typowaniem przy użyciu kodu wygenerowanego z usługami WSE 3.0 WSDL. Drugi test używa programu WCF jako klient i serwer, wysyłając komunikaty bezpośrednio na kanale interfejsów API.  
  
 Podczas uruchamiania przykładu, należy się następujące dane wyjściowe.  
  
 Klient:  
  
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
  
 Serwer:  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Aby uruchomić ten przykład, konieczne jest posiadanie programu WSE 3.0 i WSE `TcpSyncStockService` przykładowe zainstalowane. Możesz pobrać [programu WSE 3.0 z witryny MSDN](https://go.microsoft.com/fwlink/?LinkId=95000).  
  
> [!NOTE]
>  Ponieważ programu WSE 3.0 nie jest obsługiwany na [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nie można zainstalować ani uruchomić `TcpSyncStockService` przykład w tym systemie operacyjnym.  
  
1.  Po zainstalowaniu `TcpSyncStockService` przykładowy, wykonaj następujące czynności:  
  
    1.  Otwórz `TcpSyncStockService` w programie Visual Studio (Uwaga zainstalowania przykładowej TcpSyncStockService z usługami WSE 3.0. Nie jest częścią tego przykładu kodu).  
  
    2.  Ustaw projekt StockService jako projekt startowy.  
  
    3.  Otwórz StockService.cs w projekcie StockService i komentarz dla atrybutu [zasady] na `StockService` klasy. Powoduje to wyłączenie zabezpieczeń z próbki. Gdy WCF może współpracować z usługami WSE 3.0 bezpieczne punkty końcowe, zabezpieczeń jest wyłączona, aby zachować ten przykład koncentruje się na niestandardowej warstwy transportowej TCP.  
  
    4.  Naciśnij klawisz F5, aby rozpocząć `TcpSyncStockService`. Usługa jest uruchamiana w nowym oknie konsoli.  
  
    5.  Otwórz w tym przykładzie transportu TCP w programie Visual Studio.  
  
    6.  Aktualizacja zmiennej "Nazwa hosta" w TestCode.cs do dopasowania uruchomiona Nazwa maszyny `TcpSyncStockService`.  
  
    7.  Naciśnij klawisz F5, aby uruchomić przykład transportu TCP.  
  
    8.  Klient testowy transportu TCP rozpoczyna się w nowej konsoli. Klient żąda giełdowych z usługi i następnie wyświetla wyniki w oknie swojej konsoli.  
  
## <a name="see-also"></a>Zobacz też
