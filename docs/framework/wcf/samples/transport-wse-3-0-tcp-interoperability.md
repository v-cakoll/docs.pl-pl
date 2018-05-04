---
title: 'Transport: Współdziałanie protokołu TCP z usługami WSE 3.0'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9ce948a9239e7a8171424fa9f1cf0fa8624d0156
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="transport-wse-30-tcp-interoperability"></a>Transport: Współdziałanie protokołu TCP z usługami WSE 3.0
Przykładowe WSE 3.0 TCP współdziałanie transportu pokazano, jak zaimplementować sesji dupleksowej TCP jako niestandardowego transportu Windows Communication Foundation (WCF). Przedstawiono również, jak używasz rozszerzalności warstwy kanału do interfejsu przez sieć z istniejącymi systemami wdrożone. W następujących krokach przedstawiono sposób tworzenia tej niestandardowej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transportu:  
  
1.  Począwszy od gniazda TCP, utworzyć klienta i serwera implementacje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> który umożliwia DIME Framing odróżniać granice wiadomości.  
  
2.  Tworzenie fabryki kanałów, który jest podłączany do usługi WSE TCP i wysyła ramce wiadomości przez klienta <xref:System.ServiceModel.Channels.IDuplexSessionChannel>s.  
  
3.  Utwórz odbiornik kanału do akceptowania przychodzących połączeń TCP oraz tworzenia kanały.  
  
4.  Upewnij się, że wszelkie wyjątki dotyczące sieci są znormalizowane do odpowiedniej klasy pochodnej z <xref:System.ServiceModel.CommunicationException>.  
  
5.  Dodaj element powiązania, który dodaje niestandardowy transportu do stosu kanału. Aby uzyskać więcej informacji zobacz [Dodawanie elementu powiązania].  
  
