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
# <a name="chunking-channel"></a>Kanał dzielący na fragmenty

Podczas wysyłania dużych wiadomości przy użyciu programu Windows Communication Foundation (WCF), często jest pożądane, aby ograniczyć ilość pamięci używanej do buforowania tych wiadomości. Jednym z możliwych rozwiązań jest przesyłanie strumieniowe treści wiadomości (przy założeniu, że większość danych znajduje się w treści). Jednak niektóre protokoły wymagają buforowania całej wiadomości. Niezawodne wiadomości i zabezpieczenia to dwa takie przykłady. Innym możliwym rozwiązaniem jest podzielenie dużych wiadomości na mniejsze wiadomości o nazwie fragmenty, wysłać te fragmenty jeden fragment na raz i odtworzyć dużą wiadomość po stronie odbierającej. Sama aplikacja może to zrobić fragmentowanie i de-chunking lub może użyć kanału niestandardowego, aby to zrobić. Przykład kanału fragmentowania pokazuje, jak niestandardowy protokół lub warstwowy kanał może służyć do tworzenia fragmentów i usuwania fragmentów dowolnie dużych wiadomości.

Fragmentowanie powinny być zawsze stosowane tylko po skonstruowaniu całej wiadomości, która ma zostać wysłana. Kanał fragmentowania powinien być zawsze warstwowy poniżej kanału zabezpieczeń i niezawodnego kanału sesji.

> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a>Fragmentowanie założeń i ograniczeń kanału

### <a name="message-structure"></a>Struktura wiadomości

Kanał fragmentowania zakłada następującą strukturę komunikatów dla wiadomości, które mają być fragmentowane:

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

Podczas korzystania z ServiceModel, operacje umowy, które mają 1 parametr wejściowy są zgodne z tym kształtem komunikatu dla ich komunikatu wejściowego. Podobnie operacje kontraktowe, które mają 1 parametr wyjściowy lub zwraca wartość są zgodne z tym kształtem komunikatu dla ich komunikatu wyjściowego. Poniżej przedstawiono przykłady takich operacji:

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

### <a name="sessions"></a>Sesje

Kanał fragmentowania wymaga wiadomości, które mają być dostarczane dokładnie raz, w zamówionej dostarczania wiadomości (fragmentów). Oznacza to, że podstawowy stos kanału musi być sessionful. Sesje mogą być dostarczane przez transport (na przykład transport TCP) lub przez kanał protokołu sesyjnego (na przykład kanał ReliableSession).

### <a name="asynchronous-send-and-receive"></a>Asynchroniczne wysyłanie i odbieranie

Metody asynchroniczne wysyłania i odbierania nie są implementowane w tej wersji przykładu kanału fragmentowania.

## <a name="chunking-protocol"></a>Protokół fragmentowania

Kanał fragmentowania definiuje protokół, który wskazuje początek i koniec serii fragmentów, a także numer sekwencyjny każdego fragmentu. Następujące trzy przykładowe komunikaty pokazują wiadomości początkowe, fragmentowe i końcowe za pomocą komentarzy opisujących kluczowe aspekty każdego z nich.

### <a name="start-message"></a>Rozpocznij wiadomość

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

### <a name="chunk-message"></a>Wiadomość fragmentu

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

### <a name="end-message"></a>Zakończ wiadomość

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

## <a name="chunking-channel-architecture"></a>Architektura kanału fragmentowania

Chunking kanał `IDuplexSessionChannel` jest, który na wysokim poziomie, następuje typowe architektury kanału. `ChunkingBindingElement` Istnieje, że można `ChunkingChannelFactory` zbudować `ChunkingChannelListener`i . Tworzy `ChunkingChannelFactory` wystąpienia, `ChunkingChannel` gdy jest proszony. Tworzy `ChunkingChannelListener` `ChunkingChannel` wystąpienia, gdy nowy kanał wewnętrzny jest akceptowany. Sam `ChunkingChannel` jest odpowiedzialny za wysyłanie i odbieranie wiadomości.

