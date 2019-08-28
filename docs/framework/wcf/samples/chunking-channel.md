---
title: Kanał dzielący na fragmenty
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: b59f5c42f5a0f81f666bc5d22924f14c678a60e1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045699"
---
# <a name="chunking-channel"></a>Kanał dzielący na fragmenty

Podczas wysyłania dużych komunikatów przy użyciu Windows Communication Foundation (WCF) często pożądane jest ograniczenie ilości pamięci używanej do buforowania tych komunikatów. Jednym z możliwych rozwiązań jest przesyłanie strumieniowe treści wiadomości (przy założeniu, że dane są zawarte w treści). Jednak niektóre protokoły wymagają buforowania całej wiadomości. Niezawodna obsługa komunikatów i zabezpieczeń to dwa przykłady. Innym możliwym rozwiązaniem jest dzielenie dużej liczby wiadomości na mniejsze wiadomości o nazwie fragmenty, wysłanie tych fragmentów z jednego fragmentu jednocześnie i odbudowanie dużej wiadomości po stronie odbiorczej. Sama aplikacja może wykonać to dzielenie i cofanie fragmentów. w tym celu można użyć niestandardowego kanału. Przykład kanału fragmentowania pokazuje, w jaki sposób niestandardowy protokół lub kanał warstwowy może służyć do rozdzielania i defragmentowania bardzo dużych komunikatów.

Dzielenie powinno być zawsze stosowane tylko po skonstruowaniu całej wysyłanej wiadomości. Kanał fragmentowania powinien być zawsze warstwowy poniżej kanału zabezpieczeń i niezawodnego kanału sesji.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a>Założenia i ograniczenia kanału podziału

### <a name="message-structure"></a>Struktura wiadomości

Kanał fragmentacji przyjmuje następującą strukturę komunikatów, aby można było uzyskać fragmenty komunikatów:

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

W przypadku używania elementu ServiceModel operacje kontraktu z 1 parametrem wejściowym są zgodne z tym kształtem komunikatu dla wiadomości wejściowej. Podobnie operacje kontraktu z 1 parametrem wyjściowym lub wartością zwracaną są zgodne z tym kształtem komunikatu dla wiadomości wyjściowej. Poniżej przedstawiono przykłady takich operacji:

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

### <a name="sessions"></a>Kategoria Sessions

Kanał fragmentowania wymaga, aby komunikaty były dostarczane dokładnie raz, w zamówionej dostawie komunikatów (fragmentów). Oznacza to, że bazowy stos kanałów musi być sesją. Sesje mogą być dostarczane przez transporty (na przykład transport TCP) lub kanał protokołu sesji (na przykład kanał ReliableSession).

### <a name="asynchronous-send-and-receive"></a>Wysyłanie i odbieranie asynchroniczne

Asynchroniczne metody wysyłania i odbierania nie są zaimplementowane w tej wersji przykładowego kanału fragmentu.

## <a name="chunking-protocol"></a>Protokół fragmentaryczny

Kanał fragmentowania definiuje protokół, który wskazuje początek i koniec serii fragmentów, jak również numer sekwencyjny każdego fragmentu. Poniższe trzy przykładowe komunikaty pokazują, jak rozpocząć, fragmenty i końcowe wiadomości z komentarzami opisującymi kluczowe aspekty każdego z nich.

### <a name="start-message"></a>Rozpocznij komunikat

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

### <a name="chunk-message"></a>Komunikat fragmentu

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

### <a name="end-message"></a>Zakończ komunikat

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

## <a name="chunking-channel-architecture"></a>Architektura kanału podziału

Kanał fragmentowania to `IDuplexSessionChannel` na wysokim poziomie, zgodnie z typową architekturą kanału. `ChunkingBindingElement` Istnieje możliwość`ChunkingChannelFactory` utworzenia i `ChunkingChannelListener`. `ChunkingChannelFactory` Tworzy`ChunkingChannel` wystąpienia, gdy zostanie wyświetlony monit. `ChunkingChannelListener` Tworzy`ChunkingChannel` wystąpienia po zaakceptowaniu nowego kanału wewnętrznego. `ChunkingChannel` Sam jest odpowiedzialny za wysyłanie i otrzymywanie komunikatów.

