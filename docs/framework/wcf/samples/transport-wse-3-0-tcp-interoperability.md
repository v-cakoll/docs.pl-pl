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
# <a name="transport-wse-30-tcp-interoperability"></a>Transport: Współdziałanie protokołu TCP z usługami WSE 3.0
Przykład transportu interoperacyjności protokołu WSE 3.0 TCP pokazuje, jak zaimplementować sesję dupleksu TCP jako niestandardowy transport programu Windows Communication Foundation (WCF). Pokazano również, jak można użyć rozszerzalności warstwy kanału do interfejsu przez przewod z istniejącymi wdrożonymi systemami. Poniższe kroki pokazują, jak utworzyć ten niestandardowy transport WCF:  
  
1. Począwszy od gniazda TCP, należy utworzyć <xref:System.ServiceModel.Channels.IDuplexSessionChannel> implementacje klienta i serwera, których użycie służy do wytyczania granic wiadomości przez moduł DIME Framing.  
  
2. Utwórz fabrykę kanałów, która łączy się z usługą GPW <xref:System.ServiceModel.Channels.IDuplexSessionChannel>TCP i wysyła wiadomości w ramkach za pomocą klienta s.  
  
3. Utwórz odbiornik kanałów, aby akceptować przychodzące połączenia TCP i tworzyć odpowiednie kanały.  
  
4. Upewnij się, że wszelkie wyjątki specyficzne dla sieci <xref:System.ServiceModel.CommunicationException>są znormalizowane do odpowiedniej klasy pochodnej .  
  
5. Dodaj element wiązania, który dodaje niestandardowy transport do stosu kanału. Aby uzyskać więcej informacji, zobacz [Dodawanie elementu wiązania].  
  