## <a name="creating-iduplexsessionchannel"></a>Tworzenie IDuplexSessionChannel  
 Pierwszą czynnością przy tworzeniu transportu współdziałanie programu WSE 3.0 protokołu TCP jest utworzenie implementacja <xref:System.ServiceModel.Channels.IDuplexSessionChannel> nad <xref:System.Net.Sockets.Socket>. `WseTcpDuplexSessionChannel` pochodną <xref:System.ServiceModel.Channels.ChannelBase>. Logika wysyłania wiadomości składa się z dwóch głównych elementów: (1) Kodowanie komunikatu na bajty oraz (2) framing tych bajtów i wysyłania ich przesyłania.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Ponadto blokady jest zajęty, aby wywołania Send() zachować gwarancji w kolejności IDuplexSessionChannel i tak, aby wywołania do gniazda podstawowej są poprawnie synchronizowane.  
  
 `WseTcpDuplexSessionChannel` używa <xref:System.ServiceModel.Channels.MessageEncoder> do tłumaczenia <xref:System.ServiceModel.Channels.Message> do i z byte []. Ponieważ istnieje transportu, `WseTcpDuplexSessionChannel` również jest odpowiedzialna za stosowanie zdalny adres, który kanał został skonfigurowany z. `EncodeMessage` hermetyzuje logikę do konwersji.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 Raz <xref:System.ServiceModel.Channels.Message> jest zakodowany w bajtach, muszą być przekazywane w sieci. Wymaga to systemu do definiowania granice wiadomości. WSE 3.0 używa wersji [DIME](http://go.microsoft.com/fwlink/?LinkId=94999) jako protokół ramek. `WriteData` hermetyzuje logiki ramek do opakowywania byte [] w zestawie rekordów DIME.  
  
 Logika do odbierania wiadomości jest bardzo podobne. Główne złożoności obsługuje fakt, że gniazda do odczytu mogą zwracać mniej bajtów niż żądano. Aby otrzymywać wiadomość, `WseTcpDuplexSessionChannel` odczytuje bajtów poza przewodowo, dekoduje ramek DIME, a następnie używa <xref:System.ServiceModel.Channels.MessageEncoder> służący do włączania byte [] do <xref:System.ServiceModel.Channels.Message>.  
  
 Podstawowym `WseTcpDuplexSessionChannel` przyjęto założenie, że odbiera połączenia gniazda. Klasa podstawowa obsługuje zamknięcia gniazda. Istnieją trzy miejsca z zamknięcia gniazda:  
  
-   OnAbort — Zamknij gniazda ungracefully (Zamknij twarde).  
  
-   Na [Begin] Zamknij — Zamknij gniazda bezpiecznie (Zamknij nietrwałego).  
  
-   sesji. CloseOutputSession — zamknięcie strumień danych wychodzących (Zamknij połowa).  
  
## <a name="channel-factory"></a>Fabryka kanałów  
 Następnym krokiem w pisaniu transportu TCP jest utworzenie implementacja <xref:System.ServiceModel.Channels.IChannelFactory> kanałów klienta.  
  
-   `WseTcpChannelFactory` pochodną <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel >. Fabryka, która zastępuje jest `OnCreateChannel` do tworzenia kanałów klienta.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   `ClientWseTcpDuplexSessionChannel` dodaje logikę do podstawy `WseTcpDuplexSessionChannel` do nawiązania połączenia z serwerem TCP `channel.Open` czasu. Nazwa hosta jest najpierw rozpoznana jako adres IP, jak pokazano w poniższym kodzie.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   Następnie nazwa hosta jest podłączony do pierwszy dostępny adres IP w pętli, jak pokazano w poniższym kodzie.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   W ramach umowy kanału, wszelkie wyjątki specyficznego dla domeny są opakowywane, takich jak `SocketException` w <xref:System.ServiceModel.CommunicationException>.  
  
## <a name="channel-listener"></a>Odbiornik kanału  
 Następnym krokiem w pisaniu transportu TCP jest utworzenie implementacja <xref:System.ServiceModel.Channels.IChannelListener> akceptowania kanały serwera.  
  
-   `WseTcpChannelListener` pochodną <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel > i zastąpienia na otwieranie [Begin] i [Begin] Zamknij, aby kontrolować okres istnienia jego gniazdo. W zdarzenia gniazda jest tworzony do nasłuchiwania IP_ANY. Implementacje bardziej zaawansowanych można utworzyć drugi gniazda do nasłuchiwania protokołu IPv6, jak również. Umożliwiają one również adres IP, należy określić w nazwie hosta.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Po zaakceptowaniu nowe gniazdo kanału serwera jest inicjowany z tego gniazda. Wszystkie dane wejściowe i wyjściowe został już zaimplementowany w klasie podstawowej, dlatego ten kanał jest odpowiedzialny za inicjowanie gniazda.  
  
## <a name="adding-a-binding-element"></a>Dodawanie elementu powiązania  
 Teraz, kiedy są tworzone i fabryki kanałów, muszą być widoczne dla środowiska uruchomieniowego ServiceModel za pośrednictwem powiązania. Powiązanie to kolekcja elementów powiązań reprezentujący stosu komunikacji skojarzony z adresem usługi. Każdy element na stosie jest reprezentowany przez element powiązania.  
  
 W przykładzie jest element powiązania `WseTcpTransportBindingElement`, która jest pochodną <xref:System.ServiceModel.Channels.TransportBindingElement>. Obsługuje ona <xref:System.ServiceModel.Channels.IDuplexSessionChannel> i zastępuje następujące metody umożliwiające tworzenie fabryki skojarzony z powiązaniem naszych.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Zawiera także członków do klonowania `BindingElement` i zwracanie naszych schematu (wse.tcp).  
  
## <a name="the-wse-tcp-test-console"></a>Konsolę programu WSE TCP testu  
 Za pomocą tego transportu przykładowy kod testu jest dostępny w TestCode.cs. Poniższe instrukcje przedstawiają sposób konfigurowania programu WSE `TcpSyncStockService` próbki.  
  
 Kod testu tworzy niestandardowego powiązania, który używa jako kodowanie MTOM i `WseTcpTransport` jako transportu. Konfiguruje również wersja adresowania mogła być być zgodność z programu WSE 3.0, jak pokazano w poniższym kodzie.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 Składa się z dwóch testów — jeden test konfiguruje klient z typowaniem przy użyciu kodu wygenerowane z pliku programu WSE 3.0 WSDL. Drugi test używa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jako klient i serwer wysyła komunikaty bezpośrednio na kanale interfejsów API.  
  
 Podczas uruchamiania próbki, oczekiwano następujących danych wyjściowych.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Aby uruchomić ten przykład, musi mieć WSE 3.0 i WSE `TcpSyncStockService` próbki zainstalowane. Możesz pobrać [WSE 3.0 w sieci MSDN](http://go.microsoft.com/fwlink/?LinkId=95000).  
  
> [!NOTE]
>  Ponieważ WSE 3.0 nie jest obsługiwany na [!INCLUDE[lserver](../../../../includes/lserver-md.md)], nie można zainstalować ani uruchomić `TcpSyncStockService` przykładowa w tym systemie operacyjnym.  
  
1.  Po zainstalowaniu `TcpSyncStockService` przykładowe, wykonaj następujące czynności:  
  
    1.  Otwórz `TcpSyncStockService` w programie Visual Studio (należy pamiętać, że przykładowe TcpSyncStockService jest instalowany z programu WSE 3.0. Nie jest częścią ten przykład kodu).  
  
    2.  Ustaw projekt StockService jako projekt startowy.  
  
    3.  Otwórz StockService.cs w StockService projektu i komentarz dla atrybutu [zasad] `StockService` klasy. Powoduje wyłączenie zabezpieczeń z próbki. Gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] może współdziałać z programu WSE 3.0 bezpieczne punkty końcowe, zabezpieczeń jest wyłączone, aby zachować ten przykład koncentruje się na niestandardowe transportu TCP.  
  
    4.  Naciśnij klawisz F5, aby uruchomić `TcpSyncStockService`. Usługa jest uruchamiana w nowym oknie konsoli.  
  
    5.  Otwórz ten przykład transportu TCP w programie Visual Studio.  
  
    6.  Zaktualizować zmiennej "Nazwa hosta" w TestCode.cs odpowiadające działa Nazwa maszyny `TcpSyncStockService`.  
  
    7.  Naciśnij klawisz F5, aby uruchomić przykładowe transportu TCP.  
  
    8.  Klient testowy transportu TCP rozpoczyna się w nowej konsoli. Klient żąda giełdowych z usługi i następnie wyświetla wyniki w oknie swojej konsoli.  
  
## <a name="see-also"></a>Zobacz też