Na następnym poziomie w dół `ChunkingChannel` polega na kilku składnikach w celu zaimplementowania protokołu dzielącego. Na stronie wysyłanie kanał używa niestandardowego <xref:System.Xml.XmlDictionaryWriter> wywołana `ChunkingWriter` , który wykonuje rzeczywiste fragmenty. `ChunkingWriter`używa wewnętrznego kanału bezpośrednio do wysyłania fragmentów. Użycie niestandardowych `XmlDictionaryWriter` pozwala nam wysyłać fragmenty w miarę pisania dużej treści oryginalnej wiadomości. Oznacza to, że nie buforuje całej oryginalnej wiadomości.

![Diagram przedstawiający architekturę wysyłania kanału.](./media/chunking-channel/chunking-channel-send.gif)

Po stronie `ChunkingChannel` odbierającej odbierane są komunikaty z kanału wewnętrznego i są one dołączane do <xref:System.Xml.XmlDictionaryReader> niestandardowego `ChunkingReader`wywołania, które polega na tym, że oryginalny komunikat zostanie utworzony z przychodzących fragmentów. `ChunkingChannel`Zawija ten `ChunkingReader` element w niestandardowej `Message` implementacji o nazwie `ChunkingMessage` i zwraca ten komunikat do warstwy powyżej. Ta kombinacja `ChunkingReader` i `ChunkingMessage` pozwala nam oddzielać pierwotną treść wiadomości w miarę ich odczytywania przez warstwę powyżej zamiast konieczności buforowania całej oryginalnej treści wiadomości. `ChunkingReader`ma kolejkę, w której buforuje przychodzące fragmenty do maksymalnej konfigurowalnej liczby buforowanych fragmentów. Po osiągnięciu tego maksymalnego limitu czytnik czeka na opróżnianie komunikatów z kolejki przez warstwę powyżej (czyli przez właśnie odczytywanie z oryginalnej treści wiadomości) lub do czasu osiągnięcia maksymalnego limitu czasu odbierania.