Na następnym poziomie `ChunkingChannel` w dół, opiera się na kilka składników do zaimplementowania protokołu fragmentowania. Po stronie wysyłania kanał używa <xref:System.Xml.XmlDictionaryWriter> niestandardowego wywoływanego, `ChunkingWriter` który wykonuje rzeczywiste fragmentowanie. `ChunkingWriter`używa kanału wewnętrznego bezpośrednio do wysyłania fragmentów. Korzystanie z `XmlDictionaryWriter` niestandardowego pozwala nam wysyłać fragmenty, ponieważ duża treść oryginalnej wiadomości jest zapisywana. Oznacza to, że nie buforujemy całej oryginalnej wiadomości.

![Diagram, który pokazuje architekturę wysyłania kanału fragmentowania.](./media/chunking-channel/chunking-channel-send.gif)

Po stronie odbierania `ChunkingChannel` pobiera wiadomości z kanału wewnętrznego <xref:System.Xml.XmlDictionaryReader> i `ChunkingReader`przekazuje je do niestandardowego o nazwie , który odtwarza oryginalną wiadomość z przychodzących fragmentów. `ChunkingChannel`zawija `ChunkingReader` to `Message` w `ChunkingMessage` niestandardowej implementacji o nazwie i zwraca ten komunikat do warstwy powyżej. Ta `ChunkingReader` kombinacja `ChunkingMessage` i pozwala nam odkrztuszać oryginalną treść wiadomości, ponieważ jest ona odczytywana przez warstwę powyżej, zamiast buforowania całej oryginalnej treści wiadomości. `ChunkingReader`ma kolejkę, w której buforuje przychodzące fragmenty do maksymalnej konfigurowalnej liczby buforowanych fragmentów. Po osiągnięciu tego maksymalnego limitu czytelnik czeka na wiadomości, które mają być opróżniane z kolejki przez warstwę powyżej (to znaczy, po prostu odczytu z oryginalnej treści wiadomości) lub do osiągnięcia limitu czasu maksymalnego odbioru.