## <a name="creating-iduplexsessionchannel"></a>Tworzenie iduplexSessionChannel  
 Pierwszym krokiem w pisaniu GPW 3.0 TCP Interoperability <xref:System.ServiceModel.Channels.IDuplexSessionChannel> Transport jest <xref:System.Net.Sockets.Socket>stworzenie implementacji na szczycie . `WseTcpDuplexSessionChannel`pochodzi od <xref:System.ServiceModel.Channels.ChannelBase>. Logika wysyłania wiadomości składa się z dwóch głównych elementów: (1) kodowania wiadomości w bajty i (2) kadrowania tych bajtów i wysyłania ich na sieć.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Ponadto blokada jest pobierana tak, że Send() wywołania zachować IDuplexSessionChannel gwarancji w kolejności i tak, że wywołania do gniazda źródłowego są poprawnie zsynchronizowane.  
  
 `WseTcpDuplexSessionChannel`używa a <xref:System.ServiceModel.Channels.MessageEncoder> do tłumaczenia na bajt <xref:System.ServiceModel.Channels.Message> i z bajtu[]. Ponieważ jest to `WseTcpDuplexSessionChannel` transport, jest również odpowiedzialny za zastosowanie adresu zdalnego, który został skonfigurowany z kanałem. `EncodeMessage`hermetyzuje logikę tej konwersji.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 Gdy <xref:System.ServiceModel.Channels.Message> jest zakodowany w bajtach, musi być przesyłany na przewodach. Wymaga to systemu do definiowania granic wiadomości. WSE 3.0 używa wersji [DIME](https://docs.microsoft.com/archive/msdn-magazine/2002/december/sending-files-attachments-and-soap-messages-via-dime) jako protokołu kadrowania. `WriteData`hermetyzuje logikę kadrowania, aby zawinąć bajt[] w zestaw rekordów DIME.  
  
 Logika odbierania wiadomości jest podobna. Główną złożonością jest obsługa faktu, że odczyt gniazda może zwrócić mniej bajtów niż zostały wymagane. Aby otrzymać wiadomość, `WseTcpDuplexSessionChannel` odczytuje bajty z przewodu, dekoduje kadrowanie DIME, a następnie używa <xref:System.ServiceModel.Channels.Message> <xref:System.ServiceModel.Channels.MessageEncoder> do przekształcania bajtu[] w plik .  
  
 Podstawa `WseTcpDuplexSessionChannel` zakłada, że odbiera podłączone gniazdo. Klasa podstawowa obsługuje zamknięcie gniazda. Istnieją trzy miejsca, które interfejs z zamknięciem gniazda:  
  
- OnAbort -- zamknij gniazdo bezgranicznie (twarde zamknięcie).  
  
- On[Begin]Close -- zamknij gniazdo bezpiecznie (miękkie zamknięcie).  
  
- Sesji. CloseOutputSession - zamknij strumień danych wychodzących (połowa zamknięcia).  
  
## <a name="channel-factory"></a>Fabryka kanałów  
 Następnym krokiem w pisaniu transportu TCP <xref:System.ServiceModel.Channels.IChannelFactory> jest utworzenie implementacji dla kanałów klienta.  
  
- `WseTcpChannelFactory`pochodzi z <xref:System.ServiceModel.Channels.ChannelFactoryBase> \<IDuplexSessionChannel>. Jest to fabryka, `OnCreateChannel` która zastępuje do produkcji kanałów klienta.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
- `ClientWseTcpDuplexSessionChannel`dodaje logikę `WseTcpDuplexSessionChannel` do bazy, aby połączyć się z serwerem TCP w `channel.Open` czasie. Najpierw nazwa hosta jest rozpoznawana na adres IP, jak pokazano w poniższym kodzie.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
- Następnie nazwa hosta jest podłączona do pierwszego dostępnego adresu IP w pętli, jak pokazano w poniższym kodzie.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
- W ramach umowy kanału wszelkie wyjątki specyficzne dla `SocketException` domeny <xref:System.ServiceModel.CommunicationException>są zawijane, na przykład w .  
  
## <a name="channel-listener"></a>Odbiornik kanałów  
 Następnym krokiem w pisaniu transportu TCP <xref:System.ServiceModel.Channels.IChannelListener> jest utworzenie implementacji do akceptowania kanałów serwera.  
  
- `WseTcpChannelListener`pochodzi z <xref:System.ServiceModel.Channels.ChannelListenerBase> \<IDuplexSessionChannel> i zastępuje On[Begin]Open i On[Begin]Close, aby kontrolować okres istnienia gniazda nasłuchicia. W OnOpen, gniazdo jest tworzony do nasłuchiwać na IP_ANY. Bardziej zaawansowane implementacje można utworzyć drugie gniazdo do nasłuchiwać na IPv6, jak również. Mogą również zezwolić na adres IP, który ma być określony w nazwach hosta.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Po zaakceptowaniu nowego gniazda kanał serwera jest inicjowany za pomocą tego gniazda. Wszystkie dane wejściowe i wyjściowe są już zaimplementowane w klasie podstawowej, więc ten kanał jest odpowiedzialny za inicjowanie gniazda.  
  
## <a name="adding-a-binding-element"></a>Dodawanie elementu wiązania  
 Teraz, gdy fabryki i kanały są budowane, muszą być widoczne na servicemodel środowiska uruchomieniowego za pośrednictwem powiązania. Powiązanie jest kolekcją elementów wiązania, który reprezentuje stos komunikacji skojarzony z adresem usługi. Każdy element w stosie jest reprezentowany przez element wiązania.  
  
 W próbce element wiązania `WseTcpTransportBindingElement`jest , <xref:System.ServiceModel.Channels.TransportBindingElement>który pochodzi z . Obsługuje <xref:System.ServiceModel.Channels.IDuplexSessionChannel> i zastępuje następujące metody tworzenia fabryk skojarzonych z naszym powiązaniem.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Zawiera również członków do `BindingElement` klonowania i zwracania naszego programu (wse.tcp).  
  
## <a name="the-wse-tcp-test-console"></a>Konsola testna GPW TCP  
 Kod testowy do korzystania z tego przykładowego transportu jest dostępny w TestCode.cs. Poniższe instrukcje pokazują, jak skonfigurować `TcpSyncStockService` przykład GPW.  
  
 Kod testowy tworzy niestandardowe powiązanie, które używa `WseTcpTransport` MTOM jako kodowania i jako transportu. Konfiguruje również AddressingVersion być zgodne z GPW 3.0, jak pokazano w poniższym kodzie.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 Składa się z dwóch testów — jeden test konfiguruje wpisanego klienta przy użyciu kodu wygenerowanego z WSDL WSE 3.0. Drugi test używa WCF jako klienta i serwera, wysyłając wiadomości bezpośrednio na górze interfejsów API kanału.  
  
 Podczas uruchamiania próbki oczekuje się następującego wyjścia.  
  
 Klient:  
  
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
  
 Serwer:  
  
```console  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
## <a name="set-up-build-and-run-the-sample"></a>Konfigurowanie, tworzenie i uruchamianie próbki  
  
1. Aby uruchomić ten przykład, musisz mieć [ulepszenia usług sieci Web (GPSE) 3.0 dla firmy Microsoft .NET](https://www.microsoft.com/download/details.aspx?id=14089) i `TcpSyncStockService` zainstalowano przykład gpw.
  
> [!NOTE]
> Ponieważ usługa WSE 3.0 nie jest obsługiwana w systemie Windows Server `TcpSyncStockService` 2008, nie można zainstalować ani uruchomić próbki w tym systemie operacyjnym.  
  
1. Po zainstalowaniu `TcpSyncStockService` próbki wykonaj następujące czynności:  
  
    1. Otwórz `TcpSyncStockService` program Visual Studio. (Próbka TcpSyncStockService jest zainstalowana z gpw 3.0. Nie jest częścią kodu tego przykładu.)  
  
    2. Ustaw projekt StockService jako projekt startowy.  
  
    3. Otwórz StockService.cs w projekcie StockService i skomentuj atrybut `StockService` [Zasady] w klasie. Spowoduje to wyłączenie zabezpieczeń z przykładu. Podczas WCF można współpracować z gpw 3.0 bezpiecznych punktów końcowych, zabezpieczenia jest wyłączona, aby utrzymać ten przykład koncentruje się na niestandardowy transport TCP.  
  
    4. Naciśnij klawisz F5, aby uruchomić przycisk `TcpSyncStockService`. Usługa zostanie uruchomiony w nowym oknie konsoli.  
  
    5. Otwórz ten przykład transportu TCP w programie Visual Studio.  
  
    6. Zaktualizuj zmienną "nazwa hosta" w TestCode.cs, aby dopasować nazwę komputera z uruchomionym programem `TcpSyncStockService`.  
  
    7. Naciśnij klawisz F5, aby uruchomić próbkę transportu TCP.  
  
    8. Klient testu transportu TCP uruchamia się w nowej konsoli. Klient żąda notowań akcji z usługi, a następnie wyświetla wyniki w oknie konsoli.  