![Diagram przedstawiający architekturę odbierania w kanale.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a>Model programowania fragmentarycznego

Deweloperzy usług mogą określić, które wiadomości mają być dzielone przez zastosowanie `ChunkingBehavior` atrybutu do operacji w ramach kontraktu. Ten atrybut uwidacznia `AppliesTo` właściwość, która umożliwia deweloperowi określenie, czy fragmentacja dotyczy wiadomości wejściowej, wiadomości wyjściowej czy obu. W poniższym przykładzie pokazano użycie `ChunkingBehavior` atrybutu:

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

Z tego modelu `ChunkingBindingElement` programowania kompiluje listę identyfikatorów URI akcji, które identyfikują komunikaty do rozdzielenia. Akcja każdej wiadomości wychodzącej jest porównywana z tą listą, aby określić, czy komunikat powinien zostać podzielony lub wysłany bezpośrednio.

## <a name="implementing-the-send-operation"></a>Implementowanie operacji wysyłania

Na wysokim poziomie operacja wysyłania najpierw sprawdza, czy komunikat wychodzący musi zostać podzielony i, jeśli nie, wysyła komunikat bezpośrednio przy użyciu wewnętrznego kanału.

Jeśli komunikat musi zostać podzielony na fragmenty, polecenie Wyślij powoduje utworzenie `ChunkingWriter` nowego i `WriteBodyContents` wywołania komunikatu `ChunkingWriter`wychodzącego. `ChunkingWriter` Następnie wykonuje fragmenty komunikatów (łącznie z kopiowaniem oryginalnych nagłówków wiadomości do startowego komunikatu fragmentu) i wysyła fragmenty przy użyciu wewnętrznego kanału.

Oto kilka szczegółów:

- Wysyłaj pierwsze `ThrowIfDisposedOrNotOpened` wywołania, aby `CommunicationState` upewnić się, że jest otwarty.

- Wysyłanie jest synchronizowane, aby w danym momencie można było wysyłać tylko jeden komunikat dla każdej sesji. `ManualResetEvent` Istnieje nazwa `sendingDone` , która jest resetowana podczas wysyłania komunikatu z fragmentem. Po wysłaniu komunikatu o końcowym fragmencie to zdarzenie jest ustawiane. Metoda Send czeka na ustawienie tego zdarzenia przed podjęciem próby wysłania wiadomości wychodzącej.

- Send blokuje, `CommunicationObject.ThisLock` aby zapobiec zmianom stanu zsynchronizowanych podczas wysyłania. Zapoznaj <xref:System.ServiceModel.Channels.CommunicationObject> się z dokumentacją, aby <xref:System.ServiceModel.Channels.CommunicationObject> uzyskać więcej informacji na temat stanów i automatu Stanów.

- Przekroczenie limitu czasu, który został przesłany do wysłania, jest używany jako limit czasu dla całej operacji wysyłania, który obejmuje wysłanie wszystkich fragmentów.

- Projekt niestandardowy <xref:System.Xml.XmlDictionaryWriter> został wybrany tak, aby uniknąć buforowania całej oryginalnej treści wiadomości. Jeśli firma Microsoft musiała uzyskać <xref:System.Xml.XmlDictionaryReader> zawartość w treści przy `message.GetReaderAtBodyContents` użyciu całej treści, będzie buforowana. Zamiast tego mamy niestandardowy <xref:System.Xml.XmlDictionaryWriter> , który jest przesyłany do. `message.WriteBodyContents` Ponieważ komunikat wywołuje WriteBase64 na składniku zapisywania, pakiet składnika zapisywania umieszcza fragmenty w wiadomości i wysyła je przy użyciu wewnętrznego kanału. WriteBase64 bloki do momentu wysłania fragmentu.

## <a name="implementing-the-receive-operation"></a>Implementowanie operacji odbierania

Na wysokim poziomie operacja odbierania najpierw sprawdza, czy komunikat przychodzący nie `null` jest i czy jego Akcja `ChunkingAction`jest. Jeśli nie spełnia obydwu kryteriów, komunikat jest zwracany niezmieniony z odbierania. W przeciwnym razie polecenie Receive tworzy `ChunkingReader` nową i nową `ChunkingMessage` opakowaną w ten sposób ( `GetNewChunkingMessage`poprzez wywoływanie). Przed zwróceniem nowego `ChunkingMessage`elementu, funkcja Receive używa wątku puli wątków `ReceiveChunkLoop`do wykonania, `innerChannel.Receive` który wywołuje `ChunkingReader` pętlę i rozrywane fragmenty do momentu otrzymania komunikatu końca fragmentu lub gdy zostanie osiągnięty limit czasu odbierania.

Oto kilka szczegółów:

- Jak wysyłać, odbieraj pierwsze `ThrowIfDisposedOrNotOepned` wywołania, aby `CommunicationState` upewnić się, że jest otwarty.

- Odbieranie jest również synchronizowane, dzięki czemu w danej chwili można odbierać tylko jeden komunikat z sesji. Jest to szczególnie ważne, ponieważ po odebraniu komunikatu o początkowym fragmencie wszystkie kolejne odebrane komunikaty powinny być fragmentami w tej nowej sekwencji fragmentów do momentu odebrania komunikatu końcowego fragmentu. Wartość Receive nie może ściągać komunikatów z kanału wewnętrznego, dopóki nie zostaną odebrane wszystkie fragmenty należące do komunikatu, który jest obecnie usuwany. Aby to osiągnąć, funkcja Receive używa `ManualResetEvent` nazwy `currentMessageCompleted`, która jest ustawiana, gdy końcowy komunikat fragmentu zostanie odebrany i zresetowany po odebraniu nowego komunikatu o początkowym fragmencie.

- W przeciwieństwie do wysyłania, odbieranie nie zapobiega przeniesieniu zsynchronizowanych zmian stanu podczas odbierania. Na przykład Zamknij można wywołać podczas odbierania i czeka na zakończenie oczekiwania na odebranie oryginalnego komunikatu lub osiągnięcie określonej wartości limitu czasu.

- Limit czasu przekazywania jest używany jako limit czasu dla całej operacji odbierania, który obejmuje odbieranie wszystkich fragmentów.

- Jeśli warstwa korzystająca z komunikatów zużywa komunikat z szybkością niższą niż szybkość przychodzących komunikatów fragmentów, `ChunkingReader` bufory te przychodzące te fragmenty do limitu określonego przez. `ChunkingBindingElement.MaxBufferedChunks` Po osiągnięciu tego limitu żadne fragmenty nie są ściągane z warstwy niższej do momentu użycia zbuforowanego fragmentu lub przekroczenia limitu czasu odbierania.

## <a name="communicationobject-overrides"></a>Przesłonięcia komunikacjiobject

### <a name="onopen"></a>OnOpen

`OnOpen`wywołuje `innerChannel.Open` , aby otworzyć wewnętrzny kanał.

### <a name="onclose"></a>OnClose —

`OnClose`najpierw ustawia `stopReceive` `true` , aby sygnalizować oczekiwanie `ReceiveChunkLoop` na zatrzymanie. Następnie czeka na `receiveStopped` <xref:System.Threading.ManualResetEvent>, który jest ustawiony po `ReceiveChunkLoop` zatrzymaniu. Przy założeniu, że `OnClose` `innerChannel.Close` zatrzymasięwokreślonymlimicieczasu,wywołujezpozostałym`ReceiveChunkLoop` limitem czasu.

### <a name="onabort"></a>OnAbort

`OnAbort`wywołuje `innerChannel.Abort` przerwanie wewnętrznego kanału. Jeśli istnieje oczekujące `ReceiveChunkLoop` , pobiera wyjątek z oczekującego `innerChannel.Receive` wywołania.

### <a name="onfaulted"></a>Onfaultd

W `ChunkingChannel` przypadku awarii kanału nie jest wymagane specjalne zachowanie, które `OnFaulted` nie jest zastępowane.

## <a name="implementing-channel-factory"></a>Implementowanie fabryki kanałów

Jest odpowiedzialny za tworzenie `ChunkingDuplexSessionChannel` wystąpień i dla przejścia stanu kaskadowego do fabryki kanałów wewnętrznych. `ChunkingChannelFactory`

`OnCreateChannel`używa wewnętrznej fabryki kanałów do tworzenia `IDuplexSessionChannel` wewnętrznego kanału. Następnie tworzy nowe `ChunkingDuplexSessionChannel` przekazanie go do tego kanału wewnętrznego wraz z listą akcji komunikatów, które mają być rozłożone, oraz maksymalną liczbę fragmentów do buforowania po odebraniu. Lista akcji komunikatów, które mają zostać rozłączone, a maksymalna liczba fragmentów do buforu to dwa parametry przesłane do `ChunkingChannelFactory` w konstruktorze. Sekcja `ChunkingBindingElement` opisująca, z której pochodzą te wartości.

`OnOpen`, ,I`OnAbort` ich równoważne asynchronicznie wywołują odpowiednią metodę przechodzenia stanu w wewnętrznej fabryki kanałów. `OnClose`

## <a name="implementing-channel-listener"></a>Implementowanie odbiornika kanału

`ChunkingChannelListener` Jest otoką wokół odbiornika wewnętrznego kanału. Jej główna funkcja, oprócz wywołań delegatów tego odbiornika kanału wewnętrznego, polega na zawijaniu `ChunkingDuplexSessionChannels` nowych kanałów, które zaakceptowały z odbiornika wewnętrznego kanału. Jest to realizowane w `OnAcceptChannel` i `OnEndAcceptChannel`. Nowo utworzony `ChunkingDuplexSessionChannel` został przekazaną wewnętrzny kanał wraz z innymi opisanymi wcześniej parametrami.

## <a name="implementing-binding-element-and-binding"></a>Implementowanie elementu powiązania i powiązania

`ChunkingBindingElement`jest odpowiedzialny za tworzenie `ChunkingChannelFactory` i `ChunkingChannelListener`. Sprawdza `ChunkingBindingElement` , czy t w `CanBuildChannelFactory` \<t > i `CanBuildChannelListener` \<t > jest typu `IDuplexSessionChannel` (jedyny kanał obsługiwany przez kanał fragmentu) i że inne elementy powiązania w powiązaniu obsługują tę Typ kanału.

`BuildChannelFactory`\<T > najpierw sprawdza, czy żądany typ kanału można skompilować, a następnie pobiera listę akcji komunikatów, które mają zostać rozbudowane. Aby uzyskać więcej informacji, zobacz następującą sekcję. Następnie tworzy nowe `ChunkingChannelFactory` przekazanie do niego wewnętrzną fabrykę kanałów (w wyniku `context.BuildInnerChannelFactory<IDuplexSessionChannel>`powrotu z), listę akcji komunikatów oraz maksymalną liczbę fragmentów do buforowania. Maksymalna liczba fragmentów pochodzi z właściwości o nazwie `MaxBufferedChunks` uwidocznionej `ChunkingBindingElement`przez.

`BuildChannelListener<T>`ma podobną implementację do `ChunkingChannelListener` tworzenia i przekazywania do niego wewnętrznego odbiornika kanału.

Istnieje przykładowe powiązanie dołączone do tego przykładu o nazwie `TcpChunkingBinding`. To powiązanie składa się z dwóch elementów `TcpTransportBindingElement` powiązań `ChunkingBindingElement`: i. Oprócz ujawniania `MaxBufferedChunks` właściwości, powiązanie również ustawia niektóre `TcpTransportBindingElement` właściwości, takie jak `MaxReceivedMessageSize` (ustawia go na `ChunkingUtils.ChunkSize` + 100KB bajtów dla nagłówków).

`TcpChunkingBinding`Ponadto implementuje `IBindingRuntimePreferences` i zwraca wartość true `ReceiveSynchronously` z metody wskazującej, że zaimplementowano tylko synchroniczne wywołania odbioru.

### <a name="determining-which-messages-to-chunk"></a>Określanie komunikatów do fragmentu

Segment segmentu fragmentu tylko komunikaty identyfikowane za pośrednictwem `ChunkingBehavior` atrybutu. Klasa implementuje `IOperationBehavior` i`AddBindingParameter` jest implementowana przez wywołanie metody. `ChunkingBehavior` W tej metodzie `ChunkingBehavior` sprawdza wartość jej `AppliesTo` właściwości (`InMessage` `OutMessage` lub obie), aby określić, które komunikaty powinny zostać rozdzieleniem. Następnie pobiera akcję każdego z tych komunikatów (z kolekcji messages on `OperationDescription`) i dodaje ją do kolekcji ciągów zawartej w `ChunkingBindingParameter`wystąpieniu. Następnie dodaje to `ChunkingBindingParameter` do podanego `BindingParameterCollection`.

Jest `BindingParameterCollection` to przesyłane w `BindingContext` obrębie do każdego elementu wiązania w powiązaniu, gdy ten element powiązania kompiluje fabrykę kanałów lub odbiornik kanału. `ChunkingBindingElement` Implementacja`BuildChannelListener<T>` i wyciągnij te`ChunkingBindingParameter` elementy zprogramu`BindingParameterCollection`. `BuildChannelFactory<T>` `BindingContext’` Kolekcja `ChunkingBindingParameter` akcji zawartych w elemencie jest następnie przekazywana `ChunkingChannelFactory` do lub `ChunkingChannelListener` `ChunkingDuplexSessionChannel`, co z kolei przekazuje go do.

## <a name="running-the-sample"></a>Uruchamianie przykładu

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.

    ```
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

3. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

5. Uruchom najpierw plik Service. exe, a następnie uruchom program Client. exe i obejrzyj oba okna konsoli dla danych wyjściowych.

Podczas uruchamiania przykładu, oczekiwane są następujące dane wyjściowe.

Klient:

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

Server

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