![Diagram, który pokazuje architekturę odbierania fragmentów kanału.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a>Model programowania fragmentów

Deweloperzy usług można określić, które wiadomości `ChunkingBehavior` mają być fragmentowane przez zastosowanie atrybutu do operacji w ramach umowy. Atrybut udostępnia `AppliesTo` właściwość, która umożliwia deweloperowi określić, czy fragmentowanie ma zastosowanie do komunikatu wejściowego, komunikat wyjściowy lub obu. W poniższym przykładzie `ChunkingBehavior` pokazano użycie atrybutu:

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

Z tego modelu `ChunkingBindingElement` programowania kompiluje listę identyfikatorów URI akcji, które identyfikują komunikaty, które mają być fragmentaryzowane. Akcja każdej wiadomości wychodzącej jest porównywana z tą listą, aby ustalić, czy wiadomość powinna być fragmentowana lub wysłana bezpośrednio.

## <a name="implementing-the-send-operation"></a>Implementowanie operacji wysyłania

Na wysokim poziomie Wyślij operacji najpierw sprawdza, czy wychodzące wiadomości muszą być fragmentowane, a jeśli nie, wysyła wiadomość bezpośrednio przy użyciu kanału wewnętrznego.

Jeśli wiadomość musi być fragmentowany, `ChunkingWriter` Wyślij `WriteBodyContents` tworzy nowy i wywołuje `ChunkingWriter`wiadomość wychodzącą przekazując go w ten sposób . Następnie `ChunkingWriter` nie fragmentowanie wiadomości (w tym kopiowanie nagłówków oryginalnej wiadomości do początkowej wiadomości fragmentu) i wysyła fragmenty przy użyciu kanału wewnętrznego.

Kilka szczegółów warto zauważyć:

- Wyślij pierwsze `ThrowIfDisposedOrNotOpened` połączenia, `CommunicationState` aby upewnić się, że jest otwarty.

- Wysyłanie jest synchronizowane, dzięki czemu dla każdej sesji można wysłać tylko jedną wiadomość. Istnieje `ManualResetEvent` nazwa, `sendingDone` która jest resetowana, gdy wysyłana jest wiadomość fragmentowana. Po wysłaniu komunikatu o fragmencie końcowym to zdarzenie jest ustawione. Send Metoda czeka na to zdarzenie, które ma zostać ustawione, zanim spróbuje wysłać wiadomość wychodzącą.

- Wyślij blokuje, `CommunicationObject.ThisLock` aby zapobiec zsynchronizowanym zmianom stanu podczas wysyłania. Zobacz <xref:System.ServiceModel.Channels.CommunicationObject> dokumentację, aby <xref:System.ServiceModel.Channels.CommunicationObject> uzyskać więcej informacji na temat stanów i komputera stanu.

- Limit czasu przekazany do wysyłania jest używany jako limit czasu dla całej operacji wysyłania, która obejmuje wysyłanie wszystkich fragmentów.

- Niestandardowy <xref:System.Xml.XmlDictionaryWriter> projekt został wybrany, aby uniknąć buforowania całego oryginalnego obiektu wiadomości. Gdybyśmy mieli dostać <xref:System.Xml.XmlDictionaryReader> na ciele `message.GetReaderAtBodyContents` za pomocą całego ciała byłoby buforowane. Zamiast tego mamy zwyczaj, <xref:System.Xml.XmlDictionaryWriter> który `message.WriteBodyContents`jest przekazywany do . Jak komunikat wywołuje WriteBase64 na modułu zapisującego, moduł zapisujący pakiety do fragmentów do wiadomości i wysyła je przy użyciu kanału wewnętrznego. WriteBase64 blokuje, dopóki fragment nie zostanie wysłany.

## <a name="implementing-the-receive-operation"></a>Wdrażanie operacji odbierania

Na wysokim poziomie Receive operacji najpierw sprawdza, czy `null` wiadomość przychodząca `ChunkingAction`nie jest i że jego działanie jest . Jeśli nie spełnia obu kryteriów, wiadomość jest zwracana bez zmian z Receive. W przeciwnym razie `ChunkingReader` Receive tworzy `ChunkingMessage` nowy i nowy `GetNewChunkingMessage`owinięty wokół niego (przez wywołanie ). Przed zwróceniem `ChunkingMessage`tego nowego , Receive używa `ReceiveChunkLoop`wątku `innerChannel.Receive` wątku do wykonania , który `ChunkingReader` wywołuje w pętli i przekazuje fragmenty do momentu odebrania komunikatu fragmentu końcowego lub zostanie trafiony limit czasu odbioru.

Kilka szczegółów warto zauważyć:

- Podobnie jak Wyślij, `ThrowIfDisposedOrNotOepned` odbierz pierwsze połączenia, aby upewnić się, `CommunicationState` że jest otwarty.

- Receive jest również synchronizowany, dzięki czemu można odbierać tylko jedną wiadomość naraz z sesji. Jest to szczególnie ważne, ponieważ po odebraniu komunikatu fragmentu początkowego wszystkie kolejne odebrane wiadomości powinny być fragmentami w tej nowej sekwencji fragmentów, dopóki nie zostanie odebrana komunikat o fragmencie końcowym. Receive nie może pobierać wiadomości z kanału wewnętrznego, dopóki nie zostaną odebrane wszystkie fragmenty, które należą do wiadomości, która jest obecnie usuwana z fragmentami. Aby to osiągnąć, Receive `ManualResetEvent` `currentMessageCompleted`używa nazwanego , który jest ustawiany po odebraniu komunikatu o fragmencie końcowym i zresetowaniu po odebraniu nowej wiadomości fragmentu początkowego.

- W przeciwieństwie do Wysyłania, Odbierania nie zapobiega zsynchronizowanych przejściach stanu podczas odbierania. Na przykład Close można wywołać podczas odbierania i czeka, aż oczekujące odbieranie oryginalnej wiadomości zostanie zakończona lub zostanie osiągnięta określona wartość limitu czasu.

- Limit czasu przekazany do receive jest używany jako limit czasu dla całej operacji odbierania, która obejmuje odbieranie wszystkich fragmentów.

- Jeśli warstwa, która zużywa wiadomość zużywa treść wiadomości z szybkością niższą niż `ChunkingReader` szybkość przychodzących wiadomości fragmentów, `ChunkingBindingElement.MaxBufferedChunks`buforuje te przychodzące fragmenty do limitu określonego przez program . Po osiągnięciu tego limitu nie więcej fragmentów są pobierane z dolnej warstwy, dopóki nie zostanie wykorzystany buforowany fragment lub limit czasu odbioru zostanie osiągnięty.

## <a name="communicationobject-overrides"></a>Przesłonięcia znacznicy komunikacyjnej

### <a name="onopen"></a>Onopen

`OnOpen`wezwań `innerChannel.Open` do otwarcia kanału wewnętrznego.

### <a name="onclose"></a>Onclose

`OnClose`pierwsze `stopReceive` zestawy, aby `true` `ReceiveChunkLoop` zasygnalizować oczekujące zatrzymanie. Następnie czeka na `receiveStopped` <xref:System.Threading.ManualResetEvent>, który jest `ReceiveChunkLoop` ustawiany po zatrzymaniu. Przy `ReceiveChunkLoop` założeniu, że zatrzymuje `OnClose` `innerChannel.Close` się w określonym limit czasu, wywołuje z pozostałym limit czasu.

### <a name="onabort"></a>Onabort

`OnAbort`wzywa `innerChannel.Abort` do przerwania kanału wewnętrznego. Jeśli istnieje oczekujące `ReceiveChunkLoop` pobiera wyjątek `innerChannel.Receive` od oczekującego wywołania.

### <a name="onfaulted"></a>OnFaulted ( OnFaulted )

Nie `ChunkingChannel` wymaga specjalnego zachowania, gdy kanał `OnFaulted` jest uszkodzony, więc nie jest zastępowany.

## <a name="implementing-channel-factory"></a>Wdrożenie fabryki kanałów

Jest `ChunkingChannelFactory` odpowiedzialny za tworzenie wystąpień `ChunkingDuplexSessionChannel` i dla kaskadowych przejść stanu do fabryki kanałów wewnętrznych.

`OnCreateChannel`wykorzystuje fabrykę kanałów wewnętrznych `IDuplexSessionChannel` do utworzenia kanału wewnętrznego. Następnie tworzy nowy `ChunkingDuplexSessionChannel` przekazując go tego kanału wewnętrznego wraz z listą akcji wiadomości, które mają być fragmentowane i maksymalną liczbę fragmentów do buforowania po otrzymaniu. Lista akcji wiadomości, które mają być fragmentowane i maksymalna liczba `ChunkingChannelFactory` fragmentów do buforu są dwa parametry przekazywane do jego konstruktora. W sekcji `ChunkingBindingElement` opisano, skąd pochodzą te wartości.

The `OnOpen` `OnClose`, `OnAbort` i ich odpowiedniki asynchroniczne wywołać odpowiednią metodę przejścia stanu w fabryce kanału wewnętrznego.

## <a name="implementing-channel-listener"></a>Implementowanie odbiornika kanałów

Jest `ChunkingChannelListener` otoka wokół odbiornika kanału wewnętrznego. Jego główną funkcją, oprócz delegowania wywołań do `ChunkingDuplexSessionChannels` tego odbiornika kanału wewnętrznego, jest zawijanie nowych wokół kanałów akceptowanych z odbiornika kanału wewnętrznego. Odbywa się `OnAcceptChannel` to `OnEndAcceptChannel`w i . Nowo utworzony `ChunkingDuplexSessionChannel` jest przekazywany kanał wewnętrzny wraz z innymi parametrami wcześniej opisane.

## <a name="implementing-binding-element-and-binding"></a>Implementowanie elementu wiążącego i powiązania

`ChunkingBindingElement`jest odpowiedzialny za `ChunkingChannelFactory` tworzenie `ChunkingChannelListener`i . Sprawdza, `ChunkingBindingElement` czy `CanBuildChannelFactory` \<T w T `CanBuildChannelListener` \<> i T> `IDuplexSessionChannel` jest typu (tylko kanał obsługiwany przez kanał fragmentowania) i czy inne elementy powiązania w powiązaniu obsługuje ten typ kanału.

`BuildChannelFactory`\<T> najpierw sprawdza, czy żądany typ kanału może być zbudowany, a następnie pobiera listę akcji wiadomości, które mają być fragmentowane. Aby uzyskać więcej informacji, zobacz następującą sekcję. Następnie tworzy nowy `ChunkingChannelFactory` przekazując go wewnętrznej fabryki `context.BuildInnerChannelFactory<IDuplexSessionChannel>`kanału (jako zwrócone z ), lista akcji wiadomości i maksymalna liczba fragmentów do bufora. Maksymalna liczba fragmentów pochodzi z `MaxBufferedChunks` właściwości `ChunkingBindingElement`o nazwie exposed przez .

`BuildChannelListener<T>`ma podobną implementację `ChunkingChannelListener` do tworzenia i przekazywania go odbiornika kanału wewnętrznego.

Istnieje przykład powiązania zawarte w tym `TcpChunkingBinding`przykładzie o nazwie . To powiązanie składa się `TcpTransportBindingElement` `ChunkingBindingElement`z dwóch elementów wiążących: i . Oprócz uwidaczniania `MaxBufferedChunks` właściwości powiązanie ustawia również `TcpTransportBindingElement` niektóre właściwości, `MaxReceivedMessageSize` takie jak `ChunkingUtils.ChunkSize` (ustawia go na + 100 KB bajtów dla nagłówków).

`TcpChunkingBinding`implementuje `IBindingRuntimePreferences` i zwraca true `ReceiveSynchronously` z metody wskazującej, że implementowane są tylko wywołania synchroniczne odbieranie.

### <a name="determining-which-messages-to-chunk"></a>Określanie, które wiadomości mają być fragmentowe

Fragmenty kanału fragmenty tylko wiadomości zidentyfikowane `ChunkingBehavior` za pośrednictwem atrybutu. Klasa `ChunkingBehavior` implementuje `IOperationBehavior` i jest implementowana `AddBindingParameter` przez wywołanie metody. W tej `ChunkingBehavior` metodzie sprawdza wartość `AppliesTo` jego`InMessage`właściwości `OutMessage` ( lub obu), aby określić, które komunikaty powinny być fragmentowane. Następnie pobiera akcję każdej z tych wiadomości (z `OperationDescription`messages collection on ) i dodaje go `ChunkingBindingParameter`do kolekcji ciągów zawartych w wystąpieniu . Następnie dodaje `ChunkingBindingParameter` to do `BindingParameterCollection`dostarczonego .

To `BindingParameterCollection` jest przekazywane `BindingContext` wewnątrz do każdego elementu wiązania w powiązanie, gdy ten element wiązania tworzy fabryki kanału lub odbiornika kanału. Realizacji `ChunkingBindingElement` `BuildChannelFactory<T>` `BuildChannelListener<T>` i wyciągnąć `ChunkingBindingParameter` to z `BindingContext’`s `BindingParameterCollection`. Zbiór działań zawartych `ChunkingBindingParameter` w a następnie `ChunkingChannelFactory` `ChunkingChannelListener`jest przekazywana do `ChunkingDuplexSessionChannel`lub , który z kolei przekazuje go do .

## <a name="running-the-sample"></a>Uruchamianie próbki

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę

1. Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

3. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).

5. Najpierw uruchom program Service.exe, a następnie uruchom program Client.exe i obserwuj oba okna konsoli w celu uzyskania danych wyjściowych.

Podczas uruchamiania próbki oczekuje się następującego wyjścia.

Klient:

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

Serwer:

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
